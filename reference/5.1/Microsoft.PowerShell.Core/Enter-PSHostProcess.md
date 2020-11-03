---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pshostprocess?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSHostProcess
ms.openlocfilehash: 56b8cef1911d1365f9568483921bfb49fbc32451
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212073"
---
# <span data-ttu-id="93e00-103">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="93e00-103">Enter-PSHostProcess</span></span>

## <span data-ttu-id="93e00-104">개요</span><span class="sxs-lookup"><span data-stu-id="93e00-104">SYNOPSIS</span></span>
<span data-ttu-id="93e00-105">에 연결 하 고 로컬 프로세스를 사용 하 여 대화형 세션으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-105">Connects to and enters into an interactive session with a local process.</span></span>

## <span data-ttu-id="93e00-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="93e00-106">SYNTAX</span></span>

### <span data-ttu-id="93e00-107">ProcessIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="93e00-107">ProcessIdParameterSet (Default)</span></span>

```
Enter-PSHostProcess [-Id] <Int32> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="93e00-108">ProcessParameterSet</span><span class="sxs-lookup"><span data-stu-id="93e00-108">ProcessParameterSet</span></span>

```
Enter-PSHostProcess [-Process] <Process> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="93e00-109">ProcessNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="93e00-109">ProcessNameParameterSet</span></span>

```
Enter-PSHostProcess [-Name] <String> [[-AppDomainName] <String>] [<CommonParameters>]
```

### <span data-ttu-id="93e00-110">PSHostProcessInfoParameterSet</span><span class="sxs-lookup"><span data-stu-id="93e00-110">PSHostProcessInfoParameterSet</span></span>

```
Enter-PSHostProcess [-HostProcessInfo] <PSHostProcessInfo> [[-AppDomainName] <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="93e00-111">설명</span><span class="sxs-lookup"><span data-stu-id="93e00-111">DESCRIPTION</span></span>

<span data-ttu-id="93e00-112">`Enter-PSHostProcess`Cmdlet은에 연결 하 여 로컬 프로세스와의 대화형 세션으로 전환 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-112">The `Enter-PSHostProcess` cmdlet connects to and enters into an interactive session with a local process.</span></span>

<span data-ttu-id="93e00-113">PowerShell을 호스트 하 고 원격 세션을 실행 하는 새 프로세스를 만드는 대신 PowerShell을 이미 실행 하 고 있는 기존 프로세스에서 원격 대화형 세션이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-113">Instead of creating a new process to host PowerShell and run a remote session, the remote, interactive session is run in an existing process that is already running PowerShell.</span></span> <span data-ttu-id="93e00-114">지정 된 프로세스에서 원격 세션과 상호 작용 하는 경우 실행 중인 runspace를 열거 하 고 또는를 실행 하 여 디버그할 runspace를 선택할 수 있습니다 `Debug-Runspace` `Enable-RunspaceDebug` .</span><span class="sxs-lookup"><span data-stu-id="93e00-114">When you are interacting with a remote session on a specified process, you can enumerate running runspaces, and then select a runspace to debug by running either `Debug-Runspace` or `Enable-RunspaceDebug`.</span></span>

<span data-ttu-id="93e00-115">입력 하려는 프로세스는 PowerShell (System.Management.Automation.dll)을 호스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-115">The process that you want to enter must be hosting PowerShell (System.Management.Automation.dll).</span></span>
<span data-ttu-id="93e00-116">프로세스가 있는 컴퓨터에서 Administrators 그룹의 구성원 이거나 프로세스를 시작 하는 스크립트를 실행 하는 사용자 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-116">You must be either a member of the Administrators group on the computer on which the process is found, or you must be the user who is running the script that started the process.</span></span>

<span data-ttu-id="93e00-117">디버깅할 runspace를 선택한 후 현재 명령을 실행 중이거나 디버거에서 중지 된 경우 runspace에 대 한 원격 디버그 세션이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-117">After you have selected a runspace to debug, a remote debug session is opened for the runspace if it is either currently running a command or is stopped in the debugger.</span></span> <span data-ttu-id="93e00-118">그런 다음 다른 원격 세션 스크립트를 디버깅 하는 것과 같은 방법으로 runspace 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-118">You can then debug the runspace script in the same way you would debug other remote session scripts.</span></span>

<span data-ttu-id="93e00-119">종료를 두 번 실행 하 여 디버깅 세션에서 프로세스와 대화형 세션을 분리 하거나 기존 디버거 quit 명령을 실행 하 여 스크립트 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-119">Detach from a debugging session, and then the interactive session with the process, by running exit twice, or stop script execution by running the existing debugger quit command.</span></span>

<span data-ttu-id="93e00-120">**Name** 매개 변수를 사용 하 여 프로세스를 지정 하 고 지정 된 이름의 프로세스가 하나만 있는 경우 프로세스가 입력 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-120">If you specify a process by using the **Name** parameter, and there is only one process found with the specified name, the process is entered.</span></span> <span data-ttu-id="93e00-121">지정 된 이름을 가진 프로세스가 둘 이상 발견 되 면 PowerShell에서 오류를 반환 하 고 지정 된 이름의 모든 프로세스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-121">If more than one process with the specified name is found, PowerShell returns an error, and lists all processes found with the specified name.</span></span>

<span data-ttu-id="93e00-122">원격 컴퓨터의 프로세스에 대 한 연결을 지원 하기 위해 `Enter-PSHostProcess` 지정 된 원격 컴퓨터에서 cmdlet을 사용 하도록 설정 하 여 원격 PowerShell 세션 내에서 로컬 프로세스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-122">To support attaching to processes on remote computers, the `Enter-PSHostProcess` cmdlet is enabled in a specified remote computer, so that you can attach to a local process within a remote PowerShell session.</span></span>

## <span data-ttu-id="93e00-123">예제</span><span class="sxs-lookup"><span data-stu-id="93e00-123">EXAMPLES</span></span>

### <span data-ttu-id="93e00-124">예제 1: PowerShell ISE 프로세스 내에서 runspace 디버깅 시작</span><span class="sxs-lookup"><span data-stu-id="93e00-124">Example 1: Start debugging a runspace within the PowerShell ISE process</span></span>

<span data-ttu-id="93e00-125">이 예에서는 powershell `Enter-PSHostProcess` 콘솔 내에서를 실행 하 여 POWERSHELL ISE 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-125">In this example, you run `Enter-PSHostProcess` from within the PowerShell console to enter the PowerShell ISE process.</span></span> <span data-ttu-id="93e00-126">결과 대화형 세션에서를 실행 하 여 디버깅 하려는 runspace를 찾은 `Get-Runspace` 다음 runspace를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-126">In the resulting interactive session, you can find a runspace that you want to debug by running `Get-Runspace`, and then debug the runspace.</span></span>

```
PS C:\> Enter-PSHostProcess -Name powershell_ise
[Process:1520]: PS C:\Test\Documents>

