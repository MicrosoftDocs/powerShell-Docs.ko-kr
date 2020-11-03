---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/19/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/test-json?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Json
ms.openlocfilehash: 2e3d49700adb8115bf24ae505fbb00c14a774f15
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93211385"
---
# Test-Json

## 개요
문자열이 유효한 JSON 문서 인지 테스트 합니다.

## SYNTAX

```
Test-Json [-Json] <string> [[-Schema] <string>] [<CommonParameters>]
```

## 설명

`Test-Json`Cmdlet은 문자열이 유효한 json (JavaScript Object Notation) 문서 인지 여부를 테스트 하 고, 제공 된 스키마에 대해 json 문서를 선택적으로 확인할 수 있습니다.

그런 다음 확인 된 문자열을 cmdlet과 함께 사용 하 여 json `ConvertFrom-Json` 형식 문자열을 json 개체로 변환할 수 있습니다. json 개체는 PowerShell에서 쉽게 관리 하거나 json 입력에 액세스 하는 다른 프로그램 또는 웹 서비스로 전송 됩니다.

많은 웹 사이트에서는 XML이 아닌 JSON을 사용하여 서버와 웹 기반 앱 간의 통신 데이터를 직렬화합니다.

이 cmdlet은 PowerShell 6.1에서 도입 되었습니다.

## 예제

### 예제 1: 개체가 유효한 JSON 인지 테스트

이 예제에서는 입력 문자열이 유효한 JSON 문서 인지 여부를 테스트 합니다.

```powershell
"{'name': 'Ashley', 'age': 25}" | Test-Json
```

```Output
True
```

### 예제 2: 제공 된 스키마에 대해 개체 테스트

이 예제에서는 JSON 스키마를 포함 하는 문자열을 사용 하 여 입력 문자열과 비교 합니다.

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

이 예에서는 스키마에 **age** 에 대 한 정수가 필요 하지만 테스트 한 JSON 입력에서 문자열 값을 대신 사용 하기 때문에 오류가 발생 합니다.

자세한 내용은 [JSON 스키마](https://json-schema.org/)를 참조 하세요.

## PARAMETERS

### -Json

유효성을 테스트할 JSON 문자열을 지정 합니다. 문자열이 포함된 변수를 입력하거나 문자열을 가져오는 명령 또는 식을 입력합니다. 문자열을로 파이프 할 수도 있습니다 `Test-Json` .

**Json** 매개 변수가 필요 합니다.

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

### -스키마

JSON 입력의 유효성을 검사할 스키마를 지정 합니다. 전달 된 경우 `Test-Json` Json 입력이 **스키마** 매개 변수로 지정 된 사양을 준수 하는지 확인 하 고 입력이 `$True` 제공 된 스키마를 준수 하는 경우에만를 반환 합니다.

자세한 내용은 [JSON 스키마](https://json-schema.org/)를 참조 하세요.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

JSON 문자열을로 파이프 할 수 있습니다 `Test-Json` .

## 출력

### 부울

## 참고

`Test-Json`Cmdlet은 [NJsonSchema 클래스](https://github.com/RSuter/NJsonSchema)를 사용 하 여 구현 됩니다.

## 관련 링크

[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[추가 JSON 스키마 세부 정보](https://json-schema.org/)

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
