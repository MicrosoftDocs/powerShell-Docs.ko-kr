---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2020
ms.locfileid: "93219049"
---
# <span data-ttu-id="3404a-103">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="3404a-103">Register-WmiEvent</span></span>

## <span data-ttu-id="3404a-104">개요</span><span class="sxs-lookup"><span data-stu-id="3404a-104">SYNOPSIS</span></span>
<span data-ttu-id="3404a-105">WMI(Windows Management Instrumentation) 이벤트를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-105">Subscribes to a Windows Management Instrumentation (WMI) event.</span></span>

## <span data-ttu-id="3404a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3404a-106">SYNTAX</span></span>

### <span data-ttu-id="3404a-107">클래스 (기본값)</span><span class="sxs-lookup"><span data-stu-id="3404a-107">class (Default)</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="3404a-108">Query</span><span class="sxs-lookup"><span data-stu-id="3404a-108">query</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="3404a-109">설명</span><span class="sxs-lookup"><span data-stu-id="3404a-109">DESCRIPTION</span></span>

<span data-ttu-id="3404a-110">`Register-WmiEvent`Cmdlet은 로컬 컴퓨터 또는 원격 컴퓨터에서 WMI(Windows Management Instrumentation) (WMI) 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-110">The `Register-WmiEvent` cmdlet subscribes to Windows Management Instrumentation (WMI) events on the local computer or on a remote computer.</span></span>

<span data-ttu-id="3404a-111">구독한 WMI 이벤트가 발생할 경우 원격 컴퓨터에서 이벤트가 발생해도 로컬 세션의 이벤트 큐에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-111">When the subscribed WMI event is raised, it is added to the event queue in your local session even if the event occurs on a remote computer.</span></span> <span data-ttu-id="3404a-112">이벤트 큐에서 이벤트를 가져오려면 cmdlet을 사용 `Get-Event` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-112">To get events in the event queue, use the `Get-Event` cmdlet.</span></span>

<span data-ttu-id="3404a-113">의 매개 변수를 사용 하 여 `Register-WmiEvent` 원격 컴퓨터의 이벤트를 구독 하 고, 큐에서 이벤트를 식별 하는 데 도움이 될 수 있는 이벤트의 속성 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-113">You can use the parameters of `Register-WmiEvent` to subscribe to events on remote computers and to specify the property values of the events that can help you identify the event in the queue.</span></span> <span data-ttu-id="3404a-114">**Action** 매개 변수를 사용 하 여 구독 된 이벤트가 발생할 때 수행할 작업을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-114">You can also use the **Action** parameter to specify actions to take when a subscribed event is raised.</span></span>

<span data-ttu-id="3404a-115">이벤트를 구독하면 이벤트 구독자가 세션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-115">When you subscribe to an event, an event subscriber is added to your session.</span></span> <span data-ttu-id="3404a-116">세션의 이벤트 구독자를 가져오려면 cmdlet을 사용 합니다 `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="3404a-116">To get the event subscribers in the session, use the `Get-EventSubscriber` cmdlet.</span></span> <span data-ttu-id="3404a-117">구독을 취소 하려면 `Unregister-Event` 세션에서 이벤트 구독자를 삭제 하는 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-117">To cancel the subscription, use the `Unregister-Event` cmdlet, which deletes the event subscriber from the session.</span></span>

<span data-ttu-id="3404a-118">Windows PowerShell 3.0에서 도입 된 새로운 CIM(Common Information Model) (CIM) cmdlet은 WMI cmdlet과 동일한 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-118">New Common Information Model (CIM) cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="3404a-119">CIM cmdlet은 Windows 운영 체제를 실행 하는 컴퓨터 및 다른 운영 체제를 실행 하는 컴퓨터를 관리 하는 데 동일한 기술을 사용할 수 있도록 하는 CIM 표준과 WS-Management (WSMan) 표준을 준수 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-119">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those that run other operating systems.</span></span> <span data-ttu-id="3404a-120">를 사용 하는 대신 `Register-WmiEvent` [CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) cmdlet을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-120">Instead of using `Register-WmiEvent`, consider using the [Register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) cmdlet.</span></span>

## <span data-ttu-id="3404a-121">예제</span><span class="sxs-lookup"><span data-stu-id="3404a-121">EXAMPLES</span></span>

### <span data-ttu-id="3404a-122">예제 1: 클래스에서 생성 된 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="3404a-122">Example 1: Subscribe to events generated by a class</span></span>

