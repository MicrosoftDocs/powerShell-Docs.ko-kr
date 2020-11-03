---
description: PowerShell 디버거에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/06/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_debuggers?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Debuggers
ms.openlocfilehash: 6765c33e4508e19dfca7f291f8452f1bb4730747
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222114"
---
# <a name="about-debuggers"></a><span data-ttu-id="9b010-104">디버거 정보</span><span class="sxs-lookup"><span data-stu-id="9b010-104">About Debuggers</span></span>

## <a name="short-description"></a><span data-ttu-id="9b010-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9b010-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="9b010-106">PowerShell 디버거에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-106">Describes the PowerShell debugger.</span></span>

## <a name="long-description"></a><span data-ttu-id="9b010-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9b010-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9b010-108">디버깅은 스크립트를 실행 하는 동안 스크립트를 검사 하 여 스크립트 지침에서 오류를 식별 하 고 수정 하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-108">Debugging is the process of examining a script while it is running to identify and correct errors in the script instructions.</span></span> <span data-ttu-id="9b010-109">PowerShell 디버거를 통해 스크립트, 함수, 명령, PowerShell DSC (필요한 상태 구성) 구성 또는 식에서 오류와 비효율성을 검사 하 고 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-109">The PowerShell debugger can help you examine and identify errors and inefficiencies in your scripts, functions, commands, PowerShell Desired State Configuration (DSC) configurations, or expressions.</span></span>

<span data-ttu-id="9b010-110">PowerShell 5.0부터 PowerShell 디버거는 콘솔 또는 원격 컴퓨터의 Windows PowerShell ISE 실행 되는 스크립트, 함수, 명령, 구성 또는 식을 디버그 하도록 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-110">Starting in PowerShell 5.0, the PowerShell debugger has been updated to debug scripts, functions, commands, configurations, or expressions that are running in either the console or Windows PowerShell ISE on remote computers.</span></span> <span data-ttu-id="9b010-111">`Enter-PSSession`를 실행 하 여 원격 컴퓨터에서 중단점을 설정 하 고 스크립트 파일과 명령을 디버그할 수 있는 대화형 원격 PowerShell 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-111">You can run `Enter-PSSession` to start an interactive remote PowerShell session in which you can set breakpoints and debug script files and commands on the remote computer.</span></span> <span data-ttu-id="9b010-112">`Enter-PSSession` 원격 컴퓨터에서 스크립트나 명령을 실행 하는 연결이 끊어진 세션에 다시 연결 하 고이를 시작할 수 있도록 기능이 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-112">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running a script or command on a remote computer.</span></span> <span data-ttu-id="9b010-113">실행 중인 스크립트가 중단점에 도달 하면 클라이언트 세션이 자동으로 디버거를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-113">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span> <span data-ttu-id="9b010-114">스크립트를 실행 하는 연결이 끊어진 세션에서 이미 중단점에 도달 하 고 중단점에서 중지 된 경우는 `Enter-PSSession` 세션에 다시 연결한 후 자동으로 명령줄 디버거를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-114">If the disconnected session that is running a script has already hit a breakpoint, and is stopped at the breakpoint, `Enter-PSSession` automatically starts the command-line debugger, after you reconnect to the session.</span></span>

<span data-ttu-id="9b010-115">Powershell 디버거의 기능을 사용 하 여 실행 중인 PowerShell 스크립트, 함수, 명령 또는 식을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-115">You can use the features of the PowerShell debugger to examine a PowerShell script, function, command, or expression while it is running.</span></span> <span data-ttu-id="9b010-116">PowerShell 디버거에는 중단점을 설정 하 고, 중단점을 관리 하 고, 호출 스택을 볼 수 있는 일련의 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-116">The PowerShell debugger includes a set of cmdlets that let you set breakpoints, manage breakpoints, and view the call stack.</span></span>

## <a name="debugger-cmdlets"></a><span data-ttu-id="9b010-117">디버거 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9b010-117">Debugger Cmdlets</span></span>

<span data-ttu-id="9b010-118">PowerShell 디버거에는 다음과 같은 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-118">The PowerShell debugger includes the following set of cmdlets:</span></span>

- <span data-ttu-id="9b010-119">`Set-PSBreakpoint`: 줄, 변수 및 명령에 대 한 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-119">`Set-PSBreakpoint`: Sets breakpoints on lines, variables, and commands.</span></span>
- <span data-ttu-id="9b010-120">`Get-PSBreakpoint`: 현재 세션의 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-120">`Get-PSBreakpoint`: Gets breakpoints in the current session.</span></span>
- <span data-ttu-id="9b010-121">`Disable-PSBreakpoint`: 현재 세션에서 중단점을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-121">`Disable-PSBreakpoint`: Turns off breakpoints in the current session.</span></span>
- <span data-ttu-id="9b010-122">`Enable-PSBreakpoint`: 현재 세션에서 중단점을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-122">`Enable-PSBreakpoint`: Re-enables breakpoints in the current session.</span></span>
- <span data-ttu-id="9b010-123">`Remove-PSBreakpoint`: 현재 세션에서 중단점을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-123">`Remove-PSBreakpoint`: Deletes breakpoints from the current session.</span></span>
- <span data-ttu-id="9b010-124">`Get-PSCallStack`: 현재 호출 스택을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-124">`Get-PSCallStack`: Displays the current call stack.</span></span>

## <a name="starting-and-stopping-the-debugger"></a><span data-ttu-id="9b010-125">디버거 시작 및 중지</span><span class="sxs-lookup"><span data-stu-id="9b010-125">Starting and Stopping the Debugger</span></span>

<span data-ttu-id="9b010-126">디버거를 시작 하려면 하나 이상의 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-126">To start the debugger, set one or more breakpoints.</span></span> <span data-ttu-id="9b010-127">그런 다음 디버깅 하려는 스크립트, 명령 또는 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-127">Then, run the script, command, or function that you want to debug.</span></span>

