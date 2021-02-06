---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSBreakpoint
ms.openlocfilehash: 5e2bdf435bf7cb9da3f31712c346beff29a11baf
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99603307"
---
# <span data-ttu-id="82210-102">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82210-102">Set-PSBreakpoint</span></span>

## <span data-ttu-id="82210-103">개요</span><span class="sxs-lookup"><span data-stu-id="82210-103">SYNOPSIS</span></span>
<span data-ttu-id="82210-104">줄, 명령 또는 변수에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-104">Sets a breakpoint on a line, command, or variable.</span></span>

## <span data-ttu-id="82210-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82210-105">SYNTAX</span></span>

### <span data-ttu-id="82210-106">줄 (기본값)</span><span class="sxs-lookup"><span data-stu-id="82210-106">Line (Default)</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Column] <Int32>] [-Line] <Int32[]> [-Script] <String[]>
 [<CommonParameters>]
```

### <span data-ttu-id="82210-107">명령</span><span class="sxs-lookup"><span data-stu-id="82210-107">Command</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] -Command <String[]> [[-Script] <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="82210-108">변수</span><span class="sxs-lookup"><span data-stu-id="82210-108">Variable</span></span>

```
Set-PSBreakpoint [-Action <ScriptBlock>] [[-Script] <String[]>] -Variable <String[]>
 [-Mode <VariableAccessMode>] [<CommonParameters>]
```

## <span data-ttu-id="82210-109">설명</span><span class="sxs-lookup"><span data-stu-id="82210-109">DESCRIPTION</span></span>

<span data-ttu-id="82210-110">`Set-PSBreakpoint`Cmdlet은 현재 세션에서 실행 되는 명령 또는 스크립트에 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-110">The `Set-PSBreakpoint` cmdlet sets a breakpoint in a script or in any command run in the current session.</span></span> <span data-ttu-id="82210-111">를 사용 하 여 스크립트를 실행 `Set-PSBreakpoint` 하거나 명령을 실행 하기 전에 또는 다른 중단점에서 중지 된 경우 디버깅 중에 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-111">You can use `Set-PSBreakpoint` to set a breakpoint before executing a script or running a command, or during debugging, when stopped at another breakpoint.</span></span>

<span data-ttu-id="82210-112">`Set-PSBreakpoint` 원격 컴퓨터에 중단점을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-112">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="82210-113">원격 컴퓨터에서 스크립트를 디버그하려면 스크립트를 로컬 컴퓨터로 복사한 다음 로컬로 디버그하세요.</span><span class="sxs-lookup"><span data-stu-id="82210-113">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>

<span data-ttu-id="82210-114">각 `Set-PSBreakpoint` 명령은 다음 세 가지 중단점 유형 중 하나를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82210-114">Each `Set-PSBreakpoint` command creates one of the following three types of breakpoints:</span></span>

- <span data-ttu-id="82210-115">줄 중단점-특정 줄과 열 좌표에 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-115">Line breakpoint - Sets breakpoints at particular line and column coordinates.</span></span>
- <span data-ttu-id="82210-116">명령 중단점-명령 및 함수에 대 한 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-116">Command breakpoint - Sets breakpoints on commands and functions.</span></span>
- <span data-ttu-id="82210-117">변수 중단점-변수에 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-117">Variable breakpoint - Sets breakpoints on variables.</span></span>

<span data-ttu-id="82210-118">단일 명령으로 여러 줄, 명령 또는 변수에 중단점을 설정할 수 `Set-PSBreakpoint` 있지만 각 `Set-PSBreakpoint` 명령은 하나의 중단점 유형만 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-118">You can set a breakpoint on multiple lines, commands, or variables in a single `Set-PSBreakpoint` command, but each `Set-PSBreakpoint` command sets only one type of breakpoint.</span></span>

<span data-ttu-id="82210-119">중단점에서 PowerShell은 일시적으로 실행을 중지 하 고 디버거에 제어를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-119">At a breakpoint, PowerShell temporarily stops executing and gives control to the debugger.</span></span> <span data-ttu-id="82210-120">명령 프롬프트가로 변경 `DBG\>` 되 고 디버거 명령 집합을 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-120">The command prompt changes to `DBG\>`, and a set of debugger commands become available for use.</span></span> <span data-ttu-id="82210-121">그러나 **Action** 매개 변수를 사용 하 여 로깅 또는 진단과 같은 추가 작업을 수행 하는 중단점 또는 명령 조건과 같은 대체 응답을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-121">However, you can use the **Action** parameter to specify an alternate response, such as conditions for the breakpoint or instructions to perform additional tasks such as logging or diagnostics.</span></span>

<span data-ttu-id="82210-122">`Set-PSBreakpoint`Cmdlet은 PowerShell 스크립트 디버깅을 위해 설계 된 여러 cmdlet 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="82210-122">The `Set-PSBreakpoint` cmdlet is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="82210-123">PowerShell 디버거에 대 한 자세한 내용은 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82210-123">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="82210-124">예제</span><span class="sxs-lookup"><span data-stu-id="82210-124">EXAMPLES</span></span>

### <span data-ttu-id="82210-125">예제 1: 줄에 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="82210-125">Example 1: Set a breakpoint on a line</span></span>

<span data-ttu-id="82210-126">이 예에서는 Sample.ps1 스크립트의 줄 5에 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-126">This example sets a breakpoint at line 5 in the Sample.ps1 script.</span></span> <span data-ttu-id="82210-127">스크립트가 실행 되 면 줄 5가 실행 되기 직전에 실행이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-127">When the script runs, execution stops immediately before line 5 would execute.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Line 5
```

