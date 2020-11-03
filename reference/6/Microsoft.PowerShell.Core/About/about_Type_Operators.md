---
description: Microsoft .NET 형식에서 작동 하는 연산자에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/15/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_type_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Type_Operators
ms.openlocfilehash: 6b4b0f2eea28ddd5544174d01359491808e2e653
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "93224234"
---
# <a name="about-type-operators"></a><span data-ttu-id="eaf19-104">형식 연산자 정보</span><span class="sxs-lookup"><span data-stu-id="eaf19-104">About Type Operators</span></span>

## <a name="short-description"></a><span data-ttu-id="eaf19-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="eaf19-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="eaf19-106">Microsoft .NET 형식에서 작동 하는 연산자에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-106">Describes the operators that work with Microsoft .NET types.</span></span>

## <a name="long-description"></a><span data-ttu-id="eaf19-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="eaf19-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="eaf19-108">부울 형식 연산자 ( `-is` 및 `-isNot` )는 개체가 지정 된 .net 형식의 인스턴스인지 여부를 알려 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-108">The Boolean type operators (`-is` and `-isNot`) tell whether an object is an instance of a specified .NET type.</span></span> <span data-ttu-id="eaf19-109">형식이와 일치 하는 `-is` 경우 연산자는 **TRUE** 값을 반환 하 고 그렇지 않으면 **FALSE** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-109">The `-is` operator returns a value of **TRUE** if the type matches and a value of **FALSE** otherwise.</span></span> <span data-ttu-id="eaf19-110">형식이와 일치 하는 `-isNot` 경우 연산자는 **FALSE** 값을 반환 하 고 그렇지 않으면 **TRUE** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-110">The `-isNot` operator returns a value of **FALSE** if the type matches and a value of **TRUE** otherwise.</span></span>

<span data-ttu-id="eaf19-111">`-as`연산자가 입력 개체를 지정 된 .net 형식으로 변환 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-111">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="eaf19-112">성공 하면 변환 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-112">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="eaf19-113">실패하면 `$null`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-113">If it fails, it returns `$null`.</span></span> <span data-ttu-id="eaf19-114">오류를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-114">It does not return an error.</span></span>

<span data-ttu-id="eaf19-115">다음 표에서는 PowerShell의 형식 연산자를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-115">The following table lists the type operators in PowerShell.</span></span>

|<span data-ttu-id="eaf19-116">연산자</span><span class="sxs-lookup"><span data-stu-id="eaf19-116">Operator</span></span>|<span data-ttu-id="eaf19-117">Description</span><span class="sxs-lookup"><span data-stu-id="eaf19-117">Description</span></span>                |<span data-ttu-id="eaf19-118">예제</span><span class="sxs-lookup"><span data-stu-id="eaf19-118">Example</span></span>                          |
|--------|---------------------------|---------------------------------|
|`-is`   |<span data-ttu-id="eaf19-119">입력이 인 경우 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-119">Returns TRUE when the input</span></span>|`(get-date) -is [DateTime]`      |
|        |<span data-ttu-id="eaf19-120">는의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-120">is an instance of the</span></span>      |`True`                           |
|        |<span data-ttu-id="eaf19-121">지정 된 .NET 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-121">specified .NET type.</span></span>       |                                 |
|`-isNot`|<span data-ttu-id="eaf19-122">입력이 인 경우 TRUE를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-122">Returns TRUE when the input</span></span>|`(get-date) -isNot [DateTime]`   |
|        |<span data-ttu-id="eaf19-123">의 인스턴스가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-123">not an instance of the</span></span>     |`False`                          |
|        |<span data-ttu-id="eaf19-124">specified.NET 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-124">specified.NET type.</span></span>        |                                 |
|`-as`   |<span data-ttu-id="eaf19-125">입력을로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-125">Converts the input to the</span></span>  |`"5/7/07" -as [DateTime]`        |
|        |<span data-ttu-id="eaf19-126">지정 된 .NET 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-126">specified .NET type.</span></span>       |`Monday, May 7, 2007 12:00:00 AM`|

<span data-ttu-id="eaf19-127">형식 연산자의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-127">The syntax of the type operators is as follows:</span></span>

```powershell
<input> <operator> [.NET type]
```

<span data-ttu-id="eaf19-128">다음 구문을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-128">You can also use the following syntax:</span></span>

```powershell
<input> <operator> ".NET type"
```

