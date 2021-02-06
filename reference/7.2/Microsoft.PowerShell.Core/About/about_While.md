---
description: 조건부 테스트의 결과에 따라 명령 블록을 실행 하는 데 사용할 수 있는 언어 문에 대해 설명 합니다.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_while?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_While
ms.openlocfilehash: 37c277a5919ba5fc39f953e05edaf58d159f3e7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600846"
---
# <a name="about-while"></a>While 정보

## <a name="short-description"></a>간단한 설명
조건부 테스트의 결과에 따라 명령 블록을 실행 하는 데 사용할 수 있는 언어 문에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

While 문 (While 루프 라고도 함)은 조건부 테스트가 true로 평가 되는 한 명령 블록에서 명령을 실행 하는 루프를 만들기 위한 언어 구문입니다. While 문은 구문이 더 복잡 하기 때문에 For 문 보다 생성 하기가 더 쉽습니다. 또한 While 문에서 조건부 테스트를 지정 하 여 루프가 실행 되는 횟수를 제어 하므로 Foreach 문 보다 유연성이 높습니다.

다음은 While 문 구문을 보여 줍니다.

```powershell
while (<condition>){<statement list>}
```

While 문을 실행 하는 경우 PowerShell은 섹션을 `<condition>` 시작 하기 전에 문의 섹션을 평가 합니다 `<statement list>` . 문의 조건 부분은 true 또는 false로 확인 됩니다. 조건이 true로 유지 되는 한 PowerShell은 섹션을 다시 활성화 합니다 `<statement list>` .

`<statement list>`문의 섹션에는 루프가 입력 되거나 반복 될 때마다 실행 되는 명령이 하나 이상 포함 되어 있습니다.

예를 들어 다음 While 문에는 $val 변수가 만들어지지 않았거나 $val 변수가 생성 되 고 0으로 초기화 된 경우 1에서 3 까지의 숫자가 표시 됩니다.

```powershell
while($val -ne 3)
{
    $val++
    Write-Host $val
}
```

이 예제에서 조건 ($val 3과 같지 않음)은 true ( \= 0, 1, 2 $val)입니다. 루프가 반복 될 때마다 $val \+ \+ 단항 증가 연산자 ($val)를 사용 하 여 1 씩 증가 \+ \+ 합니다. 루프를 마지막으로 수행한 후에는 $val \= 3입니다. $Val이 3 이면 condition 문이 false로 계산 되 고 루프가 종료 됩니다.

PowerShell 명령 프롬프트에서이 명령을 편리 하 게 작성 하려면 다음과 같은 방법으로 입력할 수 있습니다.

```powershell
while($val -ne 3){$val++; Write-Host $val}
```

세미콜론은 $val 값을 콘솔에 기록 하는 두 번째 명령에서 $val 1을 추가 하는 첫 번째 명령을 구분 합니다.

## <a name="see-also"></a>참고 항목

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Do](about_Do.md)

[about_Foreach](about_Foreach.md)

[about_For](about_For.md)

[about_Language_Keywords](about_Language_Keywords.md)

