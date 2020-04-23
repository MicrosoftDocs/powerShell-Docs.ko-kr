---
ms.date: 12/12/2018
keywords: dsc,powershell,리소스,갤러리,설정
title: 추가 DSC 리소스 설치
ms.openlocfilehash: 7a6a935349358e11a77d2f00c0bf88e0ad18c097
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417803"
---
# <a name="install-additional-dsc-resources"></a>추가 DSC 리소스 설치

PowerShell에는 DSC(Desired State Configuration)의 여러 가지 기본 제공 리소스가 포함됩니다. **PSDesiredStateConfiguration** 모듈에는 특정 PowerShell 인스턴스에서 사용할 수 있는 모든 OOB DSC 리소스가 포함됩니다.

PowerShell 4.0에 포함된 OOB 리소스 및 리소스 기능에 대한 설명의 목록입니다.

> [!NOTE]
> OOB 리소스 수가 PowerShell의 각 버전과 함께 증가하므로 불완전한 목록입니다.

|리소스  |Description  |
|---------|---------|
|**최근에 사용한 파일**|파일 및 디렉터리의 상태를 제어합니다. **원본**에서 **대상**으로 파일을 복사하고 날짜, 체크섬 및 해시를 비교하여 **원본**이 변경되면 파일을 업데이트합니다.|
|**보관**|지정된 위치에 보관 파일의 압축을 풉니다. 지정된 **체크섬**을 사용하여 보관 파일의 유효성을 검사합니다.|
|**환경**|환경 변수를 관리합니다.|
|**그룹**|로컬 그룹을 관리하고 그룹 멤버 자격을 제어합니다.|
|**Log**|`Microsoft-Windows-Desired State Configuration/Analytic` 이벤트 로그에 메시지를 씁니다.|
|**패키지**|**Arguments**, **LogPath**, **ReturnCode**, 기타 설정을 사용하여 패키지를 설치하거나 제거합니다.|
|**Registry**|레지스트리 키 및 값을 관리합니다.|
|**스크립트**|고유한 [get-test-set](../resources/get-test-set.md) script 블록을 디자인할 수 있습니다.|
|**서비스**|Windows 서비스를 구성합니다.|
|**사용자** |로컬 사용자 및 특성을 관리합니다.|
|**WindowsFeature**|역할 및 기능을 관리합니다.|
|**WindowsProcess**|Windows 프로세스를 구성합니다.|

OOB 리소스는 일반적인 작업을 위한 좋은 시작점입니다. OOB 리소스가 필요에 맞지 않으면 고유한 [사용자 지정 리소스](../resources/authoringResource.md)를 작성할 수 있습니다. 문제를 해결하기 위한 사용자 지정 리소스를 작성하기 전에 Microsoft 및 PowerShell 커뮤니티에서 이미 만들어진 수많은 DSC 리소스를 살펴보아야 합니다.

