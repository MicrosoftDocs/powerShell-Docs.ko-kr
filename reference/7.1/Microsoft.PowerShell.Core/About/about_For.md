---
description: 조건부 테스트를 기반으로 문을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 3/4/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_for?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_For
ms.openlocfilehash: 07037b73a5507bb0ef420ad39271be8832f7500b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93220921"
---
# <a name="about-for"></a>정보

## <a name="short-description"></a>간단한 설명
조건부 테스트를 기반으로 문을 실행 하는 데 사용할 수 있는 언어 명령을 설명 합니다.

## <a name="long-description"></a>자세한 설명입니다.

`For`문 (루프 라고도 함 `For` )은 지정 된 조건이로 평가 되는 동안 명령 블록에서 명령을 실행 하는 루프를 만드는 데 사용할 수 있는 언어 구문입니다 `$true` .

루프의 일반적인 용도는 `For` 값의 배열을 반복 하 고 이러한 값의 하위 집합에 대해 작동 하는 것입니다. 대부분의 경우 배열의 모든 값을 반복 하려면 문을 사용 하는 것이 좋습니다 `Foreach` .

### <a name="syntax"></a>구문

다음은 `For` 문 구문을 보여 줍니다.

```
for (<Init>; <Condition>; <Repeat>)
{
    <Statement list>
}
```

**Init** 자리 표시자는 루프가 시작 되기 전에 실행 되는 하나 이상의 명령을 나타냅니다. 일반적으로 문의 **Init** 부분을 사용 하 여 시작 값을 사용 하 여 변수를 만들고 초기화 합니다.

이 변수는 문의 다음 부분에서 테스트할 조건의 기반이 됩니다 `For` .

**조건** 자리 표시자는 `For` `$true` 또는 `$false` **부울** 값으로 확인 되는 문의 부분을 나타냅니다. PowerShell은 루프가 실행 될 때마다 조건을 평가 `For` 합니다. 문이 이면 `$true` 명령 블록의 명령이 실행 되 고 문이 다시 계산 됩니다. 조건이 여전히 이면 `$true` **문 목록의** 명령이 다시 실행 됩니다. 조건이이 될 때까지 루프가 반복 됩니다 `$false` .

**반복** 자리 표시자는 루프가 반복 될 때마다 실행 되는 쉼표로 구분 된 하나 이상의 명령을 나타냅니다. 일반적으로이는 문의 **조건** 부분 내에서 테스트 되는 변수를 수정 하는 데 사용 됩니다.

**문 목록** 자리 표시자는 루프가 입력 되거나 반복 될 때마다 실행 되는 하나 이상의 명령 집합을 나타냅니다. **문 목록의** 내용은 중괄호로 묶여 있습니다.

### <a name="support-for-multiple-operations"></a>여러 작업 지원

**Init** 문의 여러 할당 작업에 대해 다음과 같은 구문이 지원 됩니다.

```powershell
# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}
```

다음 구문은 **반복** 문의 여러 할당 연산에 대해 지원 됩니다.

```powershell
# Comma separated assignment expressions.
for (($i = 0), ($j = 0); $i -lt 10; $i++)
{
    "`$i:$i"
    "`$j:$j"
}

# Comma separated assignment expressions enclosed in parenthesis.
for (($i = 0), ($j = 0); $i -lt 10; ($i++), ($j++))
{
    "`$i:$i"
    "`$j:$j"
}

