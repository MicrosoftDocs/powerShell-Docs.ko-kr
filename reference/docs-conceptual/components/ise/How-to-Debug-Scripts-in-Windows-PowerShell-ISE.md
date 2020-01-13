---
ms.date: 01/02/2020
keywords: powershell,cmdlet
title: Windows PowerShell ISE에서 스크립트를 디버깅하는 방법
ms.openlocfilehash: c5da80f3e0e013448533c80bbe1957a301be38f5
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737120"
---
# <a name="how-to-debug-scripts-in-windows-powershell-ise"></a>Windows PowerShell ISE에서 스크립트를 디버깅하는 방법

이 문서에서는 Windows PowerShell ISE(통합 스크립팅 환경) 시각적 디버깅 기능을 사용하여 로컬 컴퓨터에서 스크립트를 디버그하는 방법을 설명합니다.

## <a name="how-to-manage-breakpoints"></a>중단점을 관리하는 방법

중단점은 변수의 현재 상태와 스크립트를 실행하는 환경을 검사할 수 있도록 작업을 일시 중지하려는 스크립트의 지정된 지점입니다.
스크립트가 중단점에서 일시 중지되면 콘솔 창에서 명령을 실행하여 스크립트 상태를 검사할 수 있습니다. 변수를 출력하거나 다른 명령을 실행할 수 있습니다. 현재 실행 중인 스크립트의 컨텍스트에 표시되는 모든 변수의 값을 수정할 수도 있습니다. 보려는 사항을 검사한 후 스크립트 작업을 다시 시작할 수 있습니다.

Windows PowerShell 디버깅 환경에서는 다음 세 가지 유형의 중단점을 설정할 수 있습니다.

1. **줄 중단점**. 스크립트 작업 중 지정된 줄에 도달하면 스크립트가 일시 중지됩니다.

1. **변수 중단점.** 지정된 변수의 값이 변경될 때마다 스크립트가 일시 중지됩니다.

1. **명령 중단점.** 스크립트 작업 중 지정된 명령을 실행하려 할 때마다 스크립트가 일시 중지됩니다. 매개 변수를 포함하여 중단점을 원하는 작업으로만 추가로 필터링할 수 있습니다. 명령은 사용자가 만든 함수일 수도 있습니다.

Windows PowerShell ISE 디버깅 환경에서는 이 중에서 줄 중단점만 메뉴 또는 바로 가기 키를 통해 설정할 수 있습니다. 다른 두 유형의 중단점도 설정할 수 있지만 콘솔 창에서 [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md) cmdlet을 통해 설정됩니다. 이 섹션에서는 Windows PowerShell ISE에서 메뉴(사용할 수 있을 경우)를 사용하여 디버깅 작업을 수행하는 방법과 콘솔 창에서 스크립팅을 사용하여 보다 다양한 명령을 수행하는 방법을 설명합니다.

### <a name="to-set-a-breakpoint"></a>중단점을 설정하려면

스크립트를 저장한 후에만 스크립트에 중단점을 설정할 수 있습니다. 줄 중단점을 설정할 줄을 마우스 오른쪽 단추로 클릭한 다음 **중단점 설정/해제**를 클릭합니다. 또는 줄 중단점을 설정할 줄을 클릭한 다음 <kbd>F9</kbd> 키를 누르거나 **디버그** 메뉴에서 **중단점 설정/해제**를 클릭합니다.

