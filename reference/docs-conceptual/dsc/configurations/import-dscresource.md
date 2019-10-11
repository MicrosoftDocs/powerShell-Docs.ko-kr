---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Import-DSCResource 사용
ms.openlocfilehash: f6c1260bac7d4c545f5a6bc4c098ca90ebb186b5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954060"
---
# <a name="using-import-dscresource"></a>Import-DSCResource 사용

`Import-DScResource`는 구성 스크립트 블록 내부에서만 사용할 수 있는 동적 키워드입니다. 구성에 필요한 모든 리소스를 가져오기 위한 `Import-DSCResource` 키워드입니다. `$pshome` 아래에 있는 리소스를 자동으로 가져오지만, [구성](Configurations.md)에서 사용된 모든 리소스를 명시적으로 가져오는 것이 좋습니다.

`Import-DSCResource`의 구문은 다음과 같습니다.  이름으로 모듈을 지정하는 경우 각 모듈을 새 줄에 나열해야 합니다.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>] [-ModuleVersion <ModuleVersion>]
```

|매개 변수  |설명  |
|---------|---------|
|`-Name`|가져와야 하는 DSC 리소스 이름입니다. 모듈 이름을 지정하면 명령은 이 모듈 내에서 해당 DSC 리소스를 검색하고, 모듈 이름을 지정하지 않으면 명령은 모든 DSC 리소스 경로에서 DSC 리소스를 검색합니다. 와일드카드가 지원됩니다.|
|`-ModuleName`|모듈 이름 또는 모듈 사양입니다.  모듈에서 가져올 리소스를 지정하면 명령은 해당 리소스만 가져옵니다. 모듈만 지정하면 명령은 모듈에 있는 모든 DSC 리소스를 가져옵니다.|
|`-ModuleVersion`|PowerShell 5.0부터 구성에서 사용해야 하는 모듈의 버전을 지정할 수 있습니다. 자세한 내용은 [설치된 리소스의 특정 버전 가져오기](sxsresource.md)를 참조하세요.|

```powershell
Import-DscResource -ModuleName xActiveDirectory
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>예: 구성 내에서 Import-DSCResource 사용

```powershell
Configuration MSDSCConfiguration
{
    # Search for and imports Service, File, and Registry from the module PSDesiredStateConfiguration.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration -Name Service, File, Registry

    # Search for and import Resource1 from the module that defines it.
    # If only –Name parameter is used then resources can belong to different PowerShell modules as well.
    # TimeZone resource is from the ComputerManagementDSC module which is not installed by default.
    # As a best practice, list each requirement on a different line if possible.  This makes reviewing
    # multiple changes in source control a bit easier.
    Import-DSCResource -Name File
    Import-DSCResource -Name TimeZone

    # Search for and import all DSC resources inside the module PSDesiredStateConfiguration.
    # When specifying the modulename parameter, it is a requirement to list each on a new line.
    Import-DSCResource -ModuleName PSDesiredStateConfiguration
    # In PowerShell 5.0 and later, you can specify a ModuleVersion parameter
    Import-DSCResource -ModuleName ComputerManagementDsc -ModuleVersion 6.0.0.0
...
```

> [!NOTE]
> 동일한 명령에서 리소스 이름 및 모듈 이름에 여러 값을 지정할 수는 없습니다. 명령은 동일한 리소스가 여러 모듈에 있는 경우 어떤 모듈에서 어떤 리소스를 로드할지에 대한 비결정적 동작을 포함할 수 없습니다. 아래 명령을 실행하면 컴파일하는 동안 오류가 발생합니다.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Name 매개 변수를 사용하는 경우 고려해야 할 사항:

- 머신에 설치된 모듈 수에 따라 리소스가 많이 사용되는 작업입니다.
- 지정된 이름을 사용하여 발견된 첫 번째 리소스를 로드합니다. 동일한 이름을 가진 둘 이상의 리소스가 설치된 경우 잘못된 리소스를 로드할 수 있습니다.

아래 설명된 대로 `-Name` 매개 변수를 사용하여 `–ModuleName`을 지정하는 것이 좋습니다.

이 방법은 다음과 같은 이점이 있습니다.

- 지정된 리소스의 검색 범위를 제한하여 성능에 미치는 영향을 줄입니다.
- 리소스를 정의하는 모듈을 명시적으로 정의하므로 올바른 리소스가 로드됩니다.

> [!NOTE]
> PowerShell 5.0에서 DSC 리소스는 여러 버전이 있을 수 있으며, 이러한 버전들을 컴퓨터에 병렬로 설치할 수 있습니다. 이는 동일한 모듈 폴더에 포함된 여러 버전의 리소스 모듈에 의해 구현됩니다.
> 자세한 내용은 [여러 버전의 리소스 사용](sxsresource.md)을 참조하세요.

