---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-objectevent?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ObjectEvent
ms.openlocfilehash: a8e59419aed08a4ebe4fc781e9827ca5b0593b3e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212929"
---
# Register-ObjectEvent

## 개요
Microsoft .NET Framework 개체에서 생성된 이벤트를 구독합니다.

## SYNTAX

```
Register-ObjectEvent [-InputObject] <PSObject> [-EventName] <String> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>]
 [<CommonParameters>]
```

## 설명

`Register-ObjectEvent`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터의 .net 개체에 의해 생성 된 이벤트를 구독 합니다.

가입된 이벤트가 발생하면 세션의 이벤트 큐에 추가됩니다. 이벤트 큐에서 이벤트를 가져오려면 cmdlet을 사용 `Get-Event` 합니다.

의 매개 변수를 사용 하 여 `Register-ObjectEvent` 큐에서 이벤트를 식별 하는 데 도움이 될 수 있는 이벤트의 속성 값을 지정할 수 있습니다. **Action** 매개 변수를 사용 하 여 구독 된 이벤트가 발생할 때 수행할 작업을 지정 하 고, **전달** 매개 변수를 사용 하 여 원격 이벤트를 로컬 세션의 이벤트 큐로 보낼 수도 있습니다.

이벤트를 구독하면 이벤트 구독자가 세션에 추가됩니다. 세션의 이벤트 구독자를 가져오려면 cmdlet을 사용 합니다 `Get-EventSubscriber` . 구독을 취소 하려면 `Unregister-Event` 세션에서 이벤트 구독자를 삭제 하는 cmdlet을 사용 합니다.

## 예제

### 예 1: 새 프로세스가 시작 될 때 이벤트 구독

이 예제에서는 새 프로세스가 시작될 때 생성되는 이벤트를 구독합니다.

이 명령은 **Managementeventwatcher** 개체를 사용 하 여 **event도착** 이벤트를 가져옵니다. Query 개체는 이벤트가 **Win32_Process** 클래스에 대 한 인스턴스 생성 이벤트 임을 지정 합니다.

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived"
```

### 예제 2: 이벤트에 응답 하는 동작 지정

작업을 지정하면 발생한 이벤트가 이벤트 큐에 추가되지 않습니다. 대신 작업이 이벤트에 응답합니다. 이 예에서는 새 프로세스가 시작 되었음을 나타내는 인스턴스 작성 이벤트가 발생 하면 새 **Processcreated** 이벤트가 발생 합니다.

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $query
$newEventArgs = @{
    SourceIdentifier = 'PowerShell.ProcessCreated'
    Sender = $Sender
    EventArguments = $EventArgs.NewEvent.TargetInstance
}
$Action = { New-Event @newEventArgs }
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived" -Action $Action
```

```Output
Id   Name               PSJobTypeName   State       HasMoreData   Location   Command
--   ----               -------------   -----       -----------   --------   -------
 5   3db2d67a-efff-...                 NotStarted   False                    New-Event @newEventArgs
```

`$Sender` `$EventArgs` 이 동작은 이벤트 작업에 대해서만 채워지는 및 자동 변수를 사용 합니다.

이 `Register-ObjectEvent` 명령은 백그라운드 작업으로 실행 되는 작업을 나타내는 작업 개체를 반환 합니다. 작업 cmdlet (예: 및)을 사용 `Get-Job` `Receive-Job` 하 여 백그라운드 작업을 관리할 수 있습니다. 자세한 내용은 [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조하세요.

### 예 3: 원격 컴퓨터의 개체 이벤트 구독

이 예제에서는 원격 컴퓨터의 개체 이벤트에 가입하는 방법을 보여 줍니다. 이 예에서는 `Enable-ProcessCreationEvent` 스크립트 파일에 정의 된 함수를 사용 `ProcessCreationEvent.ps1` 합니다. 이 스크립트는 예제의 모든 컴퓨터에서 사용할 수 있습니다.

```powershell
# ProcessCreationEvent.ps1
function  Enable-ProcessCreationEvent {
    $queryParameters = "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1),
        "TargetInstance isa 'Win32_Process'"
    $Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters

    $objectEventArgs = @{
        Input = New-Object System.Management.ManagementEventWatcher $Query
        EventName = 'EventArrived'
        SourceIdentifier = 'WMI.ProcessCreated'
        MessageData = 'Test'
        Forward = $True
    }
    Register-ObjectEvent @objectEventArgs
}

$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S -FilePath ProcessCreationEvent.ps1
Invoke-Command -Session $S { Enable-ProcessCreationEvent }
```

첫 번째는 두 원격 컴퓨터에서 pssession **을 만든 후** 변수에 저장 하는 것 `$S` 입니다. 그런 다음 `Invoke-Command` cmdlet은 `ProcessCreationEvent.ps1` 의 각 pssessions에서 스크립트를 실행 합니다 `$S` . 이 동작은 `Enable-ProcessCreationEvent` 원격 세션에 함수를 만듭니다.
마지막으로 `Enable-ProcessCreationEvent` 원격 세션에서 함수를 실행 합니다.

 함수에는 `Register-ObjectEvent` **Managementeventwatcher** 개체 및 해당 **event도착** 이벤트를 통해 **Win32_Process** 개체의 인스턴스 생성 이벤트를 구독 하는 명령이 포함 되어 있습니다.

### 예제 4: PSEventJob 개체에서 동적 모듈 사용

이 예에서는 이벤트 등록에 **작업** 을 포함할 때 생성 된 **PSEventJob** 개체의 동적 모듈을 사용 하는 방법을 보여 줍니다. 먼저 타이머 개체를 사용 하도록 설정 하 고 타이머의 간격을 500 (밀리초)로 설정 합니다. `Register-ObjectEvent`Cmdlet은 timer 개체의 **경과** 된 이벤트를 등록 합니다. **PSEventJob** 개체는 변수에 저장 되며 `$Job` 이벤트 구독자의 **Action** 속성 에서도 사용할 수 있습니다. 자세한 내용은 [Get EventSubscriber](Get-EventSubscriber.md)를 참조 하세요.

타이머 간격이 경과할 때마다 이벤트가 발생 하 고 동작이 실행 됩니다. 이 경우 `Get-Random` cmdlet은 0에서 100 사이의 난수를 생성 하 고 `$Random` 변수에 저장 합니다.

```powershell
$Timer = New-Object Timers.Timer
$Timer.Interval = 500
$Timer.Enabled = $True
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Random'
    Action = {$Random = Get-Random -Min 0 -Max 100}
}
$Job = Register-ObjectEvent @objectEventArgs
$Job | Format-List -Property *
& $Job.module {$Random}
& $Job.module {$Random}
```

```Output
State         : Running
Module        : __DynamicModule_53113769-31f2-42dc-830b-8749325e28d6
StatusMessage :
HasMoreData   : True
Location      :
Command       : $Random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 47b5ec9f-bfe3-4605-860a-4674e5d44ca8
Id            : 7
Name          : Timer.Random
ChildJobs     : {}
PSBeginTime   : 6/27/2019 10:19:06 AM
PSEndTime     :
PSJobTypeName :
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
60
47
```

**PSEventJob** 에는 작업을 구현 하는 동적 스크립트 모듈이 포함 된 **module** 속성이 있습니다. 호출 연산자 ()를 사용 하 여 `&` 모듈의 명령을 호출 하 여 변수의 값을 표시 `$Random` 합니다.

모듈에 대 한 자세한 내용은 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)를 참조 하세요.

