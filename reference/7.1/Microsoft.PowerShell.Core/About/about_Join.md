---
description: 조인 연산자 (-조인)가 여러 문자열을 단일 문자열로 결합 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_join?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_join
ms.openlocfilehash: 578d12461a1e915e699970ca17c6f8220eb7fef1
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223617"
---
# <a name="about-join"></a>조인 정보

## <a name="short-description"></a>간단한 설명
조인 연산자 (-조인)가 여러 문자열을 단일 문자열로 결합 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

Join 연산자는 문자열 집합을 단일 문자열로 연결 합니다. 문자열은 결과 문자열에 명령에 표시 되는 순서 대로 추가 됩니다.

### <a name="syntax"></a>구문

다음 다이어그램에서는 조인 연산자의 구문을 보여 줍니다.

```powershell
-Join <String[]>
<String[]> -Join <Delimiter>
```

#### <a name="parameters"></a>매개 변수

String []-조인할 문자열을 하나 이상 지정 합니다.

Delimiter-연결 된 문자열 사이에 배치 되는 하나 이상의 문자를 지정 합니다. 기본값은 구분 기호 ("")가 아닙니다.

설명

단항 조인 연산자 (-join <string [] >)는 쉼표 보다 우선 순위가 높습니다. 결과적으로, 쉼표로 구분 된 문자열 목록을 단항 join 연산자에 제출 하면 첫 번째 쉼표 앞의 첫 번째 문자열만 조인 연산자에 전송 됩니다.

단항 조인 연산자를 사용 하려면 문자열을 괄호로 묶거나 변수에 문자열을 저장 한 다음 조인할 변수를 제출 합니다.

다음은 그 예입니다.

```powershell
-join "a", "b", "c"
a
b
c

-join ("a", "b", "c")
abc

$z = "a", "b", "c"
-join $z
abc
```

### <a name="examples"></a>예

다음 문은 세 개의 문자열을 조인 합니다.

```powershell
-join ("Windows", "PowerShell", "2.0")
WindowsPowerShell2.0
```

다음 문은 공백으로 구분 된 세 개의 문자열을 조인 합니다.

```powershell
"Windows", "PowerShell", "2.0" -join " "
Windows PowerShell 2.0
```

다음 문에서는 여러 문자 구분 기호를 사용 하 여 세 개의 문자열을 조인 합니다.

```powershell
$a = "WIND", "S P", "ERSHELL"
$a -join "OW"
WINDOWS POWERSHELL
```

다음 문은 문자열의 줄을 단일 문자열로 조인 합니다. 여기에 있는 문자열은 하나의 문자열 이기 때문에 조인 하려면 여기 문자열의 줄을 분할 해야 합니다. 이 메서드를 사용 하 여 다음 문자열에 저장 된 XML 파일의 문자열을 다시 조인할 수 있습니다.

```powershell
$a = @'
a
b
c
'@

(-split $a) -join " "
a b c
```

## <a name="see-also"></a>참고 항목

[about_Operators](about_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Split](about_Split.md)

