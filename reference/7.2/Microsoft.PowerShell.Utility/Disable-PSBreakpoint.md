---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 2bd1a48d2075950cdb337063a100bf31534ac6fe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600443"
---
# <span data-ttu-id="f1a3c-102">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f1a3c-102">Disable-PSBreakpoint</span></span>

## <span data-ttu-id="f1a3c-103">개요</span><span class="sxs-lookup"><span data-stu-id="f1a3c-103">SYNOPSIS</span></span>
<span data-ttu-id="f1a3c-104">현재 콘솔의 중단점을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-104">Disables the breakpoints in the current console.</span></span>

## <span data-ttu-id="f1a3c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f1a3c-105">SYNTAX</span></span>

### <span data-ttu-id="f1a3c-106">중단점 (기본값)</span><span class="sxs-lookup"><span data-stu-id="f1a3c-106">Breakpoint (Default)</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f1a3c-107">Id</span><span class="sxs-lookup"><span data-stu-id="f1a3c-107">Id</span></span>

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f1a3c-108">설명</span><span class="sxs-lookup"><span data-stu-id="f1a3c-108">DESCRIPTION</span></span>

<span data-ttu-id="f1a3c-109">**Disable-psbreakpoint** cmdlet은 스크립트가 실행 될 때 적중 되지 않도록 하는 중단점을 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-109">The **Disable-PSBreakpoint** cmdlet disables breakpoints, which assures that they are not hit when the script runs.</span></span>
<span data-ttu-id="f1a3c-110">이 cmdlet을 사용하여 모든 중단점을 해제하거나 중단점 개체 또는 중단점 ID를 제출하여 중단점을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-110">You can use it to disable all breakpoints, or you can specify breakpoints by submitting breakpoint objects or breakpoint IDs.</span></span>

<span data-ttu-id="f1a3c-111">기술적으로 이 cmdlet은 중단점 개체의 Enabled 속성 값을 False로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-111">Technically, this cmdlet changes the value of the Enabled property of a breakpoint object to False.</span></span>
<span data-ttu-id="f1a3c-112">중단점을 다시 설정하려면 Enable-PSBreakpoint cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-112">To re-enable a breakpoint, use the Enable-PSBreakpoint cmdlet.</span></span>
<span data-ttu-id="f1a3c-113">Set-PSBreakpoint cmdlet을 사용하여 중단점을 만드는 경우 중단점이 기본적으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-113">Breakpoints are enabled by default when you create them by using the Set-PSBreakpoint cmdlet.</span></span>

<span data-ttu-id="f1a3c-114">중단점은 스크립트의 명령을 검사할 수 있도록 실행이 일시적으로 중지되는 스크립트의 한 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-114">A breakpoint is a point in a script where execution stops temporarily so that you can examine the instructions in the script.</span></span>
<span data-ttu-id="f1a3c-115">**Disable-PSBreakpoint** PowerShell 스크립트를 디버깅 하기 위해 디자인 된 여러 cmdlet 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-115">**Disable-PSBreakpoint** is one of several cmdlets designed for debugging PowerShell scripts.</span></span>
<span data-ttu-id="f1a3c-116">PowerShell 디버거에 대 한 자세한 내용은 about_Debuggers를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-116">For more information about the PowerShell debugger, see about_Debuggers.</span></span>

## <span data-ttu-id="f1a3c-117">예제</span><span class="sxs-lookup"><span data-stu-id="f1a3c-117">EXAMPLES</span></span>

### <span data-ttu-id="f1a3c-118">예제 1: 중단점 설정 및 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="f1a3c-118">Example 1: Set a breakpoint and disable it</span></span>

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

<span data-ttu-id="f1a3c-119">이 명령은 새로 만든 중단점을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-119">These commands disable a newly-created breakpoint.</span></span>

<span data-ttu-id="f1a3c-120">첫 번째 명령은 Set-PSBreakpoint cmdlet을 사용 하 여 Sample.ps1 스크립트의 *이름* 변수에 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-120">The first command uses the Set-PSBreakpoint cmdlet to create a breakpoint on the *Name* variable in the Sample.ps1 script.</span></span>
<span data-ttu-id="f1a3c-121">그런 다음 $B 변수에 중단점 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-121">Then, it saves the breakpoint object in the $B variable.</span></span>

