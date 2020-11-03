---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/compare-object?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compare-Object
ms.openlocfilehash: c72cde8e626993726ae1a52206c88e20c3a7c588
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/24/2020
ms.locfileid: "93225233"
---
# <span data-ttu-id="7caff-103">Compare-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-103">Compare-Object</span></span>

## <span data-ttu-id="7caff-104">개요</span><span class="sxs-lookup"><span data-stu-id="7caff-104">Synopsis</span></span>
<span data-ttu-id="7caff-105">두 개체 집합을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-105">Compares two sets of objects.</span></span>

## <span data-ttu-id="7caff-106">구문</span><span class="sxs-lookup"><span data-stu-id="7caff-106">Syntax</span></span>

```
Compare-Object [-ReferenceObject] <PSObject[]> [-DifferenceObject] <PSObject[]>
 [-SyncWindow <Int32>] [-Property <Object[]>] [-ExcludeDifferent] [-IncludeEqual] [-PassThru]
 [-Culture <String>] [-CaseSensitive] [<CommonParameters>]
```

## <span data-ttu-id="7caff-107">Description</span><span class="sxs-lookup"><span data-stu-id="7caff-107">Description</span></span>

<span data-ttu-id="7caff-108">`Compare-Object`Cmdlet은 두 개체 집합을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-108">The `Compare-Object` cmdlet compares two sets of objects.</span></span> <span data-ttu-id="7caff-109">한 개체 집합은 **참조** 이 고 다른 개체 집합은 서로 **다릅니다**.</span><span class="sxs-lookup"><span data-stu-id="7caff-109">One set of objects is the **reference** , and the other set of objects is the **difference**.</span></span>

<span data-ttu-id="7caff-110">`Compare-Object` 전체 개체를 비교 하는 사용 가능한 메서드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-110">`Compare-Object` checks for available methods of comparing a whole object.</span></span> <span data-ttu-id="7caff-111">적절 한 메서드를 찾을 수 없는 경우 입력 개체의 **ToString ()** 메서드를 호출 하 고 문자열 결과를 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-111">If it can't find a suitable method, it calls the **ToString()** methods of the input objects and compares the string results.</span></span> <span data-ttu-id="7caff-112">비교에 사용할 속성을 하나 이상 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-112">You can provide one or more properties to be used for comparison.</span></span> <span data-ttu-id="7caff-113">속성이 제공 되는 경우 cmdlet은 해당 속성의 값만 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-113">When properties are provided, the cmdlet compares the values of those properties only.</span></span>

<span data-ttu-id="7caff-114">비교 결과는 속성 값이 **참조** 개체에만 표시 되는지 ( `<=` ) 아니면 **차이점** 개체 () 에서만 표시 되는지 여부를 나타냅니다 `=>` .</span><span class="sxs-lookup"><span data-stu-id="7caff-114">The result of the comparison indicates whether a property value appeared only in the **reference** object (`<=`) or only in the **difference** object (`=>`).</span></span> <span data-ttu-id="7caff-115">**Includeequal** 매개 변수가 사용 되는 경우 ( `==` )는 두 개체 모두에 값이 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-115">If the **IncludeEqual** parameter is used, (`==`) indicates the value is in both objects.</span></span>

<span data-ttu-id="7caff-116">**참조** 또는 **차이점** 개체가 null ( `$null` ) 이면에서 `Compare-Object` 종료 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-116">If the **reference** or the **difference** objects are null (`$null`), `Compare-Object` generates a terminating error.</span></span>

<span data-ttu-id="7caff-117">일부 예제에서는 스 플랫를 사용 하 여 코드 샘플의 줄 길이를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-117">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="7caff-118">자세한 내용은 [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7caff-118">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="7caff-119">예</span><span class="sxs-lookup"><span data-stu-id="7caff-119">Examples</span></span>

### <span data-ttu-id="7caff-120">예제 1-두 텍스트 파일의 내용 비교</span><span class="sxs-lookup"><span data-stu-id="7caff-120">Example 1 - Compare the content of two text files</span></span>

<span data-ttu-id="7caff-121">이 예에서는 두 텍스트 파일의 내용을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-121">This example compares the contents of two text files.</span></span> <span data-ttu-id="7caff-122">이 예제에서는 다음 두 텍스트 파일을 사용 하며, 각 값은 별도의 줄에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-122">The example uses the following two text files, with each value on a separate line.</span></span>

