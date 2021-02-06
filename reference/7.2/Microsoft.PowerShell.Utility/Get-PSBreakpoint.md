---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 78691b806fe68aaa8d9e502d28e6f3967867f95b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600628"
---
# <span data-ttu-id="3687a-102">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3687a-102">Get-PSBreakpoint</span></span>

## <span data-ttu-id="3687a-103">개요</span><span class="sxs-lookup"><span data-stu-id="3687a-103">SYNOPSIS</span></span>
<span data-ttu-id="3687a-104">현재 세션에 설정된 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-104">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="3687a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3687a-105">SYNTAX</span></span>

### <span data-ttu-id="3687a-106">스크립트 (기본값)</span><span class="sxs-lookup"><span data-stu-id="3687a-106">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3687a-107">변수</span><span class="sxs-lookup"><span data-stu-id="3687a-107">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="3687a-108">명령</span><span class="sxs-lookup"><span data-stu-id="3687a-108">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="3687a-109">Type</span><span class="sxs-lookup"><span data-stu-id="3687a-109">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="3687a-110">Id</span><span class="sxs-lookup"><span data-stu-id="3687a-110">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="3687a-111">설명</span><span class="sxs-lookup"><span data-stu-id="3687a-111">DESCRIPTION</span></span>

<span data-ttu-id="3687a-112">**Get psbreakpoint** cmdlet은 현재 세션에 설정 된 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-112">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="3687a-113">cmdlet 매개 변수를 사용하여 특정 중단점을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-113">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="3687a-114">중단점은 명령 또는 스크립트에서 명령을 조사할 수 있도록 실행이 일시적으로 중지되는 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-114">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="3687a-115">**Get PSBreakpoint** 은 PowerShell 스크립트 및 명령을 디버깅 하기 위해 디자인 된 여러 cmdlet 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-115">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="3687a-116">PowerShell 디버거에 대 한 자세한 내용은 about_Debuggers를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3687a-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="3687a-117">예제</span><span class="sxs-lookup"><span data-stu-id="3687a-117">EXAMPLES</span></span>

### <span data-ttu-id="3687a-118">예제 1: 모든 스크립트 및 함수에 대 한 모든 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="3687a-118">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="3687a-119">이 명령은 현재 세션의 모든 스크립트 및 함수에 설정된 모든 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-119">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="3687a-120">예제 2: ID로 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="3687a-120">Example 2: Get breakpoints by ID</span></span>

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="3687a-121">이 명령은 중단점 ID가 2인 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-121">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="3687a-122">예 3: Get-PSBreakpoint에 대 한 ID 파이프</span><span class="sxs-lookup"><span data-stu-id="3687a-122">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="3687a-123">이 명령은 중단점 ID를 **Get psbreakpoint** 에 파이프 하 여 중단점을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-123">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint**.</span></span>

<span data-ttu-id="3687a-124">첫 번째 명령은 Set-PSBreakpoint cmdlet을 사용하여 Sample.ps1 스크립트의 Increment 함수에 중단점을 만들고,</span><span class="sxs-lookup"><span data-stu-id="3687a-124">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="3687a-125">$B 변수에 중단점 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-125">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="3687a-126">두 번째 명령은 점 연산자 (.)를 사용 하 여 $B 변수에서 중단점 개체의 Id 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-126">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="3687a-127">파이프라인 연산자 (|)를 사용 하 여 ID를 **Get PSBreakpoint** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-127">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="3687a-128">결과적으로, **Get psbreakpoint** 지정 된 ID의 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-128">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="3687a-129">예제 4: 지정 된 스크립트 파일에서 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="3687a-129">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="3687a-130">이 명령은 Sample.ps1 및 SupportScript.ps1 파일에서 모든 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-130">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="3687a-131">이 명령은 세션의 다른 스크립트나 함수에 설정 되었을 수 있는 다른 중단점을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-131">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="3687a-132">예 5: 지정 된 cmdlet에서 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="3687a-132">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="3687a-133">이 명령은 Sample.ps1 파일의 Read-Host 또는 Write-Host 명령에 설정된 모든 Command 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-133">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="3687a-134">예제 6: 지정 된 파일에서 명령 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="3687a-134">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="3687a-135">이 명령은 Sample.ps1 파일에서 모든 Command 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-135">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="3687a-136">예 7: 변수를 기준으로 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="3687a-136">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="3687a-137">이 명령은 $Index에 설정 된 중단점과 현재 세션의 $Swap 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-137">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="3687a-138">예 8: 파일에서 모든 줄 및 변수 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="3687a-138">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="3687a-139">이 명령은 Sample.ps1 스크립트에서 모든 줄 및 변수 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-139">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="3687a-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3687a-140">PARAMETERS</span></span>

