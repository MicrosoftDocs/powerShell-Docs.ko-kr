---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: DSC 리소스
ms.openlocfilehash: 1f77b5e6630a2e3de6e1d1a05638f94d2df039ae
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681013"
---
# <a name="dsc-resources"></a>DSC 리소스

>적용 대상: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC(필요한 상태 구성) 리소스에서는 DSC 구성에 대한 구성 요소를 제공합니다. 리소스는 구성할 수 있는 속성(스키마)을 노출하고 LCM(로컬 구성 관리자)이 "그대로 수행"하기 위해 호출하는 PowerShell 스크립트 함수를 포함합니다.

리소스는 파일만큼 일반적이거나 IIS 서버만큼 특별한 것을 모델링할 수 있습니다.  같은 리소스들의 그룹은 모든 필수 파일을 이식 가능한 구조로 정리하고, 리소스를 사용하려고 한 방법을 식별하는 메타데이터를 포함하는 DSC 모듈에 결합됩니다.

각 리소스에는 *에서 리소스를 사용 하는 데 필요한 구문을 결정 하는 스키마를 [구성](../configurations/configurations.md)합니다. 다음과 같은 방법으로 리소스의 스키마를 정의할 수 있습니다.

- **'Schema.Mof'** 파일: 대부분의 리소스 정의 자신의 *스키마* 'schema.mof'에서 파일을 사용 하 여 [Managed Object Format](/windows/desktop/wmisdk/managed-object-format--mof-)합니다.
- **'\<리소스 이름\>. schema.psm1'** 파일: [복합 리소스](../configurations/compositeConfigs.md) 정의 해당 *스키마* 에 '<ResourceName>. schema.psm1'를 사용 하 여 파일을 [매개 변수 블록](/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-6#functions-with-parameters)합니다.
- **'\<리소스 이름\>. psm1 '** 파일: 클래스 기반된 DSC 리소스 정의 자신의 *스키마* 클래스 정의에서 합니다. 구문 항목 클래스 속성으로 표시 됩니다. 자세한 내용은 [about_Classes](/powershell/module/psdesiredstateconfiguration/about/about_classes_and_dsc)합니다.

DSC 리소스에 대 한 구문을 검색 하려면 사용 합니다 [Get-dscresource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet을 사용 합니다 `-Syntax` 매개 변수입니다. 이 사용법은 사용 하 여 유사 [Get-command](/powershell/module/microsoft.powershell.core/get-command) 사용 하 여는 `-Syntax` cmdlet 구문을 가져오려면 매개 변수입니다. 출력에는 지정 하는 리소스에 대 한 리소스 블록에 사용 된 템플릿을 표시 됩니다.

```powershell
Get-DscResource -Syntax Service
```

이 리소스의이 구문은 나중에 변경할 수 있지만 출력 아래 출력과 유사 하 게 해야 합니다. Cmdlet 구문으로 *키* 대괄호 안에 표시 하는 것은 선택 사항입니다. 형식에 각 키에서 예상 하는 데이터의 형식을 지정 합니다.

> [!NOTE]
> 합니다 **확인** 키 이므로 선택적 기본값은 "Present"로 합니다.

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

구성에서는 내부를 **서비스** 리소스 블록을 다음과 같이 표시 될 수 있습니다 **확인** 스풀러 서비스를 실행 하는 합니다.

> [!NOTE]
> 구성에서 리소스를 사용 하기 전에 가져와야를 사용 하 여 [Import-dscresource](../configurations/import-dscresource.md)합니다.

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

구성이 동일한 리소스 유형의 여러 인스턴스를 포함할 수 있습니다. 각 인스턴스는 고유 하 게 지정 해야 합니다. 다음 예제에서 두 번째 **서비스** 리소스 블록 "DHCP" 서비스 구성에 추가 됩니다.

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
> PowerShell 5.0부터 intellisense DSC에 추가 되었습니다. 이 새로운 기능을 사용 하면 사용할 수 있습니다 \<탭\> 하 고 \<Ctrl + Space\> 키 이름 자동 완성 합니다.

![리소스 탭 완성 기능](../media/resource-tabcompletion.png)

## <a name="built-in-resources"></a>기본 제공 리소스

커뮤니티 리소스와 함께 Windows, Linux에 대 한 리소스 및 노드 간 종속성에 대 한 리소스에 대 한 기본 제공 리소스가 있습니다. 이러한 리소스 및 사용 하는 방법의 구문을 확인 하려면 위의 단계를 사용할 수 있습니다. 이러한 리소스를 제공 하는 페이지에서 보관 된 **참조**합니다.

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
