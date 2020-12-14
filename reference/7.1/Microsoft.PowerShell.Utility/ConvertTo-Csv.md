---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-csv?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Csv
ms.openlocfilehash: 7ad8dc837bd843c2df48587ad809d9f65a4cf8a7
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913222"
---
# <span data-ttu-id="1148d-102">ConvertTo-Csv</span><span class="sxs-lookup"><span data-stu-id="1148d-102">ConvertTo-Csv</span></span>

## <span data-ttu-id="1148d-103">개요</span><span class="sxs-lookup"><span data-stu-id="1148d-103">SYNOPSIS</span></span>
<span data-ttu-id="1148d-104">.NET 개체를 일련의 CSV (쉼표로 구분 된 값) 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-104">Converts .NET objects into a series of character-separated value (CSV) strings.</span></span>

## <span data-ttu-id="1148d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1148d-105">SYNTAX</span></span>

### <span data-ttu-id="1148d-106">구분 기호 (기본값)</span><span class="sxs-lookup"><span data-stu-id="1148d-106">Delimiter (Default)</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [[-Delimiter] <Char>] [-IncludeTypeInformation]
 [-NoTypeInformation] [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

### <span data-ttu-id="1148d-107">UseCulture</span><span class="sxs-lookup"><span data-stu-id="1148d-107">UseCulture</span></span>

```
ConvertTo-Csv [-InputObject] <PSObject> [-UseCulture] [-IncludeTypeInformation] [-NoTypeInformation]
 [-QuoteFields <String[]>] [-UseQuotes <QuoteKind>] [<CommonParameters>]
```

## <span data-ttu-id="1148d-108">설명</span><span class="sxs-lookup"><span data-stu-id="1148d-108">DESCRIPTION</span></span>

<span data-ttu-id="1148d-109">`ConvertTo-CSV`Cmdlet은 제출한 개체를 나타내는 일련의 CSV (쉼표로 구분 된 값) 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-109">The `ConvertTo-CSV` cmdlet returns a series of comma-separated value (CSV) strings that represent the objects that you submit.</span></span> <span data-ttu-id="1148d-110">그런 다음 cmdlet을 사용 `ConvertFrom-Csv` 하 여 CSV 문자열에서 개체를 다시 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-110">You can then use the `ConvertFrom-Csv` cmdlet to recreate objects from the CSV strings.</span></span> <span data-ttu-id="1148d-111">CSV에서 변환 된 개체는 속성 값을 포함 하 고 메서드를 포함 하지 않는 원래 개체의 문자열 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-111">The objects converted from CSV are string values of the original objects that contain property values and no methods.</span></span>

<span data-ttu-id="1148d-112">Cmdlet을 사용 `Export-Csv` 하 여 개체를 CSV 문자열로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-112">You can use the `Export-Csv` cmdlet to convert objects to CSV strings.</span></span> <span data-ttu-id="1148d-113">`Export-CSV` 은 `ConvertTo-CSV` CSV 문자열을 파일에 저장 한다는 점을 제외 하 고와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-113">`Export-CSV` is similar to `ConvertTo-CSV`, except that it saves the CSV strings to a file.</span></span>

<span data-ttu-id="1148d-114">Cmdlet에는 `ConvertTo-CSV` 쉼표 이외의 구분 기호를 지정 하거나 현재 문화권을 구분 기호로 사용 하는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-114">The `ConvertTo-CSV` cmdlet has parameters to specify a delimiter other than a comma or use the current culture as the delimiter.</span></span>

## <span data-ttu-id="1148d-115">예제</span><span class="sxs-lookup"><span data-stu-id="1148d-115">EXAMPLES</span></span>

### <span data-ttu-id="1148d-116">예제 1: 개체를 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="1148d-116">Example 1: Convert an object to CSV</span></span>

<span data-ttu-id="1148d-117">이 예에서는 **프로세스** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-117">This example converts a **Process** object to a CSV string.</span></span>

```powershell
Get-Process -Name pwsh | ConvertTo-Csv -NoTypeInformation
```

```Output
"Name","SI","Handles","VM","WS","PM","NPM","Path","Parent","Company","CPU","FileVersion", ...
"pwsh","8","950","2204001161216","100925440","59686912","67104", ...
```

<span data-ttu-id="1148d-118">`Get-Process`Cmdlet은 **프로세스** 개체를 가져오고 **Name** 매개 변수를 사용 하 여 PowerShell 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-118">The `Get-Process` cmdlet gets the **Process** object and uses the **Name** parameter to specify the PowerShell process.</span></span> <span data-ttu-id="1148d-119">Process 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="1148d-119">The process object is sent down the pipeline to the `ConvertTo-CSV` cmdlet.</span></span> <span data-ttu-id="1148d-120">`ConvertTo-CSV`Cmdlet은 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-120">The `ConvertTo-CSV` cmdlet converts the object to CSV strings.</span></span> <span data-ttu-id="1148d-121">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-121">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="1148d-122">예제 2: DateTime 개체를 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="1148d-122">Example 2: Convert a DateTime object to CSV</span></span>

<span data-ttu-id="1148d-123">이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-123">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
$Date = Get-Date
ConvertTo-Csv -InputObject $Date -Delimiter ';' -NoTypeInformation
```

```Output
"DisplayHint";"DateTime";"Date";"Day";"DayOfWeek";"DayOfYear";"Hour";"Kind";"Millisecond";"Minute";"Month";"Second";"Ticks";"TimeOfDay";"Year"
"DateTime";"Friday, January 4, 2019 14:40:51";"1/4/2019 00:00:00";"4";"Friday";"4";"14";"Local";"711";"40";"1";"51";"636822096517114991";"14:40:51.7114991";"2019"
```

<span data-ttu-id="1148d-124">`Get-Date`Cmdlet은 **DateTime** 개체를 가져와서 변수에 저장 합니다 `$Date` .</span><span class="sxs-lookup"><span data-stu-id="1148d-124">The `Get-Date` cmdlet gets the **DateTime** object and saves it in the `$Date` variable.</span></span> <span data-ttu-id="1148d-125">`ConvertTo-Csv`Cmdlet은 **DateTime** 개체를 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-125">The `ConvertTo-Csv` cmdlet converts the **DateTime** object to strings.</span></span> <span data-ttu-id="1148d-126">**InputObject** 매개 변수는 변수에 저장 된 **DateTime** 개체를 사용 합니다 `$Date` .</span><span class="sxs-lookup"><span data-stu-id="1148d-126">The **InputObject** parameter uses the **DateTime** object stored in the `$Date` variable.</span></span> <span data-ttu-id="1148d-127">**Delimiter** 매개 변수는 문자열 값을 구분 하기 위해 세미콜론을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-127">The **Delimiter** parameter specifies a semicolon to separate the string values.</span></span> <span data-ttu-id="1148d-128">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-128">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="1148d-129">예 3: PowerShell 이벤트 로그를 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="1148d-129">Example 3: Convert the PowerShell event log to CSV</span></span>

<span data-ttu-id="1148d-130">이 예에서는 PowerShell에 대 한 Windows 이벤트 로그를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-130">This example converts the Windows event log for PowerShell to a series of CSV strings.</span></span>

```powershell
(Get-Culture).TextInfo.ListSeparator
Get-WinEvent -LogName 'PowerShellCore/Operational' | ConvertTo-Csv -UseCulture -NoTypeInformation
```

```Output
,
"Message","Id","Version","Qualifiers","Level","Task","Opcode","Keywords","RecordId", ...
"Error Message = System error""4100","1",,"3","106","19","0","31716","PowerShellCore", ...
```

<span data-ttu-id="1148d-131">이 `Get-Culture` cmdlet은 중첩 된 속성 **System.globalization.cultureinfo.installeduiculture.textinfo.oemcodepage** 및 **listseparator** 를 사용 하 고 현재 문화권의 기본 목록 구분 기호를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-131">The `Get-Culture` cmdlet uses the nested properties **TextInfo** and **ListSeparator** and displays the current culture's default list separator.</span></span> <span data-ttu-id="1148d-132">`Get-WinEvent`Cmdlet은 이벤트 로그 개체를 가져오고 **LogName** 매개 변수를 사용 하 여 로그 파일 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-132">The `Get-WinEvent` cmdlet gets the event log objects and uses the **LogName** parameter to specify the log file name.</span></span> <span data-ttu-id="1148d-133">이벤트 로그 개체는 파이프라인에서 cmdlet으로 전송 됩니다 `ConvertTo-Csv` .</span><span class="sxs-lookup"><span data-stu-id="1148d-133">The event log objects are sent down the pipeline to the `ConvertTo-Csv` cmdlet.</span></span> <span data-ttu-id="1148d-134">`ConvertTo-Csv`Cmdlet은 이벤트 로그 개체를 일련의 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-134">The `ConvertTo-Csv` cmdlet converts the event log objects to a series of CSV strings.</span></span> <span data-ttu-id="1148d-135">**UseCulture** 매개 변수는 현재 문화권의 기본 목록 구분 기호를 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-135">The **UseCulture** parameter uses the current culture's default list separator as the delimiter.</span></span> <span data-ttu-id="1148d-136">**Notypeinformation** 매개 변수는 CSV 출력에서 **#TYPE** information 헤더를 제거 하며 PowerShell 6에서는 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-136">The **NoTypeInformation** parameter removes the **#TYPE** information header from the CSV output and is not required in PowerShell 6.</span></span>

### <span data-ttu-id="1148d-137">예제 4: 두 열 주위에 따옴표를 사용 하 여 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="1148d-137">Example 4: Convert to CSV with quotes around two columns</span></span>

<span data-ttu-id="1148d-138">이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-138">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -QuoteFields "DateTime","Date"
```

```Output
DisplayHint,"DateTime","Date",Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:27:34 AM","8/22/2019 12:00:00 AM",22,Thursday,234,11,Local,569,27,8,34,637020700545699784,11:27:34.5699784,2019
```

### <span data-ttu-id="1148d-139">예제 4: 필요한 경우에만 따옴표를 사용 하 여 CSV로 변환</span><span class="sxs-lookup"><span data-stu-id="1148d-139">Example 4: Convert to CSV with quotes only when needed</span></span>

<span data-ttu-id="1148d-140">이 예제에서는 **DateTime** 개체를 CSV 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-140">This example converts a **DateTime** object to a CSV string.</span></span>

```powershell
Get-Date | ConvertTo-Csv -UseQuotes AsNeeded
```

```Output
DisplayHint,DateTime,Date,Day,DayOfWeek,DayOfYear,Hour,Kind,Millisecond,Minute,Month,Second,Ticks,TimeOfDay,Year
DateTime,"Thursday, August 22, 2019 11:31:00 AM",8/22/2019 12:00:00 AM,22,Thursday,234,11,Local,713,31,8,0,637020702607132640,11:31:00.7132640,2019
```

## <span data-ttu-id="1148d-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1148d-141">PARAMETERS</span></span>

### <span data-ttu-id="1148d-142">-구분 기호</span><span class="sxs-lookup"><span data-stu-id="1148d-142">-Delimiter</span></span>

<span data-ttu-id="1148d-143">CSV 문자열의 속성 값을 구분 하는 구분 기호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-143">Specifies the delimiter to separate the property values in CSV strings.</span></span> <span data-ttu-id="1148d-144">기본값은 쉼표 ()입니다 `,` .</span><span class="sxs-lookup"><span data-stu-id="1148d-144">The default is a comma (`,`).</span></span> <span data-ttu-id="1148d-145">콜론 ()과 같은 문자를 입력 `:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-145">Enter a character, such as a colon (`:`).</span></span> <span data-ttu-id="1148d-146">세미콜론 ()을 지정 하려면 작은따옴표로 `;` 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-146">To specify a semicolon (`;`) enclose it in single quotation marks.</span></span>

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

### <span data-ttu-id="1148d-147">-IncludeTypeInformation</span><span class="sxs-lookup"><span data-stu-id="1148d-147">-IncludeTypeInformation</span></span>

<span data-ttu-id="1148d-148">이 매개 변수를 사용 하는 경우 출력의 첫 번째 줄에 **#TYPE** 와 개체 형식의 정규화 된 이름이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-148">When this parameter is used the first line of the output contains **#TYPE** followed by the fully qualified name of the object type.</span></span> <span data-ttu-id="1148d-149">예를 들어, **#TYPE를 처리** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-149">For example, **#TYPE System.Diagnostics.Process**.</span></span>

<span data-ttu-id="1148d-150">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-150">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: ITI

Required: False
Position: Named
Default value: #TYPE <Object>
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1148d-151">-InputObject</span><span class="sxs-lookup"><span data-stu-id="1148d-151">-InputObject</span></span>

<span data-ttu-id="1148d-152">CSV 문자열로 변환 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-152">Specifies the objects that are converted to CSV strings.</span></span> <span data-ttu-id="1148d-153">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1148d-153">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span> <span data-ttu-id="1148d-154">개체를로 파이프 할 수도 있습니다 `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="1148d-154">You can also pipe objects to `ConvertTo-CSV`.</span></span>

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

### <span data-ttu-id="1148d-155">-NoTypeInformation</span><span class="sxs-lookup"><span data-stu-id="1148d-155">-NoTypeInformation</span></span>

<span data-ttu-id="1148d-156">출력에서 **#TYPE** 정보 헤더를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-156">Removes the **#TYPE** information header from the output.</span></span> <span data-ttu-id="1148d-157">이 매개 변수는 PowerShell 6.0의 기본값이 며 이전 버전과의 호환성을 위해 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-157">This parameter became the default in PowerShell 6.0 and is included for backwards compatibility.</span></span>

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

### <span data-ttu-id="1148d-158">-UseCulture</span><span class="sxs-lookup"><span data-stu-id="1148d-158">-UseCulture</span></span>

<span data-ttu-id="1148d-159">현재 문화권의 목록 구분 기호를 항목 구분 기호로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-159">Uses the list separator for the current culture as the item delimiter.</span></span> <span data-ttu-id="1148d-160">문화권에 대 한 목록 구분 기호를 찾으려면 다음 명령을 사용 합니다. `(Get-Culture).TextInfo.ListSeparator`</span><span class="sxs-lookup"><span data-stu-id="1148d-160">To find the list separator for a culture, use the following command: `(Get-Culture).TextInfo.ListSeparator`.</span></span>

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

### <span data-ttu-id="1148d-161">-QuoteFields</span><span class="sxs-lookup"><span data-stu-id="1148d-161">-QuoteFields</span></span>

<span data-ttu-id="1148d-162">따옴표로 묶을 열의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-162">Specifies the names of the columns that should be quoted.</span></span> <span data-ttu-id="1148d-163">이 매개 변수를 사용 하는 경우 지정 된 열만 따옴표로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-163">When this parameter is used only the specified columns are quoted.</span></span> <span data-ttu-id="1148d-164">이 매개 변수는 PowerShell 7.0에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-164">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: QF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1148d-165">-UseQuotes 기술</span><span class="sxs-lookup"><span data-stu-id="1148d-165">-UseQuotes</span></span>

<span data-ttu-id="1148d-166">CSV 파일에서 따옴표를 사용 하는 경우를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-166">Specifies when quotes are used in the CSV files.</span></span> <span data-ttu-id="1148d-167">가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-167">Possible values are:</span></span>

- <span data-ttu-id="1148d-168">안 함-아무것도 인용 하지 않음</span><span class="sxs-lookup"><span data-stu-id="1148d-168">Never - don't quote anything</span></span>
- <span data-ttu-id="1148d-169">항상 따옴표 모든 항목 (기본 동작)</span><span class="sxs-lookup"><span data-stu-id="1148d-169">Always - quote everything (default behavior)</span></span>
- <span data-ttu-id="1148d-170">AsNeeded-구분 문자를 포함 하는 견적 필드만</span><span class="sxs-lookup"><span data-stu-id="1148d-170">AsNeeded - only quote fields that contain a delimiter character</span></span>

<span data-ttu-id="1148d-171">이 매개 변수는 PowerShell 7.0에 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-171">This parameter was added in PowerShell 7.0.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BaseCsvWritingCommand+QuoteKind
Parameter Sets: (All)
Aliases: UQ

Required: False
Position: Named
Default value: Always
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1148d-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1148d-172">CommonParameters</span></span>

<span data-ttu-id="1148d-173">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1148d-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1148d-174">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1148d-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1148d-175">입력</span><span class="sxs-lookup"><span data-stu-id="1148d-175">INPUTS</span></span>

### <span data-ttu-id="1148d-176">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="1148d-176">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="1148d-177">Any (확장 형식 시스템) 어댑터가 있는 개체를로 파이프 할 수 있습니다 `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="1148d-177">You can pipe any object that has an Extended Type System (ETS) adapter to `ConvertTo-CSV`.</span></span>

## <span data-ttu-id="1148d-178">출력</span><span class="sxs-lookup"><span data-stu-id="1148d-178">OUTPUTS</span></span>

### <span data-ttu-id="1148d-179">System.String</span><span class="sxs-lookup"><span data-stu-id="1148d-179">System.String</span></span>

<span data-ttu-id="1148d-180">CSV 출력은 문자열 컬렉션으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-180">The CSV output is returned as a collection of strings.</span></span>

## <span data-ttu-id="1148d-181">참고</span><span class="sxs-lookup"><span data-stu-id="1148d-181">NOTES</span></span>

<span data-ttu-id="1148d-182">CSV 형식에서 각 개체는 해당 속성 값의 쉼표로 구분된 목록으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-182">In CSV format, each object is represented by a comma-separated list of its property value.</span></span> <span data-ttu-id="1148d-183">속성 값은 개체의 **ToString ()** 메서드를 사용 하 여 문자열로 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-183">The property values are converted to strings using the object's **ToString()** method.</span></span> <span data-ttu-id="1148d-184">문자열은 속성 값 이름으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-184">The strings are represented by the property value name.</span></span> <span data-ttu-id="1148d-185">`ConvertTo-CSV` 개체의 메서드를 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-185">`ConvertTo-CSV` does not export the object's methods.</span></span>

<span data-ttu-id="1148d-186">CSV 문자열은 다음과 같이 출력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-186">The CSV strings are output as follows:</span></span>

- <span data-ttu-id="1148d-187">**Includetypeinformation** 을 사용 하는 경우 첫 번째 문자열은 **#TYPE** 다음에 개체 형식의 정규화 된 이름으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-187">If **IncludeTypeInformation** is used, the first string consists of **#TYPE** followed by the object type's fully qualified name.</span></span> <span data-ttu-id="1148d-188">예를 들어, **#TYPE를 처리** 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-188">For example, **#TYPE System.Diagnostics.Process**.</span></span>
- <span data-ttu-id="1148d-189">**Includetypeinformation** 을 사용 하지 않으면 첫 번째 문자열에 열 머리글이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-189">If **IncludeTypeInformation** is not used the first string includes the column headers.</span></span> <span data-ttu-id="1148d-190">헤더는 첫 번째 개체의 속성 이름을 쉼표로 구분 된 목록으로 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-190">The headers contain the first object's property names as a comma-separated list.</span></span>
- <span data-ttu-id="1148d-191">나머지 문자열은 각 개체의 속성 값에 대 한 쉼표로 구분 된 목록을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-191">The remaining strings contain comma-separated lists of each object's property values.</span></span>

<span data-ttu-id="1148d-192">PowerShell 6.0부터의 기본 동작은 `ConvertTo-CSV` CSV에 **#TYPE** 정보를 포함 하지 않는 것이 고 **notypeinformation** 이 암시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-192">Beginning with PowerShell 6.0 the default behavior of `ConvertTo-CSV` is to not include the **#TYPE** information in the CSV and **NoTypeInformation** is implied.</span></span> <span data-ttu-id="1148d-193">**Includetypeinformation** 은 **#TYPE** 정보를 포함 하 고 PowerShell 6.0 이전의 기본 동작을 에뮬레이트하는 데 사용할 수 있습니다 `ConvertTo-CSV` .</span><span class="sxs-lookup"><span data-stu-id="1148d-193">**IncludeTypeInformation** can be used to include the **#TYPE** information and emulate the default behavior of `ConvertTo-CSV` prior to PowerShell 6.0.</span></span>

<span data-ttu-id="1148d-194">에 여러 개체를 제출 하는 경우는 `ConvertTo-CSV` `ConvertTo-CSV` 제출한 첫 번째 개체의 속성을 기반으로 문자열을 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-194">When you submit multiple objects to `ConvertTo-CSV`, `ConvertTo-CSV` orders the strings based on the properties of the first object that you submit.</span></span> <span data-ttu-id="1148d-195">나머지 개체에 지정 된 속성 중 하나가 없는 경우 해당 개체의 속성 값은 Null 이며, 두 개의 연속 된 쉼표로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-195">If the remaining objects do not have one of the specified properties, the property value of that object is Null, as represented by two consecutive commas.</span></span> <span data-ttu-id="1148d-196">나머지 개체에 추가 속성이 있으면 해당 속성 값은 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1148d-196">If the remaining objects have additional properties, those property values are ignored.</span></span>

## <span data-ttu-id="1148d-197">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1148d-197">RELATED LINKS</span></span>

[<span data-ttu-id="1148d-198">ConvertFrom-Csv</span><span class="sxs-lookup"><span data-stu-id="1148d-198">ConvertFrom-Csv</span></span>](ConvertFrom-Csv.md)

[<span data-ttu-id="1148d-199">내보내기-Csv</span><span class="sxs-lookup"><span data-stu-id="1148d-199">Export-Csv</span></span>](Export-Csv.md)

[<span data-ttu-id="1148d-200">Import-Csv</span><span class="sxs-lookup"><span data-stu-id="1148d-200">Import-Csv</span></span>](Import-Csv.md)
