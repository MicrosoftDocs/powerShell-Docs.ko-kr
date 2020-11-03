---
description: PowerShell에 대 한 상태 정보를 저장 하는 변수에 대해 설명 합니다. 이러한 변수는 PowerShell에서 만들고 유지 관리 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: d56e844bd10dfffabb1d2cfd75bcfe113724a334
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93222818"
---
# <a name="about-automatic-variables"></a><span data-ttu-id="15ddb-105">자동 변수 정보</span><span class="sxs-lookup"><span data-stu-id="15ddb-105">About Automatic Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="15ddb-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="15ddb-106">Short description</span></span>

<span data-ttu-id="15ddb-107">PowerShell에 대 한 상태 정보를 저장 하는 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-107">Describes variables that store state information for PowerShell.</span></span> <span data-ttu-id="15ddb-108">이러한 변수는 PowerShell에서 만들고 유지 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-108">These variables are created and maintained by PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="15ddb-109">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-109">Long description</span></span>

<span data-ttu-id="15ddb-110">개념적으로 이러한 변수는 읽기 전용으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-110">Conceptually, these variables are considered to be read-only.</span></span> <span data-ttu-id="15ddb-111">이전 버전과의 호환성을 위해 쓸 수 **있는** 경우에도 쓸 수 **없습니다** .</span><span class="sxs-lookup"><span data-stu-id="15ddb-111">Even though they **can** be written to, for backward compatibility they **should not** be written to.</span></span>

<span data-ttu-id="15ddb-112">PowerShell의 자동 변수 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-112">Here is a list of the automatic variables in PowerShell:</span></span>

### <a name=""></a>$$

<span data-ttu-id="15ddb-113">세션에서 받은 마지막 줄의 마지막 토큰을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-113">Contains the last token in the last line received by the session.</span></span>

### <a name=""></a><span data-ttu-id="15ddb-114">$?</span><span class="sxs-lookup"><span data-stu-id="15ddb-114">$?</span></span>

<span data-ttu-id="15ddb-115">마지막 명령의 실행 상태를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-115">Contains the execution status of the last command.</span></span> <span data-ttu-id="15ddb-116">마지막 명령이 성공한 경우 **True** 를 포함 하 고 실패 하면 **False** 를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-116">It contains **True** if the last command succeeded and **False** if it failed.</span></span>

<span data-ttu-id="15ddb-117">파이프라인의 여러 단계에서 실행 되는 cmdlet 및 고급 함수 (예: 및 블록 둘 다)의 경우 `process` `end` 언제 든 지 또는를 호출 하는 것은 및와 같이 모두 `this.WriteError()` `$PSCmdlet.WriteError()` `$?` **False** 로 설정 됩니다 `this.ThrowTerminatingError()` `$PSCmdlet.ThrowTerminatingError()` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-117">For cmdlets and advanced functions that are run at multiple stages in a pipeline, for example in both `process` and `end` blocks, calling `this.WriteError()` or `$PSCmdlet.WriteError()` respectively at any point will set `$?` to **False** , as will `this.ThrowTerminatingError()` and `$PSCmdlet.ThrowTerminatingError()`.</span></span>

<span data-ttu-id="15ddb-118">`Write-Error`Cmdlet은 `$?` 실행 후에 항상 **false** 로 설정 되지만 `$?` 함수를 호출 하는 함수에 대해 **false** 로 설정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-118">The `Write-Error` cmdlet always sets `$?` to **False** immediately after it is executed, but will not set `$?` to **False** for a function calling it:</span></span>

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

<span data-ttu-id="15ddb-119">후자의 경우에 `$PSCmdlet.WriteError()` 는 대신를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-119">For the latter purpose, `$PSCmdlet.WriteError()` should be used instead.</span></span>

<span data-ttu-id="15ddb-120">네이티브 명령 (실행 파일)의 경우가 0 이면이 `$?` **True** 로 설정 되 `$LASTEXITCODE` 고,가 다른 값 이면 **False** 로 설정 됩니다 `$LASTEXITCODE` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-120">For native commands (executables), `$?` is set to **True** when `$LASTEXITCODE` is 0, and set to **False** when `$LASTEXITCODE` is any other value.</span></span>

> [!NOTE]
> <span data-ttu-id="15ddb-121">괄호 안에 문을 포함 하는 PowerShell 7 까지는 `(...)` 부분식 구문 `$(...)` 또는 배열 식이 `@(...)` 항상 true로 다시 설정 `$?` 되므로가 **True** `(Write-Error)` `$?` **true** 로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-121">Until PowerShell 7, containing a statement within parentheses `(...)`, subexpression syntax `$(...)` or array expression `@(...)` always reset `$?` to **True** , so that `(Write-Error)` shows `$?` as **True**.</span></span>
> <span data-ttu-id="15ddb-122">이는 PowerShell 7에서 변경 되었으므로 `$?` 항상 이러한 식에서 실행 된 마지막 명령의 실제 성공을 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-122">This has been changed in PowerShell 7, so that `$?` will always reflect the actual success of the last command run in these expressions.</span></span>

### <a name=""></a>$^

<span data-ttu-id="15ddb-123">세션에서 받은 마지막 줄의 첫 번째 토큰을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-123">Contains the first token in the last line received by the session.</span></span>

### <a name="_"></a><span data-ttu-id="15ddb-124">$_</span><span class="sxs-lookup"><span data-stu-id="15ddb-124">$_</span></span>

<span data-ttu-id="15ddb-125">`$PSItem`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-125">Same as `$PSItem`.</span></span> <span data-ttu-id="15ddb-126">파이프라인 개체의 현재 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-126">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="15ddb-127">파이프라인의 모든 개체 또는 선택한 개체에 대해 작업을 수행 하는 명령에서이 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-127">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="args"></a><span data-ttu-id="15ddb-128">$args</span><span class="sxs-lookup"><span data-stu-id="15ddb-128">$args</span></span>

<span data-ttu-id="15ddb-129">함수, 스크립트 또는 스크립트 블록에 전달 되는 선언 되지 않은 매개 변수에 대 한 값 배열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-129">Contains an array of values for undeclared parameters that are passed to a function, script, or script block.</span></span> <span data-ttu-id="15ddb-130">함수를 만들 때 키워드를 사용 `param` 하거나 함수 이름 뒤에 괄호 안에 쉼표로 구분 된 매개 변수 목록을 추가 하 여 매개 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-130">When you create a function, you can declare the parameters by using the `param` keyword or by adding a comma-separated list of parameters in parentheses after the function name.</span></span>

<span data-ttu-id="15ddb-131">이벤트 동작에서 `$Args` 변수는 처리 중인 이벤트의 이벤트 인수를 나타내는 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-131">In an event action, the `$Args` variable contains objects that represent the event arguments of the event that is being processed.</span></span> <span data-ttu-id="15ddb-132">이 변수는 `Action` 이벤트 등록 명령의 블록 내 에서만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-132">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="15ddb-133">이 변수의 값은를 반환 하는 **PSEventArgs** 개체의 **sourceargs** 속성 에서도 찾을 수 있습니다 `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-133">The value of this variable can also be found in the **SourceArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="consolefilename"></a><span data-ttu-id="15ddb-134">$ConsoleFileName</span><span class="sxs-lookup"><span data-stu-id="15ddb-134">$ConsoleFileName</span></span>

<span data-ttu-id="15ddb-135">세션에서 가장 최근에 사용 된 콘솔 파일 ()의 경로를 포함 `.psc1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-135">Contains the path of the console file (`.psc1`) that was most recently used in the session.</span></span> <span data-ttu-id="15ddb-136">이 변수는 **PSConsoleFile** 매개 변수를 사용 하 여 PowerShell을 시작 하거나 cmdlet을 사용 하 여 `Export-Console` 스냅인 이름을 콘솔 파일로 내보내는 경우에 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-136">This variable is populated when you start PowerShell with the **PSConsoleFile** parameter or when you use the `Export-Console` cmdlet to export snap-in names to a console file.</span></span>

