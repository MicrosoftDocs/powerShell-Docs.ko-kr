---
description: PowerShell 디버거에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: d3353a9c684091b17f496e15f1553c860d26e973
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223538"
---
# <a name="about-debuggers"></a><span data-ttu-id="266bc-104">디버거 정보</span><span class="sxs-lookup"><span data-stu-id="266bc-104">About Debuggers</span></span>

## <a name="short-description"></a><span data-ttu-id="266bc-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="266bc-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="266bc-106">PowerShell 디버거에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-106">Describes the PowerShell debugger.</span></span>

## <a name="long-description"></a><span data-ttu-id="266bc-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="266bc-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="266bc-108">디버깅은 스크립트를 실행 하는 동안 스크립트를 검사 하 여 스크립트 지침에서 오류를 식별 하 고 수정 하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-108">Debugging is the process of examining a script while it is running to identify and correct errors in the script instructions.</span></span> <span data-ttu-id="266bc-109">PowerShell 디버거를 통해 스크립트, 함수, 명령, PowerShell 워크플로, PowerShell DSC (필요한 상태 구성) 구성 또는 식에서 오류와 비효율성을 검사 하 고 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-109">The PowerShell debugger can help you examine and identify errors and inefficiencies in your scripts, functions, commands, PowerShell workflows, PowerShell Desired State Configuration (DSC) configurations, or expressions.</span></span>

<span data-ttu-id="266bc-110">PowerShell 5.0부터 PowerShell 디버거는 콘솔 또는 원격 컴퓨터의 Windows PowerShell ISE 실행 되는 스크립트, 함수, 워크플로, 명령, 구성 또는 식을 디버그 하도록 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-110">Starting in PowerShell 5.0, the PowerShell debugger has been updated to debug scripts, functions, workflows, commands, configurations, or expressions that are running in either the console or Windows PowerShell ISE on remote computers.</span></span> <span data-ttu-id="266bc-111">`Enter-PSSession`를 실행 하 여 원격 컴퓨터에서 중단점을 설정 하 고 스크립트 파일과 명령을 디버그할 수 있는 대화형 원격 PowerShell 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-111">You can run `Enter-PSSession` to start an interactive remote PowerShell session in which you can set breakpoints and debug script files and commands on the remote computer.</span></span> <span data-ttu-id="266bc-112">`Enter-PSSession` 원격 컴퓨터에서 스크립트나 명령을 실행 하는 연결이 끊어진 세션에 다시 연결 하 고이를 시작할 수 있도록 기능이 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-112">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running a script or command on a remote computer.</span></span> <span data-ttu-id="266bc-113">실행 중인 스크립트가 중단점에 도달 하면 클라이언트 세션이 자동으로 디버거를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-113">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span> <span data-ttu-id="266bc-114">스크립트를 실행 하는 연결이 끊어진 세션에서 이미 중단점에 도달 하 고 중단점에서 중지 된 경우는 `Enter-PSSession` 세션에 다시 연결한 후 자동으로 명령줄 디버거를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-114">If the disconnected session that is running a script has already hit a breakpoint, and is stopped at the breakpoint, `Enter-PSSession` automatically starts the command-line debugger, after you reconnect to the session.</span></span>

<span data-ttu-id="266bc-115">Powershell 디버거를 사용 하 여 powershell 콘솔 또는 Windows PowerShell ISE에서 powershell 워크플로를 디버그할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-115">The PowerShell debugger can also be used to debug PowerShell workflows, in either the PowerShell console, or in Windows PowerShell ISE.</span></span> <span data-ttu-id="266bc-116">PowerShell 5.0부터 실행 중인 작업 또는 프로세스 내에서 로컬로 또는 원격으로 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-116">Starting in PowerShell 5.0, you can debug within running jobs or processes, either locally or remotely.</span></span>

<span data-ttu-id="266bc-117">Powershell 디버거의 기능을 사용 하 여 실행 중인 PowerShell 스크립트, 함수, 명령, 워크플로 또는 식을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-117">You can use the features of the PowerShell debugger to examine a PowerShell script, function, command, workflow, or expression while it is running.</span></span> <span data-ttu-id="266bc-118">PowerShell 디버거에는 중단점을 설정 하 고, 중단점을 관리 하 고, 호출 스택을 볼 수 있는 일련의 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-118">The PowerShell debugger includes a set of cmdlets that let you set breakpoints, manage breakpoints, and view the call stack.</span></span>

## <a name="debugger-cmdlets"></a><span data-ttu-id="266bc-119">디버거 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="266bc-119">Debugger Cmdlets</span></span>

<span data-ttu-id="266bc-120">PowerShell 디버거에는 다음과 같은 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-120">The PowerShell debugger includes the following set of cmdlets:</span></span>

- <span data-ttu-id="266bc-121">`Set-PSBreakpoint`: 줄, 변수 및 명령에 대 한 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-121">`Set-PSBreakpoint`: Sets breakpoints on lines, variables, and commands.</span></span>
- <span data-ttu-id="266bc-122">`Get-PSBreakpoint`: 현재 세션의 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-122">`Get-PSBreakpoint`: Gets breakpoints in the current session.</span></span>
- <span data-ttu-id="266bc-123">`Disable-PSBreakpoint`: 현재 세션에서 중단점을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-123">`Disable-PSBreakpoint`: Turns off breakpoints in the current session.</span></span>
- <span data-ttu-id="266bc-124">`Enable-PSBreakpoint`: 현재 세션에서 중단점을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-124">`Enable-PSBreakpoint`: Re-enables breakpoints in the current session.</span></span>
- <span data-ttu-id="266bc-125">`Remove-PSBreakpoint`: 현재 세션에서 중단점을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-125">`Remove-PSBreakpoint`: Deletes breakpoints from the current session.</span></span>
- <span data-ttu-id="266bc-126">`Get-PSCallStack`: 현재 호출 스택을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-126">`Get-PSCallStack`: Displays the current call stack.</span></span>

## <a name="starting-and-stopping-the-debugger"></a><span data-ttu-id="266bc-127">디버거 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="266bc-127">Starting and Stopping the Debugger</span></span>

<span data-ttu-id="266bc-128">디버거를 시작 하려면 하나 이상의 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-128">To start the debugger, set one or more breakpoints.</span></span> <span data-ttu-id="266bc-129">그런 다음 디버깅 하려는 스크립트, 명령 또는 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-129">Then, run the script, command, or function that you want to debug.</span></span>

