---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 79cf0d9a8107cbf843eba5c58e4b4e9ad30ad285
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93211753"
---
# <span data-ttu-id="97017-103">Test-Json</span><span class="sxs-lookup"><span data-stu-id="97017-103">Test-Json</span></span>

## <span data-ttu-id="97017-104">개요</span><span class="sxs-lookup"><span data-stu-id="97017-104">SYNOPSIS</span></span>
<span data-ttu-id="97017-105">문자열이 유효한 JSON 문서 인지 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-105">Tests whether a string is a valid JSON document</span></span>

## <span data-ttu-id="97017-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="97017-106">SYNTAX</span></span>

### <span data-ttu-id="97017-107">__AllParameterSets (기본값)</span><span class="sxs-lookup"><span data-stu-id="97017-107">__AllParameterSets (Default)</span></span>
```
Test-Json [-Json] <String> [<CommonParameters>]
```

### <span data-ttu-id="97017-108">SchemaString</span><span class="sxs-lookup"><span data-stu-id="97017-108">SchemaString</span></span>
```
Test-Json [-Json] <String> [[-Schema] <String>] [<CommonParameters>]
```

### <span data-ttu-id="97017-109">SchemaFile</span><span class="sxs-lookup"><span data-stu-id="97017-109">SchemaFile</span></span>
```
Test-Json [-Json] <String> [-SchemaFile <String>] [<CommonParameters>]
```

## <span data-ttu-id="97017-110">설명</span><span class="sxs-lookup"><span data-stu-id="97017-110">DESCRIPTION</span></span>

<span data-ttu-id="97017-111">`Test-Json`Cmdlet은 문자열이 유효한 json (JavaScript Object Notation) 문서 인지 여부를 테스트 하 고, 제공 된 스키마에 대해 json 문서를 선택적으로 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97017-111">The `Test-Json` cmdlet tests whether a string is a valid JavaScript Object Notation (JSON) document and can optionally verify that JSON document against a provided schema.</span></span>

<span data-ttu-id="97017-112">그런 다음 확인 된 문자열을 cmdlet과 함께 사용 하 여 json `ConvertFrom-Json` 형식 문자열을 json 개체로 변환할 수 있습니다. json 개체는 PowerShell에서 쉽게 관리 하거나 json 입력에 액세스 하는 다른 프로그램 또는 웹 서비스로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97017-112">The verified string can then be used with the `ConvertFrom-Json` cmdlet convert a JSON-formatted string to a JSON object, which is easily managed in PowerShell or sent to another program or web service that access JSON input.</span></span>

<span data-ttu-id="97017-113">많은 웹 사이트에서는 XML이 아닌 JSON을 사용하여 서버와 웹 기반 앱 간의 통신 데이터를 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-113">Many web sites use JSON instead of XML to serialize data for communication between servers and web-based apps.</span></span>

<span data-ttu-id="97017-114">이 cmdlet은 PowerShell 6.1에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97017-114">This cmdlet was introduced in PowerShell 6.1</span></span>

## <span data-ttu-id="97017-115">예제</span><span class="sxs-lookup"><span data-stu-id="97017-115">EXAMPLES</span></span>

### <span data-ttu-id="97017-116">예제 1: 개체가 유효한 JSON 인지 테스트</span><span class="sxs-lookup"><span data-stu-id="97017-116">Example 1: Test if an object is valid JSON</span></span>

<span data-ttu-id="97017-117">이 예제에서는 입력 문자열이 유효한 JSON 문서 인지 여부를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-117">This example tests whether the input string is a valid JSON document.</span></span>

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### <span data-ttu-id="97017-118">예제 2: 제공 된 스키마에 대해 개체 테스트</span><span class="sxs-lookup"><span data-stu-id="97017-118">Example 2: Test an object against a provided schema</span></span>

<span data-ttu-id="97017-119">이 예제에서는 JSON 스키마를 포함 하는 문자열을 사용 하 여 입력 문자열과 비교 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-119">This example takes a string containing a JSON schema and compares it to an input string.</span></span>

