---
description: 특성을 지정 하는 함수가 `CmdletBinding` 컴파일된 cmdlet에 사용할 수 있는 메서드 및 속성을 사용할 수 있는 방법에 대해 설명 합니다.
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_functions_advanced_methods?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Functions_Advanced_Methods
ms.openlocfilehash: 13a9d7258f1a52d5fcbb2d8c55b91c8d6454452d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600868"
---
# <a name="about-functions-advanced-methods"></a><span data-ttu-id="bf1b4-103">함수 고급 메서드 정보</span><span class="sxs-lookup"><span data-stu-id="bf1b4-103">About Functions Advanced Methods</span></span>

## <a name="short-description"></a><span data-ttu-id="bf1b4-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="bf1b4-104">Short description</span></span>

<span data-ttu-id="bf1b4-105">특성을 지정 하는 함수가 `CmdletBinding` 컴파일된 cmdlet에 사용할 수 있는 메서드 및 속성을 사용할 수 있는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-105">Describes how functions that specify the `CmdletBinding` attribute can use the methods and properties that are available to compiled cmdlets.</span></span>

## <a name="long-description"></a><span data-ttu-id="bf1b4-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-106">Long description</span></span>

<span data-ttu-id="bf1b4-107">특성을 지정 하는 함수는 `CmdletBinding` 변수를 통해 여러 메서드와 속성에 액세스할 수 있습니다 `$PSCmdlet` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-107">Functions that specify the `CmdletBinding` attribute can access a number of methods and properties through the `$PSCmdlet` variable.</span></span> <span data-ttu-id="bf1b4-108">이러한 메서드에는 다음과 같은 메서드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-108">These methods include the following methods:</span></span>

- <span data-ttu-id="bf1b4-109">컴파일된 cmdlet이 작업을 수행 하는 데 사용 하는 입력 처리 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-109">Input-processing methods that compiled cmdlets use to do their work.</span></span>
- <span data-ttu-id="bf1b4-110">`ShouldProcess`작업을 `ShouldContinue` 수행 하기 전에 사용자 의견을 가져오는 데 사용 되는 및 메서드.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-110">The `ShouldProcess` and `ShouldContinue` methods that are used to get user feedback before an action is performed.</span></span>
- <span data-ttu-id="bf1b4-111">`ThrowTerminatingError`오류 레코드를 생성 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-111">The `ThrowTerminatingError` method for generating error records.</span></span>
- <span data-ttu-id="bf1b4-112">여러 가지 `Write` 형식의 출력을 반환 하는 메서드</span><span class="sxs-lookup"><span data-stu-id="bf1b4-112">Several `Write` methods that return different types of output.</span></span>