```output
Column     : 0
Line       : 5
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="82210-128">줄 번호로 새 중단점을 설정 하는 경우 cmdlet은 `Set-PSBreakpoint` 중단점 ID 및 적중 횟수를 포함 하는 줄 중단점 개체 (**system.web**)를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-128">When you set a new breakpoint by line number, the `Set-PSBreakpoint` cmdlet generates a line breakpoint object (**System.Management.Automation.LineBreakpoint**) that includes the breakpoint ID and hit count.</span></span>

### <span data-ttu-id="82210-129">예제 2: 함수에 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="82210-129">Example 2: Set a breakpoint on a function</span></span>

<span data-ttu-id="82210-130">이 예에서는 `Increment` Sample.ps1 cmdlet의 함수에 명령 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="82210-130">This example creates a command breakpoint on the `Increment` function in the Sample.ps1 cmdlet.</span></span> <span data-ttu-id="82210-131">매번 지정된 함수를 호출하기 직전에 스크립트의 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-131">The script stops executing immediately before each call to the specified function.</span></span>

```powershell
Set-PSBreakpoint -Command "Increment" -Script "sample.ps1"
```

```Output
Command    : Increment
Action     :
Enabled    : True
HitCount   : 0
Id         : 1
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="82210-132">그 결과로, 명령 중단점 개체가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-132">The result is a command breakpoint object.</span></span> <span data-ttu-id="82210-133">스크립트를 실행 하기 전에 **HitCount** 속성의 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="82210-133">Before the script runs, the value of the **HitCount** property is 0.</span></span>

### <span data-ttu-id="82210-134">예제 3: 변수에 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="82210-134">Example 3: Set a breakpoint on a variable</span></span>

<span data-ttu-id="82210-135">이 예에서는 Sample.ps1 스크립트의 **서버** 변수에 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-135">This example sets a breakpoint on the **Server** variable in the Sample.ps1 script.</span></span> <span data-ttu-id="82210-136">**ReadWrite** 값과 함께 **Mode** 매개 변수를 사용 하 여 변수 값을 읽을 때 실행을 중지 하 고 값이 변경 되기 직전에 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-136">It uses the **Mode** parameter with a value of **ReadWrite** to stop execution when the value of the variable is read and just before the value changes.</span></span>

```powershell
Set-PSBreakpoint -Script "sample.ps1" -Variable "Server" -Mode ReadWrite
```

### <span data-ttu-id="82210-137">예제 4: 지정 된 텍스트로 시작 하는 모든 명령에 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="82210-137">Example 4: Set a breakpoint on every command that begins with specified text</span></span>

<span data-ttu-id="82210-138">이 예에서는와 같이 "write"로 시작 하는 Sample.ps1 스크립트의 모든 명령에 대 한 중단점을 설정 `Write-Host` 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-138">This example sets a breakpoint on every command in the Sample.ps1 script that begins with "write", such as `Write-Host`.</span></span>

