---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: 8384cf6a4922bf408f4ac569f651c1a3b584d8af
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216010"
---
# <span data-ttu-id="fb6e5-103">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="fb6e5-103">Wait-Event</span></span>

## <span data-ttu-id="fb6e5-104">개요</span><span class="sxs-lookup"><span data-stu-id="fb6e5-104">SYNOPSIS</span></span>
<span data-ttu-id="fb6e5-105">계속 실행하기 전에 특정 이벤트가 발생할 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-105">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="fb6e5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb6e5-106">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="fb6e5-107">설명</span><span class="sxs-lookup"><span data-stu-id="fb6e5-107">DESCRIPTION</span></span>

<span data-ttu-id="fb6e5-108">`Wait-Event`Cmdlet은 특정 이벤트가 발생할 때까지 스크립트 또는 함수 실행을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-108">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="fb6e5-109">이벤트가 검색되면 실행을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-109">Execution resumes when the event is detected.</span></span> <span data-ttu-id="fb6e5-110">대기를 취소 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-110">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="fb6e5-111">이벤트를 폴링하는 대신 이 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-111">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="fb6e5-112">또한 두 가지 방법으로 이벤트에 대 한 응답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-112">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="fb6e5-113">이벤트 구독의 **Action** 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="fb6e5-113">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="fb6e5-114">이벤트가 반환 되 고 작업으로 응답할 때까지 기다리는 중</span><span class="sxs-lookup"><span data-stu-id="fb6e5-114">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="fb6e5-115">예제</span><span class="sxs-lookup"><span data-stu-id="fb6e5-115">EXAMPLES</span></span>

### <span data-ttu-id="fb6e5-116">예제 1: 다음 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="fb6e5-116">Example 1: Wait for the next event</span></span>

<span data-ttu-id="fb6e5-117">이 예에서는 다음 이벤트가 발생할 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-117">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="fb6e5-118">예제 2: 지정 된 소스 식별자를 사용 하 여 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="fb6e5-118">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="fb6e5-119">이 예제에서는 다음 이벤트가 발생 하 고 원본 식별자가 ProcessStarted 인 경우를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-119">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="fb6e5-120">예제 3: 타이머가 경과 된 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="fb6e5-120">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="fb6e5-121">이 예제에서는 cmdlet을 사용 하 여 `Wait-Event` 2000 밀리초로 설정 된 타이머의 타이머 이벤트를 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-121">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

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

### <span data-ttu-id="fb6e5-122">예제 4: 지정 된 시간 제한 후 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="fb6e5-122">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="fb6e5-123">이 예제에서는 다음 이벤트가 발생 하 고 원본 식별자가 **Processstarted** 인 경우 최대 90 초 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-123">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted** .</span></span> <span data-ttu-id="fb6e5-124">지정한 시간이 만료되면 대기가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-124">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="fb6e5-125">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="fb6e5-125">PARAMETERS</span></span>

### <span data-ttu-id="fb6e5-126">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="fb6e5-126">-SourceIdentifier</span></span>

<span data-ttu-id="fb6e5-127">이 cmdlet이 이벤트를 대기 하는 원본 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-127">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="fb6e5-128">기본적으로는 `Wait-Event` 이벤트를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-128">By default, `Wait-Event` waits for any event.</span></span>

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

### <span data-ttu-id="fb6e5-129">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="fb6e5-129">-Timeout</span></span>

<span data-ttu-id="fb6e5-130">이벤트가 발생할 때까지 대기 하는 최대 시간 (초)을 지정 합니다 `Wait-Event` .</span><span class="sxs-lookup"><span data-stu-id="fb6e5-130">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="fb6e5-131">기본값 -1은 무기한 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-131">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="fb6e5-132">이 타이밍은 명령을 제출할 때 시작 됩니다 `Wait-Event` .</span><span class="sxs-lookup"><span data-stu-id="fb6e5-132">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="fb6e5-133">지정한 시간을 초과하면 이벤트가 발생하지 않았어도 대기가 종료되고 명령 프롬프트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-133">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="fb6e5-134">오류 메시지는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-134">No error message is displayed.</span></span>

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

### <span data-ttu-id="fb6e5-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb6e5-135">CommonParameters</span></span>

<span data-ttu-id="fb6e5-136">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb6e5-137">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb6e5-138">입력</span><span class="sxs-lookup"><span data-stu-id="fb6e5-138">INPUTS</span></span>

### <span data-ttu-id="fb6e5-139">System.String</span><span class="sxs-lookup"><span data-stu-id="fb6e5-139">System.String</span></span>

## <span data-ttu-id="fb6e5-140">출력</span><span class="sxs-lookup"><span data-stu-id="fb6e5-140">OUTPUTS</span></span>

### <span data-ttu-id="fb6e5-141">PSEventArgs.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-141">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="fb6e5-142">참고</span><span class="sxs-lookup"><span data-stu-id="fb6e5-142">NOTES</span></span>

<span data-ttu-id="fb6e5-143">이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="fb6e5-144">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="fb6e5-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="fb6e5-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="fb6e5-145">RELATED LINKS</span></span>

[<span data-ttu-id="fb6e5-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="fb6e5-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="fb6e5-147">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="fb6e5-147">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="fb6e5-148">New-Event</span><span class="sxs-lookup"><span data-stu-id="fb6e5-148">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="fb6e5-149">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="fb6e5-149">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="fb6e5-150">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="fb6e5-150">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="fb6e5-151">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="fb6e5-151">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="fb6e5-152">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="fb6e5-152">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="fb6e5-153">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="fb6e5-153">Wait-Event</span></span>](Wait-Event.md)
