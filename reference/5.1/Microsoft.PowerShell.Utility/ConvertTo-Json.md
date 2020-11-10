---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: 9831249a9f1ffcc65fc275e44da04fde9348ae71
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388062"
---
# <span data-ttu-id="43e5a-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="43e5a-103">ConvertTo-Json</span></span>

## <span data-ttu-id="43e5a-104">개요</span><span class="sxs-lookup"><span data-stu-id="43e5a-104">SYNOPSIS</span></span>
<span data-ttu-id="43e5a-105">개체를 JSON 형식 문자열로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="43e5a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="43e5a-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## <span data-ttu-id="43e5a-107">설명</span><span class="sxs-lookup"><span data-stu-id="43e5a-107">DESCRIPTION</span></span>

<span data-ttu-id="43e5a-108">`ConvertTo-Json`Cmdlet은 모든 .net 개체를 JSON (JavaScript Object Notation) 형식의 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="43e5a-109">속성은 필드 이름으로 변환되고, 필드 값은 속성 값으로 변환되고, 메서드는 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="43e5a-110">그런 다음 cmdlet을 사용 `ConvertFrom-Json` 하 여 json 형식 문자열을 PowerShell에서 쉽게 관리 되는 json 개체로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="43e5a-111">많은 웹 사이트에서는 XML이 아닌 JSON을 사용하여 서버와 웹 기반 앱 간의 통신 데이터를 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="43e5a-112">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="43e5a-113">예제</span><span class="sxs-lookup"><span data-stu-id="43e5a-113">EXAMPLES</span></span>

### <span data-ttu-id="43e5a-114">예 1</span><span class="sxs-lookup"><span data-stu-id="43e5a-114">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
    "MinSupportedDateTime":  "\/Date(-62135596800000)\/",
    "MaxSupportedDateTime":  "\/Date(253402300799999)\/",
    "AlgorithmType":  1,
    "CalendarType":  1,
    "Eras":  [
                 1
             ],
    "TwoDigitYearMax":  2029,
    "IsReadOnly":  false
}
```

<span data-ttu-id="43e5a-115">이 명령은 cmdlet을 사용 하 여 `ConvertTo-Json` GregorianCalendar 개체를 JSON 형식 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="43e5a-116">예제 2</span><span class="sxs-lookup"><span data-stu-id="43e5a-116">Example 2</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="43e5a-117">이 명령은의 **압축** 매개 변수를 사용한 결과를 보여 줍니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="43e5a-117">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="43e5a-118">비교는 문자열의 모양에만 영향을 줄 뿐 유효성에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-118">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="43e5a-119">예제 3</span><span class="sxs-lookup"><span data-stu-id="43e5a-119">Example 3</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
    "DisplayHint":  2,
    "DateTime":  "Friday, January 13, 2012 8:06:16 PM",
    "Date":  "\/Date(1326441600000)\/",
    "Day":  13,
    "DayOfWeek":  5,
    "DayOfYear":  13,
    "Hour":  20,
    "Kind":  2,
    "Millisecond":  221,
    "Minute":  6,
    "Month":  1,
    "Second":  16,
    "Ticks":  634620819762218083,
    "TimeOfDay":  {
                      "Ticks":  723762218083,
                      "Days":  0,
                      "Hours":  20,
                      "Milliseconds":  221,
                      "Minutes":  6,
                      "Seconds":  16,
                      "TotalDays":  0.83768775241087956,
                      "TotalHours":  20.104506057861109,
                      "TotalMilliseconds":  72376221.8083,
                      "TotalMinutes":  1206.2703634716668,
                      "TotalSeconds":  72376.22180829999
                  },
    "Year":  2012
}
```

