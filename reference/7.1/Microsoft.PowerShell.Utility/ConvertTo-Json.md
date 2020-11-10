---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: acfeae4025b3a32d2a04307609597cf30332d708
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389456"
---
# <span data-ttu-id="ddb99-103">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="ddb99-103">ConvertTo-Json</span></span>

## <span data-ttu-id="ddb99-104">개요</span><span class="sxs-lookup"><span data-stu-id="ddb99-104">SYNOPSIS</span></span>
<span data-ttu-id="ddb99-105">개체를 JSON 형식 문자열로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-105">Converts an object to a JSON-formatted string.</span></span>

## <span data-ttu-id="ddb99-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ddb99-106">SYNTAX</span></span>

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
[-EnumsAsStrings] [-AsArray] [-EscapeHandling <StringEscapeHandling>]
[<CommonParameters>]
```

## <span data-ttu-id="ddb99-107">설명</span><span class="sxs-lookup"><span data-stu-id="ddb99-107">DESCRIPTION</span></span>

<span data-ttu-id="ddb99-108">`ConvertTo-Json`Cmdlet은 모든 .net 개체를 JSON (JavaScript Object Notation) 형식의 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-108">The `ConvertTo-Json` cmdlet converts any .NET object to a string in JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="ddb99-109">속성은 필드 이름으로 변환되고, 필드 값은 속성 값으로 변환되고, 메서드는 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-109">The properties are converted to field names, the field values are converted to property values, and the methods are removed.</span></span>

<span data-ttu-id="ddb99-110">그런 다음 cmdlet을 사용 `ConvertFrom-Json` 하 여 json 형식 문자열을 PowerShell에서 쉽게 관리 되는 json 개체로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-110">You can then use the `ConvertFrom-Json` cmdlet to convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell.</span></span>

<span data-ttu-id="ddb99-111">많은 웹 사이트에서는 XML이 아닌 JSON을 사용하여 서버와 웹 기반 앱 간의 통신 데이터를 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-111">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="ddb99-112">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-112">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="ddb99-113">예제</span><span class="sxs-lookup"><span data-stu-id="ddb99-113">EXAMPLES</span></span>

### <span data-ttu-id="ddb99-114">예 1</span><span class="sxs-lookup"><span data-stu-id="ddb99-114">Example 1</span></span>

```powershell
(Get-UICulture).Calendar | ConvertTo-Json
```

```Output
{
  "MinSupportedDateTime": "0001-01-01T00:00:00",
  "MaxSupportedDateTime": "9999-12-31T23:59:59.9999999",
  "AlgorithmType": 1,
  "CalendarType": 1,
  "Eras": [
    1
  ],
  "TwoDigitYearMax": 2029,
  "IsReadOnly": true
}
```

<span data-ttu-id="ddb99-115">이 명령은 cmdlet을 사용 하 여 `ConvertTo-Json` GregorianCalendar 개체를 JSON 형식 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-115">This command uses the `ConvertTo-Json` cmdlet to convert a GregorianCalendar object to a JSON-formatted string.</span></span>

### <span data-ttu-id="ddb99-116">예제 2</span><span class="sxs-lookup"><span data-stu-id="ddb99-116">Example 2</span></span>

```powershell
Get-Date | ConvertTo-Json; Get-Date | ConvertTo-Json -AsArray
```

```Output
{
  "value": "2018-10-12T23:07:18.8450248-05:00",
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 11:07:18 PM"
}
[
  {
    "value": "2018-10-12T23:07:18.8480668-05:00",
    "DisplayHint": 2,
    "DateTime": "October 12, 2018 11:07:18 PM"
  }
]
```

<span data-ttu-id="ddb99-117">이 예에서는 `ConvertTo-Json` **asarray** 스위치 매개 변수를 사용 하거나 사용 하지 않고 cmdlet의 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-117">This example shows the output from `ConvertTo-Json` cmdlet with and without the **AsArray** switch parameter.</span></span> <span data-ttu-id="ddb99-118">출력의 두 번째 부분이 배열 괄호로 래핑되어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-118">You can see the second portion of the output is wrapped in array brackets.</span></span>

### <span data-ttu-id="ddb99-119">예제 3</span><span class="sxs-lookup"><span data-stu-id="ddb99-119">Example 3</span></span>

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

<span data-ttu-id="ddb99-120">이 명령은의 **압축** 매개 변수를 사용한 결과를 보여 줍니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="ddb99-120">This command shows the effect of using the **Compress** parameter of `ConvertTo-Json`.</span></span> <span data-ttu-id="ddb99-121">비교는 문자열의 모양에만 영향을 줄 뿐 유효성에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-121">The compression affects only the appearance of the string, not its validity.</span></span>

### <span data-ttu-id="ddb99-122">예제 4</span><span class="sxs-lookup"><span data-stu-id="ddb99-122">Example 4</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json
```

