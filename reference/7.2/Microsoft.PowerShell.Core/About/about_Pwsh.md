---
description: 명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `pwsh` . 명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Pwsh
ms.openlocfilehash: eae22efa9302826d3e1303dd933d8ea114123ab9
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195997"
---
# <a name="about-pwsh"></a>Pwsh 정보

## <a name="short-description"></a>간단한 설명
명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `pwsh` . 명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.

## <a name="long-description"></a>자세한 설명

## <a name="syntax"></a>구문

```
pwsh[.exe]
   [[-File] <filePath> [args]]
   [-Command { - | <script-block> [-args <arg-array>]
                 | <string> [<CommandParameters>] } ]
   [-ConfigurationName <string>]
   [-CustomPipeName <string>]
   [-EncodedCommand <Base64EncodedCommand>]
   [-ExecutionPolicy <ExecutionPolicy>]
   [-InputFormat {Text | XML}]
   [-Interactive]
   [-Login]
   [-MTA]
   [-NoExit]
   [-NoLogo]
   [-NonInteractive]
   [-NoProfile]
   [-OutputFormat {Text | XML}]
   [-SettingsFile <SettingsFilePath>]
   [-SSHServerMode]
   [-STA]
   [-Version]
   [-WindowStyle <style>]
   [-WorkingDirectory <directoryPath>]

pwsh[.exe] -h | -Help | -? | /?
```

## <a name="parameters"></a>매개 변수

모든 매개 변수는 대/소문자를 구분 하지 않습니다.

### <a name="-file---f"></a>-File | -f

의 값이 이면 `File` `-` 표준 입력에서 명령 텍스트를 읽습니다.
`pwsh -File -`리디렉션된 표준 입력 없이 실행 하면 일반 세션이 시작 됩니다. 이는 매개 변수를 지정 하지 않는 것과 같습니다 `File` .

매개 변수가 없지만 명령줄에 값이 있는 경우이 매개 변수는 기본 매개 변수입니다. 지정 된 스크립트는 로컬 범위 ("점 원본")에서 실행 되므로 스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있습니다. 스크립트 파일의 경로와 매개 변수를 입력합니다. 파일 매개 변수 이름 뒤에 입력 된 모든 문자는 스크립트 파일 경로 다음에 스크립트 매개 변수로 해석 되기 때문에 file은 명령의 마지막 매개 변수 여야 합니다.

일반적으로 스크립트의 스위치 매개 변수는 포함되거나 생략됩니다.
예를 들어 다음 명령은 Get-Script.ps1 스크립트 파일의 All 매개 변수를 사용 합니다. `-File .\Get-Script.ps1 -All`

드문 경우 지만 스위치 매개 변수에 대해 **부울** 값을 제공 해야 할 수 있습니다. **File** 매개 변수의 값에 스위치 매개 변수에 대 한 **부울** 값을 제공 하려면 일반적으로 매개 변수를 즉시 콜론 및 부울 값 (예:)으로 사용 `-File .\Get-Script.ps1 -All:$False` 합니다.

스크립트에 전달되는 매개 변수는 리터럴 문자열로 전달됩니다(현재 셸에서 해석한 후). 예를 들어를 `cmd.exe` 사용 하 고 환경 변수 값을 전달 하려는 경우 `cmd.exe` 다음 구문을 사용 합니다. `pwsh -File .\test.ps1 -TestParam %windir%`

이와 달리 `pwsh -File .\test.ps1 -TestParam $env:windir` 에서를 실행 하면 `cmd.exe` `$env:windir` 현재 셸에 대 한 특별 한 의미가 없기 때문에 스크립트에서 리터럴 문자열을 받습니다 `cmd.exe` . `$env:windir`환경 변수 참조의 스타일은 PowerShell 코드로 해석 되기 때문에 **명령** 매개 변수 내에서 사용할 _수 있습니다_ .