```powershell
Set-PSBreakpoint -Script Sample.ps1 -Command "write*"
```

### <span data-ttu-id="82210-139">예 5: 변수 값에 따라 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="82210-139">Example 5: Set a breakpoint depending on the value of a variable</span></span>

<span data-ttu-id="82210-140">이 예에서는 `DiskTest` 변수 값이 2 보다 큰 경우에만 Test.ps1 스크립트의 함수에서 실행을 중지 `$Disk` 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-140">This example stops execution at the `DiskTest` function in the Test.ps1 script only when the value of the `$Disk` variable is greater than 2.</span></span>

```powershell
Set-PSBreakpoint -Script "test.ps1" -Command "DiskTest" -Action { if ($Disk -gt 2) { break } }
```

<span data-ttu-id="82210-141">**동작** 의 값은 함수의 변수 값을 테스트 하는 스크립트 블록입니다 `$Disk` .</span><span class="sxs-lookup"><span data-stu-id="82210-141">The value of the **Action** is a script block that tests the value of the `$Disk` variable in the function.</span></span>

<span data-ttu-id="82210-142">`break`이 동작은 조건을 충족 하는 경우 키워드를 사용 하 여 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-142">The action uses the `break` keyword to stop execution if the condition is met.</span></span> <span data-ttu-id="82210-143">대안 (및 기본값)은 **계속** 입니다.</span><span class="sxs-lookup"><span data-stu-id="82210-143">The alternative (and the default) is **Continue**.</span></span>

### <span data-ttu-id="82210-144">예제 6: 함수에 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="82210-144">Example 6: Set a breakpoint on a function</span></span>

<span data-ttu-id="82210-145">이 예제에서는 함수에 대 한 중단점을 설정 `CheckLog` 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-145">This example sets a breakpoint on the `CheckLog` function.</span></span> <span data-ttu-id="82210-146">이 명령은 스크립트를 지정하지 않으므로 중단점은 현재 세션에서 실행되는 모든 항목에 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-146">Because the command does not specify a script, the breakpoint is set on anything that runs in the current session.</span></span> <span data-ttu-id="82210-147">디버거는 함수가 선언될 때가 아니라 호출될 때 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-147">The debugger breaks when the function is called, not when it is declared.</span></span>

```
PS> Set-PSBreakpoint -Command "checklog"
Id       : 0
Command  : checklog
Enabled  : True
HitCount : 0
Action   :

function CheckLog {
>> get-eventlog -log Application |
>> where {($_.source -like "TestApp") -and ($_.Message -like "*failed*")}
>>}
>>
PS> Checklog
DEBUG: Hit breakpoint(s)
DEBUG:  Function breakpoint on 'prompt:Checklog'
```

### <span data-ttu-id="82210-148">예제 7: 여러 줄에 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="82210-148">Example 7: Set breakpoints on multiple lines</span></span>

<span data-ttu-id="82210-149">이 예제에서는 Sample.ps1 스크립트에 세 개의 줄 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-149">This example sets three line breakpoints in the Sample.ps1 script.</span></span> <span data-ttu-id="82210-150">스크립트에서 지정된 각 줄의 열 2에 중단점을 하나씩 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-150">It sets one breakpoint at column 2 on each of the lines specified in the script.</span></span> <span data-ttu-id="82210-151">**Action** 매개 변수에 지정 된 작업은 모든 중단점에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-151">The action specified in the **Action** parameter applies to all breakpoints.</span></span>

```powershell
PS C:\> Set-PSBreakpoint -Script "sample.ps1" -Line 1, 14, 19 -Column 2 -Action {&(log.ps1)}
```

