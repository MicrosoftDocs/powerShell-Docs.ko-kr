---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: e1bab9250269dadf0d899f9e172e8a4a8387271d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388130"
---
# <span data-ttu-id="2f033-103">ConvertFrom-Json</span><span class="sxs-lookup"><span data-stu-id="2f033-103">ConvertFrom-Json</span></span>

## <span data-ttu-id="2f033-104">개요</span><span class="sxs-lookup"><span data-stu-id="2f033-104">SYNOPSIS</span></span>
<span data-ttu-id="2f033-105">JSON 형식 문자열을 사용자 지정 개체로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-105">Converts a JSON-formatted string to a custom object.</span></span>

## <span data-ttu-id="2f033-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f033-106">SYNTAX</span></span>

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## <span data-ttu-id="2f033-107">설명</span><span class="sxs-lookup"><span data-stu-id="2f033-107">DESCRIPTION</span></span>

<span data-ttu-id="2f033-108">`ConvertFrom-Json`Cmdlet JavaScript Object Notation (json) 형식 문자열을 json 문자열의 각 필드에 대 한 속성이 있는 사용자 지정 **PSCustomObject** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-108">The `ConvertFrom-Json` cmdlet converts a JavaScript Object Notation (JSON) formatted string to a custom **PSCustomObject** object that has a property for each field in the JSON string.</span></span> <span data-ttu-id="2f033-109">JSON은 주로 웹 사이트에서 개체의 텍스트 표현을 제공하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-109">JSON is commonly used by web sites to provide a textual representation of objects.</span></span> <span data-ttu-id="2f033-110">JSON 표준은 **PSCustomObject** 에서 금지 된 사용을 금지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-110">The JSON standard does not prohibit usage that is prohibited with a **PSCustomObject**.</span></span> <span data-ttu-id="2f033-111">예를 들어 JSON 문자열에 중복 키가 포함 되어 있는 경우이 cmdlet은 마지막 키만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-111">For example, if the JSON string contains duplicate keys, only the last key is used by this cmdlet.</span></span> <span data-ttu-id="2f033-112">아래의 다른 예를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2f033-112">See other examples below.</span></span>

<span data-ttu-id="2f033-113">모든 개체에서 JSON 문자열을 생성 하려면 cmdlet을 사용 `ConvertTo-Json` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-113">To generate a JSON string from any object, use the `ConvertTo-Json` cmdlet.</span></span>

<span data-ttu-id="2f033-114">이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="2f033-115">이 cmdlet은 주석이 있는 JSON을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-115">This cmdlet doesn't support JSON with comments.</span></span>

## <span data-ttu-id="2f033-116">예제</span><span class="sxs-lookup"><span data-stu-id="2f033-116">EXAMPLES</span></span>

### <span data-ttu-id="2f033-117">예제 1: DateTime 개체를 JSON 개체로 변환</span><span class="sxs-lookup"><span data-stu-id="2f033-117">Example 1: Convert a DateTime object to a JSON object</span></span>

<span data-ttu-id="2f033-118">이 명령은 및 cmdlet을 사용 하 여 `ConvertTo-Json` `ConvertFrom-Json` **DateTime** 개체를 cmdlet에서 `Get-Date` JSON 개체로 변환한 다음 **PSCustomObject** 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-118">This command uses the `ConvertTo-Json` and `ConvertFrom-Json` cmdlets to convert a **DateTime** object from the `Get-Date` cmdlet to a JSON object then to a **PSCustomObject**.</span></span>

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

<span data-ttu-id="2f033-119">이 예에서는 cmdlet을 사용 `Select-Object` 하 여 **DateTime** 개체의 모든 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-119">The example uses the `Select-Object` cmdlet to get all of the properties of the **DateTime** object.</span></span> <span data-ttu-id="2f033-120">Cmdlet을 사용 하 여 `ConvertTo-Json` **DateTime** 개체를 json 개체로 서식 지정 된 문자열로 변환 하 고 cmdlet을 사용 하 여 `ConvertFrom-Json` Json 형식 문자열을 **PSCustomObject** 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-120">It uses the `ConvertTo-Json` cmdlet to convert the **DateTime** object to a string formatted as a JSON object and the `ConvertFrom-Json` cmdlet to convert the JSON-formatted string to a **PSCustomObject** object.</span></span>

### <span data-ttu-id="2f033-121">예제 2: 웹 서비스에서 JSON 문자열 가져오기 및 PowerShell 개체로 변환</span><span class="sxs-lookup"><span data-stu-id="2f033-121">Example 2: Get JSON strings from a web service and convert them to PowerShell objects</span></span>

