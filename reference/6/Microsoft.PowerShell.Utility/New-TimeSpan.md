---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/1/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-timespan?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-TimeSpan
ms.openlocfilehash: 1cfc2cdf4aaf15d54485fb04741f2bbca65fd3be
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216290"
---
# New-TimeSpan

## 개요
TimeSpan 개체를 만듭니다.

## SYNTAX

### 날짜 (기본값)

```
New-TimeSpan [[-Start] <DateTime>] [[-End] <DateTime>] [<CommonParameters>]
```

### 시간

```
New-TimeSpan [-Days <Int32>] [-Hours <Int32>] [-Minutes <Int32>] [-Seconds <Int32>] [<CommonParameters>]
```

## 설명

`New-TimeSpan`Cmdlet은 시간 간격을 나타내는 **TimeSpan** 개체를 만듭니다.
**TimeSpan** 개체를 사용 하 여 **DateTime** 개체에서 시간을 더하거나 뺄 수 있습니다.

매개 변수를 사용 하지 않으면 `New-TimeSpan` 명령에서 시간 간격을 0으로 나타내는 **TimeSpan** 개체를 반환 합니다.

## 예제

### 예제 1: 지정 된 기간 동안 TimeSpan 개체 만들기

이 명령은 기간이 1 시간에서 25 분인 **TimeSpan** 개체를 만들어 라는 변수에 저장 `$TimeSpan` 합니다. **TimeSpan** 개체의 표현을 표시 합니다.

```powershell
$TimeSpan = New-TimeSpan -Hours 1 -Minutes 25
$TimeSpan
```

```Output
Days              : 0
Hours             : 1
Minutes           : 25
Seconds           : 0
Milliseconds      : 0
Ticks             : 51000000000
TotalDays         : 0.0590277777777778
TotalHours        : 1.41666666666667
TotalMinutes      : 85
TotalSeconds      : 5100
TotalMilliseconds : 5100000
```

### 예제 2: 시간 간격에 대 한 TimeSpan 개체 만들기

이 예제에서는 명령이 실행 된 시간과 1 월 2010 1 일 사이의 간격을 나타내는 새 **TimeSpan** 개체를 만듭니다.

**Start** 매개 변수의 기본값이 현재 날짜 및 시간 이므로이 명령에는 **start** 매개 변수가 필요 하지 않습니다.

```powershell
New-TimeSpan -End (Get-Date -Year 2010 -Month 1 -Day 1)
```

### 예 3: 현재 날짜 로부터 90 일을 가져옵니다.

```powershell
$90days = New-TimeSpan -Days 90
(Get-Date) + $90days
```

이 명령은 현재 날짜부터 90일 후의 날짜를 반환합니다.

### 예제 4: 파일이 업데이트 된 후 TimeSpan 검색

이 명령은 [about_remote](../Microsoft.PowerShell.Core/About/about_Remote.md) 도움말 파일이 마지막으로 업데이트 된 이후 경과 된 시간을 알려 줍니다.
모든 파일 또는 **LastWriteTime** 속성이 있는 다른 모든 개체에서이 명령 형식을 사용할 수 있습니다.

이 명령은의 **Start** 매개 변수가 `New-TimeSpan` **LastWriteTime** 의 별칭을 포함 하기 때문에 작동 합니다. **LastWriteTime** 속성이 있는 개체를로 파이프 하면 `New-TimeSpan` PowerShell에서 **LastWriteTime** 속성 값을 **Start** 매개 변수 값으로 사용 합니다.

```powershell
Get-ChildItem $PSHOME\en-us\about_remote.help.txt | New-TimeSpan
```

```Output
Days              : 321
Hours             : 21
Minutes           : 59
Seconds           : 22
Milliseconds      : 312
Ticks             : 278135623127728
TotalDays         : 321.916230471907
TotalHours        : 7725.98953132578
TotalMinutes      : 463559.371879547
TotalSeconds      : 27813562.3127728
TotalMilliseconds : 27813562312.7728
```

## PARAMETERS

### -Days

시간 범위의 날짜를 지정 합니다.
기본값은 0입니다.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -끝

시간 범위의 끝을 지정 합니다.
기본값이 현재 날짜와 시간입니다.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: False
Position: 1
Default value: Current date and time
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -시간

시간 범위의 시간을 지정 합니다.
기본값은 영입니다.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -분

시간 범위의 분을 지정 합니다.
기본값은 0입니다.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -초

시간 범위의 길이 (초)를 지정 합니다.
기본값은 0입니다.

```yaml
Type: System.Int32
Parameter Sets: Time
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -시작

시간 범위의 시작을 지정 합니다.
날짜 및 시간을 나타내는 문자열 (예: "3/15/09") 또는 **DateTime** 개체 (예: 명령)를 입력 `Get-Date` 합니다. 기본값이 현재 날짜와 시간입니다.

**Start** 또는 해당 별칭인 **LastWriteTime** 을 사용할 수 있습니다.
**LastWriteTime** 별칭을 사용 하면 파일 시스템의 파일과 같이 **LastWriteTime** 속성이 있는 개체 `[System.Io.FileIO]` 를의 **시작** 매개 변수로 파이프 할 수 있습니다 `New-TimeSpan` .

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases: LastWriteTime

Required: False
Position: 0
Default value: Current date and time
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.DateTime

시작 시간을 나타내는 **DateTime** 개체를로 파이프 할 수 있습니다 `New-TimeSpan` .

## 출력

### System.TimeSpan

`New-TimeSpan` 시간 범위를 나타내는 개체를 반환 합니다.

## 참고

## 관련 링크

[가져오기-날짜](Get-Date.md)

[Set-Date](Set-Date.md)