<span data-ttu-id="266bc-130">중단점에 도달 하면 실행이 중지 되 고 컨트롤이 디버거로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-130">When you reach a breakpoint, execution stops, and control is turned over to the debugger.</span></span>

<span data-ttu-id="266bc-131">디버거를 중지 하려면 완료 될 때까지 스크립트, 명령 또는 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-131">To stop the debugger, run the script, command, or function until it is complete.</span></span> <span data-ttu-id="266bc-132">또는를 입력 `stop` `t` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-132">Or, type `stop` or `t`.</span></span>

### <a name="debugger-commands"></a><span data-ttu-id="266bc-133">디버거 명령</span><span class="sxs-lookup"><span data-stu-id="266bc-133">Debugger Commands</span></span>

<span data-ttu-id="266bc-134">PowerShell 콘솔에서 디버거를 사용 하는 경우 다음 명령을 사용 하 여 실행을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-134">When you use the debugger in the PowerShell console, use the following commands to control the execution.</span></span> <span data-ttu-id="266bc-135">Windows PowerShell ISE에서 디버그 메뉴의 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-135">In Windows PowerShell ISE, use commands on the Debug menu.</span></span>

<span data-ttu-id="266bc-136">참고: 다른 호스트 응용 프로그램에서 디버거를 사용 하는 방법에 대 한 자세한 내용은 호스트 응용 프로그램 설명서를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="266bc-136">Note: For information about how to use the debugger in other host applications, see the host application documentation.</span></span>

- <span data-ttu-id="266bc-137">`s`, `StepInto` : 다음 문을 실행 한 다음 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-137">`s`, `StepInto`: Executes the next statement and then stops.</span></span>

- <span data-ttu-id="266bc-138">`v`, `StepOver` : 다음 문을 실행 하지만 함수 및 호출을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-138">`v`, `StepOver`: Executes the next statement, but skips functions and invocations.</span></span> <span data-ttu-id="266bc-139">건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-139">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="266bc-140">`Ctrl+Break`: (ISE에서 모두 중단)은 PowerShell 콘솔 또는 Windows PowerShell ISE 내에서 실행 중인 스크립트로 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-140">`Ctrl+Break`: (Break All in ISE) Breaks into a running script within either the PowerShell console, or Windows PowerShell ISE.</span></span> <span data-ttu-id="266bc-141"><kbd>Ctrl</kbd> + Windows PowerShell 2.0, 3.0 및 4.0의 Ctrl<kbd>구분선</kbd> 은 프로그램을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-141">Note that <kbd>Ctrl</kbd>+<kbd>Break</kbd> in Windows PowerShell 2.0, 3.0, and 4.0 closes the program.</span></span> <span data-ttu-id="266bc-142">모두 중단은 대화형으로 실행 되는 로컬 및 원격 스크립트 모두에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-142">Break All works on both local and remote interactively-running scripts.</span></span>

- <span data-ttu-id="266bc-143">`o`, `StepOut` : 현재 함수에서 수행 되는 단계입니다. 중첩 된 경우에는 한 수준 위로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-143">`o`, `StepOut`: Steps out of the current function; up one level if nested.</span></span> <span data-ttu-id="266bc-144">주 본문에서 끝 또는 다음 중단점까지 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-144">If in the main body, it continues to the end or the next breakpoint.</span></span> <span data-ttu-id="266bc-145">건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-145">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="266bc-146">`c`, `Continue` : 스크립트가 완료 될 때까지 또는 다음 중단점에 도달할 때까지 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-146">`c`, `Continue`: Continues to run until the script is complete or until the next breakpoint is reached.</span></span> <span data-ttu-id="266bc-147">건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-147">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="266bc-148">`l`, `List` : 실행 중인 스크립트의 일부를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-148">`l`, `List`: Displays the part of the script that is executing.</span></span> <span data-ttu-id="266bc-149">기본적으로 현재 줄, 5 개의 이전 줄 및 10 개의 다음 줄을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-149">By default, it displays the current line, five previous lines, and 10 subsequent lines.</span></span>
  <span data-ttu-id="266bc-150">스크립트를 계속 나열 하려면 ENTER 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-150">To continue listing the script, press ENTER.</span></span>

- <span data-ttu-id="266bc-151">`l <m>`, `List` :로 지정 된 줄 번호로 시작 하는 스크립트의 16 줄을 표시 `<m>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-151">`l <m>`, `List`: Displays 16 lines of the script beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="266bc-152">`l <m> <n>`, `List` : `<n>` 로 지정 된 줄 번호로 시작 하 여 스크립트의 줄을 표시 합니다 `<m>` .</span><span class="sxs-lookup"><span data-stu-id="266bc-152">`l <m> <n>`, `List`: Displays `<n>` lines of the script, beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="266bc-153">`q`, `Stop` , `Exit` : 스크립트 실행을 중지 하 고 디버거를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-153">`q`, `Stop`, `Exit`: Stops executing the script, and exits the debugger.</span></span> <span data-ttu-id="266bc-154">Cmdlet을 실행 하 여 작업을 디버깅 하는 경우이 `Debug-Job` `Exit` 명령은 디버거를 분리 하 고 작업을 계속 실행 하도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-154">If you are debugging a job by running the `Debug-Job` cmdlet, the `Exit` command detaches the debugger, and allows the job to continue running.</span></span>

- <span data-ttu-id="266bc-155">`k`, `Get-PsCallStack` : 현재 호출 스택을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-155">`k`, `Get-PsCallStack`: Displays the current call stack.</span></span>

- <span data-ttu-id="266bc-156">`<Enter>`: 단계, 스텝 오버 (v) 또는 목록 (l) 인 경우 마지막 명령을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-156">`<Enter>`: Repeats the last command if it was Step (s), StepOver (v), or List (l).</span></span> <span data-ttu-id="266bc-157">그렇지 않으면는 제출 동작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-157">Otherwise, represents a submit action.</span></span>

- <span data-ttu-id="266bc-158">`?`, `h` : 디버거 명령 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-158">`?`, `h`: Displays the debugger command Help.</span></span>

<span data-ttu-id="266bc-159">디버거를 종료 하려면 Stop (q)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-159">To exit the debugger, you can use Stop (q).</span></span>

<span data-ttu-id="266bc-160">PowerShell 5.0부터 끝내기 명령을 실행 하 여 또는를 실행 하 여 시작한 중첩 된 디버깅 세션을 종료할 수 있습니다 `Debug-Job` `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="266bc-160">Starting in PowerShell 5.0, you can run the Exit command to exit a nested debugging session that you started by running either `Debug-Job` or `Debug-Runspace`.</span></span>

