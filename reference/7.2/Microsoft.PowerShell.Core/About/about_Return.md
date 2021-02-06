---
description: 함수, 스크립트 또는 스크립트 블록일 수 있는 현재 범위를 종료합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_return?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Return
ms.openlocfilehash: 032f3c694096e11e2800be941eb76b1f442b5088
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599611"
---
# <a name="about-return"></a>반환 정보

## <a name="short-description"></a>간단한 설명

함수, 스크립트 또는 스크립트 블록일 수 있는 현재 범위를 종료합니다.

## <a name="long-description"></a>자세한 설명입니다.

`return`키워드는 함수, 스크립트 또는 스크립트 블록을 종료 합니다. 특정 지점에서 범위를 종료 하거나, 값을 반환 하거나, 범위의 끝에 도달 했음을 나타내는 데 사용할 수 있습니다.

C 또는 C와 같은 언어에 익숙한 사용자는 \# 키워드를 사용 하 여 `return` 범위를 명시적으로 유지 하는 논리를 만들 수 있습니다.

PowerShell에서 Return 키워드를 포함 하는 문이 없어도 각 문의 결과가 output으로 반환 됩니다. C 또는 C와 같은 언어는 \# 키워드에 지정 된 값 또는 값만 반환 `return` 합니다.

> [!NOTE]
> PowerShell 5.0부터 PowerShell은 정식 구문을 사용 하 여 클래스를 정의 하기 위한 언어를 추가 했습니다.  PowerShell 클래스의 컨텍스트에서는 문을 사용 하 여 지정 하는 것을 제외 하 고는 메서드에서 아무것도 출력 하지 않습니다 `return` . [About_Classes](about_Classes.md)에서 PowerShell 클래스에 대해 자세히 알아볼 수 있습니다.

### <a name="syntax"></a>Syntax

키워드의 구문은 다음과 같습니다 `return` .

```
return [<expression>]
```

`return`키워드는 단독으로 표시 되거나 다음과 같이 값 또는 식 뒤에 올 수 있습니다.

```powershell
return
return $a
return (2 + $a)
```

### <a name="examples"></a>예

다음 예제에서는 키워드를 사용 하 여 `return` 조건이 충족 되는 경우 특정 지점에서 함수를 종료 합니다. Return 문이 실행 되기 전에 return 문이 종료 되므로 홀수는 곱할 수 없습니다.

```powershell
function MultiplyEven
{
    param($number)

    if ($number % 2) { return "$number is not even" }
    $number * 2
}

1..10 | ForEach-Object {MultiplyEven -Number $_}
```

```output
1 is not even
4
3 is not even
8
5 is not even
12
7 is not even
16
9 is not even
20
```

PowerShell에서 `return` 키워드가 사용 되지 않은 경우에도 값을 반환할 수 있습니다.
각 문의 결과가 반환 됩니다. 예를 들어 다음 문은 변수 값을 반환 합니다 `$a` .

```powershell
$a
return
```

다음 문은의 값도 반환 합니다 `$a` .

```powershell
return $a
```

다음 예에는 함수에서 계산을 수행 하 고 있음을 사용자에 게 알리기 위한 문이 포함 되어 있습니다.

```powershell
function calculation {
    param ($value)

    "Please wait. Working on calculation..."
    $value += 73
    return $value
}

$a = calculation 14
```

"잠시 기다려 주십시오. 계산 작업 중 ... " 문자열이 표시 되지 않습니다. 대신, `$a` 다음 예제와 같이 변수에 할당 됩니다.

```
PS> $a
Please wait. Working on calculation...
87
```

정보 문자열과 계산 결과가 모두 함수에 의해 반환 되 고 변수에 할당 됩니다 `$a` .

PowerShell 5.0부터 함수 내에 메시지를 표시 하려는 경우 스트림을 사용할 수 있습니다 `Information` . 아래 코드에서는 Continue를 사용 하 여 cmdlet을 사용 하는 위의 예를 수정 `Write-Information` `InformationAction` 합니다. 

```powershell
function calculation {
    param ($value)

    Write-Information "Please wait. Working on calculation..." -InformationAction Continue
    $value += 73
    return $value
}

$a = calculation 14
```

```output
Please wait. Working on calculation...
C:\PS> $a
87
```

### <a name="return-values-and-the-pipeline"></a>반환 값 및 파이프라인

스크립트 블록이 나 함수에서 컬렉션을 반환 하면 PowerShell에서 자동으로 멤버를 롤링 하지 않으며 파이프라인을 통해 한 번에 하나씩 해당 멤버를 전달 합니다. 이는 PowerShell의 일회성 처리로 인 한 것입니다. 자세한 내용은 [about_pipelines](about_pipelines.md)를 참조 하세요.

이 개념은 숫자의 배열을 반환 하는 다음 샘플 함수에서 설명 합니다. 함수의 출력은 파이프라인의 개체 수를 계산 하는 cmdlet으로 파이프 됩니다 `Measure-Object` .

```powershell
function Test-Return
{
    $array = 1,2,3
    return $array
}
Test-Return | Measure-Object
```

```Output
Count    : 3
Average  :
Sum      :
Maximum  :
Minimum  :
Property :
```

스크립트 블록이 나 함수에서 컬렉션을 단일 개체로 반환 하도록 강제 하려면 다음 두 가지 방법 중 하나를 사용 합니다.

- 단항 배열 식

  단항 식을 활용 하 여 다음 예제에 나와 있는 것 처럼 반환 값을 파이프라인에서 단일 개체로 보낼 수 있습니다.

  ```powershell
  function Test-Return
  {
      $array = 1,2,3
      return (, $array)
  }
  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

- `Write-Output`**Noenumerate** 매개 변수 사용.

  `Write-Output` **Noenumerate** 매개 변수와 함께 cmdlet을 사용할 수도 있습니다. 아래 예제에서는 cmdlet을 사용 하 여 `Measure-Object` 키워드를 통해 샘플 함수에서 파이프라인으로 전송 된 개체 수를 계산 합니다 `return` .

  ```powershell
  function Test-Return
  {
      $array = 1, 2, 3
      return Write-Output -NoEnumerate $array
  }

  Test-Return | Measure-Object
  ```

  ```Output
  Count    : 1
  Average  :
  Sum      :
  Maximum  :
  Minimum  :
  Property :
  ```

## <a name="see-also"></a>참고 항목

[about_Language_Keywords](about_Language_Keywords.md)

[about_Functions](about_Functions.md)

[about_Scopes](about_Scopes.md)

[about_Classes](about_Classes.md)

[Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information)

[about_Script_Blocks](about_Script_Blocks.md)

