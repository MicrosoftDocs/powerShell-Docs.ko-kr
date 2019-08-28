---
title: PowerShell Core 6.0의 새로운 기능
description: PowerShell Core 6.0에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 08/06/2018
ms.openlocfilehash: e1218a38398f4d86829cf2b4ba6a3a882675eaab
ms.sourcegitcommit: 09f02ccef56ef30e7a9ca901f8d3713724960c68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843925"
---
# <a name="whats-new-in-powershell-core-60"></a>PowerShell Core 6.0의 새로운 기능

[PowerShell Core 6.0][github]은 PowerShell의 새로운 버전으로, 크로스 플랫폼(Windows, macOS 및 Linux)이자 오픈 소스이며 다른 유형의 환경 및 하이브리드 클라우드용으로 빌드되었습니다.

## <a name="moved-from-net-framework-to-net-core"></a>.NET Framework에서 .NET Core로 이동됨

PowerShell Core는 [.NET Core 2.0][]을 런타임으로 사용합니다.
.NET Core 2.0을 사용하면 PowerShell Core가 여러 플랫폼(Windows, macOS 및 Linux)에서 작동할 수 있습니다.
또한 PowerShell Core는 PowerShell cmdlet 및 스크립트에서 사용하도록 .NET Core 2.0에서 제공하는 API 집합을 노출합니다.

Windows PowerShell은 .NET Framework 런타임을 사용하여 PowerShell 엔진을 호스팅합니다.
즉, Windows PowerShell은 .NET Framework에서 제공하는 API 집합을 노출합니다.

.NET Core와 .NET Framework 간에서 공유된 API는 [.NET Standard][]의 일부로 정의됩니다.