- <span data-ttu-id="7caff-123">`Testfile1.txt` dog, squirrel 및 bird 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-123">`Testfile1.txt` contains the values: dog, squirrel, and bird.</span></span>
- <span data-ttu-id="7caff-124">`Testfile2.txt` cat, bird 및 racoon 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-124">`Testfile2.txt` contains the values: cat, bird, and racoon.</span></span>

<span data-ttu-id="7caff-125">출력에는 파일 간에 다른 줄만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-125">The output displays only the lines that are different between the files.</span></span> <span data-ttu-id="7caff-126">`Testfile1.txt` 는 **참조** 개체 ( `<=` )이 고 `Testfile2.txt` 은 **차이** 개체 ( `=>` )입니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-126">`Testfile1.txt` is the **reference** object (`<=`) and `Testfile2.txt`is the **difference** object (`=>`).</span></span> <span data-ttu-id="7caff-127">내용이 두 파일에 모두 표시 되는 줄은 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-127">Lines with content that appear in both files aren't displayed.</span></span>

```powershell
Compare-Object -ReferenceObject (Get-Content -Path C:\Test\Testfile1.txt) -DifferenceObject (Get-Content -Path C:\Test\Testfile2.txt)
```

```Output
InputObject SideIndicator
----------- -------------
cat         =>
racoon      =>
dog         <=
squirrel    <=
```

### <span data-ttu-id="7caff-128">예제 2-콘텐츠의 각 줄 비교 및 차이점 제외</span><span class="sxs-lookup"><span data-stu-id="7caff-128">Example 2 - Compare each line of content and exclude the differences</span></span>

<span data-ttu-id="7caff-129">이 예제에서는 **Includeequal** 및 **excludedifferent** 매개 변수를 사용 하 여 두 텍스트 파일의 각 내용 줄을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-129">This example uses the **IncludeEqual** and **ExcludeDifferent** parameters to compare each line of content in two text files.</span></span>

<span data-ttu-id="7caff-130">이 명령은 **excludedifferent** 매개 변수를 사용 하기 때문에 출력 **에는 두** 파일에 포함 된 줄만 포함 됩니다 ( `==` ).</span><span class="sxs-lookup"><span data-stu-id="7caff-130">Because the command uses the **ExcludeDifferent** parameter, the output only contains lines contained in both files, as shown by the **SideIndicator** (`==`).</span></span>

```powershell
$objects = @{
  ReferenceObject = (Get-Content -Path C:\Test\Testfile1.txt)
  DifferenceObject = (Get-Content -Path C:\Test\Testfile2.txt)
}
Compare-Object @objects -IncludeEqual -ExcludeDifferent
```

```Output
InputObject SideIndicator
----------- -------------
bird        ==
```

<a id="ex3" />

### <span data-ttu-id="7caff-131">예 3-PassThru 매개 변수를 사용 하는 경우의 차이점 표시</span><span class="sxs-lookup"><span data-stu-id="7caff-131">Example 3 - Show the difference when using the PassThru parameter</span></span>

<span data-ttu-id="7caff-132">일반적으로는 `Compare-Object` 다음 속성을 사용 하 여 **PSCustomObject** 형식을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-132">Normally, `Compare-Object` returns a **PSCustomObject** type with the following properties:</span></span>

- <span data-ttu-id="7caff-133">비교할 **InputObject** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-133">The **InputObject** being compared</span></span>
- <span data-ttu-id="7caff-134">출력이 속한 입력 개체를 표시 하는가 중 **표시기** 속성</span><span class="sxs-lookup"><span data-stu-id="7caff-134">The **SideIndicator** property showing which input object the output belongs to</span></span>

<span data-ttu-id="7caff-135">**PassThru** 매개 변수를 사용 하는 경우 개체의 **형식은** 변경 되지 않지만 반환 되는 개체의 인스턴스에는 ' 이름 ' 이라는 추가 된 **참고 속성이** **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="7caff-135">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="7caff-136">나란히 **표시기** 는 출력이 속한 입력 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-136">**SideIndicator** shows which input object the output belongs to.</span></span>

<span data-ttu-id="7caff-137">다음 예에서는 다양 한 출력 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-137">The following examples shows the different output types.</span></span>

```powershell
$a = $True
Compare-Object -IncludeEqual $a $a
(Compare-Object -IncludeEqual $a $a) | Get-Member
```

```Output
InputObject SideIndicator
----------- -------------
       True ==

   TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
InputObject   NoteProperty System.Boolean InputObject=True
SideIndicator NoteProperty string SideIndicator===
```

