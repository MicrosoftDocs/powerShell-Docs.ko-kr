---
description: 명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `powershell.exe` . 명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/05/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_exe
ms.openlocfilehash: ef03558a6b58868b98c9da488934b0bfbbce9fe7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223330"
---
# <a name="about-powershellexe"></a>PowerShell.exe 정보

## <a name="short-description"></a>간단한 설명
명령줄 인터페이스를 사용 하는 방법을 설명 합니다 `powershell.exe` . 명령줄 매개 변수를 표시 하 고 구문을 설명 합니다.

## <a name="long-description"></a>자세한 설명

### <a name="syntax"></a>SYNTAX

```
PowerShell[.exe]
    [-PSConsoleFile <file> | -Version <version>]
    [-NoLogo]
    [-NoExit]
    [-Sta]
    [-Mta]
    [-NoProfile]
    [-NonInteractive]
    [-InputFormat {Text | XML}]
    [-OutputFormat {Text | XML}]
    [-WindowStyle <style>]
    [-EncodedCommand <Base64EncodedCommand>]
    [-ConfigurationName <string>]
    [-File - | <filePath> <args>]
    [-ExecutionPolicy <ExecutionPolicy>]
    [-Command - | { <script-block> [-args <arg-array>] }
                | { <string> [<CommandParameters>] } ]

PowerShell[.exe] -Help | -? | /?
```

### <a name="parameters"></a>매개 변수

#### <a name="-psconsolefile-filepath"></a>-PSConsoleFile \<FilePath\>

지정된 PowerShell 콘솔 파일을 로드합니다. 콘솔 파일의 경로와 이름을 입력합니다. 콘솔 파일을 만들려면 PowerShell에서 Export-Console cmdlet을 사용합니다.

#### <a name="-version-powershell-version"></a>버전 \<PowerShell Version\>

지정된 버전의 PowerShell을 시작합니다. 유효한 값은 2.0 및 3.0입니다. 지정한 버전이 시스템에 설치되어 있어야 합니다. 컴퓨터에 Windows PowerShell 3.0이 설치 되어 있는 경우 "3.0"이 기본 버전입니다.
그렇지 않으면 "2.0"이 기본 버전입니다. 자세한 내용은 [PowerShell 설치](/powershell/scripting/install/installing-windows-powershell)를 참조 하세요.

#### <a name="-nologo"></a>-NoLogo

시작 시 저작권 배너를 숨깁니다.

#### <a name="-noexit"></a>-NoExit

시작 명령을 실행한 후 종료하지 않습니다.

#### <a name="-sta"></a>-Sta

단일 스레드 아파트를 사용하여 PowerShell을 시작합니다. Windows PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다. Windows PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다.

#### <a name="-mta"></a>-Mta

다중 스레드 아파트를 사용하여 PowerShell을 시작합니다. 이 매개 변수는 PowerShell 3.0에서 도입되었습니다. PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다. PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다.

#### <a name="-noprofile"></a>-NoProfile

PowerShell 프로필을 로드하지 않습니다.

#### <a name="-noninteractive"></a>-NonInteractive

사용자에게 대화형 프롬프트를 표시하지 않습니다.

#### <a name="-inputformat-text--xml"></a>-InputFormat {Text | XML}

PowerShell로 전송되는 데이터 형식을 설명합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

#### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

PowerShell의 출력 형식을 결정합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

#### <a name="-windowstyle-window-style"></a>-WindowStyle \<Window style\>

세션에 대한 창 스타일을 설정합니다. 유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.

#### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand \<Base64EncodedCommand\>

명령의 Base 64로 인코드된 문자열 버전을 허용합니다. 이 매개 변수를 사용하여 명령을 큰따옴표 또는 중괄호가 필요한 PowerShell로 전송합니다. UTF-16LE 문자 인코딩을 사용 하 여 문자열의 서식을 지정 해야 합니다.

#### <a name="-configurationname-string"></a>-ConfigurationName \<string\>

PowerShell이 실행 되는 구성 끝점을 지정 합니다. 이는 기본 PowerShell 원격 끝점 또는 특정 사용자 역할 기능이 있는 사용자 지정 끝점을 포함 하 여 로컬 컴퓨터에 등록 된 모든 끝점이 될 수 있습니다.

#### <a name="-file----filepath-args"></a>-File-| \<filePath\>\<args\>

**File** 값이 "-" 이면 표준 입력에서 명령 텍스트를 읽습니다.
`powershell -File -`리디렉션된 표준 입력 없이 실행 하면 일반 세션이 시작 됩니다. 이는 **파일** 매개 변수를 지정 하지 않는 것과 같습니다.