<span data-ttu-id="3404a-123">이 명령은 **Win32_ProcessStartTrace** 클래스에 의해 생성 된 이벤트를 구독 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-123">This command subscribes to the events generated by the **Win32_ProcessStartTrace** class.</span></span> <span data-ttu-id="3404a-124">이 클래스는 프로세스가 시작될 때마다 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-124">This class raises an event whenever a process starts.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="3404a-125">예 2: 프로세스에 대 한 생성 이벤트 구독</span><span class="sxs-lookup"><span data-stu-id="3404a-125">Example 2: Subscribe to creation events for a process</span></span>

<span data-ttu-id="3404a-126">이 명령은 쿼리를 사용하여 Win32_process 인스턴스 만들기 이벤트를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-126">This command uses a query to subscribe to Win32_process instance creation events.</span></span>

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### <span data-ttu-id="3404a-127">예제 3: 작업을 사용 하 여 이벤트에 응답</span><span class="sxs-lookup"><span data-stu-id="3404a-127">Example 3: Use an action to respond to an event</span></span>

<span data-ttu-id="3404a-128">이 예제에서는 작업을 사용하여 이벤트에 응답하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-128">This example shows how to use an action to respond to an event.</span></span> <span data-ttu-id="3404a-129">이 경우 프로세스가 시작 되 면 `Start-Process` 현재 세션의 모든 명령이 XML 파일에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-129">In this case, when a process starts, any `Start-Process` commands in the current session are written to an XML file.</span></span>

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

<span data-ttu-id="3404a-130">**Action** 매개 변수를 사용 하는 경우는 `Register-WmiEvent` 이벤트 동작을 나타내는 백그라운드 작업을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-130">When you use the **Action** parameter, `Register-WmiEvent` returns a background job that represents the event action.</span></span> <span data-ttu-id="3404a-131">**작업** cmdlet (예: 및)을 사용 `Get-Job` `Receive-Job` 하 여 이벤트 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-131">You can use the **Job** cmdlets, such as `Get-Job` and `Receive-Job`, to manage the event job.</span></span>

<span data-ttu-id="3404a-132">자세한 내용은 about_Jobs를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3404a-132">For more information, see about_Jobs.</span></span>

### <span data-ttu-id="3404a-133">예제 4: 원격 컴퓨터의 이벤트 등록</span><span class="sxs-lookup"><span data-stu-id="3404a-133">Example 4: Register for events on a remote computer</span></span>

<span data-ttu-id="3404a-134">이 예제에서는 Server01 원격 컴퓨터의 이벤트를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-134">This example registers for events on the Server01 remote computer.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

<span data-ttu-id="3404a-135">WMI에서 이벤트를 로컬 컴퓨터에 반환하고 현재 세션의 이벤트 큐에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-135">WMI returns the events to the local computer and stores them in the event queue in the current session.</span></span> <span data-ttu-id="3404a-136">이벤트를 검색 하려면 로컬 `Get-Event` 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-136">To retrieve the events, run a local `Get-Event` command.</span></span>

## <span data-ttu-id="3404a-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3404a-137">PARAMETERS</span></span>

### <span data-ttu-id="3404a-138">-Action</span><span class="sxs-lookup"><span data-stu-id="3404a-138">-Action</span></span>

<span data-ttu-id="3404a-139">이벤트를 처리하는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-139">Specifies commands that handle the events.</span></span> <span data-ttu-id="3404a-140">이벤트 큐에 이벤트를 전송 하는 대신 이벤트를 발생 시킬 때 **Action** 매개 변수의 명령이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-140">The commands in the **Action** parameter run when an event is raised instead of sending the event to the event queue.</span></span> <span data-ttu-id="3404a-141">명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-141">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="3404a-142">**Action** 값에는 `$Event` `$EventSubscriber` `$Sender` `$EventArgs` `$Args` **동작** 스크립트 블록에 이벤트 정보를 제공 하는,,, 및 자동 변수가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-142">The value of **Action** can include the `$Event`, `$EventSubscriber`, `$Sender`, `$EventArgs`, and `$Args` automatic variables, which provide information about the event to the **Action** script block.</span></span> <span data-ttu-id="3404a-143">자세한 내용은 about_Automatic_Variables를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3404a-143">For more information, see about_Automatic_Variables.</span></span>