<span data-ttu-id="15ddb-137">`Export-Console`매개 변수 없이 cmdlet을 사용 하는 경우 세션에서 가장 최근에 사용 된 콘솔 파일을 자동으로 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-137">When you use the `Export-Console` cmdlet without parameters, it automatically updates the console file that was most recently used in the session.</span></span> <span data-ttu-id="15ddb-138">이 자동 변수를 사용 하 여 업데이트 되는 파일을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-138">You can use this automatic variable to determine which file will be updated.</span></span>

### <a name="error"></a><span data-ttu-id="15ddb-139">$Error</span><span class="sxs-lookup"><span data-stu-id="15ddb-139">$Error</span></span>

<span data-ttu-id="15ddb-140">가장 최근의 오류를 나타내는 오류 개체의 배열을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-140">Contains an array of error objects that represent the most recent errors.</span></span>
<span data-ttu-id="15ddb-141">가장 최근의 오류는 배열의 첫 번째 오류 개체입니다 `$Error[0]` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-141">The most recent error is the first error object in the array `$Error[0]`.</span></span>

<span data-ttu-id="15ddb-142">오류가 배열에 추가 되지 않도록 하려면 `$Error` **Ignore** 값에 **erroraction** 일반 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-142">To prevent an error from being added to the `$Error` array, use the **ErrorAction** common parameter with a value of **Ignore**.</span></span> <span data-ttu-id="15ddb-143">자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-143">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="event"></a><span data-ttu-id="15ddb-144">$Event</span><span class="sxs-lookup"><span data-stu-id="15ddb-144">$Event</span></span>

<span data-ttu-id="15ddb-145">처리 중인 이벤트를 나타내는 **PSEventArgs** 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-145">Contains a **PSEventArgs** object that represents the event that is being processed.</span></span> <span data-ttu-id="15ddb-146">이 변수는 `Action` 와 같은 이벤트 등록 명령의 블록 내 에서만 채워집니다 `Register-ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-146">This variable is populated only within the `Action` block of an event registration command, such as `Register-ObjectEvent`.</span></span> <span data-ttu-id="15ddb-147">이 변수의 값은 cmdlet이 반환 하는 것과 동일한 개체입니다 `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-147">The value of this variable is the same object that the `Get-Event` cmdlet returns.</span></span> <span data-ttu-id="15ddb-148">따라서 `Event` 와 같은 변수의 속성을 `$Event.TimeGenerated` 스크립트 블록에서 사용할 수 있습니다 `Action` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-148">Therefore, you can use the properties of the `Event` variable, such as `$Event.TimeGenerated`, in an `Action` script block.</span></span>

### <a name="eventargs"></a><span data-ttu-id="15ddb-149">$EventArgs</span><span class="sxs-lookup"><span data-stu-id="15ddb-149">$EventArgs</span></span>

<span data-ttu-id="15ddb-150">처리 중인 이벤트의 **EventArgs** 에서 파생 되는 첫 번째 이벤트 인수를 나타내는 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-150">Contains an object that represents the first event argument that derives from **EventArgs** of the event that is being processed.</span></span> <span data-ttu-id="15ddb-151">이 변수는 `Action` 이벤트 등록 명령의 블록 내 에서만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-151">This variable is populated only within the `Action` block of an event registration command.</span></span>
<span data-ttu-id="15ddb-152">이 변수의 값은를 반환 하는 **PSEventArgs** 개체의 **sourceeventargs** 속성 에서도 찾을 수 있습니다 `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-152">The value of this variable can also be found in the **SourceEventArgs** property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="eventsubscriber"></a><span data-ttu-id="15ddb-153">$EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="15ddb-153">$EventSubscriber</span></span>

<span data-ttu-id="15ddb-154">처리 중인 이벤트의 이벤트 구독자를 나타내는 **PSEventSubscriber** 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-154">Contains a **PSEventSubscriber** object that represents the event subscriber of the event that is being processed.</span></span> <span data-ttu-id="15ddb-155">이 변수는 `Action` 이벤트 등록 명령의 블록 내 에서만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-155">This variable is populated only within the `Action` block of an event registration command.</span></span> <span data-ttu-id="15ddb-156">이 변수의 값은 cmdlet이 반환 하는 것과 동일한 개체입니다 `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-156">The value of this variable is the same object that the `Get-EventSubscriber` cmdlet returns.</span></span>

### <a name="executioncontext"></a><span data-ttu-id="15ddb-157">$ExecutionContext</span><span class="sxs-lookup"><span data-stu-id="15ddb-157">$ExecutionContext</span></span>

<span data-ttu-id="15ddb-158">PowerShell 호스트의 실행 컨텍스트를 나타내는 **EngineIntrinsics** 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-158">Contains an **EngineIntrinsics** object that represents the execution context of the PowerShell host.</span></span> <span data-ttu-id="15ddb-159">이 변수를 사용 하 여 cmdlet에서 사용할 수 있는 실행 개체를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-159">You can use this variable to find the execution objects that are available to cmdlets.</span></span>

### <a name="false"></a><span data-ttu-id="15ddb-160">$false</span><span class="sxs-lookup"><span data-stu-id="15ddb-160">$false</span></span>

<span data-ttu-id="15ddb-161">**False** 를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-161">Contains **False**.</span></span> <span data-ttu-id="15ddb-162">"False" 문자열을 사용 하는 대신이 변수를 사용 하 여 명령 및 스크립트에서 **False** 를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-162">You can use this variable to represent **False** in commands and scripts instead of using the string "false".</span></span> <span data-ttu-id="15ddb-163">문자열은 비어 있지 않은 문자열이 나 0이 아닌 정수로 변환 되는 경우 **True** 로 해석 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-163">The string can be interpreted as **True** if it's converted to a non-empty string or to a non-zero integer.</span></span>

### <a name="foreach"></a><span data-ttu-id="15ddb-164">$foreach</span><span class="sxs-lookup"><span data-stu-id="15ddb-164">$foreach</span></span>

<span data-ttu-id="15ddb-165">[ForEach](about_ForEach.md) 루프의 결과 값이 아니라 열거자를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-165">Contains the enumerator (not the resulting values) of a [ForEach](about_ForEach.md) loop.</span></span> <span data-ttu-id="15ddb-166">`$ForEach`변수는 루프가 실행 되는 동안에만 존재 합니다. `ForEach` 루프가 완료 된 후에는 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-166">The `$ForEach` variable exists only while the `ForEach` loop is running; it's deleted after the loop is completed.</span></span>

<span data-ttu-id="15ddb-167">열거자는 루프 값을 검색 하 고 현재 루프 반복을 변경 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-167">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="15ddb-168">자세한 내용은 [열거자 사용](#using-enumerators)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-168">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="home"></a><span data-ttu-id="15ddb-169">$HOME</span><span class="sxs-lookup"><span data-stu-id="15ddb-169">$HOME</span></span>

<span data-ttu-id="15ddb-170">사용자의 홈 디렉터리에 대 한 전체 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-170">Contains the full path of the user's home directory.</span></span> <span data-ttu-id="15ddb-171">이 변수는 `"$env:homedrive$env:homepath"` 일반적으로 Windows 환경 변수에 해당 합니다 `C:\Users\<UserName>` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-171">This variable is the equivalent of the `"$env:homedrive$env:homepath"` Windows environment variables, typically `C:\Users\<UserName>`.</span></span>

### <a name="host"></a><span data-ttu-id="15ddb-172">$Host</span><span class="sxs-lookup"><span data-stu-id="15ddb-172">$Host</span></span>

<span data-ttu-id="15ddb-173">PowerShell에 대 한 현재 호스트 응용 프로그램을 나타내는 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-173">Contains an object that represents the current host application for PowerShell.</span></span> <span data-ttu-id="15ddb-174">이 변수를 사용 하 여 명령의 현재 호스트를 나타내거나 또는 등의 호스트 속성을 표시 하거나 변경할 수 있습니다 `$Host.version` `$Host.CurrentCulture` `$host.ui.rawui.setbackgroundcolor("Red")` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-174">You can use this variable to represent the current host in commands or to display or change the properties of the host, such as `$Host.version` or `$Host.CurrentCulture`, or `$host.ui.rawui.setbackgroundcolor("Red")`.</span></span>

### <a name="input"></a><span data-ttu-id="15ddb-175">$input</span><span class="sxs-lookup"><span data-stu-id="15ddb-175">$input</span></span>

<span data-ttu-id="15ddb-176">함수에 전달 되는 모든 입력을 열거 하는 열거자를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-176">Contains an enumerator that enumerates all input that is passed to a function.</span></span> <span data-ttu-id="15ddb-177">`$input`변수는 함수 및 스크립트 블록 (명명 되지 않은 함수) 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-177">The `$input` variable is available only to functions and script blocks (which are unnamed functions).</span></span>

- <span data-ttu-id="15ddb-178">`Begin`, 또는 블록이 없는 함수에서 `Process` `End` `$input` 변수는 함수에 대 한 모든 입력의 컬렉션을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-178">In a function without a `Begin`, `Process`, or `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