<span data-ttu-id="9b010-128">중단점에 도달 하면 실행이 중지 되 고 컨트롤이 디버거로 전환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-128">When you reach a breakpoint, execution stops, and control is turned over to the debugger.</span></span>

<span data-ttu-id="9b010-129">디버거를 중지 하려면 완료 될 때까지 스크립트, 명령 또는 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-129">To stop the debugger, run the script, command, or function until it is complete.</span></span> <span data-ttu-id="9b010-130">또는를 입력 `stop` `t` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-130">Or, type `stop` or `t`.</span></span>

### <a name="debugger-commands"></a><span data-ttu-id="9b010-131">디버거 명령</span><span class="sxs-lookup"><span data-stu-id="9b010-131">Debugger Commands</span></span>

<span data-ttu-id="9b010-132">PowerShell 콘솔에서 디버거를 사용 하는 경우 다음 명령을 사용 하 여 실행을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-132">When you use the debugger in the PowerShell console, use the following commands to control the execution.</span></span> <span data-ttu-id="9b010-133">Windows PowerShell ISE에서 디버그 메뉴의 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-133">In Windows PowerShell ISE, use commands on the Debug menu.</span></span>

<span data-ttu-id="9b010-134">참고: 다른 호스트 응용 프로그램에서 디버거를 사용 하는 방법에 대 한 자세한 내용은 호스트 응용 프로그램 설명서를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b010-134">Note: For information about how to use the debugger in other host applications, see the host application documentation.</span></span>

- <span data-ttu-id="9b010-135">`s`, `StepInto` : 다음 문을 실행 한 다음 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-135">`s`, `StepInto`: Executes the next statement and then stops.</span></span>

- <span data-ttu-id="9b010-136">`v`, `StepOver` : 다음 문을 실행 하지만 함수 및 호출을 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-136">`v`, `StepOver`: Executes the next statement, but skips functions and invocations.</span></span> <span data-ttu-id="9b010-137">건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-137">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="9b010-138">`Ctrl+Break`: (ISE에서 모두 중단)은 PowerShell 콘솔 또는 Windows PowerShell ISE 내에서 실행 중인 스크립트로 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-138">`Ctrl+Break`: (Break All in ISE) Breaks into a running script within either the PowerShell console, or Windows PowerShell ISE.</span></span> <span data-ttu-id="9b010-139"><kbd>Ctrl</kbd> + Windows PowerShell 2.0, 3.0 및 4.0의 Ctrl<kbd>구분선</kbd> 은 프로그램을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-139">Note that <kbd>Ctrl</kbd>+<kbd>Break</kbd> in Windows PowerShell 2.0, 3.0, and 4.0 closes the program.</span></span> <span data-ttu-id="9b010-140">모두 중단은 대화형으로 실행 되는 로컬 및 원격 스크립트 모두에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-140">Break All works on both local and remote interactively-running scripts.</span></span>

- <span data-ttu-id="9b010-141">`o`, `StepOut` : 현재 함수에서 수행 되는 단계입니다. 중첩 된 경우에는 한 수준 위로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-141">`o`, `StepOut`: Steps out of the current function; up one level if nested.</span></span> <span data-ttu-id="9b010-142">주 본문에서 끝 또는 다음 중단점까지 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-142">If in the main body, it continues to the end or the next breakpoint.</span></span> <span data-ttu-id="9b010-143">건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-143">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="9b010-144">`c`, `Continue` : 스크립트가 완료 될 때까지 또는 다음 중단점에 도달할 때까지 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-144">`c`, `Continue`: Continues to run until the script is complete or until the next breakpoint is reached.</span></span> <span data-ttu-id="9b010-145">건너뛴 문은 실행되지만 단계별로 실행되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-145">The skipped statements are executed, but not stepped through.</span></span>

- <span data-ttu-id="9b010-146">`l`, `List` : 실행 중인 스크립트의 일부를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-146">`l`, `List`: Displays the part of the script that is executing.</span></span> <span data-ttu-id="9b010-147">기본적으로 현재 줄, 5 개의 이전 줄 및 10 개의 다음 줄을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-147">By default, it displays the current line, five previous lines, and 10 subsequent lines.</span></span>
  <span data-ttu-id="9b010-148">스크립트를 계속 나열 하려면 ENTER 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-148">To continue listing the script, press ENTER.</span></span>

- <span data-ttu-id="9b010-149">`l <m>`, `List` :로 지정 된 줄 번호로 시작 하는 스크립트의 16 줄을 표시 `<m>` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-149">`l <m>`, `List`: Displays 16 lines of the script beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="9b010-150">`l <m> <n>`, `List` : `<n>` 로 지정 된 줄 번호로 시작 하 여 스크립트의 줄을 표시 합니다 `<m>` .</span><span class="sxs-lookup"><span data-stu-id="9b010-150">`l <m> <n>`, `List`: Displays `<n>` lines of the script, beginning with the line number specified by `<m>`.</span></span>

- <span data-ttu-id="9b010-151">`q`, `Stop` , `Exit` : 스크립트 실행을 중지 하 고 디버거를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-151">`q`, `Stop`, `Exit`: Stops executing the script, and exits the debugger.</span></span> <span data-ttu-id="9b010-152">Cmdlet을 실행 하 여 작업을 디버깅 하는 경우이 `Debug-Job` `Exit` 명령은 디버거를 분리 하 고 작업을 계속 실행 하도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-152">If you are debugging a job by running the `Debug-Job` cmdlet, the `Exit` command detaches the debugger, and allows the job to continue running.</span></span>

- <span data-ttu-id="9b010-153">`k`, `Get-PsCallStack` : 현재 호출 스택을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-153">`k`, `Get-PsCallStack`: Displays the current call stack.</span></span>