<span data-ttu-id="266bc-161">이러한 디버거 명령을 사용 하면 스크립트를 실행 하 고, 문제 발생 지점에서 중지 하 고, 변수의 값과 시스템 상태를 검사 하 고, 문제를 식별할 때까지 스크립트를 계속 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-161">By using these debugger commands, you can run a script, stop on a point of concern, examine the values of variables and the state of the system, and continue running the script until you have identified a problem.</span></span>

<span data-ttu-id="266bc-162">참고: ">"와 같은 리디렉션 연산자를 사용 하 여 문을 한 단계씩 실행 하는 경우 PowerShell 디버거는 스크립트의 나머지 모든 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-162">NOTE: If you step into a statement with a redirection operator, such as ">", the PowerShell debugger steps over all remaining statements in the script.</span></span>

<span data-ttu-id="266bc-163">스크립트 변수의 값 표시</span><span class="sxs-lookup"><span data-stu-id="266bc-163">Displaying the Values of script Variables</span></span>

<span data-ttu-id="266bc-164">디버거를 사용 하는 동안 명령을 입력 하 고, 변수 값을 표시 하 고, cmdlet을 사용 하 고, 명령줄에서 스크립트를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-164">While you are in the debugger, you can also enter commands, display the value of variables, use cmdlets, and run scripts at the command line.</span></span>

<span data-ttu-id="266bc-165">다음 자동 변수를 제외 하 고 디버깅 중인 스크립트에 모든 변수의 현재 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-165">You can display the current value of all variables in the script that is being debugged, except for the following automatic variables:</span></span>

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

<span data-ttu-id="266bc-166">이러한 변수의 값을 표시하려는 경우 스크립트의 변수 값이 아니라 디버거가 사용하는 내부 파이프라인의 해당 변수 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-166">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span>

<span data-ttu-id="266bc-167">디버깅할 스크립트에 대해 이러한 변수 값을 표시 하려면 스크립트에서 자동 변수의 값을 새 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-167">To display the value these variables for the script that is being debugged, in the script, assign the value of the automatic variable to a new variable.</span></span> <span data-ttu-id="266bc-168">그런 다음 새 변수의 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-168">Then you can display the value of the new variable.</span></span>

<span data-ttu-id="266bc-169">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-169">For example,</span></span>

```powershell
$scriptArgs = $Args
$scriptArgs
```

<span data-ttu-id="266bc-170">이 항목의 예제에서는 변수 값이 다음과 같이 다시 `$MyInvocation` 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-170">In the example in this topic, the value of the `$MyInvocation` variable is reassigned as follows:</span></span>

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a><span data-ttu-id="266bc-171">디버거 환경</span><span class="sxs-lookup"><span data-stu-id="266bc-171">The Debugger Environment</span></span>

<span data-ttu-id="266bc-172">중단점에 도달 하면 디버거 환경을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-172">When you reach a breakpoint, you enter the debugger environment.</span></span> <span data-ttu-id="266bc-173">명령 프롬프트는 "[DBG]:"으로 시작 되도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-173">The command prompt changes so that it begins with "[DBG]:".</span></span> <span data-ttu-id="266bc-174">워크플로를 디버깅 하는 경우 프롬프트는 "[WFDBG]"입니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-174">If you are debugging a workflow, the prompt is "[WFDBG]".</span></span> <span data-ttu-id="266bc-175">프롬프트를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-175">You can customize the prompt.</span></span>

