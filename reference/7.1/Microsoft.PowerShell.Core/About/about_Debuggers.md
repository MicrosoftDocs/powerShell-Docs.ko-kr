---
description: PowerShell 디버거에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: 6765c33e4508e19dfca7f291f8452f1bb4730747
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222114"
---
# <a name="about-debuggers"></a>디버거 정보

## <a name="short-description"></a>간단한 설명
PowerShell 디버거에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

디버깅은 스크립트를 실행 하는 동안 스크립트를 검사 하 여 스크립트 지침에서 오류를 식별 하 고 수정 하는 프로세스입니다. PowerShell 디버거를 통해 스크립트, 함수, 명령, PowerShell DSC (필요한 상태 구성) 구성 또는 식에서 오류와 비효율성을 검사 하 고 식별할 수 있습니다.

PowerShell 5.0부터 PowerShell 디버거는 콘솔 또는 원격 컴퓨터의 Windows PowerShell ISE 실행 되는 스크립트, 함수, 명령, 구성 또는 식을 디버그 하도록 업데이트 되었습니다. `Enter-PSSession`를 실행 하 여 원격 컴퓨터에서 중단점을 설정 하 고 스크립트 파일과 명령을 디버그할 수 있는 대화형 원격 PowerShell 세션을 시작할 수 있습니다. `Enter-PSSession` 원격 컴퓨터에서 스크립트나 명령을 실행 하는 연결이 끊어진 세션에 다시 연결 하 고이를 시작할 수 있도록 기능이 업데이트 되었습니다. 실행 중인 스크립트가 중단점에 도달 하면 클라이언트 세션이 자동으로 디버거를 시작 합니다. 스크립트를 실행 하는 연결이 끊어진 세션에서 이미 중단점에 도달 하 고 중단점에서 중지 된 경우는 `Enter-PSSession` 세션에 다시 연결한 후 자동으로 명령줄 디버거를 시작 합니다.

Powershell 디버거의 기능을 사용 하 여 실행 중인 PowerShell 스크립트, 함수, 명령 또는 식을 검사할 수 있습니다. PowerShell 디버거에는 중단점을 설정 하 고, 중단점을 관리 하 고, 호출 스택을 볼 수 있는 일련의 cmdlet이 포함 되어 있습니다.

## <a name="debugger-cmdlets"></a>디버거 Cmdlet

PowerShell 디버거에는 다음과 같은 cmdlet 집합이 포함 되어 있습니다.

- `Set-PSBreakpoint`: 줄, 변수 및 명령에 대 한 중단점을 설정 합니다.
- `Get-PSBreakpoint`: 현재 세션의 중단점을 가져옵니다.
- `Disable-PSBreakpoint`: 현재 세션에서 중단점을 해제 합니다.
- `Enable-PSBreakpoint`: 현재 세션에서 중단점을 다시 사용 하도록 설정 합니다.
- `Remove-PSBreakpoint`: 현재 세션에서 중단점을 삭제 합니다.
- `Get-PSCallStack`: 현재 호출 스택을 표시 합니다.

## <a name="starting-and-stopping-the-debugger"></a>디버거 시작 및 중지

디버거를 시작 하려면 하나 이상의 중단점을 설정 합니다. 그런 다음 디버깅 하려는 스크립트, 명령 또는 함수를 실행 합니다.

중단점에 도달 하면 실행이 중지 되 고 컨트롤이 디버거로 전환 됩니다.

디버거를 중지 하려면 완료 될 때까지 스크립트, 명령 또는 함수를 실행 합니다. 또는를 입력 `stop` `t` 합니다.

### <a name="debugger-commands"></a>디버거 명령

PowerShell 콘솔에서 디버거를 사용 하는 경우 다음 명령을 사용 하 여 실행을 제어 합니다. Windows PowerShell ISE에서 디버그 메뉴의 명령을 사용 합니다.

참고: 다른 호스트 응용 프로그램에서 디버거를 사용 하는 방법에 대 한 자세한 내용은 호스트 응용 프로그램 설명서를 참조 하십시오.

- `s`, `StepInto` : 다음 문을 실행 한 다음 중지 합니다.

- `v`, `StepOver` : 다음 문을 실행 하지만 함수 및 호출을 건너뜁니다. 건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.

- `Ctrl+Break`: (ISE에서 모두 중단)은 PowerShell 콘솔 또는 Windows PowerShell ISE 내에서 실행 중인 스크립트로 중단 됩니다. <kbd>Ctrl</kbd> + Windows PowerShell 2.0, 3.0 및 4.0의 Ctrl<kbd>구분선</kbd> 은 프로그램을 닫습니다. 모두 중단은 대화형으로 실행 되는 로컬 및 원격 스크립트 모두에서 작동 합니다.

