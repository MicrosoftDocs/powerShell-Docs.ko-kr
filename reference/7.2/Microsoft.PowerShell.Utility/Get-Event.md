---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: 4b275d489984f85aea401b781e38c80fbc4b2177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600636"
---
# <span data-ttu-id="f6a08-102">Get-Event</span><span class="sxs-lookup"><span data-stu-id="f6a08-102">Get-Event</span></span>

## <span data-ttu-id="f6a08-103">개요</span><span class="sxs-lookup"><span data-stu-id="f6a08-103">SYNOPSIS</span></span>
<span data-ttu-id="f6a08-104">이벤트 큐의 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-104">Gets the events in the event queue.</span></span>

## <span data-ttu-id="f6a08-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f6a08-105">SYNTAX</span></span>

### <span data-ttu-id="f6a08-106">BySource (기본값)</span><span class="sxs-lookup"><span data-stu-id="f6a08-106">BySource (Default)</span></span>

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### <span data-ttu-id="f6a08-107">ById</span><span class="sxs-lookup"><span data-stu-id="f6a08-107">ById</span></span>

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## <span data-ttu-id="f6a08-108">설명</span><span class="sxs-lookup"><span data-stu-id="f6a08-108">DESCRIPTION</span></span>

<span data-ttu-id="f6a08-109">`Get-Event`Cmdlet은 현재 세션에 대 한 PowerShell 이벤트 큐의 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-109">The `Get-Event` cmdlet gets events in the PowerShell event queue for the current session.</span></span> <span data-ttu-id="f6a08-110">모든 이벤트를 가져오거나 **EventIdentifier** 또는 **SourceIdentifier** 매개 변수를 사용 하 여 이벤트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-110">You can get all events or use the **EventIdentifier** or **SourceIdentifier** parameter to specify the events.</span></span>

<span data-ttu-id="f6a08-111">이벤트가 발생하면 이벤트 큐에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-111">When an event occurs, it is added to the event queue.</span></span> <span data-ttu-id="f6a08-112">이벤트 큐에는 등록 한 이벤트, cmdlet을 사용 하 여 만든 이벤트 `New-Event` 및 PowerShell이 종료 될 때 발생 하는 이벤트가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-112">The event queue includes events for which you have registered, events created by using the `New-Event` cmdlet, and the event that is raised when PowerShell exits.</span></span> <span data-ttu-id="f6a08-113">`Get-Event`또는를 사용 하 여 이벤트를 가져올 수 있습니다 `Wait-Event` .</span><span class="sxs-lookup"><span data-stu-id="f6a08-113">You can use `Get-Event` or `Wait-Event` to get the events.</span></span>

<span data-ttu-id="f6a08-114">이 명령은 이벤트 뷰어 로그에서 이벤트를 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-114">This cmdlet does not get events from the Event Viewer logs.</span></span> <span data-ttu-id="f6a08-115">이러한 이벤트를 가져오려면 또는를 `Get-WinEvent` 사용 `Get-EventLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-115">To get those events, use `Get-WinEvent` or `Get-EventLog`.</span></span>

## <span data-ttu-id="f6a08-116">예제</span><span class="sxs-lookup"><span data-stu-id="f6a08-116">EXAMPLES</span></span>

### <span data-ttu-id="f6a08-117">예제 1: 모든 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="f6a08-117">Example 1: Get all events</span></span>

```
PS C:\> Get-Event
```

<span data-ttu-id="f6a08-118">이 명령은 이벤트 큐의 모든 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-118">This command gets all events in the event queue.</span></span>

### <span data-ttu-id="f6a08-119">예 2: 소스 식별자로 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="f6a08-119">Example 2: Get events by source identifier</span></span>

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

<span data-ttu-id="f6a08-120">이 명령은 SourceIdentifier 속성 값이 PowerShell. ProcessCreated 인 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-120">This command gets events in which the value of the SourceIdentifier property is PowerShell.ProcessCreated.</span></span>

### <span data-ttu-id="f6a08-121">예제 3: 생성 된 시간에 따라 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="f6a08-121">Example 3: Get an event based on the time it was generated</span></span>

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

<span data-ttu-id="f6a08-122">이 예제는 SourceIdentifier 이외의 속성을 사용하여 이벤트를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-122">This example shows how to get events by using properties other than SourceIdentifier.</span></span>

<span data-ttu-id="f6a08-123">첫 번째 명령은 이벤트 큐의 모든 이벤트를 가져와 변수에 저장 합니다 `$Events` .</span><span class="sxs-lookup"><span data-stu-id="f6a08-123">The first command gets all events in the event queue and saves them in the `$Events` variable.</span></span>

