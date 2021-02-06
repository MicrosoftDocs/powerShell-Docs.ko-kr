---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: caf2a1c80848d3140e7ad46fdf54dbe71886c633
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602430"
---
# <span data-ttu-id="35ec6-102">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="35ec6-102">Wait-Event</span></span>

## <span data-ttu-id="35ec6-103">개요</span><span class="sxs-lookup"><span data-stu-id="35ec6-103">SYNOPSIS</span></span>
<span data-ttu-id="35ec6-104">계속 실행하기 전에 특정 이벤트가 발생할 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-104">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="35ec6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="35ec6-105">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="35ec6-106">설명</span><span class="sxs-lookup"><span data-stu-id="35ec6-106">DESCRIPTION</span></span>

<span data-ttu-id="35ec6-107">`Wait-Event`Cmdlet은 특정 이벤트가 발생할 때까지 스크립트 또는 함수 실행을 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-107">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="35ec6-108">이벤트가 검색되면 실행을 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-108">Execution resumes when the event is detected.</span></span> <span data-ttu-id="35ec6-109">대기를 취소 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-109">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="35ec6-110">이벤트를 폴링하는 대신 이 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-110">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="35ec6-111">또한 두 가지 방법으로 이벤트에 대 한 응답을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-111">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="35ec6-112">이벤트 구독의 **Action** 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="35ec6-112">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="35ec6-113">이벤트가 반환 되 고 작업으로 응답할 때까지 기다리는 중</span><span class="sxs-lookup"><span data-stu-id="35ec6-113">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="35ec6-114">예제</span><span class="sxs-lookup"><span data-stu-id="35ec6-114">EXAMPLES</span></span>

### <span data-ttu-id="35ec6-115">예제 1: 다음 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="35ec6-115">Example 1: Wait for the next event</span></span>

<span data-ttu-id="35ec6-116">이 예에서는 다음 이벤트가 발생할 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-116">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="35ec6-117">예제 2: 지정 된 소스 식별자를 사용 하 여 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="35ec6-117">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="35ec6-118">이 예제에서는 다음 이벤트가 발생 하 고 원본 식별자가 ProcessStarted 인 경우를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-118">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="35ec6-119">예제 3: 타이머가 경과 된 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="35ec6-119">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="35ec6-120">이 예제에서는 cmdlet을 사용 하 여 `Wait-Event` 2000 밀리초로 설정 된 타이머의 타이머 이벤트를 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-120">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

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

### <span data-ttu-id="35ec6-121">예제 4: 지정 된 시간 제한 후 이벤트 대기</span><span class="sxs-lookup"><span data-stu-id="35ec6-121">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="35ec6-122">이 예제에서는 다음 이벤트가 발생 하 고 원본 식별자가 **Processstarted** 인 경우 최대 90 초 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-122">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted**.</span></span> <span data-ttu-id="35ec6-123">지정한 시간이 만료되면 대기가 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-123">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="35ec6-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="35ec6-124">PARAMETERS</span></span>

### <span data-ttu-id="35ec6-125">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="35ec6-125">-SourceIdentifier</span></span>

<span data-ttu-id="35ec6-126">이 cmdlet이 이벤트를 대기 하는 원본 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-126">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="35ec6-127">기본적으로는 `Wait-Event` 이벤트를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-127">By default, `Wait-Event` waits for any event.</span></span>

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

### <span data-ttu-id="35ec6-128">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="35ec6-128">-Timeout</span></span>

<span data-ttu-id="35ec6-129">이벤트가 발생할 때까지 대기 하는 최대 시간 (초)을 지정 합니다 `Wait-Event` .</span><span class="sxs-lookup"><span data-stu-id="35ec6-129">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="35ec6-130">기본값 -1은 무기한 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-130">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="35ec6-131">이 타이밍은 명령을 제출할 때 시작 됩니다 `Wait-Event` .</span><span class="sxs-lookup"><span data-stu-id="35ec6-131">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="35ec6-132">지정한 시간을 초과하면 이벤트가 발생하지 않았어도 대기가 종료되고 명령 프롬프트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-132">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="35ec6-133">오류 메시지는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-133">No error message is displayed.</span></span>

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

### <span data-ttu-id="35ec6-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="35ec6-134">CommonParameters</span></span>

<span data-ttu-id="35ec6-135">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="35ec6-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="35ec6-136">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="35ec6-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="35ec6-137">입력</span><span class="sxs-lookup"><span data-stu-id="35ec6-137">INPUTS</span></span>

### <span data-ttu-id="35ec6-138">System.String</span><span class="sxs-lookup"><span data-stu-id="35ec6-138">System.String</span></span>

## <span data-ttu-id="35ec6-139">출력</span><span class="sxs-lookup"><span data-stu-id="35ec6-139">OUTPUTS</span></span>

### <span data-ttu-id="35ec6-140">PSEventArgs.</span><span class="sxs-lookup"><span data-stu-id="35ec6-140">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="35ec6-141">참고</span><span class="sxs-lookup"><span data-stu-id="35ec6-141">NOTES</span></span>

<span data-ttu-id="35ec6-142">이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-142">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="35ec6-143">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="35ec6-143">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="35ec6-144">관련 링크</span><span class="sxs-lookup"><span data-stu-id="35ec6-144">RELATED LINKS</span></span>

[<span data-ttu-id="35ec6-145">Get-Event</span><span class="sxs-lookup"><span data-stu-id="35ec6-145">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="35ec6-146">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="35ec6-146">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="35ec6-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="35ec6-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="35ec6-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="35ec6-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="35ec6-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="35ec6-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="35ec6-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="35ec6-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="35ec6-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="35ec6-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="35ec6-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="35ec6-152">Wait-Event</span></span>](Wait-Event.md)