### <span data-ttu-id="3687a-141">-Command</span><span class="sxs-lookup"><span data-stu-id="3687a-141">-Command</span></span>

<span data-ttu-id="3687a-142">지정 된 명령 이름에 설정 된 명령 중단점의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-142">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="3687a-143">cmdlet이나 함수의 이름과 같은 명령 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-143">Enter the command names, such as the name of a cmdlet or function.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3687a-144">-Id</span><span class="sxs-lookup"><span data-stu-id="3687a-144">-Id</span></span>

<span data-ttu-id="3687a-145">이 cmdlet이 가져오는 중단점 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-145">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="3687a-146">쉼표로 구분된 목록에 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-146">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="3687a-147">중단점 Id를 **psbreakpoint** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-147">You can also pipe breakpoint IDs to **Get-PSBreakpoint**.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3687a-148">-스크립트</span><span class="sxs-lookup"><span data-stu-id="3687a-148">-Script</span></span>

<span data-ttu-id="3687a-149">중단점이 포함 된 스크립트의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-149">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="3687a-150">하나 이상의 스크립트 파일의 경로 (선택 사항) 및 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-150">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="3687a-151">경로를 생략할 경우 기본 위치는 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-151">If you omit the path, the default location is the current directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3687a-152">-Type</span><span class="sxs-lookup"><span data-stu-id="3687a-152">-Type</span></span>

<span data-ttu-id="3687a-153">이 cmdlet이 가져오는 중단점 형식의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-153">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="3687a-154">하나 이상의 유형을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-154">Enter one or more types.</span></span>
<span data-ttu-id="3687a-155">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-155">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3687a-156">선</span><span class="sxs-lookup"><span data-stu-id="3687a-156">Line</span></span>
- <span data-ttu-id="3687a-157">명령</span><span class="sxs-lookup"><span data-stu-id="3687a-157">Command</span></span>
- <span data-ttu-id="3687a-158">변수</span><span class="sxs-lookup"><span data-stu-id="3687a-158">Variable</span></span>

<span data-ttu-id="3687a-159">중단점 형식을 **Get psbreakpoint** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-159">You can also pipe breakpoint types to **Get-PSBreakPoint**.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3687a-160">-Variable</span><span class="sxs-lookup"><span data-stu-id="3687a-160">-Variable</span></span>

<span data-ttu-id="3687a-161">지정 된 변수 이름에 설정 된 변수 중단점의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-161">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="3687a-162">달러 기호 없이 변수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-162">Enter the variable names without dollar signs.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3687a-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3687a-163">CommonParameters</span></span>

<span data-ttu-id="3687a-164">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3687a-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3687a-165">자세한 내용은 about_CommonParameters(https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3687a-165">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3687a-166">입력</span><span class="sxs-lookup"><span data-stu-id="3687a-166">INPUTS</span></span>

### <span data-ttu-id="3687a-167">System.object, Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3687a-167">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="3687a-168">중단점 Id 및 중단점 형식을 **Get psbreakpoint** 에 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-168">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint**.</span></span>

## <span data-ttu-id="3687a-169">출력</span><span class="sxs-lookup"><span data-stu-id="3687a-169">OUTPUTS</span></span>

### <span data-ttu-id="3687a-170">System.object. 중단점</span><span class="sxs-lookup"><span data-stu-id="3687a-170">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="3687a-171">**Get PSBreakPoint** 세션의 중단점을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-171">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="3687a-172">참고</span><span class="sxs-lookup"><span data-stu-id="3687a-172">NOTES</span></span>

* <span data-ttu-id="3687a-173">**Get PSBreakpoint** 나 해당 별칭인 "gbp"를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3687a-173">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="3687a-174">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3687a-174">RELATED LINKS</span></span>

[<span data-ttu-id="3687a-175">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3687a-175">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="3687a-176">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3687a-176">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="3687a-177">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="3687a-177">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="3687a-178">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3687a-178">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="3687a-179">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="3687a-179">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

