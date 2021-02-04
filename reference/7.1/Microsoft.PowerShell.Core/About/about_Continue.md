---
description: '`continue`문이 프로그램 루프, `switch` 문 또는 문 맨 위에 프로그램 흐름을 즉시 반환 하는 방법에 대해 설명 합니다 `trap` .'
keywords: powershell,cmdlet
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_continue?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Continue
ms.openlocfilehash: 2b299726b3fe75e5d13e91bbde7564705d3e2112
ms.sourcegitcommit: 0c31814bed14ff715dc7d4aace07cbdc6df2438e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97614118"
---
# <a name="about-continue"></a>계속 정보

## <a name="short-description"></a>간단한 설명

`continue`문이 프로그램 루프, `switch` 문 또는 문 맨 위에 프로그램 흐름을 즉시 반환 하는 방법에 대해 설명 합니다 `trap` .

## <a name="long-description"></a>자세한 설명입니다.

`continue`문은 완전히 종료 하는 대신 현재 제어 블록을 끝내는 방법을 제공 하지만 실행을 계속 합니다. 문은 레이블을 지원 합니다.
레이블은 스크립트의 문에 할당 하는 이름입니다.

## <a name="using-continue-in-loops"></a>루프에서 계속 사용

레이블 없는 `continue` 문은 즉시 프로그램 흐름을 `for` ,, `foreach` `do` 또는 문에 의해 제어 되는 가장 안쪽 루프의 맨 위로 반환 합니다 `while` . 루프의 현재 반복이 종료 되 고 루프는 다음 반복에서 계속 됩니다.

다음 예제에서 프로그램 흐름은 `while` `$ctr` 변수가 5와 같은 경우 루프의 맨 위로 돌아갑니다. 따라서 5를 제외 하 고 1과 10 사이의 모든 숫자가 표시 됩니다.

```powershell
while ($ctr -lt 10)
{
    $ctr += 1
    if ($ctr -eq 5)
    {
        continue
    }

    Write-Host -Object $ctr
}
```

루프를 사용 하는 경우 `for` 문에서 실행이 계속 되 고 `<Repeat>` 그 다음에 `<Condition>` 테스트가 수행 됩니다. 아래 예제에서는가 키워드 다음에 감소 하는 경우 무한 루프가 발생 하지 않습니다 `$i` `continue` .

```powershell
#   <Init>  <Condition> <Repeat>
for ($i = 0; $i -lt 10; $i++)
{
    Write-Host -Object $i
    if ($i -eq 5)
    {
        continue
        # Will not result in an infinite loop.
        $i--
    }
}
```

### <a name="using-a-labeled-continue-in-a-loop"></a>루프에서 레이블이 지정 된 continue 사용

레이블이 지정 된 `continue` 문은 반복의 실행을 종료 하 고 대상으로 지정 된 포함 반복 또는 문 레이블로 제어를 전달 합니다 `switch` .

다음 예제에서는 `for` `$condition` 가 **True** 이 고에서 두 번째 루프를 사용 하 여 반복이 계속 되 면 가장 안쪽이 종료 됩니다 `for` `labelB` .

```powershell
:labelA for ($i = 1; $i -le 10; $i++) {
    :labelB for ($j = 1; $j -le 10; $j++) {
        :labelC for ($k = 1; $k -le 10; $k++) {
            if ($condition) {
                continue labelB
            } else {
                $condition = Update-Condition
            }
        }
    }
}
```

## <a name="using-continue-in-a-switch-statement"></a>Switch 문에서 continue 사용

`continue`내에서 레이블이 없는 문은 `switch` 현재 반복의 실행을 종료 하 `switch` 고 컨트롤을의 위쪽으로 전달 `switch` 하 여 다음 입력 항목을 가져옵니다.

단일 입력 항목이 있으면 `continue` 전체 `switch` 문을 종료 합니다.
`switch`입력이 컬렉션인 경우는 `switch` 컬렉션의 각 요소를 테스트 합니다. 는 `continue` 현재 반복을 종료 하 고는 `switch` 다음 요소를 계속 합니다.

```powershell
switch (1,2,3) {
  2 { continue }  # moves on to the next element, 3
  default { $_ }
}
```

```Output
1
3
```

## <a name="using-continue-in-a-trap-statement"></a>Trap 문에서 continue 사용

본문에서 실행 된 마지막 문이 `trap` 인 경우 `continue` 트랩 된 오류는 자동으로 무시 되 고 발생 한 원인이 되는 문 바로 다음의 문을 사용 하 여 실행이 계속 됩니다 `trap` .

## <a name="do-not-use-continue-outside-of-a-loop-switch-or-trap"></a>루프, 스위치 또는 트랩 외부에서 계속 사용 안 함

를 `continue` 직접 지 원하는 구문 외부에서 사용 하는 경우 (루프, `switch` , `trap` ) PowerShell에서 바깥쪽 구문에 대 한 _호출 스택을_ 찾습니다. 바깥쪽 구문을 찾을 수 없는 경우 현재 runspace가 자동으로 종료 됩니다.

즉, 실수로이를 지 원하는 바깥쪽 구문 외부에서를 사용 하는 함수 및 스크립트는 `continue` 실수로 _호출자_ 를 종료할 수 있습니다.

`continue`스크립트 블록과 같은 파이프라인 내에서를 사용 하면 `ForEach-Object` 파이프라인이 종료 될 뿐만 아니라 전체 runspace가 종료 될 수 있습니다.

## <a name="see-also"></a>참조

[about_Break](about_Break.md)

[about_For](about_For.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)