```powershell
Compare-Object -IncludeEqual $a $a -PassThru
(Compare-Object -IncludeEqual $a $a -PassThru) | Get-Member
```

```Output
True

   TypeName: System.Boolean
Name          MemberType   Definition
----          ----------   ----------
CompareTo     Method       int CompareTo(System.Object obj), int CompareTo(bool value), int IComparable.CompareTo(Syst
Equals        Method       bool Equals(System.Object obj), bool Equals(bool obj), bool IEquatable[bool].Equals(bool ot
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
GetTypeCode   Method       System.TypeCode GetTypeCode(), System.TypeCode IConvertible.GetTypeCode()
ToBoolean     Method       bool IConvertible.ToBoolean(System.IFormatProvider provider)
ToByte        Method       byte IConvertible.ToByte(System.IFormatProvider provider)
ToChar        Method       char IConvertible.ToChar(System.IFormatProvider provider)
ToDateTime    Method       datetime IConvertible.ToDateTime(System.IFormatProvider provider)
ToDecimal     Method       decimal IConvertible.ToDecimal(System.IFormatProvider provider)
ToDouble      Method       double IConvertible.ToDouble(System.IFormatProvider provider)
ToInt16       Method       short IConvertible.ToInt16(System.IFormatProvider provider)
ToInt32       Method       int IConvertible.ToInt32(System.IFormatProvider provider)
ToInt64       Method       long IConvertible.ToInt64(System.IFormatProvider provider)
ToSByte       Method       sbyte IConvertible.ToSByte(System.IFormatProvider provider)
ToSingle      Method       float IConvertible.ToSingle(System.IFormatProvider provider)
ToString      Method       string ToString(), string ToString(System.IFormatProvider provider), string IConvertible.To
ToType        Method       System.Object IConvertible.ToType(type conversionType, System.IFormatProvider provider)
ToUInt16      Method       ushort IConvertible.ToUInt16(System.IFormatProvider provider)
ToUInt32      Method       uint IConvertible.ToUInt32(System.IFormatProvider provider)
ToUInt64      Method       ulong IConvertible.ToUInt64(System.IFormatProvider provider)
TryFormat     Method       bool TryFormat(System.Span[char] destination, [ref] int charsWritten)
SideIndicator NoteProperty string SideIndicator===
```

<span data-ttu-id="7caff-138">**PassThru** 를 사용 하는 경우 원래 개체 형식 ( **system.string)이 반환 됩니다.**</span><span class="sxs-lookup"><span data-stu-id="7caff-138">When using **PassThru** , the original object type ( **System.Boolean** ) is returned.</span></span> <span data-ttu-id="7caff-139">System.string 개체의 기본 형식으로 표시 된 출력에는 함께 표시 된 **표시기** 속성이 표시 **되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="7caff-139">Note how the output displayed by the default format for **System.Boolean** objects didn't display the **SideIndicator** property.</span></span> <span data-ttu-id="7caff-140">그러나 반환 된 system.string 개체에는 추가 된 **참고 속성이** **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="7caff-140">However, the returned **System.Boolean** object has the added **NoteProperty**.</span></span>

### <span data-ttu-id="7caff-141">예제 4-속성을 사용 하 여 두 개의 단순 개체 비교</span><span class="sxs-lookup"><span data-stu-id="7caff-141">Example 4 - Compare two simple objects using properties</span></span>

<span data-ttu-id="7caff-142">이 예제에서는 길이가 같은 두 개의 서로 다른 문자열을 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-142">In this example, we compare two different string that have the same length.</span></span>

```powershell
Compare-Object -ReferenceObject 'abc' -DifferenceObject 'xyz' -Property Length -IncludeEqual
```

```Output
Length SideIndicator
------ -------------
     3 ==
```

### <span data-ttu-id="7caff-143">예 5: 속성을 사용 하 여 복합 개체 비교</span><span class="sxs-lookup"><span data-stu-id="7caff-143">Example 5 - Comparing complex objects using properties</span></span>

