---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 1920d7a834de133b377cdab7e16851c86477c3da
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216713"
---
# Get-Event

## 개요
이벤트 큐의 이벤트를 가져옵니다.

## SYNTAX

### BySource (기본값)

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### ById

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## 설명

**Get 이벤트** cmdlet은 현재 세션에 대 한 PowerShell 이벤트 큐의 이벤트를 가져옵니다.
모든 이벤트를 가져오거나 *EventIdentifier* 또는 *SourceIdentifier* 매개 변수를 사용 하 여 이벤트를 지정할 수 있습니다.

이벤트가 발생하면 이벤트 큐에 추가됩니다.
이벤트 큐에는 등록 한 이벤트, New-Event cmdlet을 사용 하 여 만든 이벤트 및 PowerShell이 종료 될 때 발생 하는 이벤트가 포함 됩니다.
이벤트를 가져오려면 **Get 이벤트** 또는 Wait-Event를 사용할 수 있습니다.

이 명령은 이벤트 뷰어 로그에서 이벤트를 가져오지 않습니다.
이러한 이벤트를 가져오려면 Get-WinEvent 또는 Get-EventLog를 사용하세요.

## 예제

### 예제 1: 모든 이벤트 가져오기

```
PS C:\> Get-Event
```

이 명령은 이벤트 큐의 모든 이벤트를 가져옵니다.

### 예 2: 소스 식별자로 이벤트 가져오기

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

이 명령은 SourceIdentifier 속성 값이 PowerShell. ProcessCreated 인 이벤트를 가져옵니다.

### 예제 3: 생성 된 시간에 따라 이벤트 가져오기

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

이 예제는 SourceIdentifier 이외의 속성을 사용하여 이벤트를 가져오는 방법을 보여 줍니다.

첫 번째 명령은 이벤트 큐의 모든 이벤트를 가져와 $Events 변수에 저장 합니다.

두 번째 명령은 배열 표기법을 사용 하 여 $Events 변수에 있는 배열의 첫 번째 (0 인덱스) 이벤트를 가져옵니다.
파이프라인 연산자(|)를 사용하여 이벤트를 Format-List 명령으로 보내면 이 명령은 목록에 있는 이벤트의 모든 속성을 표시합니다.
이를 통해 이벤트 개체의 속성을 검사할 수 있습니다.

세 번째 명령은 Where-Object cmdlet을 사용 하 여 생성 된 시간을 기준으로 이벤트를 가져오는 방법을 보여 줍니다.

### 예제 4: 해당 식별자로 이벤트 가져오기

```
PS C:\> Get-Event -EventIdentifier 2
```

이 명령은 이벤트 식별자가 2인 이벤트를 가져옵니다.

## PARAMETERS

### -EventIdentifier

이 cmdlet이 이벤트를 가져오는 이벤트 식별자를 지정 합니다.

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -SourceIdentifier

이 cmdlet이 이벤트를 가져오는 원본 식별자를 지정 합니다.
기본값은 이벤트 큐의 모든 이벤트입니다.
와일드카드는 사용할 수 없습니다.

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### PSEventArgs.

**Get 이벤트** 는 각 이벤트에 대 한 **PSEventArgs** 개체를 반환 합니다.
이 개체에 대 한 설명을 보려면를 입력 하 `Get-Help Get-Event -Full` 고 도움말 항목의 참고 섹션을 참조 하세요.

## 참고

* 이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

  PSEventArgs **cmdlet은** 다음 속성을 사용 하 여 **PSEventArgs** 개체 ( **PSEventArgs** )를 반환 합니다.

  - 컴퓨터.
이벤트가 발생한 컴퓨터의 이름입니다.
이 속성 값은 이벤트가 원격 컴퓨터에서 전달된 경우에만 채워집니다.

  - RunspaceId.
이벤트가 발생한 세션을 고유하게 식별하는 GUID입니다.
이 속성 값은 이벤트가 원격 컴퓨터에서 전달된 경우에만 채워집니다.

  - EventIdentifier.
현재 세션에서 이벤트 알림을 고유하게 식별하는 정수(Int32)입니다.

  - 으로부터.
이벤트를 생성한 개체입니다.
*Action* 매개 변수 값에서 $Sender 자동 변수는 Sender 개체를 포함 합니다.

  - SourceEventArgs.
EventArgs에서 파생된 첫 번째 매개 변수입니다(있는 경우).
예를 들어, 시그니처에 Object sender, Timers.elapsedeventargs가 e 형식이 있는 타이머 경과 이벤트에서 SourceEventArgs 속성에는 Timers.elapsedeventargs가가 포함 됩니다.
*Action* 매개 변수 값에서 $EventArgs 자동 변수에이 값이 포함 됩니다.

  - SourceArgs입니다.
원래 이벤트 서명의 모든 매개 변수입니다.
표준 이벤트 시그니처의 경우 \[ 0 $Args 발신자를 \] 나타내고 $Args \[ 1은 \] sourceeventargs를 나타냅니다.
*Action* 매개 변수 값에서 $Args 자동 변수에이 값이 포함 됩니다.

  - SourceIdentifier.
이벤트 구독을 식별하는 문자열입니다.
*Action* 매개 변수 값에서 $Event 자동 변수의 SourceIdentifier 속성은이 값을 포함 합니다.

  - TimeGenerated.
이벤트가 생성 된 시간을 나타내는 **DateTime** 개체입니다.
*Action* 매개 변수 값에서 $Event 자동 변수의 timegenerated 속성에이 값이 포함 됩니다.

  - MessageData.
이벤트 구독과 연결된 데이터입니다.
사용자는 이벤트를 등록할 때 이 데이터를 지정합니다.
*Action* 매개 변수 값에서 $Event 자동 변수의 messagedata 속성에이 값이 포함 됩니다.

## 관련 링크

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