## PARAMETERS

### -Action

이벤트를 처리할 명령을 지정 합니다. 이벤트가 발생할 경우 이벤트 큐에 이벤트를 보내는 대신 **Action** 의 명령이 실행됩니다. 명령을 중괄호( { } )로 묶어 스크립트 블록을 만드세요.

**Action** 매개 변수 값에는 `$Event` ,, `$EventSubscriber` `$Sender` , `$EventArgs` 및 `$Args` 자동 변수가 포함 될 수 있습니다. 이러한 변수는 **작업** 스크립트 블록에 이벤트 정보를 제공 합니다. 자세한 내용은 [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)를 참조 하세요.

작업을 지정 하면 `Register-ObjectEvent` 는 해당 동작을 나타내는 이벤트 작업 개체를 반환 합니다. Job cmdlet을 사용하여 이벤트 작업을 관리할 수 있습니다.

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

### -EventName

구독할 이벤트를 지정합니다.

이 매개 변수 값은 .NET 개체가 노출 하는 이벤트의 이름 이어야 합니다. 예를 들어 **Managementeventwatcher** 클래스에는 **Event도착** 및 **중지** 라는 이벤트가 있습니다. 이벤트의 이벤트 이름을 찾으려면 cmdlet을 사용 합니다 `Get-Member` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -전달

Cmdlet이이 구독에 대 한 이벤트를 원격 세션으로 보냄을 나타냅니다. 원격 컴퓨터 또는 원격 세션에서 이벤트를 등록할 때 이 매개 변수를 사용합니다.

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

### -InputObject

이벤트를 생성 하는 .NET 개체를 지정 합니다. 개체를 포함하는 변수를 입력하거나 개체를 가져오는 명령 또는 식을 입력하세요.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaxTriggerCount

이벤트를 트리거할 수 있는 최대 횟수를 지정 합니다.

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

이 이벤트 구독에 연결할 추가 데이터를 지정합니다. 이 매개 변수 값은 이 구독과 연결된 모든 이벤트의 MessageData 속성에 표시됩니다.

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

선택한 구독 이름을 지정합니다. 선택한 이름은 현재 세션에서 고유해야 합니다. 기본값은 PowerShell이 할당 하는 GUID입니다.

이 매개 변수 값은 구독자 개체의 **SourceIdentifier** 속성 값과이 구독과 연결 된 모든 이벤트 개체에 표시 됩니다.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SupportEvent

Cmdlet이 이벤트 구독을 숨기도록 지정 합니다. 현재 구독이 더 복잡 한 이벤트 등록 메커니즘의 일부 이며 독립적으로 검색 되지 않아야 하는 경우이 매개 변수를 사용 합니다.

**Supportevent** 매개 변수를 사용 하 여 만든 구독을 보거나 취소 하려면 및 Cmdlet의 **Force** 매개 변수를 사용 합니다 `Get-EventSubscriber` `Unregister-Event` .

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

개체를에 연결할 수 없습니다 `Register-ObjectEvent` .

## 출력

### 없음 또는 PSEventJob

**Action** 매개 변수를 사용 하는 경우 `Register-ObjectEvent` **PSEventJob** 개체를 반환 합니다. 그러지 않으면 출력이 생성되지 않습니다.

## 참고

이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다. 현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

## 관련 링크

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

