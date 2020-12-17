---
title: PowerShell 7.1의 새로운 기능
description: PowerShell 7.1에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 11/11/2020
ms.openlocfilehash: 5596d3ca69f5d8ea47f01ff0915e6fa33c1c463f
ms.sourcegitcommit: fb1a4bc4b249afd3513663de2e1ba3025d63467e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/14/2020
ms.locfileid: "94625723"
---
# <a name="whats-new-in-powershell-71"></a>PowerShell 7.1의 새로운 기능

PowerShell 7.1은 서로 다른 환경 및 하이브리드 클라우드를 관리하도록 빌드된 오픈 소스 플랫폼 간(Windows, macOS 및 Linux) 버전입니다.

PowerShell 7.0에 구축된 토대를 기반으로 하여 커뮤니티에서 보고된 문제에 초점을 맞춘 노력을 통해 다수의 개선 사항 및 수정 사항을 포함합니다. Microsoft에서는 PowerShell을 안정적이고 성능이 뛰어난 플랫폼으로 유지하기 위해 최선을 다하고 있습니다.

PowerShell 7.1에는 PSReadLine 2.1.0도 포함되어 있습니다. 이 버전은 예측 IntelliSense를 포함합니다. 예측 IntelliSense 기능에 대한 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/)를 참조하세요.

## <a name="where-can-i-install-powershell"></a>PowerShell은 어디에 설치할 수 있나요?

<!-- TODO: Update list of OS below - make sure this is consistent across all docs -->

PowerShell 7.1은 현재 다음과 같은 x64 운영 체제를 지원합니다.

- Windows 8.1/10(ARM64 포함)
- Windows Server 2012 R2, 2016, 2019 및 SAC(반기 채널)
- Ubuntu 16.04/18.04/20.04(ARM64 포함)
- Ubuntu 19.10(맞춤 패키지를 통해)
- Debian 9/10
- CentOS 및 RHEL 7/8
- Fedora 32
- Alpine 3.11+(ARM64 포함)
- macOS 10.13 이상 버전

또한 다음에 대한 커뮤니티 지원도 제공합니다.

- Arch Linux
- Raspbian Linux
- Kali Linux

지원되는 운영 체제 및 지원 주기에 대한 최신 정보는 [PowerShell 지원 수명 주기](/powershell/scripting/powershell-support-lifecycle)를 참조하세요.

PowerShell 7.1이 Microsoft Store에 게시되었습니다. 이 PowerShell 릴리스는 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 웹 사이트 또는 Windows의 Microsoft Store 애플리케이션에서 찾을 수 있습니다.

Microsoft Store 패키지의 이점:

- Windows 10에 바로 기본 제공되는 자동 업데이트
- Intune 및 SCCM과 같은 기타 소프트웨어 배포 메커니즘과 통합

> [!NOTE]
> `$PSHOME`에 저장된 시스템 수준 구성 설정은 수정할 수 없습니다. 여기에는 WSMAN 구성이 포함됩니다. 그러므로 원격 세션에서 PowerShell의 저장소 기반 설치에 연결할 수 없습니다. 사용자 수준 구성 및 SSH 원격 기능을 지원합니다.

기본 운영 체제에 대한 설치 지침을 확인하세요.

- [Windows](/powershell/scripting/install/installing-powershell-core-on-windows)
- [macOS](/powershell/scripting/install/installing-powershell-core-on-macos)
- [Linux](/powershell/scripting/install/installing-powershell-core-on-linux)

또한 PowerShell 7.1은 Debian, Ubuntu 및 ARM64 Alpine Linux의 ARM32 및 ARM64 버전을 지원합니다.