<span data-ttu-id="43e5a-120">이 예에서는 cmdlet을 사용 하 여 `ConvertTo-Json` **시스템의 DateTime** 개체를 cmdlet에서 `Get-Date` JSON 형식 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-120">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="43e5a-121">이 명령은 cmdlet을 사용 `Select-Object` 하 여 `*` **DateTime** 개체의 속성 ()을 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-121">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="43e5a-122">출력은 반환 된 JSON 문자열을 보여 줍니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="43e5a-122">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="43e5a-123">예제 4</span><span class="sxs-lookup"><span data-stu-id="43e5a-123">Example 4</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : October 12, 2018 10:55:52 PM
Date        : 2018-10-12 12:00:00 AM
Day         : 12
DayOfWeek   : 5
DayOfYear   : 285
Hour        : 22
Kind        : 2
Millisecond : 768
Minute      : 55
Month       : 10
Second      : 52
Ticks       : 636749817527683372
TimeOfDay   : @{Ticks=825527683372; Days=0; Hours=22; Milliseconds=768; Minutes=55; Seconds=52;
              TotalDays=0.95547185575463; TotalHours=22.9313245381111; TotalMilliseconds=82552768.3372;
              TotalMinutes=1375.87947228667; TotalSeconds=82552.7683372}
Year        : 2018
```

<span data-ttu-id="43e5a-124">이 예제에서는 및 cmdlet을 사용 하 여 `ConvertTo-Json` `ConvertFrom-Json` 개체를 json 문자열 및 json 개체로 변환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-124">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="43e5a-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="43e5a-125">PARAMETERS</span></span>

### <span data-ttu-id="43e5a-126">-압축</span><span class="sxs-lookup"><span data-stu-id="43e5a-126">-Compress</span></span>

<span data-ttu-id="43e5a-127">출력 문자열에서 공백과 들여쓰기 서식을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-127">Omits white space and indented formatting in the output string.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43e5a-128">-깊이</span><span class="sxs-lookup"><span data-stu-id="43e5a-128">-Depth</span></span>

<span data-ttu-id="43e5a-129">JSON 표시에 포함되는 포함 개체의 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-129">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="43e5a-130">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-130">The default value is 2.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 2
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="43e5a-131">-InputObject</span><span class="sxs-lookup"><span data-stu-id="43e5a-131">-InputObject</span></span>

<span data-ttu-id="43e5a-132">JSON 형식으로 변환할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-132">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="43e5a-133">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="43e5a-133">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="43e5a-134">개체를로 파이프 할 수도 있습니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="43e5a-134">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="43e5a-135">**InputObject** 매개 변수는 필수 이지만 해당 값은 null ( `$null` ) 또는 빈 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-135">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="43e5a-136">입력 개체가 인 경우은 `$null` `ConvertTo-Json` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-136">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="43e5a-137">입력 개체가 빈 문자열이 면에서 `ConvertTo-Json` 빈 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-137">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="43e5a-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="43e5a-138">CommonParameters</span></span>

<span data-ttu-id="43e5a-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="43e5a-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="43e5a-140">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="43e5a-140">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="43e5a-141">입력</span><span class="sxs-lookup"><span data-stu-id="43e5a-141">INPUTS</span></span>

### <span data-ttu-id="43e5a-142">System.Object</span><span class="sxs-lookup"><span data-stu-id="43e5a-142">System.Object</span></span>

<span data-ttu-id="43e5a-143">모든 개체를로 파이프 할 수 있습니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="43e5a-143">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="43e5a-144">출력</span><span class="sxs-lookup"><span data-stu-id="43e5a-144">OUTPUTS</span></span>

### <span data-ttu-id="43e5a-145">System.String</span><span class="sxs-lookup"><span data-stu-id="43e5a-145">System.String</span></span>

## <span data-ttu-id="43e5a-146">참고</span><span class="sxs-lookup"><span data-stu-id="43e5a-146">NOTES</span></span>

<span data-ttu-id="43e5a-147">`ConvertTo-Json`Cmdlet은 [JavaScriptSerializer 클래스](/dotnet/api/system.web.script.serialization.javascriptserializer)를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="43e5a-147">The `ConvertTo-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="43e5a-148">관련 링크</span><span class="sxs-lookup"><span data-stu-id="43e5a-148">RELATED LINKS</span></span>

<span data-ttu-id="43e5a-149">[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="43e5a-149">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="43e5a-150">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="43e5a-150">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="43e5a-151">Get-Content</span><span class="sxs-lookup"><span data-stu-id="43e5a-151">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="43e5a-152">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="43e5a-152">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="43e5a-153">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="43e5a-153">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="43e5a-154">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="43e5a-154">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