## <a name="intellisense-with-import-dscresource"></a>Intellisense 및 Import-DSCResource

ISE에서 DSC 구성을 작성하면 PowerShell에서는 리소스 및 리소스 속성에 대한 IntelliSense를 제공합니다. `$pshome` 모듈 경로 아래에 있는 리소스 정의가 자동으로 로드됩니다. `Import-DSCResource` 키워드를 사용하여 리소스를 가져오면 지정된 리소스 정의가 추가되고 가져온 리소스의 스키마를 포함하도록 IntelliSense가 확장됩니다.

![리소스 IntelliSense](../media/resource-intellisense.png)

> [!NOTE]
> PowerShell 5.0부터, 탭 완성이 DSC 리소스 및 해당 속성에 대한 ISE에 추가되었습니다. 자세한 내용은 [리소스](../resources/resources.md)를 참조하세요.

구성을 컴파일할 때 PowerShell에서는 가져온 리소스 정의를 사용하여 구성에 있는 모든 리소스 블록의 유효성을 검사합니다.
다음 규칙에 대해 리소스의 스키마 정의를 사용하여 각 리소스 블록의 유효성을 검사합니다.

- 스키마에 정의된 속성만 사용됩니다.
- 각 속성의 데이터 형식이 올바릅니다.
- 키 속성이 지정됩니다.
- 읽기 전용 속성이 사용되지 않습니다.
- 값에 대한 유효성 검사가 형식을 매핑합니다.

다음 구성을 고려하세요.

```powershell
Configuration SchemaValidationInCorrectEnumValue
{
    # It is best practice to explicitly import all resources used in your Configuration.
    # This includes resources that are imported automatically, like WindowsFeature.
    Import-DSCResource -Name WindowsFeature
    Node localhost
    {
        WindowsFeature ROLE1
        {
            Name = "Telnet-Client"
            Ensure = "Invalid"
        }
    }
}
```

이 구성을 컴파일하면 오류가 발생합니다.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values 'Invalid' is not supported or valid for property 'Ensure' on class 'WindowsFeature'. Please specify only supported values: Present, Absent.
```

IntelliSense 및 스키마 유효성 검사를 사용하면 구문 분석 및 컴파일 시간에 더 많은 오류를 catch할 수 있어 런타임에 컴플리케이션이 방지됩니다.

> [!NOTE]
> 각 DSC 리소스에는 이름 및 리소스 스키마에서 정의한 **FriendlyName**이 포함될 수 있습니다. "MSFT_ServiceResource.shema.mof"의 처음 두 줄은 다음과 같습니다.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> 구성에서 이 리소스를 사용하는 경우 **MSFT_ServiceResource** 또는 **Service**를 지정할 수 있습니다.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 및 v5의 차이

PowerShell 4.0 및 PowerShell 5.0 이상에서 구성을 작성할 때 확인되는 여러 가지 차이가 있습니다. 이 섹션에서는 이 문서에 관련된 차이를 중점적으로 설명합니다.

### <a name="multiple-resource-versions"></a>여러 리소스 버전

PowerShell 4.0에서는 여러 리소스 버전을 병렬로 설치 및 사용할 수 없습니다. 리소스를 구성으로 가져오는 동안 문제가 발생하면 설치된 리소스 버전이 하나만 있는지 확인하세요.

아래 이미지에는 **xPSDesiredStateConfiguration** 모듈의 두 가지 버전이 설치되어 있습니다.

![수정된 여러 리소스 버전](../media/multiple-resource-versions-broken.png)

원하는 모듈 버전의 콘텐츠를 모듈 디렉터리의 맨 위 수준으로 복사합니다.

![수정된 여러 리소스 버전](../media/multiple-resource-versions-fixed.png)

### <a name="resource-location"></a>리소스 위치

구성을 작성하고 컴파일하면 [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)에서 지정한 디렉터리에 리소스를 저장할 수 있습니다. PowerShell 4.0에서 LCM을 사용하려면 모든 DSC 리소스 모듈을 “Program Files\WindowsPowerShell\Modules” 또는 `$pshome\Modules` 아래에 저장해야 합니다. PowerShell 5.0부터, 이 요구 사항이 제거되었고 리소스 모듈은 `PSModulePath`에서 지정한 모든 디렉터리에 저장할 수 있습니다.

### <a name="moduleversion-added"></a>ModuleVersion 추가됨

PowerShell 5.0부터 `-ModuleVersion` 매개 변수를 사용하여 구성 내에서 사용할 모듈의 버전을 지정할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [리소스](../resources/resources.md)