```Output
{
  "DisplayHint": 2,
  "DateTime": "October 12, 2018 10:55:32 PM",
  "Date": "2018-10-12T00:00:00-05:00",
  "Day": 12,
  "DayOfWeek": 5,
  "DayOfYear": 285,
  "Hour": 22,
  "Kind": 2,
  "Millisecond": 639,
  "Minute": 55,
  "Month": 10,
  "Second": 32,
  "Ticks": 636749817326397744,
  "TimeOfDay": {
    "Ticks": 825326397744,
    "Days": 0,
    "Hours": 22,
    "Milliseconds": 639,
    "Minutes": 55,
    "Seconds": 32,
    "TotalDays": 0.95523888627777775,
    "TotalHours": 22.925733270666665,
    "TotalMilliseconds": 82532639.774400011,
    "TotalMinutes": 1375.54399624,
    "TotalSeconds": 82532.6397744
  },
  "Year": 2018
}
```

<span data-ttu-id="ddb99-123">이 예에서는 cmdlet을 사용 하 여 `ConvertTo-Json` **시스템의 DateTime** 개체를 cmdlet에서 `Get-Date` JSON 형식 문자열로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-123">This example uses the `ConvertTo-Json` cmdlet to convert a **System.DateTime** object from the `Get-Date` cmdlet to a JSON-formatted string.</span></span> <span data-ttu-id="ddb99-124">이 명령은 cmdlet을 사용 `Select-Object` 하 여 `*` **DateTime** 개체의 속성 ()을 모두 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-124">The command uses the `Select-Object` cmdlet to get all (`*`) of the properties of the **DateTime** object.</span></span> <span data-ttu-id="ddb99-125">출력은 반환 된 JSON 문자열을 보여 줍니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="ddb99-125">The output shows the JSON string that `ConvertTo-Json` returned.</span></span>

### <span data-ttu-id="ddb99-126">예제 5</span><span class="sxs-lookup"><span data-stu-id="ddb99-126">Example 5</span></span>

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

<span data-ttu-id="ddb99-127">이 예제에서는 및 cmdlet을 사용 하 여 `ConvertTo-Json` `ConvertFrom-Json` 개체를 json 문자열 및 json 개체로 변환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-127">This example shows how to use the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert an object to a JSON string and a JSON object.</span></span>

## <span data-ttu-id="ddb99-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ddb99-128">PARAMETERS</span></span>

### <span data-ttu-id="ddb99-129">-AsArray</span><span class="sxs-lookup"><span data-stu-id="ddb99-129">-AsArray</span></span>

<span data-ttu-id="ddb99-130">입력이 단일 개체인 경우에도 개체를 배열 대괄호로 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-130">Outputs the object in array brackets, even if the input is a single object.</span></span>

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

### <span data-ttu-id="ddb99-131">-압축</span><span class="sxs-lookup"><span data-stu-id="ddb99-131">-Compress</span></span>

<span data-ttu-id="ddb99-132">출력 문자열에서 공백과 들여쓰기 서식을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-132">Omits white space and indented formatting in the output string.</span></span>

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

### <span data-ttu-id="ddb99-133">-깊이</span><span class="sxs-lookup"><span data-stu-id="ddb99-133">-Depth</span></span>

<span data-ttu-id="ddb99-134">JSON 표시에 포함되는 포함 개체의 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-134">Specifies how many levels of contained objects are included in the JSON representation.</span></span> <span data-ttu-id="ddb99-135">기본값은 2입니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-135">The default value is 2.</span></span>

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

### <span data-ttu-id="ddb99-136">-EnumsAsStrings</span><span class="sxs-lookup"><span data-stu-id="ddb99-136">-EnumsAsStrings</span></span>

<span data-ttu-id="ddb99-137">모든 열거형을 해당 문자열 표현으로 변환 하는 대체 serialization 옵션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-137">Provides an alternative serialization option that converts all enumerations to their string representation.</span></span>

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

### <span data-ttu-id="ddb99-138">-EscapeHandling</span><span class="sxs-lookup"><span data-stu-id="ddb99-138">-EscapeHandling</span></span>

<span data-ttu-id="ddb99-139">결과 JSON 출력에서 특정 문자가 이스케이프 되는 방법을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-139">Controls how certain characters are escaped in the resulting JSON output.</span></span> <span data-ttu-id="ddb99-140">기본적으로 제어 문자 (예: 줄 바꿈)만 이스케이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-140">By default, only control characters (like newline) are escaped.</span></span>

