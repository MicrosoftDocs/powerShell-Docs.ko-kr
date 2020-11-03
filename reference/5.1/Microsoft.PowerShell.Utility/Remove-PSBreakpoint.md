---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: b12913cd10c2c505322c1f922a05ecc98987e830
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213754"
---
# <span data-ttu-id="0a44f-103">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a44f-103">Remove-PSBreakpoint</span></span>

## <span data-ttu-id="0a44f-104">개요</span><span class="sxs-lookup"><span data-stu-id="0a44f-104">SYNOPSIS</span></span>
<span data-ttu-id="0a44f-105">현재 콘솔에서 중단점을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-105">Deletes breakpoints from the current console.</span></span>

## <span data-ttu-id="0a44f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0a44f-106">SYNTAX</span></span>

### <span data-ttu-id="0a44f-107">중단점 (기본값)</span><span class="sxs-lookup"><span data-stu-id="0a44f-107">Breakpoint (Default)</span></span>

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0a44f-108">Id</span><span class="sxs-lookup"><span data-stu-id="0a44f-108">Id</span></span>

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0a44f-109">설명</span><span class="sxs-lookup"><span data-stu-id="0a44f-109">DESCRIPTION</span></span>
<span data-ttu-id="0a44f-110">**Remove psbreakpoint** cmdlet은 중단점을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-110">The **Remove-PSBreakpoint** cmdlet deletes a breakpoint.</span></span>
<span data-ttu-id="0a44f-111">중단점 개체 또는 중단점 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-111">Enter a breakpoint object or a breakpoint ID.</span></span>

<span data-ttu-id="0a44f-112">중단점을 제거하면 중단점 개체는 더 이상 사용할 수 없게 되며 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-112">When you remove a breakpoint, the breakpoint object is no longer available or functional.</span></span>
<span data-ttu-id="0a44f-113">변수에 중단점 개체를 저장한 경우 참조는 계속 존재하지만 중단점은 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-113">If you have saved a breakpoint object in a variable, the reference still exists, but the breakpoint does not function.</span></span>

<span data-ttu-id="0a44f-114">**Remove-PSBreakpoint** Windows PowerShell 스크립트를 디버깅 하기 위해 디자인 된 여러 cmdlet 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-114">**Remove-PSBreakpoint** is one of several cmdlets designed for debugging Windows PowerShell scripts.</span></span>
<span data-ttu-id="0a44f-115">Windows PowerShell 디버거에 대한 자세한 내용은 about_Debuggers를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a44f-115">For more information about the Windows PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="0a44f-116">예제</span><span class="sxs-lookup"><span data-stu-id="0a44f-116">EXAMPLES</span></span>

### <span data-ttu-id="0a44f-117">예제 1: 모든 중단점 제거</span><span class="sxs-lookup"><span data-stu-id="0a44f-117">Example 1: Remove all breakpoints</span></span>

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

<span data-ttu-id="0a44f-118">이 명령은 현재 콘솔의 모든 중단점을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-118">This command deletes all of the breakpoints in the current console.</span></span>

### <span data-ttu-id="0a44f-119">예제 2: 지정 된 중단점 제거</span><span class="sxs-lookup"><span data-stu-id="0a44f-119">Example 2: Remove a specified breakpoint</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

<span data-ttu-id="0a44f-120">이 명령은 중단점을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-120">This command deletes a breakpoint.</span></span>

<span data-ttu-id="0a44f-121">첫 번째 명령은 Set-PSBreakpoint cmdlet을 사용하여 Sample.ps1 스크립트의 Name 변수에 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-121">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the Name variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="0a44f-122">그런 다음 $B 변수에 중단점 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-122">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="0a44f-123">두 번째 명령은 **Remove psbreakpoint** cmdlet을 사용 하 여 새 중단점을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-123">The second command uses the **Remove-PSBreakpoint** cmdlet to delete the new breakpoint.</span></span>
<span data-ttu-id="0a44f-124">파이프라인 연산자 (|)를 사용 하 여 $B 변수의 중단점 개체를 **Remove PSBreakpoint** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-124">It uses a pipeline operator (|) to send the breakpoint object in the $B variable to the **Remove-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="0a44f-125">이 명령을 실행한 후에 실행하는 스크립트는 중지되지 않고 끝까지 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-125">As a result of this command, if you run the script, it runs to completion without stopping.</span></span>
<span data-ttu-id="0a44f-126">또한, **Get psbreakpoint** cmdlet은이 중단점을 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-126">Also, the **Get-PSBreakpoint** cmdlet does not return this breakpoint.</span></span>

### <span data-ttu-id="0a44f-127">예제 3: ID로 중단점 제거</span><span class="sxs-lookup"><span data-stu-id="0a44f-127">Example 3: Remove a breakpoint by ID</span></span>

