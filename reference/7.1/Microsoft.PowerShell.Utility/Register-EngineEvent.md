---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 02/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-engineevent?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-EngineEvent
ms.openlocfilehash: 2adcbcc9e3c933e5c28521f26ec3ae2db03e50f7
ms.sourcegitcommit: f58e4a04240e3419772f9eaa031b626800b615d7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/28/2020
ms.locfileid: "93219041"
---
# Register-EngineEvent

## 개요
PowerShell 엔진 및 cmdlet에 의해 생성 된 이벤트를 구독 `New-Event` 합니다.

## SYNTAX

```
Register-EngineEvent [-SourceIdentifier] <String> [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## 설명

`Register-EngineEvent`Cmdlet은 PowerShell 엔진 및 cmdlet에 의해 생성 된 이벤트를 구독 `New-Event` 합니다. **SourceIdentifier** 매개 변수를 사용하여 이벤트를 지정합니다.

이 cmdlet을 사용 하 여 **종료** 된 엔진 이벤트 및 cmdlet에 의해 생성 된 이벤트를 구독할 수 있습니다 `New-Event` . 이러한 이벤트는 별도로 가입하지 않아도 세션의 이벤트 큐에 자동으로 추가됩니다. 그러나 가입을 하면 이벤트를 전달하고, 이벤트에 응답하는 작업을 지정하고, 가입을 취소할 수 있습니다.

가입된 이벤트가 발생하면 세션의 이벤트 큐에 추가됩니다. 이벤트 큐에서 이벤트를 가져오려면 cmdlet을 사용 `Get-Event` 합니다.

이벤트를 구독할 때 이벤트 구독자가 세션에 추가 됩니다. 세션의 이벤트 구독자를 가져오려면 cmdlet을 사용 합니다 `Get-EventSubscriber` . 구독을 취소 하려면 `Unregister-Event` 세션에서 이벤트 구독자를 삭제 하는 cmdlet을 사용 합니다.

## 예제

### 예 1: 원격 컴퓨터에 PowerShell 엔진 이벤트 등록

이 예제에서는 두 원격 컴퓨터에서 PowerShell 엔진 이벤트를 등록 합니다.

```powershell
$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S {
Register-EngineEvent -SourceIdentifier ([System.Management.Automation.PsEngineEvent]::Exiting) -Forward
}
```

`New-PSSession` 각 원격 컴퓨터에 사용자 관리 세션 (PSSession)을 만듭니다. `Invoke-Command` Cmdlet은 `Register-EngineEvent` 원격 세션에서 명령을 실행 합니다.
`Register-EngineEvent`**SourceIdentifier** 매개 변수를 사용 하 여 이벤트를 식별 합니다. **전달** 매개 변수는 원격 세션에서 로컬 세션으로 이벤트를 전달 하도록 엔진에 지시 합니다.

### 예 2: 종료 이벤트가 발생 하는 경우 지정 된 작업 수행

이 예제에서는를 실행 하 여 `Register-EngineEvent` **PowerShell 종료** 이벤트가 발생 하는 경우 특정 작업을 수행 하는 방법을 보여 줍니다.

```powershell
Register-EngineEvent -SourceIdentifier PowerShell.Exiting -SupportEvent -Action {
    Get-History | Export-Clixml $Home\history.clixml
}
```

**Supportevent** 매개 변수를 추가 하 여 이벤트 구독을 숨깁니다. PowerShell이 종료 되 면 종료 된 세션의 명령 기록을 사용자의 디렉터리에 XML 파일로 내보냅니다 `$Home` .

### 예제 3: 사용자 정의 이벤트 만들기 및 구독

이 예에서는 **Myeventsource** 원본에서 이벤트에 대 한 구독을 만듭니다. 이는 작업의 진행률을 모니터링 하는 데 사용할 임의의 원본입니다. `Register-EngineEvent` 구독을 만드는 데 사용 됩니다. **Action** 매개 변수에 대 한 스크립트 블록은 이벤트 데이터를 텍스트 파일에 기록 합니다.

```powershell
Register-EngineEvent -SourceIdentifier MyEventSource -Action {
    "Event: {0}" -f $event.messagedata | Out-File c:\temp\MyEvents.txt -Append
}