<span data-ttu-id="f6a08-124">두 번째 명령은 배열 표기법을 사용 하 여 변수에 있는 배열의 첫 번째 (0 인덱스) 이벤트를 가져옵니다 `$Events` .</span><span class="sxs-lookup"><span data-stu-id="f6a08-124">The second command uses array notation to get the first (0-index) event in the array in the `$Events` variable.</span></span> <span data-ttu-id="f6a08-125">파이프라인 연산자 ()를 사용 하 여 이벤트를 `|` 명령으로 보냅니다 .이 명령은 `Format-List` 이벤트의 모든 속성을 목록으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-125">The command uses a pipeline operator (`|`) to send the event to the `Format-List` command, which displays all properties of the event in a list.</span></span> <span data-ttu-id="f6a08-126">이를 통해 이벤트 개체의 속성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-126">This allows you to examine the properties of the event object.</span></span>

<span data-ttu-id="f6a08-127">세 번째 명령은 cmdlet을 사용 하 여 `Where-Object` 생성 된 시간을 기준으로 이벤트를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-127">The third command shows how to use the `Where-Object` cmdlet to get an event based on the time that it was generated.</span></span>

### <span data-ttu-id="f6a08-128">예제 4: 해당 식별자로 이벤트 가져오기</span><span class="sxs-lookup"><span data-stu-id="f6a08-128">Example 4: Get an event by its identifier</span></span>

```
PS C:\> Get-Event -EventIdentifier 2
```

<span data-ttu-id="f6a08-129">이 명령은 이벤트 식별자가 2인 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-129">This command gets the event with an event identifier of 2.</span></span>

## <span data-ttu-id="f6a08-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f6a08-130">PARAMETERS</span></span>

### <span data-ttu-id="f6a08-131">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="f6a08-131">-EventIdentifier</span></span>

<span data-ttu-id="f6a08-132">이 cmdlet이 이벤트를 가져오는 이벤트 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-132">Specifies the event identifiers for which this cmdlet gets events.</span></span>

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

### <span data-ttu-id="f6a08-133">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="f6a08-133">-SourceIdentifier</span></span>

<span data-ttu-id="f6a08-134">이 cmdlet이 이벤트를 가져오는 원본 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-134">Specifies source identifiers for which this cmdlet gets events.</span></span> <span data-ttu-id="f6a08-135">기본값은 이벤트 큐의 모든 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-135">The default is all events in the event queue.</span></span> <span data-ttu-id="f6a08-136">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-136">Wildcards are not permitted.</span></span>

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

### <span data-ttu-id="f6a08-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f6a08-137">CommonParameters</span></span>

<span data-ttu-id="f6a08-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f6a08-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f6a08-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6a08-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f6a08-140">입력</span><span class="sxs-lookup"><span data-stu-id="f6a08-140">INPUTS</span></span>

### <span data-ttu-id="f6a08-141">없음</span><span class="sxs-lookup"><span data-stu-id="f6a08-141">None</span></span>

<span data-ttu-id="f6a08-142">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="f6a08-143">출력</span><span class="sxs-lookup"><span data-stu-id="f6a08-143">OUTPUTS</span></span>

### <span data-ttu-id="f6a08-144">PSEventArgs.</span><span class="sxs-lookup"><span data-stu-id="f6a08-144">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="f6a08-145">`Get-Event` 각 이벤트에 대 한 **PSEventArgs** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-145">`Get-Event` returns a **PSEventArgs** object for each event.</span></span> <span data-ttu-id="f6a08-146">이 개체에 대 한 설명을 보려면를 입력 하 `Get-Help Get-Event -Full` 고 도움말 항목의 참고 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6a08-146">To see a description of this object, type `Get-Help Get-Event -Full` and see the Notes section of the help topic.</span></span>

## <span data-ttu-id="f6a08-147">참고</span><span class="sxs-lookup"><span data-stu-id="f6a08-147">NOTES</span></span>

<span data-ttu-id="f6a08-148">Linux 또는 macOS 플랫폼에서 사용할 수 있는 이벤트 원본이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-148">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="f6a08-149">이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-149">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="f6a08-150">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-150">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="f6a08-151">`Get-Event`Cmdlet은 다음 속성을 사용 하 여 **PSEventArgs** 개체 (**PSEventArgs**)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-151">The `Get-Event` cmdlet returns a **PSEventArgs** object (**System.Management.Automation.PSEventArgs**) with the following properties:</span></span>

- <span data-ttu-id="f6a08-152">컴퓨터.</span><span class="sxs-lookup"><span data-stu-id="f6a08-152">ComputerName.</span></span> <span data-ttu-id="f6a08-153">이벤트가 발생한 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-153">The name of the computer on which the event occurred.</span></span> <span data-ttu-id="f6a08-154">이 속성 값은 이벤트가 원격 컴퓨터에서 전달된 경우에만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-154">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="f6a08-155">RunspaceId.</span><span class="sxs-lookup"><span data-stu-id="f6a08-155">RunspaceId.</span></span> <span data-ttu-id="f6a08-156">이벤트가 발생한 세션을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-156">A GUID that uniquely identifies the session in which the event occurred.</span></span> <span data-ttu-id="f6a08-157">이 속성 값은 이벤트가 원격 컴퓨터에서 전달된 경우에만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-157">This property value is populated only when the event is forwarded from a remote computer.</span></span>

