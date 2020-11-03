---
description: Microsoft .NET 형식에서 작동 하는 연산자에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 807b99175463b930177f293eaf6c2fd8cc5bc224
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224441"
---
# <a name="about-type-operators"></a>형식 연산자 정보

## <a name="short-description"></a>간단한 설명
Microsoft .NET 형식에서 작동 하는 연산자에 대해 설명 합니다.

## <a name="long-description"></a>자세한 설명

부울 형식 연산자 ( `-is` 및 `-isNot` )는 개체가 지정 된 .net 형식의 인스턴스인지 여부를 알려 줍니다. 형식이와 일치 하는 `-is` 경우 연산자는 **TRUE** 값을 반환 하 고 그렇지 않으면 **FALSE** 값을 반환 합니다. 형식이와 일치 하는 `-isNot` 경우 연산자는 **FALSE** 값을 반환 하 고 그렇지 않으면 **TRUE** 값을 반환 합니다.

`-as`연산자가 입력 개체를 지정 된 .net 형식으로 변환 하려고 합니다. 성공 하면 변환 된 개체를 반환 합니다. 실패하면 `$null`를 반환합니다. 오류를 반환 하지 않습니다.

다음 표에서는 PowerShell의 형식 연산자를 보여 줍니다.

|연산자|설명                |예제                          |
|--------|---------------------------|---------------------------------|
|`-is`   |입력이 인 경우 TRUE를 반환 합니다.|`(get-date) -is [DateTime]`      |
|        |는의 인스턴스입니다.      |`True`                           |
|        |지정 된 .NET 유형입니다.       |                                 |
|`-isNot`|입력이 인 경우 TRUE를 반환 합니다.|`(get-date) -isNot [DateTime]`   |
|        |의 인스턴스가 아닙니다.     |`False`                          |
|        |specified.NET 유형입니다.        |                                 |
|`-as`   |입력을로 변환 합니다.  |`"5/7/07" -as [DateTime]`        |
|        |지정 된 .NET 유형입니다.       |`Monday, May 7, 2007 12:00:00 AM`|

형식 연산자의 구문은 다음과 같습니다.

```powershell
<input> <operator> [.NET type]
```

다음 구문을 사용할 수도 있습니다.

```powershell
<input> <operator> ".NET type"
```

.NET 형식은 대괄호의 형식 이름 또는 system.string의 경우 또는와 같은 문자열로 작성 될 수 있습니다 `[DateTime]` . `"DateTime"` **System.DateTime** 형식이 시스템 네임 스페이스의 루트에 없는 경우 개체 형식의 전체 이름을 지정 합니다. "System"을 생략할 수 있습니다. 예를 들어, **system.web. 프로세스** 를 지정 하려면, 또는를 입력 `[System.Diagnostics.Process]` `[Diagnostics.Process]` `"Diagnostics.Process"` 합니다.

형식 연산자는 항상 입력 개체에 대해 전체적으로 작동 합니다. 즉, 입력 개체가 컬렉션인 경우 컬렉션의 _요소_ 형식이 아니라 테스트 되는 _컬렉션_ 형식입니다.

### <a name="-isisnot-operators"></a>-is/isNot 연산자

**부울** 형식 연산자 ( `-is` 및)는 `-isNot` 입력이 개체의 컬렉션인 경우에도 항상 **부울** 값을 반환 합니다.

`<input>`가 .Net 형식에서 파생 되거나 .Net 형식에서 _파생_ 된 형식인 경우 연산자는을 `-is` 반환 `$True` 합니다.

예를 들어 **system.io.directoryinfo** 형식은 **FileSystemInfo** 형식에서 파생 됩니다. 따라서 두 예제 모두 **True** 를 반환 합니다.

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

`-is`연산자는가 `<input>` 비교에서 인터페이스를 구현 하는 경우 인터페이스를 일치 시킬 수도 있습니다. 이 예제에서 입력은 배열입니다. 배열은 **Collections** 인터페이스를 구현 합니다.

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a>-as 연산자