```powershell
$schema = @'
{
  "definitions": {},
  "$schema": "http://json-schema.org/draft-07/schema#",
  "$id": "http://example.com/root.json",
  "type": "object",
  "title": "The Root Schema",
  "required": [
    "name",
    "age"
  ],
  "properties": {
    "name": {
      "$id": "#/properties/name",
      "type": "string",
      "title": "The Name Schema",
      "default": "",
      "examples": [
        "Ashley"
      ],
      "pattern": "^(.*)$"
    },
    "age": {
      "$id": "#/properties/age",
      "type": "integer",
      "title": "The Age Schema",
      "default": 0,
      "examples": [
        25
      ]
    }
  }
}
'@
"{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
```

```Output
Test-Json : IntegerExpected: #/age
At line:1 char:37
+ "{'name': 'Ashley', 'age': '25'}" | Test-Json -Schema $schema
+                                     ~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : InvalidData: (:) [Test-Json], Exception
+ FullyQualifiedErrorId : InvalidJsonAgainstSchema,Microsoft.PowerShell.Commands.TestJsonCommand
False
```

<span data-ttu-id="97017-120">이 예에서는 스키마에 **age** 에 대 한 정수가 필요 하지만 테스트 한 JSON 입력에서 문자열 값을 대신 사용 하기 때문에 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-120">In this example, we get an error because the schema expects an integer for **age** but the JSON input we tested uses a string value instead.</span></span>