- <span data-ttu-id="15ddb-179">블록에서 `Begin` `$input` 변수에는 데이터가 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-179">In the `Begin` block, the `$input` variable contains no data.</span></span>

- <span data-ttu-id="15ddb-180">블록에서 `Process` `$input` 변수는 현재 파이프라인에 있는 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-180">In the `Process` block, the `$input` variable contains the object that is currently in the pipeline.</span></span>

- <span data-ttu-id="15ddb-181">블록에서 `End` `$input` 변수는 함수에 대 한 모든 입력의 컬렉션을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-181">In the `End` block, the `$input` variable enumerates the collection of all input to the function.</span></span>

  > [!NOTE]
  > <span data-ttu-id="15ddb-182">`$input`동일한 함수 또는 스크립트 블록의 프로세스 블록과 끝 블록 내에서 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-182">You cannot use the `$input` variable inside both the Process block and the End block in the same function or script block.</span></span>

<span data-ttu-id="15ddb-183">`$input`는 열거자 이므로 해당 속성에 액세스 하면 `$input` 더 이상 사용할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-183">Since `$input` is an enumerator, accessing any of it's properties causes `$input` to no longer be available.</span></span> <span data-ttu-id="15ddb-184">`$input`다른 변수에 저장 하 여 속성을 다시 사용할 수 있습니다 `$input` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-184">You can store `$input` in another variable to reuse the `$input` properties.</span></span>

