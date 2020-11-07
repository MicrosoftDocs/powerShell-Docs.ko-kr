---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 0e7f263d309908a4a62187d3d1cc5ef08283e0c3
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344408"
---
# <span data-ttu-id="a3526-103">New-Event</span><span class="sxs-lookup"><span data-stu-id="a3526-103">New-Event</span></span>

## <span data-ttu-id="a3526-104">개요</span><span class="sxs-lookup"><span data-stu-id="a3526-104">SYNOPSIS</span></span>
<span data-ttu-id="a3526-105">새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-105">Creates a new event.</span></span>

## <span data-ttu-id="a3526-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a3526-106">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="a3526-107">설명</span><span class="sxs-lookup"><span data-stu-id="a3526-107">DESCRIPTION</span></span>

<span data-ttu-id="a3526-108">`New-Event`Cmdlet은 새 사용자 지정 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-108">The `New-Event` cmdlet creates a new custom event.</span></span>

<span data-ttu-id="a3526-109">사용자 지정 이벤트를 사용하여 하드웨어 또는 시스템 상태, 애플리케이션 상태, 디스크 상태, 네트워크 상태 또는 백그라운드 작업 완료 등 프로그램에서 감지할 수 있는 변경 내용과 프로그램의 상태 변경 내용을 사용자에게 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-109">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="a3526-110">사용자 지정 이벤트는 발생할 때마다 세션의 이벤트 큐에 자동으로 추가되므로 구독할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-110">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span> <span data-ttu-id="a3526-111">그러나 이벤트를 로컬 세션으로 전달 하거나 이벤트에 응답할 작업을 지정 하려는 경우 cmdlet을 사용 하 여 `Register-EngineEvent` 사용자 지정 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-111">However, if you want to forward an event to the local session or specify an action to respond to the event, use the `Register-EngineEvent` cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="a3526-112">사용자 지정 이벤트를 구독하면 이벤트 구독자가 세션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-112">When you subscribe to a custom event, the event subscriber is added to your session.</span></span> <span data-ttu-id="a3526-113">Cmdlet을 사용 하 여 이벤트 구독을 취소 하면 `Unregister-Event` 이벤트 구독자 및 사용자 지정 이벤트가 세션에서 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-113">If you cancel the event subscription by using the `Unregister-Event` cmdlet, the event subscriber and custom event are deleted from the session.</span></span> <span data-ttu-id="a3526-114">사용자 지정 이벤트를 구독 하지 않는 경우 이벤트를 삭제 하려면 프로그램 조건을 변경 하거나 PowerShell 세션을 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-114">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the PowerShell session.</span></span>

## <span data-ttu-id="a3526-115">예제</span><span class="sxs-lookup"><span data-stu-id="a3526-115">EXAMPLES</span></span>

### <span data-ttu-id="a3526-116">예제 1: 이벤트 큐에 새 이벤트 만들기</span><span class="sxs-lookup"><span data-stu-id="a3526-116">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="a3526-117">이 명령은 PowerShell 이벤트 큐에 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-117">This command creates a new event in the PowerShell event queue.</span></span> <span data-ttu-id="a3526-118">**Windows. Timer** 개체를 사용 하 여 이벤트를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-118">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="a3526-119">예제 2: 다른 이벤트에 대 한 응답으로 이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="a3526-119">Example 2: Raise an event in response to another event</span></span>

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

<span data-ttu-id="a3526-120">이 샘플 함수는 cmdlet을 사용 하 여 `New-Event` 다른 이벤트에 대 한 응답으로 이벤트를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-120">This sample function uses the `New-Event` cmdlet to raise an event in response to another event.</span></span> <span data-ttu-id="a3526-121">이 명령은 cmdlet을 사용 하 여 `Register-ObjectEvent` 새 프로세스를 만들 때 발생 하는 WMI(Windows Management Instrumentation) (WMI) 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-121">The command uses the `Register-ObjectEvent` cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span> <span data-ttu-id="a3526-122">이 명령은 cmdlet의 **Action** 매개 변수를 사용 하 여 cmdlet을 호출 합니다. 그러면이 `New-Event` cmdlet이 새 이벤트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-122">The command uses the **Action** parameter of the cmdlet to call the `New-Event` cmdlet, which creates the new event.</span></span>

