---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: e1ac039ce49141197c2e14b060118dd4c87f7003
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213090"
---
# <span data-ttu-id="28dc8-103">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="28dc8-103">Get-EventSubscriber</span></span>

## <span data-ttu-id="28dc8-104">개요</span><span class="sxs-lookup"><span data-stu-id="28dc8-104">SYNOPSIS</span></span>
<span data-ttu-id="28dc8-105">현재 세션의 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-105">Gets the event subscribers in the current session.</span></span>

## <span data-ttu-id="28dc8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="28dc8-106">SYNTAX</span></span>

### <span data-ttu-id="28dc8-107">BySource (기본값)</span><span class="sxs-lookup"><span data-stu-id="28dc8-107">BySource (Default)</span></span>

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="28dc8-108">ById</span><span class="sxs-lookup"><span data-stu-id="28dc8-108">ById</span></span>

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="28dc8-109">설명</span><span class="sxs-lookup"><span data-stu-id="28dc8-109">DESCRIPTION</span></span>

<span data-ttu-id="28dc8-110">**Get EventSubscriber** cmdlet은 현재 세션의 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-110">The **Get-EventSubscriber** cmdlet gets the event subscribers in the current session.</span></span>

<span data-ttu-id="28dc8-111">Register event cmdlet을 사용 하 여 이벤트를 구독할 때 이벤트 구독자가 PowerShell 세션에 추가 되 고, 구독 한 이벤트가 발생할 때마다 이벤트 큐에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-111">When you subscribe to an event by using a Register event cmdlet, an event subscriber is added to your PowerShell session, and the events to which you subscribed are added to your event queue whenever they are raised.</span></span>
<span data-ttu-id="28dc8-112">이벤트 구독을 취소하려면 Unregister-Event cmdlet을 사용하여 이벤트 구독자를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-112">To cancel an event subscription, delete the event subscriber by using the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="28dc8-113">예제</span><span class="sxs-lookup"><span data-stu-id="28dc8-113">EXAMPLES</span></span>

### <span data-ttu-id="28dc8-114">예 1: 타이머 이벤트에 대 한 이벤트 구독자 가져오기</span><span class="sxs-lookup"><span data-stu-id="28dc8-114">Example 1: Get the event subscriber for a timer event</span></span>

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

<span data-ttu-id="28dc8-115">이 예에서는 **Get EventSubscriber** 명령을 사용 하 여 타이머 이벤트에 대 한 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-115">This example uses a **Get-EventSubscriber** command to get the event subscriber for a timer event.</span></span>

<span data-ttu-id="28dc8-116">첫 번째 명령은 New-Object cmdlet을 사용하여 타이머 개체의 인스턴스를 만든 다음</span><span class="sxs-lookup"><span data-stu-id="28dc8-116">The first command uses the New-Object cmdlet to create an instance of a timer object.</span></span>
<span data-ttu-id="28dc8-117">$Timer 변수에 새 타이머 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-117">It saves the new timer object in the $Timer variable.</span></span>

<span data-ttu-id="28dc8-118">두 번째 명령은 Get-Member cmdlet을 사용하여 타이머 이벤트에 대해 사용할 수 있는 이벤트를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-118">The second command uses the Get-Member cmdlet to display the events that are available for timer objects.</span></span>
<span data-ttu-id="28dc8-119">이 명령은 이벤트 값을 사용 하 여 **Get Member** Cmdlet의 Type 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-119">The command uses the Type parameter of the **Get-Member** cmdlet with a value of Event.</span></span>

<span data-ttu-id="28dc8-120">세 번째 명령은 Register-ObjectEvent cmdlet을 사용하여 타이머 개체의 Elapsed 이벤트를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-120">The third command uses the Register-ObjectEvent cmdlet to register for the Elapsed event on the timer object.</span></span>

<span data-ttu-id="28dc8-121">네 번째 명령은 **Get EventSubscriber** cmdlet을 사용 하 여 경과 된 이벤트에 대 한 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-121">The fourth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber for the Elapsed event.</span></span>

### <span data-ttu-id="28dc8-122">예제 2: 이벤트 구독자의 Action 속성에서 PSEventJob의 동적 모듈 사용</span><span class="sxs-lookup"><span data-stu-id="28dc8-122">Example 2: Use the dynamic module in PSEventJob in the Action property of the event subscriber</span></span>

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

<span data-ttu-id="28dc8-123">이 예에서는 이벤트 구독자의 Action 속성에서 **PSEventJob** 개체의 동적 모듈을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-123">This example shows how to use the dynamic module in the **PSEventJob** object in the Action property of the event subscriber.</span></span>

