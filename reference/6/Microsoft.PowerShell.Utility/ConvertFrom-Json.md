---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: 50372f0b938a1f8b051ec799ecfa94498b72dbc5
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224681"
---
# <span data-ttu-id="ea1e5-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="ea1e5-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="ea1e5-104">개요</span><span class="sxs-lookup"><span data-stu-id="ea1e5-104">SYNOPSIS</span></span>
<span data-ttu-id="ea1e5-105">JSON 형식 문자열을 사용자 지정 개체 또는 해시 테이블로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-105">Converts a JSON-formatted string to a custom object or a hash table.</span></span>

## <span data-ttu-id="ea1e5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ea1e5-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="ea1e5-107">설명</span><span class="sxs-lookup"><span data-stu-id="ea1e5-107">DESCRIPTION</span></span>

<span data-ttu-id="ea1e5-108">`ConvertFrom-Json`Cmdlet JavaScript Object Notation (json) 형식 문자열을 json 문자열의 각 필드에 대 한 속성이 있는 사용자 지정 **PSCustomObject** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="ea1e5-109">JSON은 주로 웹 사이트에서 개체의 텍스트 표현을 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="ea1e5-110">JSON 표준은 **PSCustomObject** 에서 금지 된 사용을 금지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="ea1e5-111">예를 들어 JSON 문자열에 중복 키가 포함 되어 있는 경우이 cmdlet은 마지막 키만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="ea1e5-112">아래의 다른 예를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-112">See other examples below.</span></span>

<span data-ttu-id="ea1e5-113">모든 개체에서 JSON 문자열을 생성 하려면 cmdlet을 사용 `ConvertTo-Json` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="ea1e5-114">이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="ea1e5-115">PowerShell 6부터이 cmdlet은 주석을 사용 하 여 JSON을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-115">Beginning with PowerShell 6, this cmdlet supports JSON with comments.</span></span> <span data-ttu-id="ea1e5-116">수락 된 주석은 두 개의 슬래시 ()로 시작 `//` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-116">Accepted comments are started with two forward slashes (`//`).</span></span> <span data-ttu-id="ea1e5-117">주석은 데이터에 표시 되지 않으며 PowerShell 5.1에서와 같이 데이터를 손상 시키거나 오류를 throw 하지 않고 파일에 기록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-117">The comment will not be represented in the data and can be written in the file without corrupting the data or throwing an error as it did in PowerShell 5.1.</span></span>

## <span data-ttu-id="ea1e5-118">예제</span><span class="sxs-lookup"><span data-stu-id="ea1e5-118">EXAMPLES</span></span>

### <span data-ttu-id="ea1e5-119">예제 1: DateTime 개체를 JSON 개체로 변환</span><span class="sxs-lookup"><span data-stu-id="ea1e5-119">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="ea1e5-120">이 명령은 및 cmdlet을 사용 하 여 `ConvertTo-Json` `ConvertFrom-Json` **DateTime** 개체를 cmdlet에서 `Get-Date` JSON 개체로 변환한 다음 **PSCustomObject** 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-120">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

```powershell
Get-Date | Select-Object -Property * | ConvertTo-Json | ConvertFrom-Json
```

```Output
DisplayHint : 2
DateTime    : Friday, January 13, 2012 8:06:31 PM
Date        : 1/13/2012 8:00:00 AM
Day         : 13
DayOfWeek   : 5
DayOfYear   : 13
Hour        : 20
Kind        : 2
Millisecond : 400
Minute      : 6
Month       : 1
Second      : 31
Ticks       : 634620819914009002
TimeOfDay   : @{Ticks=723914009002; Days=0; Hours=20; Milliseconds=400; Minutes=6; Seconds=31; TotalDays=0.83786343634490734; TotalHours=20.108722472277776; TotalMilliseconds=72391400.900200009; TotalMinutes=1206.5233483366667;TotalSeconds=72391.4009002}
Year        : 2012
```