<span data-ttu-id="ddb99-141">사용 가능한 값은</span><span class="sxs-lookup"><span data-stu-id="ddb99-141">Acceptable values are:</span></span>

- <span data-ttu-id="ddb99-142">기본 전용 제어 문자가 이스케이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-142">Default - Only control characters are escaped.</span></span>
- <span data-ttu-id="ddb99-143">EscapeNonAscii-ASCII가 아닌 모든 문자 및 제어 문자를 이스케이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-143">EscapeNonAscii - All non-ASCII and control characters are escaped.</span></span>
- <span data-ttu-id="ddb99-144">EscapeHtml (,, `<` `>` `&` , `'` , `"` ) 및 제어 문자는 이스케이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-144">EscapeHtml - HTML (`<`, `>`, `&`, `'`, `"`) and control characters are escaped.</span></span>

<span data-ttu-id="ddb99-145">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-145">This parameter was introduced in PowerShell 6.2.</span></span>

```yaml
Type: Newtonsoft.Json.StringEscapeHandling
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ddb99-146">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ddb99-146">-InputObject</span></span>

<span data-ttu-id="ddb99-147">JSON 형식으로 변환할 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-147">Specifies the objects to convert to JSON format.</span></span> <span data-ttu-id="ddb99-148">개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="ddb99-148">Enter a variable that contains the objects, or type a command or expression that gets the objects.</span></span> <span data-ttu-id="ddb99-149">개체를로 파이프 할 수도 있습니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="ddb99-149">You can also pipe an object to `ConvertTo-Json`.</span></span>

<span data-ttu-id="ddb99-150">**InputObject** 매개 변수는 필수 이지만 해당 값은 null ( `$null` ) 또는 빈 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-150">The **InputObject** parameter is required, but its value can be null (`$null`) or an empty string.</span></span>
<span data-ttu-id="ddb99-151">입력 개체가 인 경우은 `$null` `ConvertTo-Json` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-151">When the input object is `$null`, `ConvertTo-Json` does not generate any output.</span></span> <span data-ttu-id="ddb99-152">입력 개체가 빈 문자열이 면에서 `ConvertTo-Json` 빈 문자열을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-152">When the input object is an empty string, `ConvertTo-Json` returns an empty string.</span></span>

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

### <span data-ttu-id="ddb99-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ddb99-153">CommonParameters</span></span>

<span data-ttu-id="ddb99-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ddb99-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ddb99-155">자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ddb99-155">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ddb99-156">입력</span><span class="sxs-lookup"><span data-stu-id="ddb99-156">INPUTS</span></span>

### <span data-ttu-id="ddb99-157">System.Object</span><span class="sxs-lookup"><span data-stu-id="ddb99-157">System.Object</span></span>

<span data-ttu-id="ddb99-158">모든 개체를로 파이프 할 수 있습니다 `ConvertTo-Json` .</span><span class="sxs-lookup"><span data-stu-id="ddb99-158">You can pipe any object to `ConvertTo-Json`.</span></span>

## <span data-ttu-id="ddb99-159">출력</span><span class="sxs-lookup"><span data-stu-id="ddb99-159">OUTPUTS</span></span>

### <span data-ttu-id="ddb99-160">System.String</span><span class="sxs-lookup"><span data-stu-id="ddb99-160">System.String</span></span>

## <span data-ttu-id="ddb99-161">참고</span><span class="sxs-lookup"><span data-stu-id="ddb99-161">NOTES</span></span>

<span data-ttu-id="ddb99-162">`ConvertTo-Json`Cmdlet은 [newtonsoft.json Json.NET](https://www.newtonsoft.com/json)를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddb99-162">The `ConvertTo-Json` cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

## <span data-ttu-id="ddb99-163">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ddb99-163">RELATED LINKS</span></span>

<span data-ttu-id="ddb99-164">[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="ddb99-164">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="ddb99-165">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="ddb99-165">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="ddb99-166">Get-Content</span><span class="sxs-lookup"><span data-stu-id="ddb99-166">Get-Content</span></span>](../Microsoft.PowerShell.Management/Get-Content.md)

[<span data-ttu-id="ddb99-167">Get-UICulture</span><span class="sxs-lookup"><span data-stu-id="ddb99-167">Get-UICulture</span></span>](Get-UICulture.md)

[<span data-ttu-id="ddb99-168">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="ddb99-168">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="ddb99-169">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="ddb99-169">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="ddb99-170">NewtonSoft.Js합니다. StringEscapeHandling</span><span class="sxs-lookup"><span data-stu-id="ddb99-170">NewtonSoft.Json.StringEscapeHandling</span></span>](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)