<span data-ttu-id="28dc8-124">첫 번째 명령은 New-Object cmdlet을 사용하여 타이머 개체를 만들고</span><span class="sxs-lookup"><span data-stu-id="28dc8-124">The first command uses the New-Object cmdlet to create a timer object.</span></span>
<span data-ttu-id="28dc8-125">두 번째 명령은 타이머 간격을 500(밀리초)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-125">The second command sets the interval of the timer to 500 (milliseconds).</span></span>

<span data-ttu-id="28dc8-126">세 번째 명령은 Register-ObjectEvent cmdlet을 사용하여 타이머 개체의 Elapsed 이벤트를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-126">The third command uses the Register-ObjectEvent cmdlet to register the Elapsed event of the timer object.</span></span>
<span data-ttu-id="28dc8-127">이 명령에는 이벤트를 처리하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-127">The command includes an action that handles the event.</span></span>
<span data-ttu-id="28dc8-128">타이머 간격이 지날 때마다 이벤트가 발생하고 작업의 명령이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-128">Whenever the timer interval elapses, an event is raised and the commands in the action run.</span></span>
<span data-ttu-id="28dc8-129">이 경우 Get-Random cmdlet은 0에서 100 사이의 난수를 생성 하 고 $Random 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-129">In this case, the Get-Random cmdlet generates a random number between 0 and 100 and saves it in the $Random variable.</span></span>
<span data-ttu-id="28dc8-130">이벤트의 소스 식별자는 Timer.Random입니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-130">The source identifier of the event is Timer.Random.</span></span>

<span data-ttu-id="28dc8-131">**Register ObjectEvent** 명령에서 *action* 매개 변수를 사용 하는 경우이 명령은 동작을 나타내는 **PSEventJob** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-131">When you use an *Action* parameter in a **Register-ObjectEvent** command, the command returns a **PSEventJob** object that represents the action.</span></span>

<span data-ttu-id="28dc8-132">네 번째 명령은 타이머를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-132">The fourth command enables the timer.</span></span>

<span data-ttu-id="28dc8-133">다섯 번째 명령은 **Get EventSubscriber** cmdlet을 사용 하 여 Timer. Random 이벤트의 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-133">The fifth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber of the Timer.Random event.</span></span>
<span data-ttu-id="28dc8-134">$Subscriber 변수에 이벤트 구독자 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-134">It saves the event subscriber object in the $Subscriber variable.</span></span>

<span data-ttu-id="28dc8-135">여섯 번째 명령은 이벤트 구독자 개체의 Action 속성에 **PSEventJob** 개체가 포함 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-135">The sixth command shows that the Action property of the event subscriber object contains a **PSEventJob** object.</span></span>
<span data-ttu-id="28dc8-136">실제로 여기에는 **Register ObjectEvent** 명령이 반환 하는 것과 동일한 **PSEventJob** 개체가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-136">In fact, it contains the same **PSEventJob** object that the **Register-ObjectEvent** command returned.</span></span>

<span data-ttu-id="28dc8-137">일곱 번째 명령은 Format-List cmdlet을 사용 하 여 작업 속성에 있는 **PSEventJob** 개체의 모든 속성을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-137">The seventh command uses the Format-List cmdlet to display all of the properties of the **PSEventJob** object in the Action property in a list.</span></span>
<span data-ttu-id="28dc8-138">결과는 **PSEventJob** 개체에 작업을 구현 하는 동적 스크립트 모듈이 포함 된 module 속성이 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-138">The result reveals that the **PSEventJob** object has a Module property that contains a dynamic script module that implements the action.</span></span>

<span data-ttu-id="28dc8-139">나머지 명령은 호출 연산자 (&)를 사용 하 여 모듈의 명령을 호출 하 고 $Random 변수의 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-139">The remaining commands use the call operator (&) to invoke the command in the module and display the value of the $Random variable.</span></span>
<span data-ttu-id="28dc8-140">호출 연산자를 사용하면 내보내지 않은 명령을 포함하여 모듈의 어떠한 명령도 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-140">You can use the call operator to invoke any command in a module, including commands that are not exported.</span></span>
<span data-ttu-id="28dc8-141">이 경우 명령에는 Elapsed 이벤트가 발생할 때 생성된 임의의 숫자가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-141">In this case, the commands show the random number that is being generated when the Elapsed event occurs.</span></span>

