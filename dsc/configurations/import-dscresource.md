---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Import-DSCResource 사용
ms.openlocfilehash: ee0b2f0469c6507c8f0148138198597a9e57cdd7
ms.sourcegitcommit: c581c4c8036edf55147e7bce4b00c860da6c5a8b
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/25/2019
ms.locfileid: "56803415"
---
# <a name="using-import-dscresource"></a>Import-DSCResource 사용

`Import-DScResource` 구성 스크립트 블록 내부 에서만 사용할 수 있는 동적 키워드가입니다. `Import-DSCResource` 구성에 필요한 모든 리소스를 가져오기 위해 키워드입니다. 아래에 있는 리소스 `$pshome` 자동으로 가져와집니다를 명시적으로 사용 되는 모든 리소스를 가져와야 하는 모범 사례는 여전히 간주 하지만 하 [구성](Configurations.md)합니다.

구문은 `Import-DSCResource` 아래에 표시 됩니다.  모듈 이름으로 지정, 경우 새 줄에 나열 하는 요구 사항이 있습니다.

```syntax
Import-DscResource [-Name <ResourceName(s)>] [-ModuleName <ModuleName>]
```

|매개 변수  |설명  |
|---------|---------|
|`-Name`|가져와야 하는 DSC 리소스 이름입니다. 모듈 이름 지정,이 모듈 내에서 이러한 DSC 리소스에 대 한 명령 검색 그렇지 않은 경우 명령은 모든 DSC 리소스 경로에 DSC 리소스를 검색합니다. 와일드카드가 지원됩니다.|
|`-ModuleName`|모듈 이름 또는 모듈 사양입니다.  모듈에서 가져올 리소스를 지정 하는 경우이 명령은 해당 리소스에만 가져오기 하려고 합니다. 만 모듈을 지정 하는 경우 명령 모듈에 있는 모든 DSC 리소스를 가져옵니다.|

```powershell
Import-DscResource -ModuleName xActiveDirectory;
```

## <a name="example-use-import-dscresource-within-a-configuration"></a>예: 사용 하 여 Import-dscresource 구성 내에서

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
    Import-DSCResource -ModuleName ComputerManagementDsc
...
```

> [!NOTE]
> 동일한 명령에서 리소스 이름과 모듈에 대 한 여러 값을 지정 하는 것은 지원 되지 않습니다. 여러 모듈에 동일한 리소스가 있는 경우에 모듈에서 로드 하는 리소스에 대 한 비 결정적인 동작을 가질 수 있습니다. 아래 명령을 오류가 발생 합니다 컴파일하는 동안.
>
> ```powershell
> Import-DscResource -Name UserConfigProvider*,TestLogger1 -ModuleName UserConfigProv,PsModuleForTestLogger
> ```

Name 매개 변수를 사용 하는 경우를 고려해 야 할 사항은 다음과 같습니다.

- 이 컴퓨터에 설치 된 모듈 수에 따라 리소스 집약적 작업입니다.
- 첫 번째 리소스를 지정 된 이름을 사용 하 여 찾을 수 로드 됩니다. 경우에서 잘못 된 리소스를 다시 로드할를 설치 하는 동일한 이름 가진 둘 이상의 리소스가 있는 합니다.

권장된 사용법을 지정 하는 것 `–ModuleName` 사용 하 여는 `-Name` 아래 설명 된 대로 매개 변수입니다.

이 사용에는 다음과 같은 이점이 있습니다.

- 지정된 된 리소스에 대 한 검색 범위를 제한 하 여 성능에 영향을 줄입니다.
- 명시적으로 로드 되 고 올바른 리소스를 보장 된 리소스를 정의 하는 모듈을 정의 합니다.

> [!NOTE]
> PowerShell 5.0에서 DSC 리소스는 여러 버전이 있을 수 있으며, 이러한 버전들을 컴퓨터에 병렬로 설치할 수 있습니다. 이는 동일한 모듈 폴더에 포함된 여러 버전의 리소스 모듈에 의해 구현됩니다.
> 자세한 내용은 [여러 버전의 리소스 사용](sxsresource.md)을 참조하세요.

## <a name="intellisense-with-import-dscresource"></a>Import-dscresource를 사용 하 여 Intellisense

ISE에서 DSC 구성을 작성, PowerShell 리소스 및 리소스 속성에 대 한 IntelliSence를 제공 합니다. 아래 리소스 정의 `$pshome` 모듈 경로 자동으로 로드 됩니다. 사용 하 여 리소스를 가져올 때는 `Import-DSCResource` 키워드를 지정 된 리소스 정의 추가 하 고 Intellisense 가져온된 리소스의 스키마를 포함 하도록 확장 됩니다.

![리소스 Intellisense](/media/resource-intellisense.png)

> [!NOTE]
> PowerShell 5.0부터, 탭 완성 기능 DSC 리소스 및 해당 속성에 대 한 ISE에 추가 되었습니다. 자세한 내용은 [리소스](../resources/resources.md)합니다.

구성을 컴파일할 때 PowerShell를 사용 하 여 가져온된 리소스 정의 구성에서 모든 리소스 블록의 유효성을 검사 합니다.
다음 규칙에 대 한 리소스의 스키마 정의 사용 하 여 각 리소스 블록의 유효성이 검사 됩니다.

- 스키마에 정의 된 속성에 대해서만 사용 됩니다.
- 각 속성에 대 한 데이터 형식이 올바릅니다.
- 키 속성 지정 됩니다.
- 읽기 전용 속성이 사용 됩니다.
- 값에 대 한 유효성 검사 형식을 매핑합니다.

다음 구성을 고려 합니다.

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
            Name = “Telnet-Client”
            Ensure = “Invalid”
        }
    }
}
```

