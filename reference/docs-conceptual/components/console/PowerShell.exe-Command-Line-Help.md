---
ms.date: 08/14/2018
keywords: powershell,cmdlet
title: PowerShell.exe 명령줄 도움말
ms.assetid: 1ab7b93b-6785-42c6-a1c9-35ff686a958f
ms.openlocfilehash: 0a11ebb11d29adf5853c232b3aa10bc72f92bf0c
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402460"
---
# <a name="powershellexe-command-line-help"></a>PowerShell.exe 명령줄 도움말

PowerShell.exe를 사용하여 Cmd.exe와 같은 다른 도구의 명령줄에서 PowerShell 세션을 시작하거나, PowerShell 명령줄에서 사용하여 새 세션을 시작할 수 있습니다. 매개 변수를 사용하여 세션을 사용자 지정합니다.

## <a name="syntax"></a>구문

```syntax
PowerShell[.exe]
       [-Command { - | <script-block> [-args <arg-array>]
                     | <string> [<CommandParameters>] } ]
       [-EncodedCommand <Base64EncodedCommand>]
       [-ExecutionPolicy <ExecutionPolicy>]
       [-File <FilePath> [<Args>]]
       [-InputFormat {Text | XML}]
       [-Mta]
       [-NoExit]
       [-NoLogo]
       [-NonInteractive]
       [-NoProfile]
       [-OutputFormat {Text | XML}]
       [-PSConsoleFile <FilePath> | -Version <PowerShell version>]
       [-Sta]
       [-WindowStyle <style>]

PowerShell[.exe] -Help | -? | /?
```

## <a name="parameters"></a>매개 변수

### <a name="-encodedcommand-base64encodedcommand"></a>-EncodedCommand <Base64EncodedCommand>

명령의 Base 64로 인코드된 문자열 버전을 허용합니다. 이 매개 변수를 사용하여 명령을 큰따옴표 또는 중괄호가 필요한 PowerShell로 전송합니다.

### <a name="-executionpolicy-executionpolicy"></a>-ExecutionPolicy <ExecutionPolicy>

현재 세션에 대한 기본 실행 정책을 설정하고 $env:PSExecutionPolicyPreference 환경 변수에 저장합니다. 이 매개 변수는 레지스트리에 설정된 PowerShell 실행 정책을 변경하지는 않습니다. 유효한 값 목록을 비롯한 PowerShell 실행 정책에 대한 자세한 내용은 [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies)를 참조하세요.

### <a name="-file-filepath-parameters"></a>-File <FilePath> \[<Parameters>]

스크립트에서 만드는 함수와 변수를 현재 세션에서 사용할 수 있도록 지정한 스크립트를 로컬 범위("dot-sourced")에서 실행합니다. 스크립트 파일의 경로와 매개 변수를 입력합니다. **File**은 명령의 마지막 매개 변수여야 합니다. **-File** 매개 변수 다음에 입력하는 모든 값은 해당 스크립트에 전달되는 스크립트 파일 경로 및 매개 변수로 해석됩니다.

스크립트에 전달되는 매개 변수는 리터럴 문자열로 전달됩니다(현재 셸에서 해석한 후). 예를 들어 cmd.exe에 하는 환경 변수 값을 전달 하려는 경우 cmd.exe 구문을 사용 합니다. `powershell.exe -File .\test.ps1 -TestParam %windir%`

이와 달리 실행 `powershell.exe -File .\test.ps1 -TestParam $env:windir` 리터럴 문자열을 수신 하는 스크립트에서 cmd.exe `$env:windir` 현재 cmd.exe 셸에서에 특별 한 의미가 없으며 있기 때문입니다.
합니다 `$env:windir` 환경 변수 참조의 스타일 _수 있습니다_ 내에서 사용할 수는 `-Command` 매개 변수를 이후 있습니다 PowerShell 코드로 해석 됩니다.

### <a name="-inputformat-text--xml"></a>\-InputFormat {Text | XML}

PowerShell로 전송되는 데이터 형식을 설명합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

### <a name="-mta"></a>-Mta

다중 스레드 아파트를 사용하여 PowerShell을 시작합니다. 이 매개 변수는 PowerShell 3.0에서 도입되었습니다. PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다. PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.

### <a name="-noexit"></a>-NoExit

시작 명령을 실행한 후 종료하지 않습니다.

### <a name="-nologo"></a>-NoLogo

시작 시 저작권 배너를 숨깁니다.

### <a name="-noninteractive"></a>-NonInteractive

사용자에게 대화형 프롬프트를 표시하지 않습니다.

### <a name="-noprofile"></a>-NoProfile

PowerShell 프로필을 로드하지 않습니다.

### <a name="-outputformat-text--xml"></a>-OutputFormat {Text | XML}

PowerShell의 출력 형식을 결정합니다. 유효한 값은 "Text"(텍스트 문자열) 또는 "XML"(직렬화된 CLIXML 형식)입니다.

