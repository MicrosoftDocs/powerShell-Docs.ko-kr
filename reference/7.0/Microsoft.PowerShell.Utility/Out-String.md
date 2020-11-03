---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/29/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: a64b11206a0755cedabad2894ecc330fac95a8d5
ms.sourcegitcommit: c8d1ffeab215e74e87ea1b0af8cd606c1a6a80ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "93220137"
---
# <span data-ttu-id="2b1ab-103">Out-String</span><span class="sxs-lookup"><span data-stu-id="2b1ab-103">Out-String</span></span>

## <span data-ttu-id="2b1ab-104">개요</span><span class="sxs-lookup"><span data-stu-id="2b1ab-104">SYNOPSIS</span></span>
<span data-ttu-id="2b1ab-105">입력 개체를 문자열로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-105">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="2b1ab-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2b1ab-106">SYNTAX</span></span>

### <span data-ttu-id="2b1ab-107">NoNewLineFormatting 지정 (기본값)</span><span class="sxs-lookup"><span data-stu-id="2b1ab-107">NoNewLineFormatting (Default)</span></span>

```
Out-String [-Width <Int32>] [-NoNewline] [-InputObject <PSObject>] [<CommonParameters>]
```

### <span data-ttu-id="2b1ab-108">StreamFormatting 지정</span><span class="sxs-lookup"><span data-stu-id="2b1ab-108">StreamFormatting</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="2b1ab-109">설명</span><span class="sxs-lookup"><span data-stu-id="2b1ab-109">DESCRIPTION</span></span>

<span data-ttu-id="2b1ab-110">`Out-String`Cmdlet은 입력 개체를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-110">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="2b1ab-111">기본적으로는 `Out-String` 문자열을 누적 하 고이를 단일 문자열로 반환 하지만 **Stream** 매개 변수를 사용 하 여 한 `Out-String` 번에 한 줄씩 반환 하거나 문자열을 만들어 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-111">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="2b1ab-112">이 cmdlet을 사용하면 개체를 편하게 조작할 수 없을 경우 기존 셸과 동일한 방식으로 문자열 출력을 검색하고 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-112">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="2b1ab-113">예제</span><span class="sxs-lookup"><span data-stu-id="2b1ab-113">EXAMPLES</span></span>

### <span data-ttu-id="2b1ab-114">예 1: 현재 문화권을 가져오고 데이터를 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="2b1ab-114">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="2b1ab-115">이 예에서는 현재 사용자의 국가별 설정을 가져오고 개체 데이터를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-115">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

```powershell
$C = Get-Culture | Select-Object -Property *
Out-String -InputObject $C -Width 100
```

```Output
Parent                         : en
LCID                           : 1033
KeyboardLayoutId               : 1033
Name                           : en-US
IetfLanguageTag                : en-US
DisplayName                    : English (United States)
NativeName                     : English (United States)
EnglishName                    : English (United States)
TwoLetterISOLanguageName       : en
ThreeLetterISOLanguageName     : eng
ThreeLetterWindowsLanguageName : ENU
CompareInfo                    : CompareInfo - en-US
TextInfo                       : TextInfo - en-US
IsNeutralCulture               : False
CultureTypes                   : SpecificCultures, InstalledWin32Cultures, FrameworkCultures
NumberFormat                   : System.Globalization.NumberFormatInfo
DateTimeFormat                 : System.Globalization.DateTimeFormatInfo
Calendar                       : System.Globalization.GregorianCalendar
OptionalCalendars              : {System.Globalization.GregorianCalendar,
                                 System.Globalization.GregorianCalendar}
UseUserOverride                : True
IsReadOnly                     : False
```

<span data-ttu-id="2b1ab-116">`$C`변수는 **Selected.System를 저장 합니다. 세계화. CultureInfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-116">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="2b1ab-117">개체는 `Get-Culture` 출력을 파이프라인에서로 보낸 결과입니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="2b1ab-117">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="2b1ab-118">**Property** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 개체에 포함 된 모든 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-118">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="2b1ab-119">`Out-String`**InputObject** 매개 변수를 사용 하 여 변수에 저장 된 **CultureInfo** 개체를 지정 합니다 `$C` .</span><span class="sxs-lookup"><span data-stu-id="2b1ab-119">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="2b1ab-120">의 개체는 `$C` 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-120">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="2b1ab-121">`Out-String`배열을 보려면 출력을 변수에 저장 하 고 배열 인덱스를 사용 하 여 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-121">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="2b1ab-122">배열 인덱스에 대 한 자세한 내용은 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-122">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="2b1ab-123">예제 2: 개체 작업</span><span class="sxs-lookup"><span data-stu-id="2b1ab-123">Example 2: Working with objects</span></span>

<span data-ttu-id="2b1ab-124">이 예제에서는 개체 작업과 문자열 작업 간의 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-124">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="2b1ab-125">명령은 **gcm** 텍스트,에 대 한 별칭을 포함 하는 별칭을 표시 합니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="2b1ab-125">The command displays an alias that includes the text **gcm** , the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="2b1ab-126">`Get-Alias` 각 별칭에 대해 하나씩 **system.management.automation.aliasinfo** 개체를 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-126">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="2b1ab-127">`Out-String`**Stream** 매개 변수를 사용 하 여 모든 개체를 단일 문자열로 연결 하는 대신 각 개체를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-127">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="2b1ab-128">**System.string** 개체는 파이프라인으로 전송 되 고 `Select-String` **Pattern** 매개 변수를 사용 하 여 **gcm** 텍스트와 일치 하는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-128">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm**.</span></span>

