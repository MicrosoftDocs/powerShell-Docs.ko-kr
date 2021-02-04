---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-string?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-String
ms.openlocfilehash: c0a9557c0139af5abbe24fade07c0d018c6bffc0
ms.sourcegitcommit: 94d597c4fb38793bc49ca7610e2c9973b1e577c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98620033"
---
# <span data-ttu-id="18496-103">Out-String</span><span class="sxs-lookup"><span data-stu-id="18496-103">Out-String</span></span>

## <span data-ttu-id="18496-104">개요</span><span class="sxs-lookup"><span data-stu-id="18496-104">Synopsis</span></span>
<span data-ttu-id="18496-105">입력 개체를 문자열로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-105">Outputs input objects as a strings.</span></span>

## <span data-ttu-id="18496-106">구문</span><span class="sxs-lookup"><span data-stu-id="18496-106">Syntax</span></span>

### <span data-ttu-id="18496-107">모두</span><span class="sxs-lookup"><span data-stu-id="18496-107">All</span></span>

```
Out-String [-Stream] [-Width <Int32>] [-InputObject <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="18496-108">Description</span><span class="sxs-lookup"><span data-stu-id="18496-108">Description</span></span>

<span data-ttu-id="18496-109">`Out-String`Cmdlet은 입력 개체를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-109">The `Out-String` cmdlet converts input objects into strings.</span></span> <span data-ttu-id="18496-110">기본적으로는 `Out-String` 문자열을 누적 하 고이를 단일 문자열로 반환 하지만 **Stream** 매개 변수를 사용 하 여 한 `Out-String` 번에 한 줄씩 반환 하거나 문자열을 만들어 배열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18496-110">By default, `Out-String` accumulates the strings and returns them as a single string, but you can use the **Stream** parameter to direct `Out-String` to return one line at a time or create and array of strings.</span></span> <span data-ttu-id="18496-111">이 cmdlet을 사용하면 개체를 편하게 조작할 수 없을 경우 기존 셸과 동일한 방식으로 문자열 출력을 검색하고 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18496-111">This cmdlet lets you search and manipulate string output as you would in traditional shells when object manipulation is less convenient.</span></span>

## <span data-ttu-id="18496-112">예제</span><span class="sxs-lookup"><span data-stu-id="18496-112">Examples</span></span>

### <span data-ttu-id="18496-113">예 1: 현재 문화권을 가져오고 데이터를 문자열로 변환</span><span class="sxs-lookup"><span data-stu-id="18496-113">Example 1: Get the current culture and convert the data to strings</span></span>

<span data-ttu-id="18496-114">이 예에서는 현재 사용자의 국가별 설정을 가져오고 개체 데이터를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-114">This example gets the regional settings for the current user and converts the object data to strings.</span></span>

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

<span data-ttu-id="18496-115">`$C`변수는 **Selected.System를 저장 합니다. 세계화. CultureInfo** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="18496-115">The `$C` variable stores a **Selected.System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="18496-116">개체는 `Get-Culture` 출력을 파이프라인에서로 보낸 결과입니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="18496-116">The object is the result of `Get-Culture` sending output down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="18496-117">**Property** 매개 변수는 별표 ( `*` ) 와일드 카드를 사용 하 여 개체에 포함 된 모든 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-117">The **Property** parameter uses an asterisk (`*`) wildcard to specify all properties are contained in the object.</span></span>

<span data-ttu-id="18496-118">`Out-String`**InputObject** 매개 변수를 사용 하 여 변수에 저장 된 **CultureInfo** 개체를 지정 합니다 `$C` .</span><span class="sxs-lookup"><span data-stu-id="18496-118">`Out-String` uses the **InputObject** parameter to specify the **CultureInfo** object stored in the `$C` variable.</span></span> <span data-ttu-id="18496-119">의 개체는 `$C` 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18496-119">The objects in `$C` are converted to a string.</span></span>

> [!NOTE]
> <span data-ttu-id="18496-120">`Out-String`배열을 보려면 출력을 변수에 저장 하 고 배열 인덱스를 사용 하 여 요소를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-120">To view the `Out-String` array, store the output to a variable and use an array index to view the elements.</span></span> <span data-ttu-id="18496-121">배열 인덱스에 대 한 자세한 내용은 [about_Arrays](../microsoft.powershell.core/about/about_arrays.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="18496-121">For more information about the array index, see [about_Arrays](../microsoft.powershell.core/about/about_arrays.md).</span></span>
>
> `$str = Out-String -InputObject $C -Width 100`

### <span data-ttu-id="18496-122">예제 2: 개체 작업</span><span class="sxs-lookup"><span data-stu-id="18496-122">Example 2: Working with objects</span></span>

<span data-ttu-id="18496-123">이 예제에서는 개체 작업과 문자열 작업 간의 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="18496-123">This example demonstrates the difference between working with objects and working with strings.</span></span> <span data-ttu-id="18496-124">명령은 **gcm** 텍스트,에 대 한 별칭을 포함 하는 별칭을 표시 합니다 `Get-Command` .</span><span class="sxs-lookup"><span data-stu-id="18496-124">The command displays an alias that includes the text **gcm**, the alias for `Get-Command`.</span></span>

```powershell
Get-Alias | Out-String -Stream | Select-String -Pattern "gcm"
```

```Output
Alias           gcm -> Get-Command
```

<span data-ttu-id="18496-125">`Get-Alias` 각 별칭에 대해 하나씩 **system.management.automation.aliasinfo** 개체를 가져오고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="18496-125">`Get-Alias` gets the **System.Management.Automation.AliasInfo** objects, one for each alias, and sends the objects down the pipeline.</span></span> <span data-ttu-id="18496-126">`Out-String`**Stream** 매개 변수를 사용 하 여 모든 개체를 단일 문자열로 연결 하는 대신 각 개체를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-126">`Out-String` uses the **Stream** parameter to convert each object to a string rather concatenating all the objects into a single string.</span></span> <span data-ttu-id="18496-127">**System.string** 개체는 파이프라인으로 전송 되 고 `Select-String` **Pattern** 매개 변수를 사용 하 여 **gcm** 텍스트와 일치 하는 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="18496-127">The **System.String** objects are sent down the pipeline and `Select-String` uses the **Pattern** parameter to find matches for the text **gcm**.</span></span>

> [!NOTE]
> <span data-ttu-id="18496-128">**Stream** 매개 변수를 생략 하면에서 `Select-String` 반환 하는 단일 문자열에서 **gcm** 텍스트를 찾기 때문에 명령은 모든 별칭을 표시 합니다 `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="18496-128">If you omit the **Stream** parameter, the command displays all the aliases because `Select-String` finds the text **gcm** in the single string that `Out-String` returns.</span></span>