오류가이 구성 결과 컴파일하고 있습니다.

```output
PSDesiredStateConfiguration\WindowsFeature: At least one of the values ‘Invalid’ is not supported or valid for property ‘Ensure’ on class ‘WindowsFeature’. Please specify only supported values: Present, Absent.
```

Intellisense 및 스키마 유효성 검사를 사용 하면 런타임에 복잡성을 방지 구문 분석 및 컴파일 시간 동안 더 많은 오류를 catch 할 수 있습니다.

> [!NOTE]
> 각 DSC 리소스는 이름이 나 지정할 수와 **FriendlyName** 리소스의 스키마에 의해 정의 됩니다. "MSFT_ServiceResource.shema.mof"의 처음 두 줄은 다음과 같습니다.
> ```syntax
> [ClassVersion("1.0.0"),FriendlyName("Service")]
> class MSFT_ServiceResource : OMI_BaseResource
> ```
> 구성에서이 리소스를 사용 하는 경우 지정할 수 있습니다 **MSFT_ServiceResource** 하거나 **서비스**합니다.

## <a name="powershell-v4-and-v5-differences"></a>PowerShell v4 및 v5 차이점

PowerShell 4.0 vs에서 구성을 작성 하는 경우 표시는 여러 차이점이 있습니다. PowerShell 5.0 이상 이 섹션에서는 차이점을 강조 표시는이 문서와 관련 된 표시를 합니다.

### <a name="multiple-resource-versions"></a>여러 리소스 버전

설치 하 고 여러 버전의 리소스를 함께 사용 된 PowerShell 4.0에서 지원 되지 않습니다. 구성에 리소스를 가져오는 문제를 발견 하는 경우 설치 리소스의 버전 하나만 있는지 확인 합니다.

두 가지 버전의 아래 이미지에는 **xPSDesiredStateConfiguration** 모듈이 설치 됩니다.

![고정 하는 여러 리소스 버전](/media/multiple-resource-versions-broken.md)

모듈 디렉터리의 최상위 수준으로 원하는 모듈 버전의 콘텐츠를 복사 합니다.

![고정 하는 여러 리소스 버전](/media/multiple-resource-versions-fixed.md)

### <a name="resource-location"></a>리소스 위치

리소스에서 지정 된 디렉터리에 저장할 수 제작 및 구성 컴파일링, 경우에 [PSModulePath](/powershell/developer/module/modifying-the-psmodulepath-installation-path)합니다. PowerShell 4.0에서 LCM 필요 "프로그램 Files\WindowsPowerShell\Modules" 아래에 저장 될 모든 DSC 리소스 모듈 또는 `$pshome\Modules`합니다. PowerShell 5.0부터,이 요구 사항이 제거 되었지만, 및 리소스 모듈에서 지정 된 디렉터리에 저장할 수 있습니다 `PSModulePath`합니다.

## <a name="see-also"></a>참고 항목

- [리소스](../resources/resources.md)
