---
description: PowerShell에 대 한 상태 정보를 저장 하는 변수에 대해 설명 합니다. 이러한 변수는 PowerShell에서 만들고 유지 관리 합니다.
Locale: en-US
ms.date: 12/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: 82fc08a49b58b9518cfa50be916cf2889b5007d2
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577227"
---
# <a name="about-automatic-variables"></a>자동 변수 정보

## <a name="short-description"></a>간단한 설명

PowerShell에 대 한 상태 정보를 저장 하는 변수에 대해 설명 합니다. 이러한 변수는 PowerShell에서 만들고 유지 관리 합니다.

## <a name="long-description"></a>자세한 설명입니다.

개념적으로 이러한 변수는 읽기 전용으로 간주 됩니다. 이전 버전과의 호환성을 위해 쓸 수 **있는** 경우에도 쓸 수 **없습니다** .

PowerShell의 자동 변수 목록은 다음과 같습니다.

### <a name=""></a>$$

세션에서 받은 마지막 줄의 마지막 토큰을 포함 합니다.

### <a name=""></a>$?

마지막 명령의 실행 상태를 포함 합니다. 마지막 명령이 성공한 경우 **True** 를 포함 하 고 실패 하면 **False** 를 포함 합니다.

파이프라인의 여러 단계에서 실행 되는 cmdlet 및 고급 함수 (예: 및 블록 둘 다)의 경우 `process` `end` 언제 든 지 또는를 호출 하는 것은 및와 같이 모두 `this.WriteError()` `$PSCmdlet.WriteError()` `$?` **False** 로 설정 됩니다 `this.ThrowTerminatingError()` `$PSCmdlet.ThrowTerminatingError()` .

`Write-Error`Cmdlet은 `$?` 실행 후에 항상 **false** 로 설정 되지만 `$?` 함수를 호출 하는 함수에 대해 **false** 로 설정 되지 않습니다.

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

후자의 경우에 `$PSCmdlet.WriteError()` 는 대신를 사용 해야 합니다.

네이티브 명령 (실행 파일)의 경우가 0 이면이 `$?` **True** 로 설정 되 `$LASTEXITCODE` 고,가 다른 값 이면 **False** 로 설정 됩니다 `$LASTEXITCODE` .

> [!NOTE]
> 괄호 안에 문을 포함 하는 PowerShell 7 까지는 `(...)` 부분식 구문 `$(...)` 또는 배열 식이 `@(...)` 항상 true로 다시 설정 `$?` 되므로가  `(Write-Error)` `$?` **true** 로 표시 됩니다.
> 이는 PowerShell 7에서 변경 되었으므로 `$?` 항상 이러한 식에서 실행 된 마지막 명령의 실제 성공을 반영 합니다.

### <a name=""></a>$^

세션에서 받은 마지막 줄의 첫 번째 토큰을 포함 합니다.

### <a name="_"></a>$_

`$PSItem`와 동일합니다. 파이프라인 개체의 현재 개체를 포함 합니다. 파이프라인의 모든 개체 또는 선택한 개체에 대해 작업을 수행 하는 명령에서이 변수를 사용할 수 있습니다.

### <a name="args"></a>$args

함수, 스크립트 또는 스크립트 블록에 전달 되는 선언 되지 않은 매개 변수에 대 한 값 배열을 포함 합니다. 함수를 만들 때 키워드를 사용 `param` 하거나 함수 이름 뒤에 괄호 안에 쉼표로 구분 된 매개 변수 목록을 추가 하 여 매개 변수를 선언할 수 있습니다.

이벤트 동작에서 `$Args` 변수는 처리 중인 이벤트의 이벤트 인수를 나타내는 개체를 포함 합니다. 이 변수는 `Action` 이벤트 등록 명령의 블록 내 에서만 채워집니다.
이 변수의 값은를 반환 하는 **PSEventArgs** 개체의 **sourceargs** 속성 에서도 찾을 수 있습니다 `Get-Event` .

### <a name="consolefilename"></a>$ConsoleFileName

세션에서 가장 최근에 사용 된 콘솔 파일 ()의 경로를 포함 `.psc1` 합니다. 이 변수는 **PSConsoleFile** 매개 변수를 사용 하 여 PowerShell을 시작 하거나 cmdlet을 사용 하 여 `Export-Console` 스냅인 이름을 콘솔 파일로 내보내는 경우에 채워집니다.