마찬가지로 _일괄 처리 스크립트_ 에서 동일한 명령을 실행 하려는 경우 또는 대신를 사용 하 여 `%~dp0` `.\` `$PSScriptRoot` 현재 실행 디렉터리인를 나타냅니다 `pwsh -File %~dp0test.ps1 -TestParam %windir%` . 대신를 사용 하는 경우 `.\test.ps1` 리터럴 경로를 찾을 수 없으므로 PowerShell에서 오류를 throw 합니다. `.\test.ps1`

명령을 사용 하 여 스크립트 파일이 종료 되 면 `exit` 프로세스 종료 코드는 명령에 사용 되는 숫자 인수로 설정 됩니다 `exit` . 정상적인 종료를 사용 하는 경우 종료 코드는 항상 `0` 입니다.

와 마찬가지로 `-Command` , 스크립트 종료 오류가 발생할 때 종료 코드는로 설정 됩니다 `1` . 그러나와는 달리 `-Command` , <kbd>Ctrl</kbd>C를 사용 하 여 실행이 중단 되는 경우 - <kbd></kbd> 종료 코드는 `0` 입니다.

### <a name="-command---c"></a>-Command | -c

지정 된 명령 (및 매개 변수)을 PowerShell 명령 프롬프트에서 입력 한 것 처럼 실행 한 다음 매개 변수가 지정 되지 않은 경우 종료 합니다 `NoExit` .

**명령의** 값은 `-` , 스크립트 블록 또는 문자열일 수 있습니다. **Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다.

명령 **매개 변수** 는 **명령** 에 **ScriptBlock** 형식으로 전달 된 값을 인식할 수 있는 경우에만 실행할 스크립트 블록을 허용 합니다. 이는 다른 PowerShell 호스트에서 실행 하는 경우에 _만_ 가능 `pwsh` 합니다. **ScriptBlock** 형식은 `{}` 에 전달 되기 전에 기존 변수에 포함 되거나 식에서 반환 되거나 중괄호 ()로 묶인 리터럴 스크립트 블록으로 PowerShell 호스트에 의해 구문 분석 될 수 있습니다 `pwsh` .

```powershell
pwsh -Command {Get-WinEvent -LogName security}
```

에서는 `cmd.exe` 스크립트 블록 (또는 **ScriptBlock** 형식)이 없으므로 **명령** 에 전달 되는 값은 _항상_ 문자열입니다. 문자열 내부에 스크립트 블록을 작성할 수 있지만, 실행되지 않고 정확히 일반 PowerShell 프롬프트에 입력한 것처럼 동작하여 스크립트 블록의 콘텐츠를 다시 사용자에게 인쇄합니다.

**명령** 에 전달 된 문자열은 여전히 PowerShell 코드로 실행 되므로에서 실행할 때 스크립트 블록 중괄호는 처음에는 필요 하지 않습니다 `cmd.exe` . 문자열 내부에 정의된 인라인 스크립트 블록을 실행하려면 [호출 연산자](about_operators.md#special-operators) `&`를 사용할 수 있습니다.

```
pwsh -Command "& {Get-WinEvent -LogName security}"
```

**명령의** 값이 문자열인 경우 명령 뒤의 모든 인수가 실행할 명령의 일부로 해석 되기 때문에 **command** 는 pwsh의 마지막 매개 변수 여야 합니다.

기존 PowerShell 세션 내에서 호출 되는 경우 결과는 라이브 개체가 아니라 역직렬화 된 XML 개체로 부모 셸에 반환 됩니다. 다른 셸에서는 결과가 문자열로 반환 됩니다.

**Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다. 표준 입력으로 **Command** 매개 변수를 사용 하는 경우 표준 입력을 리디렉션해야 합니다. 예를 들면 다음과 같습니다.

```powershell
@'
"in"

"hi" |
  % { "$_ there" }