<span data-ttu-id="bf1b4-113">**PSCmdlet** 클래스의 모든 메서드 및 속성은 고급 함수에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-113">All the methods and properties of the **PSCmdlet** class are available to advanced functions.</span></span> <span data-ttu-id="bf1b4-114">자세한 내용은 [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-114">For more information, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="bf1b4-115">특성에 대 한 자세한 내용은 `CmdletBinding` [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-115">For more information about the `CmdletBinding` attribute, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md).</span></span>
<span data-ttu-id="bf1b4-116">**Cmdletbindingattribute** 클래스의 경우에는 [system.object](/dotnet/api/system.management.automation.cmdletbindingattribute)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-116">For the **CmdletBindingAttribute** class, see [System.Management.Automation.Cmdlet.CmdletBindingAttribute](/dotnet/api/system.management.automation.cmdletbindingattribute).</span></span>

### <a name="input-processing-methods"></a><span data-ttu-id="bf1b4-117">입력 처리 방법</span><span class="sxs-lookup"><span data-stu-id="bf1b4-117">Input processing methods</span></span>

<span data-ttu-id="bf1b4-118">이 섹션에서 설명 하는 메서드를 입력 처리 메서드 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-118">The methods described in this section are referred to as the input processing methods.</span></span> <span data-ttu-id="bf1b4-119">함수의 경우이 세 가지 메서드는 `Begin` `Process` 함수의, 및 블록으로 표현 됩니다 `End` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-119">For functions, these three methods are represented by the `Begin`, `Process`, and `End` blocks of the function.</span></span> <span data-ttu-id="bf1b4-120">함수에서 이러한 블록을 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-120">You aren't required to use any of these blocks in your functions.</span></span>

> [!NOTE]
> <span data-ttu-id="bf1b4-121">이러한 블록은 특성을 사용 하지 않는 함수에도 사용할 수 있습니다 `CmdletBinding` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-121">These blocks are also available to functions that don't use the `CmdletBinding` attribute.</span></span>

#### <a name="begin"></a><span data-ttu-id="bf1b4-122">시작</span><span class="sxs-lookup"><span data-stu-id="bf1b4-122">Begin</span></span>

<span data-ttu-id="bf1b4-123">이 블록은 함수에 대 한 선택적 일회성 전처리를 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-123">This block is used to provide optional one-time preprocessing for the function.</span></span>
<span data-ttu-id="bf1b4-124">PowerShell 런타임은 파이프라인에서 함수의 각 인스턴스에 대해 한 번씩이 블록의 코드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-124">The PowerShell runtime uses the code in this block once for each instance of the function in the pipeline.</span></span>

#### <a name="process"></a><span data-ttu-id="bf1b4-125">프로세스</span><span class="sxs-lookup"><span data-stu-id="bf1b4-125">Process</span></span>

<span data-ttu-id="bf1b4-126">이 블록은 함수에 대 한 레코드 레코드 처리를 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-126">This block is used to provide record-by-record processing for the function.</span></span> <span data-ttu-id="bf1b4-127">`Process`다른 블록을 정의 하지 않고 블록을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-127">You can use a `Process` block without defining the other blocks.</span></span> <span data-ttu-id="bf1b4-128">`Process`블록 실행 수는 함수를 사용 하는 방법 및 함수가 수신 하는 입력에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-128">The number of `Process` block executions depends on how you use the function and what input the function receives.</span></span>

<span data-ttu-id="bf1b4-129">자동 변수 `$_` 이거나 `$PSItem` 블록에서 사용할 파이프라인의 현재 개체를 포함 합니다 `Process` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-129">The automatic variable `$_` or `$PSItem` contains the current object in the pipeline for use in the `Process` block.</span></span> <span data-ttu-id="bf1b4-130">`$input`자동 변수에는 함수와 스크립트 블록에만 사용할 수 있는 열거자가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-130">The `$input` automatic variable contains an enumerator that's only available to functions and script blocks.</span></span>
<span data-ttu-id="bf1b4-131">자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-131">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md).</span></span>

- <span data-ttu-id="bf1b4-132">함수를 시작 부분 또는 파이프라인 외부에서 호출 하면 `Process` 블록을 한 번 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-132">Calling the function at the beginning, or outside of a pipeline, executes the `Process` block once.</span></span>
- <span data-ttu-id="bf1b4-133">파이프라인 내에서 블록은 `Process` 함수에 도달 하는 각 입력 개체에 대해 한 번씩 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-133">Within a pipeline, the `Process` block executes once for each input object that reaches the function.</span></span>
- <span data-ttu-id="bf1b4-134">함수에 도달 하는 파이프라인 입력이 비어 있으면 `Process` 블록이 실행 **되지 않습니다** .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-134">If the pipeline input that reaches the function is empty, the `Process` block **does not** execute.</span></span>
  - <span data-ttu-id="bf1b4-135">`Begin`및 `End` 블록은 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-135">The `Begin` and `End` blocks still execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf1b4-136">파이프라인 입력을 허용 하도록 함수 매개 변수를 설정 하 고 `Process` 블록이 정의 되지 않은 경우 레코드에의 한 레코드 처리가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-136">If a function parameter is set to accept pipeline input, and a `Process` block isn't defined, record-by-record processing will fail.</span></span> <span data-ttu-id="bf1b4-137">이 경우 함수는 입력에 관계 없이 한 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-137">In this case, your function will only execute once, regardless of the input.</span></span>

#### <a name="end"></a><span data-ttu-id="bf1b4-138">끝</span><span class="sxs-lookup"><span data-stu-id="bf1b4-138">End</span></span>

<span data-ttu-id="bf1b4-139">이 블록은 함수에 대 한 선택적인 일회성 사후 처리를 제공 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-139">This block is used to provide optional one-time post-processing for the function.</span></span>

<span data-ttu-id="bf1b4-140">다음 예에서는 일회성 `Begin` 전처리를 위한 블록, `Process` 다중 레코드 처리를 위한 블록 및 `End` 일회성 사후 처리를 위한 블록을 포함 하는 함수의 개요를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-140">The following example shows the outline of a function that contains a `Begin` block for one-time preprocessing, a `Process` block for multiple record processing, and an `End` block for one-time post-processing.</span></span>

```powershell
Function Test-ScriptCmdlet
{
[CmdletBinding(SupportsShouldProcess=$True)]
    Param ($Parameter1)
    Begin{}
    Process{}
    End{}
}
```

> [!NOTE]
> <span data-ttu-id="bf1b4-141">또는 블록 중 하나를 사용 `Begin` `End` 하려면 세 개의 블록을 모두 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-141">Using either a `Begin` or `End` block requires that you define all three blocks.</span></span> <span data-ttu-id="bf1b4-142">세 블록을 모두 사용 하는 경우 모든 PowerShell 코드는 블록 중 하나에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-142">When using all three blocks, all PowerShell code must be inside one of the blocks.</span></span>

### <a name="confirmation-methods"></a><span data-ttu-id="bf1b4-143">확인 방법</span><span class="sxs-lookup"><span data-stu-id="bf1b4-143">Confirmation methods</span></span>

#### <a name="shouldprocess"></a><span data-ttu-id="bf1b4-144">ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="bf1b4-144">ShouldProcess</span></span>

<span data-ttu-id="bf1b4-145">이 메서드는 함수에서 시스템을 변경 하는 작업을 수행 하기 전에 사용자의 확인을 요청 하기 위해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-145">This method is called to request confirmation from the user before the function performs an action that would change the system.</span></span> <span data-ttu-id="bf1b4-146">함수는 메서드에서 반환 된 부울 값을 기반으로 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-146">The function can continue based on the Boolean value returned by the method.</span></span> <span data-ttu-id="bf1b4-147">이 메서드는 함수 블록 내 에서만 호출할 수 있습니다 `Process{}` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-147">This method can only be called only from within the `Process{}` block of the function.</span></span> <span data-ttu-id="bf1b4-148">`CmdletBinding`또한 특성은 `ShouldProcess` 앞의 예제와 같이 함수에서 지원 되는를 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-148">The `CmdletBinding` attribute must also declare that the function supports `ShouldProcess` (as shown in the previous example).</span></span>

<span data-ttu-id="bf1b4-149">이 메서드에 대 한 자세한 내용은 [system.object](/dotnet/api/system.management.automation.cmdlet.shouldprocess)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-149">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess).</span></span>

<span data-ttu-id="bf1b4-150">확인을 요청 하는 방법에 대 한 자세한 내용은 [확인 요청](/powershell/scripting/developer/cmdlet/requesting-confirmation)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-150">For more information about how to request confirmation, see [Requesting Confirmation](/powershell/scripting/developer/cmdlet/requesting-confirmation).</span></span>

#### <a name="shouldcontinue"></a><span data-ttu-id="bf1b4-151">ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="bf1b4-151">ShouldContinue</span></span>

<span data-ttu-id="bf1b4-152">이 메서드는 두 번째 확인 메시지를 요청 하기 위해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-152">This method is called to request a second confirmation message.</span></span> <span data-ttu-id="bf1b4-153">메서드가 반환 될 때 호출 되어야 합니다 `ShouldProcess` `$true` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-153">It should be called when the `ShouldProcess` method returns `$true`.</span></span> <span data-ttu-id="bf1b4-154">이 메서드에 대 한 자세한 내용은 [system.object](/dotnet/api/system.management.automation.cmdlet.shouldcontinue)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-154">For more information about this method, see [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span></span>

### <a name="error-methods"></a><span data-ttu-id="bf1b4-155">오류 메서드</span><span class="sxs-lookup"><span data-stu-id="bf1b4-155">Error methods</span></span>

<span data-ttu-id="bf1b4-156">오류가 발생 하는 경우 함수는 두 가지 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-156">Functions can call two different methods when errors occur.</span></span> <span data-ttu-id="bf1b4-157">종료 되지 않는 오류가 발생 하면 함수는 `WriteError` 메서드 섹션에서 설명 하는 메서드를 호출 해야 합니다 `Write` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-157">When a non-terminating error occurs, the function should call the `WriteError` method, which is described in the `Write` methods section.</span></span> <span data-ttu-id="bf1b4-158">종료 오류가 발생 하 고 함수를 계속할 수 없는 경우 메서드를 호출 해야 합니다 `ThrowTerminatingError` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-158">When a terminating error occurs and the function can't continue, it should call the `ThrowTerminatingError` method.</span></span> <span data-ttu-id="bf1b4-159">종료 오류에 대 한 문을 사용 하 여 오류 `Throw` 를 종료 하 고 [오류를 기록할](xref:Microsoft.PowerShell.Utility.Write-Error) 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-159">You can also use the `Throw` statement for terminating errors and the [Write-Error](xref:Microsoft.PowerShell.Utility.Write-Error) cmdlet for non-terminating errors.</span></span>

<span data-ttu-id="bf1b4-160">자세한 내용은 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror)을 (를) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-160">For more information, see [System.Management.Automation.Cmdlet.ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror).</span></span>