<span data-ttu-id="ea1e5-121">이 예에서는 cmdlet을 사용 `Select-Object` 하 여 **DateTime** 개체의 모든 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-121">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="ea1e5-122">Cmdlet을 사용 하 여 `ConvertTo-Json` **DateTime** 개체를 json 개체로 서식 지정 된 문자열로 변환 하 고 cmdlet을 사용 하 여 `ConvertFrom-Json` Json 형식 문자열을 **PSCustomObject** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-122">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="ea1e5-123">예제 2: 웹 서비스에서 JSON 문자열 가져오기 및 PowerShell 개체로 변환</span><span class="sxs-lookup"><span data-stu-id="ea1e5-123">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="ea1e5-124">이 명령은 cmdlet을 사용 하 여 `Invoke-WebRequest` 웹 서비스에서 json 문자열을 가져온 다음 cmdlet을 사용 하 여 `ConvertFrom-Json` json 콘텐츠를 PowerShell에서 관리할 수 있는 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-124">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="ea1e5-125">`Invoke-RestMethod`JSON 콘텐츠를 개체로 자동으로 변환 하는 cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-125">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="ea1e5-126">예제 3: JSON 문자열을 사용자 지정 개체로 변환</span><span class="sxs-lookup"><span data-stu-id="ea1e5-126">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="ea1e5-127">이 예제에서는 cmdlet을 사용 하 여 `ConvertFrom-Json` JSON 파일을 PowerShell 사용자 지정 개체로 변환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-127">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="ea1e5-128">이 명령은 Get-Content cmdlet을 사용 하 여 JSON 파일의 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-128">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="ea1e5-129">그런 다음 파이프라인 연산자를 사용 하 여 구분 기호로 분리 된 문자열을 cmdlet으로 보냅니다 `ConvertFrom-Json` . 그러면이 cmdlet이 사용자 지정 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-129">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

### <span data-ttu-id="ea1e5-130">예제 4: JSON 문자열을 해시 테이블로 변환</span><span class="sxs-lookup"><span data-stu-id="ea1e5-130">Example 4: Convert a JSON string to a hash table</span></span>

<span data-ttu-id="ea1e5-131">이 명령은 `-AsHashtable` 스위치가 명령의 제한을 극복할 수 있는 예를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-131">This command shows an example where the `-AsHashtable` switch can overcome limitations of the command.</span></span>

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

<span data-ttu-id="ea1e5-132">JSON 문자열에는 대/소문자만 다른 키를 가진 두 개의 키 값 쌍이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-132">The JSON string contains two key value pairs with keys that differ only in casing.</span></span> <span data-ttu-id="ea1e5-133">스위치가 없으면 명령에서 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-133">Without the switch, the command would have thrown an error.</span></span>

## <span data-ttu-id="ea1e5-134">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ea1e5-134">PARAMETERS</span></span>

### <span data-ttu-id="ea1e5-135">-AsHashtable</span><span class="sxs-lookup"><span data-stu-id="ea1e5-135">-AsHashtable</span></span>

<span data-ttu-id="ea1e5-136">JSON을 해시 테이블 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-136">Converts the JSON to a hash table object.</span></span> <span data-ttu-id="ea1e5-137">이 스위치는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-137">This switch was introduced in PowerShell 6.0.</span></span> <span data-ttu-id="ea1e5-138">Cmdlet에 대 한 몇 가지 제한 사항을 해결할 수 있는 몇 가지 시나리오가 있습니다 `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="ea1e5-138">There are several scenarios where it can overcome some limitations of the `ConvertFrom-Json` cmdlet.</span></span>

- <span data-ttu-id="ea1e5-139">JSON에 대/소문자만 다른 키가 있는 목록이 포함 된 경우</span><span class="sxs-lookup"><span data-stu-id="ea1e5-139">If the JSON contains a list with keys that only differ in casing.</span></span> <span data-ttu-id="ea1e5-140">스위치가 없으면 해당 키는 동일한 키로 표시 되므로 마지막 항목만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-140">Without the switch, those keys would be seen as identical keys and therefore only the last one would get used.</span></span>
- <span data-ttu-id="ea1e5-141">JSON에 빈 문자열인 키가 포함 되어 있으면입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-141">If the JSON contains a key that is an empty string.</span></span> <span data-ttu-id="ea1e5-142">스위치를 사용 하지 않을 경우 cmdlet은 오류를 throw `PSCustomObject` 합니다. 단,이는 해시 테이블의 경우에는 허용 되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-142">Without the switch, the cmdlet would throw an error since a `PSCustomObject` does not allow for that but a hash table does.</span></span> <span data-ttu-id="ea1e5-143">이 문제가 발생할 수 있는 예제 사용 사례는 `project.lock.json` 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-143">An example use case where this can occurs are `project.lock.json` files.</span></span>
- <span data-ttu-id="ea1e5-144">특정 데이터 구조에 대해 해시 테이블을 더 빠르게 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-144">Hash tables can be processed faster for certain data structures.</span></span>

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

### <span data-ttu-id="ea1e5-145">-깊이</span><span class="sxs-lookup"><span data-stu-id="ea1e5-145">-Depth</span></span>

<span data-ttu-id="ea1e5-146">JSON 입력에 허용 되는 최대 깊이를 가져오거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-146">Gets or sets the maximum depth the JSON input is allowed to have.</span></span> <span data-ttu-id="ea1e5-147">기본적으로 1024입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-147">By default, it is 1024.</span></span>

<span data-ttu-id="ea1e5-148">이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-148">This parameter was introduced in PowerShell 6.2.</span></span>

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

### <span data-ttu-id="ea1e5-149">-InputObject</span><span class="sxs-lookup"><span data-stu-id="ea1e5-149">-InputObject</span></span>

<span data-ttu-id="ea1e5-150">JSON 개체로 변환할 JSON 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-150">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="ea1e5-151">문자열이 포함된 변수를 입력하거나 문자열을 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-151">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="ea1e5-152">문자열을로 파이프 할 수도 있습니다 `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="ea1e5-152">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="ea1e5-153">**InputObject** 매개 변수는 필수이지만 값이 빈 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-153">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="ea1e5-154">입력 개체가 빈 문자열이 면에서 `ConvertFrom-Json` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-154">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="ea1e5-155">**InputObject** 값은 일 수 없습니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="ea1e5-155">The **InputObject** value cannot be `$null`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ea1e5-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ea1e5-156">CommonParameters</span></span>