<span data-ttu-id="3404a-144">작업을 지정 하면 `Register-WmiEvent` 는 해당 동작을 나타내는 이벤트 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-144">When you specify an action, `Register-WmiEvent` returns an event job object that represents that action.</span></span> <span data-ttu-id="3404a-145">**작업** 명사 ( **job** cmdlet)를 포함 하는 cmdlet을 사용 하 여 이벤트 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-145">You can use the cmdlets that contain the **Job** noun (the **Job** cmdlets) to manage the event job.</span></span>

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

### <span data-ttu-id="3404a-146">-클래스</span><span class="sxs-lookup"><span data-stu-id="3404a-146">-Class</span></span>

<span data-ttu-id="3404a-147">구독할 이벤트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-147">Specifies the event to which you are subscribing.</span></span> <span data-ttu-id="3404a-148">이벤트를 생성하는 WMI 클래스를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-148">Enter the WMI class that generates the events.</span></span> <span data-ttu-id="3404a-149">**클래스** 또는 **쿼리** 매개 변수는 모든 명령에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-149">A **Class** or **Query** parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3404a-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="3404a-150">-ComputerName</span></span>

<span data-ttu-id="3404a-151">명령이 실행 되는 컴퓨터의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-151">Specifies the name of the computer on which the command runs.</span></span> <span data-ttu-id="3404a-152">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-152">The default is the local computer.</span></span>

<span data-ttu-id="3404a-153">컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="3404a-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of the computer.</span></span> <span data-ttu-id="3404a-154">로컬 컴퓨터를 지정 하려면 컴퓨터 이름, 점 ( `.` ) 또는 localhost를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-154">To specify the local computer, type the computer name, a dot (`.`), or localhost.</span></span>

<span data-ttu-id="3404a-155">이 매개 변수는 Windows PowerShell 원격 기능을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-155">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="3404a-156">원격 명령을 실행하도록 컴퓨터를 구성하지 않은 경우에도 **ComputerName** 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-156">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3404a-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="3404a-157">-Credential</span></span>

<span data-ttu-id="3404a-158">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-158">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="3404a-159">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-159">The default is the current user.</span></span>

<span data-ttu-id="3404a-160">User01 또는 Domain01\User01과 같은 사용자 이름을 입력 하거나, cmdlet에 의해 생성 된 것과 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3404a-160">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3404a-161">사용자 이름을 입력 하는 경우이 cmdlet은 암호를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-161">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3404a-162">-전달</span><span class="sxs-lookup"><span data-stu-id="3404a-162">-Forward</span></span>

<span data-ttu-id="3404a-163">이 cmdlet이이 구독에 대 한 이벤트를 로컬 컴퓨터의 세션으로 보내도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-163">Indicates that this cmdlet sends events for this subscription to the session on the local computer.</span></span>
<span data-ttu-id="3404a-164">원격 컴퓨터 또는 원격 세션에서 이벤트를 등록할 때 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-164">Use this parameter when you are registering for events on a remote computer or in a remote session.</span></span>

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

### <span data-ttu-id="3404a-165">-MaxTriggerCount</span><span class="sxs-lookup"><span data-stu-id="3404a-165">-MaxTriggerCount</span></span>

<span data-ttu-id="3404a-166">최대 트리거 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-166">Specifies the maximum trigger count.</span></span>

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

### <span data-ttu-id="3404a-167">-MessageData</span><span class="sxs-lookup"><span data-stu-id="3404a-167">-MessageData</span></span>

<span data-ttu-id="3404a-168">이 이벤트 구독에 연결할 추가 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-168">Specifies any additional data to be associated with this event subscription.</span></span> <span data-ttu-id="3404a-169">이 매개 변수 값은이 구독과 연결 된 모든 이벤트의 **Messagedata** 속성에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-169">The value of this parameter appears in the **MessageData** property of all events associated with this subscription.</span></span>

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

### <span data-ttu-id="3404a-170">-Namespace</span><span class="sxs-lookup"><span data-stu-id="3404a-170">-Namespace</span></span>

<span data-ttu-id="3404a-171">WMI 클래스의 네임스페이스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-171">Specifies the namespace of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3404a-172">-Query</span><span class="sxs-lookup"><span data-stu-id="3404a-172">-Query</span></span>