<span data-ttu-id="eaf19-129">.NET 형식은 대괄호의 형식 이름 또는 system.string의 경우 또는와 같은 문자열로 작성 될 수 있습니다 `[DateTime]` . `"DateTime"` **System.DateTime**</span><span class="sxs-lookup"><span data-stu-id="eaf19-129">The .NET type can be written as a type name in brackets or a string, such as `[DateTime]` or `"DateTime"` for **System.DateTime**.</span></span> <span data-ttu-id="eaf19-130">형식이 시스템 네임 스페이스의 루트에 없는 경우 개체 형식의 전체 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-130">If the type is not at the root of the system namespace, specify the full name of the object type.</span></span> <span data-ttu-id="eaf19-131">"System"을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-131">You can omit "System.".</span></span> <span data-ttu-id="eaf19-132">예를 들어, **system.web. 프로세스** 를 지정 하려면, 또는를 입력 `[System.Diagnostics.Process]` `[Diagnostics.Process]` `"Diagnostics.Process"` 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-132">For example, to specify **System.Diagnostics.Process** , enter `[System.Diagnostics.Process]`, `[Diagnostics.Process]`, or `"Diagnostics.Process"`.</span></span>

<span data-ttu-id="eaf19-133">형식 연산자는 항상 입력 개체에 대해 전체적으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-133">The type operators always operate on the input object as a whole.</span></span> <span data-ttu-id="eaf19-134">즉, 입력 개체가 컬렉션인 경우 컬렉션의 _요소_ 형식이 아니라 테스트 되는 _컬렉션_ 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-134">That is, if the input object is a collection, it is the _collection_ type that is tested, not the types of the collection's _elements_.</span></span>

### <a name="-isisnot-operators"></a><span data-ttu-id="eaf19-135">-is/isNot 연산자</span><span class="sxs-lookup"><span data-stu-id="eaf19-135">-is/isNot operators</span></span>

<span data-ttu-id="eaf19-136">**부울** 형식 연산자 ( `-is` 및)는 `-isNot` 입력이 개체의 컬렉션인 경우에도 항상 **부울** 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-136">The **Boolean** type operators (`-is` and `-isNot`) always return a **Boolean** value, even if the input is a collection of objects.</span></span>

<span data-ttu-id="eaf19-137">`<input>`가 .Net 형식에서 파생 되거나 .Net 형식에서 _파생_ 된 형식인 경우 연산자는을 `-is` 반환 `$True` 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-137">If `<input>` is a type that is the same as or is _derived_ from the .NET Type, the `-is` operator returns `$True`.</span></span>

<span data-ttu-id="eaf19-138">예를 들어 **system.io.directoryinfo** 형식은 **FileSystemInfo** 형식에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-138">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="eaf19-139">따라서 두 예제 모두 **True** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-139">Therefore, both of these examples return **True**.</span></span>

```powershell
PS> (Get-Item /) -is [System.IO.DirectoryInfo]
True
PS> (Get-Item /) -is [System.IO.FileSystemInfo]
True
```

<span data-ttu-id="eaf19-140">`-is`연산자는가 `<input>` 비교에서 인터페이스를 구현 하는 경우 인터페이스를 일치 시킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-140">The `-is` operator can also match interfaces if the `<input>` implements the interface in the comparison.</span></span> <span data-ttu-id="eaf19-141">이 예제에서 입력은 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-141">In this example, the input is an array.</span></span> <span data-ttu-id="eaf19-142">배열은 **Collections** 인터페이스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-142">Arrays implement the **System.Collections.IList** interface.</span></span>

```powershell
PS> 1, 2 -is [System.Collections.IList]
True
```

### <a name="-as-operator"></a><span data-ttu-id="eaf19-143">-as 연산자</span><span class="sxs-lookup"><span data-stu-id="eaf19-143">-as operator</span></span>

<span data-ttu-id="eaf19-144">`-as`연산자가 입력 개체를 지정 된 .net 형식으로 변환 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-144">The `-as` operator tries to convert the input object to the specified .NET type.</span></span> <span data-ttu-id="eaf19-145">성공 하면 변환 된 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-145">If it succeeds, it returns the converted object.</span></span> <span data-ttu-id="eaf19-146">실패 하면이 반환 `$null` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-146">It if fails, it returns `$null`.</span></span> <span data-ttu-id="eaf19-147">오류를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-147">It does not return an error.</span></span>

