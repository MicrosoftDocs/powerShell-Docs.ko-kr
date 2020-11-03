---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 1/7/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 7d399661e4514c0a39ad00601d554c41c2897ff9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214137"
---
# <span data-ttu-id="8c996-103">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="8c996-103">ConvertTo-Csv</span></span>

## <span data-ttu-id="8c996-104">개요</span><span class="sxs-lookup"><span data-stu-id="8c996-104">SYNOPSIS</span></span>
<span data-ttu-id="8c996-105">.NET 개체를 일련의 CSV (쉼표로 구분 된 값) 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-105">Converts .NET objects into a series of comma-separated value (CSV) strings.</span></span>

## <span data-ttu-id="8c996-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c996-106">SYNTAX</span></span>

### <span data-ttu-id="8c996-107">구분 기호 (기본값)</span><span class="sxs-lookup"><span data-stu-id="8c996-107">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [[-Delimiter] <char>] [-NoTypeInformation]
 [<CommonParameters>]
```

### <span data-ttu-id="8c996-108">UseCulture</span><span class="sxs-lookup"><span data-stu-id="8c996-108">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <psobject> [-UseCulture] [-NoTypeInformation] [<CommonParameters>]
```

## <span data-ttu-id="8c996-109">설명</span><span class="sxs-lookup"><span data-stu-id="8c996-109">DESCRIPTION</span></span>

<span data-ttu-id="8c996-110">`ConvertTo-CSV`Cmdlet은 제출한 개체를 나타내는 일련의 CSV (쉼표로 구분 된 값) 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-110">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="8c996-111">그런 다음 cmdlet을 사용 `ConvertFrom-Csv` 하 여 CSV 문자열에서 개체를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-111">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="8c996-112">CSV에서 변환 된 개체는 속성 값을 포함 하 고 메서드를 포함 하지 않는 원래 개체의 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-112">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="8c996-113">Cmdlet을 사용 `Export-Csv` 하 여 개체를 CSV 문자열로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-113">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="8c996-114">`Export-CSV` 은 `ConvertTo-CSV` CSV 문자열을 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-114">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="8c996-115">Cmdlet에는 `ConvertTo-CSV` 쉼표 이외의 구분 기호를 지정 하거나 현재 문화권을 구분 기호로 사용 하는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-115">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="8c996-116">예제</span><span class="sxs-lookup"><span data-stu-id="8c996-116">EXAMPLES</span></span>

### <span data-ttu-id="8c996-117">예제 1: 개체를 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="8c996-117">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="8c996-118">이 예에서는 **프로세스** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-118">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name 'PowerShell' | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Company","CPU","FileVersion", ...
"powershell","11","691","2204036739072","175943680","132665344","33312", ...
```

<span data-ttu-id="8c996-119">`Get-Process`Cmdlet은 **프로세스** 개체를 가져오고 **Name** 매개 변수를 사용 하 여 PowerShell 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-119">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="8c996-120">Process 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="8c996-120">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="8c996-121">`ConvertTo-CSV`Cmdlet은 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-121">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="8c996-122">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** 정보 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-122">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="8c996-123">예제 2: DateTime 개체를 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="8c996-123">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="8c996-124">이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-124">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="8c996-125">`Get-Date`Cmdlet은 **DateTime** 개체를 가져와서 변수에 저장 합니다 `$Date` .</span><span class="sxs-lookup"><span data-stu-id="8c996-125">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="8c996-126">`ConvertTo-Csv`Cmdlet은 **DateTime** 개체를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-126">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="8c996-127">**InputObject** 매개 변수는 변수에 저장 된 **DateTime** 개체를 사용 합니다 `$Date` .</span><span class="sxs-lookup"><span data-stu-id="8c996-127">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="8c996-128">**Delimiter** 매개 변수는 문자열 값을 구분 하기 위해 세미콜론을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-128">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="8c996-129">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** 정보 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-129">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

### <span data-ttu-id="8c996-130">예 3: PowerShell 이벤트 로그를 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="8c996-130">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="8c996-131">이 예에서는 PowerShell에 대 한 Windows 이벤트 로그를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-131">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'Windows PowerShell' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error","403",,"0","4","4",,"36028797018963968","46891","PowerShell", ...
```

<span data-ttu-id="8c996-132">이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 고 현재 문화권의 기본 목록 구분 기호를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-132">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="8c996-133">`Get-WinEvent`Cmdlet은 이벤트 로그 개체를 가져오고 **LogName** 매개 변수를 사용 하 여 로그 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-133">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="8c996-134">이벤트 로그 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="8c996-134">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="8c996-135">`ConvertTo-Csv`Cmdlet은 이벤트 로그 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-135">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="8c996-136">**UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-136">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="8c996-137">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** 정보 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-137">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output.</span></span>

## <span data-ttu-id="8c996-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="8c996-138">PARAMETERS</span></span>

