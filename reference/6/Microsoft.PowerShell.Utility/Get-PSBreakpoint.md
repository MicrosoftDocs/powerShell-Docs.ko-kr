---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: c130feac876ff812a854d52961ba3141ba341af0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93216650"
---
# <span data-ttu-id="81f1f-103">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="81f1f-103">Get-PSBreakpoint</span></span>

## <span data-ttu-id="81f1f-104">개요</span><span class="sxs-lookup"><span data-stu-id="81f1f-104">SYNOPSIS</span></span>
<span data-ttu-id="81f1f-105">현재 세션에 설정된 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-105">Gets the breakpoints that are set in the current session.</span></span>

## <span data-ttu-id="81f1f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="81f1f-106">SYNTAX</span></span>

### <span data-ttu-id="81f1f-107">스크립트 (기본값)</span><span class="sxs-lookup"><span data-stu-id="81f1f-107">Script (Default)</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="81f1f-108">변수</span><span class="sxs-lookup"><span data-stu-id="81f1f-108">Variable</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### <span data-ttu-id="81f1f-109">명령</span><span class="sxs-lookup"><span data-stu-id="81f1f-109">Command</span></span>

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### <span data-ttu-id="81f1f-110">유형</span><span class="sxs-lookup"><span data-stu-id="81f1f-110">Type</span></span>

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### <span data-ttu-id="81f1f-111">Id</span><span class="sxs-lookup"><span data-stu-id="81f1f-111">Id</span></span>

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="81f1f-112">설명</span><span class="sxs-lookup"><span data-stu-id="81f1f-112">DESCRIPTION</span></span>

<span data-ttu-id="81f1f-113">**Get psbreakpoint** cmdlet은 현재 세션에 설정 된 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-113">The **Get-PSBreakPoint** cmdlet gets the breakpoints that are set in the current session.</span></span>
<span data-ttu-id="81f1f-114">cmdlet 매개 변수를 사용하여 특정 중단점을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-114">You can use the cmdlet parameters to get particular breakpoints.</span></span>

<span data-ttu-id="81f1f-115">중단점은 명령 또는 스크립트에서 명령을 조사할 수 있도록 실행이 일시적으로 중지되는 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-115">A breakpoint is a point in a command or script where execution stops temporarily so that you can examine the instructions.</span></span>
<span data-ttu-id="81f1f-116">**Get PSBreakpoint** 은 PowerShell 스크립트 및 명령을 디버깅 하기 위해 디자인 된 여러 cmdlet 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-116">**Get-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts and commands.</span></span> <span data-ttu-id="81f1f-117">PowerShell 디버거에 대 한 자세한 내용은 about_Debuggers를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="81f1f-117">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="81f1f-118">예제</span><span class="sxs-lookup"><span data-stu-id="81f1f-118">EXAMPLES</span></span>

### <span data-ttu-id="81f1f-119">예제 1: 모든 스크립트 및 함수에 대 한 모든 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="81f1f-119">Example 1: Get all breakpoints for all scripts and functions</span></span>

```
PS C:\> Get-PSBreakpoint
```

<span data-ttu-id="81f1f-120">이 명령은 현재 세션의 모든 스크립트 및 함수에 설정된 모든 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-120">This command gets all breakpoints set on all scripts and functions in the current session.</span></span>

### <span data-ttu-id="81f1f-121">예제 2: ID로 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="81f1f-121">Example 2: Get breakpoints by ID</span></span>

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

<span data-ttu-id="81f1f-122">이 명령은 중단점 ID가 2인 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-122">This command gets the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="81f1f-123">예 3: Get-PSBreakpoint에 대 한 ID 파이프</span><span class="sxs-lookup"><span data-stu-id="81f1f-123">Example 3: Pipe an ID to Get-PSBreakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

<span data-ttu-id="81f1f-124">이 명령은 중단점 ID를 **Get psbreakpoint** 에 파이프 하 여 중단점을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-124">These commands show how to get a breakpoint by piping a breakpoint ID to **Get-PSBreakpoint** .</span></span>