<span data-ttu-id="28dc8-142">모듈에 대 한 자세한 내용은 [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="28dc8-142">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="28dc8-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="28dc8-143">PARAMETERS</span></span>

### <span data-ttu-id="28dc8-144">-Force</span><span class="sxs-lookup"><span data-stu-id="28dc8-144">-Force</span></span>

<span data-ttu-id="28dc8-145">이 cmdlet은 Register-wmievent 및 Register-engineevent의 *supportevent* 매개 변수를 사용 하 여 숨겨진 이벤트의 등록자를 비롯 하 여 모든 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-145">Indicates that this cmdlet gets all event subscribers, including subscribers for events that are hidden by using the *SupportEvent* parameter of Register-ObjectEvent, Register-WmiEvent, and Register-EngineEvent.</span></span>

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

### <span data-ttu-id="28dc8-146">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="28dc8-146">-SourceIdentifier</span></span>

<span data-ttu-id="28dc8-147">이벤트 구독자만 가져오는 **SourceIdentifier** 속성 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-147">Specifies the **SourceIdentifier** property value that gets only the event subscribers.</span></span>
<span data-ttu-id="28dc8-148">기본적으로 **Get EventSubscriber** 는 세션의 모든 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-148">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>
<span data-ttu-id="28dc8-149">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-149">Wildcards are not permitted.</span></span>
<span data-ttu-id="28dc8-150">이 매개 변수는 대/소문자를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-150">This parameter is case-sensitive.</span></span>

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

### <span data-ttu-id="28dc8-151">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="28dc8-151">-SubscriptionId</span></span>

<span data-ttu-id="28dc8-152">이 cmdlet이 가져오는 구독 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-152">Specifies the subscription identifier that this cmdlet gets.</span></span>
<span data-ttu-id="28dc8-153">기본적으로 **Get EventSubscriber** 는 세션의 모든 이벤트 구독자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-153">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>

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

### <span data-ttu-id="28dc8-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="28dc8-154">CommonParameters</span></span>

<span data-ttu-id="28dc8-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="28dc8-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="28dc8-156">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="28dc8-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="28dc8-157">입력</span><span class="sxs-lookup"><span data-stu-id="28dc8-157">INPUTS</span></span>

### <span data-ttu-id="28dc8-158">없음</span><span class="sxs-lookup"><span data-stu-id="28dc8-158">None</span></span>

<span data-ttu-id="28dc8-159">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="28dc8-160">출력</span><span class="sxs-lookup"><span data-stu-id="28dc8-160">OUTPUTS</span></span>

### <span data-ttu-id="28dc8-161">PSEventSubscriber.</span><span class="sxs-lookup"><span data-stu-id="28dc8-161">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="28dc8-162">**Get EventSubscriber** 는 각 이벤트 구독자를 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-162">**Get-EventSubscriber** returns an object that represents each event subscriber.</span></span>

## <span data-ttu-id="28dc8-163">참고</span><span class="sxs-lookup"><span data-stu-id="28dc8-163">NOTES</span></span>

* <span data-ttu-id="28dc8-164">사용자 지정 이벤트를 만드는 New-Event cmdlet은 가입자를 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-164">The New-Event cmdlet, which creates a custom event, does not generate a subscriber.</span></span> <span data-ttu-id="28dc8-165">따라서 **Get eventsubscriber** cmdlet은 이러한 이벤트에 대 한 구독자 개체를 찾지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-165">Therefore, the **Get-EventSubscriber** cmdlet will not find a subscriber object for these events.</span></span> <span data-ttu-id="28dc8-166">그러나 이벤트를 전달 하거나 동작을 지정 하기 위해 Register-EngineEvent **cmdlet을 사용** 하 여 사용자 지정 이벤트를 구독 하는 경우에는 **register-engineevent** 에서 생성 하는 구독자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-166">However, if you use the Register-EngineEvent cmdlet to subscribe to a custom event (in order to forward the event or to specify an action), **Get-EventSubscriber** will find the subscriber that **Register-EngineEvent** generates.</span></span>

  <span data-ttu-id="28dc8-167">이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-167">Events, event subscriptions, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="28dc8-168">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="28dc8-168">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="28dc8-169">관련 링크</span><span class="sxs-lookup"><span data-stu-id="28dc8-169">RELATED LINKS</span></span>

[<span data-ttu-id="28dc8-170">Get-Event</span><span class="sxs-lookup"><span data-stu-id="28dc8-170">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="28dc8-171">New-Event</span><span class="sxs-lookup"><span data-stu-id="28dc8-171">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="28dc8-172">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="28dc8-172">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="28dc8-173">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="28dc8-173">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="28dc8-174">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="28dc8-174">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="28dc8-175">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="28dc8-175">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="28dc8-176">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="28dc8-176">Wait-Event</span></span>](Wait-Event.md)

