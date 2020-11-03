---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: cf7236d31ccd248701a0464c84e94d0d910cc26f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216057"
---
# <span data-ttu-id="e8db3-103">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="e8db3-103">Remove-Event</span></span>

## <span data-ttu-id="e8db3-104">개요</span><span class="sxs-lookup"><span data-stu-id="e8db3-104">SYNOPSIS</span></span>
<span data-ttu-id="e8db3-105">이벤트 큐에서 이벤트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-105">Deletes events from the event queue.</span></span>

## <span data-ttu-id="e8db3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e8db3-106">SYNTAX</span></span>

### <span data-ttu-id="e8db3-107">BySource (기본값)</span><span class="sxs-lookup"><span data-stu-id="e8db3-107">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e8db3-108">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="e8db3-108">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e8db3-109">설명</span><span class="sxs-lookup"><span data-stu-id="e8db3-109">DESCRIPTION</span></span>
<span data-ttu-id="e8db3-110">**Remove 이벤트** cmdlet은 현재 세션의 이벤트 큐에서 이벤트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-110">The **Remove-Event** cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="e8db3-111">이 cmdlet은 현재 큐에 있는 이벤트만 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-111">This cmdlet deletes only the events currently in the queue.</span></span>
<span data-ttu-id="e8db3-112">이벤트 등록이나 가입을 취소하려면 Unregister-Event cmdlet을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="e8db3-112">To cancel event registrations or unsubscribe, use the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="e8db3-113">예제</span><span class="sxs-lookup"><span data-stu-id="e8db3-113">EXAMPLES</span></span>

### <span data-ttu-id="e8db3-114">예제 1: 소스 식별자로 이벤트 제거</span><span class="sxs-lookup"><span data-stu-id="e8db3-114">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="e8db3-115">이 명령은 이벤트 큐에서 시작 된 프로세스의 원본 식별자를 사용 하 여 이벤트를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-115">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="e8db3-116">예제 2: 이벤트 식별자로 이벤트 제거</span><span class="sxs-lookup"><span data-stu-id="e8db3-116">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="e8db3-117">이 명령은 이벤트 ID가 30인 이벤트를 이벤트 큐에서 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-117">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="e8db3-118">예제 3: 모든 이벤트 제거</span><span class="sxs-lookup"><span data-stu-id="e8db3-118">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="e8db3-119">이 명령은 이벤트 큐에서 모든 이벤트를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-119">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="e8db3-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e8db3-120">PARAMETERS</span></span>

### <span data-ttu-id="e8db3-121">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="e8db3-121">-EventIdentifier</span></span>
<span data-ttu-id="e8db3-122">Cmdlet이 삭제 하는 이벤트 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-122">Specifies the event identifier for which the cmdlet deletes.</span></span>
<span data-ttu-id="e8db3-123">*EventIdentifier* 또는 *SourceIdentifier* 매개 변수는 모든 명령에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-123">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e8db3-124">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="e8db3-124">-SourceIdentifier</span></span>
<span data-ttu-id="e8db3-125">이 cmdlet이 이벤트를 삭제할 원본 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-125">Specifies the source identifier for which this cmdlet deletes events from.</span></span>
<span data-ttu-id="e8db3-126">와일드카드는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-126">Wildcards are not permitted.</span></span>
<span data-ttu-id="e8db3-127">*EventIdentifier* 또는 *SourceIdentifier* 매개 변수는 모든 명령에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-127">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e8db3-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e8db3-128">-Confirm</span></span>
<span data-ttu-id="e8db3-129">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-129">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e8db3-130">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e8db3-130">-WhatIf</span></span>
<span data-ttu-id="e8db3-131">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-131">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="e8db3-132">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-132">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e8db3-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e8db3-133">CommonParameters</span></span>
<span data-ttu-id="e8db3-134">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e8db3-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e8db3-135">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e8db3-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e8db3-136">입력</span><span class="sxs-lookup"><span data-stu-id="e8db3-136">INPUTS</span></span>

### <span data-ttu-id="e8db3-137">PSEventArgs.</span><span class="sxs-lookup"><span data-stu-id="e8db3-137">System.Management.Automation.PSEventArgs</span></span>
<span data-ttu-id="e8db3-138">Get-Event에서 **이벤트를 제거** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-138">You can pipe events from Get-Event to **Remove-Event** .</span></span>

## <span data-ttu-id="e8db3-139">출력</span><span class="sxs-lookup"><span data-stu-id="e8db3-139">OUTPUTS</span></span>

### <span data-ttu-id="e8db3-140">없음</span><span class="sxs-lookup"><span data-stu-id="e8db3-140">None</span></span>
<span data-ttu-id="e8db3-141">이 cmdlet에서 어떠한 출력도 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-141">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e8db3-142">참고</span><span class="sxs-lookup"><span data-stu-id="e8db3-142">NOTES</span></span>

* <span data-ttu-id="e8db3-143">이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="e8db3-144">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="e8db3-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="e8db3-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e8db3-145">RELATED LINKS</span></span>

[<span data-ttu-id="e8db3-146">Get-Event</span><span class="sxs-lookup"><span data-stu-id="e8db3-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="e8db3-147">New-Event</span><span class="sxs-lookup"><span data-stu-id="e8db3-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="e8db3-148">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="e8db3-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="e8db3-149">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="e8db3-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="e8db3-150">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="e8db3-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="e8db3-151">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="e8db3-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="e8db3-152">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="e8db3-152">Wait-Event</span></span>](Wait-Event.md)