`Export-Console`매개 변수 없이 cmdlet을 사용 하는 경우 세션에서 가장 최근에 사용 된 콘솔 파일을 자동으로 업데이트 합니다. 이 자동 변수를 사용 하 여 업데이트 되는 파일을 확인할 수 있습니다.

### <a name="error"></a>$Error

가장 최근의 오류를 나타내는 오류 개체의 배열을 포함 합니다.
가장 최근의 오류는 배열의 첫 번째 오류 개체입니다 `$Error[0]` .

오류가 배열에 추가 되지 않도록 하려면 `$Error` **Ignore** 값에 **erroraction** 일반 매개 변수를 사용 합니다. 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.

### <a name="event"></a>$Event

처리 중인 이벤트를 나타내는 **PSEventArgs** 개체를 포함 합니다. 이 변수는 `Action` 와 같은 이벤트 등록 명령의 블록 내 에서만 채워집니다 `Register-ObjectEvent` . 이 변수의 값은 cmdlet이 반환 하는 것과 동일한 개체입니다 `Get-Event` . 따라서 `Event` 와 같은 변수의 속성을 `$Event.TimeGenerated` 스크립트 블록에서 사용할 수 있습니다 `Action` .

### <a name="eventargs"></a>$EventArgs

처리 중인 이벤트의 **EventArgs** 에서 파생 되는 첫 번째 이벤트 인수를 나타내는 개체를 포함 합니다. 이 변수는 `Action` 이벤트 등록 명령의 블록 내 에서만 채워집니다.
이 변수의 값은를 반환 하는 **PSEventArgs** 개체의 **sourceeventargs** 속성 에서도 찾을 수 있습니다 `Get-Event` .

### <a name="eventsubscriber"></a>$EventSubscriber

처리 중인 이벤트의 이벤트 구독자를 나타내는 **PSEventSubscriber** 개체를 포함 합니다. 이 변수는 `Action` 이벤트 등록 명령의 블록 내 에서만 채워집니다. 이 변수의 값은 cmdlet이 반환 하는 것과 동일한 개체입니다 `Get-EventSubscriber` .

### <a name="executioncontext"></a>$ExecutionContext

PowerShell 호스트의 실행 컨텍스트를 나타내는 **EngineIntrinsics** 개체를 포함 합니다. 이 변수를 사용 하 여 cmdlet에서 사용할 수 있는 실행 개체를 찾을 수 있습니다.

### <a name="false"></a>$false

**False** 를 포함 합니다. "False" 문자열을 사용 하는 대신이 변수를 사용 하 여 명령 및 스크립트에서 **False** 를 나타낼 수 있습니다. 문자열은 비어 있지 않은 문자열이 나 0이 아닌 정수로 변환 되는 경우 **True** 로 해석 될 수 있습니다.

### <a name="foreach"></a>$foreach

[ForEach](about_ForEach.md) 루프의 결과 값이 아니라 열거자를 포함 합니다. `$ForEach`변수는 루프가 실행 되는 동안에만 존재 합니다. `ForEach` 루프가 완료 된 후에는 삭제 됩니다.