### <span data-ttu-id="8c996-139">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="8c996-139">-Delimiter</span></span>

<span data-ttu-id="8c996-140">CSV 문자열의 속성 값을 구분 하는 구분 기호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-140">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="8c996-141">기본값은 쉼표 ()입니다 `,` .</span><span class="sxs-lookup"><span data-stu-id="8c996-141">The default is a comma (`,`).</span></span> <span data-ttu-id="8c996-142">콜론 ()과 같은 문자를 입력 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-142">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="8c996-143">세미콜론 ()을 지정 하려면 작은따옴표로 `;` 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-143">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

```yaml
Type: System.Char
Parameter Sets: Delimiter
Aliases:

Required: False
Position: 1
Default value: comma (,)
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c996-144">-InputObject</span><span class="sxs-lookup"><span data-stu-id="8c996-144">-InputObject</span></span>

<span data-ttu-id="8c996-145">CSV 문자열로 변환 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-145">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="8c996-146">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="8c996-146">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="8c996-147">개체를로 파이프 할 수도 있습니다 `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="8c996-147">You can also pipe objects to `ConvertTo-CSV`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="8c996-148">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="8c996-148">-NoTypeInformation</span></span>

<span data-ttu-id="8c996-149">출력에서 **#TYPE** 정보 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-149">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="8c996-150">이 매개 변수는 PowerShell 6.0의 기본값이 며 이전 버전과의 호환성을 위해 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-150">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NTI

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c996-151">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="8c996-151">-UseCulture</span></span>

<span data-ttu-id="8c996-152">현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-152">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="8c996-153">문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`</span><span class="sxs-lookup"><span data-stu-id="8c996-153">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: UseCulture
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8c996-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c996-154">CommonParameters</span></span>

<span data-ttu-id="8c996-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c996-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c996-156">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8c996-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c996-157">입력</span><span class="sxs-lookup"><span data-stu-id="8c996-157">INPUTS</span></span>

### <span data-ttu-id="8c996-158">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="8c996-158">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="8c996-159">Any (확장 형식 시스템) 어댑터가 있는 개체를로 파이프 할 수 있습니다 `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="8c996-159">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="8c996-160">출력</span><span class="sxs-lookup"><span data-stu-id="8c996-160">OUTPUTS</span></span>

### <span data-ttu-id="8c996-161">System.String</span><span class="sxs-lookup"><span data-stu-id="8c996-161">System.String</span></span>

<span data-ttu-id="8c996-162">CSV 출력은 문자열 컬렉션으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-162">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="8c996-163">참고</span><span class="sxs-lookup"><span data-stu-id="8c996-163">NOTES</span></span>

<span data-ttu-id="8c996-164">CSV 형식에서 각 개체는 해당 속성 값의 쉼표로 구분된 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-164">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="8c996-165">속성 값은 개체의 **ToString ()** 메서드를 사용 하 여 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-165">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="8c996-166">문자열은 속성 값 이름으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-166">The strings are represented by the property value name.</span></span> <span data-ttu-id="8c996-167">`ConvertTo-CSV` 개체의 메서드를 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-167">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="8c996-168">CSV 문자열은 다음과 같이 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-168">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="8c996-169">기본적으로 첫 번째 문자열에는 **#TYPE** 정보 헤더와 개체 형식의 정규화 된 이름이 차례로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-169">By default the first string contains the **#TYPE** information header followed by the object type's fully qualified name.</span></span> <span data-ttu-id="8c996-170">예를 들어, **#TYPE를 처리** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-170">For example, **#TYPE System.Diagnostics.Process** .</span></span>
- <span data-ttu-id="8c996-171">**Notypeinformation** 이 사용 되는 경우 첫 번째 문자열에는 열 머리글이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-171">If **NoTypeInformation** is used the first string includes the column headers.</span></span> <span data-ttu-id="8c996-172">헤더는 첫 번째 개체의 속성 이름을 쉼표로 구분 된 목록으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-172">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="8c996-173">나머지 문자열은 각 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-173">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="8c996-174">에 여러 개체를 제출 하는 경우는 `ConvertTo-CSV` `ConvertTo-CSV` 제출한 첫 번째 개체의 속성을 기반으로 문자열을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-174">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="8c996-175">나머지 개체에 지정 된 속성 중 하나가 없는 경우 해당 개체의 속성 값은 Null 이며, 두 개의 연속 된 쉼표로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-175">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="8c996-176">나머지 개체에 추가 속성이 있으면 해당 속성 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8c996-176">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="8c996-177">관련 링크</span><span class="sxs-lookup"><span data-stu-id="8c996-177">RELATED LINKS</span></span>

[<span data-ttu-id="8c996-178">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="8c996-178">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="8c996-179">Export-Csv</span><span class="sxs-lookup"><span data-stu-id="8c996-179">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="8c996-180">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="8c996-180">Import-Csv</span></span>](Import-Csv.md)