<span data-ttu-id="f1a3c-122">두 번째 명령은 **disable-psbreakpoint** cmdlet을 사용 하 여 새 중단점을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-122">The second command uses the **Disable-PSBreakpoint** cmdlet to disable the new breakpoint.</span></span>
<span data-ttu-id="f1a3c-123">파이프라인 연산자 (|)를 사용 하 여 $B에 있는 중단점 개체를 **Disable-PSBreakpoint** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-123">It uses a pipeline operator (|) to send the breakpoint object in $B to the **Disable-PSBreakpoint** cmdlet.</span></span>

<span data-ttu-id="f1a3c-124">이 명령의 결과로 $B에 있는 중단점 개체의 Enabled 속성 값은 False입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-124">As a result of this command, the value of the Enabled property of the breakpoint object in $B is False.</span></span>

### <span data-ttu-id="f1a3c-125">예제 2: 중단점 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="f1a3c-125">Example 2: Disable a breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Id 0
```

<span data-ttu-id="f1a3c-126">이 명령은 중단점 ID가 0인 중단점을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-126">This command disables the breakpoint with breakpoint ID 0.</span></span>

### <span data-ttu-id="f1a3c-127">예제 3: 비활성화 된 중단점 만들기</span><span class="sxs-lookup"><span data-stu-id="f1a3c-127">Example 3: Create a disabled breakpoint</span></span>

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

<span data-ttu-id="f1a3c-128">이 명령은 설정할 때까지 해제된 상태로 있는 새 중단점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-128">This command creates a new breakpoint that is disabled until you enable it.</span></span>

<span data-ttu-id="f1a3c-129">**Disable-psbreakpoint** cmdlet을 사용 하 여 중단점을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-129">It uses the **Disable-PSBreakpoint** cmdlet to disable the breakpoint.</span></span>
<span data-ttu-id="f1a3c-130">*중단점* 매개 변수 값은 새 중단점을 설정 하 고, 중단점 개체를 생성 하 고, 개체를 $B 변수에 저장 하는 Set-PSBreakpoint 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-130">The value of the *Breakpoint* parameter is a Set-PSBreakpoint command that sets a new breakpoint, generates a breakpoint object, and saves the object in the $B variable.</span></span>

<span data-ttu-id="f1a3c-131">값으로 개체를 사용하는 cmdlet 매개 변수는 개체 또는 개체를 가져오거나 생성하는 명령이 포함된 변수를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-131">Cmdlet parameters that take objects as their values can accept a variable that contains the object or a command that gets or generates the object.</span></span>
<span data-ttu-id="f1a3c-132">이 경우 **Set-PSBreakpoint** 중단점 개체를 생성 하므로 *중단점* 매개 변수의 값으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-132">In this case, because **Set-PSBreakpoint** generates a breakpoint object, it can be used as the value of the *Breakpoint* parameter.</span></span>

<span data-ttu-id="f1a3c-133">두 번째 명령은 $B 변수 값에 있는 중단점 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-133">The second command displays the breakpoint object in the value of the $B variable.</span></span>

### <span data-ttu-id="f1a3c-134">예제 4: 현재 콘솔의 모든 중단점 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="f1a3c-134">Example 4: Disable all breakpoints in the current console</span></span>

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

<span data-ttu-id="f1a3c-135">이 명령은 현재 콘솔의 모든 중단점을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-135">This command disables all breakpoints in the current console.</span></span>
<span data-ttu-id="f1a3c-136">이 명령의 약어는 다음과 같이 지정할 수 있습니다. "gbp | .dbp ".</span><span class="sxs-lookup"><span data-stu-id="f1a3c-136">You can abbreviate this command as: "gbp | dbp".</span></span>

## <span data-ttu-id="f1a3c-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="f1a3c-137">PARAMETERS</span></span>

### <span data-ttu-id="f1a3c-138">-중단점</span><span class="sxs-lookup"><span data-stu-id="f1a3c-138">-Breakpoint</span></span>

<span data-ttu-id="f1a3c-139">해제할 중단점을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-139">Specifies the breakpoints to disable.</span></span>
<span data-ttu-id="f1a3c-140">중단점 개체가 포함된 변수를 입력하거나 중단점 개체를 가져오는 명령(예: Get-PSBreakpoint 명령)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-140">Enter a variable that contains breakpoint objects or a command that gets breakpoint objects, such as a Get-PSBreakpoint command.</span></span>
<span data-ttu-id="f1a3c-141">중단점 개체를 **Disable-psbreakpoint** cmdlet으로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-141">You can also pipe breakpoint objects to the **Disable-PSBreakpoint** cmdlet.</span></span>

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

### <span data-ttu-id="f1a3c-142">-Id</span><span class="sxs-lookup"><span data-stu-id="f1a3c-142">-Id</span></span>

<span data-ttu-id="f1a3c-143">지정한 중단점 ID를 가진 중단점을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-143">Disables the breakpoints with the specified breakpoint IDs.</span></span>
<span data-ttu-id="f1a3c-144">ID 또는 ID가 포함된 변수를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-144">Enter the IDs or a variable that contains the IDs.</span></span>
<span data-ttu-id="f1a3c-145">**-PSBreakpoint을 사용 하지 않도록 설정** 하려면 id를 파이프 할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-145">You cannot pipe IDs to **Disable-PSBreakpoint**.</span></span>

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

### <span data-ttu-id="f1a3c-146">-PassThru</span><span class="sxs-lookup"><span data-stu-id="f1a3c-146">-PassThru</span></span>

<span data-ttu-id="f1a3c-147">설정된 중단점을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-147">Returns an object representing the enabled breakpoints.</span></span>
<span data-ttu-id="f1a3c-148">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-148">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f1a3c-149">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f1a3c-149">-Confirm</span></span>

<span data-ttu-id="f1a3c-150">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-150">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f1a3c-151">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f1a3c-151">-WhatIf</span></span>

<span data-ttu-id="f1a3c-152">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-152">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f1a3c-153">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-153">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f1a3c-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f1a3c-154">CommonParameters</span></span>

<span data-ttu-id="f1a3c-155">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f1a3c-156">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f1a3c-157">입력</span><span class="sxs-lookup"><span data-stu-id="f1a3c-157">INPUTS</span></span>

### <span data-ttu-id="f1a3c-158">System.object. 중단점</span><span class="sxs-lookup"><span data-stu-id="f1a3c-158">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="f1a3c-159">중단점 개체를 **사용 하지 않도록 설정 하 여-PSBreakpoint을 사용 하지 않도록 설정할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-159">You can pipe a breakpoint object to **Disable-PSBreakpoint**.</span></span>

## <span data-ttu-id="f1a3c-160">출력</span><span class="sxs-lookup"><span data-stu-id="f1a3c-160">OUTPUTS</span></span>

### <span data-ttu-id="f1a3c-161">없음 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="f1a3c-161">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="f1a3c-162">*PassThru* 매개 변수를 사용 하는 경우 **-psbreakpoint** 사용 하지 않도록 설정 된 중단점을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-162">When you use the *PassThru* parameter, **Disable-PSBreakpoint** returns an object that represents the disabled breakpoint.</span></span>
<span data-ttu-id="f1a3c-163">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1a3c-163">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f1a3c-164">참고</span><span class="sxs-lookup"><span data-stu-id="f1a3c-164">NOTES</span></span>

## <span data-ttu-id="f1a3c-165">관련 링크</span><span class="sxs-lookup"><span data-stu-id="f1a3c-165">RELATED LINKS</span></span>

[<span data-ttu-id="f1a3c-166">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f1a3c-166">Enable-PSBreakpoint</span></span>](Enable-PSBreakpoint.md)

[<span data-ttu-id="f1a3c-167">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f1a3c-167">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="f1a3c-168">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="f1a3c-168">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="f1a3c-169">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f1a3c-169">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="f1a3c-170">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="f1a3c-170">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