Next, get available runspaces within the process you have entered.
PS C:\> [Process:1520]: PS C:\>  Get-Runspace
Id    Name          InstanceId                               State           Availability
--    -------       -----------                              ------          -------------
1     Runspace1     2d91211d-9cce-42f0-ab0e-71ac258b32b5     Opened          Available
2     Runspace2     a3855043-cb16-424a-a616-685360c3763b     Opened          RemoteDebug
3     MyLocalRS     2236dbd8-2105-4dec-a15a-a27d0bfaacb5     Opened          LocalDebug
4     MyRunspace    771356e9-8c44-4b70-9de5-dd17cb41e48e     Opened          Busy
5     Runspace8     3e517382-a97a-49ba-9c3c-fd21f6664288     Broken          None

The runspace objects returned by Get-Runspace also have a NoteProperty called ScriptStackTrace of
the running command stack, if available.Next, debug runspace ID 4, that is running another user's
long-running script. From the list returned from Get-Runspace, note that the runspace state is
Opened, and Availability is Busy, meaning that the runspace is still running the long-running
script.

PS C:\> [Process:1520]: PS C:\>  (Get-Runspace -Id 4).ScriptStackTrace
Command                    Arguments                           Location
-------                    ---------                           --------
MyModuleWorkflowF1         {}                                  TestNoFile3.psm1: line 6
WFTest1                    {}                                  TestNoFile2.ps1: line 14
TestNoFile2.ps1            {}                                  TestNoFile2.ps1: line 22
<ScriptBlock>              {}                                  <No file>

Start an interactive debugging session with this runspace by running the Debug-Runspace cmdlet.

PS C:\> [Process: 1520]: PS C:\>  Debug-Runspace -Id 4
Hit Line breakpoint on 'C:\TestWFVar1.ps1:83'

At C:\TestWFVar1.ps1:83 char:1
+ $scriptVar = "Script Variable"
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[Process: 1520]: [RSDBG: 4]: PS C:\> >

After you are finished debugging, allow the script to continue running without the debugger attached
by running the exit debugger command. Alternatively, you can quit the debugger with the q or Stop
commands.

PS C:\> [Process:346]: [RSDBG: 3]: PS C:\> > exit
[Process:1520]: PS C:\>

When you are finished working in the process, exit the process by running the Exit-PSHostProcess
cmdlet. This returns you to the PS C:\> prompt.

