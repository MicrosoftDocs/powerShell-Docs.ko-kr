---
description: While 또는 Until 조건이 적용 되는 문 목록을 한 번 이상 실행 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: ee4d7fbb53c5d1e9dd72243385f7eca0f4665623
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223889"
---
# <a name="about-do"></a>작업 정보

## <a name="short-description"></a>간단한 설명
While 또는 Until 조건이 적용 되는 문 목록을 한 번 이상 실행 합니다.

## <a name="long-description"></a>자세한 설명

Do 키워드는 While 키워드 또는 Until 키워드와 함께 작동 하 여 조건에 따라 스크립트 블록에서 문을 실행 합니다. 관련 While 루프와 달리 Do 루프의 스크립트 블록은 항상 한 번 이상 실행 됩니다.

**Do while** 루프는 다양 한 while 루프입니다. **Do while** 루프에서 조건은 스크립트 블록이 실행 된 후 평가 됩니다. While 루프 에서처럼 조건이 true로 평가 되는 한 스크립트 블록을 반복 합니다.

**Do while** **루프와** 마찬가지로 항상 조건을 평가 하기 전에 항상 한 번 이상 실행 됩니다. 그러나 스크립트 블록은 조건이 false 인 경우에만 실행 됩니다.

*Continue* 및 *Break* Flow 제어 키워드는 **Do while** 루프 또는 **do until** 루프에서 사용할 수 있습니다.

### <a name="syntax"></a>구문

다음은 **Do While** 문의 구문을 보여 줍니다.

```powershell
do {<statement list>} while (<condition>)
```

다음은 **Do Until** 문의 구문을 보여 줍니다.

```powershell
do {<statement list>} until (<condition>)
```

문 목록에는 루프가 입력 되거나 반복 될 때마다 실행 되는 문이 하나 이상 포함 되어 있습니다.

문의 조건 부분은 true 또는 false로 확인 됩니다.

### <a name="example"></a>예제

Do 문의 다음 예제는 값이 0 인 항목에 도달할 때까지 배열의 항목 수를 계산 합니다.

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

다음 예에서는 Until 키워드를 사용 합니다. 같지 않음 연산자 ( `-ne` )는 같음 연산자 ()로 대체 됩니다 `-eq` .

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

다음 예제에서는 0 보다 작은 값을 건너뛰어 배열의 모든 값을 씁니다.

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a>참고 항목

[about_While](about_While.md)

[about_Operators](about_Operators.md)

[about_assignment_operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)
