---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 269eb4e8252b29a01cce043c954bb88d651be0e5
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216177"
---
# <span data-ttu-id="4107b-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="4107b-103">Unregister-Event</span></span>

## <span data-ttu-id="4107b-104">개요</span><span class="sxs-lookup"><span data-stu-id="4107b-104">SYNOPSIS</span></span>
<span data-ttu-id="4107b-105">이벤트 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="4107b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4107b-106">SYNTAX</span></span>

### <span data-ttu-id="4107b-107">BySource (기본값)</span><span class="sxs-lookup"><span data-stu-id="4107b-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4107b-108">ById</span><span class="sxs-lookup"><span data-stu-id="4107b-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4107b-109">설명</span><span class="sxs-lookup"><span data-stu-id="4107b-109">DESCRIPTION</span></span>
<span data-ttu-id="4107b-110">Register-engineevent, Register-ObjectEvent 또는 Register-WmiEvent cmdlet을 사용 하 여 생성 된 이벤트 등록을 취소 **하는 이벤트를 취소** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-110">The **Unregister-Event** cmdlet cancels an event subscription that was created by using the Register-EngineEvent, Register-ObjectEvent, or Register-WmiEvent cmdlet.</span></span>

<span data-ttu-id="4107b-111">이벤트 구독을 취소하면 이벤트 구독자가 세션에서 삭제되고 가입된 이벤트는 더 이상 이벤트 큐에 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span>
<span data-ttu-id="4107b-112">New-Event cmdlet을 사용하여 만든 이벤트에 대한 가입을 취소하면 새 이벤트도 세션에서 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-112">When you cancel a subscription to an event created by using the New-Event cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="4107b-113">**등록 취소** 이벤트는 이벤트 큐에서 이벤트를 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-113">**Unregister-Event** does not delete events from the event queue.</span></span>
<span data-ttu-id="4107b-114">이벤트를 삭제하려면 Remove-Event cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-114">To delete events, use the Remove-Event cmdlet.</span></span>

## <span data-ttu-id="4107b-115">예제</span><span class="sxs-lookup"><span data-stu-id="4107b-115">EXAMPLES</span></span>

### <span data-ttu-id="4107b-116">예제 1: 소스 식별자로 이벤트 구독 취소</span><span class="sxs-lookup"><span data-stu-id="4107b-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="4107b-117">이 명령은 ProcessStarted의 원본 식별자를 가진 이벤트 구독을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="4107b-118">이벤트의 원본 식별자를 찾으려면 Get-Event cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-118">To find the source identifier of an event, use the Get-Event cmdlet.</span></span>
<span data-ttu-id="4107b-119">이벤트 구독의 원본 식별자를 찾으려면 **Get EventSubscriber** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-119">To find the source identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="4107b-120">예제 2: 구독 식별자로 이벤트 구독 취소</span><span class="sxs-lookup"><span data-stu-id="4107b-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="4107b-121">이 명령은 가입 식별자가 2인 이벤트 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="4107b-122">이벤트 구독의 구독 식별자를 찾으려면 **Get EventSubscriber** cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-122">To find the subscription identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="4107b-123">예 3: 모든 이벤트 구독 취소</span><span class="sxs-lookup"><span data-stu-id="4107b-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="4107b-124">이 명령은 세션에서 모든 이벤트 구독을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="4107b-125">이 명령은 이벤트 등록 cmdlet의 *supportevent* 매개 변수를 사용 하 여 숨겨진 구독자를 포함 하 여 세션의 모든 이벤트 구독자 개체 **를 가져오는 데** 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-125">The command uses the **Get-EventSubscriber** cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the *SupportEvent* parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="4107b-126">파이프라인 연산자 (|)를 사용 하 여 구독자 개체를 **등록 취소** 로 보내면이 이벤트는 세션에서 해당 개체를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-126">It uses a pipeline operator (|) to send the subscriber objects to **Unregister-Event** , which deletes them from the session.</span></span>
<span data-ttu-id="4107b-127">작업을 완료 하려면 **이벤트 등록 취소** 에도 *Force* 매개 변수가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-127">To complete the task, the *Force* parameter is also required on **Unregister-Event** .</span></span>