PS C:\> [Process:1520]: PS C:\>  Exit-PSHostProcess
PS C:\>
```

## <span data-ttu-id="93e00-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="93e00-127">PARAMETERS</span></span>

### <span data-ttu-id="93e00-128">-AppDomainName</span><span class="sxs-lookup"><span data-stu-id="93e00-128">-AppDomainName</span></span>

<span data-ttu-id="93e00-129">생략 된 경우 연결할 응용 프로그램 도메인 이름을 지정 합니다. **Defaultappdomain** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-129">Specifies an application domain name to connect to if omitted, uses **DefaultAppDomain** .</span></span> <span data-ttu-id="93e00-130">`Get-PSHostProcessInfo`응용 프로그램 도메인 이름을 표시 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-130">Use `Get-PSHostProcessInfo` to display the application domain names.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: DefaultAppDomain
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93e00-131">-HostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="93e00-131">-HostProcessInfo</span></span>

<span data-ttu-id="93e00-132">PowerShell을 사용 하 여 연결할 수 있는 **exit-pshostprocessinfo** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-132">Specifies a **PSHostProcessInfo** object that can be connected to with PowerShell.</span></span> <span data-ttu-id="93e00-133">`Get-PSHostProcessInfo`를 사용 하 여 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-133">Use `Get-PSHostProcessInfo` to get the object.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.PSHostProcessInfo
Parameter Sets: PSHostProcessInfoParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="93e00-134">-Id</span><span class="sxs-lookup"><span data-stu-id="93e00-134">-Id</span></span>

<span data-ttu-id="93e00-135">프로세스 ID로 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-135">Specifies a process by the process ID.</span></span> <span data-ttu-id="93e00-136">프로세스 ID를 가져오려면 cmdlet을 실행 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-136">To get a process ID, run the `Get-Process` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ProcessIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93e00-137">-Name</span><span class="sxs-lookup"><span data-stu-id="93e00-137">-Name</span></span>

<span data-ttu-id="93e00-138">프로세스 이름으로 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-138">Specifies a process by the process name.</span></span> <span data-ttu-id="93e00-139">프로세스 이름을 가져오려면 cmdlet을 실행 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-139">To get a process name, run the `Get-Process` cmdlet.</span></span> <span data-ttu-id="93e00-140">작업 관리자의 프로세스에 대 한 속성 대화 상자에서 프로세스 이름을 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-140">You can also get process names from the Properties dialog box of a process in Task Manager.</span></span>

```yaml
Type: System.String
Parameter Sets: ProcessNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="93e00-141">-Process</span><span class="sxs-lookup"><span data-stu-id="93e00-141">-Process</span></span>

<span data-ttu-id="93e00-142">프로세스 개체의 프로세스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-142">Specifies a process by the process object.</span></span> <span data-ttu-id="93e00-143">이 매개 변수를 사용 하는 가장 간단한 방법은 `Get-Process` 변수에 입력 하려는 프로세스를 반환 하는 명령의 결과를 저장 한 다음이 매개 변수의 값으로 변수를 지정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-143">The simplest way to use this parameter is to save the results of a `Get-Process` command that returns process that you want to enter in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Diagnostics.Process
Parameter Sets: ProcessParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="93e00-144">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="93e00-144">CommonParameters</span></span>

<span data-ttu-id="93e00-145">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="93e00-145">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="93e00-146">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93e00-146">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="93e00-147">입력</span><span class="sxs-lookup"><span data-stu-id="93e00-147">INPUTS</span></span>

### <span data-ttu-id="93e00-148">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="93e00-148">System.Diagnostics.Process</span></span>

## <span data-ttu-id="93e00-149">출력</span><span class="sxs-lookup"><span data-stu-id="93e00-149">OUTPUTS</span></span>

## <span data-ttu-id="93e00-150">참고</span><span class="sxs-lookup"><span data-stu-id="93e00-150">NOTES</span></span>

<span data-ttu-id="93e00-151">`Enter-PSHostProcess` 명령을 실행 하는 PowerShell 세션의 프로세스를 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-151">`Enter-PSHostProcess` cannot enter the process of the PowerShell session in which you are running the command.</span></span> <span data-ttu-id="93e00-152">그러나 실행 중인 세션과 동시에 실행 되는 다른 PowerShell 세션 또는 PowerShell ISE 세션의 프로세스를 입력할 수 있습니다 `Enter-PSHostProcess` .</span><span class="sxs-lookup"><span data-stu-id="93e00-152">You can, however, enter the process of another PowerShell session, or a PowerShell ISE session that is running at the same time as the session in which you are running `Enter-PSHostProcess`.</span></span>

<span data-ttu-id="93e00-153">`Enter-PSHostProcess` PowerShell을 호스트 하는 프로세스만 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-153">`Enter-PSHostProcess` can enter only those processes that are hosting PowerShell.</span></span> <span data-ttu-id="93e00-154">즉, PowerShell 엔진을 로드 했습니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-154">That is, they have loaded the PowerShell engine.</span></span>

<span data-ttu-id="93e00-155">프로세스 내에서 프로세스를 종료 하려면 **exit** 를 입력 한 다음 <kbd>enter</kbd>키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="93e00-155">To exit a process from within the process, type **exit** , and then press <kbd>Enter</kbd>.</span></span>

## <span data-ttu-id="93e00-156">관련 링크</span><span class="sxs-lookup"><span data-stu-id="93e00-156">RELATED LINKS</span></span>

[<span data-ttu-id="93e00-157">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="93e00-157">Exit-PSHostProcess</span></span>](Exit-PSHostProcess.md)

[<span data-ttu-id="93e00-158">Get-PSHostProcessInfo</span><span class="sxs-lookup"><span data-stu-id="93e00-158">Get-PSHostProcessInfo</span></span>](Get-PSHostProcessInfo.md)
