---
description: PowerShell에서 해시 테이블을 만들고 사용 하 고 정렬 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: aa56a29d3888f4283a5a9510970e53ea678d01f7
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389320"
---
# <a name="about-hash-tables"></a>해시 테이블 정보

## <a name="short-description"></a>간단한 설명
PowerShell에서 해시 테이블을 만들고 사용 하 고 정렬 하는 방법을 설명 합니다.

## <a name="long-description"></a>자세한 설명

사전 또는 결합형 배열이 라고도 하는 해시 테이블은 하나 이상의 키/값 쌍을 저장 하는 간단한 데이터 구조입니다. 예를 들어 해시 테이블에는 일련의 IP 주소와 컴퓨터 이름이 포함 될 수 있습니다. 여기서 IP 주소는 키 이며 컴퓨터 이름은 값 이거나 그 반대의 경우도 마찬가지입니다.

PowerShell에서 각 해시 테이블은 해시 테이블 (System.object) 개체입니다. PowerShell에서 해시 테이블 개체의 속성 및 메서드를 사용할 수 있습니다.

PowerShell 3.0부터 [정렬 된] 특성을 사용 하 여 PowerShell에서 순서가 지정 된 사전 (OrderedDictionary)을 만들 수 있습니다.

순서가 지정 된 사전은 키가 나열 된 순서 대로 항상 표시 된다는 점에서 해시 테이블과 다릅니다. 해시 테이블의 키 순서는 결정 되지 않습니다.

해시 테이블의 키와 값은 .NET 개체 이기도 합니다. 가장 일반적으로 문자열이 나 정수 이지만 모든 개체 유형을 가질 수 있습니다. 또한 키 값이 다른 해시 테이블인 중첩 된 해시 테이블을 만들 수 있습니다.

해시 테이블은 데이터를 찾고 검색 하는 데 매우 효율적 이기 때문에 자주 사용 됩니다. 해시 테이블을 사용 하 여 목록을 저장 하 고 PowerShell에서 계산 된 속성을 만들 수 있습니다. 그리고 PowerShell에는 문자열을 해시 테이블로 변환 하는 Convertfrom-csv cmdlet이 있습니다.

### <a name="syntax"></a>구문

해시 테이블의 구문은 다음과 같습니다.

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

순서가 지정 된 사전의 구문은 다음과 같습니다.

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

[정렬 된] 특성은 PowerShell 3.0에서 도입 되었습니다.

### <a name="creating-hash-tables"></a>해시 테이블 만들기

해시 테이블을 만들려면 다음 지침을 따르세요.

- @ 기호를 사용 하 여 해시 테이블을 시작 합니다.
- 해시 테이블을 중괄호 ()로 묶습니다 {} .
- 해시 테이블의 내용에 대해 하나 이상의 키/값 쌍을 입력 합니다.
- 등호 (=)를 사용 하 여 각 키를 해당 값과 구분 합니다.
- 세미콜론 (;)을 사용 합니다. 또는 줄 바꿈으로 키/값 쌍을 구분 합니다.
- 공백을 포함 하는 키는 따옴표로 묶어야 합니다. 값은 유효한 PowerShell 식 이어야 합니다. 문자열은 공백이 포함 되지 않은 경우에도 따옴표로 묶어야 합니다.
- 해시 테이블을 관리 하려면 변수에 변수를 저장 합니다.
- 변수에 순서가 지정 된 해시 테이블을 할당 하는 경우에는 [순서가 지정 된] 특성을 "@" 기호 앞에 배치 합니다. 변수 이름 앞에 놓으면 명령이 실패 합니다.

$Hash 값에 빈 해시 테이블을 만들려면 다음을 입력 합니다.

```powershell
$hash = @{}
```

해시 테이블을 만들 때 키 및 값을 해시 테이블에 추가할 수도 있습니다. 예를 들어 다음 문은 세 개의 키가 있는 해시 테이블을 만듭니다.

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a>정렬 된 사전 만들기

OrderedDictionary 형식의 개체를 추가 하 여 정렬 된 사전을 만들 수 있지만 정렬 된 사전을 만드는 가장 쉬운 방법은 [정렬 된] 특성을 사용 하는 것입니다.

[정렬 된] 특성은 PowerShell 3.0에서 도입 되었습니다.

"@" 기호 바로 앞에 특성을 추가 합니다.

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

