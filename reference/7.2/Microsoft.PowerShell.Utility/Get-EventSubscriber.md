---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: b8f55770770fa9077f654d382818386cc480c638
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599584"
---
# Get-EventSubscriber

## 개요
현재 세션의 이벤트 구독자를 가져옵니다.

## SYNTAX

### BySource (기본값)

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### ById

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## 설명

**Get EventSubscriber** cmdlet은 현재 세션의 이벤트 구독자를 가져옵니다.

Register event cmdlet을 사용 하 여 이벤트를 구독할 때 이벤트 구독자가 PowerShell 세션에 추가 되 고, 구독 한 이벤트가 발생할 때마다 이벤트 큐에 추가 됩니다.
이벤트 구독을 취소하려면 Unregister-Event cmdlet을 사용하여 이벤트 구독자를 삭제합니다.

## 예제

### 예 1: 타이머 이벤트에 대 한 이벤트 구독자 가져오기

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

이 예에서는 **Get EventSubscriber** 명령을 사용 하 여 타이머 이벤트에 대 한 이벤트 구독자를 가져옵니다.

첫 번째 명령은 New-Object cmdlet을 사용하여 타이머 개체의 인스턴스를 만든 다음
$Timer 변수에 새 타이머 개체를 저장 합니다.

두 번째 명령은 Get-Member cmdlet을 사용하여 타이머 이벤트에 대해 사용할 수 있는 이벤트를 표시합니다.
이 명령은 이벤트 값을 사용 하 여 **Get Member** Cmdlet의 Type 매개 변수를 사용 합니다.

세 번째 명령은 Register-ObjectEvent cmdlet을 사용하여 타이머 개체의 Elapsed 이벤트를 등록합니다.

네 번째 명령은 **Get EventSubscriber** cmdlet을 사용 하 여 경과 된 이벤트에 대 한 이벤트 구독자를 가져옵니다.

### 예제 2: 이벤트 구독자의 Action 속성에서 PSEventJob의 동적 모듈 사용

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

이 예에서는 이벤트 구독자의 Action 속성에서 **PSEventJob** 개체의 동적 모듈을 사용 하는 방법을 보여 줍니다.

첫 번째 명령은 New-Object cmdlet을 사용하여 타이머 개체를 만들고
두 번째 명령은 타이머 간격을 500(밀리초)으로 설정합니다.

세 번째 명령은 Register-ObjectEvent cmdlet을 사용하여 타이머 개체의 Elapsed 이벤트를 등록합니다.
이 명령에는 이벤트를 처리하는 작업이 포함됩니다.
타이머 간격이 지날 때마다 이벤트가 발생하고 작업의 명령이 실행됩니다.
이 경우 Get-Random cmdlet은 0에서 100 사이의 난수를 생성 하 고 $Random 변수에 저장 합니다.
이벤트의 소스 식별자는 Timer.Random입니다.

**Register ObjectEvent** 명령에서 *action* 매개 변수를 사용 하는 경우이 명령은 동작을 나타내는 **PSEventJob** 개체를 반환 합니다.

네 번째 명령은 타이머를 설정합니다.

다섯 번째 명령은 **Get EventSubscriber** cmdlet을 사용 하 여 Timer. Random 이벤트의 이벤트 구독자를 가져옵니다.
$Subscriber 변수에 이벤트 구독자 개체를 저장 합니다.

여섯 번째 명령은 이벤트 구독자 개체의 Action 속성에 **PSEventJob** 개체가 포함 되어 있음을 보여 줍니다.
실제로 여기에는 **Register ObjectEvent** 명령이 반환 하는 것과 동일한 **PSEventJob** 개체가 포함 됩니다.

일곱 번째 명령은 Format-List cmdlet을 사용 하 여 작업 속성에 있는 **PSEventJob** 개체의 모든 속성을 목록으로 표시 합니다.
결과는 **PSEventJob** 개체에 작업을 구현 하는 동적 스크립트 모듈이 포함 된 module 속성이 있음을 나타냅니다.

나머지 명령은 호출 연산자 (&)를 사용 하 여 모듈의 명령을 호출 하 고 $Random 변수의 값을 표시 합니다.
호출 연산자를 사용하면 내보내지 않은 명령을 포함하여 모듈의 어떠한 명령도 호출할 수 있습니다.
이 경우 명령에는 Elapsed 이벤트가 발생할 때 생성된 임의의 숫자가 표시됩니다.

모듈에 대 한 자세한 내용은 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)를 참조 하세요.

## PARAMETERS

### -Force

이 cmdlet은 Register-wmievent 및 Register-engineevent의 *supportevent* 매개 변수를 사용 하 여 숨겨진 이벤트의 등록자를 비롯 하 여 모든 이벤트 구독자를 가져옵니다.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SourceIdentifier

이벤트 구독자만 가져오는 **SourceIdentifier** 속성 값을 지정 합니다.
기본적으로 **Get EventSubscriber** 는 세션의 모든 이벤트 구독자를 가져옵니다.
와일드카드는 사용할 수 없습니다.
이 매개 변수는 대/소문자를 구분합니다.

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

### -SubscriptionId

이 cmdlet이 가져오는 구독 식별자를 지정 합니다.
기본적으로 **Get EventSubscriber** 는 세션의 모든 이벤트 구독자를 가져옵니다.

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

### CommonParameters

이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable. 자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.

## 입력

### 없음

이 cmdlet에 입력을 파이프할 수 없습니다.

## 출력

### PSEventSubscriber.

**Get EventSubscriber** 는 각 이벤트 구독자를 나타내는 개체를 반환 합니다.

## 참고

* 사용자 지정 이벤트를 만드는 New-Event cmdlet은 가입자를 생성하지 않습니다. 따라서 **Get eventsubscriber** cmdlet은 이러한 이벤트에 대 한 구독자 개체를 찾지 않습니다. 그러나 이벤트를 전달 하거나 동작을 지정 하기 위해 Register-EngineEvent **cmdlet을 사용** 하 여 사용자 지정 이벤트를 구독 하는 경우에는 **register-engineevent** 에서 생성 하는 구독자를 찾습니다.

  이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.
현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.

*

## 관련 링크

[Get-Event](Get-Event.md)

[New-Event](New-Event.md)

[Register-EngineEvent](Register-EngineEvent.md)

[Register-ObjectEvent](Register-ObjectEvent.md)

[Remove-Event](Remove-Event.md)

[Unregister-Event](Unregister-Event.md)

[Wait-Event](Wait-Event.md)