```Output
Column     : 2
Line       : 1
Action     :
Enabled    : True
HitCount   : 0
Id         : 6
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 14
Action     :
Enabled    : True
HitCount   : 0
Id         : 7
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1


Column     : 2
Line       : 19
Action     :
Enabled    : True
HitCount   : 0
Id         : 8
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

## <span data-ttu-id="82210-152">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="82210-152">PARAMETERS</span></span>

### <span data-ttu-id="82210-153">-Action</span><span class="sxs-lookup"><span data-stu-id="82210-153">-Action</span></span>

<span data-ttu-id="82210-154">각 중단점에서 중단되지 않는 대신 실행되는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-154">Specifies commands that run at each breakpoint instead of breaking.</span></span> <span data-ttu-id="82210-155">명령을 포함하는 스크립트 블록을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-155">Enter a script block that contains the commands.</span></span> <span data-ttu-id="82210-156">이 매개 변수를 사용하여 조건부 중단점을 설정하거나 테스트 또는 로깅 같은 다른 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-156">You can use this parameter to set conditional breakpoints or to perform other tasks, such as testing or logging.</span></span>

<span data-ttu-id="82210-157">이 매개 변수를 생략하거나 작업을 지정하지 않으면 중단점에서 실행이 중지되고 디버거가 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-157">If this parameter is omitted, or no action is specified, execution stops at the breakpoint, and the debugger starts.</span></span>

<span data-ttu-id="82210-158">**Action** 매개 변수를 사용 하면 각 중단점에서 action 스크립트 블록이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-158">When the **Action** parameter is used, the Action script block runs at each breakpoint.</span></span> <span data-ttu-id="82210-159">스크립트 블록에 Break 키워드가 포함되지 않은 한 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-159">Execution does not stop unless the script block includes the Break keyword.</span></span> <span data-ttu-id="82210-160">스크립트 블록에서 Continue 키워드를 사용하면 다음 중단점까지 실행이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-160">If you use the Continue keyword in the script block, execution resumes until the next breakpoint.</span></span>

<span data-ttu-id="82210-161">자세한 내용은 [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md)및 [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="82210-161">For more information, see [about_Script_Blocks](../Microsoft.PowerShell.Core/About/about_Script_Blocks.md), [about_Break](../Microsoft.PowerShell.Core/About/about_Break.md), and [about_Continue](../Microsoft.PowerShell.Core/About/about_Continue.md).</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82210-162">-열</span><span class="sxs-lookup"><span data-stu-id="82210-162">-Column</span></span>

<span data-ttu-id="82210-163">스크립트 파일에서 실행이 중지되는 열의 열 번호를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-163">Specifies the column number of the column in the script file on which execution stops.</span></span> <span data-ttu-id="82210-164">열 번호는 하나만 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-164">Enter only one column number.</span></span> <span data-ttu-id="82210-165">기본값은 열 1입니다.</span><span class="sxs-lookup"><span data-stu-id="82210-165">The default is column 1.</span></span>

<span data-ttu-id="82210-166">열 값은 **Line** 매개 변수 값과 함께 중단점을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-166">The Column value is used with the value of the **Line** parameter to specify the breakpoint.</span></span> <span data-ttu-id="82210-167">**Line** 매개 변수가 여러 줄을 지정 하는 경우 **Column** 매개 변수는 지정 된 각 줄의 지정 된 열에 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-167">If the **Line** parameter specifies multiple lines, the **Column** parameter sets a breakpoint at the specified column on each of the specified lines.</span></span> <span data-ttu-id="82210-168">PowerShell은 지정 된 줄 및 열 위치에 있는 문자가 포함 된 문 또는 식 앞에서 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-168">PowerShell stops executing before the statement or expression that includes the character at the specified line and column position.</span></span>

<span data-ttu-id="82210-169">열은 왼쪽 위 여백에서부터 열 번호 1(0 아님)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-169">Columns are counted from the top left margin beginning with column number 1 (not 0).</span></span> <span data-ttu-id="82210-170">스크립트에 없는 열을 지정하는 경우 오류가 선언되지는 않지만 중단점도 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-170">If you specify a column that does not exist in the script, an error is not declared, but the breakpoint is never executed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Line
Aliases:

Required: False
Position: 2
Default value: 1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82210-171">-Command</span><span class="sxs-lookup"><span data-stu-id="82210-171">-Command</span></span>

<span data-ttu-id="82210-172">명령 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-172">Sets a command breakpoint.</span></span> <span data-ttu-id="82210-173">Cmdlet 이름 (예: `Get-Process` 또는 함수 이름)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-173">Enter cmdlet names, such as `Get-Process`, or function names.</span></span> <span data-ttu-id="82210-174">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-174">Wildcards are permitted.</span></span>

<span data-ttu-id="82210-175">각 명령의 각 인스턴스가 실행되기 직전에 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-175">Execution stops just before each instance of each command is executed.</span></span> <span data-ttu-id="82210-176">명령이 함수인 경우 함수가 호출될 때마다, 그리고 각 BEGIN, PROCESS 및 END 섹션에서 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-176">If the command is a function, execution stops each time the function is called and at each BEGIN, PROCESS, and END section.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases: C

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="82210-177">-줄</span><span class="sxs-lookup"><span data-stu-id="82210-177">-Line</span></span>

<span data-ttu-id="82210-178">스크립트에 줄 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-178">Sets a line breakpoint in a script.</span></span> <span data-ttu-id="82210-179">하나 이상의 줄 번호를 쉼표로 구분하여 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-179">Enter one or more line numbers, separated by commas.</span></span> <span data-ttu-id="82210-180">PowerShell은 지정 된 각 줄에서 시작 하는 문을 실행 하기 직전에 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-180">PowerShell stops immediately before executing the statement that begins on each of the specified lines.</span></span>

<span data-ttu-id="82210-181">줄은 스크립트 파일의 왼쪽 위 여백에서부터 줄 번호 1(0 아님)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-181">Lines are counted from the top left margin of the script file beginning with line number 1 (not 0).</span></span>
<span data-ttu-id="82210-182">빈 줄을 지정하면 빈 줄이 아닌 다음 줄 앞에서 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-182">If you specify a blank line, execution stops before the next non-blank line.</span></span> <span data-ttu-id="82210-183">줄이 범위를 벗어나는 경우 중단점은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-183">If the line is out of range, the breakpoint is never hit.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Line
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82210-184">-Mode</span><span class="sxs-lookup"><span data-stu-id="82210-184">-Mode</span></span>

<span data-ttu-id="82210-185">변수 중단점을 트리거하는 액세스 모드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-185">Specifies the mode of access that triggers variable breakpoints.</span></span> <span data-ttu-id="82210-186">기본값은 **Write** 입니다.</span><span class="sxs-lookup"><span data-stu-id="82210-186">The default is **Write**.</span></span>

<span data-ttu-id="82210-187">이 매개 변수는 명령에서 **변수** 매개 변수가 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-187">This parameter is valid only when the **Variable** parameter is used in the command.</span></span> <span data-ttu-id="82210-188">이 모드는 명령에 설정된 모든 중단점에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-188">The mode applies to all breakpoints set in the command.</span></span> <span data-ttu-id="82210-189">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-189">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="82210-190">**쓰기** -변수에 새 값을 쓰기 직전에 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-190">**Write** - Stops execution immediately before a new value is written to the variable.</span></span>
- <span data-ttu-id="82210-191">**읽기** -변수를 읽을 때 즉, 할당, 표시 또는 사용 하기 위해 해당 값에 액세스 하는 경우 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-191">**Read** - Stops execution when the variable is read, that is, when its value is accessed, either to be assigned, displayed, or used.</span></span> <span data-ttu-id="82210-192">읽기 모드에서는 변수 값이 변경될 때 실행이 중지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-192">In read mode, execution does not stop when the value of the variable changes.</span></span>
- <span data-ttu-id="82210-193">**ReadWrite** -변수를 읽거나 쓸 때 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-193">**ReadWrite** - Stops execution when the variable is read or written.</span></span>

```yaml
Type: System.Management.Automation.VariableAccessMode
Parameter Sets: Variable
Aliases:
Accepted values: Read, Write, ReadWrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82210-194">-스크립트</span><span class="sxs-lookup"><span data-stu-id="82210-194">-Script</span></span>

