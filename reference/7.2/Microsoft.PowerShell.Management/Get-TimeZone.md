---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-timezone?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TimeZone
ms.openlocfilehash: 22034eeac6988478a5f2ff87b2582cc5e1acc1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599958"
---
# Get-TimeZone

## 개요
현재 표준 시간대 또는 사용 가능한 표준 시간대 목록을 가져옵니다.

## SYNTAX

### 이름 (기본값)

```
Get-TimeZone [[-Name] <String[]>] [<CommonParameters>]
```

### Id

```
Get-TimeZone -Id <String[]> [<CommonParameters>]
```

### ListAvailable

```
Get-TimeZone [-ListAvailable] [<CommonParameters>]
```

## 설명

**표준** 시간대 cmdlet은 현재 표준 시간대 또는 사용 가능한 표준 시간대 목록을 가져옵니다.

## 예제

### 예 1: 현재 표준 시간대 가져오기

```
PS C:\> Get-TimeZone
Pacific Standard Time
```

이 명령은 현재 표준 시간대를 가져옵니다.

### 예제 2: 지정 된 문자열과 일치 하는 표준 시간대 가져오기

```
PS C:\> Get-TimeZone -Name "*pac*"
Pacific Standard Time (Mexico)

(UTC-08:00) Pacific Time (US &amp; Canada)

Pacific Standard Time

SA Pacific Standard Time

Pacific SA Standard Time

West Pacific Standard Time

Central Pacific Standard Time
```

이 명령은 지정 된 와일드 카드와 일치 하는 모든 표준 시간대를 가져옵니다.

### 예제 3: 사용 가능한 모든 표준 시간대 가져오기

```
PS C:\> Get-TimeZone -ListAvailable
```

이 명령은 사용 가능한 모든 표준 시간대를 가져옵니다.

## PARAMETERS

### -Id

이 cmdlet이 가져오는 표준 시간대의 ID 또는 ID를 문자열 배열로 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: Id
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -ListAvailable

이 cmdlet은 사용 가능한 모든 표준 시간대를 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ListAvailable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

이 cmdlet이 가져오는 표준 시간대의 이름 또는 이름을 문자열 배열로 지정 합니다.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String[]

## 출력

### TimeZoneInfo []

## 참고

이 cmdlet은 Windows 플랫폼 에서만 사용할 수 있습니다.

## 관련 링크

[Set-TimeZone](Set-TimeZone.md)