[PowerShell 갤러리](https://www.powershellgallery.com/) 및 [GitHub](https://github.com/)에서 DSC 리소스를 찾을 수 있습니다. [PowerShellGet](/powershell/module/powershellget/)을 사용하여 PowerShell 콘솔에서 직접 DSC 리소스를 설치할 수도 있습니다.

## <a name="installing-powershellget"></a>PowerShellGet 설치

**PowerShell**을 이미 다운로드했는지 확인하거나 설치하는 데 도움이 필요하면 다음 가이드를 참조하세요. [PowerShellGet 설치](/powershell/scripting/gallery/installing-psget).

## <a name="finding-dsc-resources-using-powershellget"></a>PowerShellGet을 사용하여 DSC 리소스 찾기

**PowerShellGet**이 시스템에 설치되면 [PowerShell 갤러리](https://www.powershellgallery.com/)에서 호스트되는 DSC 리소스를 찾고 설치할 수 있습니다.

먼저, [Find-DSCResource](/powershell/module/powershellget/find-dscresource) cmdlet을 사용하여 DSC 리소스를 찾습니다. `Find-DSCResource`를 처음 실행하면 “NuGet 공급자”를 설치하라는 다음 메시지가 표시됩니다.

```
PS> Find-DSCResource

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The
NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\xAdministrator\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider
 by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to
install and import the NuGet provider now?
[Y] Yes  [N] No  [?] Help (default is "Y"):
```

‘y’를 누른 후 “NuGet” 공급자가 설치되고, PowerShell 갤러리에서 설치할 수 있는 DSC 리소스 목록이 표시됩니다.

> [!NOTE]
> 목록이 매우 크기 때문에 표시되지 않습니다.

와일드카드를 사용하여 `-Name` 매개 변수를 지정하거나 와일드카드 없이 `-Filter` 매개 변수를 지정하여 검색 범위를 좁힐 수도 있습니다. 이 예제에서는 와일드카드를 사용하여 “TimeZone” DSC 리소스를 찾겠습니다.

> [!IMPORTANT]
> 현재 `Find-DSCResource` cmdlet에는 `-Name` 및 `-Filter` 매개 변수에서 와일드카드를 사용할 수 없는 버그가 있습니다. 아래 두 번째 예제에서는 `Where-Object`를 사용하여 해결 방법을 보여 줍니다.

```
PS> Find-DSCResource -Name *Time*

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Carbon_EnvironmentVariable          2.6.0      Carbon                              PSGallery
Carbon_FirewallRule                 2.6.0      Carbon                              PSGallery
Carbon_Group                        2.6.0      Carbon                              PSGallery
Carbon_IniFile                      2.6.0      Carbon                              PSGallery
Carbon_Permission                   2.6.0      Carbon                              PSGallery
Carbon_Privilege                    2.6.0      Carbon                              PSGallery
Carbon_ScheduledTask                2.6.0      Carbon                              PSGallery
Carbon_Service                      2.6.0      Carbon                              PSGallery
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
xTimeZone                           1.8.0.0    xTimeZone                           PSGallery
xSqlServerDefaultDir                1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerMoveDatabaseFiles         1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerSQLDataRoot               1.0.0      mlSqlServerDSC                      PSGallery
xSqlServerStartupParam              1.0.0      mlSqlServerDSC                      PSGallery
```

`Where-Object`를 사용하여 더 세분화된 필터링을 통해 DSC 리소스를 찾을 수도 있습니다. 이 방법은 기본 제공 필터링 매개 변수를 사용하는 것보다 느립니다.

```
PS> Find-DSCResource | Where-Object {$_.Name -like "Time*"}

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
TimeZone                            6.0.0.0    ComputerManagementDsc               PSGallery
```

필터링에 대한 자세한 내용은 [Where-Object](/powershell/module/microsoft.powershell.core/where-object)를 참조하세요.

## <a name="installing-dsc-resources-using-powershellget"></a>PowerShellGet을 사용하여 DSC 리소스 설치

DSC 리소스를 설치하려면 [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet을 사용하여 검색 결과에서 **모듈** 이름 아래에 표시되는 모듈 이름을 지정합니다.

“TimeZone” 리소스는 이 예제에서 설치하는 “ComputerManagementDSC” 모듈에 있습니다.

> [!NOTE]
> PowerShell 갤러리를 신뢰하지 않은 경우에는 확인 여부를 묻고 설치 관련 후속 프롬프트를 표시하지 않는 방법을 알려주는 아래 경고가 표시됩니다.

```
PS> Install-Module -Name ComputerManagementDSC

Untrusted repository
You are installing the modules from an untrusted repository. If you trust this repository, change its
InstallationPolicy value by running the Set-PSRepository cmdlet. Are you sure you want to install the modules from
'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

‘y’를 눌러 모듈을 계속 설치합니다. 설치한 후 새 리소스가 [Get-DSCResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)를 사용하여 설치되었음을 확인할 수 있습니다.

```
PS> Get-DSCResource -Name TimeZone -Syntax

TimeZone [String] #ResourceName
{
    IsSingleInstance = [string]{ Yes }
    TimeZone = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

`-ModuleName` 매개 변수를 지정하여 새로 설치된 모듈에서 다른 리소스를 볼 수도 있습니다.

```
PS> Get-DSCResource -Module ComputerManagementDSC

ImplementedAs   Name                      ModuleName                     Version    Properties
-------------   ----                      ----------                     -------    ----------
PowerShell      Computer                  ComputerManagementDsc          6.0.0.0    {Name, Credential, DependsOn, ...
PowerShell      OfflineDomainJoin         ComputerManagementDsc          6.0.0.0    {IsSingleInstance, RequestFile...
PowerShell      PowerPlan                 ComputerManagementDsc          6.0.0.0    {IsSingleInstance, Name, Depen...
PowerShell      PowerShellExecutionPolicy ComputerManagementDsc          6.0.0.0    {ExecutionPolicy, ExecutionPol...
PowerShell      ScheduledTask             ComputerManagementDsc          6.0.0.0    {TaskName, ActionArguments, Ac...
PowerShell      TimeZone                  ComputerManagementDsc          6.0.0.0    {IsSingleInstance, TimeZone, D...
PowerShell      VirtualMemory             ComputerManagementDsc          6.0.0.0    {Drive, Type, DependsOn, Initi...
```

## <a name="see-also"></a>참고 항목

- [리소스란?](../resources/resources.md)