<span data-ttu-id="97017-121">자세한 내용은 [JSON 스키마](https://json-schema.org/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97017-121">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

### <span data-ttu-id="97017-122">예제 3: 파일에서 스키마에 대 한 개체 테스트</span><span class="sxs-lookup"><span data-stu-id="97017-122">Example 3: Test an object against a schema from file</span></span>

<span data-ttu-id="97017-123">JSON 스키마는 키워드를 사용 하 여 정의를 참조할 수 있습니다 `$ref` .</span><span class="sxs-lookup"><span data-stu-id="97017-123">JSON schema can reference definitions using `$ref` keyword.</span></span> <span data-ttu-id="97017-124">는 `$ref` 다른 파일을 참조 하는 URI로 확인 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97017-124">The `$ref` can resolve to a URI that references another file.</span></span> <span data-ttu-id="97017-125">`SchemaFile`매개 변수는 json 스키마 파일의 리터럴 경로를 허용 하며 이러한 스키마에 대해 json 파일의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97017-125">The `SchemaFile` parameter accepts literal path to the JSON schema file and allows JSON files to be validated against such schemas.</span></span>

<span data-ttu-id="97017-126">이 예제에서는를 `schema.json` 참조 하는 파일이 있습니다 `definitions.json` .</span><span class="sxs-lookup"><span data-stu-id="97017-126">In this example we have `schema.json` file which references `definitions.json`.</span></span>

```powershell
PS> Get-Content schema.json

{
  "description":"A person",
  "type":"object",
  "properties":{
    "name":{
      "$ref":"definitions.json#/definitions/name"
    },
    "hobbies":{
      "$ref":"definitions.json#/definitions/hobbies"
    }
  }
}

PS> Get-Content definitions.json

{
  "definitions":{
    "name":{
      "type":"string"
    },
    "hobbies":{
      "type":"array",
      "items":{
        "type":"string"
      }
    }
  }
}

'{"name": "James", "hobbies": [".NET", "Blogging"]}' | Test-Json -SchemaFile 'schema.json'
```

```Output
True
```

<span data-ttu-id="97017-127">자세한 내용은 [복합 스키마 구조화](https://json-schema.org/understanding-json-schema/structuring.html)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97017-127">For more information, see [Structuring a complex schema](https://json-schema.org/understanding-json-schema/structuring.html).</span></span>

## <span data-ttu-id="97017-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="97017-128">PARAMETERS</span></span>

### <span data-ttu-id="97017-129">-Json</span><span class="sxs-lookup"><span data-stu-id="97017-129">-Json</span></span>

<span data-ttu-id="97017-130">유효성을 테스트할 JSON 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-130">Specifies the JSON string to test for validity.</span></span> <span data-ttu-id="97017-131">문자열이 포함된 변수를 입력하거나 문자열을 가져오는 명령 또는 식을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-131">Enter a variable that contains the string, or type a command or expression that gets the string.</span></span> <span data-ttu-id="97017-132">문자열을로 파이프 할 수도 있습니다 `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="97017-132">You can also pipe a string to `Test-Json`.</span></span>

<span data-ttu-id="97017-133">**Json** 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-133">The **Json** parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="97017-134">-스키마</span><span class="sxs-lookup"><span data-stu-id="97017-134">-Schema</span></span>

<span data-ttu-id="97017-135">JSON 입력의 유효성을 검사할 스키마를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-135">Specifies a Schema to validate the JSON input against.</span></span> <span data-ttu-id="97017-136">전달 된 경우 `Test-Json` Json 입력이 **스키마** 매개 변수로 지정 된 사양을 준수 하는지 확인 하 고 입력이 `$True` 제공 된 스키마를 준수 하는 경우에만를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-136">If passed `Test-Json` will validate that the Json input conforms to the spec specified by the **Schema** parameter and return `$True` only if the input conforms to the provided Schema.</span></span>

<span data-ttu-id="97017-137">자세한 내용은 [JSON 스키마](https://json-schema.org/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97017-137">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: SchemaString
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97017-138">-SchemaFile</span><span class="sxs-lookup"><span data-stu-id="97017-138">-SchemaFile</span></span>

<span data-ttu-id="97017-139">JSON 입력의 유효성을 검사 하는 데 사용 되는 스키마 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-139">Specifies a schema file used to validate the JSON input.</span></span> <span data-ttu-id="97017-140">사용 되는 경우 `Test-Json` 는 `$True` JSON 입력이 **schemafile** 매개 변수로 지정 된 파일에 정의 된 스키마를 준수 하는 경우에만를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97017-140">When used, the `Test-Json` returns `$True` only if the JSON input conforms to the Schema defined in the file specified by the **SchemaFile** parameter.</span></span>

<span data-ttu-id="97017-141">자세한 내용은 [JSON 스키마](https://json-schema.org/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97017-141">For more information, see [JSON Schema](https://json-schema.org/).</span></span>

```yaml
Type: System.String
Parameter Sets: SchemaFile
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="97017-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="97017-142">CommonParameters</span></span>

<span data-ttu-id="97017-143">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="97017-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="97017-144">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97017-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="97017-145">입력</span><span class="sxs-lookup"><span data-stu-id="97017-145">INPUTS</span></span>

### <span data-ttu-id="97017-146">System.String</span><span class="sxs-lookup"><span data-stu-id="97017-146">System.String</span></span>

<span data-ttu-id="97017-147">JSON 문자열을로 파이프 할 수 있습니다 `Test-Json` .</span><span class="sxs-lookup"><span data-stu-id="97017-147">You can pipe a JSON string to `Test-Json`.</span></span>

## <span data-ttu-id="97017-148">출력</span><span class="sxs-lookup"><span data-stu-id="97017-148">OUTPUTS</span></span>

### <span data-ttu-id="97017-149">부울</span><span class="sxs-lookup"><span data-stu-id="97017-149">Boolean</span></span>

## <span data-ttu-id="97017-150">참고</span><span class="sxs-lookup"><span data-stu-id="97017-150">NOTES</span></span>

<span data-ttu-id="97017-151">`Test-Json`Cmdlet은 [NJsonSchema 클래스](https://github.com/RSuter/NJsonSchema)를 사용 하 여 구현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97017-151">The `Test-Json` cmdlet is implemented by using the [NJsonSchema Class](https://github.com/RSuter/NJsonSchema).</span></span>

## <span data-ttu-id="97017-152">관련 링크</span><span class="sxs-lookup"><span data-stu-id="97017-152">RELATED LINKS</span></span>

<span data-ttu-id="97017-153">[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="97017-153">[An Introduction to JavaScript Object Notation (JSON) in JavaScript and .NET](/previous-versions/dotnet/articles/bb299886(v=msdn.10))</span></span>

[<span data-ttu-id="97017-154">추가 JSON 스키마 세부 정보</span><span class="sxs-lookup"><span data-stu-id="97017-154">Additional JSON Schema Details</span></span>](https://json-schema.org/)

[<span data-ttu-id="97017-155">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="97017-155">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="97017-156">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="97017-156">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)

[<span data-ttu-id="97017-157">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="97017-157">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)