"out"
'@ | powershell -NoProfile -Command -
```

이 예제는 다음과 같은 출력을 생성합니다.

```Output
in
hi there
out
```

프로세스 종료 코드는 스크립트 블록 내의 마지막 (실행 됨) 명령의 상태에 따라 결정 됩니다. 가 이거나가 인 경우 종료 코드는입니다 `0` `$?` `$true` `1` `$?` `$false` . 마지막 명령이 또는 이외의 종료 코드를 명시적으로 설정 하는 외부 프로그램 또는 PowerShell 스크립트인 경우 `0` `1` 해당 종료 코드는 `1` 프로세스 종료 코드의로 변환 됩니다. 특정 종료 코드를 유지 하려면 `exit $LASTEXITCODE` 명령 문자열 또는 스크립트 블록에를 추가 합니다.

마찬가지로, 또는와 같은 스크립트 종료 (runspace 종료) 오류가 `throw` `-ErrorAction Stop` 발생 하거나 실행이 <kbd>Ctrl</kbd>C를 사용 하 여 중단 되 면 값 1이 반환 됩니다 - <kbd></kbd>.

### <a name="-configurationname---config"></a>-ConfigurationName | -config

PowerShell이 실행 되는 구성 끝점을 지정 합니다. 이는 기본 PowerShell 원격 끝점 또는 특정 사용자 역할 기능이 있는 사용자 지정 끝점을 포함 하 여 로컬 컴퓨터에 등록 된 모든 끝점이 될 수 있습니다.

예: `pwsh -ConfigurationName AdminRoles`

### <a name="-custompipename"></a>-CustomPipeName

디버깅 및 기타 프로세스 간 통신에 사용 되는 추가 IPC 서버 (명명 된 파이프)에 사용할 이름을 지정 합니다. 이는 다른 PowerShell 인스턴스에 연결 하는 데 사용할 수 있는 예측 가능한 메커니즘을 제공 합니다. 일반적으로의 **CustomPipeName** 매개 변수와 함께 사용 `Enter-PSHostProcess` 됩니다.

이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.

예를 들면 다음과 같습니다.

```powershell
# PowerShell instance 1
pwsh -CustomPipeName mydebugpipe
# PowerShell instance 2
Enter-PSHostProcess -CustomPipeName mydebugpipe
```

### <a name="-encodedcommand---e---ec"></a>-EncodedCommand | -e | -ec

명령의 b a s e 64로 인코드된 문자열 버전을 허용 합니다. 이 매개 변수를 사용 하 여 복잡 하 고 중첩 된 따옴표를 필요로 하는 명령을 PowerShell에 제출할 수 있습니다. Base64 표현은 u t f-UTF-16LE로 인코딩된 문자열 이어야 합니다.

예를 들면 다음과 같습니다.

```powershell
$command = 'dir "c:\program files" '
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
pwsh -encodedcommand $encodedCommand
```

### <a name="-executionpolicy---ex---ep"></a>-Set-executionpolicy | -ex | -ep

현재 세션에 대 한 기본 실행 정책을 설정 하 고 `$env:PSExecutionPolicyPreference` 환경 변수에 저장 합니다. 이 매개 변수는 영구적으로 구성 된 실행 정책을 변경 하지 않습니다.

이 매개 변수는 Windows 컴퓨터에만 적용 됩니다. `$env:PSExecutionPolicyPreference`Windows가 아닌 플랫폼에 환경 변수가 없습니다.

### <a name="-inputformat---inp---if"></a>-InputFormat | -sct.inp | -if

PowerShell로 전송되는 데이터 형식을 설명합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

### <a name="-interactive---i"></a>-Interactive | -i

사용자에 게 대화형 프롬프트를 표시 합니다. 비 대화형 매개 변수의 역함수입니다.

### <a name="-login---l"></a>-로그인 | -l

Linux 및 macOS에서는/bin/sh을 사용 하 여/etc/profile 및 ~/.profile. 로그인 프로필을 실행 하는 로그인 셸로 PowerShell을 시작 합니다.
Windows에서는이 스위치가 아무 작업도 수행 하지 않습니다.

> [!IMPORTANT]
> 이 매개 변수는 먼저 로그인 셸로 PowerShell을 시작 해야 합니다.
> 이 매개 변수를 다른 위치에 전달 하는 것은 무시 됩니다.

`pwsh`UNIX와 비슷한 운영 체제에서 로그인 셸로 설정 하려면 다음을 수행 합니다.

- 의 전체 절대 경로가 나열 되는지 확인 합니다. `pwsh``/etc/shells`
  - 이 경로는 일반적으로 `/usr/bin/pwsh` Linux 또는 `/usr/local/bin/pwsh` macos와 같은 항목입니다.
  - 일부 설치 방법의 경우 설치 시이 항목이 자동으로 추가 됩니다.
  - `pwsh`에이 없으면 편집기를 `/etc/shells` 사용 하 여 마지막 줄에 경로를 추가 합니다 `pwsh` . 이렇게 하려면 관리자 권한으로 편집 해야 합니다.
- [Chsh](https://linux.die.net/man/1/chsh) 유틸리티를 사용 하 여 현재 사용자의 셸을 `pwsh` 다음과 같이 설정 합니다.

  ```sh
  chsh -s /usr/bin/pwsh
  ```

> [!WARNING]
> 를 `pwsh` 로그인 셸로 설정 하는 기능은 현재 Linux 용 Windows 하위 시스템 (WSL)에서 지원 되지 않으며, 로그인 셸로 설정 하려고 시도 하면 `pwsh` wsl을 대화형으로 시작할 수 없습니다.

### <a name="-mta"></a>-MTA

다중 스레드 아파트를 사용 하 여 PowerShell을 시작 합니다. 이 스위치는 Windows 에서만 사용할 수 있습니다.

### <a name="-noexit---noe"></a>-NoExit | -noe

시작 명령을 실행한 후 종료하지 않습니다.

예: `pwsh -NoExit -Command Get-Date`

### <a name="-nologo---nol"></a>-NoLogo | -nol

대화형 세션 시작 시 저작권 배너를 숨깁니다.

### <a name="-noninteractive---noni"></a>-비 대화형 | -비 i

사용자에게 대화형 프롬프트를 표시하지 않습니다. 또는 확인 프롬프트와 같은 대화형 기능을 사용 하려고 하면 `Read-Host` 문 종료 오류가 발생 합니다.

### <a name="-noprofile---nop"></a>-NoProfile | -nop

PowerShell 프로필을 로드 하지 않습니다.

### <a name="-outputformat---o---of"></a>-OutputFormat | -o | -/

PowerShell의 출력 형식을 결정합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

예: `pwsh -o XML -c Get-Date`

PowerShell 세션을 트 내의 호출 하면 deserialize 된 개체를 일반 문자열 대신 출력으로 가져옵니다. 다른 셸에서 호출 된 경우 출력은 EXPORT-CLIXML 텍스트로 형식이 지정 된 문자열 데이터입니다.

### <a name="-settingsfile---settings"></a>-SettingsFile | -설정

`powershell.config.json`세션에 대 한 시스템 차원 설정 파일을 재정의 합니다. 기본적으로 시스템 차원의 설정은 `powershell.config.json` 디렉터리의에서 읽습니다 `$PSHOME` .

이러한 설정은 인수로 지정 된 끝점에서 사용 되지 않습니다 `-ConfigurationName` .

예: `pwsh -SettingsFile c:\myproject\powershell.config.json`

### <a name="-sshservermode---sshs"></a>-SSHServerMode | -sshs

PowerShell을 SSH 하위 시스템으로 실행 하기 위해 sshd_config에 사용 됩니다. 다른 용도로 사용 하거나 지원 하지 않습니다.

### <a name="-sta"></a>-STA

단일 스레드 아파트를 사용 하 여 PowerShell을 시작 합니다. 기본값입니다. 이 스위치는 Windows 에서만 사용할 수 있습니다.

### <a name="-version---v"></a>-Version | -v

PowerShell의 버전을 표시 합니다. 추가 매개 변수는 무시 됩니다.

### <a name="-windowstyle---w"></a>-System.windows.window.windowstyle | -w

세션에 대한 창 스타일을 설정합니다. 유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.

### <a name="-workingdirectory---wd"></a>-WorkingDirectory | -wd

시작 시를 실행 하 여 초기 작업 디렉터리를 설정 합니다. 유효한 PowerShell 파일 경로가 지원 됩니다.

홈 디렉터리에서 PowerShell을 시작 하려면 다음을 사용 합니다. `pwsh -WorkingDirectory ~`

### <a name="-help---"></a>-Help, -?, /?

에 대 한 도움말을 표시 `pwsh` 합니다. PowerShell에서 pwsh 명령을 입력 하는 경우 슬래시 ()가 아닌 하이픈 ()을 사용 하 여 명령 매개 변수 앞에 추가 `-` `/` 합니다.