> [!NOTE]
> <span data-ttu-id="2b1ab-129">**Stream** 매개 변수를 생략 하면에서 `Select-String` 반환 하는 단일 문자열에서 **gcm** 텍스트를 찾기 때문에 명령은 모든 별칭을 표시 합니다 `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="2b1ab-129">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="2b1ab-130">예 3: Width 매개 변수를 사용 하 여 잘림 방지</span><span class="sxs-lookup"><span data-stu-id="2b1ab-130">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="2b1ab-131">의 출력 대부분 `Out-String` 은 다음 줄로 래핑되어,에 전달 되기 전에 형식 지정 시스템에 의해 출력이 잘리는 시나리오는 있습니다 `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="2b1ab-131">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="2b1ab-132">**Width** 매개 변수를 사용 하 여 잘림을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-132">You can avoid truncation using the **Width** parameter.</span></span>

```powershell
PS> @{TestKey = ('x' * 200)} | Out-String
Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx...

PS> @{TestKey = ('x' * 200)} | Out-String -Width 250

Name                           Value
----                           -----
TestKey                        xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

## <span data-ttu-id="2b1ab-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2b1ab-133">PARAMETERS</span></span>

### <span data-ttu-id="2b1ab-134">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2b1ab-134">-InputObject</span></span>

<span data-ttu-id="2b1ab-135">문자열에 기록할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-135">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="2b1ab-136">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-136">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="2b1ab-137">-NoNewline</span><span class="sxs-lookup"><span data-stu-id="2b1ab-137">-NoNewline</span></span>

<span data-ttu-id="2b1ab-138">PowerShell 포맷터에 의해 생성 된 출력에서 모든 줄바꿈를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-138">Removes all newlines from output generated by the PowerShell formatter.</span></span> <span data-ttu-id="2b1ab-139">문자열 개체의 일부인 줄바꿈은 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-139">Newlines that are part of the string objects are preserved.</span></span>

<span data-ttu-id="2b1ab-140">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-140">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NoNewLineFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b1ab-141">-스트림</span><span class="sxs-lookup"><span data-stu-id="2b1ab-141">-Stream</span></span>

<span data-ttu-id="2b1ab-142">Cmdlet이 입력 개체의 각 줄에 대해 별도의 문자열을 보내는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-142">Indicates that the cmdlet sends a separate string for each line of an input object.</span></span> <span data-ttu-id="2b1ab-143">기본적으로 각 개체의 문자열은 누적되어 하나의 문자열로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-143">By default, the strings for each object are accumulated and sent as a single string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StreamFormatting
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b1ab-144">-너비</span><span class="sxs-lookup"><span data-stu-id="2b1ab-144">-Width</span></span>

<span data-ttu-id="2b1ab-145">출력의 각 줄에 포함되는 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-145">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="2b1ab-146">추가 문자는 사용 된 포맷터 cmdlet에 따라 다음 줄로 래핑되어 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-146">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="2b1ab-147">**Width** 매개 변수는 형식이 지정 된 개체에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-147">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="2b1ab-148">이 매개 변수를 생략할 경우 호스트 프로그램의 특성에 따라 너비가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-148">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="2b1ab-149">터미널 (콘솔) 창에서 현재 창 너비가 기본값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-149">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="2b1ab-150">PowerShell 콘솔 windows의 기본값은 설치 시 80 자입니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-150">PowerShell console windows default to a width of 80 characters on installation.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2b1ab-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2b1ab-151">CommonParameters</span></span>

<span data-ttu-id="2b1ab-152">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2b1ab-153">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2b1ab-154">입력</span><span class="sxs-lookup"><span data-stu-id="2b1ab-154">INPUTS</span></span>

### <span data-ttu-id="2b1ab-155">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="2b1ab-155">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="2b1ab-156">파이프라인에서로 개체를 보낼 수 있습니다 `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="2b1ab-156">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="2b1ab-157">출력</span><span class="sxs-lookup"><span data-stu-id="2b1ab-157">OUTPUTS</span></span>

### <span data-ttu-id="2b1ab-158">System.String</span><span class="sxs-lookup"><span data-stu-id="2b1ab-158">System.String</span></span>

<span data-ttu-id="2b1ab-159">`Out-String` 입력 개체에서 만든 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-159">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="2b1ab-160">참고</span><span class="sxs-lookup"><span data-stu-id="2b1ab-160">NOTES</span></span>

<span data-ttu-id="2b1ab-161">동사를 포함 하는 cmdlet은 `Out` 개체의 형식을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-161">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="2b1ab-162">`Out`Cmdlet은 지정 된 표시 대상에 대 한 포맷터에 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="2b1ab-162">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="2b1ab-163">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2b1ab-163">RELATED LINKS</span></span>

[<span data-ttu-id="2b1ab-164">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="2b1ab-164">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="2b1ab-165">Out-Default</span><span class="sxs-lookup"><span data-stu-id="2b1ab-165">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="2b1ab-166">Out-File</span><span class="sxs-lookup"><span data-stu-id="2b1ab-166">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="2b1ab-167">Out-Host</span><span class="sxs-lookup"><span data-stu-id="2b1ab-167">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="2b1ab-168">Out-Null</span><span class="sxs-lookup"><span data-stu-id="2b1ab-168">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="2b1ab-169">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="2b1ab-169">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="2b1ab-170">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="2b1ab-170">Out-Printer</span></span>](Out-Printer.md)