<span data-ttu-id="7caff-144">이 예제에서는 복합 개체를 비교할 때의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-144">This example shows the behavior when comparing complex objects.</span></span> <span data-ttu-id="7caff-145">이 예에서는 PowerShell의 각 인스턴스에 대해 서로 다른 두 개의 프로세스 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-145">In this example we store two different process objects for different instances of PowerShell.</span></span> <span data-ttu-id="7caff-146">두 변수에 모두 동일한 이름의 프로세스 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-146">Both variables contain process objects with the same name.</span></span> <span data-ttu-id="7caff-147">**속성** 매개 변수를 지정 하지 않고 개체를 비교할 때 cmdlet은 개체가 동일한 것으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-147">When the objects are compared without specifying the **Property** parameter, the cmdlet considers the objects to be equal.</span></span> <span data-ttu-id="7caff-148">**InputObject** 값은 **ToString ()** 메서드의 결과와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-148">Notice that the value of the **InputObject** is the same as the result of the **ToString()** method.</span></span> <span data-ttu-id="7caff-149">**System.object** 클래스는 **IComparable** 인터페이스를 포함 하지 않으므로 cmdlet은 개체를 문자열로 변환 하 고 결과를 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-149">Since the **System.Diagnostics.Process** class does not have the **IComparable** interface, the cmdlet converts the objects to strings then compares the results.</span></span>

```powershell
PS> Get-Process pwsh

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    101   123.32     139.10      35.81   11168   1 pwsh
     89   107.55      66.97      11.44   17600   1 pwsh

PS> $a = Get-Process -Id 11168
PS> $b = Get-Process -Id 17600
PS> $a.ToString()
System.Diagnostics.Process (pwsh)
PS> $b.ToString()
System.Diagnostics.Process (pwsh)
PS> Compare-Object $a $b -IncludeEqual

InputObject                       SideIndicator
-----------                       -------------
System.Diagnostics.Process (pwsh) ==

PS> Compare-Object $a $b -Property ProcessName, Id, CPU

ProcessName    Id       CPU SideIndicator
-----------    --       --- -------------
pwsh        17600   11.4375 =>
pwsh        11168 36.203125 <=
```

<span data-ttu-id="7caff-150">비교할 속성을 지정 하는 경우 cmdlet에서 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-150">When you specify properties to be compared, the cmdlet shows the differences.</span></span>

### <span data-ttu-id="7caff-151">예 6-IComparable을 구현 하는 복잡 한 개체 비교</span><span class="sxs-lookup"><span data-stu-id="7caff-151">Example 6 - Comparing complex objects that implement IComparable</span></span>

<span data-ttu-id="7caff-152">개체가 **IComparable** 을 구현 하는 경우이 cmdlet은 개체를 비교 하는 방법을 검색 합니다. 개체가 다른 유형인 경우 **차이** 개체가 **referenceobject** 의 형식으로 변환 된 다음 비교 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-152">If the object implements **IComparable** , the cmdlet searches for ways to compare the objects.If the objects are different types, the **Difference** object is converted to the type of the **ReferenceObject** then compared.</span></span>

<span data-ttu-id="7caff-153">이 예제에서는 문자열을 **TimeSpan** 개체와 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-153">In this example, we are comparing a string to a **TimeSpan** object.</span></span> <span data-ttu-id="7caff-154">첫 번째 경우에는 문자열이 **TimeSpan** 으로 변환 되므로 개체가 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-154">In the first case, the string is converted to a **TimeSpan** so the objects are equal.</span></span>

```powershell
Compare-Object ([TimeSpan]"0:0:1") "0:0:1" -IncludeEqual
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    ==
```

```powershell
Compare-Object "0:0:1" ([TimeSpan]"0:0:1")
```

```Output
InputObject SideIndicator
----------- -------------
00:00:01    =>
0:0:1       <=
```

<span data-ttu-id="7caff-155">두 번째 경우에는 **TimeSpan** 이 문자열로 변환 되어 개체가 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-155">In the second case, the **TimeSpan** is converted to a string so the object are different.</span></span>

## <span data-ttu-id="7caff-156">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7caff-156">Parameters</span></span>

### <span data-ttu-id="7caff-157">-CaseSensitive</span><span class="sxs-lookup"><span data-stu-id="7caff-157">-CaseSensitive</span></span>

<span data-ttu-id="7caff-158">비교할 때 대/소문자를 구분해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-158">Indicates that comparisons should be case-sensitive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-159">-문화권</span><span class="sxs-lookup"><span data-stu-id="7caff-159">-Culture</span></span>

<span data-ttu-id="7caff-160">비교할 때 사용할 문화권을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-160">Specifies the culture to use for comparisons.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-161">-DifferenceObject</span><span class="sxs-lookup"><span data-stu-id="7caff-161">-DifferenceObject</span></span>

<span data-ttu-id="7caff-162">**참조** 개체와 비교할 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-162">Specifies the objects that are compared to the **reference** objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-163">-ExcludeDifferent</span><span class="sxs-lookup"><span data-stu-id="7caff-163">-ExcludeDifferent</span></span>