<span data-ttu-id="2f033-122">이 명령은 cmdlet을 사용 하 여 `Invoke-WebRequest` 웹 서비스에서 json 문자열을 가져온 다음 cmdlet을 사용 하 여 `ConvertFrom-Json` json 콘텐츠를 PowerShell에서 관리할 수 있는 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-122">This command uses the `Invoke-WebRequest` cmdlet to get JSON strings from a web service and then it uses the `ConvertFrom-Json` cmdlet to convert JSON content to objects that can be managed in PowerShell.</span></span>

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

<span data-ttu-id="2f033-123">`Invoke-RestMethod`JSON 콘텐츠를 개체로 자동으로 변환 하는 cmdlet을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-123">You can also use the `Invoke-RestMethod` cmdlet, which automatically converts JSON content to objects.</span></span>

### <span data-ttu-id="2f033-124">예제 3: JSON 문자열을 사용자 지정 개체로 변환</span><span class="sxs-lookup"><span data-stu-id="2f033-124">Example 3: Convert a JSON string to a custom object</span></span>

<span data-ttu-id="2f033-125">이 예제에서는 cmdlet을 사용 하 여 `ConvertFrom-Json` JSON 파일을 PowerShell 사용자 지정 개체로 변환 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-125">This example shows how to use the `ConvertFrom-Json` cmdlet to convert a JSON file to a PowerShell custom object.</span></span>

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

<span data-ttu-id="2f033-126">이 명령은 Get-Content cmdlet을 사용 하 여 JSON 파일의 문자열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-126">The command uses Get-Content cmdlet to get the strings in a JSON file.</span></span> <span data-ttu-id="2f033-127">그런 다음 파이프라인 연산자를 사용 하 여 구분 기호로 분리 된 문자열을 cmdlet으로 보냅니다 `ConvertFrom-Json` . 그러면이 cmdlet이 사용자 지정 개체로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-127">Then it uses the pipeline operator to send the delimited string to the `ConvertFrom-Json` cmdlet, which converts it to a custom object.</span></span>

## <span data-ttu-id="2f033-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f033-128">PARAMETERS</span></span>

### <span data-ttu-id="2f033-129">-InputObject</span><span class="sxs-lookup"><span data-stu-id="2f033-129">-InputObject</span></span>

<span data-ttu-id="2f033-130">JSON 개체로 변환할 JSON 문자열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-130">Specifies the JSON strings to convert to JSON objects.</span></span> <span data-ttu-id="2f033-131">문자열이 포함된 변수를 입력하거나 문자열을 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="2f033-132">문자열을로 파이프 할 수도 있습니다 `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="2f033-132">You can also pipe a string to `ConvertFrom-Json`.</span></span>

<span data-ttu-id="2f033-133">**InputObject** 매개 변수는 필수이지만 값이 빈 문자열일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-133">The **InputObject** parameter is required, but its value can be an empty string.</span></span> <span data-ttu-id="2f033-134">입력 개체가 빈 문자열이 면에서 `ConvertFrom-Json` 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-134">When the input object is an empty string, `ConvertFrom-Json` does not generate any output.</span></span> <span data-ttu-id="2f033-135">**InputObject** 값은 일 수 없습니다 `$null` .</span><span class="sxs-lookup"><span data-stu-id="2f033-135">The **InputObject** value cannot be `$null`.</span></span>

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

### <span data-ttu-id="2f033-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f033-136">CommonParameters</span></span>

<span data-ttu-id="2f033-137">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f033-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f033-138">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f033-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f033-139">입력</span><span class="sxs-lookup"><span data-stu-id="2f033-139">INPUTS</span></span>

### <span data-ttu-id="2f033-140">System.String</span><span class="sxs-lookup"><span data-stu-id="2f033-140">System.String</span></span>

<span data-ttu-id="2f033-141">JSON 문자열을로 파이프 할 수 있습니다 `ConvertFrom-Json` .</span><span class="sxs-lookup"><span data-stu-id="2f033-141">You can pipe a JSON string to `ConvertFrom-Json`.</span></span>

## <span data-ttu-id="2f033-142">출력</span><span class="sxs-lookup"><span data-stu-id="2f033-142">OUTPUTS</span></span>

### <span data-ttu-id="2f033-143">PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="2f033-143">PSCustomObject</span></span>

## <span data-ttu-id="2f033-144">참고</span><span class="sxs-lookup"><span data-stu-id="2f033-144">NOTES</span></span>

<span data-ttu-id="2f033-145">`ConvertFrom-Json`Cmdlet은 [JavaScriptSerializer 클래스](/dotnet/api/system.web.script.serialization.javascriptserializer)를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f033-145">The `ConvertFrom-Json` cmdlet is implemented using the [JavaScriptSerializer class](/dotnet/api/system.web.script.serialization.javascriptserializer).</span></span>

## <span data-ttu-id="2f033-146">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2f033-146">RELATED LINKS</span></span>

<span data-ttu-id="2f033-147">[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="2f033-147">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="2f033-148">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="2f033-148">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="2f033-149">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="2f033-149">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="2f033-150">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="2f033-150">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
