---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 28cda7a2fa4435092b647e43a250222a852114b0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602252"
---
# <span data-ttu-id="41a53-102">Enable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="41a53-102">Enable-PSBreakpoint</span></span>

## <span data-ttu-id="41a53-103">개요</span><span class="sxs-lookup"><span data-stu-id="41a53-103">SYNOPSIS</span></span>
<span data-ttu-id="41a53-104">현재 콘솔의 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-104">Enables the breakpoints in the current console.</span></span>

## <span data-ttu-id="41a53-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41a53-105">SYNTAX</span></span>

### <span data-ttu-id="41a53-106">Id (기본값)</span><span class="sxs-lookup"><span data-stu-id="41a53-106">Id (Default)</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="41a53-107">중단점</span><span class="sxs-lookup"><span data-stu-id="41a53-107">Breakpoint</span></span>

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="41a53-108">설명</span><span class="sxs-lookup"><span data-stu-id="41a53-108">DESCRIPTION</span></span>

<span data-ttu-id="41a53-109">`Enable-PSBreakpoint`Cmdlet은 해제 된 중단점을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-109">The `Enable-PSBreakpoint` cmdlet re-enables disabled breakpoints.</span></span> <span data-ttu-id="41a53-110">중단점 개체 또는 Id를 제공 하 여 모든 중단점 또는 특정 중단점을 사용 하도록 설정 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-110">You can use it to enable all breakpoints, or specific breakpoints by providing breakpoint objects or IDs.</span></span>

<span data-ttu-id="41a53-111">중단점은 스크립트의 상태를 검사할 수 있도록 실행이 일시적으로 중지 되는 스크립트의 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-111">A breakpoint is a point in a script where execution stops temporarily so that you can examine the state of the script.</span></span> <span data-ttu-id="41a53-112">새로 만든 중단점은 자동으로 사용 하도록 설정 되지만를 사용 하 여 사용 하지 않도록 설정할 수 있습니다 `Disable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="41a53-112">Newly created breakpoints are automatically enabled, but can be disabled using `Disable-PSBreakpoint`.</span></span>

<span data-ttu-id="41a53-113">기술적으로이 cmdlet은 중단점 개체의 **Enabled** 속성 값을 **True** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-113">Technically, this cmdlet changes the value of the **Enabled** property of a breakpoint object to **True**.</span></span>

<span data-ttu-id="41a53-114">`Enable-PSBreakpoint` 는 PowerShell 스크립트 디버깅을 위해 설계 된 여러 cmdlet 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-114">`Enable-PSBreakpoint` is one of several cmdlets designed for debugging PowerShell scripts.</span></span> <span data-ttu-id="41a53-115">PowerShell 디버거에 대 한 자세한 내용은 [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="41a53-115">For more information about the PowerShell debugger, see [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).</span></span>

## <span data-ttu-id="41a53-116">예제</span><span class="sxs-lookup"><span data-stu-id="41a53-116">EXAMPLES</span></span>

### <span data-ttu-id="41a53-117">예제 1: 모든 중단점 사용</span><span class="sxs-lookup"><span data-stu-id="41a53-117">Example 1: Enable all breakpoints</span></span>

<span data-ttu-id="41a53-118">이 예에서는 현재 세션의 모든 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-118">This example enables all breakpoints in the current session.</span></span>

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

<span data-ttu-id="41a53-119">별칭을 사용 하 여이 예제를 약식으로 사용할 수 있습니다 `gbp | ebp` .</span><span class="sxs-lookup"><span data-stu-id="41a53-119">Using aliases, this example can be abbreviated as `gbp | ebp`.</span></span>

### <span data-ttu-id="41a53-120">예제 2: ID로 중단점 사용</span><span class="sxs-lookup"><span data-stu-id="41a53-120">Example 2: Enable breakpoints by ID</span></span>

<span data-ttu-id="41a53-121">이 예제에서는 중단점 Id를 사용 하 여 여러 중단점을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-121">This example enables multiple breakpoints using their breakpoint IDs.</span></span>

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### <span data-ttu-id="41a53-122">예제 3: 비활성화 된 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="41a53-122">Example 3: Enable a disabled breakpoint</span></span>

<span data-ttu-id="41a53-123">이 예제에서는 사용 하지 않도록 설정 된 중단점을 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-123">This example re-enables a breakpoint that has been disabled.</span></span>

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