<span data-ttu-id="7caff-164">이 cmdlet이 같은 비교 개체의 특성만 표시 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-164">Indicates that this cmdlet displays only the characteristics of compared objects that are equal.</span></span> <span data-ttu-id="7caff-165">개체 간의 차이점은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-165">The differences between the objects are discarded.</span></span>

<span data-ttu-id="7caff-166">**Includeequal** 와 함께 **excludedifferent** 사용 하 여 **참조** 와 **차이점** 개체 사이에 일치 하는 선만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-166">Use **ExcludeDifferent** with **IncludeEqual** to display only the lines that match between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="7caff-167">**Includeequal** 없이 **excludedifferent** 가 지정 된 경우에는 출력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-167">If **ExcludeDifferent** is specified without **IncludeEqual** , there's no output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-168">-IncludeEqual</span><span class="sxs-lookup"><span data-stu-id="7caff-168">-IncludeEqual</span></span>

<span data-ttu-id="7caff-169">**Includeequal** 는 **참조** 와 **차이점** 개체 간의 일치 항목을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-169">**IncludeEqual** displays the matches between the **reference** and **difference** objects.</span></span>

<span data-ttu-id="7caff-170">기본적으로 출력에는 **참조** 와 **차이점** 개체 간의 차이점이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-170">By default, the output also includes the differences between the **reference** and **difference** objects.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-171">-PassThru</span><span class="sxs-lookup"><span data-stu-id="7caff-171">-PassThru</span></span>

<span data-ttu-id="7caff-172">**PassThru** 매개 변수를 사용 하는 경우는 `Compare-Object` 비교 된 개체 주위의 **PSCustomObject** 래퍼를 생략 하 고 다른 개체는 변경 되지 않은 상태로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-172">When you use the **PassThru** parameter, `Compare-Object` omits the **PSCustomObject** wrapper around the compared objects and returns the differing objects, unchanged.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-173">-속성</span><span class="sxs-lookup"><span data-stu-id="7caff-173">-Property</span></span>

<span data-ttu-id="7caff-174">비교할 **참조** 및 **차이점** 개체의 속성 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-174">Specifies an array of properties of the **reference** and **difference** objects to compare.</span></span>

<span data-ttu-id="7caff-175">**Property** 매개 변수 값은 새 계산 된 속성 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-175">The value of the **Property** parameter can be a new calculated property.</span></span> <span data-ttu-id="7caff-176">계산 된 속성은 스크립트 블록이 나 해시 테이블 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-176">The calculated property can be a script block or a hash table.</span></span> <span data-ttu-id="7caff-177">유효한 키-값 쌍은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-177">Valid key-value pairs are:</span></span>

- <span data-ttu-id="7caff-178">식 `<string>` 또는 `<script block>`</span><span class="sxs-lookup"><span data-stu-id="7caff-178">Expression - `<string>` or `<script block>`</span></span>