다음 스크립트는 [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 변수 중단점을 설정하는 방법의 예입니다.

```powershell
# This command sets a breakpoint on the Server variable in the Sample.ps1 script.
Set-PSBreakpoint -Script sample.ps1 -Variable Server
```

### <a name="list-all-breakpoints"></a>모든 중단점 표시

현재 Windows PowerShell 세션에 있는 중단점을 모두 표시합니다.

**디버그** 메뉴에서 **중단점 목록**을 클릭합니다. 다음 스크립트는 [Get-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Get-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 모든 중단점을 표시하는 방법의 예입니다.

```powershell
# This command lists all breakpoints in the current session.
Get-PSBreakpoint
```

### <a name="remove-a-breakpoint"></a>중단점 제거

중단점을 제거하면 삭제됩니다.

나중에 다시 사용할 수도 있는 경우 대신 [중단점을 사용하지 않도록 설정](#disable-a-breakpoint)하는 것이 좋습니다. 중단점을 제거할 줄을 마우스 오른쪽 단추로 클릭한 다음, **ToggleBreakpoint**를 클릭합니다.
또는 중단점을 제거할 줄을 클릭한 다음 **디버그** 메뉴에서 **중단점 설정/해제**를 클릭합니다. 다음 스크립트는 [Remove-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Remove-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 지정된 ID의 중단점을 제거하는 방법의 예입니다.

```powershell
# This command deletes the breakpoint with breakpoint ID 2.
Remove-PSBreakpoint -Id 2
```

### <a name="remove-all-breakpoints"></a>모든 중단점 제거

현재 세션에서 정의된 모든 중단점을 제거하려면 **디버그** 메뉴에서 **모든 중단점 제거**를 클릭합니다.

다음 스크립트는 [Remove-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Remove-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 모든 중단점을 제거하는 방법의 예입니다.

```powershell
# This command deletes all of the breakpoints in the current session.
Get-PSBreakpoint | Remove-PSBreakpoint
```

### <a name="disable-a-breakpoint"></a>중단점 사용 안 함

중단점을 사용하지 않도록 설정할 경우 중단점이 제거되지 않고, 사용하도록 설정할 때까지 해제됩니다. 특정 줄 중단점을 사용하지 않도록 설정하려면 중단점을 사용하지 않도록 설정할 줄을 마우스 오른쪽 단추로 클릭한 다음 **중단점 사용 안 함**을 클릭합니다. 또는 중단점을 사용하지 않도록 설정할 줄을 클릭한 다음 <kbd>F9</kbd> 키를 누르거나 **디버그** 메뉴에서 **중단점 사용 안 함**을 클릭합니다. 다음 스크립트는 [Disable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Disable-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 지정된 ID의 중단점을 제거하는 방법의 예입니다.

```powershell
# This command disables the breakpoint with breakpoint ID 0.
Disable-PSBreakpoint -Id 0
```

### <a name="disable-all-breakpoints"></a>모든 중단점 사용 안 함

중단점을 사용하지 않도록 설정할 경우 중단점이 제거되지 않고, 사용하도록 설정할 때까지 해제됩니다. 현재 세션의 모든 중단점을 사용하지 않도록 설정하려면 **디버그** 메뉴에서 **모든 중단점 사용 안 함**을 클릭합니다. 다음 스크립트는 [Disable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Disable-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 모든 중단점을 사용하지 않도록 설정하는 방법의 예입니다.

```powershell
# This command disables all breakpoints in the current session.
# You can abbreviate this command as: "gbp | dbp".
Get-PSBreakpoint | Disable-PSBreakpoint
```

### <a name="enable-a-breakpoint"></a>중단점 사용

특정 중단점을 사용하도록 설정하려면 중단점을 사용하도록 설정할 줄을 마우스 오른쪽 단추로 클릭한 다음 **중단점 사용**을 클릭합니다. 또는 중단점을 사용하도록 설정할 줄을 클릭한 다음 <kbd>F9</kbd> 키를 누르거나 **디버그** 메뉴에서 **중단점 사용**을 클릭합니다. 다음 스크립트는 [Enable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Enable-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 특정 중단점을 사용하도록 설정하는 방법의 예입니다.

```powershell
# This command enables breakpoints with breakpoint IDs 0, 1, and 5.
Enable-PSBreakpoint -Id 0, 1, 5
```

### <a name="enable-all-breakpoints"></a>모든 중단점 사용

현재 세션에서 정의된 모든 중단점을 사용하도록 설정하려면 **디버그** 메뉴에서 **모든 중단점 사용**을 클릭합니다. 다음 스크립트는 [Enable-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Enable-PSBreakpoint.md) cmdlet을 사용하여 콘솔 창에서 모든 중단점을 사용하도록 설정하는 방법의 예입니다.

```powershell
# This command enables all breakpoints in the current session.
# You can abbreviate the command by using their aliases: "gbp | ebp".
Get-PSBreakpoint | Enable-PSBreakpoint
```

## <a name="how-to-manage-a-debugging-session"></a>디버깅 세션을 관리하는 방법

디버깅을 시작하기 전에 중단점을 하나 이상 설정해야 합니다. 디버그하려는 스크립트를 저장하지 않은 경우 중단점을 설정할 수 없습니다. 중단점을 설정하는 방법에 대한 지침은 [중단점을 관리하는 방법](#how-to-manage-breakpoints) 또는 [Set-PSBreakpoint](/reference/6/Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)를 참조하세요.
디버깅을 시작한 후에는 디버깅을 중지할 때까지 스크립트를 편집할 수 없습니다. 중단점이 하나 이상 설정되어 있는 스크립트는 실행되기 전에 자동으로 저장됩니다.

### <a name="to-start-debugging"></a>디버깅을 시작하려면

<kbd>F5</kbd> 키를 누르거나, 도구 모음에서 **스크립트 실행** 아이콘을 클릭하거나, **디버그** 메뉴에서 **실행/계속**을 클릭합니다. 스크립트가 첫 번째 중단점에 도달할 때까지 실행됩니다. 여기서 작업이 일시 중지되고, 일시 중지된 줄이 강조 표시됩니다.

### <a name="to-continue-debugging"></a>디버깅을 계속하려면

<kbd>F5</kbd> 키를 누르거나, 도구 모음에서 **스크립트 실행** 아이콘을 클릭하거나, **디버그** 메뉴에서 **실행/계속**을 클릭하거나, 콘솔 창에서 `C`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다. 이렇게 하면 스크립트가 다음 중단점이나 더 이상 중단점이 없는 경우 스크립트의 끝까지 계속 실행됩니다.

### <a name="to-view-the-call-stack"></a>호출 스택을 보려면

호출 스택은 스크립트에서 현재 실행 위치를 표시합니다. 다른 함수에 의해 호출된 함수에서 스크립트를 실행하는 경우 출력에서 추가 행으로 표시됩니다. 맨 아래에 있는 행은 원래 스크립트와 함수가 호출된 스크립트의 줄을 표시합니다. 위에 있는 다음 줄은 해당 함수와 다른 함수가 호출되었을 수 있는 함수의 줄을 보여 줍니다. 맨 위에 있는 행은 중단점이 설정된 현재 줄의 현재 컨텍스트를 보여 줍니다.

일시 중지된 동안 현재 호출 스택을 보려면 <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>를 누르거나, **디버그** 메뉴에서 **호출 스택 표시**를 클릭하거나, 콘솔 창에서 `K`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

### <a name="to-stop-debugging"></a>디버깅을 중지하려면

<kbd>Shift</kbd>+<kbd>F5</kbd>를 누르거나, **디버그** 메뉴에서 **디버거 중지**를 클릭하거나, 콘솔 창에서 `Q`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

## <a name="how-to-step-over-step-into-and-step-out-while-debugging"></a>디버그하는 동안 프로시저 단위 실행, 한 단계씩 코드 실행 및 프로시저 나가기를 수행하는 방법

한 단계씩 코드 실행은 한 번에 하나씩 문을 실행하는 프로세스입니다. 코드 줄에서 중지하고 변수 값과 시스템 상태를 검사할 수 있습니다. 다음 표에서는 프로시저 단위 실행, 한 단계씩 코드 실행, 프로시저 나가기 등의 일반적인 디버깅 작업에 대해 설명합니다.

| 디버깅 작업 |                                                                                                                   Description                                                                                                                    |                                                      PowerShell ISE에서 작업을 수행하는 방법                                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| **한 단계씩 코드 실행**  | 현재 문을 실행하고 다음 문에서 중지합니다. 현재 문이 함수 또는 스크립트 호출이면 디버거가 해당 함수나 스크립트로 한 단계씩 코드를 실행하고, 그렇지 않으면 다음 문에서 중지합니다.                      | <kbd>F11</kbd> 키를 누르거나, **디버그** 메뉴에서 **한 단계씩 코드 실행**을 클릭하거나, 콘솔 창에서 `S`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.                 |
| **프로시저 단위 실행**  | 현재 문을 실행하고 다음 문에서 중지합니다. 현재 문이 함수 또는 스크립트 호출이면 디버거가 전체 함수나 스크립트를 실행하고, 함수 호출 후 다음 문에서 중지합니다. | <kbd>F10</kbd> 키를 누르거나, **디버그** 메뉴에서 **프로시저 단위 실행**을 클릭하거나, 콘솔 창에서 `V`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.                 |
| **프로시저 나가기**   | 현재 함수에서 나가고, 함수가 중첩된 경우에는 한 수준 위로 올라갑니다. 본문에 있는 경우 스크립트가 끝 또는 다음 중단점까지 실행됩니다. 건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.                   | <kbd>Shift</kbd>+<kbd>F11</kbd>을 누르거나, **디버그** 메뉴에서 **프로시저 나가기**를 클릭하거나, 콘솔 창에서 `O`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다. |
| **계속**   | 끝이나 다음 중단점까지 실행을 계속합니다. 건너뛴 함수 및 호출은 실행되지만 단계별로 실행되지는 않습니다.                                                                                                          | <kbd>F5</kbd> 키를 누르거나, **디버그** 메뉴에서 **실행/계속**을 클릭하거나, 콘솔 창에서 `C`를 입력하고 <kbd>Enter</kbd> 키를 누릅니다.               |

## <a name="how-to-display-the-values-of-variables-while-debugging"></a>디버그하는 동안 변수 값을 표시하는 방법

코드를 단계별로 실행할 때 스크립트에서 변수의 현재 값을 표시할 수 있습니다.

### <a name="to-display-the-values-of-standard-variables"></a>표준 변수의 값을 표시하려면

다음 방법 중 하나를 사용합니다.

- 스크립트 창에서 변수를 마우스로 가리켜 해당 값을 도구 설명으로 표시합니다.

- 콘솔 창에서 변수 이름을 입력하고 <kbd>Enter</kbd> 키를 누릅니다.

ISE에서 모든 창은 항상 동일한 범위입니다. 따라서 스크립트를 디버그하는 동안 콘솔 창에 입력한 명령은 스크립트 범위에서 실행됩니다. 따라서 콘솔 창을 사용하여 변수 값을 찾고 스크립트에만 정의되어 있는 함수를 호출할 수 있습니다.

### <a name="to-display-the-values-of-automatic-variables"></a>자동 변수의 값을 표시하려면

앞에서 설명한 방법을 사용하면 스크립트를 디버그하는 동안 거의 모든 변수의 값을 표시할 수 있습니다. 그러나 다음과 같은 자동 변수에는 이러한 방법을 사용할 수 없습니다.

- `$_`

- `$Input`

- `$MyInvocation`

- `$PSBoundParameters`

- `$Args`

이러한 변수의 값을 표시하려는 경우 스크립트의 변수 값이 아니라 디버거가 사용하는 내부 파이프라인의 해당 변수 값을 가져옵니다. 다음 방법을 사용하여 일부 변수(`$_`, `$Input`, `$MyInvocation`, `$PSBoundParameters` 및 `$Args`)에 대해 이 문제를 해결할 수 있습니다.

1. 스크립트에서 자동 변수의 값을 새 변수에 할당합니다.

1. 스크립트 창에서 새 변수를 마우스로 가리키거나 콘솔 창에서 새 변수를 입력하여 새 변수의 값을 표시합니다.

예를 들어 `$MyInvocation` 변수의 값을 표시하려면 스크립트에서 `$scriptName` 등의 새 변수에 값을 할당한 다음, `$scriptName` 변수를 마우스로 가리키거나 입력하여 해당 값을 표시합니다.

```powershell
# In C:\ps-test\MyScript.ps1
$scriptName = $MyInvocation.MyCommand.Path
```

```PowerShell
# In the Console Pane:
.\MyScript.ps1
$scriptName
```

```Output
C:\ps-test\MyScript.ps1
```

## <a name="see-also"></a>참고 항목

- [Windows PowerShell ISE 탐색](exploring-the-windows-powershell-ise.md)