`-as`연산자가 입력 개체를 지정 된 .net 형식으로 변환 하려고 합니다. 성공 하면 변환 된 개체를 반환 합니다. 실패 하면이 반환 `$null` 됩니다. 오류를 반환 하지 않습니다.

`<input>`가 .Net 형식에서 _파생_ 된 형식이 면에서 반환 하는 `-as` _passes through_ 입력 개체를 반환 합니다. 예를 들어 **system.io.directoryinfo** 형식은 **FileSystemInfo** 형식에서 파생 됩니다. 따라서 다음 예제에서는 개체 형식이 변경 되지 않습니다.

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a>DateTime 형식을 변환 하는 것은 문화권을 구분 합니다.

형식 캐스팅과 달리 연산자를 `[DateTime]` 사용 하 여 형식으로 변환 하는 `-as` 것은 현재 문화권의 규칙에 따라 형식이 지정 된 문자열만 사용 합니다.

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr-FR'
PS> '13/5/20' -as [datetime]

mercredi 13 mai 2020 00:00:00

PS> '05/13/20' -as [datetime]
PS> [datetime]'05/13/20'

mercredi 13 mai 2020 00:00:00

PS> [datetime]'13/05/20'
InvalidArgument: Cannot convert value "13/05/20" to type "System.DateTime".
Error: "String '13/05/20' was not recognized as a valid DateTime."
```

개체의 .NET 형식을 찾으려면 cmdlet을 사용 합니다 `Get-Member` . 또는이 메서드의 **FullName** 속성과 함께 모든 개체의 **GetType** 메서드를 사용 합니다. 예를 들어 다음 문은 명령의 반환 값 형식을 가져옵니다 `Get-Culture` .

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a>예제

다음 예에서는 형식 연산자를 사용 하는 몇 가지 방법을 보여 줍니다.

```powershell
PS> 32 -is [Float]
False

PS> 32 -is "int"
True

PS> (get-date) -is [DateTime]
True

PS> "12/31/2007" -is [DateTime]
False

PS> "12/31/2007" -is [String]
True

PS> (get-process PowerShell)[0] -is [System.Diagnostics.Process]
True

PS> (get-command get-member) -is [System.Management.Automation.CmdletInfo]
True
```

다음 예제에서는 입력이 개체 컬렉션인 경우 컬렉션의 개별 개체 형식이 아니라 컬렉션의 .NET 형식인 일치 하는 형식을 보여 줍니다.

이 예제에서 및 cmdlet은 모두 `Get-Culture` `Get-UICulture` **system.object** 개체를 반환 하지만 이러한 개체의 컬렉션은 system.object 배열입니다.

```powershell
PS> (get-culture) -is [System.Globalization.CultureInfo]
True

PS> (get-uiculture) -is [System.Globalization.CultureInfo]
True

PS> (get-culture), (get-uiculture) -is [System.Globalization.CultureInfo]
False

PS> (get-culture), (get-uiculture) -is [Array]
True

PS> (get-culture), (get-uiculture) | foreach {
  $_ -is [System.Globalization.CultureInfo])
}
True
True

PS> (get-culture), (get-uiculture) -is [Object]
True
```

다음 예에서는 연산자를 사용 하는 방법을 보여 줍니다 `-as` .

```powershell
PS> "12/31/07" -is [DateTime]
False

PS> "12/31/07" -as [DateTime]
Monday, December 31, 2007 12:00:00 AM

PS> $date = "12/31/07" -as [DateTime]

C:\PS>$a -is [DateTime]
True

PS> 1031 -as [System.Globalization.CultureInfo]

LCID      Name      DisplayName
----      ----      -----------
1031      de-DE     German (Germany)
```

다음 예제에서는 `-as` 연산자가 입력 개체를 .net 형식으로 변환할 수 없는 경우를 반환 합니다 `$null` .

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a>참고 항목

[about_Operators](about_Operators.md)