해시 테이블을 사용 하는 것과 동일한 방식으로 순서가 지정 된 사전을 사용할 수 있습니다.
두 유형을 모두 해시 테이블 또는 사전을 사용 하는 매개 변수 값으로 사용할 수 있습니다 (iDictionary).

[정렬 된] 특성을 사용 하 여 해시 테이블을 변환 하거나 캐스팅할 수는 없습니다. 정렬 된 특성을 변수 이름 앞에 배치 하는 경우 명령이 실패 하 고 다음과 같은 오류 메시지가 표시 됩니다.

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

식을 수정 하려면 [정렬 된] 특성을 이동 합니다.

```powershell
PS C:\> $hash = [ordered]@{}
```

정렬 된 사전을 해시 테이블로 캐스팅할 수 있지만 변수를 지우고 새 값을 입력 하는 경우에도 정렬 된 특성을 복구할 수 없습니다. 순서를 다시 설정 하려면 변수를 제거 하 고 다시 만들어야 합니다.

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a>해시 테이블 표시

변수에 저장 된 해시 테이블을 표시 하려면 변수 이름을 입력 합니다.
기본적으로 해시 테이블은 하나의 키 열과 값에 대 한 하나의 열이 있는 테이블로 표시 됩니다.

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

해시 테이블에는 키와 값 속성이 있습니다. 점 표기법을 사용 하 여 모든 키 또는 모든 값을 표시 합니다.

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

또한 각 키 이름은 해시 테이블의 속성 이며, 해당 값은 키-이름 속성의 값입니다. 다음 형식을 사용 하 여 속성 값을 표시 합니다.

```powershell
$hashtable.<key>
<value>
```

예를 들어:

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

키 이름이 HashTable 형식의 속성 이름 중 하 나와 충돌 하는 경우 `PSBase` 를 사용 하 여 해당 속성에 액세스할 수 있습니다. 예를 들어 키 이름이이 `keys` 고 키 컬렉션을 반환 하려는 경우 다음 구문을 사용 합니다.

```powershell
$hashtable.PSBase.Keys
```

해시 테이블에는 해시 테이블의 키-값 쌍 수를 나타내는 Count 속성이 있습니다.

```powershell
C:\PS> $hash.count
3
```

해시 테이블 테이블은 배열이 아니므로 해시 테이블에 대 한 인덱스로 정수를 사용할 수 없지만 키 이름을 사용 하 여 해시 테이블로 인덱싱할 수 있습니다.
키가 문자열 값 이면 키 이름을 따옴표로 묶으십시오.

예를 들어:

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a>키 및 값 추가 및 제거

해시 테이블에 키 및 값을 추가 하려면 다음 명령 형식을 사용 합니다.

```powershell
$hash["<key>"] = "<value>"
```

예를 들어, "Now" 값을 가진 "Time" 키를 해시 테이블에 추가 하려면 다음 문 형식을 사용 합니다.

```powershell
$hash["Time"] = "Now"
```

또한 System.object 개체의 Add 메서드를 사용 하 여 해시 테이블에 키 및 값을 추가할 수 있습니다. Add 메서드의 구문은 다음과 같습니다.

```powershell
Add(Key, Value)
```

예를 들어, "Now" 값을 가진 "Time" 키를 해시 테이블에 추가 하려면 다음 문 형식을 사용 합니다.

```powershell
$hash.Add("Time", "Now")
```

더하기 연산자 (+)를 사용 하 여 해시 테이블에 키 및 값을 추가 하 여 기존 해시 테이블에 해시 테이블을 추가할 수 있습니다. 예를 들어 다음 문은 $hash 변수의 해시 테이블에 "Now" 값을 가진 "Time" 키를 추가 합니다.

```powershell
$hash = $hash + @{Time="Now"}
```

변수에 저장 된 값을 추가할 수도 있습니다.

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

빼기 연산자를 사용 하 여 해시 테이블에서 키/값 쌍을 제거할 수는 없지만 Hashtable 개체의 Remove 메서드는 사용할 수 있습니다. Remove 메서드는 키를 해당 값으로 사용 합니다.

Remove 메서드의 구문은 다음과 같습니다.

```
Remove(Key)
```

예를 들어 $hash 변수 값의 해시 테이블에서 Time = Now key/value 쌍을 제거 하려면 다음을 입력 합니다.

```powershell
$hash.Remove("Time")
```