### <span data-ttu-id="18496-129">예 3: Width 매개 변수를 사용 하 여 잘림 방지</span><span class="sxs-lookup"><span data-stu-id="18496-129">Example 3: Use the Width parameter to prevent truncation.</span></span>

<span data-ttu-id="18496-130">의 출력 대부분 `Out-String` 은 다음 줄로 래핑되어,에 전달 되기 전에 형식 지정 시스템에 의해 출력이 잘리는 시나리오는 있습니다 `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="18496-130">While most output from `Out-String` is wrapped to the next line, there are scenarios where the output is truncated by the formatting system before being passed to `Out-String`.</span></span> <span data-ttu-id="18496-131">**Width** 매개 변수를 사용 하 여 잘림을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18496-131">You can avoid truncation using the **Width** parameter.</span></span>

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

## <span data-ttu-id="18496-132">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="18496-132">PARAMETERS</span></span>

### <span data-ttu-id="18496-133">-InputObject</span><span class="sxs-lookup"><span data-stu-id="18496-133">-InputObject</span></span>

<span data-ttu-id="18496-134">문자열에 기록할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-134">Specifies the objects to be written to a string.</span></span> <span data-ttu-id="18496-135">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="18496-135">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="18496-136">-스트림</span><span class="sxs-lookup"><span data-stu-id="18496-136">-Stream</span></span>

<span data-ttu-id="18496-137">기본적으로는 `Out-String` 빈 머리글이 나 후행 줄바꿈를 포함 하 여 콘솔에서 볼 수 있는 것 처럼 형식이 지정 된 단일 문자열을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-137">By default, `Out-String` outputs a single string formatted as you would see it in the console including any blank headers or trailing newlines.</span></span> <span data-ttu-id="18496-138">**Stream** 매개 변수는 `Out-String` 를 사용 하 여 각 줄을 하나씩 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-138">The **Stream** parameter enables `Out-String` to output each line one by one.</span></span> <span data-ttu-id="18496-139">이에 대 한 유일한 예외는 여러 줄 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="18496-139">The only exception to this are multiline strings.</span></span> <span data-ttu-id="18496-140">이 경우는 `Out-String` 계속 해 서 문자열을 한 줄로 된 단일 문자열로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-140">In that case, `Out-String` will still output the string as a single, multiline string.</span></span>

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

### <span data-ttu-id="18496-141">-너비</span><span class="sxs-lookup"><span data-stu-id="18496-141">-Width</span></span>

<span data-ttu-id="18496-142">출력의 각 줄에 포함되는 문자 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-142">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="18496-143">추가 문자는 사용 된 포맷터 cmdlet에 따라 다음 줄로 래핑되어 잘립니다.</span><span class="sxs-lookup"><span data-stu-id="18496-143">Any additional characters are wrapped to the next line or truncated depending on the formatter cmdlet used.</span></span> <span data-ttu-id="18496-144">**Width** 매개 변수는 형식이 지정 된 개체에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18496-144">The **Width** parameter applies only to objects that are being formatted.</span></span> <span data-ttu-id="18496-145">이 매개 변수를 생략할 경우 호스트 프로그램의 특성에 따라 너비가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="18496-145">If you omit this parameter, the width is determined by the characteristics of the host program.</span></span> <span data-ttu-id="18496-146">터미널 (콘솔) 창에서 현재 창 너비가 기본값으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18496-146">In terminal (console) windows, the current window width is used as the default value.</span></span> <span data-ttu-id="18496-147">PowerShell 콘솔 windows의 기본값은 설치 시 80 자입니다.</span><span class="sxs-lookup"><span data-stu-id="18496-147">PowerShell console windows default to a width of 80 characters on installation.</span></span>

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

### <span data-ttu-id="18496-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="18496-148">CommonParameters</span></span>

<span data-ttu-id="18496-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="18496-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="18496-150">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18496-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="18496-151">입력</span><span class="sxs-lookup"><span data-stu-id="18496-151">INPUTS</span></span>

### <span data-ttu-id="18496-152">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="18496-152">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="18496-153">파이프라인에서로 개체를 보낼 수 있습니다 `Out-String` .</span><span class="sxs-lookup"><span data-stu-id="18496-153">You can send objects down the pipeline to `Out-String`.</span></span>

## <span data-ttu-id="18496-154">출력</span><span class="sxs-lookup"><span data-stu-id="18496-154">OUTPUTS</span></span>

### <span data-ttu-id="18496-155">System.String</span><span class="sxs-lookup"><span data-stu-id="18496-155">System.String</span></span>

<span data-ttu-id="18496-156">`Out-String` 입력 개체에서 만든 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="18496-156">`Out-String` returns the string that it creates from the input object.</span></span>

## <span data-ttu-id="18496-157">참고</span><span class="sxs-lookup"><span data-stu-id="18496-157">NOTES</span></span>

<span data-ttu-id="18496-158">동사를 포함 하는 cmdlet은 `Out` 개체의 형식을 지정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="18496-158">The cmdlets that contain the `Out` verb don't format objects.</span></span> <span data-ttu-id="18496-159">`Out`Cmdlet은 지정 된 표시 대상에 대 한 포맷터에 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="18496-159">The `Out` cmdlets send objects to the formatter for the specified display destination.</span></span>

## <span data-ttu-id="18496-160">관련 링크</span><span class="sxs-lookup"><span data-stu-id="18496-160">RELATED LINKS</span></span>

[<span data-ttu-id="18496-161">about_Formatting</span><span class="sxs-lookup"><span data-stu-id="18496-161">about_Formatting</span></span>](../Microsoft.PowerShell.Core/About/about_Format.ps1xml.md)

[<span data-ttu-id="18496-162">Out-Default</span><span class="sxs-lookup"><span data-stu-id="18496-162">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="18496-163">Out-File</span><span class="sxs-lookup"><span data-stu-id="18496-163">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="18496-164">Out-Host</span><span class="sxs-lookup"><span data-stu-id="18496-164">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="18496-165">Out-Null</span><span class="sxs-lookup"><span data-stu-id="18496-165">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="18496-166">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="18496-166">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="18496-167">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="18496-167">Out-Printer</span></span>](Out-Printer.md)
