---
description: ',,,, `foreach` `for` `while` `do` `switch` 또는 `trap` 문을 즉시 종료 하는 데 사용할 수 있는 문을 설명 합니다.'
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_break?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Break
ms.openlocfilehash: 3c418f5bae11f957880c8b53ee0bcf2fb44515ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601463"
---
# <a name="about-break"></a>중단 정보

## <a name="short-description"></a>간단한 설명

,,,, `foreach` `for` `while` `do` `switch` 또는 `trap` 문을 즉시 종료 하는 데 사용할 수 있는 문을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`break`문은 현재 제어 블록을 종료 하는 방법을 제공 합니다.
제어 블록 다음의 문에서 실행이 계속 됩니다. 문은 레이블을 지원 합니다. 레이블은 스크립트의 문에 할당 하는 이름입니다.

## <a name="using-break-in-loops"></a>루프에서 중단 사용

루프 (예 `break` :,, 또는 루프)에 문이 `foreach` 나타나면 `for` PowerShell에서 `do` `while` 즉시 루프를 종료 합니다.

`break`문에는 포함 된 루프를 종료할 수 있는 레이블이 포함 될 수 있습니다. 레이블은 `foreach` 스크립트에서, 또는와 같은 루프 키워드를 지정할 수 있습니다 `for` `while` .

다음 예에서는 문을 사용 하 여 문을 종료 하는 방법을 보여 줍니다 `break` `for` .

```powershell
for($i=1; $i -le 10; $i++) {
   Write-Host $i
   break
}
```

이 예제에서 `break` 문은 `for` `$i` 변수가 1 이면 루프를 종료 합니다. `for`문이 10 보다 클 때까지 **True** 로 평가 되는 경우에도 `$i` 루프를 처음 실행할 때 PowerShell은 break 문에 도달 합니다 `for` .

`break`내부 조건이 충족 되어야 하는 루프에서 문을 사용 하는 것이 더 일반적입니다. 다음 `foreach` 문 예를 살펴보십시오.

```powershell
$i=0
$varB = 10,20,30,40
foreach ($val in $varB) {
  if ($val -eq 30) {
    break
  }
  $i++
}
Write-Host "30 was found in array index $i"
```

이 예제에서 `foreach` 문은 배열을 반복 합니다 `$varB` . `if`문은 루프를 처음 두 번 실행 하 고 변수가 1 씩 증가 하는 경우 False로 평가 됩니다 `$i` . 루프가 실행 되는 세 번째 시간은 `$i` 2이 고 `$val` 변수는 30입니다. 이 시점에서 `break` 문이 실행 되 고 `foreach` 루프가 종료 됩니다.

### <a name="using-a-labeled-break-in-a-loop"></a>루프에서 레이블이 지정 된 나누기 사용

`break`문에는 레이블이 포함 될 수 있습니다. 키워드를 레이블과 함께 사용 하는 경우 `break` PowerShell은 현재 루프를 종료 하는 대신 레이블이 지정 된 루프를 종료 합니다.
레이블은 콜론 뒤에 사용자가 할당 한 이름입니다. 레이블은 문의 첫 번째 토큰 이어야 하며,와 같은 루핑 키워드 뒤에와 야 합니다 `while` .

`break` 레이블이 지정 된 루프에서 실행을 이동 합니다. 포함 된 루프에서이는 `break` 단독으로 사용 될 때 키워드와 다른 결과를 가집니다. 이 예제에는 `while` 문이 포함 된 문이 있습니다 `for` .

```powershell
:myLabel while (<condition 1>) {
  for ($item in $items) {
    if (<condition 2>) {
      break myLabel
    }
    $item = $x   # A statement inside the For-loop
  }
}
$a = $c  # A statement after the labeled While-loop
```

조건 2가 **True** 로 평가 되는 경우 스크립트 실행은 레이블이 지정 된 루프 뒤의 문으로 건너뜁니다. 이 예제에서는 문을 사용 하 여 실행을 다시 시작 `$a = $c` 합니다.

다음 예제와 같이 레이블이 지정 된 여러 루프를 중첩할 수 있습니다.

```powershell
:red while (<condition1>) {
  :yellow while (<condition2>) {
    while (<condition3>) {
      if ($a) {break}
      if ($b) {break red}
      if ($c) {break yellow}
    }
    Write-Host "After innermost loop"
  }
  Write-Host "After yellow loop"
}
Write-Host "After red loop"
```