- `o`, `StepOut` : 현재 함수에서 수행 되는 단계입니다. 중첩 된 경우에는 한 수준 위로 설정 합니다. 주 본문에서 끝 또는 다음 중단점까지 계속 합니다. 건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.

- `c`, `Continue` : 스크립트가 완료 될 때까지 또는 다음 중단점에 도달할 때까지 계속 실행 됩니다. 건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.

- `l`, `List` : 실행 중인 스크립트의 일부를 표시 합니다. 기본적으로 현재 줄, 5 개의 이전 줄 및 10 개의 다음 줄을 표시 합니다.
  스크립트를 계속 나열 하려면 ENTER 키를 누릅니다.

- `l <m>`, `List` :로 지정 된 줄 번호로 시작 하는 스크립트의 16 줄을 표시 `<m>` 합니다.

- `l <m> <n>`, `List` : `<n>` 로 지정 된 줄 번호로 시작 하 여 스크립트의 줄을 표시 합니다 `<m>` .

- `q`, `Stop` , `Exit` : 스크립트 실행을 중지 하 고 디버거를 종료 합니다. Cmdlet을 실행 하 여 작업을 디버깅 하는 경우이 `Debug-Job` `Exit` 명령은 디버거를 분리 하 고 작업을 계속 실행 하도록 허용 합니다.

- `k`, `Get-PsCallStack` : 현재 호출 스택을 표시 합니다.

- `<Enter>`: 단계, 스텝 오버 (v) 또는 목록 (l) 인 경우 마지막 명령을 반복 합니다. 그렇지 않으면는 제출 동작을 나타냅니다.

- `?`, `h` : 디버거 명령 도움말을 표시 합니다.

디버거를 종료 하려면 Stop (q)을 사용할 수 있습니다.

PowerShell 5.0부터 끝내기 명령을 실행 하 여 또는를 실행 하 여 시작한 중첩 된 디버깅 세션을 종료할 수 있습니다 `Debug-Job` `Debug-Runspace` .

이러한 디버거 명령을 사용 하면 스크립트를 실행 하 고, 문제 발생 지점에서 중지 하 고, 변수의 값과 시스템 상태를 검사 하 고, 문제를 식별할 때까지 스크립트를 계속 실행할 수 있습니다.

참고: ">"와 같은 리디렉션 연산자를 사용 하 여 문을 한 단계씩 실행 하는 경우 PowerShell 디버거는 스크립트의 나머지 모든 문을 실행 합니다.

스크립트 변수의 값 표시

디버거를 사용 하는 동안 명령을 입력 하 고, 변수 값을 표시 하 고, cmdlet을 사용 하 고, 명령줄에서 스크립트를 실행할 수도 있습니다.

다음 자동 변수를 제외 하 고 디버깅 중인 스크립트에 모든 변수의 현재 값을 표시할 수 있습니다.

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

이러한 변수의 값을 표시하려는 경우 스크립트의 변수 값이 아니라 디버거가 사용하는 내부 파이프라인의 해당 변수 값을 가져옵니다.

디버깅할 스크립트에 대해 이러한 변수 값을 표시 하려면 스크립트에서 자동 변수의 값을 새 변수에 할당 합니다. 그런 다음 새 변수의 값을 표시할 수 있습니다.

예를 들면 다음과 같습니다.

```powershell
$scriptArgs = $Args
$scriptArgs
```

이 항목의 예제에서는 변수 값이 다음과 같이 다시 `$MyInvocation` 할당 됩니다.

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a>디버거 환경

중단점에 도달 하면 디버거 환경을 시작 합니다. 명령 프롬프트는 "[DBG]:"으로 시작 되도록 변경 됩니다.

프롬프트를 사용자 지정 하는 방법에 대 한 자세한 내용은 [about_Prompts](about_prompts.md)를 참조 하세요.

또한 PowerShell 콘솔과 같은 일부 호스트 응용 프로그램 (Windows PowerShell ISE (통합 스크립팅 환경)에는 포함 되지 않음)에서는 디버깅을 위해 중첩 된 프롬프트가 열립니다. 명령 프롬프트에 표시 되는 반복 보다 큼 문자 (ASCII 62)로 중첩 된 프롬프트를 검색할 수 있습니다.