<span data-ttu-id="82210-195">이 cmdlet이 중단점을 설정 하는 스크립트 파일의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-195">Specifies an array of script files that this cmdlet sets a breakpoint in.</span></span> <span data-ttu-id="82210-196">스크립트 파일 중 하나 이상의 경로 및 파일 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-196">Enter the paths and file names of one or more script files.</span></span> <span data-ttu-id="82210-197">파일이 현재 디렉터리에 있는 경우 경로를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-197">If the files are in the current directory, you can omit the path.</span></span>
<span data-ttu-id="82210-198">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-198">Wildcards are permitted.</span></span>

<span data-ttu-id="82210-199">기본적으로 변수 중단점과 명령 중단점은 현재 세션에서 실행되는 모든 명령에 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-199">By default, variable breakpoints and command breakpoints are set on any command that runs in the current session.</span></span> <span data-ttu-id="82210-200">이 매개 변수는 줄 중단점을 설정하는 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-200">This parameter is required only when setting a line breakpoint.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Line, Command, Variable
Aliases:

Required: True (Line), False (Command, Variable)
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82210-201">-Variable</span><span class="sxs-lookup"><span data-stu-id="82210-201">-Variable</span></span>

<span data-ttu-id="82210-202">이 cmdlet이 중단점을 설정 하는 변수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-202">Specifies an array of variables that this cmdlet sets breakpoints on.</span></span> <span data-ttu-id="82210-203">달러 기호 ()를 제외 하 고 쉼표로 구분 된 변수 목록을 입력 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-203">Enter a comma-separated list of variables without dollar signs (`$`).</span></span>