## <span data-ttu-id="4107b-128">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="4107b-128">PARAMETERS</span></span>

### <span data-ttu-id="4107b-129">-Force</span><span class="sxs-lookup"><span data-stu-id="4107b-129">-Force</span></span>
<span data-ttu-id="4107b-130">**Register-wmievent** 및 **Register-engineevent** 의 *supportevent* 매개 **변수를 사용** 하 여 숨겨진 구독을 포함 하 여 모든 이벤트 구독을 취소 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-130">Cancels all event subscriptions, including subscriptions that were hidden by using the *SupportEvent* parameter of **Register-ObjectEvent** , **Register-WmiEvent** , and **Register-EngineEvent** .</span></span>

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

### <span data-ttu-id="4107b-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="4107b-131">-SourceIdentifier</span></span>
<span data-ttu-id="4107b-132">이 cmdlet이 이벤트 구독을 취소 하는 원본 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="4107b-133">*SourceIdentifier* 또는 *SubscriptionId* 매개 변수는 모든 명령에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-133">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4107b-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="4107b-134">-SubscriptionId</span></span>
<span data-ttu-id="4107b-135">이 cmdlet이 이벤트 구독을 취소 하는 원본 식별자 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="4107b-136">*SourceIdentifier* 또는 *SubscriptionId* 매개 변수는 모든 명령에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-136">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="4107b-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4107b-137">-Confirm</span></span>
<span data-ttu-id="4107b-138">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-138">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4107b-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4107b-139">-WhatIf</span></span>
<span data-ttu-id="4107b-140">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-140">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4107b-141">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-141">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="4107b-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4107b-142">CommonParameters</span></span>
<span data-ttu-id="4107b-143">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4107b-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4107b-144">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4107b-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4107b-145">입력</span><span class="sxs-lookup"><span data-stu-id="4107b-145">INPUTS</span></span>

### <span data-ttu-id="4107b-146">PSEventSubscriber.</span><span class="sxs-lookup"><span data-stu-id="4107b-146">System.Management.Automation.PSEventSubscriber</span></span>
<span data-ttu-id="4107b-147">Get-EventSubscriber 출력을 **이벤트 등록 취소** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-147">You can pipe the output from Get-EventSubscriber to **Unregister-Event** .</span></span>

## <span data-ttu-id="4107b-148">출력</span><span class="sxs-lookup"><span data-stu-id="4107b-148">OUTPUTS</span></span>

### <span data-ttu-id="4107b-149">없음</span><span class="sxs-lookup"><span data-stu-id="4107b-149">None</span></span>
<span data-ttu-id="4107b-150">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="4107b-151">참고</span><span class="sxs-lookup"><span data-stu-id="4107b-151">NOTES</span></span>

* <span data-ttu-id="4107b-152">이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="4107b-153">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

  <span data-ttu-id="4107b-154">**Register-engineevent** cmdlet을 사용 하 여 이벤트를 구독 하지 않은 경우 **이벤트 등록 취소** 는 New-Event cmdlet을 사용 하 여 만든 이벤트를 삭제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-154">**Unregister-Event** cannot delete events created by using the New-Event cmdlet unless you have subscribed to the event by using the **Register-EngineEvent** cmdlet.</span></span>
<span data-ttu-id="4107b-155">세션에서 사용자 지정 이벤트를 삭제하려면 프로그래밍 방식으로 제거하거나 세션을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4107b-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

*

## <span data-ttu-id="4107b-156">관련 링크</span><span class="sxs-lookup"><span data-stu-id="4107b-156">RELATED LINKS</span></span>

[<span data-ttu-id="4107b-157">Get-Event</span><span class="sxs-lookup"><span data-stu-id="4107b-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="4107b-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="4107b-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="4107b-159">New-Event</span><span class="sxs-lookup"><span data-stu-id="4107b-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="4107b-160">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="4107b-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="4107b-161">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="4107b-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="4107b-162">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="4107b-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="4107b-163">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="4107b-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="4107b-164">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="4107b-164">Wait-Event</span></span>](Wait-Event.md)