<span data-ttu-id="266bc-176">프롬프트를 사용자 지정 하는 방법에 대 한 자세한 내용은 [about_Prompts](about_prompts.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="266bc-176">For more information about customizing the prompt, see [about_Prompts](about_prompts.md).</span></span>

<span data-ttu-id="266bc-177">또한 PowerShell 콘솔과 같은 일부 호스트 응용 프로그램 (Windows PowerShell ISE (통합 스크립팅 환경)에는 포함 되지 않음)에서는 디버깅을 위해 중첩 된 프롬프트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-177">Also, in some host applications, such as the PowerShell console, (but not in Windows PowerShell Integrated Scripting Environment [ISE]), a nested prompt opens for debugging.</span></span> <span data-ttu-id="266bc-178">명령 프롬프트에 표시 되는 반복 보다 큼 문자 (ASCII 62)로 중첩 된 프롬프트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-178">You can detect the nested prompt by the repeating greater-than characters (ASCII 62) that appear at the command prompt.</span></span>

<span data-ttu-id="266bc-179">예를 들어 PowerShell 콘솔의 기본 디버깅 프롬프트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-179">For example, the following is the default debugging prompt in the PowerShell console:</span></span>

```
[DBG]: PS (get-location)>>>
```

<span data-ttu-id="266bc-180">자동 변수를 사용 하 여 중첩 수준을 찾을 수 있습니다 `$NestedPromptLevel` .</span><span class="sxs-lookup"><span data-stu-id="266bc-180">You can find the nesting level by using the `$NestedPromptLevel` automatic variable.</span></span>

<span data-ttu-id="266bc-181">또한 자동 변수인는 `$PSDebugContext` 로컬 범위에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-181">Additionally, an automatic variable, `$PSDebugContext`, is defined in the local scope.</span></span> <span data-ttu-id="266bc-182">변수의 현재 상태를 사용 하 여 디버거를 사용 하 고 `$PsDebugContext` 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-182">You can use the presence of the `$PsDebugContext` variable to determine whether you are in the debugger.</span></span>

<span data-ttu-id="266bc-183">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="266bc-183">For example:</span></span>

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

<span data-ttu-id="266bc-184">디버깅에서 변수의 값을 사용할 수 있습니다 `$PSDebugContext` .</span><span class="sxs-lookup"><span data-stu-id="266bc-184">You can use the value of the `$PSDebugContext` variable in your debugging.</span></span>

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a><span data-ttu-id="266bc-185">디버깅 및 범위</span><span class="sxs-lookup"><span data-stu-id="266bc-185">Debugging and Scope</span></span>

<span data-ttu-id="266bc-186">디버거를 중단 해도 작업 중인 범위는 변경 되지 않지만 스크립트의 중단점에 도달 하면 스크립트 범위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-186">Breaking into the debugger does not change the scope in which you are operating, but when you reach a breakpoint in a script, you move into the script scope.</span></span> <span data-ttu-id="266bc-187">스크립트 범위는 디버거를 실행 한 범위의 자식입니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-187">The script scope is a child of the scope in which you ran the debugger.</span></span>

<span data-ttu-id="266bc-188">스크립트 범위에 정의 된 변수와 별칭을 찾으려면 또는 cmdlet의 Scope 매개 변수를 사용 `Get-Alias` `Get-Variable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-188">To find the variables and aliases that are defined in the script scope, use the Scope parameter of the `Get-Alias` or `Get-Variable` cmdlets.</span></span>

<span data-ttu-id="266bc-189">예를 들어 다음 명령은 로컬 (스크립트) 범위에서 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-189">For example, the following command gets the variables in the local (script) scope:</span></span>

```powershell
Get-Variable -scope 0
```

<span data-ttu-id="266bc-190">명령의 약어는 다음과 같이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-190">You can abbreviate the command as:</span></span>

```powershell
gv -s 0
```

<span data-ttu-id="266bc-191">이 방법은 스크립트에서 정의한 변수와 디버깅 중에 정의한 변수만 확인 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-191">This is a useful way to see only the variables that you defined in the script and that you defined while debugging.</span></span>

<span data-ttu-id="266bc-192">명령줄에서 디버깅</span><span class="sxs-lookup"><span data-stu-id="266bc-192">Debugging at the Command Line</span></span>

<span data-ttu-id="266bc-193">변수 중단점 또는 명령 중단점을 설정 하는 경우 스크립트 파일에만 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-193">When you set a variable breakpoint or a command breakpoint, you can set the breakpoint only in a script file.</span></span> <span data-ttu-id="266bc-194">그러나 기본적으로 중단점은 현재 세션에서 실행 되는 모든 항목에 대해 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-194">However, by default, the breakpoint is set on anything that runs in the current session.</span></span>

<span data-ttu-id="266bc-195">예를 들어 변수에 중단점을 설정 하는 경우 `$name` 디버거는 `$name` 중단점을 사용 하지 않도록 설정 하거나 제거할 때까지 실행 되는 스크립트, 명령, 함수, 스크립트 cmdlet 또는 식의 모든 변수에 대해 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-195">For example, if you set a breakpoint on the `$name` variable, the debugger breaks on any `$name` variable in any script, command, function, script cmdlet or expression that you run until you disable or remove the breakpoint.</span></span>

<span data-ttu-id="266bc-196">이를 통해 세션 및 사용자의 프로필에 있는 함수, 변수 및 기타 스크립트의 영향을 받을 수 있는 보다 현실적인 컨텍스트에서 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-196">This allows you to debug your scripts in a more realistic context in which they might be affected by functions, variables, and other scripts in the session and in the user's profile.</span></span>

<span data-ttu-id="266bc-197">줄 중단점은 스크립트 파일에만 적용 되므로 스크립트 파일에만 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-197">Line breakpoints are specific to script files, so they are set only in script files.</span></span>

## <a name="debugging-workflows"></a><span data-ttu-id="266bc-198">워크플로 디버깅</span><span class="sxs-lookup"><span data-stu-id="266bc-198">Debugging Workflows</span></span>

<span data-ttu-id="266bc-199">Powershell 4.0 디버거를 사용 하 여 powershell 콘솔 또는 Windows PowerShell ISE에서 PowerShell 워크플로를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-199">The PowerShell 4.0 debugger can be used to debug PowerShell workflows, either in the PowerShell console, or in Windows PowerShell ISE.</span></span> <span data-ttu-id="266bc-200">PowerShell 디버거를 사용 하 여 워크플로를 디버깅 하는 경우 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-200">There are some limitations with using the PowerShell debugger to debug workflows.</span></span>

- <span data-ttu-id="266bc-201">디버거 내에 있는 동안 워크플로 변수를 볼 수 있지만 디버거 내에서 워크플로 변수를 설정 하는 것은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-201">You can view workflow variables while you are in the debugger, but setting workflow variables from within the debugger is not supported.</span></span>
- <span data-ttu-id="266bc-202">워크플로 디버거에서 중지 된 경우 탭 완성 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-202">Tab completion when stopped in the workflow debugger is not available.</span></span>
- <span data-ttu-id="266bc-203">워크플로 디버깅은 PowerShell 스크립트에서 워크플로를 동기적으로 실행 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-203">Workflow debugging works only with synchronous running of workflows from a PowerShell script.</span></span> <span data-ttu-id="266bc-204">워크플로를 작업으로 실행 하는 경우에는 워크플로를 디버그할 수 없습니다 ( **AsJob** 매개 변수 사용).</span><span class="sxs-lookup"><span data-stu-id="266bc-204">You cannot debug workflows if they are running as a job (with the **AsJob** parameter).</span></span>
- <span data-ttu-id="266bc-205">다른 워크플로 또는 스크립트를 호출 하는 워크플로를 호출 하는 워크플로와 같은 다른 중첩 된 디버깅 시나리오는 구현 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-205">Other nested debugging scenarios, such as a workflow calling another workflow or a workflow calling a script, are not implemented.</span></span>

<span data-ttu-id="266bc-206">다음 예제에서는 워크플로를 디버깅 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-206">The following example demonstrates debugging a workflow.</span></span> <span data-ttu-id="266bc-207">디버거가 워크플로 함수를 단계별로 진행 하면 디버거 프롬프트가 "[WFDBG]"로 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-207">When the debugger steps into the workflow function, the debugger prompt changes to "[WFDBG]".</span></span>

```powershell
PS C:> Set-PSBreakpoint -Script C:\TestWFDemo1.ps1 -Line 8

ID Script           Line Command    Variable     Action
-- ------           ---- -------    --------     ------
0 TestWFDemo1.ps1   8

PS C:> C:\TestWFDemo1.ps1
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

At C:\TestWFDemo1.ps1:8 char:5
+     Write-Output -InputObject "Now writing output:"
# +!INCLUDE[]~~~~~

[WFDBG:localhost]: PS C:>> list

# 3:

4:  workflow SampleWorkflowTest
5:  {
6:      param ($MyOutput)
# 7:

8:*     Write-Output -InputObject "Now writing output:"
9:      Write-Output -Input $MyOutput
# 10:

11:      Write-Output -InputObject "Get PowerShell process:"
12:      Get-Process -Name powershell
# 13:

14:      Write-Output -InputObject "Workflow function complete."
15:  }
# 16:

17:  # Call workflow function
18:  SampleWorkflowTest -MyOutput "Hello"

[WFDBG:localhost]: PS C:>> $MyOutput
Hello
[WFDBG:localhost]: PS C:>> stepOver
Now writing output:
At C:\TestWFDemo1.ps1:9 char:5
+     Write-Output -Input $MyOutput
# +!INCLUDE[]~

[WFDBG:localhost]: PS C:>> list

4:  workflow SampleWorkflowTest
5:  {
6:      param ($MyOutput)
# 7:

8:      Write-Output -InputObject "Now writing output:"
9:*     Write-Output -Input $MyOutput
# 10:

11:      Write-Output -InputObject "Get PowerShell process:"
12:      Get-Process -Name powershell
# 13:

14:      Write-Output -InputObject "Workflow function complete."
15:  }
# 16:

17:  # Call workflow function
18:  SampleWorkflowTest -MyOutput "Hello"
# 19:


[WFDBG:localhost]: PS C:>> stepOver
Hello
At C:\TestWFDemo1.ps1:11 char:5
+     Write-Output -InputObject "Get PowerShell process:"
# +!INCLUDE[]~~~~~~~~~

[WFDBG:localhost]: PS C:>> stepOut
Get PowerShell process:

Handles  NPM(K)    PM(K)    WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----    ----- -----   ------     -- -----------
    433      35   106688   128392   726     2.67   7124 powershell
    499      44   134244   172096   787     2.79   7452 powershell

Workflow function complete.
```

## <a name="debugging-functions"></a><span data-ttu-id="266bc-208">디버깅 함수</span><span class="sxs-lookup"><span data-stu-id="266bc-208">Debugging Functions</span></span>

<span data-ttu-id="266bc-209">, 및 섹션이 있는 함수에 중단점을 설정 하면 `Begin` `Process` `End` 디버거가 각 섹션의 첫 번째 줄에서 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-209">When you set a breakpoint on a function that has `Begin`, `Process`, and `End` sections, the debugger breaks at the first line of each section.</span></span>

<span data-ttu-id="266bc-210">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="266bc-210">For example:</span></span>

```powershell
function test-cmdlet {
    begin {
        write-output "Begin"
    }
    process {
        write-output "Process"
    }
    end {
        write-output "End"
    }
}

C:\PS> Set-PSBreakpoint -command test-cmdlet

C:\PS> test-cmdlet

Begin
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
Process
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

[DBG]: C:\PS> c
End
Entering debug mode. Use h or ? for help.

Hit Command breakpoint on 'prompt:test-cmdlet'

test-cmdlet

# [DBG]: C:\PS>
```

## <a name="debugging-remote-scripts"></a><span data-ttu-id="266bc-211">원격 스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="266bc-211">Debugging Remote Scripts</span></span>

<span data-ttu-id="266bc-212">PowerShell 5.0부터 콘솔 또는 Windows PowerShell ISE 원격 세션에서 PowerShell 디버거를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-212">Starting in PowerShell 5.0, you can run the PowerShell debugger in a remote session, in either the console, or Windows PowerShell ISE.</span></span>
<span data-ttu-id="266bc-213">`Enter-PSSession` 원격 컴퓨터에서 실행 되 고 있으며 현재 스크립트를 실행 하는 연결이 끊어진 세션에 다시 연결 하 여 입력할 수 있도록 기능이 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-213">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running on a remote computer, and currently running a script.</span></span> <span data-ttu-id="266bc-214">실행 중인 스크립트가 중단점에 도달 하면 클라이언트 세션이 자동으로 디버거를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-214">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span>

<span data-ttu-id="266bc-215">다음은 줄 6, 11, 22 및 25의 스크립트에 중단점을 설정 하 여이 작업을 수행 하는 방법을 보여 주는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-215">The following is an example that shows how this works, with breakpoints set in a script at lines 6, 11, 22, and 25.</span></span> <span data-ttu-id="266bc-216">이 예제에서는 디버거가 시작 될 때 두 가지 확인 메시지가 표시 됩니다. 여기에는 세션이 실행 중인 컴퓨터의 이름이 표시 되 고, 사용자에 게 디버깅 모드를 알리는 데 사용 되는 DBG 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-216">Note that in the example, when the debugger starts, there are two identifying prompts: the name of the computer on which the session is running, and the DBG prompt that lets you know you are in debugging mode.</span></span>

```powershell
Enter-Pssession -Cn localhost
[localhost]: PS C:\psscripts> Set-PSBreakpoint .\ttest19.ps1 6,11,22,25

ID Script          Line     Command          Variable          Action
-- ------          ----     -------          --------          ------
0 ttest19.ps1          6
1 ttest19.ps1          11
2 ttest19.ps1          22
3 ttest19.ps1          25

[localhost]: PS C:\psscripts> .\ttest19.ps1
Hit Line breakpoint on 'C:\psscripts\ttest19.ps1:11'

At C:\psscripts\ttest19.ps1:11 char:1
+ $winRMName = "WinRM"
# + ~

[localhost]: [DBG]: PS C:\psscripts>> list

6:      1..5 | foreach { sleep 1; Write-Output "hello2day $_" }
7:  }
# 8:

