---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/debug-runspace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Runspace
ms.openlocfilehash: 3f01b7624ffcbca472b09bdb83a7440f3526db43
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99599586"
---
# <span data-ttu-id="6ddf0-102">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="6ddf0-102">Debug-Runspace</span></span>

## <span data-ttu-id="6ddf0-103">개요</span><span class="sxs-lookup"><span data-stu-id="6ddf0-103">SYNOPSIS</span></span>
<span data-ttu-id="6ddf0-104">Runspace를 사용 하 여 대화형 디버깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-104">Starts an interactive debugging session with a runspace.</span></span>

## <span data-ttu-id="6ddf0-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6ddf0-105">SYNTAX</span></span>

### <span data-ttu-id="6ddf0-106">RunspaceParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="6ddf0-106">RunspaceParameterSet (Default)</span></span>

```
Debug-Runspace [-Runspace] <Runspace> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ddf0-107">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ddf0-107">NameParameterSet</span></span>

```
Debug-Runspace [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ddf0-108">IdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ddf0-108">IdParameterSet</span></span>

```
Debug-Runspace [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ddf0-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ddf0-109">InstanceIdParameterSet</span></span>

```
Debug-Runspace [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6ddf0-110">설명</span><span class="sxs-lookup"><span data-stu-id="6ddf0-110">DESCRIPTION</span></span>

<span data-ttu-id="6ddf0-111">`Debug-Runspace`Cmdlet은 로컬 또는 원격 활성 runspace를 사용 하 여 대화형 디버깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-111">The `Debug-Runspace` cmdlet starts an interactive debugging session with a local or remote active runspace.</span></span> <span data-ttu-id="6ddf0-112">`Get-Process`Powershell과 연결 된 프로세스를 찾은 다음 `Enter-PSHostProcess` **id** 매개 변수에 지정 된 프로세스 id를 사용 하 여 프로세스에 연결 하 고 `Get-Runspace` powershell 호스트 프로세스 내에서 runspace을 나열 하려면 먼저를 실행 하 여 디버깅할 runspace를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-112">You can find a runspace that you want to debug by first running `Get-Process` to find processes associated with PowerShell, then `Enter-PSHostProcess` with the process ID specified in the **Id** parameter to attach to the process, and then `Get-Runspace` to list runspaces within the PowerShell host process.</span></span>

<span data-ttu-id="6ddf0-113">디버깅할 runspace를 선택 하 고 runspace에서 현재 명령이 나 스크립트를 실행 하 고 있거나 스크립트가 중단점에서 중지 된 경우 PowerShell에서 runspace에 대 한 원격 디버거 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-113">After you have selected a runspace to debug, if the runspace is currently running a command or script, or if the script has stopped at a breakpoint, PowerShell opens a remote debugger session for the runspace.</span></span> <span data-ttu-id="6ddf0-114">원격 세션 스크립트를 디버깅 하는 것과 같은 방법으로 runspace 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-114">You can debug the runspace script in the same way remote session scripts are debugged.</span></span>

<span data-ttu-id="6ddf0-115">프로세스를 실행 하는 컴퓨터의 관리자 이거나 디버깅 하려는 스크립트를 실행 하는 경우에만 PowerShell 호스트 프로세스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-115">You can only attach to a PowerShell host process if you are an administrator on the computer that is running the process, or you are running the script that you want to debug.</span></span> <span data-ttu-id="6ddf0-116">또한 현재 PowerShell 세션을 실행 하는 호스트 프로세스를 입력할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-116">Also, you cannot enter the host process that is running the current PowerShell session.</span></span> <span data-ttu-id="6ddf0-117">다른 PowerShell 세션을 실행 하는 호스트 프로세스만 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-117">You can only enter a host process that is running a different PowerShell session.</span></span>

## <span data-ttu-id="6ddf0-118">예제</span><span class="sxs-lookup"><span data-stu-id="6ddf0-118">EXAMPLES</span></span>

### <span data-ttu-id="6ddf0-119">예제 1: 원격 runspace 디버깅</span><span class="sxs-lookup"><span data-stu-id="6ddf0-119">Example 1: Debug a remote runspace</span></span>

```
PS C:\> Get-Process -ComputerName "WS10TestServer" -Name "*powershell*"

Handles      WS(K)   VM(M)      CPU(s)    Id  ProcessName
-------      -----   -----      ------    --  -----------
    377      69912     63     2.09      2420  powershell
    399     123396    829     4.48      1152  powershell_ise

PS C:\> Enter-PSSession -ComputerName "WS10TestServer"
[WS10TestServer]:PS C:\> Enter-PSHostProcess -Id 1152
[WS10TestServer:][Process:1152]: PS C:\Users\Test\Documents> Get-Runspace

Id Name            ComputerName    Type          State         Availability
-- ----            ------------    ----          -----         ------------
 1 Runspace1       WS10TestServer  Remote        Opened        Available
 2 RemoteHost      WS10TestServer  Remote        Opened        Busy

PS C:\> [WS10TestServer][Process:1152]: PS C:\Users\Test\Documents> Debug-Runspace -Id 2

Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'
At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[Process:1152]: [RSDBG: 2]: PS C:\> >
```

<span data-ttu-id="6ddf0-120">이 예제에서는 원격 컴퓨터 WS10TestServer에서 열려 있는 runspace를 디버깅 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-120">In this example, you debug a runspace that is open on a remote computer, WS10TestServer.</span></span> <span data-ttu-id="6ddf0-121">명령의 첫 번째 줄에서 `Get-Process` 원격 컴퓨터에서를 실행 하 고 Windows PowerShell 호스트 프로세스를 필터링 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-121">In the first line of the command, you run `Get-Process` on the remote computer, and filter for Windows PowerShell host processes.</span></span> <span data-ttu-id="6ddf0-122">이 예제에서는 Windows PowerShell ISE 호스트 프로세스의 프로세스 ID 1152을 디버깅 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-122">In this example, you want to debug process ID 1152, the Windows PowerShell ISE host process.</span></span>

<span data-ttu-id="6ddf0-123">두 번째 명령에서는 `Enter-PSSession` 를 실행 하 여 WS10TestServer에서 원격 세션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-123">In the second command, you run `Enter-PSSession` to open a remote session on WS10TestServer.</span></span> <span data-ttu-id="6ddf0-124">세 번째 명령은를 실행 하 `Enter-PSHostProcess` 고 첫 번째 명령 1152에서 가져온 호스트 프로세스의 ID를 지정 하 여 원격 서버에서 실행 되는 Windows PowerShell ISE 호스트 프로세스에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-124">In the third command, you attach to the Windows PowerShell ISE host process running on the remote server by running `Enter-PSHostProcess`, and specifying the ID of the host process that you obtained in the first command, 1152.</span></span>

<span data-ttu-id="6ddf0-125">네 번째 명령에서를 실행 하 여 프로세스 ID 1152에 대해 사용 가능한 runspace를 나열 `Get-Runspace` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-125">In the fourth command, you list available runspaces for process ID 1152 by running `Get-Runspace`.</span></span>
<span data-ttu-id="6ddf0-126">사용 중인 runspace의 ID 번호를 확인 합니다. 디버깅 하려는 스크립트를 실행 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-126">You note the ID number of the Busy runspace; it is running a script that you want to debug.</span></span>

<span data-ttu-id="6ddf0-127">마지막 명령은 스크립트를 실행 하는 열린 runspace TestWFVar1.ps1를 디버깅 하기 시작 하 고,를 실행 하 `Debug-Runspace` 고, **id** 매개 변수를 추가 하 여 해당 id로 runspace를 식별 합니다 (2).</span><span class="sxs-lookup"><span data-stu-id="6ddf0-127">In the last command, you start debugging an opened runspace that is running a script, TestWFVar1.ps1, by running `Debug-Runspace`, and identifying the runspace by its ID, 2, by adding the **Id** parameter.</span></span> <span data-ttu-id="6ddf0-128">스크립트에 중단점이 있기 때문에 디버거가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-128">Because there's a breakpoint in the script, the debugger opens.</span></span>

## <span data-ttu-id="6ddf0-129">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6ddf0-129">PARAMETERS</span></span>

### <span data-ttu-id="6ddf0-130">-Id</span><span class="sxs-lookup"><span data-stu-id="6ddf0-130">-Id</span></span>

<span data-ttu-id="6ddf0-131">Runspace의 ID 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-131">Specifies the ID number of a runspace.</span></span> <span data-ttu-id="6ddf0-132">`Get-Runspace`를 실행 하 여 Runspace id를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-132">You can run `Get-Runspace` to show runspace IDs.</span></span>

```yaml
Type: System.Int32
Parameter Sets: IdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ddf0-133">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6ddf0-133">-InstanceId</span></span>

<span data-ttu-id="6ddf0-134">실행 하 여 표시할 수 있는 GUID 인 인스턴스 ID로 runspace를 지정 합니다 `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="6ddf0-134">Specifies a runspace by its instance ID, a GUID that you can show by running `Get-Runspace`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ddf0-135">-Name</span><span class="sxs-lookup"><span data-stu-id="6ddf0-135">-Name</span></span>

<span data-ttu-id="6ddf0-136">이름을 기준으로 runspace를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-136">Specifies a runspace by its name.</span></span> <span data-ttu-id="6ddf0-137">`Get-Runspace`을 실행 하 여 runspace의 이름을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-137">You can run `Get-Runspace` to show the names of runspaces.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ddf0-138">-Runspace</span><span class="sxs-lookup"><span data-stu-id="6ddf0-138">-Runspace</span></span>

<span data-ttu-id="6ddf0-139">Runspace 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-139">Specifies a runspace object.</span></span> <span data-ttu-id="6ddf0-140">이 매개 변수에 대 한 값을 제공 하는 가장 간단한 방법은 필터링 된 명령의 결과를 포함 하는 변수를 지정 하는 것입니다 `Get-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="6ddf0-140">The simplest way to provide a value for this parameter is to specify a variable that contains the results of a filtered `Get-Runspace` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.Runspace
Parameter Sets: RunspaceParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6ddf0-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6ddf0-141">-Confirm</span></span>

<span data-ttu-id="6ddf0-142">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-142">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ddf0-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6ddf0-143">-WhatIf</span></span>

<span data-ttu-id="6ddf0-144">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="6ddf0-145">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-145">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: True
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ddf0-146">-간</span><span class="sxs-lookup"><span data-stu-id="6ddf0-146">-BreakAll</span></span>

<span data-ttu-id="6ddf0-147">{{모든 설명 채우기 설명}}</span><span class="sxs-lookup"><span data-stu-id="6ddf0-147">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="6ddf0-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ddf0-148">CommonParameters</span></span>

<span data-ttu-id="6ddf0-149">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ddf0-150">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ddf0-151">입력</span><span class="sxs-lookup"><span data-stu-id="6ddf0-151">INPUTS</span></span>

### <span data-ttu-id="6ddf0-152">Runspace입니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-152">System.Management.Automation.Runspaces.Runspace</span></span>

<span data-ttu-id="6ddf0-153">명령의 결과를 `Get-Runspace` **디버그 Runspace** 로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-153">You can pipe the results of a `Get-Runspace` command to **Debug-Runspace.**</span></span>

## <span data-ttu-id="6ddf0-154">출력</span><span class="sxs-lookup"><span data-stu-id="6ddf0-154">OUTPUTS</span></span>

## <span data-ttu-id="6ddf0-155">참고</span><span class="sxs-lookup"><span data-stu-id="6ddf0-155">NOTES</span></span>

<span data-ttu-id="6ddf0-156">`Debug-Runspace` 열림 상태의 runspace에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-156">`Debug-Runspace` works on runspaces that are in the Opened state.</span></span> <span data-ttu-id="6ddf0-157">Runspace 상태가 열림에서 다른 상태로 변경 되는 경우이 runspace는 실행 중인 목록에서 자동으로 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-157">If a runspace state changes from Opened to another state, that runspace is automatically removed from the running list.</span></span> <span data-ttu-id="6ddf0-158">Runspace는 다음 조건을 충족 하는 경우에만 실행 목록에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-158">A runspace is added to the running list only if it meets the following criteria.</span></span>

- <span data-ttu-id="6ddf0-159">호출에서 오는 경우 즉, `Invoke-Command` GUID ID가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-159">If it is coming from Invoke-Command; that is, it has an `Invoke-Command` GUID ID.</span></span>
- <span data-ttu-id="6ddf0-160">에서 제공 되는 경우입니다 `Debug-Runspace` . 즉, `Debug-Runspace` GUID ID가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-160">If it is coming from `Debug-Runspace`; that is, it has a `Debug-Runspace` GUID ID.</span></span>
- <span data-ttu-id="6ddf0-161">PowerShell 워크플로에서 오는 경우 워크플로 작업 ID가 현재 활성 디버거 워크플로 작업 ID와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ddf0-161">If it is coming from a PowerShell workflow, and its workflow job ID is the same as the current active debugger workflow job ID.</span></span>

## <span data-ttu-id="6ddf0-162">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6ddf0-162">RELATED LINKS</span></span>

[<span data-ttu-id="6ddf0-163">about_Debuggers</span><span class="sxs-lookup"><span data-stu-id="6ddf0-163">about_Debuggers</span></span>](../Microsoft.PowerShell.Core/About/about_Debuggers.md)

[<span data-ttu-id="6ddf0-164">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="6ddf0-164">Debug-Job</span></span>](../Microsoft.PowerShell.Core/Debug-Job.md)

[<span data-ttu-id="6ddf0-165">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="6ddf0-165">Get-Runspace</span></span>](Get-Runspace.md)

[<span data-ttu-id="6ddf0-166">Get-Process</span><span class="sxs-lookup"><span data-stu-id="6ddf0-166">Get-Process</span></span>](../Microsoft.PowerShell.Management/Get-Process.md)

[<span data-ttu-id="6ddf0-167">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="6ddf0-167">Enter-PSHostProcess</span></span>](../Microsoft.PowerShell.Core/Enter-PSHostProcess.md)

[<span data-ttu-id="6ddf0-168">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="6ddf0-168">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

