---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 4/30/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-date?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Date
ms.openlocfilehash: 4a7deaeb0570516c5d0cb1be704f0e1cb7bfe13c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216274"
---
# Set-Date

## 개요
컴퓨터의 시스템 시간을 지정한 시간으로 변경합니다.

## SYNTAX

### 날짜 (기본값)

```
Set-Date [-Date] <DateTime> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Adjust

```
Set-Date [-Adjust] <TimeSpan> [-DisplayHint <DisplayHintType>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-Date`Cmdlet은 컴퓨터의 시스템 날짜 및 시간을 지정한 날짜 및 시간으로 변경 합니다.
문자열을 입력 하거나 **DateTime** 또는 **TimeSpan** 개체를에 전달 하 여 새 날짜 및/또는 시간을 지정할 수 있습니다 `Set-Date` . 새 날짜 또는 시간을 지정 하려면 **date** 매개 변수를 사용 합니다.
변경 간격을 지정 하려면 **조정** 매개 변수를 사용 합니다.

## 예제

### 예 1: 시스템 날짜에 3 일 추가

이 명령은 현재 시스템 날짜에 3일을 더합니다.
시간에는 영향을 주지 않습니다.
이 명령은 **date** 매개 변수를 사용 하 여 날짜를 지정 합니다.

이 `Get-Date` cmdlet은 현재 날짜를 **DateTime** 개체로 반환 합니다. **Datetime** 개체의 **AddDays** 메서드는 지정 된 일 수 (3)를 현재 **DateTime** 개체에 추가 합니다.

```powershell
Set-Date -Date (Get-Date).AddDays(3)
```

### 예 2: 시스템 클록을 10 분 뒤로 설정

이 예에서는 현재 시스템 시간을 10 분 뒤로 설정 합니다.

**조정** 매개 변수를 사용 하 여 로캘의 표준 시간 형식에서 변경 간격 (10 분을 뺀 값)을 지정할 수 있습니다.

**Displayhint** 매개 변수는 PowerShell에 시간만 표시 하도록 지시 하지만을 반환 하는 **DateTime** 개체에는 영향을 주지 않습니다 `Set-Date` .

```powershell
Set-Date -Adjust -0:10:0 -DisplayHint Time
```

### 예제 3: 날짜 및 시간을 변수 값으로 설정

이 명령은 로컬 컴퓨터의 시스템 날짜 및 시간을 변수에 저장 된 날짜 및 시간으로 변경 합니다 `$T` . 첫 번째 명령은 날짜를 가져와에 저장 `$T` 합니다.

두 번째 명령은 **Date** 매개 변수를 사용 하 여의 **DateTime** 개체를 cmdlet에 전달 합니다 `$T` `Set-Date` .

```powershell
$T = Get-Date
Set-Date -Date $T
```

### 예제 4: 시스템 클록에 90 분 추가

이 명령은 로컬 컴퓨터의 시스템 시간을 90분 후로 설정합니다.

첫 번째 명령은 cmdlet을 사용 하 여 `New-TimeSpan` 90 분 간격의 **TimeSpan** 개체를 만든 다음 변수에 저장 합니다 `$90mins` .

두 번째 명령은의 **조정** 매개 변수를 사용 하 여 `Set-Date` 변수에서 **TimeSpan** 개체의 값으로 날짜를 조정 합니다 `$90mins` .

```powershell
$90mins = New-TimeSpan -Minutes 90
Set-Date -Adjust $90mins
```

## PARAMETERS

### -조정

이 cmdlet이 현재 날짜 및 시간에서 추가 하거나 빼는 값을 지정 합니다.
로캘에 대 한 표준 날짜 및 시간 형식 조정을 입력 하거나, **조정** 매개 변수를 사용 하 여에서로 **TimeSpan** 개체를 전달할 수 있습니다 `New-TimeSpan` `Set-Date` .

```yaml
Type: System.TimeSpan
Parameter Sets: Adjust
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -날짜

날짜 및 시간을 지정한 값으로 변경합니다.
새 날짜를 간단한 날짜 형식으로 입력하고 시간을 해당 로캘의 표준 시간 형식으로 입력할 수 있습니다. 또는에서 **DateTime** 개체를 전달할 수 있습니다 `Get-Date` .

날짜를 지정 하 고 시간을 지정 하지 않으면 `Set-Date` 지정 된 날짜의 자정으로 시간을 변경 합니다. 시간만 지정할 경우 날짜는 변경되지 않습니다.

```yaml
Type: System.DateTime
Parameter Sets: Date
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -DisplayHint

표시 되는 날짜 및 시간 요소를 지정 합니다. 이 매개 변수에 허용 되는 값은 다음과 같습니다.

- 날짜
  날짜만 표시 합니다.
- 시간.
  시간만 표시 합니다.
- 날짜/시간.
  날짜와 시간을 표시 합니다.

이 매개 변수는 표시에만 영향을 주고
을 검색 하는 **DateTime** 개체에는 영향을 주지 않습니다 `Get-Date` .

```yaml
Type: Microsoft.PowerShell.Commands.DisplayHintType
Parameter Sets: (All)
Aliases:
Accepted values: Date, Time, DateTime

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm

cmdlet을 실행하기 전에 확인을 요청합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

cmdlet을 실행할 경우 발생하는 일을 표시합니다.
cmdlet은 실행되지 않습니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md)를 참조하세요.

## 입력

### System.DateTime

날짜를로 파이프 할 수 있습니다 `Set-Date` .

## 출력

### System.DateTime

`Set-Date` 설정 된 날짜를 나타내는 개체를 반환 합니다.

## 참고

- 컴퓨터의 날짜 및 시간을 변경할 때이 cmdlet을 사용 하면 주의 해야 합니다. 이 변경 내용으로 인해 컴퓨터가 날짜 또는 시간에 의해 트리거되는 시스템 전체 이벤트 및 업데이트를 받지 못할 수 있습니다. 오류를 방지 하려면 **WhatIf** 및 **Confirm** 매개 변수를 사용 합니다.
- **DateTime** **TimeSpan** `Set-Date` **AddDays** , **addmonths** 및 **fromfiletime** 과 같이와 함께 사용 되는 DateTime 및 TimeSpan 개체에 표준 .net 메서드를 사용할 수 있습니다. 자세한 내용은 [DateTime 메서드](/dotnet/api/system.datetime) 및를 참조 하세요.

  MSDN library의 [TimeSpan 메서드](/dotnet/api/system.timespan) .

## 관련 링크

[가져오기-날짜](Get-Date.md)

[New-TimeSpan](New-TimeSpan.md)
