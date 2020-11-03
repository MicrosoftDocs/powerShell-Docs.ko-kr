---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Json
ms.openlocfilehash: f2159a2de3432aec14fb395b93ed476f349616a8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214145"
---
# ConvertFrom-Json

## 개요
JSON 형식 문자열을 사용자 지정 개체로 변환합니다.

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [<CommonParameters>]
```

## 설명

`ConvertFrom-Json`Cmdlet JavaScript Object Notation (json) 형식 문자열을 json 문자열의 각 필드에 대 한 속성이 있는 사용자 지정 **PSCustomObject** 개체로 변환 합니다. JSON은 주로 웹 사이트에서 개체의 텍스트 표현을 제공하는 데 사용됩니다. JSON 표준은 **PSCustomObject** 에서 금지 된 사용을 금지 하지 않습니다. 예를 들어 JSON 문자열에 중복 키가 포함 되어 있는 경우이 cmdlet은 마지막 키만 사용 합니다. 아래의 다른 예를 참조 하세요.

모든 개체에서 JSON 문자열을 생성 하려면 cmdlet을 사용 `ConvertTo-Json` 합니다.

이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.

> [!NOTE]
> 이 cmdlet은 주석이 있는 JSON을 지원 하지 않습니다.

## 예제

### 예제 1: DateTime 개체를 JSON 개체로 변환

이 명령은 및 cmdlet을 사용 하 여 `ConvertTo-Json` `ConvertFrom-Json` **DateTime** 개체를 cmdlet에서 `Get-Date` JSON 개체로 변환한 다음 **PSCustomObject** 로 변환 합니다.

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

이 예에서는 cmdlet을 사용 `Select-Object` 하 여 **DateTime** 개체의 모든 속성을 가져옵니다. Cmdlet을 사용 하 여 `ConvertTo-Json` **DateTime** 개체를 json 개체로 서식 지정 된 문자열로 변환 하 고 cmdlet을 사용 하 여 `ConvertFrom-Json` Json 형식 문자열을 **PSCustomObject** 개체로 변환 합니다.

### 예제 2: 웹 서비스에서 JSON 문자열 가져오기 및 PowerShell 개체로 변환

이 명령은 cmdlet을 사용 하 여 `Invoke-WebRequest` 웹 서비스에서 json 문자열을 가져온 다음 cmdlet을 사용 하 여 `ConvertFrom-Json` json 콘텐츠를 PowerShell에서 관리할 수 있는 개체로 변환 합니다.

```powershell
# Ensures that Invoke-WebRequest uses TLS 1.2
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$j = Invoke-WebRequest 'https://api.github.com/repos/PowerShell/PowerShell/issues' | ConvertFrom-Json
```

`Invoke-RestMethod`JSON 콘텐츠를 개체로 자동으로 변환 하는 cmdlet을 사용할 수도 있습니다.

### 예제 3: JSON 문자열을 사용자 지정 개체로 변환

이 예제에서는 cmdlet을 사용 하 여 `ConvertFrom-Json` JSON 파일을 PowerShell 사용자 지정 개체로 변환 하는 방법을 보여 줍니다.

```powershell
Get-Content JsonFile.JSON | ConvertFrom-Json
```

이 명령은 Get-Content cmdlet을 사용 하 여 JSON 파일의 문자열을 가져옵니다. 그런 다음 파이프라인 연산자를 사용 하 여 구분 기호로 분리 된 문자열을 cmdlet으로 보냅니다 `ConvertFrom-Json` . 그러면이 cmdlet이 사용자 지정 개체로 변환 합니다.

## PARAMETERS

### -InputObject

JSON 개체로 변환할 JSON 문자열을 지정합니다. 문자열이 포함된 변수를 입력하거나 문자열을 가져오는 명령 또는 식을 입력합니다. 문자열을로 파이프 할 수도 있습니다 `ConvertFrom-Json` .

**InputObject** 매개 변수는 필수이지만 값이 빈 문자열일 수 있습니다. 입력 개체가 빈 문자열이 면에서 `ConvertFrom-Json` 출력을 생성 하지 않습니다. **InputObject** 값은 일 수 없습니다 `$null` .

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

JSON 문자열을로 파이프 할 수 있습니다 `ConvertFrom-Json` .

## 출력

### PSCustomObject

## 참고

`ConvertFrom-Json`Cmdlet은 [JavaScriptSerializer 클래스](/dotnet/api/system.web.script.serialization.javascriptserializer)를 사용 하 여 구현 됩니다.

## 관련 링크

[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