공식적으로 지원되는 것은 아니지만 커뮤니티는 [Arch](https://aur.archlinux.org/packages/powershell/) 및 Kali Linux에 대한 패키지도 제공했습니다.

> [!NOTE]
> Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine, ARM은 현재 WinRM 원격 기능을 지원하지 않습니다. SSH 기반 원격을 설정하는 방법에 대한 자세한 내용은 [SSH를 통한 PowerShell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조하세요.

## <a name="running-powershell-71"></a>PowerShell 7.1 실행

PowerShell 7.1은 새 디렉터리에 설치되고 Windows PowerShell 5.1과 함께 실행됩니다.
PowerShell 7.1은 PowerShell 6.x 또는 PowerShell 7.0을 대체하는 현재 위치 업그레이드입니다.

- PowerShell 7.1은 `%programfiles%\PowerShell\7`에 설치됩니다.
- `%programfiles%\PowerShell\7` 폴더가 `$env:PATH`에 추가됩니다.

PowerShell 7.1 설치 관리자 패키지는 이전 버전의 PowerShell Core 6.x를 업그레이드합니다.

- Windows의 PowerShell Core 6.x: `%programfiles%\PowerShell\6`이 `%programfiles%\PowerShell\7`로 대체됩니다.
- Linux: `/opt/microsoft/powershell/6`이 `/opt/microsoft/powershell/7`로 대체됩니다.
- macOS: `/usr/local/microsoft/powershell/6`이 `/usr/local/microsoft/powershell/7`로 대체됩니다.

> [!NOTE]
> Windows PowerShell에서 PowerShell을 시작하는 실행 파일의 이름은 `powershell.exe`입니다. 버전 6 이상에서는 실행 파일이 병렬 실행을 지원하도록 변경되었습니다. PowerShell 7.1을 시작하는 새 실행 파일은 `pwsh.exe`입니다. 미리 보기 빌드는 7-preview 디렉터리 아래에 `pwsh` 대신 `pwsh-preview`로 그대로 유지됩니다.

## <a name="breaking-changes-and-improvements"></a>주요 변경 내용 및 개선 사항

변경 내용 및 향상된 기능에 대한 최신 정보는 GitHub 리포지토리에서 [변경 로그](https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG)를 참조하세요.

### <a name="breaking-changes"></a>주요 변경 내용

<!-- TODO: Add descriptions for each breaking change - this might need to be a separate article that we link to -->

- 네이티브 명령이 `stderr`에 쓸 때 `$false`가 되지 않도록 `$?` 수정(#13395)
- `Get-Date`에서 `-FromUnixTime` 이름을 `-UnixTimeSeconds`로 변경하여 Unix 시간 입력을 허용(#13084)(@aetos382에게 감사드립니다!)
- `$ErrorActionPreference`가 네이티브 명령의 `stderr` 출력에 영향을 주지 않도록 설정(#13361)
- 명시적으로 지정된 명명된 매개 변수가 해시 테이블 스플래팅의 동일한 매개 변수를 대체하도록 허용(#13162)
- 스위치 매개 변수 `-Qualifier`가 `Split-Path`에 대해 위치를 지정하지 않도록 설정(#12960)(@yecril71pl에게 감사드립니다!)
- 지정되지 않은 경우 작업 디렉터리를 `Start-Process`에 대한 리터럴 경로로 확인(#11946)(@NoMoreFood에게 감사드립니다!)
- 웹 cmdlet의 `-OutFile` 매개 변수가 `-LiteralPath`처럼 작동하도록 설정(#11701)(@iSazonov에게 감사드립니다!)
- `BigInteger` 숫자 리터럴에 대한 문자열 매개 변수 바인딩을 수정(#11634)(@vexx32에게 감사드립니다!)
- Windows에서 `Start-Process`는 현재 세션의 모든 환경 변수를 사용하여 프로세스 환경을 만들고, `-UseNewEnvironment`는 새 기본 프로세스 환경을 만듦(#10830)(@iSazonov에게 감사드립니다!)
- ScriptBlock을 대리자로 변환할 때 반환 결과를 `PSObject`로 래핑하지 않음(#10619)
- `-replace` 연산자에 대해 고정 문화권 문자열 변환을 사용(#10954)(@iSazonov에게 감사드립니다!)

### <a name="experimental-features"></a>실험적 기능

실험적 기능에 대한 자세한 내용은 [실험적 기능 사용](../learn/experimental-features.md)을 참조하세요.

- `PSNullConditionalOperators` 기능을 실험적 기능에서 제외(#13529)
- `PSUnixFileStat` 기능을 실험적 기능에서 제외
- `-Runspace` 매개 변수를 모든 `*-PSBreakpoint` cmdlet에 추가(#10492)(@KirkMunro에게 감사드립니다!)
- 네이티브 명령에 `PSPath`를 전달하도록 지원하기 위해 `PSNativePSPathResolution`을 추가(#12386)
- `-replace` 연산자에 대해 고정 문화권 문자열 변환을 사용(#10954)(@iSazonov에게 감사드립니다!)
- 향후 예측 IntelliSense 플러그 인을 지원하기 위해 `PSSubsystemPluginModel`을 추가

### <a name="general-cmdlet-updates-and-fixes"></a>일반 Cmdlet 업데이트 및 수정

- `ConvertTo-Json`이 `-Depth` 값을 초과하는 경우 경고를 표시(#13692)
- Windows에서 예외 메시지가 ``"`n"``만 포함하는 문제를 해결(#13684)
- `CONOUT$` 및 `CONIN$`을 예약된 디바이스 이름으로 인식(#13508)(@davidreis97에게 감사드립니다!)
- 오류를 쓸 때 대화형 고급 기능에 대해 `ConciseView`를 수정(#13623)
- 웹 cmdlet에서 `TLS` 1.3에 대한 지원을 추가(#13409)(@iSazonov에게 감사드립니다!)
- `CommandLineParser`에서 `args`에 대한 null 검사를 추가(#13451)(@iSazonov에게 감사드립니다!)
- Microsoft Store 애플리케이션에 대한 재분석 지점을 처리(#13481)(@iSazonov에게 감사드립니다!)
- 컨테이너에 대한 PowerShell Direct를 사용할 때 `ObRoot`에 대한 속성이 없는 경우 필드를 사용(#13375)(@hemisphera에게 감사드립니다!)
- 사용되지 않는 `UTF-7` 경고를 표시하지 않음(#13484)
- `Compiler.cs`에서 `IEnumerable<Expression>` 인스턴스의 다중 열거형을 사용하지 않음(#13491)
- `ConsoleApplication` 및 `WindowsApplication`을 지원하지 않도록 `Add-Type -OutputType`을 변경(#13440)
- `UTF-7`가 인코딩으로 지정된 경우 경고 만들기(#13430)
- 새 바로 가기 링크 누락 대상의 오류 메시지를 수정(#13085)(@yecril71pl에게 감사드립니다!)
- 공용 `ConsoleHost` API에서 `args` 매개 변수가 null을 허용하지 않도록 설정(#13429)
- `CancellationTokenSource`에 대해 누락된 Dispose를 추가(#13420)(@Youssef1313에게 감사드립니다!)
- 매개 변수가 와일드 카드를 지원하는지 여부를 제대로 표시하지 않는 `Get-Help`를 수정(#13353)(@ThomasNieto에게 감사드립니다!)
- `-InputFormat` 매개 변수에 대한 `pwsh` 도움말을 업데이트(#13355)(@sethvs에게 감사드립니다!)
- Roslyn에서 복사한 파일에 대해 MIT 라이선스를 선언(#13305)(@xtqqczze에게 감사드립니다!)
- `BigInteger` 캐스팅 동작을 개선(#12629)(@vexx32에게 감사드립니다!)
- `Get-Acl -LiteralPath "HKLM:Software\Classes\*"` 동작을 수정(#13107)(@Shriram0908에게 감사드립니다!)
- 방문자 인터페이스 및 클래스에 `DefaultVisit` 메서드를 추가(#13258)
- `pwsh`에 대해 충돌하는 축약형 스위치 `-s`(STA)를 수정(#13262)(@iSazonov에게 감사드립니다!)
- 기존 `SecureString` 경로를 사용하지만 일반 텍스트로 반환하도록 `Read-Host -MaskInput`을 변경(#13256)
- 이제 .NET 5.0에서 `IEnumerator`를 사용하는 COM 개체가 지원되므로 `ComEnumerator`를 제거(#13259)
- 'HOME' 환경 변수가 정의되지 않은 경우 Runspace 시작 시 임시 개인 경로를 사용(#13239)
- 동일한 기록 항목의 재귀 호출을 검색하도록 `Invoke-Command`를 수정(#13197)
- `-interactive`와 충돌하는 문제를 해결하기 위해 `pwsh` 실행 파일 `-inputformat` 스위치 접두사 `-in`을 `-inp`로 변경(#13205)(@iSazonov에게 감사드립니다!)
- 파일의 보안 영역을 분석할 때 WSL 파일 시스템 경로를 처리(#13120)
- `Split-Path`에서 다른 스위치를 필수로 설정(#13150)(@kvprasoon에게 감사드립니다!)
- PowerShell 7용 새 흐름 디자인 아이콘(#13100)(@sarthakmalik에게 감사드립니다!)
- Unix에서 교차 탑재 이동을 지원하도록 `Move-Item`을 수정(#13044)
- `CommandSearcher.GetNextCmdlet`에서 `NullReferenceException`을 수정(#12659)(@powercode에게 감사드립니다!)
- 테스트 후크가 활성화된 Unix 컴퓨터 cmdlet에서 `NullReferenceException`을 방지(#12651)(@vexx32에게 감사드립니다!)
- `Select-Object`에서 `Hashtable` 멤버(예: `Keys`)를 `-Property` 또는 `-ExpandProperty`와 함께 사용할 수 없는 문제를 해결(#11097)(@vexx32에게 감사드립니다!)
- Pwsh에서 충돌하는 축약형 스위치 `-w`를 수정(#12945)
- `CimCmdlet` 리소스 파일의 이름을 변경(#12955)(@iSazonov에게 감사드립니다!)
- `ConciseView`에서 `Test-Path` 사용을 제거(#12778)
- `default` 스위치 문 조건 절을 키워드로 플래그 지정(#10487)(@msftrncs에게 감사드립니다!)
- `Test-Json` cmdlet에 `SchemaFile` 매개 변수를 추가(#11934)(@beatcracker에게 감사드립니다!)
- 인증서 공급자 매개 변수를 다시 사용(#10622)(@iSazonov에게 감사드립니다!)
- 상대 경로 대상에 대한 바로 가기 링크를 만들도록 `New-Item`를 수정(#12797)(@iSazonov에게 감사드립니다!)
- 프로세스에 `CommandLine` 속성을 추가(#12288)(@iSazonov에게 감사드립니다!)
- `Read-Host`에 `-MaskInput` 매개 변수를 추가(#10908)(@davinci26에게 감사드립니다!)
- `AliasAttribute`를 사용하도록 `CimCmdlets`를 변경(#12617)(@thlac에게 감사드립니다!)
- ParameterBinderBase의 형식 문자열에서 잘못된 인덱스를 수정(#12630)(@powercode에게 감사드립니다!)
- `Command.Clone()`에서 `CommandInfo` 속성을 복사(#12301)(@TylerLeonhardt에게 감사드립니다!)
- `-ExcludeDifferent`가 지정된 경우 `Compare-Object`에서 `-IncludeEqual`을 적용(#12317)(@davidseibel에게 감사드립니다!)
- 출력을 쓰기 전에 파일 핸들을 닫도록 `Get-FileHash`를 변경(#12474)(@HumanEquivalentUnit에게 감사드립니다!)
- `-replace` 연산자에서 일치하지 않는 예외 메시지를 수정(#12388)(@jackdcasey에게 감사드립니다!)
- 우선 순위가 높은 PowerShell 7 모듈을 처리하도록 `WinCompat` 모듈 로딩을 수정(#12269)
- `ForEach-Object -Parallel` Runspace 재사용을 구현(#12122)
- 열거하는 동안 컬렉션을 수정하지 않도록 `Get-Service`를 수정(#11851)(@NextTurn에게 감사드립니다!)
- PowerShell 종료 시 IPC 명명된 파이프 정리(#12187)
- 웹 cmdlet에서 `<img />` 검색 regex를 수정(#12099)(@vexx32에게 감사드립니다!)
- 적절한 형식 접미사를 사용하는 더 짧은 부호 있는 16진수 리터럴을 허용(#11844)(@vexx32에게 감사드립니다!)
- Windows에서 `Start-Process` cmdlet의 `UseNewEnvironment` 매개 변수 동작을 업데이트(#10830)(@iSazonov에게 감사드립니다!)
- `Get-Random` 명령에 `-Shuffle` 스위치를 추가(#11093)(@eugenesmlv에게 감사드립니다!)
- `GetWindowsPowerShellModulePath`를 다중 PS 설치와 호환되도록 설정(#12280)
- Windows PowerShell이 기본 셸로 등록되지 않은 시스템에서 작동하도록 `Start-Job`을 수정(#12296)
- 별칭을 지정하고 `Get-Command`를 `-Syntax`로 지정하면 별칭 명령 구문을 반환(#10784)(@ChrisLGardner에게 감사드립니다!)
- `-AsNeeded`를 사용할 때 완료되지 않은 행이 있더라도 CSV cmdlet이 작동하도록 설정(#12281)(@iSazonov에게 감사드립니다!)
- 로컬 호출에서 모든 형식 데이터를 표시하기 위해 `Get-FormatData`에 `-PowerShellVersion 5.1`이 필요하지 않습니다. (#11270)(@mklement0에게 감사드립니다!)
- Big Endian `UTF-32`에 대한 지원을 추가(#11947)(@NoMoreFood에게 감사드립니다!)
- `ForEach-Object -Parallel`에서 PowerShell 개체 Dispose를 누설하는 경합 가능성을 수정(#12227)
- Unix 시간 입력을 허용하기 위해 `Get-Date`에 `-FromUnixTime`을 추가(#12179)(@jackdcasey에게 감사드립니다!)
- 기본 진행률 전경색 및 배경색을 변경하여 향상된 대비를 제공(#11455)(@rkeithhill에게 감사드립니다!)
- 현재 드라이브를 사용할 수 없는 경우 `foreach -parallel`을 수정(#12197)
- `ScriptBlock`을 `delegate`로 변환할 때 반환 결과를 `PSObject`로 래핑하지 않음(#10619)
- `Test-Connection -Quiet`에서 DNS 확인 오류를 쓰지 않음(#12204)(@vexx32에게 감사드립니다!)
- out-of-proc 작업에 대한 자식 프로세스에서 리디렉션된 출력 및 오류 스트림을 읽을 때 전용 스레드를 사용(#11713)
- 바인더 코드에서 연산자 기본 설정 순서 문제를 수정(#12075)(@DamirAinullin에게 감사드립니다!)
- `ActionPreference` 형식의 공통 매개 변수를 바인딩하는 경우 `NullReferenceException`를 수정(#12124)
- 역직렬화된 `MatchInfo`의 기본 형식을 수정(#11728)(@iSazonov에게 감사드립니다!)
- `Invoke-RestMethod`에서 비동기 스트림을 사용(#11095)(@iSazonov에게 감사드립니다!)
- `Get-Content -Tail`에서 UTF-8 검색을 처리(#11899)(@NoMoreFood에게 감사드립니다!)
- `Get-FileHash`에서 `IOException`을 처리(#11944)(@iSazonov에게 감사드립니다!)
- 리소스 문자열에서 `PowerShell Core`를 `PowerShell`로 변경(#11928)(@alexandair에게 감사드립니다!)
- `PSHostProcessInfo`에서 `MainWindowTitle`을 다시 사용(#11885)(@iSazonov에게 감사드립니다!)
- Windows 호환성에 대한 기타 사소한 업데이트(#11980)
- `[Environment]::NewLine`을 사용하여 `PositionMessage`를 분할하도록 `ConciseView`를 수정(#12010)
- 대화형 세션에 대한 네트워크 홉 제한을 제거(#11920)
- `SuspendStoppingPipeline()` 및 `RestoreStoppingPipeline()`에서 `NullReferenceException`을 수정(#11870)(@iSazonov에게 감사드립니다!)
- 제공되지 않은 경우 `FormatViewDefinition` `InstanceId`에 대한 GUID를 생성(#11896)
- `ConciseView`에서 오류 메시지가 창 너비보다 넓고 공백이 없는 문제를 수정(#11880)
- 플랫폼 간 `CAPI-compatible` 원격 키 교환을 허용(#11185)(@silijon에게 감사드립니다!)
- 오류 메시지를 수정(#11862)(@NextTurn에게 감사드립니다!)
- 너비를 얻기 위한 콘솔이 없는 경우를 처리하도록 `ConciseView`를 수정(#11784)
- 인증서 공급자 대신 Microsoft Store를 사용하도록 `CmsCommands`를 업데이트(#11643)(@mikeTWC1984에게 감사드립니다!)
- `mpr.dll` 및 STA를 사용할 수 없는 Windows 시스템에서 작동하도록 `pwsh`를 설정(#11748)
- `Un*x` 및 macOS에 대해 `Restart-Computer`를 리팩터링 및 구현(#11319)
- Linux 및 macOS에 대한 `Stop-Computer` 구현을 추가(#11151)
- 사용 전에 `less`를 사용할 수 있는지 여부를 확인하도록 `help` 함수를 수정(#11737)
- `certificate_format_ps1.xml`에서 `PSPath`를 업데이트(#11603)(@xtqqczze에게 감사드립니다!)
- 링크 헤더에서 따옴표가 없는 관계 유형을 일치하도록 정규식을 변경(#11711)(@Marusyk에게 감사드립니다!)
- 바로 가기 링크 삭제 중 오류 메시지를 수정(#11331)
- `Select-Object`의 `PSCustomObject`에 사용자 지정 `Selected.*` 형식을 한 번만 추가(#11548)(@iSazonov에게 감사드립니다!)
- `Get-Date` cmdlet에 `-AsUTC`를 추가(#11611)
- `Format-Hex`에서 부울 값을 사용하여 그룹화 동작을 수정(#11587)(@vexx32에게 감사드립니다!)
- `Test-Connection`가 ping 요청을 보낼 때 항상 기본 동기화 컨텍스트를 보내도록 설정(#11517)
- 시작 오류 메시지를 수정(#11473)(@iSazonov에게 감사드립니다!)
- 웹 cmdlet에서 null 값이 있는 헤더를 무시(#11424)(@iSazonov에게 감사드립니다!)
- `Invoke-Command` 작업 Dispose에 대한 검사를 다시 추가합니다. (#11388)
- "콘텐츠가 비어 있는 경우 새 줄을 쓰도록 포맷터를 업데이트(#11193)"를 되돌림(#11342)(@iSazonov에게 감사드립니다!)
- `AST` 또는 스크립트에 일치하는 함수 정의가 있는 경우 `CompleteInput`이 `ArgumentCompleter`의 결과를 반환하도록 허용(#10574)(@M1kep에게 감사드립니다!)
- 콘텐츠가 비어 있는 경우 새 줄을 쓰지 않도록 포맷터를 업데이트(#11193)

<!-- TODO: add more general contributor thank you listing -->