- <span data-ttu-id="f6a08-158">EventIdentifier.</span><span class="sxs-lookup"><span data-stu-id="f6a08-158">EventIdentifier.</span></span> <span data-ttu-id="f6a08-159">현재 세션에서 이벤트 알림을 고유하게 식별하는 정수(Int32)입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-159">An integer (Int32) that uniquely identifies the event notification in the current session.</span></span>

- <span data-ttu-id="f6a08-160">으로부터.</span><span class="sxs-lookup"><span data-stu-id="f6a08-160">Sender.</span></span> <span data-ttu-id="f6a08-161">이벤트를 생성한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-161">The object that generated the event.</span></span> <span data-ttu-id="f6a08-162">**Action** 매개 변수 값에서 `$Sender` 자동 변수는 sender 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-162">In the value of the **Action** parameter, the `$Sender` automatic variable contains the sender object.</span></span>

- <span data-ttu-id="f6a08-163">SourceEventArgs.</span><span class="sxs-lookup"><span data-stu-id="f6a08-163">SourceEventArgs.</span></span> <span data-ttu-id="f6a08-164">EventArgs에서 파생된 첫 번째 매개 변수입니다(있는 경우).</span><span class="sxs-lookup"><span data-stu-id="f6a08-164">The first parameter that derives from EventArgs, if it exists.</span></span> <span data-ttu-id="f6a08-165">예를 들어, 시그니처에 Object sender, **timers.elapsedeventargs가** e 형식이 있는 타이머 경과 이벤트에서 **sourceeventargs** 속성에는 **timers.elapsedeventargs가** 가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-165">For example, in a timer elapsed event in which the signature has the form Object sender, **Timers.ElapsedEventArgs** e, the **SourceEventArgs** property would contain the **Timers.ElapsedEventArgs**.</span></span> <span data-ttu-id="f6a08-166">**Action** 매개 변수 값에서 `$EventArgs` 자동 변수에이 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-166">In the value of the **Action** parameter, the `$EventArgs` automatic variable contains this value.</span></span>

- <span data-ttu-id="f6a08-167">SourceArgs입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-167">SourceArgs.</span></span> <span data-ttu-id="f6a08-168">원래 이벤트 서명의 모든 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-168">All parameters of the original event signature.</span></span> <span data-ttu-id="f6a08-169">표준 이벤트 시그니처의 경우 `$Args[0]` 는 보낸 사람을 나타내며 `$Args[1]` **sourceeventargs** 를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-169">For a standard event signature, `$Args[0]` represents the sender, and `$Args[1]` represents the **SourceEventArgs**.</span></span> <span data-ttu-id="f6a08-170">**Action** 매개 변수 값에서 `$Args` 자동 변수에이 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-170">In the value of the **Action** parameter, the `$Args` automatic variable contains this value.</span></span>

- <span data-ttu-id="f6a08-171">SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="f6a08-171">SourceIdentifier.</span></span> <span data-ttu-id="f6a08-172">이벤트 구독을 식별하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-172">A string that identifies the event subscription.</span></span> <span data-ttu-id="f6a08-173">**Action** 매개 변수 값에서 자동 변수의 **SourceIdentifier** 속성은 `$Event` 이 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-173">In the value of the **Action** parameter, the **SourceIdentifier** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="f6a08-174">TimeGenerated.</span><span class="sxs-lookup"><span data-stu-id="f6a08-174">TimeGenerated.</span></span> <span data-ttu-id="f6a08-175">이벤트가 생성 된 시간을 나타내는 **DateTime** 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-175">A **DateTime** object that represents the time at which the event was generated.</span></span>
  <span data-ttu-id="f6a08-176">**Action** 매개 변수 값에서 자동 변수의 **timegenerated** 속성에 `$Event` 이 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-176">In the value of the **Action** parameter, the **TimeGenerated** property of the `$Event` automatic variable contains this value.</span></span>

- <span data-ttu-id="f6a08-177">MessageData.</span><span class="sxs-lookup"><span data-stu-id="f6a08-177">MessageData.</span></span> <span data-ttu-id="f6a08-178">이벤트 구독과 연결된 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-178">Data associated with the event subscription.</span></span> <span data-ttu-id="f6a08-179">사용자는 이벤트를 등록할 때 이 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-179">Users specify this data when they register an event.</span></span> <span data-ttu-id="f6a08-180">**Action** 매개 변수 값에서 자동 변수의 **messagedata** 속성에 `$Event` 이 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6a08-180">In the value of the **Action** parameter, the **MessageData** property of the `$Event` automatic variable contains this value.</span></span>

## <span data-ttu-id="f6a08-181">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f6a08-181">RELATED LINKS</span></span>

[<span data-ttu-id="f6a08-182">New-Event</span><span class="sxs-lookup"><span data-stu-id="f6a08-182">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="f6a08-183">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="f6a08-183">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="f6a08-184">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="f6a08-184">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="f6a08-185">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="f6a08-185">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="f6a08-186">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="f6a08-186">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="f6a08-187">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="f6a08-187">Wait-Event</span></span>](Wait-Event.md)
