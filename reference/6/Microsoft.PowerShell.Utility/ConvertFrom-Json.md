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
# ConvertFrom-Json

## 개요
JSON 형식 문자열을 사용자 지정 개체 또는 해시 테이블로 변환 합니다.

## SYNTAX

```
ConvertFrom-Json [-InputObject] <String> [-AsHashtable] [-Depth <Int32>] [<CommonParameters>]
```

## 설명

`ConvertFrom-Json`Cmdlet JavaScript Object Notation (json) 형식 문자열을 json 문자열의 각 필드에 대 한 속성이 있는 사용자 지정 **PSCustomObject** 개체로 변환 합니다. JSON은 주로 웹 사이트에서 개체의 텍스트 표현을 제공하는 데 사용됩니다. JSON 표준은 **PSCustomObject** 에서 금지 된 사용을 금지 하지 않습니다. 예를 들어 JSON 문자열에 중복 키가 포함 되어 있는 경우이 cmdlet은 마지막 키만 사용 합니다. 아래의 다른 예를 참조 하세요.

모든 개체에서 JSON 문자열을 생성 하려면 cmdlet을 사용 `ConvertTo-Json` 합니다.

이 cmdlet은 PowerShell 3.0에서 도입 되었습니다.

> [!NOTE]
> PowerShell 6부터이 cmdlet은 주석을 사용 하 여 JSON을 지원 합니다. 수락 된 주석은 두 개의 슬래시 ()로 시작 `//` 합니다. 주석은 데이터에 표시 되지 않으며 PowerShell 5.1에서와 같이 데이터를 손상 시키거나 오류를 throw 하지 않고 파일에 기록할 수 있습니다.

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

### 예제 4: JSON 문자열을 해시 테이블로 변환

이 명령은 `-AsHashtable` 스위치가 명령의 제한을 극복할 수 있는 예를 보여 줍니다.

```powershell
'{ "key":"value1", "Key":"value2" }' | ConvertFrom-Json -AsHashtable
```

JSON 문자열에는 대/소문자만 다른 키를 가진 두 개의 키 값 쌍이 포함 되어 있습니다. 스위치가 없으면 명령에서 오류를 throw 합니다.

## PARAMETERS

### -AsHashtable

JSON을 해시 테이블 개체로 변환 합니다. 이 스위치는 PowerShell 6.0에서 도입 되었습니다. Cmdlet에 대 한 몇 가지 제한 사항을 해결할 수 있는 몇 가지 시나리오가 있습니다 `ConvertFrom-Json` .

- JSON에 대/소문자만 다른 키가 있는 목록이 포함 된 경우 스위치가 없으면 해당 키는 동일한 키로 표시 되므로 마지막 항목만 사용 됩니다.
- JSON에 빈 문자열인 키가 포함 되어 있으면입니다. 스위치를 사용 하지 않을 경우 cmdlet은 오류를 throw `PSCustomObject` 합니다. 단,이는 해시 테이블의 경우에는 허용 되지 않기 때문입니다. 이 문제가 발생할 수 있는 예제 사용 사례는 `project.lock.json` 파일입니다.
- 특정 데이터 구조에 대해 해시 테이블을 더 빠르게 처리할 수 있습니다.

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

### -깊이

JSON 입력에 허용 되는 최대 깊이를 가져오거나 설정 합니다. 기본적으로 1024입니다.

이 매개 변수는 PowerShell 6.2에서 도입 되었습니다.

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

### System.Collections.Hashtable

## 참고

이 cmdlet은 [newtonsoft.json Json.NET](https://www.newtonsoft.com/json)를 사용 하 여 구현 됩니다.

PowerShell 6부터는 `ConvertTo-Json` 타임 스탬프로 형식이 지정 된 문자열을 **DateTime** 값으로 변환 하려고 합니다. 변환 된 값은 속성이 다음과 같이 `[datetime]` 설정 된 인스턴스입니다 `Kind` .

- `Unspecified`입력 문자열에 표준 시간대 정보가 없는 경우입니다.
- `Utc`표준 시간대 정보가 후행 인 경우 `Z` 입니다.
- `Local`표준 시간대 정보가와 같은 후행 UTC _오프셋_ 으로 지정 된 경우 `+02:00` 입니다. 오프셋은 호출자의 구성 된 표준 시간대로 적절 하 게 변환 됩니다. 기본 출력 형식은 원래 표준 시간대 오프셋을 나타내지 않습니다.

## 관련 링크

[JavaScript 및 .NET의 JavaScript Object Notation (JSON) 소개](/previous-versions/dotnet/articles/bb299886(v=msdn.10))

[ConvertTo-Json](ConvertTo-Json.md)

[Invoke-WebRequest](Invoke-WebRequest.md)

[Invoke-RestMethod](Invoke-RestMethod.md)