Contains, Clear, Clone 및 CopyTo를 포함 하 여 PowerShell에서 해시 테이블 개체의 모든 속성 및 메서드를 사용할 수 있습니다. 해시 테이블 개체에 대 한 자세한 내용은 [system.object](/dotnet/api/system.collections.hashtable)를 참조 하십시오.

### <a name="object-types-in-hashtables"></a>해시 테이블의 개체 형식

해시 테이블의 키와 값은 모든 .NET 개체 유형을 포함할 수 있으며, 단일 해시 테이블에는 여러 유형의 키와 값이 있을 수 있습니다.

다음 문은 프로세스 이름 문자열의 해시 테이블을 만들고 개체 값을 처리 한 다음 변수에 저장 합니다 `$p` .

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

에서 해시 테이블을 표시 `$p` 하 고 키 이름 속성을 사용 하 여 값을 표시할 수 있습니다.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

해시 테이블의 키는 .NET 형식일 수도 있습니다. 다음 문은 변수의 해시 테이블에 키/값 쌍을 추가 합니다 `$p` . 키는 WinRM 서비스를 나타내는 서비스 개체이 고 값은 서비스의 현재 상태입니다.

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

해시 테이블의 다른 쌍에 사용 하는 것과 동일한 방법을 사용 하 여 새 키/값 쌍을 표시 하 고 액세스할 수 있습니다.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

해시 테이블의 키와 값은 해시 테이블 개체 일 수도 있습니다. 다음 문은 키가 문자열인 변수의 해시 테이블에 키/값 쌍을 추가 하 `$p` 고, 값은 3 개의 키/값 쌍이 있는 해시 테이블을 Hash2 합니다.

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

동일한 메서드를 사용 하 여 새 값을 표시 하 고 액세스할 수 있습니다.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a>키 및 값 정렬

해시 테이블의 항목은 기본적으로 순서가 지정 되지 않습니다. 키/값 쌍은 표시 될 때마다 다른 순서로 표시 될 수 있습니다.

해시 테이블을 정렬할 수는 없지만, 해시 테이블의 GetEnumerator 메서드를 사용 하 여 키 및 값을 열거 한 다음 Sort-Object cmdlet을 사용 하 여 표시를 위해 열거 된 값을 정렬할 수 있습니다.

예를 들어 다음 명령은 변수에 있는 해시 테이블의 키와 값을 열거 한 `$p` 다음 키를 알파벳 순서로 정렬 합니다.

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

다음 명령은 동일한 절차를 사용 하 여 해시 값을 내림차순으로 정렬 합니다.

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a>해시 테이블에서 개체 만들기

PowerShell 3.0부터 속성 및 속성 값의 해시 테이블에서 개체를 만들 수 있습니다.

구문은 다음과 같습니다.

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

이 메서드는 null 생성자, 즉 매개 변수가 없는 생성자를 포함 하는 클래스에 대해서만 작동 합니다. 개체 속성은 public 이어야 하며 설정 가능 해야 합니다.

자세한 내용은 [about_Object_Creation](about_Object_Creation.md)를 참조 하세요.

### <a name="convertfrom-stringdata"></a>ConvertFrom-StringData

`ConvertFrom-StringData`Cmdlet은 키/값 쌍의 문자열 또는 문자열을 해시 테이블로 변환 합니다. `ConvertFrom-StringData`스크립트의 데이터 섹션에서 cmdlet을 안전 하 게 사용할 수 있으며이 cmdlet을 cmdlet과 함께 사용 `Import-LocalizedData` 하 여 현재 사용자의 UI (사용자 인터페이스) 문화권에 사용자 메시지를 표시할 수 있습니다.

여기서 문자열은 해시 테이블의 값에 따옴표가 포함 된 경우에 특히 유용 합니다. 이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.

다음 예제에서는 이전 예제에서 사용자 메시지의 여기 문자열을 만드는 방법과를 사용 하 여 `ConvertFrom-StringData` 문자열을 해시 테이블로 변환 하는 방법을 보여 줍니다.

다음 명령은 키/값 쌍의 문자열을 만든 다음 \$ 문자열 변수에 저장 합니다.

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

이 명령은 ConvertFrom-StringData cmdlet을 사용 하 여 다음 문자열을 해시 테이블로 변환 합니다.

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

이러한 문자열에 대 한 자세한 내용은 [about_Quoting_Rules](about_Quoting_Rules.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[about_Arrays](about_Arrays.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Import-LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[System.Collections.Hashtable](/dotnet/api/system.collections.hashtable)