`$b`변수가 True로 평가 되 면 "red" 라는 레이블이 지정 된 루프 다음에 스크립트 실행이 다시 시작 됩니다. `$c`변수가 True로 평가 되 면 "노란색"으로 표시 된 루프 다음에 스크립트 컨트롤의 실행이 다시 시작 됩니다.

`$a`변수가 True로 평가 되 면 가장 안쪽의 루프 다음에 실행이 다시 시작 됩니다. 레이블이 필요 하지 않습니다.

PowerShell은 레이블 실행을 다시 시작할 수 있는 시간을 제한 하지 않습니다. 레이블은 스크립트 및 함수 호출 경계에서 제어를 전달할 수도 있습니다.

## <a name="using-break-in-a-switch-statement"></a>Switch 문에서 break 사용

구문에서 `switch` PowerShell이 `break` 코드 블록을 종료 하도록 `switch` 합니다.

`break`키워드는 구문을 종료 하는 데 사용 됩니다 `switch` . 예를 들어 다음 `switch` 문은 문을 사용 하 여 `break` 가장 구체적인 조건을 테스트 합니다.

```powershell
$var = "word2"
switch -regex ($var) {
    "word2" {
      Write-Host "Exact" $_
      break
    }

    "word.*" {
      Write-Host "Match on the prefix" $_
      break
    }

    "w.*" {
      Write-Host "Match on at least the first letter" $_
      break
    }

    default {
      Write-Host "No match" $_
      break
    }
}
```

이 예에서는 변수를 `$var` 만들고 문자열 값으로 초기화 `word2` 합니다. `switch`문은 **Regex** 클래스를 사용 하 여 변수 값을 용어와 먼저 일치 시킵니다 `word2` . 변수 값과 문의 첫 번째 테스트가 `switch` 일치 하므로 문의 첫 번째 코드 블록이 `switch` 실행 됩니다.

PowerShell이 첫 번째 문에 도달할 때 `break` `switch` 문이 종료 됩니다. 이 예에서는 네 개의 `break` 문이 제거 될 경우 네 가지 조건이 모두 충족 됩니다. 이 예에서는 문을 사용 하 여 `break` 가장 구체적인 조건이 충족 될 때 결과를 표시 합니다.

## <a name="using-break-in-a-trap-statement"></a>Trap 문에서 break 사용

문의 본문에서 실행 된 마지막 문이 `trap` 인 경우 `break` 오류 개체는 표시 되지 않고 예외가 다시 throw 됩니다.

다음 예에서는 문을 사용 하 여 트랩 된 **DivideByZeroException** 예외를 만듭니다 `trap` .

```powershell
function test {
  trap [DivideByZeroException] {
    Write-Host 'divide by zero trapped'
    break
  }

  $i = 3
  'Before loop'
  while ($true) {
     "1 / $i = " + (1 / $i--)
  }
  'After loop'
}
test
```

예외가 발생 하면 실행이 중지 됩니다. 에 `After loop` 도달 하지 않습니다.
가 실행 된 후 예외가 다시 throw 됩니다 `trap` .

```Output
Before loop
1 / 3 = 0.333333333333333
1 / 2 = 0.5
1 / 1 = 1
divide by zero trapped
ParentContainsErrorRecordException:
Line |
  10 |       "1 / $i = " + (1 / $i--)
     |       ~~~~~~~~~~~~~~~~~~~~~~~~
     | Attempted to divide by zero.
```

## <a name="do-not-use-break-outside-of-a-loop-switch-or-trap"></a>루프, 스위치 또는 트랩 외부에서 break를 사용 하지 마십시오.

를 `break` 직접 지 원하는 구문 외부에서 사용 하는 경우 (루프, `switch` , `trap` ) PowerShell에서 바깥쪽 구문에 대 한 _호출 스택을_ 찾습니다. 바깥쪽 구문을 찾을 수 없는 경우 현재 runspace가 자동으로 종료 됩니다.

즉, 실수로를 지 원하는 바깥쪽 구문 외부에서를 사용 하는 함수 및 스크립트는 `break` 실수로 _호출자_ 를 종료할 수 있습니다.

`break`스크립트 블록과 같은 파이프라인 내에서를 사용 하면 `break` `ForEach-Object` 파이프라인이 종료 될 뿐만 아니라 전체 runspace가 종료 될 수 있습니다.

## <a name="see-also"></a>참고 항목

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Continue](about_Continue.md)

[about_For](about_For.md)

[about_Foreach](about_Foreach.md)

[about_Switch](about_Switch.md)

[about_Throw](about_Throw.md)

[about_Trap](about_Trap.md)

[about_Try_Catch_Finally](about_Try_Catch_Finally.md)

[about_While](about_While.md)
