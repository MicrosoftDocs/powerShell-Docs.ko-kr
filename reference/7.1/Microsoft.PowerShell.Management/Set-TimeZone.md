---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/18/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-timezone?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TimeZone
ms.openlocfilehash: 618f2ceca435e836a0c733f98533b62dfc86290b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217865"
---
# Set-TimeZone

## 개요
시스템 표준 시간대를 지정 된 표준 시간대로 설정 합니다.

## SYNTAX

### 이름 (기본값)

```
Set-TimeZone [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Set-TimeZone -Id <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Set-TimeZone [-InputObject] <TimeZoneInfo> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## 설명

`Set-TimeZone`Cmdlet은 시스템 표준 시간대를 지정 된 표준 시간대로 설정 합니다.

## 예제

### 예제 1: Id로 표준 시간대 설정

이 예에서는 로컬 컴퓨터의 표준 시간대를 러시아어 표준 시간으로 설정 합니다.

```powershell
Set-TimeZone -Id "Russian Standard Time" -PassThru
```

```Output
Id                         : Russian Standard Time
DisplayName                : (UTC+03:00) Moscow, St. Petersburg
StandardName               : Russia TZ 2 Standard Time
DaylightName               : Russia TZ 2 Daylight Time
BaseUtcOffset              : 03:00:00
SupportsDaylightSavingTime : True
```

### 예제 2: 이름을 기준으로 표준 시간대 설정

이 예에서는 로컬 컴퓨터의 표준 시간대를 러시아어 표준 시간으로 설정 합니다.

```powershell
Set-TimeZone -Name "Russia TZ 2 Standard Time"
```

이전 예제에서 보았듯이 표준 시간대의 **Id** 와 **이름은** 항상 일치 하지 않습니다.
**Name** 매개 변수는 **TimeZoneInfo** 개체의 **standardname** 또는 **daylightname** 속성과 일치 해야 합니다.

## PARAMETERS

### -Id

이 cmdlet이 설정 하는 표준 시간대의 ID를 지정 합니다. 다음 명령을 실행 하 여 표준 시간대 Id의 전체 목록을 가져올 수 있습니다 `Get-TimeZone -ListAvailable` .

```yaml
Type: System.String
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -InputObject

입력으로 사용할 **TimeZoneInfo** 개체를 지정 합니다.

```yaml
Type: System.TimeZoneInfo
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

이 cmdlet이 설정 하는 표준 시간대의 이름을 지정 합니다. 다음 명령을 실행 하 여 표준 시간대 이름의 전체 목록을 가져올 수 있습니다 `Get-TimeZone -ListAvailable` .

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PassThru

작업 중인 항목을 나타내는 개체를 반환합니다. 기본적으로 이 cmdlet은 출력을 생성하지 않습니다.

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

cmdlet을 실행할 경우 발생하는 일을 표시합니다. cmdlet은 실행되지 않습니다.

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

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.string, TimeZoneInfo, System.string

## 출력

## 참고

## 관련 링크

[Get-TimeZone](Get-TimeZone.md)