```
PS C:\> Remove-PSBreakpoint -Id 2
```

<span data-ttu-id="0a44f-128">이 명령은 중단점 ID가 2인 중단점을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-128">This command deletes the breakpoint with breakpoint ID 2.</span></span>

### <span data-ttu-id="0a44f-129">예제 4: 함수를 사용 하 여 모든 중단점 제거</span><span class="sxs-lookup"><span data-stu-id="0a44f-129">Example 4: Use a function to remove all breakpoints</span></span>

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

<span data-ttu-id="0a44f-130">이 간단한 함수는 현재 콘솔의 모든 중단점을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-130">This simple function deletes all of the breakpoints in the current console.</span></span>
<span data-ttu-id="0a44f-131">함수는 Get-PSBreakpoint cmdlet을 사용하여 중단점을 가져오며</span><span class="sxs-lookup"><span data-stu-id="0a44f-131">It uses the Get-PSBreakpoint cmdlet to get the breakpoints.</span></span>
<span data-ttu-id="0a44f-132">그런 다음 파이프라인 연산자 (|)를 사용 하 여 중단점을 **Remove psbreakpoint** cmdlet으로 보냅니다. 그러면이 cmdlet이 중단점을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-132">Then, it uses a pipeline operator (|) to send the breakpoints to the **Remove-PSBreakpoint** cmdlet, which deletes them.</span></span>

<span data-ttu-id="0a44f-133">따라서 `del-psb` 더 긴 명령 대신을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-133">As a result, you can type `del-psb` instead of the longer command.</span></span>

<span data-ttu-id="0a44f-134">함수를 저장하려면 Windows PowerShell 프로필에 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="0a44f-134">To save the function, add it to your Windows PowerShell profile.</span></span>

## <span data-ttu-id="0a44f-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="0a44f-135">PARAMETERS</span></span>

### <span data-ttu-id="0a44f-136">-중단점</span><span class="sxs-lookup"><span data-stu-id="0a44f-136">-Breakpoint</span></span>
<span data-ttu-id="0a44f-137">삭제할 중단점을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-137">Specifies the breakpoints to delete.</span></span>
<span data-ttu-id="0a44f-138">중단점 개체를 포함 하는 변수를 입력 하거나 중단점 개체 (예: **Get PSBreakpoint command)** 를 가져오는 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-138">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a **Get-PSBreakpoint** command.</span></span>
<span data-ttu-id="0a44f-139">중단점 개체를 **-Psbreakpoint 제거** 하도록 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-139">You can also pipe breakpoint objects to **Remove-PSBreakpoint** .</span></span>

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0a44f-140">-Id</span><span class="sxs-lookup"><span data-stu-id="0a44f-140">-Id</span></span>
<span data-ttu-id="0a44f-141">이 cmdlet이 중단점을 삭제 하는 중단점 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-141">Specifies breakpoint IDs for which this cmdlet deletes breakpoints.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="0a44f-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0a44f-142">-Confirm</span></span>
<span data-ttu-id="0a44f-143">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="0a44f-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0a44f-144">-WhatIf</span></span>
<span data-ttu-id="0a44f-145">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-145">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="0a44f-146">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0a44f-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0a44f-147">CommonParameters</span></span>
<span data-ttu-id="0a44f-148">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0a44f-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0a44f-149">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0a44f-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0a44f-150">입력</span><span class="sxs-lookup"><span data-stu-id="0a44f-150">INPUTS</span></span>

### <span data-ttu-id="0a44f-151">System.object. 중단점</span><span class="sxs-lookup"><span data-stu-id="0a44f-151">System.Management.Automation.Breakpoint</span></span>
<span data-ttu-id="0a44f-152">중단점 개체를 **-Psbreakpoint 제거** 하도록 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-152">You can pipe breakpoint objects to **Remove-PSBreakpoint** .</span></span>

## <span data-ttu-id="0a44f-153">출력</span><span class="sxs-lookup"><span data-stu-id="0a44f-153">OUTPUTS</span></span>

### <span data-ttu-id="0a44f-154">없음</span><span class="sxs-lookup"><span data-stu-id="0a44f-154">None</span></span>
<span data-ttu-id="0a44f-155">이 cmdlet에서 어떠한 출력도 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0a44f-155">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="0a44f-156">참고</span><span class="sxs-lookup"><span data-stu-id="0a44f-156">NOTES</span></span>

## <span data-ttu-id="0a44f-157">관련 링크</span><span class="sxs-lookup"><span data-stu-id="0a44f-157">RELATED LINKS</span></span>

[<span data-ttu-id="0a44f-158">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a44f-158">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="0a44f-159">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a44f-159">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="0a44f-160">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a44f-160">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="0a44f-161">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="0a44f-161">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="0a44f-162">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="0a44f-162">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)