9:  $count = 10
10:  $psName = "PowerShell"
11:* $winRMName = "WinRM"
12:  $myVar = 102
# 13:

14:  for ($i=0; $i -lt $count; $i++)
15:  {
16:      sleep 1
17:      Write-Output "Loop iteration is: $i"
18:      Write-Output "MyVar is $myVar"
# 19:

20:      hello2day
# 21:


[localhost]: [DBG]: PS C:\psscripts>> stepover
At C:\psscripts\ttest19.ps1:12 char:1
+ $myVar = 102
# + ~

[localhost]: [DBG]: PS C:\psscripts>> quit
[localhost]: PS C:\psscripts> Exit-PSSession
PS C:\psscripts>
```

## <a name="examples"></a><span data-ttu-id="266bc-217">예</span><span class="sxs-lookup"><span data-stu-id="266bc-217">Examples</span></span>

<span data-ttu-id="266bc-218">이 테스트 스크립트는 운영 체제의 버전을 검색 하 고 시스템에 적절 한 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-218">This test script detects the version of the operating system and displays a system-appropriate message.</span></span> <span data-ttu-id="266bc-219">여기에는 함수, 함수 호출 및 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-219">It includes a function, a function call, and a variable.</span></span>

<span data-ttu-id="266bc-220">다음 명령은 테스트 스크립트 파일의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-220">The following command displays the contents of the test script file:</span></span>

```powershell
PS C:\PS-test>  Get-Content test.ps1

function psversion {
  "PowerShell " + $PSVersionTable.PSVersion
  if ($PSVersionTable.PSVersion.Major -lt 6) {
    "Upgrade to PowerShell 6.0!"
  }
  else {
    "Have you run a background job today (start-job)?"
  }
}

$scriptName = $MyInvocation.MyCommand.Path
psversion
"Done $scriptName."
```

<span data-ttu-id="266bc-221">시작 하려면 스크립트의 관심 지점 (예: 줄, 명령, 변수 또는 함수)에서 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-221">To start, set a breakpoint at a point of interest in the script, such as a line, command, variable, or function.</span></span>

<span data-ttu-id="266bc-222">현재 디렉터리에 있는 Test.ps1 스크립트의 첫 번째 줄에 줄 중단점을 만들어 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-222">Start by creating a line breakpoint on the first line of the Test.ps1 script in the current directory.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

<span data-ttu-id="266bc-223">이 명령을</span><span class="sxs-lookup"><span data-stu-id="266bc-223">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

<span data-ttu-id="266bc-224">이 명령은 줄 중단점 개체 ( **system.web** )를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-224">The command returns a line-breakpoint object ( **System.Management.Automation.LineBreakpoint** ).</span></span>

```
Column     : 0
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\test.ps1
ScriptName : C:\ps-test\test.ps1
```

<span data-ttu-id="266bc-225">이제 스크립트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-225">Now, start the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
```

<span data-ttu-id="266bc-226">스크립트가 첫 번째 중단점에 도달 하면 디버거가 활성 상태임을 나타내는 중단점 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-226">When the script reaches the first breakpoint, the breakpoint message indicates that the debugger is active.</span></span> <span data-ttu-id="266bc-227">중단점을 설명 하 고 스크립트의 첫 번째 줄 (함수 선언)을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-227">It describes the breakpoint and previews the first line of the script, which is a function declaration.</span></span> <span data-ttu-id="266bc-228">또한 명령 프롬프트를 변경 하 여 디버거에 제어가 있음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-228">The command prompt also changes to indicate that the debugger has control.</span></span>

<span data-ttu-id="266bc-229">미리 보기 줄에는 미리 보기 된 명령의 스크립트 이름 및 줄 번호가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-229">The preview line includes the script name and the line number of the previewed command.</span></span>

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

<span data-ttu-id="266bc-230">단계 명령을 사용 하 여 스크립트에서 첫 번째 문을 실행 하 고 다음 문을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-230">Use the Step command (s) to execute the first statement in the script and to preview the next statement.</span></span> <span data-ttu-id="266bc-231">다음 문은 자동 변수를 사용 하 여 `$MyInvocation` 변수 값을 `$scriptName` 스크립트 파일의 경로 및 파일 이름으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-231">The next statement uses the `$MyInvocation` automatic variable to set the value of the `$scriptName` variable to the path and file name of the script file.</span></span>

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

<span data-ttu-id="266bc-232">이 시점에서 변수는 `$scriptName` 채워지지 않지만 값을 표시 하 여 변수의 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-232">At this point, the `$scriptName` variable is not populated, but you can verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="266bc-233">이 경우 값은 `$null`입니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-233">In this case, the value is `$null`.</span></span>

```powershell
DBG> $scriptname
# DBG>
```

<span data-ttu-id="266bc-234">다른 단계 명령을 사용 하 여 현재 문을 실행 하 고 스크립트에서 다음 문을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-234">Use another Step command (s) to execute the current statement and to preview the next statement in the script.</span></span> <span data-ttu-id="266bc-235">다음 문은 PsVersion 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-235">The next statement calls the PsVersion function.</span></span>

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="266bc-236">이 시점에서 변수는 `$scriptName` 채워지며 값을 표시 하 여 변수의 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-236">At this point, the `$scriptName` variable is populated, but you verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="266bc-237">이 경우 값은 스크립트 경로로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-237">In this case, the value is set to the script path.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

<span data-ttu-id="266bc-238">다른 단계 명령을 사용 하 여 함수 호출을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-238">Use another Step command to execute the function call.</span></span> <span data-ttu-id="266bc-239">ENTER 키를 누르거나 단계에 "s"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-239">Press ENTER, or type "s" for Step.</span></span>

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

<span data-ttu-id="266bc-240">디버그 메시지에는 함수의 문 미리 보기가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-240">The debug message includes a preview of the statement in the function.</span></span> <span data-ttu-id="266bc-241">이 문을 실행 하 고 함수에서 다음 문을 미리 보려면 명령을 사용할 수 있습니다 `Step` .</span><span class="sxs-lookup"><span data-stu-id="266bc-241">To execute this statement and to preview the next statement in the function, you can use a `Step` command.</span></span> <span data-ttu-id="266bc-242">그러나이 경우에는 StepOut 명령 (o)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-242">But, in this case, use a StepOut command (o).</span></span> <span data-ttu-id="266bc-243">이 함수는 중단점에 도달 하지 않는 한 함수 실행을 완료 하 고 스크립트의 다음 문으로의 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-243">It completes the execution of the function (unless it reaches a breakpoint) and steps to the next statement in the script.</span></span>

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="266bc-244">스크립트의 마지막 문이 있기 때문에 Step, StepOut 및 Continue 명령은 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-244">Because we are on the last statement in the script, the Step, StepOut, and Continue commands have the same effect.</span></span> <span data-ttu-id="266bc-245">이 경우 StepOut (o)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-245">In this case, use StepOut (o).</span></span>

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

<span data-ttu-id="266bc-246">StepOut 명령은 마지막 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-246">The StepOut command executes the last command.</span></span> <span data-ttu-id="266bc-247">표준 명령 프롬프트는 디버거가 종료 되 고 제어를 명령 프로세서로 반환 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-247">The standard command prompt indicates that the debugger has exited and returned control to the command processor.</span></span>

<span data-ttu-id="266bc-248">이제 디버거를 다시 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-248">Now, run the debugger again.</span></span> <span data-ttu-id="266bc-249">먼저, 현재 중단점을 삭제 하려면 `Get-PsBreakpoint` 및 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-249">First, to delete the current breakpoint, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span> <span data-ttu-id="266bc-250">(중단점을 다시 사용할 수 있다고 생각 되는 경우 `Disable-PsBreakpoint` 대신 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.)</span><span class="sxs-lookup"><span data-stu-id="266bc-250">(If you think you might reuse the breakpoint, use the `Disable-PsBreakpoint` cmdlet instead of `Remove-PsBreakpoint`.)</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="266bc-251">이 명령을</span><span class="sxs-lookup"><span data-stu-id="266bc-251">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> gbp | rbp
```

<span data-ttu-id="266bc-252">또는 다음 함수와 같이 함수를 작성 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-252">Or, run the command by writing a function, such as the following function:</span></span>

```powershell
function delbr { gbp | rbp }
```

<span data-ttu-id="266bc-253">이제 변수에 중단점을 만듭니다 `$scriptname` .</span><span class="sxs-lookup"><span data-stu-id="266bc-253">Now, create a breakpoint on the `$scriptname` variable.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

<span data-ttu-id="266bc-254">명령의 약어는 다음과 같이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-254">You can abbreviate the command as:</span></span>

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

<span data-ttu-id="266bc-255">이제 스크립트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-255">Now, start the script.</span></span> <span data-ttu-id="266bc-256">스크립트는 변수 중단점에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-256">The script reaches the variable breakpoint.</span></span> <span data-ttu-id="266bc-257">기본 모드는 Write 이므로 실행이 변수 값을 변경 하는 문 바로 앞으로 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-257">The default mode is Write, so execution stops just before the statement that changes the value of the variable.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

<span data-ttu-id="266bc-258">변수의 현재 값 `$scriptName` 을 표시 `$null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-258">Display the current value of the `$scriptName` variable, which is `$null`.</span></span>

```powershell
DBG> $scriptName
# DBG>
```

<span data-ttu-id="266bc-259">단계 명령을 사용 하 여 변수를 채우는 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-259">Use a Step command (s) to execute the statement that populates the variable.</span></span>
<span data-ttu-id="266bc-260">그런 다음 변수의 새 값을 표시 `$scriptName` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-260">Then, display the new value of the `$scriptName` variable.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="266bc-261">다음 문은 PsVersion 함수를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-261">The next statement is a call to the PsVersion function.</span></span> <span data-ttu-id="266bc-262">함수를 건너뛰고 계속 실행 하려면 스텝 오버 명령 (v)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-262">To skip the function but still execute it, use a StepOver command (v).</span></span> <span data-ttu-id="266bc-263">스텝 오버를 사용할 때 함수에 이미 있는 경우에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-263">If you are already in the function when you use StepOver, it is not effective.</span></span> <span data-ttu-id="266bc-264">함수 호출이 표시 되지만 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-264">The function call is displayed, but it is not executed.</span></span>

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="266bc-265">스텝 오버 명령은 함수를 실행 하 고 스크립트에서 마지막 줄을 출력 하는 다음 문을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-265">The StepOver command executes the function, and it previews the next statement in the script, which prints the final line.</span></span>

<span data-ttu-id="266bc-266">Stop 명령 (t)을 사용 하 여 디버거를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-266">Use a Stop command (t) to exit the debugger.</span></span> <span data-ttu-id="266bc-267">명령 프롬프트가 표준 명령 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-267">The command prompt reverts to the standard command prompt.</span></span>

```powershell
C:\ps-test>
```

<span data-ttu-id="266bc-268">중단점을 삭제 하려면 `Get-PsBreakpoint` 및 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-268">To delete the breakpoints, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="266bc-269">PsVersion 함수에 새 명령 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-269">Create a new command breakpoint on the PsVersion function.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

<span data-ttu-id="266bc-270">이 명령의 약어를 다음과 같이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-270">You can abbreviate this command to:</span></span>

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

<span data-ttu-id="266bc-271">이제 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-271">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

<span data-ttu-id="266bc-272">스크립트는 함수 호출에서 중단점에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-272">The script reaches the breakpoint at the function call.</span></span> <span data-ttu-id="266bc-273">이 시점에서 함수는 아직 호출 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-273">At this point, the function has not yet been called.</span></span> <span data-ttu-id="266bc-274">이를 통해의 Action 매개 변수를 사용 하 여 `Set-PSBreakpoint` 중단점 실행 조건을 설정 하거나 준비 또는 진단 작업 (예: 로그 시작 또는 진단 또는 보안 스크립트 호출)을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-274">This gives you the opportunity to use the Action parameter of `Set-PSBreakpoint` to set conditions for the execution of the breakpoint or to perform preparatory or diagnostic tasks, such as starting a log or invoking a diagnostic or security script.</span></span>

<span data-ttu-id="266bc-275">동작을 설정 하려면 Continue 명령 (c)을 사용 하 여 스크립트를 종료 하 고 `Remove-PsBreakpoint` 현재 중단점을 삭제 하는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-275">To set an action, use a Continue command (c) to exit the script, and a `Remove-PsBreakpoint` command to delete the current breakpoint.</span></span> <span data-ttu-id="266bc-276">중단점은 읽기 전용 이므로 현재 중단점에 작업을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-276">(Breakpoints are read-only, so you cannot add an action to the current breakpoint.)</span></span>

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

<span data-ttu-id="266bc-277">이제 작업을 사용 하 여 새 명령 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-277">Now, create a new command breakpoint with an action.</span></span> <span data-ttu-id="266bc-278">다음 명령은 `$scriptName` 함수가 호출 될 때 변수의 값을 기록 하는 작업을 사용 하 여 명령 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-278">The following command sets a command breakpoint with an action that logs the value of the `$scriptName` variable when the function is called.</span></span> <span data-ttu-id="266bc-279">Break 키워드는 작업에 사용 되지 않으므로 실행이 중지 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-279">Because the Break keyword is not used in the action, execution does not stop.</span></span> <span data-ttu-id="266bc-280">(억음 (')은 줄 연속 문자입니다.)</span><span class="sxs-lookup"><span data-stu-id="266bc-280">(The backtick (\`) is the line-continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

<span data-ttu-id="266bc-281">중단점에 대 한 조건을 설정 하는 작업을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-281">You can also add actions that set conditions for the breakpoint.</span></span> <span data-ttu-id="266bc-282">다음 명령에서 명령 중단점은 실행 정책이 RemoteSigned로 설정 된 경우에만 실행 됩니다. 단, 스크립트 실행을 허용 하는 가장 제한적인 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-282">In the following command, the command breakpoint is executed only if the execution policy is set to RemoteSigned, the most restrictive policy that still permits you to run scripts.</span></span> <span data-ttu-id="266bc-283">(억음 (')은 연속 문자입니다.)</span><span class="sxs-lookup"><span data-stu-id="266bc-283">(The backtick (\`) is the continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

<span data-ttu-id="266bc-284">작업의 Break 키워드는 중단점을 실행 하도록 디버거에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-284">The Break keyword in the action directs the debugger to execute the breakpoint.</span></span>
<span data-ttu-id="266bc-285">Continue 키워드를 사용 하 여 디버거가 중단 없이 실행 되도록 지시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-285">You can also use the Continue keyword to direct the debugger to execute without breaking.</span></span> <span data-ttu-id="266bc-286">Default 키워드가 Continue 이므로 중단을 지정 하 여 실행을 중지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-286">Because the default keyword is Continue, you must specify Break to stop execution.</span></span>

<span data-ttu-id="266bc-287">이제 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-287">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

<span data-ttu-id="266bc-288">실행 정책이 **RemoteSigned** 로 설정 되어 있기 때문에 함수 호출에서 실행이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-288">Because the execution policy is set to **RemoteSigned** , execution stops at the function call.</span></span>

<span data-ttu-id="266bc-289">이 시점에서 호출 스택을 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-289">At this point, you might want to check the call stack.</span></span> <span data-ttu-id="266bc-290">`Get-PsCallStack`Cmdlet 또는 `Get-PsCallStack` 디버거 명령 (k)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-290">Use the `Get-PsCallStack` cmdlet or the `Get-PsCallStack` debugger command (k).</span></span> <span data-ttu-id="266bc-291">다음 명령은 현재 호출 스택을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-291">The following command gets the current call stack.</span></span>

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

<span data-ttu-id="266bc-292">이 예제에서는 PowerShell 디버거를 사용 하는 여러 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-292">This example demonstrates just a few of the many ways to use the PowerShell debugger.</span></span>

<span data-ttu-id="266bc-293">디버거 cmdlet에 대 한 자세한 내용을 보려면 다음 명령을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="266bc-293">For more information about the debugger cmdlets, type the following command:</span></span>

```powershell
help <cmdlet-name> -full
```

<span data-ttu-id="266bc-294">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-294">For example, type:</span></span>

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a><span data-ttu-id="266bc-295">PowerShell의 기타 디버깅 기능</span><span class="sxs-lookup"><span data-stu-id="266bc-295">Other Debugging Features in PowerShell</span></span>

<span data-ttu-id="266bc-296">Powershell 디버거 외에도 PowerShell에는 스크립트 및 함수를 디버그 하는 데 사용할 수 있는 몇 가지 다른 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-296">In addition to the PowerShell debugger, PowerShell includes several other features that you can use to debug scripts and functions.</span></span>

- <span data-ttu-id="266bc-297">Windows PowerShell ISE에는 대화형 그래픽 디버거가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-297">Windows PowerShell ISE includes an interactive graphical debugger.</span></span> <span data-ttu-id="266bc-298">자세한 내용을 보려면 Windows PowerShell ISE를 시작 하 고 F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-298">For more information, start Windows PowerShell ISE and press F1.</span></span>

- <span data-ttu-id="266bc-299">`Set-PSDebug`Cmdlet은 단계별 실행 및 추적을 포함 하 여 매우 기본적인 스크립트 디버깅 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-299">The `Set-PSDebug` cmdlet offers very basic script debugging features, including stepping and tracing.</span></span>

- <span data-ttu-id="266bc-300">Cmdlet을 사용 하 여 초기화 되지 않은 변수에 대 한 `Set-StrictMode` 참조를 검색 하 고, 개체의 존재 하지 않는 속성에 대 한 참조를 검색 하 고, 유효 하지 않은 함수 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-300">Use the `Set-StrictMode` cmdlet to detect references to uninitialized variables, to references to non-existent properties of an object, and to function syntax that is not valid.</span></span>

- <span data-ttu-id="266bc-301">변수 값을 표시 하는 문, 명령줄에서 입력을 읽는 문 또는 현재 명령을 보고 하는 문과 같은 진단 문을 스크립트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-301">Add diagnostic statements to a script, such as statements that display the value of variables, statements that read input from the command line, or statements that report the current instruction.</span></span> <span data-ttu-id="266bc-302">이 작업에 대 한 쓰기 동사를 포함 하는 cmdlet (예:,, 및)을 사용 `Write-Host` `Write-Debug` `Write-Warning` `Write-Verbose` 합니다.</span><span class="sxs-lookup"><span data-stu-id="266bc-302">Use the cmdlets that contain the Write verb for this task, such as `Write-Host`, `Write-Debug`, `Write-Warning`, and `Write-Verbose`.</span></span>

## <a name="see-also"></a><span data-ttu-id="266bc-303">참고 항목</span><span class="sxs-lookup"><span data-stu-id="266bc-303">SEE ALSO</span></span>

- [<span data-ttu-id="266bc-304">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="266bc-304">Disable-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [<span data-ttu-id="266bc-305">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="266bc-305">Enable-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [<span data-ttu-id="266bc-306">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="266bc-306">Get-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [<span data-ttu-id="266bc-307">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="266bc-307">Get-PSCallStack</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [<span data-ttu-id="266bc-308">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="266bc-308">Remove-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [<span data-ttu-id="266bc-309">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="266bc-309">Set-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [<span data-ttu-id="266bc-310">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="266bc-310">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="266bc-311">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="266bc-311">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