- <span data-ttu-id="9b010-154">`<Enter>`: 단계, 스텝 오버 (v) 또는 목록 (l) 인 경우 마지막 명령을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-154">`<Enter>`: Repeats the last command if it was Step (s), StepOver (v), or List (l).</span></span> <span data-ttu-id="9b010-155">그렇지 않으면는 제출 동작을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-155">Otherwise, represents a submit action.</span></span>

- <span data-ttu-id="9b010-156">`?`, `h` : 디버거 명령 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-156">`?`, `h`: Displays the debugger command Help.</span></span>

<span data-ttu-id="9b010-157">디버거를 종료 하려면 Stop (q)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-157">To exit the debugger, you can use Stop (q).</span></span>

<span data-ttu-id="9b010-158">PowerShell 5.0부터 끝내기 명령을 실행 하 여 또는를 실행 하 여 시작한 중첩 된 디버깅 세션을 종료할 수 있습니다 `Debug-Job` `Debug-Runspace` .</span><span class="sxs-lookup"><span data-stu-id="9b010-158">Starting in PowerShell 5.0, you can run the Exit command to exit a nested debugging session that you started by running either `Debug-Job` or `Debug-Runspace`.</span></span>

<span data-ttu-id="9b010-159">이러한 디버거 명령을 사용 하면 스크립트를 실행 하 고, 문제 발생 지점에서 중지 하 고, 변수의 값과 시스템 상태를 검사 하 고, 문제를 식별할 때까지 스크립트를 계속 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-159">By using these debugger commands, you can run a script, stop on a point of concern, examine the values of variables and the state of the system, and continue running the script until you have identified a problem.</span></span>

<span data-ttu-id="9b010-160">참고: ">"와 같은 리디렉션 연산자를 사용 하 여 문을 한 단계씩 실행 하는 경우 PowerShell 디버거는 스크립트의 나머지 모든 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-160">NOTE: If you step into a statement with a redirection operator, such as ">", the PowerShell debugger steps over all remaining statements in the script.</span></span>

<span data-ttu-id="9b010-161">스크립트 변수의 값 표시</span><span class="sxs-lookup"><span data-stu-id="9b010-161">Displaying the Values of script Variables</span></span>

<span data-ttu-id="9b010-162">디버거를 사용 하는 동안 명령을 입력 하 고, 변수 값을 표시 하 고, cmdlet을 사용 하 고, 명령줄에서 스크립트를 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-162">While you are in the debugger, you can also enter commands, display the value of variables, use cmdlets, and run scripts at the command line.</span></span>

<span data-ttu-id="9b010-163">다음 자동 변수를 제외 하 고 디버깅 중인 스크립트에 모든 변수의 현재 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-163">You can display the current value of all variables in the script that is being debugged, except for the following automatic variables:</span></span>

```powershell
$_
$Args
$Input
$MyInvocation
$PSBoundParameters
```

<span data-ttu-id="9b010-164">이러한 변수의 값을 표시하려는 경우 스크립트의 변수 값이 아니라 디버거가 사용하는 내부 파이프라인의 해당 변수 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-164">If you try to display the value of any of these variables, you get the value of that variable for in an internal pipeline the debugger uses, not the value of the variable in the script.</span></span>

<span data-ttu-id="9b010-165">디버깅할 스크립트에 대해 이러한 변수 값을 표시 하려면 스크립트에서 자동 변수의 값을 새 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-165">To display the value these variables for the script that is being debugged, in the script, assign the value of the automatic variable to a new variable.</span></span> <span data-ttu-id="9b010-166">그런 다음 새 변수의 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-166">Then you can display the value of the new variable.</span></span>

<span data-ttu-id="9b010-167">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-167">For example,</span></span>

```powershell
$scriptArgs = $Args
$scriptArgs
```

<span data-ttu-id="9b010-168">이 항목의 예제에서는 변수 값이 다음과 같이 다시 `$MyInvocation` 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-168">In the example in this topic, the value of the `$MyInvocation` variable is reassigned as follows:</span></span>

```powershell
$scriptname = $MyInvocation.MyCommand.Path
```

## <a name="the-debugger-environment"></a><span data-ttu-id="9b010-169">디버거 환경</span><span class="sxs-lookup"><span data-stu-id="9b010-169">The Debugger Environment</span></span>

<span data-ttu-id="9b010-170">중단점에 도달 하면 디버거 환경을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-170">When you reach a breakpoint, you enter the debugger environment.</span></span> <span data-ttu-id="9b010-171">명령 프롬프트는 "[DBG]:"으로 시작 되도록 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-171">The command prompt changes so that it begins with "[DBG]:".</span></span>