<span data-ttu-id="ea1e5-157">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ea1e5-158">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ea1e5-159">입력</span><span class="sxs-lookup"><span data-stu-id="ea1e5-159">INPUTS</span></span>

### <span data-ttu-id="ea1e5-160">System.String</span><span class="sxs-lookup"><span data-stu-id="ea1e5-160">System.String</span></span>

<span data-ttu-id="ea1e5-161">JSON 문자열을로 파이프 할 수 있습니다 `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="ea1e5-161">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="ea1e5-162">출력</span><span class="sxs-lookup"><span data-stu-id="ea1e5-162">OUTPUTS</span></span>

### <span data-ttu-id="ea1e5-163">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="ea1e5-163">PSCustomObject</span></span>

### <span data-ttu-id="ea1e5-164">System.Collections.Hashtable</span><span class="sxs-lookup"><span data-stu-id="ea1e5-164">System.Collections.Hashtable</span></span>

## <span data-ttu-id="ea1e5-165">참고</span><span class="sxs-lookup"><span data-stu-id="ea1e5-165">NOTES</span></span>

<span data-ttu-id="ea1e5-166">이 cmdlet은 [newtonsoft.json Json.NET](https://www.newtonsoft.com/json)를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-166">This cmdlet is implemented using [Newtonsoft Json.NET](https://www.newtonsoft.com/json).</span></span>

<span data-ttu-id="ea1e5-167">PowerShell 6부터는 `ConvertTo-Json` 타임 스탬프로 형식이 지정 된 문자열을 **DateTime** 값으로 변환 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-167">Beginning in PowerShell 6, `ConvertTo-Json` attempts to convert strings formatted as timestamps to **DateTime** values.</span></span> <span data-ttu-id="ea1e5-168">변환 된 값은 속성이 다음과 같이 `[datetime]` 설정 된 인스턴스입니다 `Kind` .</span><span class="sxs-lookup"><span data-stu-id="ea1e5-168">The converted value is a `[datetime]` instance with a `Kind` property set as follows:</span></span>

- <span data-ttu-id="ea1e5-169">`Unspecified`입력 문자열에 표준 시간대 정보가 없는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-169">`Unspecified`, if there is no time zone information in the input string.</span></span>
- <span data-ttu-id="ea1e5-170">`Utc`표준 시간대 정보가 후행 인 경우 `Z` 입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-170">`Utc`, if the time zone information is a trailing `Z`.</span></span>
- <span data-ttu-id="ea1e5-171">`Local`표준 시간대 정보가와 같은 후행 UTC _오프셋_ 으로 지정 된 경우 `+02:00` 입니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-171">`Local`, if the time zone information is given as a trailing UTC _offset_ like `+02:00`.</span></span> <span data-ttu-id="ea1e5-172">오프셋은 호출자의 구성 된 표준 시간대로 적절 하 게 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-172">The offset is properly converted to the caller's configured time zone.</span></span> <span data-ttu-id="ea1e5-173">기본 출력 형식은 원래 표준 시간대 오프셋을 나타내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea1e5-173">The default output formatting does not indicate the original time zone offset.</span></span>

## <span data-ttu-id="ea1e5-174">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ea1e5-174">RELATED LINKS</span></span>

<span data-ttu-id="ea1e5-175">[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="ea1e5-175">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="ea1e5-176">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="ea1e5-176">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="ea1e5-177">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="ea1e5-177">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="ea1e5-178">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="ea1e5-178">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