### <a name="-psconsolefile-filepath"></a>-PSConsoleFile <FilePath>

지정된 PowerShell 콘솔 파일을 로드합니다. 콘솔 파일의 경로와 이름을 입력합니다. 콘솔 파일을 만들려면 PowerShell에서 [`Export-Console`](/powershell/module/Microsoft.PowerShell.Core/Export-Console) cmdlet을 사용합니다.

### <a name="-sta"></a>-Sta

단일 스레드 아파트를 사용하여 PowerShell을 시작합니다. PowerShell 3.0에서는 STA(단일 스레드 아파트)가 기본값입니다. PowerShell 2.0에서는 MTA(다중 스레드 아파트)가 기본값입니다.

### <a name="-version-powershell-version"></a>버전 <PowerShell Version>

지정된 버전의 PowerShell을 시작합니다. 지정한 버전이 시스템에 설치되어 있어야 합니다. 컴퓨터에 PowerShell 3.0이 설치되어 있는 경우 유효한 값은 "2.0"과 "3.0"입니다. 기본값은 "3.0"입니다.

PowerShell 3.0이 설치되지 않은 경우 유효한 값은 "2.0"뿐입니다. 다른 값은 무시됩니다.

자세한 내용은 [Windows PowerShell 설치](../../setup/installing-windows-powershell.md)를 참조하세요.

### <a name="-windowstyle-window-style"></a>-WindowStyle <Window style>

세션에 대한 창 스타일을 설정합니다. 유효한 값은 Normal, Minimized, Maximized 및 Hidden입니다.

### <a name="-command"></a>-Command

지정된 명령(및 매개 변수)을 PowerShell 명령 프롬프트에서 입력된 것처럼 실행합니다.
를 실행 한 후 PowerShell 종료 하지 않으면 합니다 **NoExit** 매개 변수를 지정 합니다.
`-Command` 다음의 모든 텍스트는 PowerShell에 단일 명령줄로 전송됩니다.
이것은 `-File`이 스크립트에 전송된 매개 변수를 처리하는 방식과 다릅니다.

변수의 `-Command` 수 "-", 문자열 또는 스크립트 블록입니다.
명령의 결과를 라이브 개체가 아니라 deserialize 된 XML 개체로 부모 셸에 반환 됩니다.

경우 변수의 `-Command` 은 "-", 표준 입력에서 명령 텍스트를 읽어옵니다.

경우 값 `-Command` 는 문자열인 **명령** _해야_ 명령 인수로 해석 됩니다 명령 뒤에 입력 한 문자가 때문에 지정 된 마지막 매개 변수 여야 합니다.

합니다 **명령** 전달 되는 값을 인식할 수 있는 경우 매개 변수 실행에 대 한 스크립트 블록에만 허용 `-Command` ScriptBlock 형식으로 합니다.
이것이 _만_ 가능한 다른 PowerShell 호스트에서 PowerShell.exe를 실행 하는 경우.
중괄호로 묶인 리터럴 스크립트 블록으로 형식 변수나 식에서 반환 되는 PowerShell에서 구문 분석 된 기존의 포함 될 수 있습니다 ScriptBlock 호스트 `{}`PowerShell.exe에 전달 되 고 전에 합니다.

Cmd.exe에 있는 것은 없습니다 스크립트 블록 (또는 ScriptBlock 형식)으로 하므로 전달 되는 값 **명령** 됩니다 _항상_ 문자열 이어야 합니다.
문자열 내에서 스크립트 블록을 작성할 수 있지만 실행 되는 대신 동작 정확 하 게 일반적인 PowerShell 프롬프트에서 입력, 처럼 다시 할 차단 스크립트의 내용을 인쇄 합니다.

문자열을 전달 `-Command` 되므로 스크립트 블록 중괄호 대개 필요한 애초에 cmd.exe에서 실행 하는 경우 PowerShell로 실행 계속 됩니다.
문자열 내에 정의 된 인라인 스크립트 블록을 실행 하는 [호출 연산자](/powershell/module/microsoft.powershell.core/about/about_operators#call-operator-) `&` 사용할 수 있습니다.

```console
"& {<command>}"
```

### <a name="-help---"></a>-Help, -?, /?

powershell.exe의 구문을 표시합니다. PowerShell에서 PowerShell.exe 명령을 입력하는 경우 명령 매개 변수 앞에 슬래시(/)가 아니라 하이픈(-)을 추가합니다. Cmd.exe에서는 하이픈 또는 슬래시를 사용할 수 있습니다.

> [!NOTE]
> 문제 해결 참고: PowerShell 2.0에서 Windows powershell 콘솔에 실패 하면 일부 프로그램을 고 LastExitCode 0xc0000142가 표시 됩니다부터 시작 합니다.

## <a name="examples"></a>예제

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