열거자는 루프 값을 검색 하 고 현재 루프 반복을 변경 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다. 자세한 내용은 [열거자 사용](#using-enumerators)을 참조 하세요.

### <a name="home"></a>$HOME

사용자의 홈 디렉터리에 대 한 전체 경로를 포함 합니다. 이 변수는 `"$env:homedrive$env:homepath"` 일반적으로 Windows 환경 변수에 해당 합니다 `C:\Users\<UserName>` .

### <a name="host"></a>$Host

PowerShell에 대 한 현재 호스트 응용 프로그램을 나타내는 개체를 포함 합니다. 이 변수를 사용 하 여 명령의 현재 호스트를 나타내거나 또는 등의 호스트 속성을 표시 하거나 변경할 수 있습니다 `$Host.version` `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` .

### <a name="input"></a>$input

함수에 전달 되는 모든 입력을 열거 하는 열거자를 포함 합니다. `$input`변수는 함수 및 스크립트 블록 (명명 되지 않은 함수) 에서만 사용할 수 있습니다.

- `Begin`, 또는 블록이 없는 함수에서 `Process` `End` `$input` 변수는 함수에 대 한 모든 입력의 컬렉션을 열거 합니다.

- 블록에서 `Begin` `$input` 변수에는 데이터가 포함 되지 않습니다.

- 블록에서 `Process` `$input` 변수는 현재 파이프라인에 있는 개체를 포함 합니다.

- 블록에서 `End` `$input` 변수는 함수에 대 한 모든 입력의 컬렉션을 열거 합니다.

  > [!NOTE]
  > `$input`동일한 함수 또는 스크립트 블록의 프로세스 블록과 끝 블록 내에서 변수를 사용할 수 없습니다.

`$input`는 열거자 이므로 해당 속성에 액세스 하면 `$input` 더 이상 사용할 수 없게 됩니다. `$input`다른 변수에 저장 하 여 속성을 다시 사용할 수 있습니다 `$input` .

열거자는 루프 값을 검색 하 고 현재 루프 반복을 변경 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다. 자세한 내용은 [열거자 사용](#using-enumerators)을 참조 하세요.

`$input`변수는 `-Command` `pwsh` 명령줄에서 호출 될 때 매개 변수에서 지정 하는 명령에도 사용할 수 있습니다. 다음 예제는 Windows 명령 셸에서 실행 됩니다.

```CMD
echo Hello | powershell -Command """$input World!"""
```

### <a name="lastexitcode"></a>$LastExitCode

실행 된 마지막 Windows 기반 프로그램의 종료 코드를 포함 합니다.

### <a name="matches"></a>$Matches

`Matches`변수는 및 연산자와 함께 작동 `-match` `-notmatch` 합니다.
스칼라 입력을 or 연산자에 제출 `-match` 하 `-notmatch` 고 하나는 일치 항목을 검색 하는 경우 부울 값을 반환 하 고 `$Matches` 일치 하는 모든 문자열 값의 해시 테이블을 사용 하 여 자동 변수를 채웁니다. 연산자를 사용 하 여 `$Matches` 정규식을 사용 하는 경우에는 해시 테이블을 캡처로 채울 수도 있습니다 `-match` .

연산자에 대 한 자세한 내용은 `-match` [about_Comparison_Operators](about_comparison_operators.md)를 참조 하세요. 정규식에 대 한 자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.

### <a name="myinvocation"></a>$MyInvocation

현재 명령에 대 한 정보 (예: 이름, 매개 변수, 매개 변수 값) 및 명령이 시작, 호출 또는 호출 된 방법에 대 한 정보를 포함 합니다.

`$MyInvocation` 는 스크립트, 함수 및 스크립트 블록에 대해서만 채워집니다. 현재 스크립트에서 반환 하는 정보  `$MyInvocation` (예: 스크립트의 경로 및 파일 이름 ( `$MyInvocation.MyCommand.Path` ) 또는 함수 이름 ( `$MyInvocation.MyCommand.Name` ))를 사용 하 여 현재 명령을 식별할 수 있습니다. 이는 현재 스크립트의 이름을 찾는 데 특히 유용 합니다.

PowerShell 3.0부터에는 `MyInvocation` 다음과 같은 새 속성이 있습니다.

| 속성      | 설명                                         |
| ------------- | --------------------------------------------------- |
| **PSScriptRoot**  | 호출 된 스크립트에 대 한 전체 경로를 포함 합니다.   |
|               | 현재 명령입니다. 이 속성의 값은입니다.  |
|               | 호출자가 스크립트인 경우에만 채워집니다.         |
| **PSCommandPath** | 스크립트의 전체 경로 및 파일 이름을 포함 합니다.  |
|               | 현재 명령을 호출한입니다. 이의 값입니다. |
|               | 호출자가 인 경우에만 속성이 채워집니다.     |
|               | 스크립트를 제출하고 실행합니다.                                             |

`$PSScriptRoot`및 `$PSCommandPath` 자동 변수와 달리 자동 변수의 **Psscriptroot** 및 **psscriptroot** 속성은 `$MyInvocation` 현재 스크립트가 아니라 호출자 또는 호출 스크립트에 대 한 정보를 포함 합니다.

### <a name="nestedpromptlevel"></a>$NestedPromptLevel

현재 프롬프트 수준을 포함 합니다. 값 0은 원래 프롬프트 수준을 나타냅니다. 중첩 된 수준을 입력 하면 값이 증가 하 고 종료 될 때 감소 합니다.

예를 들어, 메서드를 사용할 때 PowerShell에서 중첩 된 명령 프롬프트를 표시 합니다 `$Host.EnterNestedPrompt` . Powershell은 PowerShell 디버거의 중단점에 도달 하는 경우에도 중첩 된 명령 프롬프트를 제공 합니다.

중첩 된 프롬프트를 입력 하면 PowerShell에서 현재 명령을 일시 중지 하 고, 실행 컨텍스트를 저장 하 고, 변수 값을 증가 시킵니다 `$NestedPromptLevel` . 추가 중첩 된 명령 프롬프트 (최대 128 수준)를 만들거나 원래 명령 프롬프트로 돌아가려면 명령을 완료 하거나를 입력 `exit` 합니다.

`$NestedPromptLevel`변수를 사용 하면 프롬프트 수준을 추적할 수 있습니다. 이 값을 포함 하는 대체 PowerShell 명령 프롬프트를 만들어 항상 표시 되도록 할 수 있습니다.

### <a name="null"></a>$null

`$null`**null** 또는 빈 값을 포함 하는 자동 변수입니다. 이 변수를 사용 하 여 명령 및 스크립트에 없거나 정의 되지 않은 값을 나타낼 수 있습니다.

PowerShell `$null` 은 값, 즉 명시적 자리 표시자로 개체를 처리 하므로를 사용 `$null` 하 여 일련의 값에서 빈 값을 나타낼 수 있습니다.

예를 들어 `$null` 가 컬렉션에 포함 되어 있으면 개체 중 하나로 계산 됩니다.

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

변수를 cmdlet에 파이프 하는 경우 `$null` `ForEach-Object` `$null` 다른 개체의 경우와 마찬가지로에 대 한 값을 생성 합니다.

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

따라서 `$null` 를 사용 하 여 **매개 변수 값을 의미 하지 않습니다**. 의 매개 변수 값이 `$null` 기본 매개 변수 값을 재정의 합니다.

그러나 PowerShell은 변수를 자리 표시자로 처리 하기 때문에 `$null` 다음과 같은 스크립트에서 사용할 수 있습니다 .이 변수는 무시 되는 경우 작동 하지 `$null` 않습니다.

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a>$PID

현재 PowerShell 세션을 호스트 하는 프로세스의 PID (프로세스 식별자)를 포함 합니다.

### <a name="profile"></a>$PROFILE

현재 사용자와 현재 호스트 응용 프로그램에 대 한 PowerShell 프로필의 전체 경로를 포함 합니다. 이 변수를 사용 하 여 명령에 프로필을 나타낼 수 있습니다. 예를 들어 명령에 사용 하 여 프로필이 생성 되었는지 여부를 확인할 수 있습니다.

```powershell
Test-Path $PROFILE
```

또는 명령에서 사용 하 여 프로필을 만들 수 있습니다.

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

명령에서이를 사용 하 여 **notepad.exe** 에서 프로필을 열 수 있습니다.

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a>$PSBoundParameters

스크립트나 함수 및 현재 값에 전달 되는 매개 변수의 사전을 포함 합니다. 이 변수에는 스크립트나 함수와 같은 매개 변수가 선언 된 범위에만 있는 값이 있습니다. 매개 변수의 현재 값을 표시 하거나 변경 하거나 매개 변수 값을 다른 스크립트나 함수에 전달 하는 데 사용할 수 있습니다.

이 예제에서 **Test2** 함수는를 `$PSBoundParameters` **Test1** 함수에 전달 합니다. 는 `$PSBoundParameters` **키** 와 **값** 의 형식으로 표시 됩니다.

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a>$PSCmdlet

실행 되는 cmdlet 또는 고급 함수를 나타내는 개체를 포함 합니다.

Cmdlet 또는 함수 코드에서 개체의 속성 및 메서드를 사용 하 여 사용 조건에 응답할 수 있습니다. 예를 들어 **ParameterSetName** 속성은 사용 중인 매개 변수 집합의 이름을 포함 하 고, **Shouldprocess** 메서드는 **WhatIf** 및 **Confirm** 매개 변수를 cmdlet에 동적으로 추가 합니다.

자동 변수에 대 한 자세한 내용은 `$PSCmdlet` [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) 및 [about_Functions_Advanced](about_Functions_Advanced.md)를 참조 하세요.

### <a name="pscommandpath"></a>$PSCommandPath

실행 되는 스크립트의 전체 경로 및 파일 이름을 포함 합니다. 이 변수는 모든 스크립트에서 유효 합니다.

### <a name="psculture"></a>$PSCulture

운영 체제에서 현재 사용 중인 문화권의 이름을 포함 합니다. 문화권에 따라 숫자, 통화 및 날짜와 같은 항목의 표시 형식이 결정 되 고,이는 **system.object** 개체에 저장 됩니다. `Get-Culture`를 사용 하 여 컴퓨터의 문화권을 표시 합니다. `$PSCulture`**이름** 속성의 값을 포함 합니다.

### <a name="psdebugcontext"></a>$PSDebugContext

디버깅 하는 동안이 변수는 디버깅 환경에 대 한 정보를 포함 합니다. 그렇지 않으면 **null** 값이 포함 됩니다. 따라서 디버거에서 컨트롤을 사용할 수 있는지 여부를 나타내는 데 사용할 수 있습니다. 채워진 경우 **중단점과** **InvocationInfo** 속성을 포함 하는 **psdebugcontext** 개체를 포함 합니다. **InvocationInfo** 속성은 **Location** 속성을 포함 하 여 몇 가지 유용한 속성을 포함 합니다. **Location** 속성은 디버깅 중인 스크립트의 경로를 나타냅니다.

### <a name="pshome"></a>$PSHOME

일반적으로 Windows 시스템에서 PowerShell에 대 한 설치 디렉터리의 전체 경로를 포함 합니다 `$env:windir\System32\PowerShell\v1.0` . PowerShell 파일의 경로에이 변수를 사용할 수 있습니다. 예를 들어 다음 명령은 단어 **변수에** 대 한 개념 도움말 항목을 검색 합니다.

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a>$PSItem

`$_`와 동일합니다. 파이프라인 개체의 현재 개체를 포함 합니다. 파이프라인의 모든 개체 또는 선택한 개체에 대해 작업을 수행 하는 명령에서이 변수를 사용할 수 있습니다.

### <a name="psscriptroot"></a>$PSScriptRoot

스크립트가 실행 되는 디렉터리를 포함 합니다.

PowerShell 2.0에서이 변수는 스크립트 모듈 () 에서만 사용할 수 `.psm1` 있습니다.
PowerShell 3.0부터 모든 스크립트에서 유효 합니다.

### <a name="pssenderinfo"></a>$PSSenderInfo

사용자 id 및 원래 컴퓨터의 표준 시간대를 포함 하 여 PSSession을 시작한 사용자에 대 한 정보를 포함 합니다. 이 변수는 PSSessions 에서만 사용할 수 있습니다.

`$PSSenderInfo`변수에는 기본적으로 원래 세션의만 포함 하는 사용자 구성 속성인 **applicationarguments** 가 포함 됩니다 `$PSVersionTable` . **Applicationarguments** 속성에 데이터를 추가 하려면 Cmdlet의 **applicationarguments** 매개 변수를 사용 합니다 `New-PSSessionOption` .

### <a name="psuiculture"></a>$PSUICulture

운영 체제에서 현재 사용 중인 UI (사용자 인터페이스) 문화권의 이름을 포함 합니다. UI 문화권에 따라 메뉴, 메시지 등의 사용자 인터페이스 요소에 사용되는 텍스트 문자열이 결정됩니다. 시스템의 **System.Globalization.CultureInfo.CurrentUICulture.Name** 속성 값입니다. 시스템에 대 한 **시스템 세계화 CultureInfo** 개체를 가져오려면 cmdlet을 사용 합니다 `Get-UICulture` .

### <a name="psversiontable"></a>$PSVersionTable

현재 세션에서 실행 중인 PowerShell 버전에 대 한 세부 정보를 표시 하는 읽기 전용 해시 테이블을 포함 합니다. 테이블에는 다음 항목이 포함 되어 있습니다.

| 속성                  | 설명                                   |
| ------------------------- | --------------------------------------------- |
| **BuildVersion**          | 현재 버전의 빌드 번호입니다.       |
| **CLRVersion**            | 공용 언어 런타임의 버전입니다.    |
|                           | CLR                                         |
| **PSCompatibleVersions**  | 호환 되는 PowerShell 버전    |
|                           | 현재 버전 사용                      |
| **PSEdition**             | 이 속성에는에 대 한 ' Desktop ' 값이 있습니다. |
|                           | Windows Server 및 Windows 클라이언트 버전   |
|                           | 이 속성의 값은     |
|                           | Nano 서버 또는에서 실행 되는 PowerShell       |
|                           | Windows IOT.                                  |
| **PSRemotingProtocolVersion** | PowerShell 원격의 버전      |
|                           | 관리 프로토콜.                          |
| **PSVersion**             | PowerShell 버전 번호                 |
| **SerializationVersion**  | Serialization 메서드의 버전입니다.       |
| **WSManStackVersion**     | WS-Management 스택의 버전 번호 |

### <a name="pwd"></a>$PWD

현재 디렉터리의 전체 경로를 나타내는 path 개체를 포함 합니다.

### <a name="sender"></a>$Sender

이 이벤트를 생성 한 개체를 포함 합니다. 이 변수는 이벤트 등록 명령의 작업 블록 내 에서만 채워집니다. 이 변수의 값은를 반환 하는 **PSEventArgs** 개체의 Sender 속성 에서도 찾을 수 있습니다 `Get-Event` .

### <a name="shellid"></a>$ShellId

현재 셸의 식별자를 포함 합니다.

### <a name="stacktrace"></a>$StackTrace

가장 최근의 오류에 대 한 스택 추적을 포함 합니다.

### <a name="switch"></a>$switch

문의 결과 값이 아닌 열거자를 포함 `Switch` 합니다. `$switch`변수는 문이 실행 되는 동안에만 존재 `Switch` 하며 `switch` 문이 실행을 완료 하면 삭제 됩니다. 자세한 내용은 [about_Switch](about_Switch.md)를 참조 하세요.

열거자는 루프 값을 검색 하 고 현재 루프 반복을 변경 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다. 자세한 내용은 [열거자 사용](#using-enumerators)을 참조 하세요.

### <a name="this"></a>$this

스크립트 속성이 나 스크립트 메서드를 정의 하는 스크립트 블록에서 변수는 `$this` 확장 중인 개체를 참조 합니다.

사용자 지정 클래스에서 변수는 클래스 `$this` 에 정의 된 속성 및 메서드에 대 한 액세스를 허용 하는 클래스 개체 자체를 참조 합니다.

### <a name="true"></a>$true

**True** 를 포함 합니다. 이 변수를 사용 하 여 명령 및 스크립트에서 **True** 를 나타낼 수 있습니다.

## <a name="using-enumerators"></a>열거자 사용

`$input`, `$foreach` 및 변수는 `$switch` 포함 하는 코드 블록에서 처리 하는 값을 반복 하는 데 사용 되는 모든 열거자입니다.

열거자는 반복을 이동 또는 다시 설정 하거나 반복 값을 검색 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다. 열거자를 직접 조작 하는 것은 모범 사례로 간주 되지 않습니다.

- 루프 내에서 흐름 제어 키워드를 [중단](about_Break.md) 하 고 [계속](about_Continue.md) 하는 것이 좋습니다.
- 파이프라인 입력을 허용 하는 함수 내에서 **ValueFromPipeline** 또는 **ValueFromPipelineByPropertyName** 특성과 함께 매개 변수를 사용 하는 것이 가장 좋습니다.

  자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.

### <a name="movenext"></a>MoveNext

[MoveNext](/dotnet/api/system.collections.ienumerator.movenext) 메서드는 열거자를 컬렉션의 다음 요소로 이동 합니다. **MoveNext** 는 열거자가 성공적으로 진행 되었으면 **True** 를 반환 하 고, 컬렉션의 끝을 지난 경우 **False** 를 반환 합니다.

> [!NOTE]
> **MoveNext** 에서 반환 된 **부울** 값은 출력 스트림으로 전송 됩니다.
> 출력을 typecasting으로 표시 하지 `[void]` 않거나 [Null](xref:Microsoft.PowerShell.Core.Out-Null)로 파이프 하 여 출력을 표시 하지 않을 수 있습니다.
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a>다시 설정

[Reset](/dotnet/api/system.collections.ienumerator.reset) 메서드는 컬렉션의 첫 번째 요소 **앞** 의 초기 위치로 열거자를 설정 합니다.

### <a name="current"></a>현재

[Current](/dotnet/api/system.collections.ienumerator.current) 속성은 컬렉션 또는 파이프라인에서 열거자의 현재 위치에 있는 요소를 가져옵니다.

**Current** 속성은 **MoveNext** 가 호출 될 때까지 계속 해 서 동일한 속성을 반환 합니다.

## <a name="examples"></a>예제

### <a name="example-1-using-the-input-variable"></a>예제 1: $input 변수 사용

다음 예제에서 변수에 액세스 하면 `$input` 다음 번에 프로세스 블록이 실행 될 때까지 변수가 지워집니다. **Reset** 메서드를 사용 하 여 `$input` 변수를 현재 파이프라인 값으로 다시 설정 합니다.

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

액세스 하지 않더라도 프로세스 블록에서 자동으로 변수를 이동 `$input` 합니다.

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a>예제 2: 프로세스 블록 외부에서 $input 사용

프로세스 블록 외부에서 변수는 `$input` 함수로 파이프 된 모든 값을 나타냅니다.

- 변수에 액세스 하면 `$input` 모든 값이 지워집니다.
- **Reset** 메서드는 전체 컬렉션을 다시 설정 합니다.
- **현재** 속성은 채워지지 않습니다.
- 컬렉션을 고급으로 사용할 수 없으므로 **MoveNext** 메서드에서 false를 반환 합니다.
  - **MoveNext** 를 호출 하면 `$input` 변수가 지워집니다.

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a>예 3: $input 사용 Current 속성

**현재** 속성을 사용 하 여 **Reset** 메서드를 사용 하지 않고 현재 파이프라인 값에 여러 번 액세스할 수 있습니다. 프로세스 블록은 **MoveNext** 메서드를 자동으로 호출 하지 않습니다.

**MoveNext** 를 명시적으로 호출 하지 않으면 **현재** 속성이 채워지지 않습니다. **현재** 속성은 해당 값을 지우지 않고 프로세스 블록 내에서 여러 번 액세스할 수 있습니다.

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a>예제 4: $foreach 변수 사용

변수와 달리 `$input` `$foreach` 변수는 항상 직접 액세스할 때 컬렉션의 모든 항목을 나타냅니다. **현재 속성을** 사용 하 여 현재 컬렉션 요소에 액세스 하 고, **Reset** 및 **MoveNext** 메서드를 사용 하 여 해당 값을 변경 합니다.

> [!NOTE]
> 루프의 각 반복 `foreach` 은 **MoveNext** 메서드를 자동으로 호출 합니다.

다음 루프는 두 번만 실행 됩니다. 두 번째 반복에서는 반복이 완료 되기 전에 컬렉션이 세 번째 요소로 이동 됩니다. 두 번째 반복 후에는 반복할 값이 더 이상 없으며 루프가 종료 됩니다.

**MoveNext** 속성은 컬렉션을 반복 하도록 선택한 변수에 영향을 주지 않습니다 ( `$Num` ).

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

**Reset** 메서드를 사용 하 여 컬렉션의 현재 요소를 다시 설정 합니다. 다음 예제에서는 **Reset** 메서드가 호출 되기 때문에 처음 두 요소를 **두 번** 반복 합니다. 처음 두 루프 후에 `if` 문이 실패 하 고 루프는 세 요소를 모두 정상적으로 반복 합니다.

> [!IMPORTANT]
> 이 경우 무한 루프가 발생할 수 있습니다.

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a>예 5: $switch 변수 사용

`$switch`변수에는 변수와 정확히 동일한 규칙이 있습니다 `$foreach` .
다음 예제에서는 모든 열거자 개념을 보여 줍니다.

> [!NOTE]
> MoveNext 메서드 뒤에 문이 없더라도 설명 **된 사례가 어떻게** 실행 되지 않는지 확인 합니다 `break` . 

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a>참조

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)
