---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertto-json?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertTo-Json
ms.openlocfilehash: b91d3b7cbf86c7ea827539903b2e8373cdfdac72
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93214097"
---
# ConvertTo-Json

## 개요
개체를 JSON 형식 문자열로 변환합니다.

## SYNTAX

```
ConvertTo-Json [-InputObject] <Object> [-Depth <Int32>] [-Compress]
 [<CommonParameters>]
```

## 설명

`ConvertTo-Json`Cmdlet은 모든 .net 개체를 JSON (JavaScript Object Notation) 형식의 문자열로 변환 합니다. 속성은 필드 이름으로 변환되고, 필드 값은 속성 값으로 변환되고, 메서드는 제거됩니다.

그런 다음 cmdlet을 사용 `ConvertFrom-Json` 하 여 json 형식 문자열을 PowerShell에서 쉽게 관리 되는 json 개체로 변환할 수 있습니다.

많은 웹 사이트에서는 XML이 아닌 JSON을 사용하여 서버와 웹 기반 앱 간의 통신 데이터를 직렬화합니다.

이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.

## 예제

### 예 1

```powershell
PS C:\> (Get-UICulture).Calendar | ConvertTo-Json
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

이 명령은 cmdlet을 사용 하 여 `ConvertTo-Json` GregorianCalendar 개체를 JSON 형식 문자열로 변환 합니다.

### 예제 2

```powershell
@{Account="User01";Domain="Domain01";Admin="True"} | ConvertTo-Json -Compress
```

```Output
{"Domain":"Domain01","Account":"User01","Admin":"True"}
```

이 명령은의 **압축** 매개 변수를 사용한 결과를 보여 줍니다 `ConvertTo-Json` . 비교는 문자열의 모양에만 영향을 줄 뿐 유효성에는 영향을 주지 않습니다.

### 예제 3

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

이 예에서는 cmdlet을 사용 하 여 `ConvertTo-Json` **시스템의 DateTime** 개체를 cmdlet에서 `Get-Date` JSON 형식 문자열로 변환 합니다. 이 명령은 cmdlet을 사용 `Select-Object` 하 여 `*` **DateTime** 개체의 속성 ()을 모두 가져옵니다. 출력은 반환 된 JSON 문자열을 보여 줍니다 `ConvertTo-Json` .

### 예제 4

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

이 예제에서는 및 cmdlet을 사용 하 여 `ConvertTo-Json` `ConvertFrom-Json` 개체를 json 문자열 및 json 개체로 변환 하는 방법을 보여 줍니다.

## PARAMETERS

### -압축

출력 문자열에서 공백과 들여쓰기 서식을 생략합니다.

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

### -깊이

JSON 표시에 포함되는 포함 개체의 수준을 지정합니다. 기본값은 2입니다.

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

### -InputObject

JSON 형식으로 변환할 개체를 지정합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요. 개체를로 파이프 할 수도 있습니다 `ConvertTo-Json` .

**InputObject** 매개 변수는 필수 이지만 해당 값은 null ( `$null` ) 또는 빈 문자열일 수 있습니다.
입력 개체가 인 경우은 `$null` `ConvertTo-Json` 출력을 생성 하지 않습니다. 입력 개체가 빈 문자열이 면에서 `ConvertTo-Json` 빈 문자열을 반환 합니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.Object

모든 개체를로 파이프 할 수 있습니다 `ConvertTo-Json` .

## 출력

### System.String

## 참고

`ConvertTo-Json`Cmdlet은 [JavaScriptSerializer 클래스](/dotnet/api/system.web.script.serialization.javascriptserializer)를 사용 하 여 구현 됩니다.

## 관련 링크

[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertFrom-Json](ConvertFrom-Json.md)

[Get-Content](../Microsoft.PowerShell.Management/Get-Content.md)

[Get-UICulture](Get-UICulture.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
