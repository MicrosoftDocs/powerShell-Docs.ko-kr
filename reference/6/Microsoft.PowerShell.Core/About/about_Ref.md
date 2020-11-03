---
description: 참조 형식 변수를 만들고 사용 하는 방법을 설명 합니다. 참조 형식 변수를 사용 하 여 함수가 전달 되는 변수의 값을 변경할 수 있도록 허용할 수 있습니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/24/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_ref?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Ref
ms.openlocfilehash: fefc0f002db0b9591b2d23e148db381f7413871f
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221322"
---
# <a name="about-ref"></a>Ref 정보

## <a name="short-description"></a>간단한 설명
참조 형식 변수를 만들고 사용 하는 방법을 설명 합니다. 참조 형식 변수를 사용 하 여 함수가 전달 되는 변수의 값을 변경할 수 있도록 허용할 수 있습니다.

## <a name="long-description"></a>자세한 설명입니다.

*참조* 또는 *값* 을 기준으로 함수에 변수를 전달할 수 있습니다.

*값으로* 변수를 전달 하는 경우 데이터의 복사본을 전달 합니다.

다음 예제에서 함수는 전달 되는 변수의 값을 변경 합니다. PowerShell에서 정수는 값 형식 이므로 값으로 전달 됩니다.
따라서 값은 `$var` 함수 범위 밖으로 변경 되지 않습니다.

```powershell
Function Test($data)
{
    $data = 3
}

$var = 10
Test -data $var
$var
```

```output
10
```

다음 예제에서는를 포함 하는 변수를 `Hashtable` 함수에 전달 합니다. `Hashtable` 는 개체 형식 이므로 기본적으로 함수에 *참조로* 전달 됩니다.

변수를 *참조로* 전달 하는 경우 함수는 데이터를 변경할 수 있으며 함수가 실행 된 후에도 변경 내용이 유지 됩니다.

```powershell
Function Test($data)
{
    $data.Test = "New Text"
}

$var = @{}
Test -data $var
$var
```

```output
Name                           Value
----                           -----
Test                           New Text
```

함수는 함수 범위 외부에 유지 되는 새 키-값 쌍을 추가 합니다.

### <a name="writing-functions-to-accept-reference-parameters"></a>참조 매개 변수를 허용 하는 함수 작성

전달 되는 데이터 형식에 관계 없이 매개 변수를 참조로 사용 하도록 함수를 코딩할 수 있습니다. 이렇게 하려면 매개 변수 형식을, 또는로 지정 해야 합니다 `System.Management.Automation.PSReference` `[ref]` .

참조를 사용 하는 경우 `Value` 형식의 속성을 사용 `System.Management.Automation.PSReference` 하 여 데이터에 액세스 해야 합니다.

```powershell
Function Test([ref]$data)
{
    $data.Value = 3
}
```

참조를 필요로 하는 매개 변수에 변수를 전달 하려면 변수를 참조로 캐스트를 입력 해야 합니다.

> [!NOTE]
> 대괄호와 괄호는 모두 필요 합니다.

```powershell
$var = 10
Test -data ([ref]$var)
$var
```

```output
3
```

### <a name="passing-references-to-net-methods"></a>.NET 메서드에 참조 전달

일부 .NET 메서드는 변수를 참조로 전달 해야 할 수 있습니다. 메서드의 정의에서 매개 변수에, 또는 키워드를 사용 하는 경우 `in` `out` `ref` 참조가 필요 합니다.

```powershell
[int] | Get-Member -Static -Name TryParse
```

```output
Name     MemberType Definition
----     ---------- ----------
TryParse Method     static bool TryParse(string s, [ref] int result)
```

`TryParse`메서드는 문자열을 정수로 구문 분석 하려고 합니다. 메서드가 성공 하면 `$true` 가 반환 되 고 결과는 **참조로** 전달 된 변수에 저장 됩니다.

```
PS> $number = 0
PS> [int]::TryParse("15", ([ref]$number))
True
PS> $number
15
```

### <a name="references-and-scopes"></a>참조 및 범위

참조를 사용 하면 부모 범위의 변수 값을 자식 범위 내에서 변경할 수 있습니다.

```powershell
# Create a value type variable.
$i = 0
# Create a reference type variable.
$iRef = [ref]0
# Invoke a scriptblock to attempt to change both values.
&{$i++;$iRef.Value++}
# Output the results.
"`$i = $i;`$iRef = $($iRef.Value)"
```

```output
$i = 0;$iRef = 1
```

참조 형식의 변수만 변경 되었습니다.

## <a name="see-also"></a>참고 항목

[about_Variables](about_Variables.md)

[about_Environment_Variables](about_Environment_Variables.md)

[about_Functions](about_Functions.md)

[about_Script_Blocks](about_Script_Blocks.md)

[about_Scopes](about_scopes.md)