<span data-ttu-id="7caff-179">자세한 내용은 [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7caff-179">For more information, see [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-180">-ReferenceObject</span><span class="sxs-lookup"><span data-stu-id="7caff-180">-ReferenceObject</span></span>

<span data-ttu-id="7caff-181">비교를 위해 참조로 사용 되는 개체의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-181">Specifies an array of objects used as a reference for comparison.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-182">-SyncWindow</span><span class="sxs-lookup"><span data-stu-id="7caff-182">-SyncWindow</span></span>

<span data-ttu-id="7caff-183">`Compare-Object`개체의 컬렉션에서 일치 하는 항목을 찾는 동안 검사 하는 인접 개체의 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-183">Specifies the number of adjacent objects that `Compare-Object` inspects while looking for a match in a collection of objects.</span></span> <span data-ttu-id="7caff-184">`Compare-Object` 컬렉션의 동일한 위치에서 개체를 찾을 수 없는 경우 인접 개체를 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-184">`Compare-Object` examines adjacent objects when it doesn't find the object in the same position in a collection.</span></span> <span data-ttu-id="7caff-185">기본값은입니다 `[Int32]::MaxValue` . 즉, `Compare-Object` 전체 개체 컬렉션을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-185">The default value is `[Int32]::MaxValue`, which means that `Compare-Object` examines the entire object collection.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: [Int32]::MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7caff-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7caff-186">CommonParameters</span></span>

<span data-ttu-id="7caff-187">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7caff-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7caff-188">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7caff-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7caff-189">입력</span><span class="sxs-lookup"><span data-stu-id="7caff-189">Inputs</span></span>

### <span data-ttu-id="7caff-190">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="7caff-190">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="7caff-191">파이프라인에서 **DifferenceObject** 매개 변수로 개체를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-191">You can send an object down the pipeline to the **DifferenceObject** parameter.</span></span>

## <span data-ttu-id="7caff-192">outputs</span><span class="sxs-lookup"><span data-stu-id="7caff-192">Outputs</span></span>

### <span data-ttu-id="7caff-193">없음</span><span class="sxs-lookup"><span data-stu-id="7caff-193">None</span></span>

<span data-ttu-id="7caff-194">**참조** 개체와 **차이점** 개체가 같으면 **includeequal** 매개 변수를 사용 하지 않는 한 출력이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-194">If the **reference** object and the **difference** object are the same, there's no output, unless you use the **IncludeEqual** parameter.</span></span>

### <span data-ttu-id="7caff-195">PSCustomObject.</span><span class="sxs-lookup"><span data-stu-id="7caff-195">System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="7caff-196">개체가 다른 경우는 차이점을 `Compare-Object` `PSCustomObject` 참조 하기 위해 함께 사용 **표시기** 속성을 사용 하 여 다른 개체를 래퍼로 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-196">If the objects are different, `Compare-Object` wraps the differing objects in a `PSCustomObject` wrapper with a **SideIndicator** property to reference the differences.</span></span>

<span data-ttu-id="7caff-197">**PassThru** 매개 변수를 사용 하는 경우 개체의 **형식은** 변경 되지 않지만 반환 되는 개체의 인스턴스에는 ' 이름 ' 이라는 추가 된 **참고 속성이** **있습니다.**</span><span class="sxs-lookup"><span data-stu-id="7caff-197">When you use the **PassThru** parameter, the **Type** of the object is not changed but the instance of the object returned has an added **NoteProperty** named **SideIndicator**.</span></span> <span data-ttu-id="7caff-198">나란히 **표시기** 는 출력이 속한 입력 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-198">**SideIndicator** shows which input object the output belongs to.</span></span>

## <span data-ttu-id="7caff-199">메모</span><span class="sxs-lookup"><span data-stu-id="7caff-199">Notes</span></span>

<span data-ttu-id="7caff-200">**PassThru** 매개 변수를 사용 하는 경우 콘솔에 표시 되는 출력에는 외부 **표시기** 속성이 포함 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-200">When using the **PassThru** parameter, the output displayed in the console may not include the **SideIndicator** property.</span></span> <span data-ttu-id="7caff-201">에서 출력 하는 개체 형식에 대 한의 기본 형식 뷰에는 외부 `Compare-Object` **표시기** 속성이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7caff-201">The default format view of the for the object type output by `Compare-Object` does not include the **SideIndicator** property.</span></span> <span data-ttu-id="7caff-202">자세한 내용은이 문서의 [예제 3](#ex3) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7caff-202">For more information see [Example 3](#ex3) in this article.</span></span>

## <span data-ttu-id="7caff-203">관련 링크</span><span class="sxs-lookup"><span data-stu-id="7caff-203">Related links</span></span>

[<span data-ttu-id="7caff-204">about_Calculated_Properties</span><span class="sxs-lookup"><span data-stu-id="7caff-204">about_Calculated_Properties</span></span>](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[<span data-ttu-id="7caff-205">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-205">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="7caff-206">Group-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-206">Group-Object</span></span>](Group-Object.md)

[<span data-ttu-id="7caff-207">Measure-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-207">Measure-Object</span></span>](Measure-Object.md)

[<span data-ttu-id="7caff-208">New-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-208">New-Object</span></span>](New-Object.md)

[<span data-ttu-id="7caff-209">Select-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-209">Select-Object</span></span>](Select-Object.md)

[<span data-ttu-id="7caff-210">Sort-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-210">Sort-Object</span></span>](Sort-Object.md)

[<span data-ttu-id="7caff-211">Tee-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-211">Tee-Object</span></span>](Tee-Object.md)

[<span data-ttu-id="7caff-212">Where-Object</span><span class="sxs-lookup"><span data-stu-id="7caff-212">Where-Object</span></span>](../Microsoft.PowerShell.Core/Where-Object.md)

[<span data-ttu-id="7caff-213">Get-Process</span><span class="sxs-lookup"><span data-stu-id="7caff-213">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)
