---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uptime?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Uptime
ms.openlocfilehash: d06dbc66d9674b59df4d75f8ae333d4fe24aa7eb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213017"
---
# Get-Uptime

## 개요
마지막 부팅 이후 **TimeSpan** 을 가져옵니다.

## SYNTAX

### Timespan (기본값)

```
Get-Uptime [<CommonParameters>]
```

### 이후

```
Get-Uptime [-Since] [<CommonParameters>]
```

## 설명

이 cmdlet은 운영 체제의 마지막 부팅 이후 경과 된 시간을 반환 합니다.

`Get-Uptime`Cmdlet은 PowerShell 6.0에서 도입 되었습니다.

## 예제

### 예제 1-마지막 부팅 이후 시간 표시

```powershell
Get-Uptime
```

```Output
Days              : 9
Hours             : 0
Minutes           : 9
Seconds           : 45
Milliseconds      : 0
Ticks             : 7781850000000
TotalDays         : 9.00677083333333
TotalHours        : 216.1625
TotalMinutes      : 12969.75
TotalSeconds      : 778185
TotalMilliseconds : 778185000
```

### 예 2-마지막 부팅 시간 표시

```powershell
Get-Uptime -Since
```

```Output
Tuesday, June 18, 2019 2:34:56 PM
```

## PARAMETERS

### -이후

Cmdlet이 운영 체제가 마지막으로 부팅 된 시간을 나타내는 **DateTime** 개체를 반환 하도록 합니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Since
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

## 출력

### System.TimeSpan

이는 매개 변수를 사용 하지 않는 경우의 기본 반환 형식입니다.

### System.DateTime

이 형식은 **이후** 매개 변수를 사용할 때 반환 됩니다.

> [!NOTE]
> Windows 빠른 시작을 사용 하는 경우 Windows에서는 **Lastbootuptime 시간** 에 저장 된 값을 업데이트 하지 않습니다. 빠른 시작을 사용 하지 않도록 설정 하려면 다음 명령을 실행 `Powercfg -h off` 합니다.
>
> Windows 빠른 시작에 대 한 자세한 내용은 절전 모드에서 절전 모드에서 [빠른 시작을 구별](/windows-hardware/drivers/kernel/distinguishing-fast-startup-from-wake-from-hibernation)하는 방법을 참조 하세요.

## 참고

Windows에서 반환 되는 값은 WMI에 있는 **Win32_OperatingSystem** 클래스의 **lastbootuptime 시간** 속성과 동일 합니다.

## 관련 링크

[Win32_OperatingSystem](/windows/win32/cimwin32prov/win32-operatingsystem#properties)