**파일** 의 값이 파일 경로인 경우 스크립트는 로컬 범위 ("점 원본")에서 실행 되므로 스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있습니다. 스크립트 파일의 경로와 매개 변수를 입력합니다. **File** 은 명령의 마지막 매개 변수여야 합니다. **File** 매개 변수 뒤에 입력 한 모든 값은 해당 스크립트에 전달 된 스크립트 파일 경로 및 매개 변수로 해석 됩니다.

스크립트에 전달되는 매개 변수는 리터럴 문자열로 전달됩니다(현재 셸에서 해석한 후). 예를 들어 **cmd.exe** 에 있고 환경 변수 값을 전달 하려는 경우 **cmd.exe** 구문을 사용 합니다. `powershell.exe -File .\test.ps1 -TestParam %windir%`

반면 `powershell.exe -File .\test.ps1 -TestParam $env:windir` **cmd.exe** 에서를 실행 하면 `$env:windir` 현재 **cmd.exe** 셸에 대 한 특별 한 의미가 없기 때문에 스크립트에서 리터럴 문자열을 받습니다. `$env:windir`환경 변수 참조의 스타일은 PowerShell 코드로 해석 되기 때문에 **명령** 매개 변수 내에서 사용할 _수 있습니다_ .

마찬가지로 **일괄 처리 스크립트** 에서 동일한 명령을 실행 하려는 경우 또는 대신를 사용 하 여 `%~dp0` `.\` `$PSScriptRoot` 현재 실행 디렉터리인를 나타냅니다 `powershell.exe -File %~dp0test.ps1 -TestParam %windir%` .
대신를 사용 하는 경우 `.\test.ps1` 리터럴 경로를 찾을 수 없으므로 PowerShell에서 오류를 throw 합니다. `.\test.ps1`

파일의 **값이 파일** 경로인 경우 **파일 매개 변수 이름 뒤에 입력** 한 문자는 스크립트 파일 경로, 스크립트 매개 변수 순으로 해석 되기 때문에 **file** 은 명령의 마지막 매개 변수 _여야 합니다_ .

**File** 매개 변수의 값에 스크립트 매개 변수 및 값을 포함할 수 있습니다. `-File .\Get-Script.ps1 -Domain Central`

일반적으로 스크립트의 스위치 매개 변수는 포함되거나 생략됩니다.
예를 들어 다음 명령은 스크립트 파일의 **All** 매개 변수를 사용 합니다 `Get-Script.ps1` . `-File .\Get-Script.ps1 -All`

드문 경우 지만 매개 변수에 **부울** 값을 제공 해야 할 수 있습니다.
이러한 방식으로 스크립트를 실행 하는 경우 스위치 매개 변수에 대 한 명시적 부울 값을 전달할 수 없습니다. 이 제한은 PowerShell 6 ()에서 제거 되었습니다 `pwsh.exe` .

#### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy \<ExecutionPolicy\>

현재 세션에 대 한 기본 실행 정책을 설정 하 고 `$env:PSExecutionPolicyPreference` 환경 변수에 저장 합니다. 이 매개 변수는 레지스트리에 설정된 PowerShell 실행 정책을 변경하지는 않습니다. 유효한 값 목록을 비롯한 PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](about_Execution_Policies.md)를 참조하세요.

#### <a name="-command"></a>-Command

지정 된 명령 (및 매개 변수)을 PowerShell 명령 프롬프트에서 입력 한 것 처럼 실행 한 다음 매개 변수가 지정 되지 않은 경우 종료 합니다 `NoExit` .

**명령의** 값은 `-` , 스크립트 블록 또는 문자열일 수 있습니다. **Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다.

명령 **매개 변수** 는 **명령** 에 **ScriptBlock** 형식으로 전달 된 값을 인식할 수 있는 경우에만 실행할 스크립트 블록을 허용 합니다. 이는 다른 PowerShell 호스트에서 실행 하는 경우에 _만_ 가능 `powershell.exe` 합니다. **ScriptBlock** 형식은 `{}` 에 전달 되기 전에 기존 변수에 포함 되거나 식에서 반환 되거나 중괄호 ()로 묶인 리터럴 스크립트 블록으로 PowerShell 호스트에 의해 구문 분석 될 수 있습니다 `powershell.exe` .

```powershell
powershell -Command {Get-WinEvent -LogName security}
```

에서는 `cmd.exe` 스크립트 블록 (또는 **ScriptBlock** 형식)이 없으므로 **명령** 에 전달 되는 값은 _항상_ 문자열입니다. 문자열 내부에 스크립트 블록을 작성할 수 있지만, 실행되지 않고 정확히 일반 PowerShell 프롬프트에 입력한 것처럼 동작하여 스크립트 블록의 콘텐츠를 다시 사용자에게 인쇄합니다.

**명령** 에 전달 된 문자열은 여전히 PowerShell 코드로 실행 되므로에서 실행할 때 스크립트 블록 중괄호는 처음에는 필요 하지 않습니다 `cmd.exe` . 문자열 내부에 정의된 인라인 스크립트 블록을 실행하려면 [호출 연산자](about_operators.md#special-operators) `&`를 사용할 수 있습니다.

```cmd
pwsh -Command "& {Get-WinEvent -LogName security}"
```

**명령의** 값이 문자열인 경우 명령 뒤의 모든 인수가 실행할 명령의 일부로 해석 되기 때문에 **command** 는 pwsh의 마지막 매개 변수 여야 합니다.

기존 PowerShell 세션 내에서 호출 되는 경우 결과는 라이브 개체가 아니라 역직렬화 된 XML 개체로 부모 셸에 반환 됩니다. 다른 셸에서는 결과가 문자열로 반환 됩니다.

**Command** 값이 이면 `-` 표준 입력에서 명령 텍스트를 읽습니다. 표준 입력으로 **Command** 매개 변수를 사용 하는 경우 표준 입력을 리디렉션해야 합니다. 다음은 그 예입니다. 

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

마찬가지로, 또는와 같은 스크립트 종료 (runspace 종료) 오류가 `throw` `-ErrorAction Stop` 발생 하거나 실행이 <kbd>Ctrl</kbd>C를 사용 하 여 중단 되 면 값 1이 반환 됩니다 - <kbd>C</kbd>.

다른 PowerShell 호스트에서 **PowerShell.exe** 를 실행 하는 경우에 _만_ 가능 합니다.
**ScriptBlock** 형식은 기존 변수에 포함 되거나, 식에서 반환 되거나, `{}` **PowerShell.exe** 에 전달 되기 전에 중괄호로 묶인 리터럴 스크립트 블록으로 PowerShell 호스트에 의해 구문 분석 될 수 있습니다.

**cmd.exe** 에는 스크립트 블록 (또는 **ScriptBlock** 형식)이 없으므로 **명령** 에 전달 되는 값은 _항상_ 문자열입니다. 문자열 내부에 스크립트 블록을 작성할 수 있지만, 실행되지 않고 정확히 일반 PowerShell 프롬프트에 입력한 것처럼 동작하여 스크립트 블록의 콘텐츠를 다시 사용자에게 인쇄합니다.

**명령** 에 전달 된 문자열은 PowerShell로 계속 실행 되므로 **cmd.exe** 에서 실행할 때 스크립트 블록 중괄호는 처음에는 필요 하지 않습니다. 문자열 내에 정의 된 인라인 스크립트 블록을 실행 하려면 [call 연산자](about_operators.md#special-operators) 를 
 `&` 사용할 수 있습니다.

```console
"& {<command>}"
```

#### <a name="-help---"></a>-Help, -?, /?

**PowerShell.exe** 에 대 한 도움말을 표시 합니다. PowerShell 세션에 **PowerShell.exe** 명령을 입력 하는 경우 슬래시 (/)가 아닌 하이픈 (-)을 사용 하 여 명령 매개 변수 앞에 추가 합니다. **cmd.exe** 에서 하이픈 또는 슬래시 중 하나를 사용할 수 있습니다.

### <a name="remarks"></a>REMARKS

문제 해결 참고: PowerShell 2.0에서는 PowerShell 콘솔에서 일부 프로그램을 시작 하는 작업이 실패 하 고 **LastExitCode** 통해가 발생 합니다.

### <a name="examples"></a>예제

```powershell
# Create a new PowerShell session and load a saved console file
PowerShell -PSConsoleFile sqlsnapin.psc1

# Create a new PowerShell V2 session with text input, XML output, and no logo
PowerShell -Version 2.0 -NoLogo -InputFormat text -OutputFormat XML

# Execute a PowerShell Command in a session
PowerShell -Command "Get-EventLog -LogName security"

# Run a script block in a session
PowerShell -Command {Get-EventLog -LogName security}

# An alternate way to run a command in a new session
PowerShell -Command "& {Get-EventLog -LogName security}"

# To use the -EncodedCommand parameter:
$command = "dir 'c:\program files' "
$bytes = [System.Text.Encoding]::Unicode.GetBytes($command)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -encodedCommand $encodedCommand
```