<span data-ttu-id="3404a-173">WMI 이벤트 클래스를 식별 하는 쿼리를 WQL(WMI Query Language) (WQL)로 지정 합니다 (예:) `select * from __InstanceDeletionEvent` .</span><span class="sxs-lookup"><span data-stu-id="3404a-173">Specifies a query in WMI Query Language (WQL) that identifies the WMI event class, such as: `select * from __InstanceDeletionEvent`.</span></span>

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3404a-174">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="3404a-174">-SourceIdentifier</span></span>

<span data-ttu-id="3404a-175">선택한 구독 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-175">Specifies a name that you select for the subscription.</span></span> <span data-ttu-id="3404a-176">선택한 이름은 현재 세션에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-176">The name that you select must be unique in the current session.</span></span> <span data-ttu-id="3404a-177">기본값은 Windows PowerShell이 할당하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-177">The default value is the GUID that Windows PowerShell assigns.</span></span>

<span data-ttu-id="3404a-178">이 매개 변수 값은 구독자 개체 및 이 구독과 연결된 모든 이벤트 개체의 **SourceIdentifier** 속성 값에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-178">The value of this parameter appears in the value of the **SourceIdentifier** property of the subscriber object and of all event objects associated with this subscription.</span></span>

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

### <span data-ttu-id="3404a-179">-SupportEvent</span><span class="sxs-lookup"><span data-stu-id="3404a-179">-SupportEvent</span></span>

<span data-ttu-id="3404a-180">이 cmdlet이 이벤트 구독을 숨기는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-180">Indicates that this cmdlet hides the event subscription.</span></span> <span data-ttu-id="3404a-181">현재 구독이 더 복잡한 이벤트 등록 메커니즘의 일부이며 독립적으로 검색되지 않아야 하는 경우 이 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-181">Use this parameter when the current subscription is part of a more complex event registration mechanism and it should not be discovered independently.</span></span>

<span data-ttu-id="3404a-182">**Supportevent** 매개 변수를 사용 하 여 만든 구독을 보거나 취소 하려면 및 Cmdlet의 **Force** 매개 변수를 지정 `Get-EventSubscriber` 합니다 `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="3404a-182">To view or cancel a subscription that was created by using the **SupportEvent** parameter, specify the **Force** parameter of the `Get-EventSubscriber` and `Unregister-Event` cmdlets.</span></span>

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

### <span data-ttu-id="3404a-183">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="3404a-183">-Timeout</span></span>

<span data-ttu-id="3404a-184">Windows PowerShell에서이 명령이 완료 될 때까지 대기 하는 기간을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-184">Specifies how long Windows PowerShell waits for this command to finish.</span></span>

<span data-ttu-id="3404a-185">기본값 0은 시간 제한이 없음을 의미하며 Windows PowerShell에서 무기한 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-185">The default value, 0 (zero), means that there is no time-out, and it causes Windows PowerShell to wait indefinitely.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3404a-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3404a-186">CommonParameters</span></span>

<span data-ttu-id="3404a-187">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3404a-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3404a-188">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3404a-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3404a-189">입력</span><span class="sxs-lookup"><span data-stu-id="3404a-189">INPUTS</span></span>

### <span data-ttu-id="3404a-190">없음</span><span class="sxs-lookup"><span data-stu-id="3404a-190">None</span></span>

<span data-ttu-id="3404a-191">이 cmdlet에 개체를 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-191">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="3404a-192">출력</span><span class="sxs-lookup"><span data-stu-id="3404a-192">OUTPUTS</span></span>

### <span data-ttu-id="3404a-193">없음</span><span class="sxs-lookup"><span data-stu-id="3404a-193">None</span></span>

<span data-ttu-id="3404a-194">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-194">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3404a-195">참고</span><span class="sxs-lookup"><span data-stu-id="3404a-195">NOTES</span></span>

<span data-ttu-id="3404a-196">Windows Vista 또는 이후 버전의 Windows 운영 체제에서이 cmdlet을 사용 하려면 관리자 권한으로 실행 옵션을 사용 하 여 Windows PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-196">To use this cmdlet in Windows Vista or a later version of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="3404a-197">이벤트, 이벤트 구독 및 이벤트 큐는 현재 세션에만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-197">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="3404a-198">현재 세션을 닫으면 이벤트 큐가 삭제되고 이벤트 구독이 취소됩니다.</span><span class="sxs-lookup"><span data-stu-id="3404a-198">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="3404a-199">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3404a-199">RELATED LINKS</span></span>
