---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: 55fa54521a6c2e9d37b333a27af4572c6a34913a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213617"
---
# Wait-Event

## 개요
계속 실행하기 전에 특정 이벤트가 발생할 때까지 대기합니다.

## SYNTAX

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## 설명

`Wait-Event`Cmdlet은 특정 이벤트가 발생할 때까지 스크립트 또는 함수 실행을 일시 중단 합니다. 이벤트가 검색되면 실행을 다시 시작합니다. 대기를 취소 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.

이벤트를 폴링하는 대신 이 기능을 사용할 수 있습니다. 또한 두 가지 방법으로 이벤트에 대 한 응답을 확인할 수 있습니다.

- 이벤트 구독의 **Action** 매개 변수 사용
- 이벤트가 반환 되 고 작업으로 응답할 때까지 기다리는 중

## 예제

### 예제 1: 다음 이벤트 대기

이 예에서는 다음 이벤트가 발생할 때까지 대기 합니다.

```powershell
Wait-Event
```

### 예제 2: 지정 된 소스 식별자를 사용 하 여 이벤트 대기

이 예제에서는 다음 이벤트가 발생 하 고 원본 식별자가 ProcessStarted 인 경우를 기다립니다.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### 예제 3: 타이머가 경과 된 이벤트 대기

이 예제에서는 cmdlet을 사용 하 여 `Wait-Event` 2000 밀리초로 설정 된 타이머의 타이머 이벤트를 대기 합니다.

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### 예제 4: 지정 된 시간 제한 후 이벤트 대기

이 예제에서는 다음 이벤트가 발생 하 고 원본 식별자가 **Processstarted** 인 경우 최대 90 초 동안 대기 합니다. 지정한 시간이 만료되면 대기가 종료됩니다.

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## PARAMETERS

### -SourceIdentifier

이 cmdlet이 이벤트를 대기 하는 원본 식별자를 지정 합니다.
기본적으로는 `Wait-Event` 이벤트를 기다립니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -시간 제한

이벤트가 발생할 때까지 대기 하는 최대 시간 (초)을 지정 합니다 `Wait-Event` . 기본값 -1은 무기한 대기합니다. 이 타이밍은 명령을 제출할 때 시작 됩니다 `Wait-Event` .

지정한 시간을 초과하면 이벤트가 발생하지 않았어도 대기가 종료되고 명령 프롬프트가 반환됩니다. 오류 메시지는 표시되지 않습니다.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### System.String

## 출력

### PSEventArgs.

## 참고

이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

## 관련 링크

[Get-Event](Get-Event.md)

[Get-EventSubscriber](Get-EventSubscriber.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