### <a name="write-methods"></a><span data-ttu-id="bf1b4-161">Write 메서드</span><span class="sxs-lookup"><span data-stu-id="bf1b4-161">Write methods</span></span>

<span data-ttu-id="bf1b4-162">함수는 다음 메서드를 호출 하 여 다른 유형의 출력을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-162">A function can call the following methods to return different types of output.</span></span>
<span data-ttu-id="bf1b4-163">모든 출력이 파이프라인의 다음 명령으로 이동 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-163">Notice that not all the output goes to the next command in the pipeline.</span></span> <span data-ttu-id="bf1b4-164">과 같은 다양 한 cmdlet을 사용할 수도 있습니다 `Write` `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-164">You can also use the various `Write` cmdlets, such as `Write-Error`.</span></span>

#### <a name="writecommanddetail"></a><span data-ttu-id="bf1b4-165">WriteCommandDetail</span><span class="sxs-lookup"><span data-stu-id="bf1b4-165">WriteCommandDetail</span></span>

<span data-ttu-id="bf1b4-166">메서드에 대 한 자세한 내용은 `WriteCommandDetails` [WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-166">For information about the `WriteCommandDetails` method, see [System.Management.Automation.Cmdlet.WriteCommandDetail](/dotnet/api/system.management.automation.cmdlet.writecommanddetail).</span></span>

#### <a name="writedebug"></a><span data-ttu-id="bf1b4-167">WriteDebug</span><span class="sxs-lookup"><span data-stu-id="bf1b4-167">WriteDebug</span></span>

<span data-ttu-id="bf1b4-168">함수 문제를 해결 하는 데 사용할 수 있는 정보를 제공 하려면 함수에서 메서드를 호출 하도록 합니다 `WriteDebug` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-168">To provide information that can be used to troubleshoot a function, make the function call the `WriteDebug` method.</span></span> <span data-ttu-id="bf1b4-169">`WriteDebug`메서드는 디버그 메시지를 사용자에 게 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-169">The `WriteDebug` method displays debug messages to the user.</span></span> <span data-ttu-id="bf1b4-170">자세한 내용은 System.web. n a m a [debug](/dotnet/api/system.management.automation.cmdlet.writedebug)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-170">For more information, see [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/system.management.automation.cmdlet.writedebug).</span></span>

#### <a name="writeerror"></a><span data-ttu-id="bf1b4-171">WriteError</span><span class="sxs-lookup"><span data-stu-id="bf1b4-171">WriteError</span></span>

<span data-ttu-id="bf1b4-172">종료 되지 않는 오류가 발생 하 고 함수가 레코드를 계속 처리 하도록 디자인 된 경우 함수는이 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-172">Functions should call this method when non-terminating errors occur and the function is designed to continue processing records.</span></span> <span data-ttu-id="bf1b4-173">자세한 내용은 [WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror)을 (를) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-173">For more information, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/system.management.automation.cmdlet.writeerror).</span></span>

