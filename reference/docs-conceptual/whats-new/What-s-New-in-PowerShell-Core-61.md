---
title: PowerShell Core 6.1의 새로운 기능
description: PowerShell Core 6.1에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 09/13/2018
ms.openlocfilehash: 3d836a24b494df9c7f6ebe994386e2a0297521fa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086137"
---
# <a name="whats-new-in-powershell-core-61"></a>PowerShell Core 6.1의 새로운 기능

다음은 PowerShell Core 6.1에 도입된 몇 가지 새로운 주요 기능 및 변경 내용의 선택 항목입니다.

PowerShell을 더 빠르고 더 안정적으로 만들어주는 “지루한 작업”도 **많이** 있습니다(또한 아주 많은 버그 수정도)!
변경 사항의 전체 목록은 [GitHub의 changelog](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG.md)를 확인하세요.

다음 이름 중 일부를 호출하는 동안 이 릴리스를 가능하게 해준 [커뮤니티 기여자 모두에게](https://github.com/PowerShell/PowerShell/graphs/contributors) 감사의 말씀을 드립니다.

## <a name="net-core-21"></a>.NET Core 2.1

[5월에 출시](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/)된 후 PowerShell Core 6.1이 .NET Core 2.1로 이동되어 다음을 포함한 다양한 항목이 PowerShell에서 개선되었습니다.

- 성능 향상([아래](#performance-improvements) 참조)
- Alpine Linux 지원(미리 보기)
- [.NET 글로벌 도구 지원](/dotnet/core/tools/global-tools) - PowerShell 곧 예정
- [`Span<T>`](/dotnet/api/system.span-1?view=netcore-2.1)

## <a name="windows-compatibility-pack-for-net-core"></a>.NET Core용 Windows 호환 기능 팩

Windows에서 .NET 팀은 제거된 많은 API를 다시 Windows의 .NET Core로 추가하는 어셈블리 집합인 [.NET Core용 Windows 호환 기능 팩](https://blogs.msdn.microsoft.com/dotnet/2017/11/16/announcing-the-windows-compatibility-pack-for-net-core/)을 제공합니다.

Windows 호환 기능 팩을 PowerShell Core 6.1 릴리스에 추가하였으므로 이러한 API를 사용하는 모든 모듈 또는 스크립트는 사용 가능한 항목에 의존할 수 있습니다.

Windows 호환 기능 책을 통해 PowerShell Core는 **Windows 10 2018년 10월 업데이트 및 Windows Server 2019와 제공되는 1900개 이상의 cmdlet**을 사용할 수 있습니다.

## <a name="support-for-application-whitelisting"></a>애플리케이션 허용 목록에 대한 지원

PowerShell Core 6.1에는 [AppLocker](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) 및 [Device Guard](https://docs.microsoft.com/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control) 애플리케이션 허용 목록을 지원하는 Windows PowerShell 5.1을 사용한 패리티가 있습니다.
애플리케이션 허용 목록은 PowerShell [제한된 언어 모드](https://blogs.msdn.microsoft.com/powershell/2017/11/02/powershell-constrained-language-mode/)와 함께 사용되어 실행할 수 있도록 허용된 바이너리의 세부적 제어를 허용합니다.

## <a name="performance-improvements"></a>성능 향상

PowerShell Core 6.0은 일부 성능이 크게 향상되었습니다.
PowerShell Core 6.1은 특정 작업의 속도를 계속 개선하고 있습니다.

예를 들어 `Group-Object`의 속도는 66% 빨라졌습니다.

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Group-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| 시간(초)   | 25.178                 | 19.653              | 6.641               |
| 속도 증가(%) | 해당 없음                    | 21.9%               | 66.2%               |

마찬가지로, 이와 같은 정렬 시나리오도 15% 이상 향상되었습니다.

```powershell
Measure-Command { 1..100000 | % {Get-Random -Minimum 1 -Maximum 10000} | Sort-Object }
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1 |
|--------------|------------------------|---------------------|---------------------|
| 시간(초)   | 12.170                 | 8.493               | 7.08                |
| 속도 증가(%) | 해당 없음                    | 30.2%               | 16.6%               |

`Import-Csv`도 Windows PowerShell에서 회귀된 후 속도가 크게 향상되었습니다.
다음 예제에서는 26,616개 행과 6개의 열이 있는 CSV 테스트를 사용합니다.

```powershell
Measure-Command {$a = Import-Csv foo.csv}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| 시간(초)   | 0.441                  | 1.069               | 0.268                  |
| 속도 증가(%) | 해당 없음                    | -142.4%             | 74.9%(WPS에서 39.2%) |

마지막으로, JSON에서 `PSObject`로 변환할 때 Windows PowerShell 이후에 50% 이상 속도가 향상되었습니다.
다음 예제에서는 ~2MB 테스트 JSON 파일을 사용합니다.

```powershell
Measure-Command {Get-Content .\foo.json | ConvertFrom-Json}
```

|              | Windows PowerShell 5.1 | PowerShell Core 6.0 | PowerShell Core 6.1    |
|--------------|------------------------|---------------------|------------------------|
| 시간(초)   | 0.259                  | 0.577               | 0.125                  |
| 속도 증가(%) | 해당 없음                    | -122.8%             | 78.3%(WPS에서 51.7%) |

## <a name="check-system32-for-compatible-in-box-modules-on-windows"></a>Windows에서 호환 미해결 모듈에 대한 `system32` 확인

Windows 10 1809 업데이트 및 Windows Server 2019에서 몇 가지 미해결 PowerShell 모듈을 업데이트하여 PowerShell Core와 호환되도록 표시했습니다.

PowerShell Core 6.1이 시작되면 자동으로 `$windir\System32`가 `PSModulePath` 환경 변수의 일부로 포함됩니다.
단, 해당 `CompatiblePSEdition`이 `Core`와 호환되는 것으로 표시되는 경우 모듈을 `Get-Module` 및 `Import-Module`에만 노출합니다.


```powershell
Get-Module -ListAvailable
```

> [!NOTE]
> 설치된 역할 및 기능에 따라 다양한 사용 가능한 모듈을 확인할 수 있습니다.

```Output
...
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, Get-AppxPackage, Get-AppxPacka...
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, Suspend-BitLocker, Resume-Bit...
Manifest   1.0.0.0    DnsClient                           Core,Desk {Resolve-DnsName, Clear-DnsClientCache, Get-DnsC...
Manifest   1.0.0.0    HgsDiagnostics                      Core,Desk {New-HgsTraceTarget, Get-HgsTrace, Get-HgsTraceF...
Binary     2.0.0.0    Hyper-V                             Core,Desk {Add-VMAssignableDevice, Add-VMDvdDrive, Add-VMF...
Binary     1.1        Hyper-V                             Core,Desk {Add-VMDvdDrive, Add-VMFibreChannelHba, Add-VMHa...
Manifest   2.0.0.0    NetAdapter                          Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetEventPacketCapture               Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                             Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                              Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                              Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                         Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam                       Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetWNV                              Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   2.0.0.0    TrustedPlatformModule               Core,Desk {Get-Tpm, Initialize-Tpm, Clear-Tpm, Unblock-Tpm...
...
```

`-SkipEditionCheck` 스위치 매개 변수를 사용하여 모든 모듈을 표시하도록 이 동작을 재정의할 수 있습니다.
또한 `PSEdition` 속성을 테이블 출력에 추가했습니다.

```powershell
Get-Module Net* -ListAvailable -SkipEditionCheck
```

```Output
    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                        PSEdition ExportedCommands
---------- -------    ----                        --------- ----------------
Manifest   2.0.0.0    NetAdapter                  Core,Desk {Disable-NetAdapter, Disable-NetAdapterBinding, ...
Manifest   1.0.0.0    NetConnection               Core,Desk {Get-NetConnectionProfile, Set-NetConnectionProf...
Manifest   1.0.0.0    NetDiagnostics              Desk      Get-NetView
Manifest   1.0.0.0    NetEventPacketCapture       Core,Desk {New-NetEventSession, Remove-NetEventSession, Ge...
Manifest   2.0.0.0    NetLbfo                     Core,Desk {Add-NetLbfoTeamMember, Add-NetLbfoTeamNic, Get-...
Manifest   1.0.0.0    NetNat                      Core,Desk {Get-NetNat, Get-NetNatExternalAddress, Get-NetN...
Manifest   2.0.0.0    NetQos                      Core,Desk {Get-NetQosPolicy, Set-NetQosPolicy, Remove-NetQ...
Manifest   2.0.0.0    NetSecurity                 Core,Desk {Get-DAPolicyChange, New-NetIPsecAuthProposal, N...
Manifest   1.0.0.0    NetSwitchTeam               Core,Desk {New-NetSwitchTeam, Remove-NetSwitchTeam, Get-Ne...
Manifest   1.0.0.0    NetTCPIP                    Core,Desk {Get-NetIPAddress, Get-NetIPInterface, Get-NetIP...
Manifest   1.0.0.0    NetWNV                      Core,Desk {Get-NetVirtualizationProviderAddress, Get-NetVi...
Manifest   1.0.0.0    NetworkConnectivityStatus   Core,Desk {Get-DAConnectionStatus, Get-NCSIPolicyConfigura...
Manifest   1.0.0.0    NetworkSwitchManager        Core,Desk {Disable-NetworkSwitchEthernetPort, Enable-Netwo...
Manifest   1.0.0.0    NetworkTransition           Core,Desk {Add-NetIPHttpsCertBinding, Disable-NetDnsTransi...
```

이 동작에 대한 자세한 내용은 [PowerShell RFC0025](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-PSCore6-and-Windows-Modules.md)를 확인하세요.

## <a name="markdown-cmdlets-and-rendering"></a>Markdown cmdlet 및 렌더링

Markdown은 HTML로 렌더링할 수 있는 기본 서식의 읽을 수 있는 일반 문서를 만들기 위한 표준입니다.

콘솔에서 Markdown 문서를 변환하고 렌더링할 수 있도록 6.1에 다음을 포함한 일부 cmdlet이 추가되었습니다.

- `ConvertFrom-Markdown`
- `Get-MarkdownOption`
- `Set-MarkdownOption`
- `Show-Markdown`

예를 들어 `Show-Markdown`은 콘솔에 Markdown 파일을 렌더링합니다.

![Show-Markdown 예제](./images/markdown_example.png)

이러한 cmdlet의 작동 방식에 대한 자세한 내용은 [이 RFC](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0025-Native-Markdown-Rendering.md)를 확인하세요.

## <a name="experimental-feature-flags"></a>실험적 기능 플래그

[실험적 기능][]에 대한 지원을 사용하도록 설정했습니다. 이 기능을 사용하여 PowerShell 개발자는 새로운 기능을 제공하고 디자인이 완료되기 전에 피드백을 얻을 수 있습니다. 이 방법으로 디자인이 진전됨에 따라 호환성이 손상되는 변경이 생성되는 것을 피합니다.

`Get-ExperimentalFeature`를 사용하여 사용 가능한 실험적 기능 목록을 확인합니다. `Enable-ExperimentalFeature` 및 `Disable-ExperimentalFeature`를 사용하여 이 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.

[PowerShell RFC0029](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0029-Support-Experimental-Features.md)에서 이 기능에 대해 자세히 알아볼 수 있습니다.

## <a name="web-cmdlet-improvements"></a>웹 cmdlet 개선 사항

[@markekraus](https://github.com/markekraus) 덕분에 다음과 같은 우리의 웹 cmdlet에 많은 개선 사항이 적용되었습니다. [`Invoke-WebRequest`](/powershell/module/microsoft.powershell.utility/invoke-webrequest)
및 [`Invoke-RestMethod`](/powershell/module/microsoft.powershell.utility/invoke-restmethod).

- [PR #6109](https://github.com/PowerShell/PowerShell/pull/6109) - `application-json` 응답을 위한 UTF-8로 설정된 기본 인코딩
- [PR #6018](https://github.com/PowerShell/PowerShell/pull/6018) -  표준을 준수하지 않는 `Content-Type` 헤더를 허용하는 `-SkipHeaderValidation` 매개 변수
- [PR #5972](https://github.com/PowerShell/PowerShell/pull/5972) -  간소화된 `multipart/form-data`를 지원하는 `Form` 매개 변수
- [PR #6338](https://github.com/PowerShell/PowerShell/pull/6338) - 호환, 대/소문자를 구분하지 않는 관계 키 처리
- [PR #6447](https://github.com/PowerShell/PowerShell/pull/6447) - 웹 cmdlet에 대한 `-Resume` 매개 변수 추가

## <a name="remoting-improvements"></a>원격 기능 향상

### <a name="powershell-direct-for-containers-tries-to-use-powershell-core-first"></a>컨테이너용 PowerShell Direct에서 먼저 PowerShell Core 사용을 시도

[PowerShell Direct](/virtualization/hyper-v-on-windows/user-guide/powershell-direct)는 사용자가 네트워크 연결 또는 기타 원격 관리 서비스 없이 Hyper-V VM 또는 컨테이너에 연결할 수 있도록 허용하는 PowerShell 및 Hyper-V의 기능입니다.

과거에 PowerShell Direct는 받은 편지함 Windows PowerShell 인스턴스를 사용하여 컨테이너에 연결되었습니다.
이제 PowerShell Direct는 먼저 `PATH` 환경 변수에서 사용 가능한 `pwsh.exe`를 사용하여 연결을 시도합니다.
`pwsh.exe`를 사용할 수 없는 경우 PowerShell Direct는 `powershell.exe`를 다시 사용합니다.

### <a name="enable-psremoting-now-creates-separate-remoting-endpoints-for-preview-versions"></a>`Enable-PSRemoting`은 이제 별도의 원격 엔드포인트를 미리 보기 버전으로 만듭니다.

`Enable-PSRemoting`은 이제 다음과 같이 두 개의 원격 세션 구성을 만듭니다.

- PowerShell의 주 버전에 대해 하나. 정의합니다(예: `PowerShell.6`). 부 버전에 의존할 수 있는 이 엔드포인트는 “시스템 수준” PowerShell 6 세션 구성으로 업데이트함
- 버전별 세션 구성에 대해 하나. 예를 들면 `PowerShell.6.1.0`입니다.

이 동작은 여러 PowerShell 6 버전을 동일한 머신에 설치하고 액세스하려는 경우에 유용합니다.

또한 PowerShell의 미리 보기 버전은 이제 `Enable-PSRemoting` cmdlet을 실행한 후에 각자 자신의 원격 세션 구성을 가져옵니다.

```powershell
C:\WINDOWS\system32> Enable-PSRemoting
```

출력은 이전에 WinRM을 설정하지 않은 경우 달라질 수 있습니다.

```Output
WinRM is already set up to receive requests on this computer.
WinRM is already set up for remote management on this computer.
```

그런 다음, PowerShell 6의 미리 보기 및 안정적 빌드에 대해서와 각 특정 버전에 대해서 별도 PowerShell 세션 구성이 표시됩니다.

```powershell
Get-PSSessionConfiguration
```

```Output
Name          : PowerShell.6.2-preview.1
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6-preview
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed

Name          : powershell.6.1.0
PSVersion     : 6.1
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed, BUILTIN\Remote Management Users AccessAllowed
```

### <a name="userhostport-syntax-supported-for-ssh"></a>SSH에 대해 지원되는 `user@host:port` 구문

SSH 클라이언트는 일반적으로 `user@host:port` 형식의 연결 문자열을 지원합니다.
추가 SSH를 PowerShell 원격 기능에 대한 프로토콜로 사용하여 연결 문자열의 이 형식에 대한 지원을 추가했습니다.

`Enter-PSSession -HostName fooUser@ssh.contoso.com:2222`

## <a name="msi-option-to-add-explorer-shell-context-menu-on-windows"></a>Windows에서 탐색기 셸 상황에 맞는 메뉴를 추가하는 MSI 옵션

[@bergmeister](https://github.com/bergmeister) 덕분에 이제 Windows에서 상황에 맞는 메뉴를 사용할 수 있습니다. 이제 Windows 탐색기의 어느 폴더에서나 PowerShell 6.1의 시스템 수준 설치를 열 수 있습니다.

![PowerShell 6을 위한 셸 상황에 맞는 메뉴](./images/shell_context_menu.png)

## <a name="goodies"></a>혜택

### <a name="run-as-administrator-in-the-windows-shortcut-jump-list"></a>Windows 바로 가기 점프 목록의 “관리자 권한으로 실행”

[@bergmeister](https://github.com/bergmeister) 덕분에 이제 “관리자 권한으로 실행”이 PowerShell Core 바로 가기의 점프 목록에 포함됩니다.

![PowerShell 6 점프 목록의 관리자 권한으로 실행](./images/jumplist.png)

### <a name="cd---returns-to-previous-directory"></a>`cd -`가 이전 디렉터리를 반환

```powershell
C:\Windows\System32> cd C:\
C:\> cd -
C:\Windows\System32>
```

또는 Linux에서:

```ShellSession
PS /etc> cd /usr/bin
PS /usr/bin> cd -
PS /etc>
```

또한 `cd` 및 `cd --`가 `$HOME`으로 변경합니다.

### `Test-Connection`

[@iSazonov](https://github.com/iSazonov) 덕분에 [`Test-Connection`](/powershell/module/microsoft.powershell.management/test-connection) cmdlet이 PowerShell Core에 포트되었습니다.

### <a name="update-help-as-non-admin"></a>`Update-Help`, 관리자가 아님

많은 요청에 의해 `Update-Help`는 더 이상 관리자 권한으로 실행될 필요가 없습니다.
`Update-Help`는 이제 기본 제공되어 사용자 범위 폴더에 대한 도움말을 저장합니다.

### <a name="new-methodsproperties-on-pscustomobject"></a>`PSCustomObject`의 새 메서드/속성

[@iSazonov](https://github.com/iSazonov) 덕분에 새 메서드 및 속성을 `PSCustomObject`에 추가했습니다.
`PSCustomObject`에는 이제 다른 개체처럼 `Count`/`Length` 속성이 포함됩니다.

```powershell
$PSCustomObject = [pscustomobject]@{foo = 1}

$PSCustomObject.Length
```

```Output
1
```

```powershell
$PSCustomObject.Count
```

```Output
1
```

이 작업에는 `PSCustomObject` 항목에서 작동하고 필터링할 수 있도록 허용하는 `ForEach` 및 `Where` 메서드도 포함됩니다.

```powershell
$PSCustomObject.ForEach({$_.foo + 1})
```

```Output
2
```

```powershell
$PSCustomObject.Where({$_.foo -gt 0})
```

```Output
foo
---
  1
```

### `Where-Object -Not`

@SimonWahlin 덕분에 `-Not` 매개 변수를 `Where-Object`에 추가했습니다.
이제 존재하지 않는 속성 또는 null/비어 있는 속성 값에 대한 파이프라인에서 개체를 필터링할 수 있습니다.

예를 들어 이 명령은 정의된 모든 종속 서비스가 없는 모든 서비스를 반환합니다.

```powershell
Get-Service | Where-Object -Not DependentServices
```

### <a name="new-modulemanifest-creates-a-bom-less-utf-8-document"></a>`New-ModuleManifest`는 BOM이 없는 UTF-8 문서를 만듭니다.

PowerShell 6.0에서 BOM이 없는 UTF-8로 이동하여 UTF-16 대신 BOM이 없는 UTF-8 문서를 만들도록 `New-ModuleManifest` cmdlet을 업데이트했습니다.

### <a name="conversions-from-psmethod-to-delegate"></a>PSMethod에서 대리자로 변환

[@powercode](https://github.com/powercode) 덕분에 이제 대리자로의 `PSMethod` 변환을 지원하게 되었습니다.
이를 통해 `PSMethod` `[M]::DoubleStrLen`을 대리자 값으로 `[M]::AggregateString`에 전달하는 등의 작업을 수행할 수 있습니다.

```powershell
class M {
    static [int] DoubleStrLen([string] $value) { return 2 * $value.Length }

    static [long] AggregateString([string[]] $values, [func[string, int]] $selector) {
        [long] $res = 0
        foreach($s in $values){
            $res += $selector.Invoke($s)
        }
        return $res
    }
}

[M]::AggregateString((gci).Name, [M]::DoubleStrLen)
```

이러한 변경 사항에 대한 자세한 내용은 [PR #5287](https://github.com/PowerShell/PowerShell/pull/5287)을 확인하세요.

### <a name="standard-deviation-in-measure-object"></a>`Measure-Object`의 표준 편차

[@CloudyDino](https://github.com/CloudyDino) 덕분에 `StandardDeviation` 속성을 `Measure-Object`에 추가했습니다.

```powershell
Get-Process | Measure-Object -Property CPU -AllStats
```

```Output
Count             : 308
Average           : 31.3720576298701
Sum               : 9662.59375
Maximum           : 4416.046875
Minimum           :
StandardDeviation : 264.389544720926
Property          : CPU
```

### `GetPfxCertificate -Password`

[@maybe-hello-world](https://github.com/maybe-hello-world) 덕분에 `Get-PfxCertificate`는 이제 `SecureString`을 사용하는 `Password` 매개 변수를 가집니다. 이를 통해 비대화형으로 사용할 수 있습니다.

```powershell
$certFile = '\\server\share\pwd-protected.pfx'
$certPass = Read-Host -AsSecureString -Prompt 'Enter the password for certificate: '

$certThumbPrint = (Get-PfxCertificate -FilePath $certFile -Password $certPass ).ThumbPrint
```

### <a name="removal-of-the-more-function"></a>`more` 함수 제거

과거에 PowerShell은 Windows에서 `more.com`을 래핑한 `more`라는 함수를 제공했습니다.
해당 함수는 이제 제거되었습니다.

또한 `help` 함수가 Windows에서 `more.com`을 사용하거나 비Windows 플랫폼에서 `$env:PAGER`에 의해 지정된 시스템의 기본 호출기를 사용하도록 변경되었습니다.

### <a name="cd-drivename-now-returns-users-to-the-current-working-directory-in-that-drive"></a>`cd DriveName:`은 이제 해당 드라이브에서 현재 작업 디렉터리에 사용자를 반환합니다.

이전에는 `Set-Location` 또는 `cd`를 사용하여 PSDrive로 돌아가면 해당 드라이브의 기본 위치로 사용자를 보냈습니다.

[@mcbobke](https://github.com/mcbobke) 덕분에 이제는 해당 세션에 대해 마지막으로 알려진 현재 작업 디렉터리로 사용자를 보냅니다.

### <a name="windows-powershell-type-accelerators"></a>Windows PowerShell 형식 가속기

Windows PowerShell에서 해당 형식과 손쉽게 작업할 수 있도록 다음과 같은 형식 가속기를 포함시켰습니다.

- `[adsi]`: `System.DirectoryServices.DirectoryEntry`
- `[adsisearcher]`: `System.DirectoryServices.DirectorySearcher`
- `[wmi]`: `System.Management.ManagementObject`
- `[wmiclass]`: `System.Management.ManagementClass`
- `[wmisearcher]`: `System.Management.ManagementObjectSearcher`

이러한 형식 가속기는 PowerShell 6에는 포함되지 않았으나, Windows에서 실행 중인 PowerShell 6.1에는 추가되었습니다.

이러한 형식은 AD 및 WMI 개체를 손쉽게 구성하는 데 유용합니다.

예를 들어, LDAP를 사용하여 쿼리할 수 있습니다.

```powershell
[adsi]'LDAP://CN=FooUse,OU=People,DC=contoso,DC=com'
```

다음 예제에서는 Win32_OperatingSystem CIM 개체를 만듭니다.

```powershell
[wmi]"Win32_OperatingSystem=@"
```

```Output
SystemDirectory : C:\WINDOWS\system32
Organization    : Contoso IT
BuildNumber     : 18234
RegisteredUser  : Contoso Corp.
SerialNumber    : 12345-67890-ABCDE-F0123
Version         : 10.0.18234
```

이 예제에서는 Win32_OperatingSystem 클래스에 대한 ManagementClass 개체를 반환합니다.

```powershell
[wmiclass]"Win32_OperatingSystem"
```

```Output
   NameSpace: ROOT\cimv2

Name                                Methods              Properties
----                                -------              ----------
Win32_OperatingSystem               {Reboot, Shutdown... {BootDevice, BuildNumber, BuildType, Caption...}
```

### <a name="-lp-alias-for-all--literalpath-parameters"></a>모든 `-LiteralPath` 매개 변수에 대한 `-lp` 별칭

[@kvprasoon](https://github.com/kvprasoon) 덕분에 이제 `-LiteralPath` 매개 변수가 있는 모든 기본 제공 PowerShell cmdlet에 대해 매개 변수 별칭 `-lp`가 있습니다.

## <a name="breaking-changes"></a>주요 변경 내용

### <a name="msi-based-installation-paths-on-windows"></a>Windows의 MSI 기반 설치 경로

Windows에서 MSI 패키지는 이제 다음 경로에 설치됩니다.

- `$env:ProgramFiles\PowerShell\6\` 6.x의 안정적인 설치용
- `$env:ProgramFiles\PowerShell\6-preview\` 6.x의 미리 보기 설치용

이 변경 내용으로 PowerShell Core는 Microsoft Update에서 업데이트/제공될 수 있습니다.

자세한 내용은 [PowerShell RFC0026](https://github.com/PowerShell/PowerShell-RFC/blob/master/5-Final/RFC0026-MSI-Installation-Path.md)을 확인하세요.

### <a name="telemetry-can-only-be-disabled-with-an-environment-variable"></a>원격 분석은 환경 변수를 통해서만 사용하지 않도록 설정할 수 있습니다.

PowerShell Core는 시작할 때 기본 원격 분석 데이터를 Microsoft로 보냅니다. 데이터에는 OS 이름, OS 버전 및 PowerShell 버전이 포함됩니다. 이 데이터를 사용하면 PowerShell이 사용되는 환경을 더 잘 이해할 수 있으며, 새 기능 및 수정 사항의 우선 순위를 지정할 수 있습니다.

이 원격 분석을 옵트아웃하려면 환경 변수 `POWERSHELL_TELEMETRY_OPTOUT`을 `true`, `yes` 또는 `1`로 설정합니다. 원격 분석을 사용하지 않도록 설정하는 파일 `DELETE_ME_TO_DISABLE_CONSOLEHOST_TELEMETRY`의 삭제를 더 이상 지원하지 않습니다.

### <a name="disallowed-basic-auth-over-http-in-powershell-remoting-on-unix-platforms"></a>Unix 플랫폼에서 PowerShell 원격 기능의 HTTP를 통해 기본 인증 허용 안 함

암호화되지 않은 트래픽 사용을 방지하려면 Unix 플랫폼의 PowerShell 원격 기능은 이제 NTLM/Negotiate 또는 HTTPS를 사용해야 합니다.

이러한 변경 사항에 대한 자세한 내용은 [문제 #6779](https://github.com/PowerShell/PowerShell/issues/6779)를 확인하세요.

### <a name="removed-visualbasic-as-a-supported-language-in-add-type"></a>Add-Type에서 지원되는 언어로 `VisualBasic` 제거

이전에는 `Add-Type` cmdlet을 사용하여 Visual Basic 코드를 컴파일할 수 있었습니다.
Visual Basic은 `Add-Type`과는 거의 사용되지 않았습니다. PowerShell의 크기를 줄이기 위해 이 기능을 제거했습니다.

### <a name="cleaned-up-uses-of-commandtypesworkflow-and-workflowinfocleaned"></a>`CommandTypes.Workflow` 및 `WorkflowInfoCleaned` 사용 정리

이러한 변경 사항에 대한 자세한 내용은 [PR #6708](https://github.com/PowerShell/PowerShell/pull/6708)을 확인하세요.

### <a name="group-object-now-sorts-the-groups"></a>이제 Group-Object가 그룹 정렬

성능 개선의 일환으로, `Group-Object`가 이제 정렬된 그룹 목록을 반환합니다.
순서에 의존해서는 안 되지만, 첫 번째 그룹을 원한 경우 이러한 변경으로 낙담할 수 있습니다. Microsoft는 이전 동작에 종속되는 영향력이 낮으므로 이 성능 개선이 변경 가치가 있다고 결정했습니다.

이 변경에 대한 자세한 내용은 [문제 #7409](https://github.com/PowerShell/PowerShell/issues/7409)를 참조하세요.

<!-- URL references -->
[실험적 기능]: /powershell/module/Microsoft.PowerShell.Core/About/about_Experimental_Features