예를 들어 PowerShell 콘솔의 기본 디버깅 프롬프트는 다음과 같습니다.

```
[DBG]: PS (get-location)>>>
```

자동 변수를 사용 하 여 중첩 수준을 찾을 수 있습니다 `$NestedPromptLevel` .

또한 자동 변수인는 `$PSDebugContext` 로컬 범위에 정의 됩니다. 변수의 현재 상태를 사용 하 여 디버거를 사용 하 고 `$PsDebugContext` 있는지 여부를 확인할 수 있습니다.

다음은 그 예입니다. 

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

디버깅에서 변수의 값을 사용할 수 있습니다 `$PSDebugContext` .

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a>디버깅 및 범위

디버거를 중단 해도 작업 중인 범위는 변경 되지 않지만 스크립트의 중단점에 도달 하면 스크립트 범위로 이동 합니다. 스크립트 범위는 디버거를 실행 한 범위의 자식입니다.

스크립트 범위에 정의 된 변수와 별칭을 찾으려면 또는 cmdlet의 Scope 매개 변수를 사용 `Get-Alias` `Get-Variable` 합니다.

예를 들어 다음 명령은 로컬 (스크립트) 범위에서 변수를 가져옵니다.

```powershell
Get-Variable -scope 0
```

명령의 약어는 다음과 같이 지정할 수 있습니다.

```powershell
gv -s 0
```

이 방법은 스크립트에서 정의한 변수와 디버깅 중에 정의한 변수만 확인 하는 데 유용 합니다.

명령줄에서 디버깅

변수 중단점 또는 명령 중단점을 설정 하는 경우 스크립트 파일에만 중단점을 설정할 수 있습니다. 그러나 기본적으로 중단점은 현재 세션에서 실행 되는 모든 항목에 대해 설정 됩니다.

예를 들어 변수에 중단점을 설정 하는 경우 `$name` 디버거는 `$name` 중단점을 사용 하지 않도록 설정 하거나 제거할 때까지 실행 되는 스크립트, 명령, 함수, 스크립트 cmdlet 또는 식의 모든 변수에 대해 중단 됩니다.

이를 통해 세션 및 사용자의 프로필에 있는 함수, 변수 및 기타 스크립트의 영향을 받을 수 있는 보다 현실적인 컨텍스트에서 스크립트를 디버그할 수 있습니다.

줄 중단점은 스크립트 파일에만 적용 되므로 스크립트 파일에만 설정 됩니다.

## <a name="debugging-functions"></a>디버깅 함수

, 및 섹션이 있는 함수에 중단점을 설정 하면 `Begin` `Process` `End` 디버거가 각 섹션의 첫 번째 줄에서 중단 됩니다.

다음은 그 예입니다. 

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a>원격 스크립트 디버깅

PowerShell 5.0부터 콘솔 또는 Windows PowerShell ISE 원격 세션에서 PowerShell 디버거를 실행할 수 있습니다.
`Enter-PSSession` 원격 컴퓨터에서 실행 되 고 있으며 현재 스크립트를 실행 하는 연결이 끊어진 세션에 다시 연결 하 여 입력할 수 있도록 기능이 업데이트 되었습니다. 실행 중인 스크립트가 중단점에 도달 하면 클라이언트 세션이 자동으로 디버거를 시작 합니다.

다음은 줄 6, 11, 22 및 25의 스크립트에 중단점을 설정 하 여이 작업을 수행 하는 방법을 보여 주는 예제입니다. 이 예제에서는 디버거가 시작 될 때 두 가지 확인 메시지가 표시 됩니다. 여기에는 세션이 실행 중인 컴퓨터의 이름이 표시 되 고, 사용자에 게 디버깅 모드를 알리는 데 사용 되는 DBG 프롬프트가 표시 됩니다.

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a>예

이 테스트 스크립트는 운영 체제의 버전을 검색 하 고 시스템에 적절 한 메시지를 표시 합니다. 여기에는 함수, 함수 호출 및 변수가 포함 됩니다.

다음 명령은 테스트 스크립트 파일의 내용을 표시 합니다.

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

시작 하려면 스크립트의 관심 지점 (예: 줄, 명령, 변수 또는 함수)에서 중단점을 설정 합니다.

현재 디렉터리에 있는 Test.ps1 스크립트의 첫 번째 줄에 줄 중단점을 만들어 시작 합니다.

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

이 명령을

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

이 명령은 줄 중단점 개체 ( **system.web** )를 반환 합니다.

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

이제 스크립트를 시작 합니다.