<span data-ttu-id="15ddb-185">열거자는 루프 값을 검색 하 고 현재 루프 반복을 변경 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-185">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="15ddb-186">자세한 내용은 [열거자 사용](#using-enumerators)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-186">For more information, see [Using Enumerators](#using-enumerators).</span></span>


### <a name="lastexitcode"></a><span data-ttu-id="15ddb-187">$LastExitCode</span><span class="sxs-lookup"><span data-stu-id="15ddb-187">$LastExitCode</span></span>

<span data-ttu-id="15ddb-188">실행 된 마지막 Windows 기반 프로그램의 종료 코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-188">Contains the exit code of the last Windows-based program that was run.</span></span>

### <a name="matches"></a><span data-ttu-id="15ddb-189">$Matches</span><span class="sxs-lookup"><span data-stu-id="15ddb-189">$Matches</span></span>

<span data-ttu-id="15ddb-190">`Matches`변수는 및 연산자와 함께 작동 `-match` `-notmatch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-190">The `Matches` variable works with the `-match` and `-notmatch` operators.</span></span>
<span data-ttu-id="15ddb-191">스칼라 입력을 or 연산자에 제출 `-match` 하 `-notmatch` 고 하나는 일치 항목을 검색 하는 경우 부울 값을 반환 하 고 `$Matches` 일치 하는 모든 문자열 값의 해시 테이블을 사용 하 여 자동 변수를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-191">When you submit scalar input to the `-match` or `-notmatch` operator, and either one detects a match, they return a Boolean value and populate the `$Matches` automatic variable with a hash table of any string values that were matched.</span></span> <span data-ttu-id="15ddb-192">연산자를 사용 하 여 `$Matches` 정규식을 사용 하는 경우에는 해시 테이블을 캡처로 채울 수도 있습니다 `-match` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-192">The `$Matches` hash table can also be populated with captures when you use regular expressions with the `-match` operator.</span></span>

<span data-ttu-id="15ddb-193">연산자에 대 한 자세한 내용은 `-match` [about_Comparison_Operators](about_comparison_operators.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-193">For more information about the `-match` operator, see [about_Comparison_Operators](about_comparison_operators.md).</span></span> <span data-ttu-id="15ddb-194">정규식에 대 한 자세한 내용은 [about_Regular_Expressions](about_Regular_Expressions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-194">For more information on regular expressions, see [about_Regular_Expressions](about_Regular_Expressions.md).</span></span>

### <a name="myinvocation"></a><span data-ttu-id="15ddb-195">$MyInvocation</span><span class="sxs-lookup"><span data-stu-id="15ddb-195">$MyInvocation</span></span>

<span data-ttu-id="15ddb-196">현재 명령에 대 한 정보 (예: 이름, 매개 변수, 매개 변수 값) 및 명령이 시작, 호출 또는 호출 된 방법에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-196">Contains information about the current command, such as the name, parameters, parameter values, and information about how the command was started, called, or invoked, such as the name of the script that called the current command.</span></span>

<span data-ttu-id="15ddb-197">`$MyInvocation` 는 스크립트, 함수 및 스크립트 블록에 대해서만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-197">`$MyInvocation` is populated only for scripts, function, and script blocks.</span></span> <span data-ttu-id="15ddb-198">현재 스크립트에서 반환 하는 정보 **System.Management.Automation.InvocationInfo** `$MyInvocation` (예: 스크립트의 경로 및 파일 이름 ( `$MyInvocation.MyCommand.Path` ) 또는 함수 이름 ( `$MyInvocation.MyCommand.Name` ))를 사용 하 여 현재 명령을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-198">You can use the information in the **System.Management.Automation.InvocationInfo** object that `$MyInvocation` returns in the current script, such as the path and file name of the script (`$MyInvocation.MyCommand.Path`) or the name of a function (`$MyInvocation.MyCommand.Name`) to identify the current command.</span></span> <span data-ttu-id="15ddb-199">이는 현재 스크립트의 이름을 찾는 데 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-199">This is particularly useful for finding the name of the current script.</span></span>

<span data-ttu-id="15ddb-200">PowerShell 3.0부터에는 `MyInvocation` 다음과 같은 새 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-200">Beginning in PowerShell 3.0, `MyInvocation` has the following new properties.</span></span>

| <span data-ttu-id="15ddb-201">속성</span><span class="sxs-lookup"><span data-stu-id="15ddb-201">Property</span></span>      | <span data-ttu-id="15ddb-202">Description</span><span class="sxs-lookup"><span data-stu-id="15ddb-202">Description</span></span>                                         |
| ------------- | --------------------------------------------------- |
| <span data-ttu-id="15ddb-203">**PSScriptRoot**</span><span class="sxs-lookup"><span data-stu-id="15ddb-203">**PSScriptRoot**</span></span>  | <span data-ttu-id="15ddb-204">호출 된 스크립트에 대 한 전체 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-204">Contains the full path to the script that invoked</span></span>   |
|               | <span data-ttu-id="15ddb-205">현재 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-205">the current command.</span></span> <span data-ttu-id="15ddb-206">이 속성의 값은입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-206">The value of this property is</span></span>  |
|               | <span data-ttu-id="15ddb-207">호출자가 스크립트인 경우에만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-207">populated only when the caller is a script.</span></span>         |
| <span data-ttu-id="15ddb-208">**PSCommandPath**</span><span class="sxs-lookup"><span data-stu-id="15ddb-208">**PSCommandPath**</span></span> | <span data-ttu-id="15ddb-209">스크립트의 전체 경로 및 파일 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-209">Contains the full path and file name of the script</span></span>  |
|               | <span data-ttu-id="15ddb-210">현재 명령을 호출한입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-210">that invoked the current command.</span></span> <span data-ttu-id="15ddb-211">이의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-211">The value of this</span></span> |
|               | <span data-ttu-id="15ddb-212">호출자가 인 경우에만 속성이 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-212">property is populated only when the caller is a</span></span>     |
|               | <span data-ttu-id="15ddb-213">스크립트를 제출하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-213">script.</span></span>                                             |

<span data-ttu-id="15ddb-214">`$PSScriptRoot`및 `$PSCommandPath` 자동 변수와 달리 자동 변수의 **Psscriptroot** 및 **psscriptroot** 속성은 `$MyInvocation` 현재 스크립트가 아니라 호출자 또는 호출 스크립트에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-214">Unlike the `$PSScriptRoot` and `$PSCommandPath` automatic variables, the **PSScriptRoot** and **PSCommandPath** properties of the `$MyInvocation` automatic variable contain information about the invoker or calling script, not the current script.</span></span>

### <a name="nestedpromptlevel"></a><span data-ttu-id="15ddb-215">$NestedPromptLevel</span><span class="sxs-lookup"><span data-stu-id="15ddb-215">$NestedPromptLevel</span></span>

<span data-ttu-id="15ddb-216">현재 프롬프트 수준을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-216">Contains the current prompt level.</span></span> <span data-ttu-id="15ddb-217">값 0은 원래 프롬프트 수준을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-217">A value of 0 indicates the original prompt level.</span></span> <span data-ttu-id="15ddb-218">중첩 된 수준을 입력 하면 값이 증가 하 고 종료 될 때 감소 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-218">The value is incremented when you enter a nested level and decremented when you exit it.</span></span>

<span data-ttu-id="15ddb-219">예를 들어, 메서드를 사용할 때 PowerShell에서 중첩 된 명령 프롬프트를 표시 합니다 `$Host.EnterNestedPrompt` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-219">For example, PowerShell presents a nested command prompt when you use the `$Host.EnterNestedPrompt` method.</span></span> <span data-ttu-id="15ddb-220">Powershell은 PowerShell 디버거의 중단점에 도달 하는 경우에도 중첩 된 명령 프롬프트를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-220">PowerShell also presents a nested command prompt when you reach a breakpoint in the PowerShell debugger.</span></span>

<span data-ttu-id="15ddb-221">중첩 된 프롬프트를 입력 하면 PowerShell에서 현재 명령을 일시 중지 하 고, 실행 컨텍스트를 저장 하 고, 변수 값을 증가 시킵니다 `$NestedPromptLevel` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-221">When you enter a nested prompt, PowerShell pauses the current command, saves the execution context, and increments the value of the `$NestedPromptLevel` variable.</span></span> <span data-ttu-id="15ddb-222">추가 중첩 된 명령 프롬프트 (최대 128 수준)를 만들거나 원래 명령 프롬프트로 돌아가려면 명령을 완료 하거나를 입력 `exit` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-222">To create additional nested command prompts (up to 128 levels) or to return to the original command prompt, complete the command, or type `exit`.</span></span>

<span data-ttu-id="15ddb-223">`$NestedPromptLevel`변수를 사용 하면 프롬프트 수준을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-223">The `$NestedPromptLevel` variable helps you track the prompt level.</span></span> <span data-ttu-id="15ddb-224">이 값을 포함 하는 대체 PowerShell 명령 프롬프트를 만들어 항상 표시 되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-224">You can create an alternative PowerShell command prompt that includes this value so that it's always visible.</span></span>

### <a name="null"></a><span data-ttu-id="15ddb-225">$null</span><span class="sxs-lookup"><span data-stu-id="15ddb-225">$null</span></span>

<span data-ttu-id="15ddb-226">`$null`**null** 또는 빈 값을 포함 하는 자동 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-226">`$null` is an automatic variable that contains a **null** or empty value.</span></span> <span data-ttu-id="15ddb-227">이 변수를 사용 하 여 명령 및 스크립트에 없거나 정의 되지 않은 값을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-227">You can use this variable to represent an absent or undefined value in commands and scripts.</span></span>

<span data-ttu-id="15ddb-228">PowerShell `$null` 은 값, 즉 명시적 자리 표시자로 개체를 처리 하므로를 사용 `$null` 하 여 일련의 값에서 빈 값을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-228">PowerShell treats `$null` as an object with a value, that is, as an explicit placeholder, so you can use `$null` to represent an empty value in a series of values.</span></span>

<span data-ttu-id="15ddb-229">예를 들어 `$null` 가 컬렉션에 포함 되어 있으면 개체 중 하나로 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-229">For example, when `$null` is included in a collection, it's counted as one of the objects.</span></span>

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

<span data-ttu-id="15ddb-230">변수를 cmdlet에 파이프 하는 경우 `$null` `ForEach-Object` `$null` 다른 개체의 경우와 마찬가지로에 대 한 값을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-230">If you pipe the `$null` variable to the `ForEach-Object` cmdlet, it generates a value for `$null`, just as it does for the other objects</span></span>

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

<span data-ttu-id="15ddb-231">따라서 `$null` 를 사용 하 여 **매개 변수 값을 의미 하지 않습니다**.</span><span class="sxs-lookup"><span data-stu-id="15ddb-231">As a result, you can't use `$null` to mean **no parameter value**.</span></span> <span data-ttu-id="15ddb-232">의 매개 변수 값이 `$null` 기본 매개 변수 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-232">A parameter value of `$null` overrides the default parameter value.</span></span>

<span data-ttu-id="15ddb-233">그러나 PowerShell은 변수를 자리 표시자로 처리 하기 때문에 `$null` 다음과 같은 스크립트에서 사용할 수 있습니다 .이 변수는 무시 되는 경우 작동 하지 `$null` 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-233">However, because PowerShell treats the `$null` variable as a placeholder, you can use it in scripts like the following one, which wouldn't work if `$null` were ignored.</span></span>

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a><span data-ttu-id="15ddb-234">$PID</span><span class="sxs-lookup"><span data-stu-id="15ddb-234">$PID</span></span>

<span data-ttu-id="15ddb-235">현재 PowerShell 세션을 호스트 하는 프로세스의 PID (프로세스 식별자)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-235">Contains the process identifier (PID) of the process that is hosting the current PowerShell session.</span></span>

### <a name="profile"></a><span data-ttu-id="15ddb-236">$PROFILE</span><span class="sxs-lookup"><span data-stu-id="15ddb-236">$PROFILE</span></span>

<span data-ttu-id="15ddb-237">현재 사용자와 현재 호스트 응용 프로그램에 대 한 PowerShell 프로필의 전체 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-237">Contains the full path of the PowerShell profile for the current user and the current host application.</span></span> <span data-ttu-id="15ddb-238">이 변수를 사용 하 여 명령에 프로필을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-238">You can use this variable to represent the profile in commands.</span></span> <span data-ttu-id="15ddb-239">예를 들어 명령에 사용 하 여 프로필이 생성 되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-239">For example, you can use it in a command to determine whether a profile has been created:</span></span>

```powershell
Test-Path $PROFILE
```

<span data-ttu-id="15ddb-240">또는 명령에서 사용 하 여 프로필을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-240">Or, you can use it in a command to create a profile:</span></span>

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

<span data-ttu-id="15ddb-241">명령에서이를 사용 하 여 **notepad.exe** 에서 프로필을 열 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-241">You can use it in a command to open the profile in **notepad.exe** :</span></span>

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a><span data-ttu-id="15ddb-242">$PSBoundParameters</span><span class="sxs-lookup"><span data-stu-id="15ddb-242">$PSBoundParameters</span></span>

<span data-ttu-id="15ddb-243">스크립트나 함수 및 현재 값에 전달 되는 매개 변수의 사전을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-243">Contains a dictionary of the parameters that are passed to a script or function and their current values.</span></span> <span data-ttu-id="15ddb-244">이 변수에는 스크립트나 함수와 같은 매개 변수가 선언 된 범위에만 있는 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-244">This variable has a value only in a scope where parameters are declared, such as a script or function.</span></span> <span data-ttu-id="15ddb-245">매개 변수의 현재 값을 표시 하거나 변경 하거나 매개 변수 값을 다른 스크립트나 함수에 전달 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-245">You can use it to display or change the current values of parameters or to pass parameter values to another script or function.</span></span>

<span data-ttu-id="15ddb-246">이 예제에서 **Test2** 함수는를 `$PSBoundParameters` **Test1** 함수에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-246">In this example, the **Test2** function passes the `$PSBoundParameters` to the **Test1** function.</span></span> <span data-ttu-id="15ddb-247">는 `$PSBoundParameters` **키** 와 **값** 의 형식으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-247">The `$PSBoundParameters` are displayed in the format of **Key** and **Value**.</span></span>

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a><span data-ttu-id="15ddb-248">$PSCmdlet</span><span class="sxs-lookup"><span data-stu-id="15ddb-248">$PSCmdlet</span></span>

<span data-ttu-id="15ddb-249">실행 되는 cmdlet 또는 고급 함수를 나타내는 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-249">Contains an object that represents the cmdlet or advanced function that's being run.</span></span>

<span data-ttu-id="15ddb-250">Cmdlet 또는 함수 코드에서 개체의 속성 및 메서드를 사용 하 여 사용 조건에 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-250">You can use the properties and methods of the object in your cmdlet or function code to respond to the conditions of use.</span></span> <span data-ttu-id="15ddb-251">예를 들어 **ParameterSetName** 속성은 사용 중인 매개 변수 집합의 이름을 포함 하 고, **Shouldprocess** 메서드는 **WhatIf** 및 **Confirm** 매개 변수를 cmdlet에 동적으로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-251">For example, the **ParameterSetName** property contains the name of the parameter set that's being used, and the **ShouldProcess** method adds the **WhatIf** and **Confirm** parameters to the cmdlet dynamically.</span></span>

<span data-ttu-id="15ddb-252">자동 변수에 대 한 자세한 내용은 `$PSCmdlet` [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) 및 [about_Functions_Advanced](about_Functions_Advanced.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-252">For more information about the `$PSCmdlet` automatic variable, see [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) and [about_Functions_Advanced](about_Functions_Advanced.md).</span></span>

### <a name="pscommandpath"></a><span data-ttu-id="15ddb-253">$PSCommandPath</span><span class="sxs-lookup"><span data-stu-id="15ddb-253">$PSCommandPath</span></span>

<span data-ttu-id="15ddb-254">실행 되는 스크립트의 전체 경로 및 파일 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-254">Contains the full path and file name of the script that's being run.</span></span> <span data-ttu-id="15ddb-255">이 변수는 모든 스크립트에서 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-255">This variable is valid in all scripts.</span></span>

### <a name="psculture"></a><span data-ttu-id="15ddb-256">$PSCulture</span><span class="sxs-lookup"><span data-stu-id="15ddb-256">$PSCulture</span></span>

<span data-ttu-id="15ddb-257">운영 체제에서 현재 사용 중인 문화권의 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-257">Contains the name of the culture currently in use in the operating system.</span></span> <span data-ttu-id="15ddb-258">문화권에 따라 숫자, 통화 및 날짜와 같은 항목의 표시 형식이 결정 되 고,이는 **system.object** 개체에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-258">The culture determines the display format of items such as numbers, currency, and dates, and is stored in a **System.Globalization.CultureInfo** object.</span></span> <span data-ttu-id="15ddb-259">`Get-Culture`를 사용 하 여 컴퓨터의 문화권을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-259">Use `Get-Culture` to display the computer's culture.</span></span> <span data-ttu-id="15ddb-260">`$PSCulture`**이름** 속성의 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-260">`$PSCulture` contains the **Name** property's value.</span></span>

### <a name="psdebugcontext"></a><span data-ttu-id="15ddb-261">$PSDebugContext</span><span class="sxs-lookup"><span data-stu-id="15ddb-261">$PSDebugContext</span></span>

<span data-ttu-id="15ddb-262">디버깅 하는 동안이 변수는 디버깅 환경에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-262">While debugging, this variable contains information about the debugging environment.</span></span> <span data-ttu-id="15ddb-263">그렇지 않으면 **null** 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-263">Otherwise, it contains a **null** value.</span></span> <span data-ttu-id="15ddb-264">따라서 디버거에서 컨트롤을 사용할 수 있는지 여부를 나타내는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-264">As a result, you can use it to indicate whether the debugger has control.</span></span> <span data-ttu-id="15ddb-265">채워진 경우 **중단점과** **InvocationInfo** 속성을 포함 하는 **psdebugcontext** 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-265">When populated, it contains a **PsDebugContext** object that has **Breakpoints** and **InvocationInfo** properties.</span></span> <span data-ttu-id="15ddb-266">**InvocationInfo** 속성은 **Location** 속성을 포함 하 여 몇 가지 유용한 속성을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-266">The **InvocationInfo** property has several useful properties, including the **Location** property.</span></span> <span data-ttu-id="15ddb-267">**Location** 속성은 디버깅 중인 스크립트의 경로를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-267">The **Location** property indicates the path of the script that is being debugged.</span></span>

### <a name="pshome"></a><span data-ttu-id="15ddb-268">$PSHOME</span><span class="sxs-lookup"><span data-stu-id="15ddb-268">$PSHOME</span></span>

<span data-ttu-id="15ddb-269">일반적으로 Windows 시스템에서 PowerShell에 대 한 설치 디렉터리의 전체 경로를 포함 합니다 `$env:windir\System32\PowerShell\v1.0` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-269">Contains the full path of the installation directory for PowerShell, typically, `$env:windir\System32\PowerShell\v1.0` in Windows systems.</span></span> <span data-ttu-id="15ddb-270">PowerShell 파일의 경로에이 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-270">You can use this variable in the paths of PowerShell files.</span></span> <span data-ttu-id="15ddb-271">예를 들어 다음 명령은 단어 **변수에** 대 한 개념 도움말 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-271">For example, the following command searches the conceptual Help topics for the word **variable** :</span></span>

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a><span data-ttu-id="15ddb-272">$PSItem</span><span class="sxs-lookup"><span data-stu-id="15ddb-272">$PSItem</span></span>

<span data-ttu-id="15ddb-273">`$_`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-273">Same as `$_`.</span></span> <span data-ttu-id="15ddb-274">파이프라인 개체의 현재 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-274">Contains the current object in the pipeline object.</span></span> <span data-ttu-id="15ddb-275">파이프라인의 모든 개체 또는 선택한 개체에 대해 작업을 수행 하는 명령에서이 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-275">You can use this variable in commands that perform an action on every object or on selected objects in a pipeline.</span></span>

### <a name="psscriptroot"></a><span data-ttu-id="15ddb-276">$PSScriptRoot</span><span class="sxs-lookup"><span data-stu-id="15ddb-276">$PSScriptRoot</span></span>

<span data-ttu-id="15ddb-277">스크립트가 실행 되는 디렉터리를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-277">Contains the directory from which a script is being run.</span></span>

<span data-ttu-id="15ddb-278">PowerShell 2.0에서이 변수는 스크립트 모듈 () 에서만 사용할 수 `.psm1` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-278">In PowerShell 2.0, this variable is valid only in script modules (`.psm1`).</span></span>
<span data-ttu-id="15ddb-279">PowerShell 3.0부터 모든 스크립트에서 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-279">Beginning in PowerShell 3.0, it's valid in all scripts.</span></span>

### <a name="pssenderinfo"></a><span data-ttu-id="15ddb-280">$PSSenderInfo</span><span class="sxs-lookup"><span data-stu-id="15ddb-280">$PSSenderInfo</span></span>

<span data-ttu-id="15ddb-281">사용자 id 및 원래 컴퓨터의 표준 시간대를 포함 하 여 PSSession을 시작한 사용자에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-281">Contains information about the user who started the PSSession, including the user identity and the time zone of the originating computer.</span></span> <span data-ttu-id="15ddb-282">이 변수는 PSSessions 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-282">This variable is available only in PSSessions.</span></span>

<span data-ttu-id="15ddb-283">`$PSSenderInfo`변수에는 기본적으로 원래 세션의만 포함 하는 사용자 구성 속성인 **applicationarguments** 가 포함 됩니다 `$PSVersionTable` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-283">The `$PSSenderInfo` variable includes a user-configurable property, **ApplicationArguments** , that by default, contains only the `$PSVersionTable` from the originating session.</span></span> <span data-ttu-id="15ddb-284">**Applicationarguments** 속성에 데이터를 추가 하려면 Cmdlet의 **applicationarguments** 매개 변수를 사용 합니다 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-284">To add data to the **ApplicationArguments** property, use the **ApplicationArguments** parameter of the `New-PSSessionOption` cmdlet.</span></span>

### <a name="psuiculture"></a><span data-ttu-id="15ddb-285">$PSUICulture</span><span class="sxs-lookup"><span data-stu-id="15ddb-285">$PSUICulture</span></span>

<span data-ttu-id="15ddb-286">운영 체제에서 현재 사용 중인 UI (사용자 인터페이스) 문화권의 이름을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-286">Contains the name of the user interface (UI) culture that's currently in use in the operating system.</span></span> <span data-ttu-id="15ddb-287">UI 문화권에 따라 메뉴, 메시지 등의 사용자 인터페이스 요소에 사용되는 텍스트 문자열이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-287">The UI culture determines which text strings are used for user interface elements, such as menus and messages.</span></span> <span data-ttu-id="15ddb-288">시스템의 **System.Globalization.CultureInfo.CurrentUICulture.Name** 속성 값입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-288">This is the value of the **System.Globalization.CultureInfo.CurrentUICulture.Name** property of the system.</span></span> <span data-ttu-id="15ddb-289">시스템에 대 한 **시스템 세계화 CultureInfo** 개체를 가져오려면 cmdlet을 사용 합니다 `Get-UICulture` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-289">To get the **System.Globalization.CultureInfo** object for the system, use the `Get-UICulture` cmdlet.</span></span>

### <a name="psversiontable"></a><span data-ttu-id="15ddb-290">$PSVersionTable</span><span class="sxs-lookup"><span data-stu-id="15ddb-290">$PSVersionTable</span></span>

<span data-ttu-id="15ddb-291">현재 세션에서 실행 중인 PowerShell 버전에 대 한 세부 정보를 표시 하는 읽기 전용 해시 테이블을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-291">Contains a read-only hash table that displays details about the version of PowerShell that is running in the current session.</span></span> <span data-ttu-id="15ddb-292">테이블에는 다음 항목이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-292">The table includes the following items:</span></span>

| <span data-ttu-id="15ddb-293">속성</span><span class="sxs-lookup"><span data-stu-id="15ddb-293">Property</span></span>                  | <span data-ttu-id="15ddb-294">Description</span><span class="sxs-lookup"><span data-stu-id="15ddb-294">Description</span></span>                                   |
| ------------------------- | --------------------------------------------- |
| <span data-ttu-id="15ddb-295">**BuildVersion**</span><span class="sxs-lookup"><span data-stu-id="15ddb-295">**BuildVersion**</span></span>          | <span data-ttu-id="15ddb-296">현재 버전의 빌드 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-296">The build number of the current version</span></span>       |
| <span data-ttu-id="15ddb-297">**CLRVersion**</span><span class="sxs-lookup"><span data-stu-id="15ddb-297">**CLRVersion**</span></span>            | <span data-ttu-id="15ddb-298">공용 언어 런타임의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-298">The version of the common language runtime</span></span>    |
|                           | <span data-ttu-id="15ddb-299">CLR</span><span class="sxs-lookup"><span data-stu-id="15ddb-299">(CLR)</span></span>                                         |
| <span data-ttu-id="15ddb-300">**PSCompatibleVersions**</span><span class="sxs-lookup"><span data-stu-id="15ddb-300">**PSCompatibleVersions**</span></span>  | <span data-ttu-id="15ddb-301">호환 되는 PowerShell 버전</span><span class="sxs-lookup"><span data-stu-id="15ddb-301">Versions of PowerShell that are compatible</span></span>    |
|                           | <span data-ttu-id="15ddb-302">현재 버전 사용</span><span class="sxs-lookup"><span data-stu-id="15ddb-302">with the current version</span></span>                      |
| <span data-ttu-id="15ddb-303">**PSEdition**</span><span class="sxs-lookup"><span data-stu-id="15ddb-303">**PSEdition**</span></span>             | <span data-ttu-id="15ddb-304">이 속성에는에 대 한 ' Desktop ' 값이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-304">This property has the value of 'Desktop', for</span></span> |
|                           | <span data-ttu-id="15ddb-305">Windows Server 및 Windows 클라이언트 버전</span><span class="sxs-lookup"><span data-stu-id="15ddb-305">Windows Server and Windows client versions.</span></span>   |
|                           | <span data-ttu-id="15ddb-306">이 속성의 값은</span><span class="sxs-lookup"><span data-stu-id="15ddb-306">This property has the value of 'Core' for</span></span>     |
|                           | <span data-ttu-id="15ddb-307">Nano 서버 또는에서 실행 되는 PowerShell</span><span class="sxs-lookup"><span data-stu-id="15ddb-307">PowerShell running under Nano Server or</span></span>       |
|                           | <span data-ttu-id="15ddb-308">Windows IOT.</span><span class="sxs-lookup"><span data-stu-id="15ddb-308">Windows IOT.</span></span>                                  |
| <span data-ttu-id="15ddb-309">**PSRemotingProtocolVersion**</span><span class="sxs-lookup"><span data-stu-id="15ddb-309">**PSRemotingProtocolVersion**</span></span> | <span data-ttu-id="15ddb-310">PowerShell 원격의 버전</span><span class="sxs-lookup"><span data-stu-id="15ddb-310">The version of the PowerShell remote</span></span>      |
|                           | <span data-ttu-id="15ddb-311">관리 프로토콜.</span><span class="sxs-lookup"><span data-stu-id="15ddb-311">management protocol.</span></span>                          |
| <span data-ttu-id="15ddb-312">**PSVersion**</span><span class="sxs-lookup"><span data-stu-id="15ddb-312">**PSVersion**</span></span>             | <span data-ttu-id="15ddb-313">PowerShell 버전 번호</span><span class="sxs-lookup"><span data-stu-id="15ddb-313">The PowerShell version number</span></span>                 |
| <span data-ttu-id="15ddb-314">**SerializationVersion**</span><span class="sxs-lookup"><span data-stu-id="15ddb-314">**SerializationVersion**</span></span>  | <span data-ttu-id="15ddb-315">Serialization 메서드의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-315">The version of the serialization method</span></span>       |
| <span data-ttu-id="15ddb-316">**WSManStackVersion**</span><span class="sxs-lookup"><span data-stu-id="15ddb-316">**WSManStackVersion**</span></span>     | <span data-ttu-id="15ddb-317">WS-Management 스택의 버전 번호</span><span class="sxs-lookup"><span data-stu-id="15ddb-317">The version number of the WS-Management stack</span></span> |

### <a name="pwd"></a><span data-ttu-id="15ddb-318">$PWD</span><span class="sxs-lookup"><span data-stu-id="15ddb-318">$PWD</span></span>

<span data-ttu-id="15ddb-319">현재 디렉터리의 전체 경로를 나타내는 path 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-319">Contains a path object that represents the full path of the current directory.</span></span>

### <a name="sender"></a><span data-ttu-id="15ddb-320">$Sender</span><span class="sxs-lookup"><span data-stu-id="15ddb-320">$Sender</span></span>

<span data-ttu-id="15ddb-321">이 이벤트를 생성 한 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-321">Contains the object that generated this event.</span></span> <span data-ttu-id="15ddb-322">이 변수는 이벤트 등록 명령의 작업 블록 내 에서만 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-322">This variable is populated only within the Action block of an event registration command.</span></span> <span data-ttu-id="15ddb-323">이 변수의 값은를 반환 하는 **PSEventArgs** 개체의 Sender 속성 에서도 찾을 수 있습니다 `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-323">The value of this variable can also be found in the Sender property of the **PSEventArgs** object that `Get-Event` returns.</span></span>

### <a name="shellid"></a><span data-ttu-id="15ddb-324">$ShellId</span><span class="sxs-lookup"><span data-stu-id="15ddb-324">$ShellId</span></span>

<span data-ttu-id="15ddb-325">현재 셸의 식별자를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-325">Contains the identifier of the current shell.</span></span>

### <a name="stacktrace"></a><span data-ttu-id="15ddb-326">$StackTrace</span><span class="sxs-lookup"><span data-stu-id="15ddb-326">$StackTrace</span></span>

<span data-ttu-id="15ddb-327">가장 최근의 오류에 대 한 스택 추적을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-327">Contains a stack trace for the most recent error.</span></span>

### <a name="switch"></a><span data-ttu-id="15ddb-328">$switch</span><span class="sxs-lookup"><span data-stu-id="15ddb-328">$switch</span></span>

<span data-ttu-id="15ddb-329">문의 결과 값이 아닌 열거자를 포함 `Switch` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-329">Contains the enumerator not the resulting values of a `Switch` statement.</span></span> <span data-ttu-id="15ddb-330">`$switch`변수는 문이 실행 되는 동안에만 존재 `Switch` 하며 `switch` 문이 실행을 완료 하면 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-330">The `$switch` variable exists only while the `Switch` statement is running; it's deleted when the `switch` statement completes execution.</span></span> <span data-ttu-id="15ddb-331">자세한 내용은 [about_Switch](about_Switch.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-331">For more information, see [about_Switch](about_Switch.md).</span></span>

<span data-ttu-id="15ddb-332">열거자는 루프 값을 검색 하 고 현재 루프 반복을 변경 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-332">Enumerators contain properties and methods you can use to retrieve loop values and change the current loop iteration.</span></span> <span data-ttu-id="15ddb-333">자세한 내용은 [열거자 사용](#using-enumerators)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-333">For more information, see [Using Enumerators](#using-enumerators).</span></span>

### <a name="this"></a><span data-ttu-id="15ddb-334">$this</span><span class="sxs-lookup"><span data-stu-id="15ddb-334">$this</span></span>

<span data-ttu-id="15ddb-335">스크립트 속성이 나 스크립트 메서드를 정의 하는 스크립트 블록에서 변수는 `$this` 확장 중인 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-335">In a script block that defines a script property or script method, the `$this` variable refers to the object that is being extended.</span></span>

<span data-ttu-id="15ddb-336">사용자 지정 클래스에서 변수는 클래스 `$this` 에 정의 된 속성 및 메서드에 대 한 액세스를 허용 하는 클래스 개체 자체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-336">In a custom class, the `$this` variable refers to the class object itself allowing access to properties and methods defined in the class.</span></span>

### <a name="true"></a><span data-ttu-id="15ddb-337">$true</span><span class="sxs-lookup"><span data-stu-id="15ddb-337">$true</span></span>

<span data-ttu-id="15ddb-338">**True** 를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-338">Contains **True**.</span></span> <span data-ttu-id="15ddb-339">이 변수를 사용 하 여 명령 및 스크립트에서 **True** 를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-339">You can use this variable to represent **True** in commands and scripts.</span></span>

## <a name="using-enumerators"></a><span data-ttu-id="15ddb-340">열거자 사용</span><span class="sxs-lookup"><span data-stu-id="15ddb-340">Using Enumerators</span></span>

<span data-ttu-id="15ddb-341">`$input`, `$foreach` 및 변수는 `$switch` 포함 하는 코드 블록에서 처리 하는 값을 반복 하는 데 사용 되는 모든 열거자입니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-341">The `$input`, `$foreach`, and `$switch` variables are all enumerators used to iterate through the values processed by their containing code block.</span></span>

<span data-ttu-id="15ddb-342">열거자는 반복을 이동 또는 다시 설정 하거나 반복 값을 검색 하는 데 사용할 수 있는 속성 및 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-342">An enumerator contains properties and methods you can use to advance or reset iteration, or retrieve iteration values.</span></span> <span data-ttu-id="15ddb-343">열거자를 직접 조작 하는 것은 모범 사례로 간주 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-343">Directly manipulating enumerators isn't considered best practice.</span></span>

- <span data-ttu-id="15ddb-344">루프 내에서 흐름 제어 키워드를 [중단](about_Break.md) 하 고 [계속](about_Continue.md) 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-344">Within loops, flow control keywords [break](about_Break.md) and [continue](about_Continue.md) should be preferred.</span></span>
- <span data-ttu-id="15ddb-345">파이프라인 입력을 허용 하는 함수 내에서 **ValueFromPipeline** 또는 **ValueFromPipelineByPropertyName** 특성과 함께 매개 변수를 사용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-345">Within functions that accept pipeline input, it's best practice to use Parameters with the **ValueFromPipeline** or **ValueFromPipelineByPropertyName** attributes.</span></span>

  <span data-ttu-id="15ddb-346">자세한 내용은 [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15ddb-346">For more information, see [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).</span></span>

### <a name="movenext"></a><span data-ttu-id="15ddb-347">MoveNext</span><span class="sxs-lookup"><span data-stu-id="15ddb-347">MoveNext</span></span>

<span data-ttu-id="15ddb-348">[MoveNext](/dotnet/api/system.collections.ienumerator.movenext) 메서드는 열거자를 컬렉션의 다음 요소로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-348">The [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) method advances the enumerator to the next element of the collection.</span></span> <span data-ttu-id="15ddb-349">**MoveNext** 는 열거자가 성공적으로 진행 되었으면 **True** 를 반환 하 고, 컬렉션의 끝을 지난 경우 **False** 를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-349">**MoveNext** returns **True** if the enumerator was successfully advanced, **False** if the enumerator has passed the end of the collection.</span></span>

> [!NOTE]
> <span data-ttu-id="15ddb-350">**MoveNext** 에서 반환 된 **부울** 값은 출력 스트림으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-350">The **Boolean** value returned my **MoveNext** is sent to the output stream.</span></span>
> <span data-ttu-id="15ddb-351">출력을 typecasting으로 표시 하지 `[void]` 않거나 [Null](xref:Microsoft.PowerShell.Core.Out-Null)로 파이프 하 여 출력을 표시 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-351">You can suppress the output by typecasting it to `[void]` or piping it to [Out-Null](xref:Microsoft.PowerShell.Core.Out-Null).</span></span>
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a><span data-ttu-id="15ddb-352">다시 설정</span><span class="sxs-lookup"><span data-stu-id="15ddb-352">Reset</span></span>

<span data-ttu-id="15ddb-353">[Reset](/dotnet/api/system.collections.ienumerator.reset) 메서드는 컬렉션의 첫 번째 요소 **앞** 의 초기 위치로 열거자를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-353">The [Reset](/dotnet/api/system.collections.ienumerator.reset) method sets the enumerator to its initial position, which is **before** the first element in the collection.</span></span>

### <a name="current"></a><span data-ttu-id="15ddb-354">현재</span><span class="sxs-lookup"><span data-stu-id="15ddb-354">Current</span></span>

<span data-ttu-id="15ddb-355">[Current](/dotnet/api/system.collections.ienumerator.current) 속성은 컬렉션 또는 파이프라인에서 열거자의 현재 위치에 있는 요소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-355">The [Current](/dotnet/api/system.collections.ienumerator.current) property gets the element in the collection, or pipeline, at the current position of the enumerator.</span></span>

<span data-ttu-id="15ddb-356">**Current** 속성은 **MoveNext** 가 호출 될 때까지 계속 해 서 동일한 속성을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-356">The **Current** property continues to return the same property until **MoveNext** is called.</span></span>

## <a name="examples"></a><span data-ttu-id="15ddb-357">예</span><span class="sxs-lookup"><span data-stu-id="15ddb-357">Examples</span></span>

### <a name="example-1-using-the-input-variable"></a><span data-ttu-id="15ddb-358">예제 1: $input 변수 사용</span><span class="sxs-lookup"><span data-stu-id="15ddb-358">Example 1: Using the $input variable</span></span>

<span data-ttu-id="15ddb-359">다음 예제에서 변수에 액세스 하면 `$input` 다음 번에 프로세스 블록이 실행 될 때까지 변수가 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-359">In the following example, accessing the `$input` variable clears the variable until the next time the process block executes.</span></span> <span data-ttu-id="15ddb-360">**Reset** 메서드를 사용 하 여 `$input` 변수를 현재 파이프라인 값으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-360">Using the **Reset** method resets the `$input` variable to the current pipeline value.</span></span>

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

<span data-ttu-id="15ddb-361">액세스 하지 않더라도 프로세스 블록에서 자동으로 변수를 이동 `$input` 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-361">The process block automatically advances the `$input` variable even if you don't access it.</span></span>

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a><span data-ttu-id="15ddb-362">예제 2: 프로세스 블록 외부에서 $input 사용</span><span class="sxs-lookup"><span data-stu-id="15ddb-362">Example 2: Using $input outside the process block</span></span>

<span data-ttu-id="15ddb-363">프로세스 블록 외부에서 변수는 `$input` 함수로 파이프 된 모든 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-363">Outside of the process block the `$input` variable represents all the values piped into the function.</span></span>

- <span data-ttu-id="15ddb-364">변수에 액세스 하면 `$input` 모든 값이 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-364">Accessing the `$input` variable clears all values.</span></span>
- <span data-ttu-id="15ddb-365">**Reset** 메서드는 전체 컬렉션을 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-365">The **Reset** method resets the entire collection.</span></span>
- <span data-ttu-id="15ddb-366">**현재** 속성은 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-366">The **Current** property is never populated.</span></span>
- <span data-ttu-id="15ddb-367">컬렉션을 고급으로 사용할 수 없으므로 **MoveNext** 메서드에서 false를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-367">The **MoveNext** method returns false because the collection can't be advanced.</span></span>
  - <span data-ttu-id="15ddb-368">**MoveNext** 를 호출 하면 `$input` 변수가 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-368">Calling **MoveNext** clears out the `$input` variable.</span></span>

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a><span data-ttu-id="15ddb-369">예 3: $input 사용 Current 속성</span><span class="sxs-lookup"><span data-stu-id="15ddb-369">Example 3: Using the $input.Current property</span></span>

<span data-ttu-id="15ddb-370">**현재** 속성을 사용 하 여 **Reset** 메서드를 사용 하지 않고 현재 파이프라인 값에 여러 번 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-370">By using the **Current** property, the current pipeline value can be accessed multiple times without using the **Reset** method.</span></span> <span data-ttu-id="15ddb-371">프로세스 블록은 **MoveNext** 메서드를 자동으로 호출 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-371">The process block doesn't automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="15ddb-372">**MoveNext** 를 명시적으로 호출 하지 않으면 **현재** 속성이 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-372">The **Current** property will never be populated unless you explicitly call **MoveNext**.</span></span> <span data-ttu-id="15ddb-373">**현재** 속성은 해당 값을 지우지 않고 프로세스 블록 내에서 여러 번 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-373">The **Current** property can be accessed multiple times inside the process block without clearing its value.</span></span>

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a><span data-ttu-id="15ddb-374">예제 4: $foreach 변수 사용</span><span class="sxs-lookup"><span data-stu-id="15ddb-374">Example 4: Using the $foreach variable</span></span>

<span data-ttu-id="15ddb-375">변수와 달리 `$input` `$foreach` 변수는 항상 직접 액세스할 때 컬렉션의 모든 항목을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-375">Unlike the `$input` variable, the `$foreach` variable always represents all items in the collection when accessed directly.</span></span> <span data-ttu-id="15ddb-376">**현재 속성을** 사용 하 여 현재 컬렉션 요소에 액세스 하 고, **Reset** 및 **MoveNext** 메서드를 사용 하 여 해당 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-376">Use the **Current** property to access the current collection element, and the **Reset** and **MoveNext** methods to change its value.</span></span>

> [!NOTE]
> <span data-ttu-id="15ddb-377">루프의 각 반복 `foreach` 은 **MoveNext** 메서드를 자동으로 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-377">Each iteration of the `foreach` loop will automatically call the **MoveNext** method.</span></span>

<span data-ttu-id="15ddb-378">다음 루프는 두 번만 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-378">The following loop only executes twice.</span></span> <span data-ttu-id="15ddb-379">두 번째 반복에서는 반복이 완료 되기 전에 컬렉션이 세 번째 요소로 이동 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-379">In the second iteration, the collection is moved to the third element before the iteration is complete.</span></span> <span data-ttu-id="15ddb-380">두 번째 반복 후에는 반복할 값이 더 이상 없으며 루프가 종료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-380">After the second iteration, there are now no more values to iterate, and the loop terminates.</span></span>

<span data-ttu-id="15ddb-381">**MoveNext** 속성은 컬렉션을 반복 하도록 선택한 변수에 영향을 주지 않습니다 ( `$Num` ).</span><span class="sxs-lookup"><span data-stu-id="15ddb-381">The **MoveNext** property doesn't affect the variable chosen to iterate through the collection (`$Num`).</span></span>

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

<span data-ttu-id="15ddb-382">**Reset** 메서드를 사용 하 여 컬렉션의 현재 요소를 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-382">Using the **Reset** method resets the current element in the collection.</span></span> <span data-ttu-id="15ddb-383">다음 예제에서는 **Reset** 메서드가 호출 되기 때문에 처음 두 요소를 **두 번** 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-383">The following example loops through the first two elements **twice** because the **Reset** method is called.</span></span> <span data-ttu-id="15ddb-384">처음 두 루프 후에 `if` 문이 실패 하 고 루프는 세 요소를 모두 정상적으로 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-384">After the first two loops, the `if` statement fails and the loop iterates through all three elements normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15ddb-385">이 경우 무한 루프가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-385">This could result in an infinite loop.</span></span>

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a><span data-ttu-id="15ddb-386">예 5: $switch 변수 사용</span><span class="sxs-lookup"><span data-stu-id="15ddb-386">Example 5: Using the $switch variable</span></span>

<span data-ttu-id="15ddb-387">`$switch`변수에는 변수와 정확히 동일한 규칙이 있습니다 `$foreach` .</span><span class="sxs-lookup"><span data-stu-id="15ddb-387">The `$switch` variable has the exact same rules as the `$foreach` variable.</span></span>
<span data-ttu-id="15ddb-388">다음 예제에서는 모든 열거자 개념을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="15ddb-388">The following example demonstrates all the enumerator concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="15ddb-389">MoveNext 메서드 뒤에 문이 없더라도 설명 **된 사례가 어떻게** 실행 되지 않는지 확인 합니다 `break` . **MoveNext**</span><span class="sxs-lookup"><span data-stu-id="15ddb-389">Note how the **NotEvaluated** case is never executed, even though there's no `break` statement after the **MoveNext** method.</span></span>

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a><span data-ttu-id="15ddb-390">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15ddb-390">See also</span></span>

[<span data-ttu-id="15ddb-391">about_Functions</span><span class="sxs-lookup"><span data-stu-id="15ddb-391">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="15ddb-392">about_Functions_Advanced</span><span class="sxs-lookup"><span data-stu-id="15ddb-392">about_Functions_Advanced</span></span>](about_Functions_Advanced.md)

[<span data-ttu-id="15ddb-393">about_Functions_Advanced_Methods</span><span class="sxs-lookup"><span data-stu-id="15ddb-393">about_Functions_Advanced_Methods</span></span>](about_Functions_Advanced_Methods.md)

[<span data-ttu-id="15ddb-394">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="15ddb-394">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="15ddb-395">about_Functions_OutputTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="15ddb-395">about_Functions_OutputTypeAttribute</span></span>](about_Functions_OutputTypeAttribute.md)

[<span data-ttu-id="15ddb-396">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="15ddb-396">about_Functions_CmdletBindingAttribute</span></span>](about_Functions_CmdletBindingAttribute.md)

[<span data-ttu-id="15ddb-397">about_Hash_Tables</span><span class="sxs-lookup"><span data-stu-id="15ddb-397">about_Hash_Tables</span></span>](about_Hash_Tables.md)

[<span data-ttu-id="15ddb-398">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="15ddb-398">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="15ddb-399">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="15ddb-399">about_Splatting</span></span>](about_Splatting.md)

[<span data-ttu-id="15ddb-400">about_Variables</span><span class="sxs-lookup"><span data-stu-id="15ddb-400">about_Variables</span></span>](about_Variables.md)