> [!NOTE]
> <span data-ttu-id="bf1b4-174">종료 오류가 발생 하는 경우 함수는 [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-174">If a terminating error occurs, the function should call the [ThrowTerminatingError](/dotnet/api/system.management.automation.cmdlet.throwterminatingerror) method.</span></span>

#### <a name="writeobject"></a><span data-ttu-id="bf1b4-175">WriteObject</span><span class="sxs-lookup"><span data-stu-id="bf1b4-175">WriteObject</span></span>

<span data-ttu-id="bf1b4-176">`WriteObject`메서드를 사용 하 여 함수는 파이프라인의 다음 명령으로 개체를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-176">The `WriteObject` method allows the function to send an object to the next command in the pipeline.</span></span> <span data-ttu-id="bf1b4-177">대부분의 경우 `WriteObject` 는 함수가 데이터를 반환할 때 사용 하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-177">In most cases, `WriteObject` is the method to use when the function returns data.</span></span> <span data-ttu-id="bf1b4-178">자세한 내용은 [PSCmdlet. WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-178">For more information, see [System.Management.Automation.PSCmdlet.WriteObject](/dotnet/api/system.management.automation.cmdlet.writeobject).</span></span>

#### <a name="writeprogress"></a><span data-ttu-id="bf1b4-179">WriteProgress</span><span class="sxs-lookup"><span data-stu-id="bf1b4-179">WriteProgress</span></span>

<span data-ttu-id="bf1b4-180">작업을 완료 하는 데 오랜 시간이 걸리는 함수에서이 메서드를 사용 하면 `WriteProgress` 진행률 정보가 표시 되도록 함수에서 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-180">For functions with actions that take a long time to complete, this method allows the function to call the `WriteProgress` method so that progress information is displayed.</span></span> <span data-ttu-id="bf1b4-181">예를 들어 완료 된 비율을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-181">For example, you can display the percent completed.</span></span>
<span data-ttu-id="bf1b4-182">자세한 내용은 [PSCmdlet 진행률](/dotnet/api/system.management.automation.cmdlet.writeprogress)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-182">For more information, see [System.Management.Automation.PSCmdlet.WriteProgress](/dotnet/api/system.management.automation.cmdlet.writeprogress).</span></span>

#### <a name="writeverbose"></a><span data-ttu-id="bf1b4-183">WriteVerbose</span><span class="sxs-lookup"><span data-stu-id="bf1b4-183">WriteVerbose</span></span>

<span data-ttu-id="bf1b4-184">함수에서 수행 하는 작업에 대 한 자세한 정보를 제공 하려면 함수에서 메서드를 호출 하 여 `WriteVerbose` 사용자에 게 자세한 정보 메시지를 표시 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-184">To provide detailed information about what the function is doing, make the function call the `WriteVerbose` method to display verbose messages to the user.</span></span> <span data-ttu-id="bf1b4-185">기본적으로 자세한 정보 표시 메시지는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-185">By default, verbose messages aren't displayed.</span></span> <span data-ttu-id="bf1b4-186">자세한 내용은 [PSCmdlet](/dotnet/api/system.management.automation.cmdlet.writeverbose)을 (를) 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-186">For more information, see [System.Management.Automation.PSCmdlet.WriteVerbose](/dotnet/api/system.management.automation.cmdlet.writeverbose).</span></span>

#### <a name="writewarning"></a><span data-ttu-id="bf1b4-187">WriteWarning</span><span class="sxs-lookup"><span data-stu-id="bf1b4-187">WriteWarning</span></span>

<span data-ttu-id="bf1b4-188">예기치 않은 결과를 발생 시킬 수 있는 조건에 대 한 정보를 제공 하기 위해 함수가 WriteWarning 메서드를 호출 하 여 사용자에 게 경고 메시지를 표시 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-188">To provide information about conditions that may cause unexpected results, make the function call the WriteWarning method to display warning messages to the user.</span></span> <span data-ttu-id="bf1b4-189">기본적으로 경고 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-189">By default, warning messages are displayed.</span></span> <span data-ttu-id="bf1b4-190">자세한 내용은 [PSCmdlet 경고](/dotnet/api/system.management.automation.cmdlet.writewarning)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-190">For more information, see [System.Management.Automation.PSCmdlet.WriteWarning](/dotnet/api/system.management.automation.cmdlet.writewarning).</span></span>

> [!NOTE]
> <span data-ttu-id="bf1b4-191">`$WarningPreference` `Verbose` 및 명령줄 옵션을 사용 하 여 또는 변수를 구성 하 여 경고 메시지를 표시할 수도 있습니다 `Debug` .</span><span class="sxs-lookup"><span data-stu-id="bf1b4-191">You can also display warning messages by configuring the `$WarningPreference` variable or by using the `Verbose` and `Debug` command-line options.</span></span> <span data-ttu-id="bf1b4-192">변수에 대 한 자세한 내용은 `$WarningPreference` [about_Preference_Variables](about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-192">for more information about the `$WarningPreference` variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="other-methods-and-properties"></a><span data-ttu-id="bf1b4-193">기타 메서드 및 속성</span><span class="sxs-lookup"><span data-stu-id="bf1b4-193">Other methods and properties</span></span>

<span data-ttu-id="bf1b4-194">변수를 통해 액세스할 수 있는 다른 메서드 및 속성에 대 한 자세한 내용은 `$PSCmdlet` [PSCmdlet](/dotnet/api/system.management.automation.pscmdlet)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-194">For information about the other methods and properties that can be accessed through the `$PSCmdlet` variable, see [System.Management.Automation.PSCmdlet](/dotnet/api/system.management.automation.pscmdlet).</span></span>

<span data-ttu-id="bf1b4-195">예를 들어 [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) 속성을 사용 하 여 사용 중인 매개 변수 집합을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-195">For example, the [ParameterSetName](/dotnet/api/system.management.automation.pscmdlet.parametersetname) property allows you to see the parameter set that is being used.</span></span> <span data-ttu-id="bf1b4-196">매개 변수 집합을 사용 하면 함수를 실행할 때 지정 된 매개 변수를 기반으로 다양 한 작업을 수행 하는 함수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf1b4-196">Parameter sets allow you to create a function that performs different tasks based on the parameters that are specified when the function is run.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf1b4-197">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf1b4-197">See also</span></span>

[<span data-ttu-id="bf1b4-198">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="bf1b4-198">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="bf1b4-199">about_Functions</span><span class="sxs-lookup"><span data-stu-id="bf1b4-199">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="bf1b4-200">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="bf1b4-200">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="bf1b4-201">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="bf1b4-201">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="bf1b4-202">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="bf1b4-202">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="bf1b4-203">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="bf1b4-203">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="bf1b4-204">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="bf1b4-204">about_Preference_Variables</span></span>](about_Preference_Variables.md)