이것이 PowerShell Core와 Windows PowerShell 간의 모듈/스크립트 호환성에 미치는 영향에 대한 자세한 내용은 [Windows PowerShell 이전 버전과의 호환성](#backwards-compatibility-with-windows-powershell).

## <a name="support-for-macos-and-linux"></a>macOS 및 Linux 지원

PowerShell은 이제 다음을 포함하여 공식적으로 macOS 및 Linux를 지원합니다.

- Windows 7, 8.1, 10
- Windows Server 2008 R2, 2012 R2, 2016
- [Windows Server 반기 채널][semi-annual]
- Ubuntu 14.04, 16.04, 17.04
- Debian 8.7+, 9
- CentOS 7
- Red Hat Enterprise Linux 7
- OpenSUSE 42.2
- Fedora 25, 26
- macOS 10.12+

또한 커뮤니티에서 다음 플랫폼과 관련한 패키지를 제공하였으나 공식적으로 지원되지는 않습니다.

- Arch Linux
- Kali Linux
- AppImage(여러 Linux 플랫폼에서 사용)

또한 다음 플랫폼에 대해 실험적(지원되지 않는) 릴리스도 있습니다.

- Windows on ARM32/ARM64
- Raspbian(Stretch)

비 Windows 시스템에서 잘 작동하도록 PowerShell Core 6.0에서 여러 가지가 변경되었습니다.
이들 중 일부는 Windows에 영향을 주는 주요 변경 내용입니다.
다른 변경 사항은 비 Windows에 PowerShell Core가 설치된 경우에만 제공되거나 적용할 수 있습니다.

- Unix 플랫폼에서 기본 명령 와일드 카드 사용 지원이 추가되었습니다.
- `more` 기능은 Linux `$PAGER`를 따르며 기본값은 `less`입니다.
  즉, 네이티브 바이너리/명령(예: `ls *.txt`)과 함께 와일드 카드를 사용할 수 있습니다. (#3463)
- 네이티브 명령 인수를 처리할 때 후행 백슬래시가 자동으로 이스케이프됩니다. (#4965)
- 현재 스크립트 서명이 지원되지 않기 때문에 Windows 이외의 플랫폼에서 PowerShell을 실행할 때 `-ExecutionPolicy` 스위치를 무시합니다. (#3481)
- Unix 플랫폼에서 `NoEcho`를 지원하기 위해 ConsoleHost가 수정되었습니다. (#3801)
- Unix 플랫폼에서 대/소문자를 구분하지 않는 패턴 일치를 지원하도록 `Get-Help`가 수정되었습니다. (#3852)
- 패키지에 `powershell` man-page 추가됨

### <a name="logging"></a>로깅

macOS에서 PowerShell은 기본 `os_log` API를 사용하여 Apple의 [통합 로깅 시스템][os_log]에 로깅합니다.
Linux에서 PowerShell은 유비쿼터스 로깅 솔루션인 [Syslog][]를 사용합니다.

### <a name="filesystem"></a>파일 시스템

Windows에서 일반적으로 지원되지 않는 파일 이름 문자를 지원하도록 macOS 및 Linux에서 많은 변경이 이루어졌습니다.

- cmdlet에 지정된 경로는 이제 슬래시를 구분하지 않습니다(/ 및 \ 모두 디렉터리 구분 기호로 사용).
- 기본적으로 이제 XDG 기본 디렉터리 지정이 적용되고 사용됩니다.
  - Linux/macOS 프로필 경로는 `~/.config/powershell/profile.ps1`에 있습니다.
  - 기록 저장 경로는 `~/.local/share/powershell/PSReadline/ConsoleHost_history.txt`에 있습니다.
  - 사용자 모듈 경로는 `~/.local/share/powershell/Modules`에 있습니다.
- Unix에서 콜론 문자가 포함된 파일 및 폴더 이름을 지원합니다. (#4959)
- 스크립트 이름이나 콤마가 포함된 전체 경로를 지원합니다. (#4136) ([@TimCurwick](https://github.com/TimCurwick)에게 감사드립니다!)
- 탐색 cmdlet의 와일드 카드를 확장하지 않기 위해 `-LiteralPath`를 사용할 때 검색합니다. (#5038)
- *nix `ls -R` 및 Windows `DIR /S` 네이티브 명령 등을 실행하도록 `Get-ChildItem`이 업데이트되었습니다.
  `Get-ChildItem`은 재귀 검색 중에 발견된 심볼릭 링크를 반환하고 대상과 연결되는 디렉터리를 검색하지 않습니다. (#3780)

### <a name="case-sensitivity"></a>대/소문자 구분

Linux와 macOS는 대/소문자를 구분하지만 Windows는 대/소문자를 유지하면서 대/소문자를 구분하지 않습니다.
일반적으로 PowerShell은 대/소문자를 구분하지 않습니다.

예를 들어, 환경 변수는 macOS 및 Linux에서 대/소문자를 구분하므로 `PSModulePath` 환경 변수의 대/소문자가 표준화되었습니다. (# 3255) `Import-Module`은 파일 경로를 사용하여 모듈의 이름을 구분할 때 대/소문자를 구분하지 않습니다. (#5097)

## <a name="support-for-side-by-side-installations"></a>병렬 설치 지원

PowerShell Core는 Windows PowerShell과 별도로 설치, 구성 및 실행됩니다.
PowerShell Core에는 "휴대용" ZIP 패키지가 있습니다.
ZIP 패키지를 사용하면 PowerShell을 종속 요소로 사용하는 애플리케이션에 로컬로 설치하는 등 디스크의 어느 위치에나 원하는 버전을 설치할 수 있습니다.
병렬 설치를 통해 새로운 버전의 PowerShell을 쉽게 테스트하고 기존 스크립트를 시간에 따라 마이그레이션할 수 있습니다
병렬 설치는 또한 스크립트가 필요로 하는 특정 버전에 고정될 수 있으므로 이전 버전과의 호환될 수 있습니다.

> [!NOTE]
> 기본적으로 Windows의 MSI 기반 설치 관리자는 적절한 업데이트 설치를 수행합니다.
>

## <a name="renamed-powershellexe-to-pwshexe"></a>`powershell(.exe)`에서 `pwsh(.exe)`로 이름이 변경됨

PowerShell Core의 이진 이름이 `powershell(.exe)`에서 `pwsh(.exe)`로 변경되었습니다.
이 변경은 사용자가 Windows PowerShell 및 PowerShell Core의 병렬 설치를 지원하는 컴퓨터에서 사용자가 PowerShell Core를 실행할 수 있는 결정적인 방법을 제공합니다.
`pwsh`는 또한 훨씬 짧고 쉽게 입력할 수 있습니다.

`powershell.exe`에서 `pwsh(.exe)`로의 추가 변경 사항:

- 첫 번째 위치 매개 변수를 `-Command`에서 `-File`로 변경했습니다.
  이 변경 사항은 Windows 이외의 플랫폼에서 PowerShell이 아닌 셸에서 실행되는 PowerShell 스크립트에서 `#!`의 사용(즉, shebang)을 수정합니다.
  또한 `-File`을 지정하지 않고 `pwsh foo.ps1` 또는 `pwsh fooScript`와 같은 명령을 실행할 수 있음을 의미합니다.
  그러나 이 변경 사항은 `pwsh.exe -Command Get-Command`와 같은 명령을 실행하려고 할 때 `-c` 또는 `-Command`을 명시적으로 지정해야 합니다. (#4019)
- PowerShell Core는 대화형 셸을 나타내기 위해 `-i`(또는 `-Interactive`) 스위치를 허용합니다. (# 3558) 이렇게 하면 Unix 플랫폼에서 PowerShell을 기본 셸로 사용할 수 있습니다.
- `pwsh.exe`에서 매개 변수 `-importsystemmodules` 및 `-psconsoleFile`을 제거했습니다. (#4995)
- `pwsh -version`과 기본 제공 도움말 `pwsh.exe`이 다른 네이티브 도구와 일치하도록 변경되었습니다. (#4958 & #4931) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- `-File` 및 `-Command`에 대한 잘못된 인수 오류 메시지 및 Unix 표준과 일치하는 종료 코드 (#4573)
- Windows에 `-WindowStyle` 매개 변수가 추가되었습니다. (# 4573) 마찬가지로 Windows 이외의 플랫폼에서 패키지 기반 설치 업데이트가 적절한 업데이트입니다.

## <a name="backwards-compatibility-with-windows-powershell"></a>이전 버전 Windows PowerShell과의 호환성

PowerShell Core의 목표는 가능한 한 Windows PowerShell과 호환을 유지하는 것입니다.
PowerShell Core는 [.NET Standard][] 2.0을 사용하여 기존 .NET 어셈블리와 이진 호환성을 제공합니다.
많은 PowerShell 모듈이 이러한 어셈블리(종종 DLL)에 의존하기 때문에 .NET Standard는 .NET Core를 사용하여 계속 작업할 수 있습니다.
또한 PowerShell Core에는 일반적으로 전역 어셈블리 캐시가 디스크에 있는 것처럼 잘 알려진 폴더를 검색하여 .NET Framework DLL 종속성을 찾는 추론 기능이 포함되어 있습니다.

[.NET Blog][], 이 [YouTube][] 비디오 및 GitHub의 이 [FAQ][]에서 .NET Standard에 대해 자세히 알 수 있습니다.

PowerShell 언어와 "기본 제공" 모듈(`Microsoft.PowerShell.Management`, `Microsoft.PowerShell.Utility` 등)이 Windows PowerShell에서와 동일하게 작동하도록 최선의 노력이 기울여 왔습니다.
많은 경우 커뮤니티의 도움을 받아 해당 cmdlet에 새로운 기능과 버그 수정이 추가되었습니다.
경우에 따라 기본 .NET 계층의 종속성이 없어서 기능이 제거되었거나 사용할 수 없습니다.

Windows의 일부로 제공되는 대부분의 모듈(예: `DnsClient`, `Hyper-V`, `NetTCPIP`, `Storage` 등) 및 Azure 및 Office를 포함한 기타 Microsoft 제품은 *명시적으로* .NET Core로 아직 포팅되지 않았습니다.
PowerShell 팀은 이러한 제품 그룹 및 팀과 협력하여 기존 모듈의 유효성을 확인하고 PowerShell 코어로 포팅합니다.
.NET Standard 및 [CDXML][]을 사용하면 이러한 기존의 Windows PowerShell 모듈 중 상당수가 PowerShell Core에서 작동하는 것처럼 보이지만, 공식적으로 유효성이 검사되지 않았을 뿐만 아니라 공식적으로 지원되지 않습니다.

[`WindowsPSModulePath`][windowspsmodulepath] 모듈을 설치하면 Windows PowerShell `PSModulePath`를 PowerShell Core `PSModulePath`에 추가하여 Windows PowerShell 모듈을 사용할 수 있습니다.

먼저 PowerShell 갤러리에서 `WindowsPSModulePath` 모듈을 설치합니다.

```powershell
# Add `-Scope CurrentUser` if you're installing as non-admin
Install-Module WindowsPSModulePath -Force
```

이 모듈이 설치되면, `Add-WindowsPSModulePath` cmdlet을 실행하여 Windows PowerShell `PSModulePath`를 PowerShell Core에 추가합니다.

```powershell
# Add this line to your profile if you always want Windows PowerShell PSModulePath
Add-WindowsPSModulePath
```

## <a name="docker-support"></a>Docker 지원

PowerShell Core는 지원하는 모든 주요 플랫폼(여러 Linux 배포판, Windows Server Core 및 Nano 서버 포함)에 대한 Docker 컨테이너 지원을 추가합니다.

전체 목록을 보려면 [`microsoft/powershell`Docker Hub][docker-hub]에 있는 태그를 확인합니다.
Docker 및 PowerShell Core에 대한 자세한 내용은 GitHub의 [Docker][]를 참조하세요.

## <a name="ssh-based-powershell-remoting"></a>SSH 기반 PowerShell 원격

PowerShell Remoting Protocol(PSRP)은 이제 기존 WinRM 기반 PSRP 외에도 Secure Shell(SSH) 프로토콜과도 함께 작동합니다.

즉, `Enter-PSSession` 및 `New-PSSession`와 같은 cmdlet을 사용하고 SSH를 사용하여 인증할 수 있습니다.
OpenSSH 기반 SSH 서버를 사용하여 PowerShell을 서브 시스템으로 등록하면, 기존의 `PSSession` 의미 체계와 함께 기존 SSH 기반 인증 메커니즘(암호 또는 프라이빗 키 등)을 사용할 수 있습니다.

SSH 기반 원격 구성 및 사용에 대한 자세한 내용은 [SSH를 통한 PowerShell 원격][ssh-remoting]을 참조하세요.

## <a name="default-encoding-is-utf-8-without-a-bom-except-for-new-modulemanifest"></a>New-ModuleManifest를 제외하고는 기본 인코딩은 BOM이 없는 UTF-8

과거에는 `Get-Content`, `Set-Content`와 같은 Windows PowerShell cmdlet에서 ASCII 및 UTF-16 등 다른 인코딩을 사용했습니다.
인코딩 기본값을 변경하면 인코딩을 지정하지 않고 cmdlet을 혼합할 때 문제가 발생했습니다.

Windows 이외의 플랫폼에서는 텍스트 파일의 기본 인코딩으로 BOM(Byte Order Mark)이 없는 UTF-8을 일반적으로 사용합니다.
점점 많은 Windows 애플리케이션과 도구가 UTF-16에서 BOM 없는 UTF-8 인코딩으로 이동하고 있습니다.
PowerShell Core는 보다 넓은 에코시스템을 준수하도록 기본 인코딩을 변경합니다.

즉, `-Encoding` 매개 변수를 사용하는 모든 기본 제공 cmdlet은 기본적으로 `UTF8NoBOM` 값을 사용합니다.
다음 cmdlet가 이러한 변경에 의해 영향을 받습니다.

- Add-Content
- Export-Clixml
- Export-Csv
- Export-PSSession
- Format-Hex
- Get-Content
- Import-Csv
- Out-File
- Select-String
- Send-MailMessage
- Set-Content

이러한 cmdlet도 업데이트되어 `-Encoding` 매개 변수가 보편적으로 `System.Text.Encoding`을 허용합니다.

`$OutputEncoding`의 기본값도 UTF-8로 변경되었습니다.

가장 좋은 방법은 `-Encoding` 매개 변수를 사용하여 스크립트에서 인코딩을 명시적으로 설정하여 플랫폼 간의 결정적 동작을 생성하는 것입니다.

`New-ModuleManifest` cmdlet에는 **인코딩** 매개 변수가 없습니다. `New-ModuleManifest` cmdlet을 사용하여 만든 모듈 매니페스트(.psd1) 파일의 인코딩은 환경에 따라 다릅니다. 즉, Linux에서 실행되는 PowerShell Core인 경우 인코딩은 UTF-8(BOM 없음)이며, 그렇지 않은 경우 인코딩은 UTF-16(BOM 포함)입니다. (#3940)

## <a name="support-backgrounding-of-pipelines-with-ampersand--3360"></a>앰퍼샌드(`&`)를 사용하여 파이프라인의 백그라운드 지원 (#3360)

파이프라인 끝에 `&`을 배치하면 파이프라인이 PowerShell 작업으로 실행됩니다.
파이프라인이 백그라운드로 설정되면 작업 개체가 반환됩니다.
일단 파이프라인이 작업으로 실행되면 모든 표준 `*-Job` cmdlet을 사용하여 작업을 관리할 수 있습니다.
파이프라인에서 사용되는 변수(프로세스별 변수 무시)는 작업에 자동으로 복사되므로 `Copy-Item $foo $bar &`가 작동합니다.
작업은 또한 사용자의 홈 디렉터리가 아닌 현재 디렉터리에서 실행됩니다.
PowerShell 작업에 대한 자세한 내용은 [about_Jobs](https://msdn.microsoft.com/powershell/reference/6/about/about_jobs)를 참조하세요.

## <a name="semantic-versioning"></a>유의적 버전 사용

- `SemVer 2.0`와 호환되도록 `SemanticVersion`을 만들었습니다. (#5037) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- SemVer와 일치하도록 `New-ModuleManifest`의 기본값 `ModuleVersion`을 `0.0.1`로 변경했습니다. (#4842) ([@LDSpits](https://github.com/LDSpits)에게 감사드립니다.)
- `semver`을 `System.Management.Automation.SemanticVersion`의 유형 가속기로 추가했습니다. (#4142) ([@oising](https://github.com/oising)에게 감사드립니다!)
- `Major` 및 `Minor` 버전 값으로만 구성된 `SemanticVersion` 인스턴스와 `Version` 인스턴스 간의 비교가 가능합니다.

## <a name="language-updates"></a>언어 업데이트

- 사용자가 유니코드 문자를 인수, 문자열 또는 변수 이름으로 사용할 수 있도록 유니코드 이스케이프 구문 분석을 구현합니다. (#3958) ([@rkeithhill](https://github.com/rkeithhill)에게 감사드립니다!)
- ESC: `` `e``를 위한 새로운 이스케이프 문자 추가됨
- 열거형을 문자열로 변환하기 위한 지원 추가됨(#4318) ([@KirkMunro](https://github.com/KirkMunro)에게 감사드립니다.)
- 단일 요소 배열을 일반 컬렉션에 캐스팅되는 현상 수정됨 (#3170)
- 문자 범위 오버로드가 `..` 연산자에 추가되어 `'a'..'z'`는 'a'에서 'z'로 문자를 반환합니다. (#5026) ([@IISResetMe](https://github.com/IISResetMe)에게 감사드립니다!)
- 읽기 전용 변수를 덮어 쓰지 않도록 변수 할당 수정됨
- 스크립트 cmdlet를 도팅할 때 자동 변수의 로컬을 'DottedScopes'에 밀어넣기 (#4709)
- 분할 연산자에서 ‘Singleline, Multiline’ 옵션 사용 가능(#4721) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다.)

## <a name="engine-updates"></a>엔진 업데이트

- `$PSVersionTable`에는 다음과 같이 4개의 새로운 속성이 있습니다.
  - `PSEdition`: PowerShell Core에서는 `Core`로 설정되고 Windows PowerShell에서는 `Desktop`으로 설정됩니다.
  - `GitCommitId`: PowerShell이 빌드된 Git 분기 또는 태그의 Git 커밋 ID입니다.
    릴리스된 빌드에서는 `PSVersion`과 동일할 가능성이 높습니다.
  - `OS`: `[System.Runtime.InteropServices.RuntimeInformation]::OSDescription`에 의해 반환된 OS 버전 문자열입니다.
  - `Platform`: `[System.Environment]::OSVersion.Platform`에 의해 반환됩니다. Windows에서는 `Win32NT`, macOS에서는 `Unix`, Linux에서는 `Unix`로 설정됩니다.
- `$PSVersionTable`에서 `BuildVersion` 속성이 제거되었습니다.
  이 속성은 Windows 빌드 버전과 강하게 연결되어 있습니다.
  대신 `GitCommitId`를 사용하여 PowerShell Core의 정확한 빌드 버전을 검색하는 것이 좋습니다. (#3877) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- `$PSVersionTable`에서 `ClrVersion` 속성을 제거합니다.
  이 속성은 .NET Core와는 관련이 없으며 PowerShell에 적용할 수 없는 특정 레거시 용도로만 .NET Core에 유지되었습니다.
- PowerShell이 주어진 OS(`$IsWindows`, `$IsMacOs` 및 `$IsLinux`)에서 실행 중인지 여부를 결정하는 세 가지 새로운 자동 변수가 추가되었습니다.
- PowerShell Core 배너에 `GitCommitId`를 추가합니다.
  이제 버전을 얻기 위해 PowerShell을 시작하자마자 `$PSVersionTable`을 실행할 필요가 없습니다! (#3916) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- `$PSHome`에 `powershell.config.json`이라는 JSON 구성 파일을 추가하여 시작 시간(예: `ExecutionPolicy`) 이전에 필요한 일부 설정을 저장합니다.
- Windows EXE를 실행할 때 파이프라인을 차단하지 않음
- COM 컬렉션의 열거를 사용했습니다. (#4553)

## <a name="cmdlet-updates"></a>cmdlet 업데이트

### <a name="new-cmdlets"></a>새로운 cmdlet

- `Get-Uptime`을 `Microsoft.PowerShell.Utility`에 추가합니다.
- `Remove-Alias` 명령을 추가합니다. (#5143) ([@PowershellNinja](https://github.com/PowershellNinja)에게 감사드립니다!)
- `Remove-Service`를 관리 모듈에 추가합니다. (#4858) ([@joandrsn](https://github.com/joandrsn)에게 감사드립니다!)

### <a name="web-cmdlets"></a>웹 cmdlet

- 웹 cmdlet에 대한 인증서 인증 지원을 추가합니다. (#4646) ([@markekraus](https://github.com/markekraus)에게 감사드립니다.)
- 웹 cmdlet에 콘텐츠 헤더 지원을 추가합니다. (#4494 & #4640) ([@markekraus](https://github.com/markekraus)에게 감사드립니다.)
- 웹 cmdlet에 다중 링크 헤더 지원을 추가합니다. (#5265) ([@markekraus](https://github.com/markekraus)에게 감사드립니다!)
- 웹 cmdlet의 링크 헤더 페이지 매김 지원 (#3828)
  - `Invoke-WebRequest`의 경우, 응답에 링크 헤더가 포함될 때 URL 및 `rel` 특성을 나타내는 사전으로 RelationLink 속성을 만들고 개발자가 쉽게 사용할 수 있도록 URL이 절대적인지 확인합니다.
  - `Invoke-RestMethod`의 경우, 응답에 링크 헤더가 포함될 때 더 이상 존재하지 않거나 선택적 `-MaximumFollowRelLink` 매개 변수 값에 도달할 때까지 자동으로 `next` `rel` 링크를 따라가는 `-FollowRelLink` 스위치가 노출됩니다.
- 웹 cmdlet에 `-CustomMethod` 매개 변수를 추가하여 비표준 메서드 동사를 허용합니다. (#3142) ([@Lee303](https://github.com/Lee303)에게 감사드립니다!)
- 웹 cmdlet에 `SslProtocol` 지원을 추가합니다. (#5329) ([@markekraus](https://github.com/markekraus)에게 감사드립니다!)
- 웹 cmdlet에 Multipart 지원을 추가합니다. (#4782) ([@markekraus](https://github.com/markekraus)에게 감사드립니다.)
- 웹 cmdlet에 `-NoProxy`를 추가하여 시스템 수준의 프록시 설정을 무시합니다. (#3447) ([@TheFlyingCorpse](https://github.com/TheFlyingCorpse)에게 감사드립니다!)
- 웹 cmdlet의 사용자 에이전트가 이제 OS 플랫폼을 보고합니다. (#4937) ([@LDSpits](https://github.com/LDSpits)에게 감사드립니다.)
- 웹 cmdlet에 `-SkipHeaderValidation` 스위치를 추가하여 헤더 값의 유효성을 검사하지 않고 헤더 추가를 지원합니다. (#4085)
- 필요한 경우 웹 cmdlet이 서버의 HTTPS 인증서의 유효성을 검사하지 않도록 설정합니다.
- 웹 cmdlet에 인증 매개 변수를 추가합니다. (#5052) ([@markekraus](https://github.com/markekraus)에게 감사드립니다.)
  - `-Authentication`을 추가합니다. 이 매개 변수는 기본, OAuth 및 전달자 옵션을 제공합니다.
  - `-Token`을 추가하여 OAuth 및 전달자 옵션에 대한 전달자 토큰을 가져옵니다.
  - HTTPS 이외의 전송 체계에 제공된 인증을 생략하려면 `-AllowUnencryptedAuthentication`을 추가합니다.
- 응답 헤더 캡처를 사용하려면 `-ResponseHeadersVariable`을 `Invoke-RestMethod`에 추가합니다. (#4888) ([@markekraus](https://github.com/markekraus)에게 감사드립니다.)
- 응답 상태 코드가 성공적이지 않은 경우 예외에 HTTP 응답을 포함하도록 웹 cmdlet을 수정합니다. (#3201)
- 웹 cmdlet `UserAgent`를 `WindowsPowerShell`에서 `PowerShell`로 변경합니다. (#4914) ([@markekraus](https://github.com/markekraus)에게 감사드립니다.)
- 명시적 `ContentType` 검색을 `Invoke-RestMethod`에 추가합니다. (#4692)
- 비표준 사용자 에이전트 헤더에서 작동하도록 웹 cmdlet `-SkipHeaderValidation`을 수정합니다. (#4479 & #4512) ([@markekraus](https://github.com/markekraus)에게 감사드립니다.)

### <a name="json-cmdlets"></a>JSON cmdlet

- `-AsHashtable`을 `ConvertFrom-Json`에 추가하여 `Hashtable`을 대신 반환합니다. (#5043) ([@bergmeister](https://github.com/bergmeister)에게 감사드립니다!)
- `ConvertTo-Json` 출력과 함께 더 보기 좋은 포맷터를 사용합니다. (#2787) (@kittholland에게 감사드립니다!)
- `Jobject` 직렬화 지원을 `ConvertTo-Json`에 추가합니다. (#5141)
- `ConvertFrom-Json`을 수정하여 완전한 JSON 문자열을 함께 구성하는 파이프라인에서 문자열 배열을 역직렬화합니다.
  이렇게 하면 줄 바꿈이 JSON 구문 분석을 중단시키는 일부 경우가 수정됩니다. (#3823)
- `System.Array`에 대해 정의된 `AliasProperty "Count"`를 제거합니다.
  이렇게 하면 일부 `ConvertFrom-Json` 출력에서 불필요한 `Count` 속성이 제거됩니다. (#3231) ([@PetSerAl](https://github.com/PetSerAl)에게 감사드립니다!)

### <a name="csv-cmdlets"></a>CSV cmdlet

- `Import-Csv`는 이제 W3C 확장 로그 파일 형식(#2482)을 지원합니다([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- `Import-Csv` 및 `ConvertFrom-Csv`에 대한 `PSTypeName` 지원을 추가합니다. (#5389) ([@markekraus](https://github.com/markekraus)에게 감사드립니다!)
- `Import-Csv`를 `CR`, `LF` 및 `CRLF`를 줄 구분 기호로 지원하도록 합니다. (#5363) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- `-NoTypeInformation`을 `Export-Csv` 및 `ConvertTo-Csv`의 기본값으로 만듭니다. (#5164)([@markekraus](https://github.com/markekraus)에게 감사드립니다!)

### <a name="service-cmdlets"></a>서비스 cmdlet

- `Get-Service`에 의해 반환된 `ServiceController` 객체에 속성 `UserName`, `Description`, `DelayedAutoStart`, `BinaryPathName` 및 `StartupType`을 추가합니다. (#4907) ([@joandrsn](https://github.com/joandrsn)에게 감사드립니다.)
- `Set-Service` 명령에서 자격 증명을 설정하는 기능을 추가합니다. (#4844) ([@joandrsn](https://github.com/joandrsn)에게 감사드립니다.)

### <a name="other-cmdlets"></a>기타 cmdlet

- 링크 루프를 확인하고 필요 시 symlinks를 통과하는 `-FollowSymlink`라는 `Get-ChildItem`에 매개 변수를 추가합니다. (#4020)
- `Add-Type`을 업데이트하여 `CSharpVersion7`을 지원합니다. (#3933) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다.)
- 더 나은 해결책을 찾을 때까지 지원되지 않는 API를 사용하기 때문에 `Microsoft.PowerShell.LocalAccounts` 모듈을 제거합니다. (#4302)
- 더 나은 해결책을 찾을 때까지 지원되지 않는 API를 사용하기 때문에 `Microsoft.PowerShell.Diagnostics`에 있는 `*-Counter` cmdlet을 제거합니다. (#4303)
- `Invoke-Item -Path <folder>`에 대한 지원을 추가합니다. (#4262)
- `-Extension` 및 `-LeafBase` 스위치를 `Split-Path`에 추가하면 파일 이름 확장자와 파일 이름의 나머지 사이에 경로를 분할할 수 있습니다. (#2721) ([@powercode](https://github.com/powercode)에게 감사드립니다!)
- 위쪽/아래쪽 N 정렬을 위해 매개 변수 `-Top` 및 `-Bottom`을 `Sort-Object`에 추가합니다.
- `CodeProperty "Parent"`를 `System.Diagnostics.Process`에 추가하여 프로세스의 상위 프로세스를 노출합니다. (#2850) ([@powercode](https://github.com/powercode)에게 감사드립니다!)
- `Get-Process`의 메모리 열에 KB 대신 MB를 사용합니다.
- `Out-String`을 위해 `-NoNewLine` 스위치를 추가합니다. (#5056) ([@raghav710](https://github.com/raghav710)에게 감사드립니다.)
- `Move-Item` cmdlet은 `-Include`, `-Exclude` 및 `-Filter` 매개 변수를 지원합니다. (#3878)
- `Remove-Item`의 레지스트리 경로에 사용되도록 `*`를 허용합니다. (#4866)
- `-Title`을 `Get-Credential`에 추가하고 플랫폼 간 프롬프트 경험을 통합합니다.
- `-TimeOut` 매개 변수를 `Test-Connection`에 추가합니다. (#2492)
- `Get-AuthenticodeSignature` cmdlet은 이제 파일 서명 타임스탬프를 가져올 수 있습니다. (#4061)
- `Get-Help`에서 지원되지 않는 `-ShowWindow` 스위치를 제거합니다. (#4903)
- 반환된 배열 요소에 구분 기호를 포함하지 않도록 `Get-Content -Delimiter`를 수정합니다. (#3706) ([@mklement0](https://github.com/mklement0)에게 감사드립니다.)
- `Meta`, `Charset` 및 `Transitional` 매개 변수를 `ConvertTo-HTML`에 추가합니다. (#4184) ([@ergo3114](https://github.com/ergo3114)에게 감사드립니다.)
- `WindowsUBR` 및 `WindowsVersion` 속성을 `Get-ComputerInfo` 결과에 추가합니다.
- `-Group` 매개 변수를 `Get-Verb`에 추가합니다.
- `ShouldProcess` 지원을 `New-FileCatalog` 및 `Test-FileCatalog`에 추가합니다(`-WhatIf` 및 `-Confirm` 수정). (#3074) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- `-WhatIf` 스위치를 `Start-Process` cmdlet에 추가합니다. (#4735) ([@sarithsutha](https://github.com/sarithsutha)에게 감사드립니다.)
- `ValidateNotNullOrEmpty` 너무 많은 기존 매개 변수를 추가합니다.

## <a name="tab-completion"></a>탭 완성

- 런타임 변수 값을 기반으로 탭 완성의 형식 유추를 향상시켰습니다. (#2744) ([@powercode](https://github.com/powercode)에게 감사드립니다!) 이렇게 하면 다음과 같은 상황에서 탭 완성이 가능합니다.

  ```powershell
  $p = Get-Process
  $p | Foreach-Object Prio<tab>
  ```

- `Select-Object`의 `-Property`에 대해 해시 테이블 탭 완성을 추가합니다. (#3625) ([@powercode](https://github.com/powercode)에게 감사드립니다.)
- `-ExcludeProperty`와 `Select-Object`의 `-ExpandProperty`에 인수 자동 완성을 사용합니다. (#3443) ([@iSazonov](https://github.com/iSazonov)에게 감사드립니다!)
- `native.exe --<tab>`를 네이티브 완성자로 호출하도록 탭 완성의 버그를 수정했습니다. (#3633) ([@powercode](https://github.com/powercode)에게 감사드립니다!)

## <a name="breaking-changes"></a>주요 변경 내용

PowerShell Core 6.0은 많은 주요 내용이 변경되었습니다.
자세한 내용은 [PowerShell Core 6.0의 주요 변경 내용][breaking-changes]을 참조하세요.

## <a name="debugging"></a>디버깅

- `Invoke-Command -ComputerName`에 대한 원격 스텝인 디버깅을 지원합니다. (#3015)
- PowerShell Core에서 바인더 디버그 로깅 사용

## <a name="filesystem-updates"></a>파일 시스템 업데이트

- UNC 경로의 파일 시스템 공급자의 사용을 활성화합니다. ($4998)
- `Split-Path`가 이제 UNC 루트와 함께 작동
- 인수가 없는 `cd`가 `cd ~`처럼 동작
- PowerShell Core를 수정하여 260자 보다 더 긴 있는 경로를 사용할 수 있게 되었습니다. (#3960)

## <a name="bug-fixes-and-performance-improvements"></a>버그 수정 및 성능 향상

시작 시간, 다양한 기본 제공 cmdlet 및 네이티브 이진 파일과의 상호 작용 등 PowerShell 전체 성능이 *대폭* 향상되었습니다.

또한 PowerShell Core 내의 여러 가지 버그를 수정했습니다.
수정 사항 및 변경 사항 전체 목록은 GitHub의 [changelog][]를 확인하세요.

## <a name="telemetry"></a>원격 분석

- PowerShell Core 6.0은 다음과 같은 두 값을 보고하기 위해 콘솔 호스트에 원격 분석 기능을 추가했습니다. (#3620)
  - OS 플랫폼(`$PSVersionTable.OSDescription`)
  - PowerShell의 정확한 버전(`$PSVersionTable.GitCommitId`)

이 원격 분석을 옵트아웃(opt out)하려는 경우 `true`, `1` 또는 `yes` 값 중 하나로 간단히 `POWERSHELL_TELEMETRY_OPTOUT` 환경 변수를 만듭니다.
변수를 만들면 PowerShell의 첫 실행 전이라도 모든 원격 분석이 바이패스됩니다.
또한 이 원격 분석 데이터와 [커뮤니티 대시보드][community-dashboard]의 원격 분석에서 얻은 정보를 공개할 예정입니다.
[블로그 게시물][telemetry-blog]에서 이 데이터를 사용하는 방법에 대해 자세히 알 수 있습니다.

[github]: https://github.com/PowerShell/PowerShell
[.NET Core 2.0]: https://docs.microsoft.com/dotnet/core/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[os_log]: https://developer.apple.com/documentation/os/logging
[Syslog]: https://en.wikipedia.org/wiki/Syslog
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[breaking-changes]: breaking-changes-ps6.md
[changelog]: https://github.com/PowerShell/PowerShell/tree/master/CHANGELOG.md
[community-dashboard]: https://aka.ms/PSGitHubBI
[telemetry-blog]: https://blogs.msdn.microsoft.com/powershell/2017/01/31/powershell-open-source-community-dashboard/
[.NET Standard]: https://docs.microsoft.com/dotnet/standard/net-standard
[.NET Blog]: https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard
[YouTube]: https://www.youtube.com/watch?v=YI4MurjfMn8&list=PLRAdsfhKI4OWx321A_pr-7HhRNk7wOLLY
[FAQ]: https://github.com/dotnet/standard/blob/master/docs/faq.md
[CDXML]: https://msdn.microsoft.com/library/jj542525(v=vs.85).aspx
[docker-hub]: https://hub.docker.com/r/microsoft/powershell/
[docker]: https://github.com/PowerShell/PowerShell/tree/master/docker
[windowspsmodulepath]: https://www.powershellgallery.com/packages/WindowsPSModulePath/
[semi-annual]: https://docs.microsoft.com/windows-server/get-started/semi-annual-channel-overview