<span data-ttu-id="81f1f-125">첫 번째 명령은 Set-PSBreakpoint cmdlet을 사용하여 Sample.ps1 스크립트의 Increment 함수에 중단점을 만들고,</span><span class="sxs-lookup"><span data-stu-id="81f1f-125">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Increment function in the Sample.ps1 script.</span></span> <span data-ttu-id="81f1f-126">$B 변수에 중단점 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-126">It saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="81f1f-127">두 번째 명령은 점 연산자 (.)를 사용 하 여 $B 변수에서 중단점 개체의 Id 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-127">The second command uses the dot operator (.) to get the Id property of the breakpoint object in the $B variable.</span></span> <span data-ttu-id="81f1f-128">파이프라인 연산자 (|)를 사용 하 여 ID를 **Get PSBreakpoint** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-128">It uses a pipeline operator (|) to send the ID to the **Get-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="81f1f-129">결과적으로, **Get psbreakpoint** 지정 된 ID의 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-129">As a result, **Get-PSBreakpoint** gets the breakpoint with the specified ID.</span></span>

### <span data-ttu-id="81f1f-130">예제 4: 지정 된 스크립트 파일에서 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="81f1f-130">Example 4: Get breakpoints in specified script files</span></span>

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

<span data-ttu-id="81f1f-131">이 명령은 Sample.ps1 및 SupportScript.ps1 파일에서 모든 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-131">This command gets all of the breakpoints in the Sample.ps1 and SupportScript.ps1 files.</span></span>

<span data-ttu-id="81f1f-132">이 명령은 세션의 다른 스크립트나 함수에 설정 되었을 수 있는 다른 중단점을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-132">This command does not get other breakpoints that might be set in other scripts or on functions in the session.</span></span>

### <span data-ttu-id="81f1f-133">예 5: 지정 된 cmdlet에서 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="81f1f-133">Example 5: Get breakpoints in specified cmdlets</span></span>

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

<span data-ttu-id="81f1f-134">이 명령은 Sample.ps1 파일의 Read-Host 또는 Write-Host 명령에 설정된 모든 Command 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-134">This command gets all Command breakpoints that are set on Read-Host or Write-Host commands in the Sample.ps1 file.</span></span>

### <span data-ttu-id="81f1f-135">예제 6: 지정 된 파일에서 명령 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="81f1f-135">Example 6: Get Command breakpoints in a specified file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

<span data-ttu-id="81f1f-136">이 명령은 Sample.ps1 파일에서 모든 Command 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-136">This command gets all Command breakpoints in the Sample.ps1 file.</span></span>

### <span data-ttu-id="81f1f-137">예 7: 변수를 기준으로 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="81f1f-137">Example 7: Get breakpoints by variable</span></span>

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

<span data-ttu-id="81f1f-138">이 명령은 $Index에 설정 된 중단점과 현재 세션의 $Swap 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-138">This command gets breakpoints that are set on the $Index and $Swap variables in the current session.</span></span>

### <span data-ttu-id="81f1f-139">예 8: 파일에서 모든 줄 및 변수 중단점 가져오기</span><span class="sxs-lookup"><span data-stu-id="81f1f-139">Example 8: Get all Line and Variable breakpoints in a file</span></span>

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

<span data-ttu-id="81f1f-140">이 명령은 Sample.ps1 스크립트에서 모든 줄 및 변수 중단점을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-140">This command gets all line and variable breakpoints in the Sample.ps1 script.</span></span>

## <span data-ttu-id="81f1f-141">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="81f1f-141">PARAMETERS</span></span>

### <span data-ttu-id="81f1f-142">-Command</span><span class="sxs-lookup"><span data-stu-id="81f1f-142">-Command</span></span>

<span data-ttu-id="81f1f-143">지정 된 명령 이름에 설정 된 명령 중단점의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-143">Specifies an array of command breakpoints that are set on the specified command names.</span></span>
<span data-ttu-id="81f1f-144">cmdlet이나 함수의 이름과 같은 명령 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-144">Enter the command names, such as the name of a cmdlet or function.</span></span>

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

### <span data-ttu-id="81f1f-145">-Id</span><span class="sxs-lookup"><span data-stu-id="81f1f-145">-Id</span></span>

<span data-ttu-id="81f1f-146">이 cmdlet이 가져오는 중단점 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-146">Specifies the breakpoint IDs that this cmdlet gets.</span></span>
<span data-ttu-id="81f1f-147">쉼표로 구분된 목록에 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-147">Enter the IDs in a comma-separated list.</span></span>
<span data-ttu-id="81f1f-148">중단점 Id를 **psbreakpoint** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-148">You can also pipe breakpoint IDs to **Get-PSBreakpoint** .</span></span>

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

