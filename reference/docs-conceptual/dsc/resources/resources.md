---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 리소스
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954250"
---
# <a name="dsc-resources"></a>DSC 리소스

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다. 리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.

리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다.  같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.

각 리소스에는 [구성](../configurations/configurations.md)에서 리소스를 사용하는 데 필요한 구문을 결정하는 *스키마가 있습니다. 리소스 스키마는 다음 방법으로 정의할 수 있습니다.

- **'Schema.Mof'** 파일: 대부분의 리소스는 [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-)을 사용하여 'schema.mof' 파일에서 해당 ‘스키마’를 정의합니다. 
- **'\<리소스 이름\>.schema.psm1'** 파일: [복합 리소스](../configurations/compositeConfigs.md)는 [매개 변수 블록](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)을 사용하여 '<ResourceName>.schema.psm1' 파일에서 해당 ‘스키마’를 정의합니다. 
- **'\<리소스 이름\>.psm1'** 파일: 클래스 기반 DSC 리소스는 클래스 정의에서 해당 ‘스키마’를 정의합니다.  구문 항목은 클래스 속성으로 표시됩니다. 자세한 내용은 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)를 참조하세요.

DSC 리소스의 구문을 검색하려면 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet과 함께 `-Syntax` 매개 변수를 사용합니다. 이 사용법은 [Get-Command](/powershell/module/microsoft.powershell.core/get-command)와 함께 `-Syntax` 매개 변수를 사용하여 cmdlet 구문을 가져오는 것과 비슷합니다. 표시되는 출력은 지정하는 리소스의 리소스 블록에 사용되는 템플릿을 보여 줍니다.

```powershell
Get-DscResource -Syntax Service
```

표시되는 출력은 아래 출력과 비슷하지만, 이 리소스의 구문은 나중에 변경될 수 있습니다. cmdlet 구문과 같이 대괄호 안에 표시되는 ‘키’는 선택 사항입니다.  형식은 각 키에 필요한 데이터 형식을 지정합니다.

> [!NOTE]
> **Ensure** 키는 기본적으로 "Present"로 설정되므로 선택 사항입니다.

```output
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

구성 내부에 있는 **Service** 리소스 블록은 Spooler 서비스가 실행 중인지 **확인**하기 위해 이와 같이 표시될 수 있습니다.

> [!NOTE]
> 구성에서 리소스를 사용하기 전에 [Import-DSCResource](../configurations/import-dscresource.md)를 사용하여 리소스를 가져와야 합니다.

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }
    }
}
```

구성에는 동일한 리소스 종류의 여러 인스턴스가 포함될 수 있습니다. 각 인스턴스의 이름은 고유해야 합니다. 다음 예제에서는 "DHCP" 서비스를 구성하는 두 번째 **Service** 리소스 블록이 추가됩니다.

```powershell
Configuration TestConfig
{
    # It is best practice to always directly import resources, even if the resource is a built-in resource.
    Import-DSCResource -Name Service
    Node localhost
    {
        # The name of this resource block, can be anything you choose, as long as it is of type [String] as indicated by the schema.
        Service "Spooler:Running"
        {
            Name = "Spooler"
            State = "Running"
        }

        # To configure a second service resource block, add another Service resource block and use a unique name.
        Service "DHCP:Running"
        {
            Name = "DHCP"
            State = "Running"
        }
    }
}
```

> [!NOTE]
> PowerShell 5.0부터, IntelliSense가 DSC용으로 추가되었습니다. 이 새로운 기능을 통해 \<TAB\> 및 \<Ctrl+Space\>를 사용하여 키 이름을 자동 완성할 수 있습니다.

![리소스 탭 완성](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>기본 제공 리소스

커뮤니티 리소스 외에도 Windows용 기본 제공 리소스, Linux용 리소스 및 노드 간 종속성용 리소스가 있습니다. 위의 단계를 사용하여 이 리소스의 구문 및 리소스 사용 방법을 확인할 수 있습니다. 이 리소스를 제공하는 페이지는 **참조**아래에 보관되었습니다.

Windows 기본 제공 리소스

* [보관 리소스](../reference/resources/windows/archiveResource.md)
* [환경 리소스](../reference/resources/windows/environmentResource.md)
* [파일 리소스](../reference/resources/windows/fileResource.md)
* [그룹 리소스](../reference/resources/windows/groupResource.md)
* [GroupSet 리소스](../reference/resources/windows/groupSetResource.md)
* [로그 리소스](../reference/resources/windows/logResource.md)
* [패키지 리소스](../reference/resources/windows/packageResource.md)
* [ProcessSet 리소스](../reference/resources/windows/ProcessSetResource.md)
* [레지스트리 리소스](../reference/resources/windows/registryResource.md)
* [스크립트 리소스](../reference/resources/windows/scriptResource.md)
* [서비스 리소스](../reference/resources/windows/serviceResource.md)
* [ServiceSet 리소스](../reference/resources/windows/serviceSetResource.md)
* [사용자 리소스](../reference/resources/windows/userResource.md)
* [WindowsFeature 리소스](../reference/resources/windows/windowsFeatureResource.md)
* [WindowsFeatureSet 리소스](../reference/resources/windows/windowsFeatureSetResource.md)
* [WindowsOptionalFeature 리소스](../reference/resources/windows/windowsOptionalFeatureResource.md)
* [WindowsOptionalFeatureSet 리소스](../reference/resources/windows/windowsOptionalFeatureSetResource.md)
* [WindowsPackageCabResource 리소스](../reference/resources/windows/windowsPackageCabResource.md)
* [WindowsProcess 리소스](../reference/resources/windows/windowsProcessResource.md)

[노드 간 종속성](../configurations/crossNodeDependencies.md) 리소스

* [WaitForAll 리소스](../reference/resources/windows/waitForAllResource.md)
* [WaitForSome 리소스](../reference/resources/windows/waitForSomeResource.md)
* [WaitForAny 리소스](../reference/resources/windows/waitForAnyResource.md)

패키지 관리 리소스

* [PackageManagement 리소스](../reference/resources/packagemanagement/PackageManagementDscResource.md)
* [PackageManagementSource 리소스](../reference/resources/packagemanagement/PackageManagementSourceDscResource.md)

Linux 리소스

* [Linux 보관 리소스](../reference/resources/linux/lnxArchiveResource.md)
* [Linux 환경 리소스](../reference/resources/linux/lnxEnvironmentResource.md)
* [Linux FileLine 리소스](../reference/resources/linux/lnxFileLineResource.md)
* [Linux 파일 리소스](../reference/resources/linux/lnxFileResource.md)
* [Linux 그룹 리소스](../reference/resources/linux/lnxGroupResource.md)
* [Linux 패키지 리소스](../reference/resources/linux/lnxPackageResource.md)
* [Linux 스크립트 리소스](../reference/resources/linux/lnxScriptResource.md)
* [Linux 서비스 리소스](../reference/resources/linux/lnxServiceResource.md)
* [Linux SshAuthorizedKeys 리소스](../reference/resources/linux/lnxSshAuthorizedKeysResource.md)
* [Linux 사용자 리소스](../reference/resources/linux/lnxUserResource.md)