<span data-ttu-id="41a53-124">`Set-PSBreakpoint` `Sample.ps1` 변수에 중단점 개체를 저장 하는 스크립트의 이름 변수에 중단점을 만듭니다 `$B` .</span><span class="sxs-lookup"><span data-stu-id="41a53-124">`Set-PSBreakpoint` creates a breakpoint on the **Name** variable in the `Sample.ps1` script saving the breakpoint object in the `$B` variable.</span></span> <span data-ttu-id="41a53-125">**PassThru** 매개 변수는 중단점의 **Enabled** 속성 값이 **False** 인 것을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-125">The **PassThru** parameter displays the value of the **Enabled** property of the breakpoint is **False**.</span></span>

<span data-ttu-id="41a53-126">`Enable-PSBreakpoint` 중단점을 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-126">`Enable-PSBreakpoint` re-enables the breakpoint.</span></span> <span data-ttu-id="41a53-127">다시 **PassThru** 매개 변수를 사용 하 여 Enabled 속성의 값이 **True** 인 것을 확인할 **수** 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-127">Again, using the **PassThru** parameter we see that the value of the **Enabled** property is **True**.</span></span>

### <span data-ttu-id="41a53-128">예제 4: 변수를 사용 하 여 중단점 설정</span><span class="sxs-lookup"><span data-stu-id="41a53-128">Example 4: Enable breakpoints using a variable</span></span>

<span data-ttu-id="41a53-129">이 예제에서는 중단점 개체를 사용 하 여 중단점 집합을 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-129">This example enables a set of breakpoints using the breakpoint objects.</span></span>

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

<span data-ttu-id="41a53-130">`Get-PSBreakpoint` 중단점을 가져와서 `$B` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-130">`Get-PSBreakpoint` gets the breakpoints and saves them in the `$B` variable.</span></span> <span data-ttu-id="41a53-131">**중단점** 매개 변수를 사용 하 여 중단점을 사용 `Enable-PSBreakpoint` 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-131">Using the **Breakpoint** parameter, `Enable-PSBreakpoint` enables the breakpoints.</span></span>

<span data-ttu-id="41a53-132">이 예제는를 실행 하는 것과 같습니다 `Enable-PSBreakpoint -Id 3, 5` .</span><span class="sxs-lookup"><span data-stu-id="41a53-132">This example is equivalent to running `Enable-PSBreakpoint -Id 3, 5`.</span></span>

## <span data-ttu-id="41a53-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="41a53-133">PARAMETERS</span></span>

### <span data-ttu-id="41a53-134">-중단점</span><span class="sxs-lookup"><span data-stu-id="41a53-134">-Breakpoint</span></span>

<span data-ttu-id="41a53-135">설정할 중단점을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-135">Specifies the breakpoints to enable.</span></span> <span data-ttu-id="41a53-136">중단점을 포함 하는 변수 또는와 같은 중단점 개체를 가져오는 명령을 제공 `Get-PSBreakpoint` 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-136">Provide a variable containing breakpoints or a command that gets breakpoint objects, such as `Get-PSBreakpoint`.</span></span> <span data-ttu-id="41a53-137">중단점 개체를로 파이프 할 수도 있습니다 `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="41a53-137">You can also pipe breakpoint objects to `Enable-PSBreakpoint`.</span></span>

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

### <span data-ttu-id="41a53-138">-Id</span><span class="sxs-lookup"><span data-stu-id="41a53-138">-Id</span></span>

<span data-ttu-id="41a53-139">사용할 중단점의 **Id** 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-139">Specifies the **Id** numbers of the breakpoints to enable.</span></span> <span data-ttu-id="41a53-140">기본값은 모든 중단점입니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-140">The default value is all breakpoints.</span></span>
<span data-ttu-id="41a53-141">**Id** 를 숫자나 변수로 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-141">Provide the **Id** by number or in a variable.</span></span> <span data-ttu-id="41a53-142">**Id** 번호는로 파이프 할 수 없습니다 `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="41a53-142">You can't pipe **Id** numbers to `Enable-PSBreakpoint`.</span></span> <span data-ttu-id="41a53-143">중단점의 **Id** 를 확인 하려면 cmdlet을 사용 합니다 `Get-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="41a53-143">To find the **Id** of a breakpoint, use the `Get-PSBreakpoint` cmdlet.</span></span>

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