Start-Job -Name TestJob -ScriptBlock {
    While ($True) {
        Register-EngineEvent -SourceIdentifier MyEventSource -Forward
        Start-Sleep -seconds 2
        "Doing some work..."
        New-Event -SourceIdentifier MyEventSource -Message ("{0} -  Work done..." -f (Get-Date))
    }
}
Start-Sleep -seconds 4
Get-EventSubscriber
Get-Job
```

```Output
SubscriptionId   : 12
SourceObject     :
EventName        :
SourceIdentifier : MyEventSource
Action           : System.Management.Automation.PSEventJob
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Running       True                                 …
19     TestJob         BackgroundJob   Running       True            localhost            …
```

`Register-EngineEvent` 작업 Id 18을 만들었습니다. `Start-Job` 작업 Id 19를 만들었습니다. 예 #4 들어 이벤트 구독과 작업을 제거한 다음 로그 파일을 검사 합니다.

### 예제 4: 이벤트 등록 취소 및 작업 정리

이는 예제 3의 연속입니다. 이 예제에서는 10 초 동안 기다린 후 여러 이벤트가 발생 하도록 합니다. 그런 다음 이벤트 구독의 등록을 취소 합니다.

```powershell
PS> Start-Sleep -seconds 10
PS> Get-EventSubscriber | Unregister-Event
PS> Get-Job

Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
18     MyEventSource                   Stopped       False                                …
19     TestJob         BackgroundJob   Running       True            localhost            …

PS> Stop-Job -Id 19
PS> Get-Job | Remove-Job
PS> Get-Content C:\temp\MyEvents.txt
Event: 2/18/2020 2:36:19 PM -  Work done...
Event: 2/18/2020 2:36:21 PM -  Work done...
Event: 2/18/2020 2:36:23 PM -  Work done...
Event: 2/18/2020 2:36:25 PM -  Work done...
Event: 2/18/2020 2:36:27 PM -  Work done...
Event: 2/18/2020 2:36:29 PM -  Work done...
Event: 2/18/2020 2:36:31 PM -  Work done...
```

`Unregister-Event`Cmdlet은 이벤트 구독 (작업 Id 18)과 관련 된 작업을 중지 합니다. 작업 Id 19는 계속 실행 중 이며 새 이벤트를 만듭니다. **작업 cmdlet을** 사용 하 여 작업을 중지 하 고 불필요 한 작업 개체를 제거 합니다. `Get-Content` 로그 파일의 내용을 표시 합니다.

## PARAMETERS

### -Action

이벤트를 처리할 명령을 지정합니다. 이벤트가 발생할 경우 이벤트 큐에 이벤트를 보내는 대신 **Action** 의 명령이 실행됩니다. 명령을 중괄호( { } )로 묶어 스크립트 블록을 만드세요.

**Action** 매개 변수 값에는 `$Event` `$EventSubscriber` `$Sender` `$EventArgs` `$Args` **action** 스크립트 블록에 이벤트 정보를 제공 하는,,, 및 자동 변수가 포함 될 수 있습니다. 자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

작업을 지정 하면 `Register-EngineEvent` 는 해당 동작을 나타내는 이벤트 작업 개체를 반환 합니다. Job cmdlet을 사용하여 이벤트 작업을 관리할 수 있습니다.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -전달

Cmdlet이이 구독에 대 한 이벤트를 로컬 컴퓨터의 세션으로 보내도록 지정 합니다.
원격 컴퓨터 또는 원격 세션에서 이벤트를 등록할 때 이 매개 변수를 사용합니다.

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

### -MaxTriggerCount

이벤트 구독에 대해 동작이 실행 되는 최대 횟수를 지정 합니다.

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

### -MessageData

이벤트와 연결된 추가 데이터를 지정합니다. 이 매개 변수 값은 이벤트 개체의 **MessageData** 속성에 표시됩니다.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

가입할 이벤트의 원본 식별자를 지정합니다. 원본 식별자는 현재 세션에서 고유해야 합니다. 이 매개 변수는 필수적 요소입니다.

이 매개 변수 값은 구독자 개체 및 이 구독과 연결된 모든 이벤트 개체의 **SourceIdentifier** 속성 값에 표시됩니다.

값은 이벤트의 원본에만 적용 됩니다. Cmdlet에서 사용 하기 위해 만든 임의의 값일 수 있습니다 `New-Event` . PowerShell 엔진은 **register-engineevent** values powershell을 지원 합니다 **. 종료** 및 **powershell. OnIdle**.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Cmdlet이 이벤트 구독을 숨기도록 지정 합니다. 현재 구독이 더 복잡 한 이벤트 등록 메커니즘의 일부 이며 독립적으로 검색 되지 않아야 하는 경우이 매개 변수를 추가 합니다.

**Supportevent** 매개 변수를 사용 하 여 만든 구독을 보거나 취소 하려면 또는 Cmdlet에 **Force** 매개 변수를 추가 합니다 `Get-EventSubscriber` `Unregister-Event` .

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

입력을로 파이프 할 수 없습니다 `Register-EngineEvent` .

## 출력

### 없음 또는 PSEventJob

**Action** 매개 변수를 사용 하는 경우 `Register-EngineEvent` **PSEventJob** 개체를 반환 합니다. 그러지 않으면 출력이 생성되지 않습니다.

## 참고

이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

## 관련 링크

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