### <span data-ttu-id="81f1f-149">-스크립트</span><span class="sxs-lookup"><span data-stu-id="81f1f-149">-Script</span></span>

<span data-ttu-id="81f1f-150">중단점이 포함 된 스크립트의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-150">Specifies an array of scripts that contain the breakpoints.</span></span>
<span data-ttu-id="81f1f-151">하나 이상의 스크립트 파일의 경로 (선택 사항) 및 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-151">Enter the path (optional) and names of one or more script files.</span></span>
<span data-ttu-id="81f1f-152">경로를 생략할 경우 기본 위치는 현재 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-152">If you omit the path, the default location is the current directory.</span></span>

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

### <span data-ttu-id="81f1f-153">-Type</span><span class="sxs-lookup"><span data-stu-id="81f1f-153">-Type</span></span>

<span data-ttu-id="81f1f-154">이 cmdlet이 가져오는 중단점 형식의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-154">Specifies an array of breakpoint types that this cmdlet gets.</span></span>
<span data-ttu-id="81f1f-155">하나 이상의 유형을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-155">Enter one or more types.</span></span>
<span data-ttu-id="81f1f-156">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-156">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="81f1f-157">선</span><span class="sxs-lookup"><span data-stu-id="81f1f-157">Line</span></span>
- <span data-ttu-id="81f1f-158">명령</span><span class="sxs-lookup"><span data-stu-id="81f1f-158">Command</span></span>
- <span data-ttu-id="81f1f-159">변수</span><span class="sxs-lookup"><span data-stu-id="81f1f-159">Variable</span></span>

<span data-ttu-id="81f1f-160">중단점 형식을 **Get psbreakpoint** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-160">You can also pipe breakpoint types to **Get-PSBreakPoint** .</span></span>

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

### <span data-ttu-id="81f1f-161">-Variable</span><span class="sxs-lookup"><span data-stu-id="81f1f-161">-Variable</span></span>

<span data-ttu-id="81f1f-162">지정 된 변수 이름에 설정 된 변수 중단점의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-162">Specifies an array of variable breakpoints that are set on the specified variable names.</span></span>
<span data-ttu-id="81f1f-163">달러 기호 없이 변수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-163">Enter the variable names without dollar signs.</span></span>

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

### <span data-ttu-id="81f1f-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="81f1f-164">CommonParameters</span></span>

<span data-ttu-id="81f1f-165">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="81f1f-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="81f1f-166">자세한 내용은 about_CommonParameters(https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81f1f-166">For more information, see about_CommonParameters (https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="81f1f-167">입력</span><span class="sxs-lookup"><span data-stu-id="81f1f-167">INPUTS</span></span>

### <span data-ttu-id="81f1f-168">System.object, Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="81f1f-168">System.Int32, Microsoft.PowerShell.Commands.BreakpointType</span></span>

<span data-ttu-id="81f1f-169">중단점 Id 및 중단점 형식을 **Get psbreakpoint** 에 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-169">You can pipe breakpoint IDs and breakpoint types to **Get-PSBreakPoint** .</span></span>

## <span data-ttu-id="81f1f-170">출력</span><span class="sxs-lookup"><span data-stu-id="81f1f-170">OUTPUTS</span></span>

### <span data-ttu-id="81f1f-171">System.object. 중단점</span><span class="sxs-lookup"><span data-stu-id="81f1f-171">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="81f1f-172">**Get PSBreakPoint** 세션의 중단점을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-172">**Get-PSBreakPoint** returns objects that represent the breakpoints in the session.</span></span>

## <span data-ttu-id="81f1f-173">참고</span><span class="sxs-lookup"><span data-stu-id="81f1f-173">NOTES</span></span>

* <span data-ttu-id="81f1f-174">**Get PSBreakpoint** 나 해당 별칭인 "gbp"를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81f1f-174">You can use **Get-PSBreakpoint** or its alias, "gbp".</span></span>

## <span data-ttu-id="81f1f-175">관련 링크</span><span class="sxs-lookup"><span data-stu-id="81f1f-175">RELATED LINKS</span></span>

[<span data-ttu-id="81f1f-176">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="81f1f-176">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="81f1f-177">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="81f1f-177">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="81f1f-178">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="81f1f-178">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="81f1f-179">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="81f1f-179">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="81f1f-180">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="81f1f-180">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