### <span data-ttu-id="41a53-144">-PassThru</span><span class="sxs-lookup"><span data-stu-id="41a53-144">-PassThru</span></span>

<span data-ttu-id="41a53-145">사용할 중단점을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-145">Returns an object representing the breakpoint being enabled.</span></span> <span data-ttu-id="41a53-146">기본적으로이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-146">By default, this cmdlet doesn't generate any output.</span></span>

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

### <span data-ttu-id="41a53-147">-Confirm</span><span class="sxs-lookup"><span data-stu-id="41a53-147">-Confirm</span></span>

<span data-ttu-id="41a53-148">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-148">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="41a53-149">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="41a53-149">-WhatIf</span></span>

<span data-ttu-id="41a53-150">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-150">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="41a53-151">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-151">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="41a53-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41a53-152">CommonParameters</span></span>

<span data-ttu-id="41a53-153">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41a53-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41a53-154">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="41a53-154">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41a53-155">입력</span><span class="sxs-lookup"><span data-stu-id="41a53-155">INPUTS</span></span>

### <span data-ttu-id="41a53-156">System.object. 중단점</span><span class="sxs-lookup"><span data-stu-id="41a53-156">System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="41a53-157">중단점 개체를로 파이프 할 수 있습니다 `Enable-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="41a53-157">You can pipe a breakpoint object to `Enable-PSBreakpoint`.</span></span>

## <span data-ttu-id="41a53-158">출력</span><span class="sxs-lookup"><span data-stu-id="41a53-158">OUTPUTS</span></span>

### <span data-ttu-id="41a53-159">없음 또는 System.object</span><span class="sxs-lookup"><span data-stu-id="41a53-159">None or System.Management.Automation.Breakpoint</span></span>

<span data-ttu-id="41a53-160">**PassThru** 매개 변수를 사용 하는 경우은 `Enable-PSBreakpoint` 사용 하도록 설정 된 중단점을 나타내는 중단점 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-160">When you use the **PassThru** parameter, `Enable-PSBreakpoint` returns a breakpoint object that represents that breakpoint that was enabled.</span></span> <span data-ttu-id="41a53-161">그렇지 않으면이 cmdlet은 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-161">Otherwise, this cmdlet doesn't generate any output.</span></span>

## <span data-ttu-id="41a53-162">참고</span><span class="sxs-lookup"><span data-stu-id="41a53-162">NOTES</span></span>

- <span data-ttu-id="41a53-163">`Enable-PSBreakpoint`이미 사용 하도록 설정 된 중단점을 설정 하려고 하면 cmdlet에서 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-163">The `Enable-PSBreakpoint` cmdlet doesn't generate an error if you try to enable a breakpoint that is already enabled.</span></span> <span data-ttu-id="41a53-164">따라서 중단점 중 몇 개만 해제되어 있는 경우에도 오류 없이 모든 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-164">As such, you can enable all breakpoints without error, even when only a few are disabled.</span></span>

- <span data-ttu-id="41a53-165">중단점은 cmdlet을 사용 하 여 만들 때 사용할 수 있습니다 `Set-PSBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="41a53-165">Breakpoints are enabled when you create them by using the `Set-PSBreakpoint` cmdlet.</span></span> <span data-ttu-id="41a53-166">새로 만든 중단점을 설정 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="41a53-166">You don't need to enable newly created breakpoints.</span></span>

## <span data-ttu-id="41a53-167">관련 링크</span><span class="sxs-lookup"><span data-stu-id="41a53-167">RELATED LINKS</span></span>

[<span data-ttu-id="41a53-168">Disable-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="41a53-168">Disable-PSBreakpoint</span></span>](Disable-PSBreakpoint.md)

[<span data-ttu-id="41a53-169">Get-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="41a53-169">Get-PSBreakpoint</span></span>](Get-PSBreakpoint.md)

[<span data-ttu-id="41a53-170">Get-PSCallStack</span><span class="sxs-lookup"><span data-stu-id="41a53-170">Get-PSCallStack</span></span>](Get-PSCallStack.md)

[<span data-ttu-id="41a53-171">Remove-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="41a53-171">Remove-PSBreakpoint</span></span>](Remove-PSBreakpoint.md)

[<span data-ttu-id="41a53-172">Set-PSBreakpoint</span><span class="sxs-lookup"><span data-stu-id="41a53-172">Set-PSBreakpoint</span></span>](Set-PSBreakpoint.md)