```powershell
PS C:\ps-test> .\test.ps1
```

스크립트가 첫 번째 중단점에 도달 하면 디버거가 활성 상태임을 나타내는 중단점 메시지가 표시 됩니다. 중단점을 설명 하 고 스크립트의 첫 번째 줄 (함수 선언)을 미리 봅니다. 또한 명령 프롬프트를 변경 하 여 디버거에 제어가 있음을 나타낼 수 있습니다.

미리 보기 줄에는 미리 보기 된 명령의 스크립트 이름 및 줄 번호가 포함 됩니다.

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

단계 명령을 사용 하 여 스크립트에서 첫 번째 문을 실행 하 고 다음 문을 미리 봅니다. 다음 문은 자동 변수를 사용 하 여 `$MyInvocation` 변수 값을 `$scriptName` 스크립트 파일의 경로 및 파일 이름으로 설정 합니다.

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

이 시점에서 변수는 `$scriptName` 채워지지 않지만 값을 표시 하 여 변수의 값을 확인할 수 있습니다. 이 경우 값은 `$null`입니다.

```powershell
DBG> $scriptname
# DBG>
```

다른 단계 명령을 사용 하 여 현재 문을 실행 하 고 스크립트에서 다음 문을 미리 봅니다. 다음 문은 PsVersion 함수를 호출 합니다.

```powershell
DBG> s
test.ps1:12  psversion
```

이 시점에서 변수는 `$scriptName` 채워지며 값을 표시 하 여 변수의 값을 확인 합니다. 이 경우 값은 스크립트 경로로 설정 됩니다.

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

다른 단계 명령을 사용 하 여 함수 호출을 실행 합니다. ENTER 키를 누르거나 단계에 "s"를 입력 합니다.

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

디버그 메시지에는 함수의 문 미리 보기가 포함 되어 있습니다. 이 문을 실행 하 고 함수에서 다음 문을 미리 보려면 명령을 사용할 수 있습니다 `Step` . 그러나이 경우에는 StepOut 명령 (o)을 사용 합니다. 이 함수는 중단점에 도달 하지 않는 한 함수 실행을 완료 하 고 스크립트의 다음 문으로의 단계를 수행 합니다.

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

스크립트의 마지막 문이 있기 때문에 Step, StepOut 및 Continue 명령은 동일한 효과를 가집니다. 이 경우 StepOut (o)를 사용 합니다.

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

StepOut 명령은 마지막 명령을 실행 합니다. 표준 명령 프롬프트는 디버거가 종료 되 고 제어를 명령 프로세서로 반환 했음을 나타냅니다.

이제 디버거를 다시 실행 합니다. 먼저, 현재 중단점을 삭제 하려면 `Get-PsBreakpoint` 및 cmdlet을 사용 `Remove-PsBreakpoint` 합니다. (중단점을 다시 사용할 수 있다고 생각 되는 경우 `Disable-PsBreakpoint` 대신 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.)

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

이 명령을

```powershell
PS C:\ps-test> gbp | rbp
```

또는 다음 함수와 같이 함수를 작성 하 여 명령을 실행 합니다.

```powershell
function delbr { gbp | rbp }
```

이제 변수에 중단점을 만듭니다 `$scriptname` .

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

명령의 약어는 다음과 같이 지정할 수 있습니다.

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

이제 스크립트를 시작 합니다. 스크립트는 변수 중단점에 도달 합니다. 기본 모드는 Write 이므로 실행이 변수 값을 변경 하는 문 바로 앞으로 중지 됩니다.

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

변수의 현재 값 `$scriptName` 을 표시 `$null` 합니다.

```powershell
DBG> $scriptName
# DBG>
```

단계 명령을 사용 하 여 변수를 채우는 문을 실행 합니다.
그런 다음 변수의 새 값을 표시 `$scriptName` 합니다.

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

다음 문은 PsVersion 함수를 호출 하는 것입니다. 함수를 건너뛰고 계속 실행 하려면 스텝 오버 명령 (v)을 사용 합니다. 스텝 오버를 사용할 때 함수에 이미 있는 경우에는 적용 되지 않습니다. 함수 호출이 표시 되지만 실행 되지 않습니다.

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

스텝 오버 명령은 함수를 실행 하 고 스크립트에서 마지막 줄을 출력 하는 다음 문을 미리 봅니다.

Stop 명령 (t)을 사용 하 여 디버거를 종료 합니다. 명령 프롬프트가 표준 명령 프롬프트로 돌아갑니다.

```powershell
C:\ps-test>
```