# Sub-expression using the semicolon to separate statements.
for ($($i = 0;$j = 0); $i -lt 10; $($i++;$j++))
{
    "`$i:$i"
    "`$j:$j"
}
```

> [!NOTE]
> 이전 또는 이후 증분 이외의 작업은 일부 구문에서 작동 하지 않을 수 있습니다.

여러 **조건의** 경우 다음 예제에서 보여 주는 것 처럼 논리 연산자를 사용 합니다.

```powershell
for (($i = 0), ($j = 0); $i -lt 10 -and $j -lt 10; $i++,$j++)
{
    "`$i:$i"
    "`$j:$j"
}
```

자세한 내용은 [about_Logical_Operators](about_Logical_Operators.md)를 참조 하세요.

### <a name="examples"></a>예

문에는 최소한 문의 `For` **Init** , **Condition** 및 **Repeat** 부분을 둘러싼 괄호가 필요 하 고 문의 **문 목록** 부분에서 중괄호로 묶은 명령이 필요 합니다.

이후 예제에서는 의도적으로 문 외부의 코드를 보여 줍니다 `For` . 이후 예제에서 코드는 문에 통합 되어 `For` 있습니다.

예를 들어 다음 `For` 문은 `$i` CTRL + C를 눌러 명령을 수동으로 해제할 때까지 변수 값을 계속 표시 합니다.

```powershell
$i = 1
for (;;)
{
    Write-Host $i
}
```

`$i`다음 예제와 같이 루프가 실행 될 때마다의 값이 1 씩 증가 하도록 문 목록에 추가 명령을 추가할 수 있습니다.

```powershell
for (;;)
{
    $i++; Write-Host $i
}
```

CTRL + C를 눌러 명령에서 분리 될 때까지이 명령문은 `$i` 루프가 실행 될 때마다 1 씩 증가 하는 변수 값을 계속 표시 합니다.

문의 문 목록 부분에 있는 변수 값을 변경 하는 대신 다음과 같이 `For` 문의 **반복** 부분을 대신 사용할 수 있습니다 `For` .

```powershell
$i=1
for (;;$i++)
{
    Write-Host $i
}
```

이 문은 CTRL + C를 눌러 명령에서 중단 될 때까지 계속 무기한 반복 됩니다.

`For` *조건을* 사용 하 여 루프를 종료할 수 있습니다. 문의 **조건** 부분을 사용 하 여 조건을 지정할 수 있습니다 `For` . `For`조건이로 평가 되 면 루프가 종료 `$false` 됩니다.

다음 예제에서 `For` 루프는의 값 `$i` 이 10 보다 작거나 같은 경우에 실행 됩니다.

```powershell
$i=1
for(;$i -le 10;$i++)
{
    Write-Host $i
}
```

문 외부에서 변수를 만들고 초기화 하는 대신 `For` `For` 문의 **Init** 부분을 사용 하 여 루프 내에서이 작업을 수행할 수 있습니다 `For` .

```powershell
for($i=1; $i -le 10; $i++){Write-Host $i}
```

세미콜론 대신 캐리지 리턴을 사용 하 여 문의 **Init** , **Condition** 및 **Repeat** 부분을 구분할 수 있습니다 `For` . 다음 예제에서는 `For` 이 대체 구문을 사용 하는을 보여 줍니다.

```powershell
for ($i = 0
  $i -lt 10
  $i++){
  $i
}
```

이 문의 대체 형식은 `For` powershell 스크립트 파일 및 powershell 명령 프롬프트에서 작동 합니다. 그러나 `For` 명령 프롬프트에서 대화형 명령을 입력할 때 세미콜론으로 문 구문을 사용 하는 것이 더 쉽습니다.

루프는 `For` `Foreach` 패턴을 사용 하 여 배열 또는 컬렉션의 값을 증가 시킬 수 있기 때문에 루프 보다 더 유연 합니다. 다음 예제에서 `$i` 변수는 문의 **반복** 부분에서 2 씩 증가 `For` 합니다.

```powershell
for ($i = 0; $i -le 20; $i += 2)
{
    Write-Host $i
}
```

`For`루프는 다음 예제와 같이 한 줄에 작성할 수도 있습니다.

```powershell
for ($i = 0; $i -lt 10; $i++) { Write-Host $i }
```

## <a name="see-also"></a>참고 항목

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Foreach](about_Foreach.md)