<span data-ttu-id="9b010-172">프롬프트를 사용자 지정 하는 방법에 대 한 자세한 내용은 [about_Prompts](about_prompts.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9b010-172">For more information about customizing the prompt, see [about_Prompts](about_prompts.md).</span></span>

<span data-ttu-id="9b010-173">또한 PowerShell 콘솔과 같은 일부 호스트 응용 프로그램 (Windows PowerShell ISE (통합 스크립팅 환경)에는 포함 되지 않음)에서는 디버깅을 위해 중첩 된 프롬프트가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-173">Also, in some host applications, such as the PowerShell console, (but not in Windows PowerShell Integrated Scripting Environment [ISE]), a nested prompt opens for debugging.</span></span> <span data-ttu-id="9b010-174">명령 프롬프트에 표시 되는 반복 보다 큼 문자 (ASCII 62)로 중첩 된 프롬프트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-174">You can detect the nested prompt by the repeating greater-than characters (ASCII 62) that appear at the command prompt.</span></span>

<span data-ttu-id="9b010-175">예를 들어 PowerShell 콘솔의 기본 디버깅 프롬프트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-175">For example, the following is the default debugging prompt in the PowerShell console:</span></span>

```
[DBG]: PS (get-location)>>>
```

<span data-ttu-id="9b010-176">자동 변수를 사용 하 여 중첩 수준을 찾을 수 있습니다 `$NestedPromptLevel` .</span><span class="sxs-lookup"><span data-stu-id="9b010-176">You can find the nesting level by using the `$NestedPromptLevel` automatic variable.</span></span>

<span data-ttu-id="9b010-177">또한 자동 변수인는 `$PSDebugContext` 로컬 범위에 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-177">Additionally, an automatic variable, `$PSDebugContext`, is defined in the local scope.</span></span> <span data-ttu-id="9b010-178">변수의 현재 상태를 사용 하 여 디버거를 사용 하 고 `$PsDebugContext` 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-178">You can use the presence of the `$PsDebugContext` variable to determine whether you are in the debugger.</span></span>

<span data-ttu-id="9b010-179">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="9b010-179">For example:</span></span>

```powershell
if ($PSDebugContext) {"Debugging"} else {"Not Debugging"}
```

<span data-ttu-id="9b010-180">디버깅에서 변수의 값을 사용할 수 있습니다 `$PSDebugContext` .</span><span class="sxs-lookup"><span data-stu-id="9b010-180">You can use the value of the `$PSDebugContext` variable in your debugging.</span></span>

```
[DBG]: PS>>> $PSDebugContext.InvocationInfo

Name   CommandLineParameters  UnboundArguments  Location
----   ---------------------  ----------------  --------
=      {}                     {}                C:\ps-test\vote.ps1 (1)
```

## <a name="debugging-and-scope"></a><span data-ttu-id="9b010-181">디버깅 및 범위</span><span class="sxs-lookup"><span data-stu-id="9b010-181">Debugging and Scope</span></span>

<span data-ttu-id="9b010-182">디버거를 중단 해도 작업 중인 범위는 변경 되지 않지만 스크립트의 중단점에 도달 하면 스크립트 범위로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-182">Breaking into the debugger does not change the scope in which you are operating, but when you reach a breakpoint in a script, you move into the script scope.</span></span> <span data-ttu-id="9b010-183">스크립트 범위는 디버거를 실행 한 범위의 자식입니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-183">The script scope is a child of the scope in which you ran the debugger.</span></span>

<span data-ttu-id="9b010-184">스크립트 범위에 정의 된 변수와 별칭을 찾으려면 또는 cmdlet의 Scope 매개 변수를 사용 `Get-Alias` `Get-Variable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-184">To find the variables and aliases that are defined in the script scope, use the Scope parameter of the `Get-Alias` or `Get-Variable` cmdlets.</span></span>

<span data-ttu-id="9b010-185">예를 들어 다음 명령은 로컬 (스크립트) 범위에서 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-185">For example, the following command gets the variables in the local (script) scope:</span></span>

```powershell
Get-Variable -scope 0
```

<span data-ttu-id="9b010-186">명령의 약어는 다음과 같이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-186">You can abbreviate the command as:</span></span>

```powershell
gv -s 0
```

<span data-ttu-id="9b010-187">이 방법은 스크립트에서 정의한 변수와 디버깅 중에 정의한 변수만 확인 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-187">This is a useful way to see only the variables that you defined in the script and that you defined while debugging.</span></span>

<span data-ttu-id="9b010-188">명령줄에서 디버깅</span><span class="sxs-lookup"><span data-stu-id="9b010-188">Debugging at the Command Line</span></span>

<span data-ttu-id="9b010-189">변수 중단점 또는 명령 중단점을 설정 하는 경우 스크립트 파일에만 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-189">When you set a variable breakpoint or a command breakpoint, you can set the breakpoint only in a script file.</span></span> <span data-ttu-id="9b010-190">그러나 기본적으로 중단점은 현재 세션에서 실행 되는 모든 항목에 대해 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-190">However, by default, the breakpoint is set on anything that runs in the current session.</span></span>

<span data-ttu-id="9b010-191">예를 들어 변수에 중단점을 설정 하는 경우 `$name` 디버거는 `$name` 중단점을 사용 하지 않도록 설정 하거나 제거할 때까지 실행 되는 스크립트, 명령, 함수, 스크립트 cmdlet 또는 식의 모든 변수에 대해 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-191">For example, if you set a breakpoint on the `$name` variable, the debugger breaks on any `$name` variable in any script, command, function, script cmdlet or expression that you run until you disable or remove the breakpoint.</span></span>

<span data-ttu-id="9b010-192">이를 통해 세션 및 사용자의 프로필에 있는 함수, 변수 및 기타 스크립트의 영향을 받을 수 있는 보다 현실적인 컨텍스트에서 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-192">This allows you to debug your scripts in a more realistic context in which they might be affected by functions, variables, and other scripts in the session and in the user's profile.</span></span>

<span data-ttu-id="9b010-193">줄 중단점은 스크립트 파일에만 적용 되므로 스크립트 파일에만 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-193">Line breakpoints are specific to script files, so they are set only in script files.</span></span>

## <a name="debugging-functions"></a><span data-ttu-id="9b010-194">디버깅 함수</span><span class="sxs-lookup"><span data-stu-id="9b010-194">Debugging Functions</span></span>

<span data-ttu-id="9b010-195">, 및 섹션이 있는 함수에 중단점을 설정 하면 `Begin` `Process` `End` 디버거가 각 섹션의 첫 번째 줄에서 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-195">When you set a breakpoint on a function that has `Begin`, `Process`, and `End` sections, the debugger breaks at the first line of each section.</span></span>

<span data-ttu-id="9b010-196">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="9b010-196">For example:</span></span>

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

## <a name="debugging-remote-scripts"></a><span data-ttu-id="9b010-197">원격 스크립트 디버깅</span><span class="sxs-lookup"><span data-stu-id="9b010-197">Debugging Remote Scripts</span></span>

<span data-ttu-id="9b010-198">PowerShell 5.0부터 콘솔 또는 Windows PowerShell ISE 원격 세션에서 PowerShell 디버거를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-198">Starting in PowerShell 5.0, you can run the PowerShell debugger in a remote session, in either the console, or Windows PowerShell ISE.</span></span>
<span data-ttu-id="9b010-199">`Enter-PSSession` 원격 컴퓨터에서 실행 되 고 있으며 현재 스크립트를 실행 하는 연결이 끊어진 세션에 다시 연결 하 여 입력할 수 있도록 기능이 업데이트 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-199">`Enter-PSSession` functionality has been updated to let you reconnect to and enter a disconnected session that is running on a remote computer, and currently running a script.</span></span> <span data-ttu-id="9b010-200">실행 중인 스크립트가 중단점에 도달 하면 클라이언트 세션이 자동으로 디버거를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-200">If the running script hits a breakpoint, your client session automatically starts the debugger.</span></span>

<span data-ttu-id="9b010-201">다음은 줄 6, 11, 22 및 25의 스크립트에 중단점을 설정 하 여이 작업을 수행 하는 방법을 보여 주는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-201">The following is an example that shows how this works, with breakpoints set in a script at lines 6, 11, 22, and 25.</span></span> <span data-ttu-id="9b010-202">이 예제에서는 디버거가 시작 될 때 두 가지 확인 메시지가 표시 됩니다. 여기에는 세션이 실행 중인 컴퓨터의 이름이 표시 되 고, 사용자에 게 디버깅 모드를 알리는 데 사용 되는 DBG 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-202">Note that in the example, when the debugger starts, there are two identifying prompts: the name of the computer on which the session is running, and the DBG prompt that lets you know you are in debugging mode.</span></span>

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

## <a name="examples"></a><span data-ttu-id="9b010-203">예</span><span class="sxs-lookup"><span data-stu-id="9b010-203">Examples</span></span>

<span data-ttu-id="9b010-204">이 테스트 스크립트는 운영 체제의 버전을 검색 하 고 시스템에 적절 한 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-204">This test script detects the version of the operating system and displays a system-appropriate message.</span></span> <span data-ttu-id="9b010-205">여기에는 함수, 함수 호출 및 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-205">It includes a function, a function call, and a variable.</span></span>

<span data-ttu-id="9b010-206">다음 명령은 테스트 스크립트 파일의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-206">The following command displays the contents of the test script file:</span></span>

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

<span data-ttu-id="9b010-207">시작 하려면 스크립트의 관심 지점 (예: 줄, 명령, 변수 또는 함수)에서 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-207">To start, set a breakpoint at a point of interest in the script, such as a line, command, variable, or function.</span></span>

<span data-ttu-id="9b010-208">현재 디렉터리에 있는 Test.ps1 스크립트의 첫 번째 줄에 줄 중단점을 만들어 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-208">Start by creating a line breakpoint on the first line of the Test.ps1 script in the current directory.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -line 1 -script test.ps1
```

<span data-ttu-id="9b010-209">이 명령을</span><span class="sxs-lookup"><span data-stu-id="9b010-209">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> spb 1 -s test.ps1
```

<span data-ttu-id="9b010-210">이 명령은 줄 중단점 개체 ( **system.web** )를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-210">The command returns a line-breakpoint object ( **System.Management.Automation.LineBreakpoint** ).</span></span>

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

<span data-ttu-id="9b010-211">이제 스크립트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-211">Now, start the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
```

<span data-ttu-id="9b010-212">스크립트가 첫 번째 중단점에 도달 하면 디버거가 활성 상태임을 나타내는 중단점 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-212">When the script reaches the first breakpoint, the breakpoint message indicates that the debugger is active.</span></span> <span data-ttu-id="9b010-213">중단점을 설명 하 고 스크립트의 첫 번째 줄 (함수 선언)을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-213">It describes the breakpoint and previews the first line of the script, which is a function declaration.</span></span> <span data-ttu-id="9b010-214">또한 명령 프롬프트를 변경 하 여 디버거에 제어가 있음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-214">The command prompt also changes to indicate that the debugger has control.</span></span>

<span data-ttu-id="9b010-215">미리 보기 줄에는 미리 보기 된 명령의 스크립트 이름 및 줄 번호가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-215">The preview line includes the script name and the line number of the previewed command.</span></span>

```powershell
Entering debug mode. Use h or ? for help.

Hit Line breakpoint on 'C:\ps-test\test.ps1:1'

test.ps1:1   function psversion {
# DBG>
```

<span data-ttu-id="9b010-216">단계 명령을 사용 하 여 스크립트에서 첫 번째 문을 실행 하 고 다음 문을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-216">Use the Step command (s) to execute the first statement in the script and to preview the next statement.</span></span> <span data-ttu-id="9b010-217">다음 문은 자동 변수를 사용 하 여 `$MyInvocation` 변수 값을 `$scriptName` 스크립트 파일의 경로 및 파일 이름으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-217">The next statement uses the `$MyInvocation` automatic variable to set the value of the `$scriptName` variable to the path and file name of the script file.</span></span>

```powershell
DBG> s
test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
```

<span data-ttu-id="9b010-218">이 시점에서 변수는 `$scriptName` 채워지지 않지만 값을 표시 하 여 변수의 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-218">At this point, the `$scriptName` variable is not populated, but you can verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="9b010-219">이 경우 값은 `$null`입니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-219">In this case, the value is `$null`.</span></span>

```powershell
DBG> $scriptname
# DBG>
```

<span data-ttu-id="9b010-220">다른 단계 명령을 사용 하 여 현재 문을 실행 하 고 스크립트에서 다음 문을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-220">Use another Step command (s) to execute the current statement and to preview the next statement in the script.</span></span> <span data-ttu-id="9b010-221">다음 문은 PsVersion 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-221">The next statement calls the PsVersion function.</span></span>

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="9b010-222">이 시점에서 변수는 `$scriptName` 채워지며 값을 표시 하 여 변수의 값을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-222">At this point, the `$scriptName` variable is populated, but you verify the value of the variable by displaying its value.</span></span> <span data-ttu-id="9b010-223">이 경우 값은 스크립트 경로로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-223">In this case, the value is set to the script path.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```

<span data-ttu-id="9b010-224">다른 단계 명령을 사용 하 여 함수 호출을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-224">Use another Step command to execute the function call.</span></span> <span data-ttu-id="9b010-225">ENTER 키를 누르거나 단계에 "s"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-225">Press ENTER, or type "s" for Step.</span></span>

```powershell
DBG> s
test.ps1:2       "PowerShell " + $PSVersionTable.PSVersion
```

<span data-ttu-id="9b010-226">디버그 메시지에는 함수의 문 미리 보기가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-226">The debug message includes a preview of the statement in the function.</span></span> <span data-ttu-id="9b010-227">이 문을 실행 하 고 함수에서 다음 문을 미리 보려면 명령을 사용할 수 있습니다 `Step` .</span><span class="sxs-lookup"><span data-stu-id="9b010-227">To execute this statement and to preview the next statement in the function, you can use a `Step` command.</span></span> <span data-ttu-id="9b010-228">그러나이 경우에는 StepOut 명령 (o)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-228">But, in this case, use a StepOut command (o).</span></span> <span data-ttu-id="9b010-229">이 함수는 중단점에 도달 하지 않는 한 함수 실행을 완료 하 고 스크립트의 다음 문으로의 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-229">It completes the execution of the function (unless it reaches a breakpoint) and steps to the next statement in the script.</span></span>

```powershell
DBG> o
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="9b010-230">스크립트의 마지막 문이 있기 때문에 Step, StepOut 및 Continue 명령은 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-230">Because we are on the last statement in the script, the Step, StepOut, and Continue commands have the same effect.</span></span> <span data-ttu-id="9b010-231">이 경우 StepOut (o)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-231">In this case, use StepOut (o).</span></span>

```powershell
Done C:\ps-test\test.ps1
PS C:\ps-test>
```

<span data-ttu-id="9b010-232">StepOut 명령은 마지막 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-232">The StepOut command executes the last command.</span></span> <span data-ttu-id="9b010-233">표준 명령 프롬프트는 디버거가 종료 되 고 제어를 명령 프로세서로 반환 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-233">The standard command prompt indicates that the debugger has exited and returned control to the command processor.</span></span>

<span data-ttu-id="9b010-234">이제 디버거를 다시 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-234">Now, run the debugger again.</span></span> <span data-ttu-id="9b010-235">먼저, 현재 중단점을 삭제 하려면 `Get-PsBreakpoint` 및 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-235">First, to delete the current breakpoint, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span> <span data-ttu-id="9b010-236">(중단점을 다시 사용할 수 있다고 생각 되는 경우 `Disable-PsBreakpoint` 대신 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.)</span><span class="sxs-lookup"><span data-stu-id="9b010-236">(If you think you might reuse the breakpoint, use the `Disable-PsBreakpoint` cmdlet instead of `Remove-PsBreakpoint`.)</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="9b010-237">이 명령을</span><span class="sxs-lookup"><span data-stu-id="9b010-237">You can abbreviate this command as:</span></span>

```powershell
PS C:\ps-test> gbp | rbp
```

<span data-ttu-id="9b010-238">또는 다음 함수와 같이 함수를 작성 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-238">Or, run the command by writing a function, such as the following function:</span></span>

```powershell
function delbr { gbp | rbp }
```

<span data-ttu-id="9b010-239">이제 변수에 중단점을 만듭니다 `$scriptname` .</span><span class="sxs-lookup"><span data-stu-id="9b010-239">Now, create a breakpoint on the `$scriptname` variable.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -variable scriptname -script test.ps1
```

<span data-ttu-id="9b010-240">명령의 약어는 다음과 같이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-240">You can abbreviate the command as:</span></span>

```powershell
PS C:\ps-test> sbp -v scriptname -s test.ps1
```

<span data-ttu-id="9b010-241">이제 스크립트를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-241">Now, start the script.</span></span> <span data-ttu-id="9b010-242">스크립트는 변수 중단점에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-242">The script reaches the variable breakpoint.</span></span> <span data-ttu-id="9b010-243">기본 모드는 Write 이므로 실행이 변수 값을 변경 하는 문 바로 앞으로 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-243">The default mode is Write, so execution stops just before the statement that changes the value of the variable.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Variable breakpoint on 'C:\ps-test\test.ps1:$scriptName'
(Write access)

test.ps1:11  $scriptName = $MyInvocation.MyCommand.Path
# DBG>
```

<span data-ttu-id="9b010-244">변수의 현재 값 `$scriptName` 을 표시 `$null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-244">Display the current value of the `$scriptName` variable, which is `$null`.</span></span>

```powershell
DBG> $scriptName
# DBG>
```

<span data-ttu-id="9b010-245">단계 명령을 사용 하 여 변수를 채우는 문을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-245">Use a Step command (s) to execute the statement that populates the variable.</span></span>
<span data-ttu-id="9b010-246">그런 다음 변수의 새 값을 표시 `$scriptName` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-246">Then, display the new value of the `$scriptName` variable.</span></span>

```powershell
DBG> $scriptName
C:\ps-test\test.ps1
```powershell

Use a Step command (s) to preview the next statement in the script.

```powershell
DBG> s
test.ps1:12  psversion
```

<span data-ttu-id="9b010-247">다음 문은 PsVersion 함수를 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-247">The next statement is a call to the PsVersion function.</span></span> <span data-ttu-id="9b010-248">함수를 건너뛰고 계속 실행 하려면 스텝 오버 명령 (v)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-248">To skip the function but still execute it, use a StepOver command (v).</span></span> <span data-ttu-id="9b010-249">스텝 오버를 사용할 때 함수에 이미 있는 경우에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-249">If you are already in the function when you use StepOver, it is not effective.</span></span> <span data-ttu-id="9b010-250">함수 호출이 표시 되지만 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-250">The function call is displayed, but it is not executed.</span></span>

```powershell
DBG> v
Windows PowerShell 2.0
Have you run a background job today (start-job)?
test.ps1:13  "Done $scriptName"
```

<span data-ttu-id="9b010-251">스텝 오버 명령은 함수를 실행 하 고 스크립트에서 마지막 줄을 출력 하는 다음 문을 미리 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-251">The StepOver command executes the function, and it previews the next statement in the script, which prints the final line.</span></span>

<span data-ttu-id="9b010-252">Stop 명령 (t)을 사용 하 여 디버거를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-252">Use a Stop command (t) to exit the debugger.</span></span> <span data-ttu-id="9b010-253">명령 프롬프트가 표준 명령 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-253">The command prompt reverts to the standard command prompt.</span></span>

```powershell
C:\ps-test>
```

<span data-ttu-id="9b010-254">중단점을 삭제 하려면 `Get-PsBreakpoint` 및 cmdlet을 사용 `Remove-PsBreakpoint` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-254">To delete the breakpoints, use the `Get-PsBreakpoint` and `Remove-PsBreakpoint` cmdlets.</span></span>

```powershell
PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
```

<span data-ttu-id="9b010-255">PsVersion 함수에 새 명령 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-255">Create a new command breakpoint on the PsVersion function.</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1
```

<span data-ttu-id="9b010-256">이 명령의 약어를 다음과 같이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-256">You can abbreviate this command to:</span></span>

```powershell
PS C:\ps-test> sbp -c psversion -s test.ps1
```

<span data-ttu-id="9b010-257">이제 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-257">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
# DBG>
```

<span data-ttu-id="9b010-258">스크립트는 함수 호출에서 중단점에 도달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-258">The script reaches the breakpoint at the function call.</span></span> <span data-ttu-id="9b010-259">이 시점에서 함수는 아직 호출 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-259">At this point, the function has not yet been called.</span></span> <span data-ttu-id="9b010-260">이를 통해의 Action 매개 변수를 사용 하 여 `Set-PSBreakpoint` 중단점 실행 조건을 설정 하거나 준비 또는 진단 작업 (예: 로그 시작 또는 진단 또는 보안 스크립트 호출)을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-260">This gives you the opportunity to use the Action parameter of `Set-PSBreakpoint` to set conditions for the execution of the breakpoint or to perform preparatory or diagnostic tasks, such as starting a log or invoking a diagnostic or security script.</span></span>

<span data-ttu-id="9b010-261">동작을 설정 하려면 Continue 명령 (c)을 사용 하 여 스크립트를 종료 하 고 `Remove-PsBreakpoint` 현재 중단점을 삭제 하는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-261">To set an action, use a Continue command (c) to exit the script, and a `Remove-PsBreakpoint` command to delete the current breakpoint.</span></span> <span data-ttu-id="9b010-262">중단점은 읽기 전용 이므로 현재 중단점에 작업을 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-262">(Breakpoints are read-only, so you cannot add an action to the current breakpoint.)</span></span>

```powershell
DBG> c
Windows PowerShell 2.0
Have you run a background job today (start-job)?
Done C:\ps-test\test.ps1

PS C:\ps-test> Get-PSBreakpoint| Remove-PSBreakpoint
PS C:\ps-test>
```

<span data-ttu-id="9b010-263">이제 작업을 사용 하 여 새 명령 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-263">Now, create a new command breakpoint with an action.</span></span> <span data-ttu-id="9b010-264">다음 명령은 `$scriptName` 함수가 호출 될 때 변수의 값을 기록 하는 작업을 사용 하 여 명령 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-264">The following command sets a command breakpoint with an action that logs the value of the `$scriptName` variable when the function is called.</span></span> <span data-ttu-id="9b010-265">Break 키워드는 작업에 사용 되지 않으므로 실행이 중지 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-265">Because the Break keyword is not used in the action, execution does not stop.</span></span> <span data-ttu-id="9b010-266">(억음 (')은 줄 연속 문자입니다.)</span><span class="sxs-lookup"><span data-stu-id="9b010-266">(The backtick (\`) is the line-continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -command psversion -script test.ps1  `
-action { add-content "The value of `$scriptName is $scriptName." `
-path action.log}
```

<span data-ttu-id="9b010-267">중단점에 대 한 조건을 설정 하는 작업을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-267">You can also add actions that set conditions for the breakpoint.</span></span> <span data-ttu-id="9b010-268">다음 명령에서 명령 중단점은 실행 정책이 RemoteSigned로 설정 된 경우에만 실행 됩니다. 단, 스크립트 실행을 허용 하는 가장 제한적인 정책입니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-268">In the following command, the command breakpoint is executed only if the execution policy is set to RemoteSigned, the most restrictive policy that still permits you to run scripts.</span></span> <span data-ttu-id="9b010-269">(억음 (')은 연속 문자입니다.)</span><span class="sxs-lookup"><span data-stu-id="9b010-269">(The backtick (\`) is the continuation character.)</span></span>

```powershell
PS C:\ps-test> Set-PSBreakpoint -script test.ps1 -command psversion `
-action { if ((Get-ExecutionPolicy) -eq "RemoteSigned") { break }}
```

<span data-ttu-id="9b010-270">작업의 Break 키워드는 중단점을 실행 하도록 디버거에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-270">The Break keyword in the action directs the debugger to execute the breakpoint.</span></span>
<span data-ttu-id="9b010-271">Continue 키워드를 사용 하 여 디버거가 중단 없이 실행 되도록 지시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-271">You can also use the Continue keyword to direct the debugger to execute without breaking.</span></span> <span data-ttu-id="9b010-272">Default 키워드가 Continue 이므로 중단을 지정 하 여 실행을 중지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-272">Because the default keyword is Continue, you must specify Break to stop execution.</span></span>

<span data-ttu-id="9b010-273">이제 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-273">Now, run the script.</span></span>

```powershell
PS C:\ps-test> .\test.ps1
Hit Command breakpoint on 'C:\ps-test\test.ps1:psversion'

test.ps1:12  psversion
```

<span data-ttu-id="9b010-274">실행 정책이 **RemoteSigned** 로 설정 되어 있기 때문에 함수 호출에서 실행이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-274">Because the execution policy is set to **RemoteSigned** , execution stops at the function call.</span></span>

<span data-ttu-id="9b010-275">이 시점에서 호출 스택을 확인 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-275">At this point, you might want to check the call stack.</span></span> <span data-ttu-id="9b010-276">`Get-PsCallStack`Cmdlet 또는 `Get-PsCallStack` 디버거 명령 (k)을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-276">Use the `Get-PsCallStack` cmdlet or the `Get-PsCallStack` debugger command (k).</span></span> <span data-ttu-id="9b010-277">다음 명령은 현재 호출 스택을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-277">The following command gets the current call stack.</span></span>

```powershell
DBG> k
2: prompt
1: .\test.ps1: $args=[]
0: prompt: $args=[]
```

<span data-ttu-id="9b010-278">이 예제에서는 PowerShell 디버거를 사용 하는 여러 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-278">This example demonstrates just a few of the many ways to use the PowerShell debugger.</span></span>

<span data-ttu-id="9b010-279">디버거 cmdlet에 대 한 자세한 내용을 보려면 다음 명령을 입력 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9b010-279">For more information about the debugger cmdlets, type the following command:</span></span>

```powershell
help <cmdlet-name> -full
```

<span data-ttu-id="9b010-280">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-280">For example, type:</span></span>

```powershell
help Set-PSBreakpoint -full
```

## <a name="other-debugging-features-in-powershell"></a><span data-ttu-id="9b010-281">PowerShell의 기타 디버깅 기능</span><span class="sxs-lookup"><span data-stu-id="9b010-281">Other Debugging Features in PowerShell</span></span>

<span data-ttu-id="9b010-282">Powershell 디버거 외에도 PowerShell에는 스크립트 및 함수를 디버그 하는 데 사용할 수 있는 몇 가지 다른 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-282">In addition to the PowerShell debugger, PowerShell includes several other features that you can use to debug scripts and functions.</span></span>

- <span data-ttu-id="9b010-283">Windows PowerShell ISE에는 대화형 그래픽 디버거가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-283">Windows PowerShell ISE includes an interactive graphical debugger.</span></span> <span data-ttu-id="9b010-284">자세한 내용을 보려면 Windows PowerShell ISE를 시작 하 고 F1 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-284">For more information, start Windows PowerShell ISE and press F1.</span></span>

- <span data-ttu-id="9b010-285">`Set-PSDebug`Cmdlet은 단계별 실행 및 추적을 포함 하 여 매우 기본적인 스크립트 디버깅 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-285">The `Set-PSDebug` cmdlet offers very basic script debugging features, including stepping and tracing.</span></span>

- <span data-ttu-id="9b010-286">Cmdlet을 사용 하 여 초기화 되지 않은 변수에 대 한 `Set-StrictMode` 참조를 검색 하 고, 개체의 존재 하지 않는 속성에 대 한 참조를 검색 하 고, 유효 하지 않은 함수 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-286">Use the `Set-StrictMode` cmdlet to detect references to uninitialized variables, to references to non-existent properties of an object, and to function syntax that is not valid.</span></span>

- <span data-ttu-id="9b010-287">변수 값을 표시 하는 문, 명령줄에서 입력을 읽는 문 또는 현재 명령을 보고 하는 문과 같은 진단 문을 스크립트에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-287">Add diagnostic statements to a script, such as statements that display the value of variables, statements that read input from the command line, or statements that report the current instruction.</span></span> <span data-ttu-id="9b010-288">이 작업에 대 한 쓰기 동사를 포함 하는 cmdlet (예:,, 및)을 사용 `Write-Host` `Write-Debug` `Write-Warning` `Write-Verbose` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-288">Use the cmdlets that contain the Write verb for this task, such as `Write-Host`, `Write-Debug`, `Write-Warning`, and `Write-Verbose`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b010-289">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b010-289">SEE ALSO</span></span>

- [<span data-ttu-id="9b010-290">사용 안 함-PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9b010-290">Disable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Disable-PSBreakpoint)
- [<span data-ttu-id="9b010-291">-PsBreakpoint 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-291">Enable-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Enable-PSBreakpoint)
- [<span data-ttu-id="9b010-292">Get PsBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9b010-292">Get-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSBreakpoint)
- [<span data-ttu-id="9b010-293">Get PsCallStack</span><span class="sxs-lookup"><span data-stu-id="9b010-293">Get-PsCallStack</span></span>](xref:Microsoft.PowerShell.Utility.Get-PSCallStack)
- [<span data-ttu-id="9b010-294">-PsBreakpoint을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9b010-294">Remove-PsBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Remove-PSBreakpoint)
- [<span data-ttu-id="9b010-295">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="9b010-295">Set-PSBreakpoint</span></span>](xref:Microsoft.PowerShell.Utility.Set-PSBreakpoint)
- [<span data-ttu-id="9b010-296">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="9b010-296">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)
- [<span data-ttu-id="9b010-297">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="9b010-297">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)