중단점을 삭제 하려면 `Get-PsBreakpoint` 및 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

PsVersion 함수에 새 명령 중단점을 만듭니다.

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

이 명령의 약어를 다음과 같이 지정할 수 있습니다.

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

이제 스크립트를 실행 합니다.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

스크립트는 함수 호출에서 중단점에 도달 합니다. 이 시점에서 함수는 아직 호출 되지 않았습니다. 이를 통해의 Action 매개 변수를 사용 하 여 `Set-PSBreakpoint` 중단점 실행 조건을 설정 하거나 준비 또는 진단 작업 (예: 로그 시작 또는 진단 또는 보안 스크립트 호출)을 수행할 수 있습니다.

동작을 설정 하려면 Continue 명령 (c)을 사용 하 여 스크립트를 종료 하 고 `Remove-PsBreakpoint` 현재 중단점을 삭제 하는 명령을 사용 합니다. 중단점은 읽기 전용 이므로 현재 중단점에 작업을 추가할 수 없습니다.

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

이제 작업을 사용 하 여 새 명령 중단점을 만듭니다. 다음 명령은 `$scriptName` 함수가 호출 될 때 변수의 값을 기록 하는 작업을 사용 하 여 명령 중단점을 설정 합니다. Break 키워드는 작업에 사용 되지 않으므로 실행이 중지 되지 않습니다. (억음 (')은 줄 연속 문자입니다.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

중단점에 대 한 조건을 설정 하는 작업을 추가할 수도 있습니다. 다음 명령에서 명령 중단점은 실행 정책이 RemoteSigned로 설정 된 경우에만 실행 됩니다. 단, 스크립트 실행을 허용 하는 가장 제한적인 정책입니다. (억음 (')은 연속 문자입니다.)

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

작업의 Break 키워드는 중단점을 실행 하도록 디버거에 지시 합니다.
Continue 키워드를 사용 하 여 디버거가 중단 없이 실행 되도록 지시할 수도 있습니다. Default 키워드가 Continue 이므로 중단을 지정 하 여 실행을 중지 해야 합니다.

이제 스크립트를 실행 합니다.

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

실행 정책이 **RemoteSigned** 로 설정 되어 있기 때문에 함수 호출에서 실행이 중지 됩니다.

이 시점에서 호출 스택을 확인 하는 것이 좋습니다. `Get-PsCallStack`Cmdlet 또는 `Get-PsCallStack` 디버거 명령 (k)을 사용 합니다. 다음 명령은 현재 호출 스택을 가져옵니다.

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

이 예제에서는 PowerShell 디버거를 사용 하는 여러 가지 방법을 보여 줍니다.

디버거 cmdlet에 대 한 자세한 내용을 보려면 다음 명령을 입력 하십시오.

```powershell
help <cmdlet-name> -full
```

예를 들어 다음과 같이 입력합니다.

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a>PowerShell의 기타 디버깅 기능

Powershell 디버거 외에도 PowerShell에는 스크립트 및 함수를 디버그 하는 데 사용할 수 있는 몇 가지 다른 기능이 포함 되어 있습니다.

- Windows PowerShell ISE에는 대화형 그래픽 디버거가 포함 되어 있습니다. 자세한 내용을 보려면 Windows PowerShell ISE를 시작 하 고 F1 키를 누릅니다.

- `Set-PSDebug`Cmdlet은 단계별 실행 및 추적을 포함 하 여 매우 기본적인 스크립트 디버깅 기능을 제공 합니다.

- Cmdlet을 사용 하 여 초기화 되지 않은 변수에 대 한 `Set-StrictMode` 참조를 검색 하 고, 개체의 존재 하지 않는 속성에 대 한 참조를 검색 하 고, 유효 하지 않은 함수 구문을 사용 합니다.

- 변수 값을 표시 하는 문, 명령줄에서 입력을 읽는 문 또는 현재 명령을 보고 하는 문과 같은 진단 문을 스크립트에 추가 합니다. 이 작업에 대 한 쓰기 동사를 포함 하는 cmdlet (예:,, 및)을 사용 `Write-Host` `Write-Debug` `Write-Warning` `Write-Verbose` 합니다.

## <a name="see-also"></a>참고 항목

- [사용 안 함-PsBreakpoint](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [-PsBreakpoint 사용 됩니다.](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [Get PsBreakpoint](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [Get PsCallStack](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [-PsBreakpoint을 제거 합니다.](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [Set-PSBreakpoint](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [Write-Debug](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose)