<span data-ttu-id="a3526-123">에서 발생 하는 이벤트는 `New-Event` PowerShell 이벤트 큐에 자동으로 추가 되므로 해당 이벤트를 등록할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-123">Because the events that `New-Event` raises are automatically added to the PowerShell event queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="a3526-124">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a3526-124">PARAMETERS</span></span>

### <span data-ttu-id="a3526-125">-EventArguments</span><span class="sxs-lookup"><span data-stu-id="a3526-125">-EventArguments</span></span>

<span data-ttu-id="a3526-126">이벤트 옵션이 포함된 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-126">Specifies an object that contains options for the event.</span></span>

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

### <span data-ttu-id="a3526-127">-MessageData</span><span class="sxs-lookup"><span data-stu-id="a3526-127">-MessageData</span></span>

<span data-ttu-id="a3526-128">이벤트와 연결된 추가 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-128">Specifies additional data associated with the event.</span></span> <span data-ttu-id="a3526-129">이 매개 변수 값은 이벤트 개체의 **MessageData** 속성에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-129">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

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

### <span data-ttu-id="a3526-130">-발신자</span><span class="sxs-lookup"><span data-stu-id="a3526-130">-Sender</span></span>

<span data-ttu-id="a3526-131">이벤트를 발생시키는 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-131">Specifies the object that raises the event.</span></span> <span data-ttu-id="a3526-132">기본값은 PowerShell 엔진입니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-132">The default is the PowerShell engine.</span></span>

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

### <span data-ttu-id="a3526-133">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="a3526-133">-SourceIdentifier</span></span>

<span data-ttu-id="a3526-134">새 이벤트의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-134">Specifies a name for the new event.</span></span> <span data-ttu-id="a3526-135">이 매개 변수는 필수이며 세션에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-135">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="a3526-136">이 매개 변수 값은 이벤트의 **SourceIdentifier** 속성에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-136">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

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

### <span data-ttu-id="a3526-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3526-137">CommonParameters</span></span>

<span data-ttu-id="a3526-138">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a3526-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3526-139">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a3526-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a3526-140">입력</span><span class="sxs-lookup"><span data-stu-id="a3526-140">INPUTS</span></span>

### <span data-ttu-id="a3526-141">없음</span><span class="sxs-lookup"><span data-stu-id="a3526-141">None</span></span>

<span data-ttu-id="a3526-142">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a3526-143">출력</span><span class="sxs-lookup"><span data-stu-id="a3526-143">OUTPUTS</span></span>

### <span data-ttu-id="a3526-144">PSEventArgs.</span><span class="sxs-lookup"><span data-stu-id="a3526-144">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="a3526-145">참고</span><span class="sxs-lookup"><span data-stu-id="a3526-145">NOTES</span></span>

<span data-ttu-id="a3526-146">Linux 또는 macOS 플랫폼에서 사용할 수 있는 이벤트 원본이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-146">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="a3526-147">새 사용자 지정 이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-147">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="a3526-148">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="a3526-148">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="a3526-149">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a3526-149">RELATED LINKS</span></span>

[<span data-ttu-id="a3526-150">Get-Event</span><span class="sxs-lookup"><span data-stu-id="a3526-150">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="a3526-151">Register-EngineEvent</span><span class="sxs-lookup"><span data-stu-id="a3526-151">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="a3526-152">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="a3526-152">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="a3526-153">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="a3526-153">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="a3526-154">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="a3526-154">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="a3526-155">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="a3526-155">Wait-Event</span></span>](Wait-Event.md)
