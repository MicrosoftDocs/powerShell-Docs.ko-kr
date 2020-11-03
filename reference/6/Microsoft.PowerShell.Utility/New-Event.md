---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 6056861bc6b472e389939e446d922d2bc4302294
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216570"
---
# New-Event

## 개요
새 이벤트를 만듭니다.

## SYNTAX

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## 설명

**새 이벤트** cmdlet은 새 사용자 지정 이벤트를 만듭니다.

사용자 지정 이벤트를 사용하여 하드웨어 또는 시스템 상태, 애플리케이션 상태, 디스크 상태, 네트워크 상태 또는 백그라운드 작업 완료 등 프로그램에서 감지할 수 있는 변경 내용과 프로그램의 상태 변경 내용을 사용자에게 알릴 수 있습니다.

사용자 지정 이벤트는 발생할 때마다 세션의 이벤트 큐에 자동으로 추가되므로 구독할 필요가 없습니다.
그러나 이벤트를 로컬 세션으로 전달하거나 이벤트에 응답할 작업을 지정하려는 경우 Register-EngineEvent cmdlet을 사용하여 사용자 지정 이벤트를 구독합니다.

사용자 지정 이벤트를 구독하면 이벤트 구독자가 세션에 추가됩니다.
Unregister-Event cmdlet을 사용하여 이벤트 구독을 취소하면 이벤트 구독자 및 사용자 지정 이벤트가 세션에서 삭제됩니다.
사용자 지정 이벤트를 구독 하지 않는 경우 이벤트를 삭제 하려면 프로그램 조건을 변경 하거나 PowerShell 세션을 닫아야 합니다.

## 예제

### 예제 1: 이벤트 큐에 새 이벤트 만들기

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

이 명령은 PowerShell 이벤트 큐에 새 이벤트를 만듭니다.
**Windows. Timer** 개체를 사용 하 여 이벤트를 보냅니다.

### 예제 2: 다른 이벤트에 대 한 응답으로 이벤트 발생

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

이 샘플 함수는 **새** 이벤트 cmdlet을 사용 하 여 다른 이벤트에 대 한 응답으로 이벤트를 발생 시킵니다.
명령에서 Register-ObjectEvent cmdlet을 사용하여 새 프로세스를 만들 때 발생하는 WMI(Windows Management Instrumentation) 이벤트를 구독합니다.
이 명령은 cmdlet의 *Action* 매개 변수를 사용 하 여 새 이벤트를 만드는 **새** 이벤트 cmdlet을 호출 합니다.

**새 이벤트** 에서 발생 하는 이벤트는 PowerShell 이벤트 큐에 자동으로 추가 되므로 해당 이벤트를 등록할 필요가 없습니다.

## PARAMETERS

### -EventArguments

이벤트 옵션이 포함된 개체를 지정합니다.

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageData

이벤트와 연결된 추가 데이터를 지정합니다.
이 매개 변수 값은 이벤트 개체의 **MessageData** 속성에 표시됩니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -발신자

이벤트를 발생시키는 개체를 지정합니다.
기본값은 PowerShell 엔진입니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

새 이벤트의 이름을 지정합니다.
이 매개 변수는 필수이며 세션에서 고유해야 합니다.

이 매개 변수 값은 이벤트의 **SourceIdentifier** 속성에 표시 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### PSEventArgs.

## 참고

새 사용자 지정 이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

## 관련 링크

[Get-Event](Get-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)