<span data-ttu-id="eaf19-148">`<input>`가 .Net 형식에서 _파생_ 된 형식이 면에서 반환 하는 `-as` _passes through_ 입력 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-148">If the `<input>` is a type that is _derived_ from the .NET Type `-as` _passes through_ returns input object unchanged.</span></span> <span data-ttu-id="eaf19-149">예를 들어 **system.io.directoryinfo** 형식은 **FileSystemInfo** 형식에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-149">For example, the **DirectoryInfo** type is derived from the **FileSystemInfo** type.</span></span> <span data-ttu-id="eaf19-150">따라서 다음 예제에서는 개체 형식이 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-150">Therefore, the object type is unchanged in the following example:</span></span>

```powershell
PS> $fsroot = (Get-Item /) -as [System.IO.FileSystemInfo]
PS> $fsroot.GetType().FullName
System.IO.DirectoryInfo
```

#### <a name="converting-the-datetime-type-is-culture-sensitive"></a><span data-ttu-id="eaf19-151">DateTime 형식을 변환 하는 것은 문화권을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-151">Converting the DateTime type is culture-sensitive</span></span>

<span data-ttu-id="eaf19-152">형식 캐스팅과 달리 연산자를 `[DateTime]` 사용 하 여 형식으로 변환 하는 `-as` 것은 현재 문화권의 규칙에 따라 형식이 지정 된 문자열만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-152">Unlike type casting, converting to `[DateTime]` type using the `-as` operator only works with strings that are formatted according to the rules of the current culture.</span></span>

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

<span data-ttu-id="eaf19-153">개체의 .NET 형식을 찾으려면 cmdlet을 사용 합니다 `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="eaf19-153">To find the .NET type of an object, use the `Get-Member` cmdlet.</span></span> <span data-ttu-id="eaf19-154">또는이 메서드의 **FullName** 속성과 함께 모든 개체의 **GetType** 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-154">Or, use the **GetType** method of all the objects together with the **FullName** property of this method.</span></span> <span data-ttu-id="eaf19-155">예를 들어 다음 문은 명령의 반환 값 형식을 가져옵니다 `Get-Culture` .</span><span class="sxs-lookup"><span data-stu-id="eaf19-155">For example, the following statement gets the type of the return value of a `Get-Culture` command:</span></span>

```powershell
PS> (Get-Culture).GetType().FullName
System.Globalization.CultureInfo
```

## <a name="examples"></a><span data-ttu-id="eaf19-156">예제</span><span class="sxs-lookup"><span data-stu-id="eaf19-156">EXAMPLES</span></span>

<span data-ttu-id="eaf19-157">다음 예에서는 형식 연산자를 사용 하는 몇 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-157">The following examples show some uses of the Type operators:</span></span>

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

<span data-ttu-id="eaf19-158">다음 예제에서는 입력이 개체 컬렉션인 경우 컬렉션의 개별 개체 형식이 아니라 컬렉션의 .NET 형식인 일치 하는 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-158">The following example shows that when the input is a collection of objects, the matching type is the .NET type of the collection, not the type of the individual objects in the collection.</span></span>

<span data-ttu-id="eaf19-159">이 예제에서 및 cmdlet은 모두 `Get-Culture` `Get-UICulture` **system.object** 개체를 반환 하지만 이러한 개체의 컬렉션은 system.object 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="eaf19-159">In this example, although both the `Get-Culture` and `Get-UICulture` cmdlets return **System.Globalization.CultureInfo** objects, a collection of these objects is a System.Object array.</span></span>

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

<span data-ttu-id="eaf19-160">다음 예에서는 연산자를 사용 하는 방법을 보여 줍니다 `-as` .</span><span class="sxs-lookup"><span data-stu-id="eaf19-160">The following examples show how to use the `-as` operator.</span></span>

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

<span data-ttu-id="eaf19-161">다음 예제에서는 `-as` 연산자가 입력 개체를 .net 형식으로 변환할 수 없는 경우를 반환 합니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="eaf19-161">The following example shows that when the `-as` operator cannot convert the input object to the .NET type, it returns `$null`.</span></span>

```powershell
PS> 1031 -as [System.Diagnostics.Process]
PS>
```

## <a name="see-also"></a><span data-ttu-id="eaf19-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eaf19-162">SEE ALSO</span></span>

[<span data-ttu-id="eaf19-163">about_Operators</span><span class="sxs-lookup"><span data-stu-id="eaf19-163">about_Operators</span></span>](about_Operators.md)