<span data-ttu-id="82210-204">**Mode** 매개 변수를 사용 하 여 중단점을 트리거하는 액세스 모드를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-204">Use the **Mode** parameter to determine the mode of access that triggers the breakpoints.</span></span> <span data-ttu-id="82210-205">기본 모드인 Write에서는 변수에 새 값을 쓰기 직전에 실행이 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="82210-205">The default mode, Write, stops execution just before a new value is written to the variable.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases: V

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="82210-206">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82210-206">CommonParameters</span></span>

<span data-ttu-id="82210-207">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="82210-207">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="82210-208">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="82210-208">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82210-209">입력</span><span class="sxs-lookup"><span data-stu-id="82210-209">INPUTS</span></span>

### <span data-ttu-id="82210-210">없음</span><span class="sxs-lookup"><span data-stu-id="82210-210">None</span></span>
<span data-ttu-id="82210-211">입력을로 파이프 할 수 없습니다 `Set-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="82210-211">You cannot pipe input to `Set-PSBreakpoint`.</span></span>

## <span data-ttu-id="82210-212">출력</span><span class="sxs-lookup"><span data-stu-id="82210-212">OUTPUTS</span></span>

### <span data-ttu-id="82210-213">중단점 개체 (VariableBreakpoint,, System.web. n a m a. n a m.</span><span class="sxs-lookup"><span data-stu-id="82210-213">Breakpoint object (System.Management.Automation.LineBreakpoint, System.Management.Automation.VariableBreakpoint, System.Management.Automation.CommandBreakpoint)</span></span>

<span data-ttu-id="82210-214">`Set-PSBreakpoint` 설정 하는 각 중단점을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-214">`Set-PSBreakpoint` returns an object that represents each breakpoint that it sets.</span></span>

## <span data-ttu-id="82210-215">참고</span><span class="sxs-lookup"><span data-stu-id="82210-215">NOTES</span></span>

- <span data-ttu-id="82210-216">`Set-PSBreakpoint` 원격 컴퓨터에 중단점을 설정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-216">`Set-PSBreakpoint` cannot set a breakpoint on a remote computer.</span></span> <span data-ttu-id="82210-217">원격 컴퓨터에서 스크립트를 디버그하려면 스크립트를 로컬 컴퓨터로 복사한 다음 로컬로 디버그하세요.</span><span class="sxs-lookup"><span data-stu-id="82210-217">To debug a script on a remote computer, copy the script to the local computer and then debug it locally.</span></span>
- <span data-ttu-id="82210-218">둘 이상의 줄, 명령 또는 변수에 중단점을 설정 하면에서 `Set-PSBreakpoint` 각 항목에 대 한 중단점 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="82210-218">When you set a breakpoint on more than one line, command, or variable, `Set-PSBreakpoint` generates a breakpoint object for each entry.</span></span>
- <span data-ttu-id="82210-219">명령 프롬프트에서 함수 또는 변수에 중단점을 설정하는 경우 함수 또는 변수를 만들기 전이나 만든 후에 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82210-219">When setting a breakpoint on a function or variable at the command prompt, you can set the breakpoint before or after you create the function or variable.</span></span>

## <span data-ttu-id="82210-220">관련 링크</span><span class="sxs-lookup"><span data-stu-id="82210-220">RELATED LINKS</span></span>

[<span data-ttu-id="82210-221">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82210-221">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="82210-222">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82210-222">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="82210-223">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82210-223">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="82210-224">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="82210-224">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="82210-225">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="82210-225">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

