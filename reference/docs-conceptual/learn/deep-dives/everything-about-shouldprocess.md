---
title: ShouldProcess에 대해 알고 싶은 모든 것
description: ShouldProcess는 자주 간과되는 중요 기능입니다. WhatIf 및 Confirm 매개 변수를 사용하면 함수에 쉽게 추가할 수 있습니다.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1d9110302a191b90bd11bdf742f77704a8c9d6f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149486"
---
# <a name="everything-you-wanted-to-know-about-shouldprocess"></a><span data-ttu-id="a2f24-104">ShouldProcess에 대해 알고 싶은 모든 것</span><span class="sxs-lookup"><span data-stu-id="a2f24-104">Everything you wanted to know about ShouldProcess</span></span>

<span data-ttu-id="a2f24-105">PowerShell 함수에는 사용자와의 상호 작용 방식을 크게 개선하는 몇 가지 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-105">PowerShell functions have several features that greatly improve the way users interact with them.</span></span>
<span data-ttu-id="a2f24-106">자주 간과되는 한 가지 중요한 기능은 `-WhatIf` 및 `-Confirm` 지원이며 함수에도 쉽게 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-106">One important feature that is often overlooked is `-WhatIf` and `-Confirm` support and it's easy to add to your functions.</span></span> <span data-ttu-id="a2f24-107">이 문서에서는 이 기능을 구현하는 방법을 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-107">In this article, we dive deep into how to implement this feature.</span></span>

> [!NOTE]
> <span data-ttu-id="a2f24-108">이 문서의 [원래 버전][]은 [@KevinMarquette][]가 작성한 블로그에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-108">The [original version][] of this article appeared on the blog written by [@KevinMarquette][].</span></span> <span data-ttu-id="a2f24-109">PowerShell 팀은 이 콘텐츠를 공유해 준 Kevin에게 감사의 말을 전합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-109">The PowerShell team thanks Kevin for sharing this content with us.</span></span> <span data-ttu-id="a2f24-110">[PowerShellExplained.com][]에 있는 그의 블로그를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a2f24-110">Please check out his blog at [PowerShellExplained.com][].</span></span>

<span data-ttu-id="a2f24-111">함수에서 사용 설정하면 사용자에게 필요한 보안 네트워크를 제공할 수 있는 단순한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-111">This is a simple feature you can enable in your functions to provide a safety net for the users that need it.</span></span> <span data-ttu-id="a2f24-112">위험할 수 있는 명령을 처음으로 수행할 때는 겁이 나기 마련입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-112">There's nothing scarier than running a command that you know can be dangerous for the first time.</span></span> <span data-ttu-id="a2f24-113">`-WhatIf`를 이용해 이를 실행하면 결과는 크게 차이 납니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-113">The option to run it with `-WhatIf` can make a big difference.</span></span>

## <a name="commonparameters"></a><span data-ttu-id="a2f24-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a2f24-114">CommonParameters</span></span>

<span data-ttu-id="a2f24-115">이러한 [공통 매개 변수][]구현 방법을 살펴보기 전에 먼저 사용 방법을 간단하게 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-115">Before we look at implementing these [common parameters][], I want to take a quick look at how they're used.</span></span>

## <a name="using--whatif"></a><span data-ttu-id="a2f24-116">-WhatIf 사용</span><span class="sxs-lookup"><span data-stu-id="a2f24-116">Using -WhatIf</span></span>

<span data-ttu-id="a2f24-117">명령에서 `-WhatIf` 매개 변수를 지원한다면 명령을 변경하는 대신 명령이 수행하는 작업을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-117">When a command supports the `-WhatIf` parameter, it allows you to see what the command would have done instead of making changes.</span></span> <span data-ttu-id="a2f24-118">문제가 될 수 있는 작업을 하기 전에 명령이 미칠 영향을 테스트하면 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-118">it's a good way to test out the impact of a command, especially before you do something destructive.</span></span>

```powershell
PS C:\temp> Remove-Item -Path .\myfile1.txt -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="a2f24-119">명령이 `ShouldProcess`를 올바르게 구현한다면 명령이 유발한 변경 내용이 모두 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-119">If the command correctly implements `ShouldProcess`, it should show you all the changes that it would have made.</span></span> <span data-ttu-id="a2f24-120">다음은 와일드카드를 사용하여 여러 파일을 삭제하는 예입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-120">Here is an example using a wildcard to delete multiple files.</span></span>

```powershell
PS C:\temp> Remove-Item -Path * -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\myfile2.txt".
What if: Performing the operation "Remove File" on target "C:\Temp\importantfile.txt".
```

## <a name="using--confirm"></a><span data-ttu-id="a2f24-121">-Confirm 사용</span><span class="sxs-lookup"><span data-stu-id="a2f24-121">Using -Confirm</span></span>

<span data-ttu-id="a2f24-122">`-WhatIf`를 지원하는 명령은 `-Confirm`도 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-122">Commands that support `-WhatIf` also support `-Confirm`.</span></span> <span data-ttu-id="a2f24-123">이 기능을 이용하면 수행하기 전에 작업을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-123">This gives you a chance confirm an action before performing it.</span></span>

```powershell
PS C:\temp> Remove-Item .\myfile1.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="a2f24-124">계속하거나, 변경을 건너뛰거나, 스크립트를 중지하는 옵션이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-124">In this case, you have multiple options that allow you to continue, skip a change, or stop the script.</span></span> <span data-ttu-id="a2f24-125">도움말 프롬프트에서 다음과 같이 각 옵션을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-125">The help prompt describes each of those options like this.</span></span>

```Output
Y - Continue with only the next step of the operation.
A - Continue with all the steps of the operation.
N - Skip this operation and proceed with the next operation.
L - Skip this operation and all subsequent operations.
S - Pause the current pipeline and return to the command prompt. Type "exit" to resume the pipeline.
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

### <a name="localization"></a><span data-ttu-id="a2f24-126">지역화</span><span class="sxs-lookup"><span data-stu-id="a2f24-126">Localization</span></span>

<span data-ttu-id="a2f24-127">이 프롬프트는 PowerShell에서 지역화되므로 언어는 운영 체제의 언어를 기준으로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-127">This prompt is localized in PowerShell so the language changes based on the language of your operating system.</span></span> <span data-ttu-id="a2f24-128">PowerShell에서는 사용자를 위해 이 기능도 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-128">This is one more thing that PowerShell manages for you.</span></span>

### <a name="switch-parameters"></a><span data-ttu-id="a2f24-129">Switch 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a2f24-129">Switch parameters</span></span>

<span data-ttu-id="a2f24-130">값을 스위치 매개 변수로 전달하는 방법을 간단하게 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-130">Let's take quick moment to look at ways to pass a value to a switch parameter.</span></span> <span data-ttu-id="a2f24-131">이 매개 변수를 호출하는 주된 이유는 호출하는 함수에 매개 변수 값을 전달해야 할 때가 잦기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-131">The main reason I call this out is that you often want to pass parameter values to functions you call.</span></span>

<span data-ttu-id="a2f24-132">첫 번째 방법은 모든 매개 변수에 사용할 수 있는 구체적인 매개 변수 구문이지만 일반적으로는 스위치 매개 변수에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-132">The first approach is a specific parameter syntax that can be used for all parameters but you mostly see it used for switch parameters.</span></span> <span data-ttu-id="a2f24-133">콜론을 지정하여 값을 매개 변수에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-133">You specify a colon to attach a value to the parameter.</span></span>

```powershell
Remove-Item -Path:* -WhatIf:$true
```

<span data-ttu-id="a2f24-134">변수에서도 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-134">You can do the same with a variable.</span></span>

```powershell
$DoWhatIf = $true
Remove-Item -Path * -WhatIf:$DoWhatIf
```

<span data-ttu-id="a2f24-135">두 번째 방법은 해시 테이블을 사용하여 값을 스플랫하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-135">The second approach is to use a hashtable to splat the value.</span></span>

```powershell
$RemoveSplat = @{
    Path = '*'
    WhatIf = $true
}
Remove-Item @RemoveSplat
```

<span data-ttu-id="a2f24-136">해시 테이블이나 스플래팅을 잘 모르신다면 [해시 테이블에 대해 알고 싶은 모든 것][]을 다루는 다른 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2f24-136">If you're new to hashtables or splatting, I have another article on that covers [everything you wanted to know about hashtables][].</span></span>

## <a name="supportsshouldprocess"></a><span data-ttu-id="a2f24-137">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="a2f24-137">SupportsShouldProcess</span></span>

<span data-ttu-id="a2f24-138">`-WhatIf` 및 `-Confirm` 지원을 사용 설정하는 첫 번째 단계는 함수의 `CmdletBinding`에서 `SupportsShouldProcess`를 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-138">The first step to enable `-WhatIf` and `-Confirm` support is to specify `SupportsShouldProcess` in the `CmdletBinding` of your function.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt
}
```

<span data-ttu-id="a2f24-139">이런 식으로 `SupportsShouldProcess`를 지정하면 이제 `-WhatIf`(또는 `-Confirm`)를 사용하여 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-139">By specifying `SupportsShouldProcess` in this way, we can now call our function with `-WhatIf` (or `-Confirm`).</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Remove File" on target "C:\Temp\myfile1.txt".
```

<span data-ttu-id="a2f24-140">`-WhatIf`라는 매개 변수는 만들지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-140">Notice that I did not create a parameter called `-WhatIf`.</span></span> <span data-ttu-id="a2f24-141">`SupportsShouldProcess`를 지정하면 자동으로 생성되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-141">Specifying `SupportsShouldProcess` automatically creates it for us.</span></span> <span data-ttu-id="a2f24-142">`Test-ShouldProcess`에서 `-WhatIf` 매개 변수를 지정하면 우리가 호출하는 항목은 `-WhatIf` 처리도 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-142">When we specify the `-WhatIf` parameter on `Test-ShouldProcess`, some things we call also perform `-WhatIf` processing.</span></span>

### <a name="trust-but-verify"></a><span data-ttu-id="a2f24-143">신뢰하되 확인하세요</span><span class="sxs-lookup"><span data-stu-id="a2f24-143">Trust but verify</span></span>

<span data-ttu-id="a2f24-144">우리가 호출하는 모든 요소가 `-WhatIf` 값을 상속한다고 신뢰하면 위험합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-144">There's some danger here trusting that everything you call inherits `-WhatIf` values.</span></span> <span data-ttu-id="a2f24-145">나머지 예제에서 이러한 신뢰가 효과가 없으며 다른 명령을 호출할 때는 더욱 그렇다고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-145">For the rest of the examples, I'm going to assume that it doesn't work and be very explicit when making calls to other commands.</span></span> <span data-ttu-id="a2f24-146">여러분에게도 이 방법을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-146">I recommend that you do the same.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()
    Remove-Item .\myfile1.txt -WhatIf:$WhatIf
}
```

<span data-ttu-id="a2f24-147">다른 내용을 설명한 다음 이 내용을 다시 다루겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-147">I will revisit the nuances much later once you have a better understanding of all the pieces in play.</span></span>

## <a name="pscmdletshouldprocess"></a><span data-ttu-id="a2f24-148">$PSCmdlet.ShouldProcess</span><span class="sxs-lookup"><span data-stu-id="a2f24-148">$PSCmdlet.ShouldProcess</span></span>

<span data-ttu-id="a2f24-149">`SupportsShouldProcess`를 구현하는 메서드는 `$PSCmdlet.ShouldProcess`입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-149">The method that allows you to implement `SupportsShouldProcess` is `$PSCmdlet.ShouldProcess`.</span></span> <span data-ttu-id="a2f24-150">`$PSCmdlet.ShouldProcess(...)`를 호출하면 어떤 논리를 사용자가 처리하고 PowerShell에서 나머지를 처리하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-150">You call `$PSCmdlet.ShouldProcess(...)` to see if you should process some logic and PowerShell takes care of the rest.</span></span> <span data-ttu-id="a2f24-151">예제를 확인해보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-151">Let's start with an example:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        $file.Delete()
    }
}
```

<span data-ttu-id="a2f24-152">`$PSCmdlet.ShouldProcess($file.name)`를 호출하면 `-WhatIf`(및 `-Confirm` 매개 변수)를 확인하고 적절하게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-152">The call to `$PSCmdlet.ShouldProcess($file.name)` checks for the `-WhatIf` (and `-Confirm` parameter) then handles it accordingly.</span></span> <span data-ttu-id="a2f24-153">`-WhatIf`는 `ShouldProcess`가 변경 설명을 출력하고 `$false`를 반환하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-153">The `-WhatIf` causes `ShouldProcess` to output a description of the change and return `$false`:</span></span>

```powershell
PS> Test-ShouldProcess -WhatIf
What if: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

<span data-ttu-id="a2f24-154">`-Confirm`를 사용하여 호출하면 스크립트가 일시 중지되고 사용자에게 진행 여부를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-154">A call using `-Confirm` pauses the script and prompts the user with the option to continue.</span></span> <span data-ttu-id="a2f24-155">사용자가 `Y`를 선택하면 `$true`가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-155">It returns `$true` if the user selected `Y`.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm
Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="a2f24-156">`$PSCmdlet.ShouldProcess`의 놀라운 기능은 자세한 정보를 출력할 수도 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-156">An awesome feature of `$PSCmdlet.ShouldProcess` is that it doubles as verbose output.</span></span> <span data-ttu-id="a2f24-157">`ShouldProcess`를 구현할 때 자주 이 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-157">I depend on this often when implementing `ShouldProcess`.</span></span>

```powershell
PS> Test-ShouldProcess -Verbose
VERBOSE: Performing the operation "Test-ShouldProcess" on target "myfile1.txt".
```

### <a name="overloads"></a><span data-ttu-id="a2f24-158">오버로드</span><span class="sxs-lookup"><span data-stu-id="a2f24-158">Overloads</span></span>

<span data-ttu-id="a2f24-159">다양한 매개 변수를 사용하여 메시지를 사용자 지정하는 `$PSCmdlet.ShouldProcess`용 몇 가지 오버 로드가 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-159">There are a few different overloads for `$PSCmdlet.ShouldProcess` with different parameters for customizing the messaging.</span></span> <span data-ttu-id="a2f24-160">첫 번째 오버로드는 위의 예제에서 이미 확인했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-160">We already saw the first one in the example above.</span></span> <span data-ttu-id="a2f24-161">이 오버로드에 대해 좀 더 자세히 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-161">Let's take a closer look at it.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    if($PSCmdlet.ShouldProcess('TARGET')){
        # ...
    }
}
```

<span data-ttu-id="a2f24-162">이 오버로드는 함수 이름과 대상(매개 변수 값)을 모두 포함하는 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-162">This produces output that includes both the function name and the target (value of the parameter).</span></span>

```powershell
What if: Performing the operation "Test-ShouldProcess" on target "TARGET".
```

<span data-ttu-id="a2f24-163">두 번째 매개 변수를 작업으로 지정하면 메시지 내 함수 이름 대신 작업 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-163">Specifying a second parameter as the operation uses the operation value instead of the function name in the message.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".
```

<span data-ttu-id="a2f24-164">다음 방법은 메시지를 완전히 사용자 지정하는 매개 변수 3개를 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-164">The next option is to specify three parameters to fully customize the message.</span></span> <span data-ttu-id="a2f24-165">매개 변수 3개를 사용하면 첫 번째 매개 변수는 전체 메시지가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-165">When three parameters are used, the first one is the entire message.</span></span> <span data-ttu-id="a2f24-166">두 번째 매개 변수는 여전히 `-Confirm` 메시지 출력에서 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-166">The second two parameters are still used in the `-Confirm` message output.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

### <a name="quick-parameter-reference"></a><span data-ttu-id="a2f24-167">빠른 매개 변수 참조</span><span class="sxs-lookup"><span data-stu-id="a2f24-167">Quick parameter reference</span></span>

<span data-ttu-id="a2f24-168">사용해야 하는 매개 변수 확인만이 목적이라면 다양한 `-WhatIf` 시나리오에서 매개 변수에 따라 메시지가 어떻게 달라지는지 보여주는 빠른 참조를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a2f24-168">Just in case you came here only to figure out what parameters you should use, here is a quick reference showing how the parameters change the message in the different `-WhatIf` scenarios.</span></span>

```powershell
## $PSCmdlet.ShouldProcess('TARGET')
What if: Performing the operation "FUNCTION_NAME" on target "TARGET".

## $PSCmdlet.ShouldProcess('TARGET','OPERATION')
What if: Performing the operation "OPERATION" on target "TARGET".

## $PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION')
What if: MESSAGE
```

<span data-ttu-id="a2f24-169">주로 이 기능을 매개 변수 2개와 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-169">I tend to use the one with two parameters.</span></span>

### <a name="shouldprocessreason"></a><span data-ttu-id="a2f24-170">ShouldProcessReason</span><span class="sxs-lookup"><span data-stu-id="a2f24-170">ShouldProcessReason</span></span>

<span data-ttu-id="a2f24-171">다른 오버로드보다 더 고급 기능인 네 번째 오버로드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-171">We have a fourth overload that's more advanced than the others.</span></span> <span data-ttu-id="a2f24-172">이 오버로드를 이용하면 `ShouldProcess`를 실행한 이유를 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-172">It allows you to get the reason `ShouldProcess` was executed.</span></span> <span data-ttu-id="a2f24-173">대신 `$WhatIf`가 `$true`인지 확인하면 되므로 이 내용은 참조용으로만 수록했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-173">I'm only adding this here for completeness because we can just check if `$WhatIf` is `$true` instead.</span></span>

```powershell
$reason = ''
if($PSCmdlet.ShouldProcess('MESSAGE','TARGET','OPERATION',[ref]$reason)){
    Write-Output "Some Action"
}
$reason
```

<span data-ttu-id="a2f24-174">`$reason` 변수를 `[ref]`를 사용하는 참조 변수로서 네 번째 매개 변수에 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-174">We have to pass the `$reason` variable into the fourth parameter as a reference variable with `[ref]`.</span></span> <span data-ttu-id="a2f24-175">`ShouldProcess`는 `$reason`을 값 `None` 또는 `WhatIf`로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-175">`ShouldProcess` populates `$reason` with the value `None` or `WhatIf`.</span></span> <span data-ttu-id="a2f24-176">이 기능이 유용하다고 생각하지 않아 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-176">I didn't say this was useful and I have had no reason to ever use it.</span></span>

### <a name="where-to-place-it"></a><span data-ttu-id="a2f24-177">배치 장소</span><span class="sxs-lookup"><span data-stu-id="a2f24-177">Where to place it</span></span>

<span data-ttu-id="a2f24-178">`ShouldProcess`를 사용하면 스크립트 보안을 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-178">You use `ShouldProcess` to make your scripts safer.</span></span> <span data-ttu-id="a2f24-179">따라서 스크립트를 변경할 때는 이 기능을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-179">So you use it when your scripts are making changes.</span></span> <span data-ttu-id="a2f24-180">`$PSCmdlet.ShouldProcess` 호출을 변경하는 부분과 최대한 가깝게 배치하는 편입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-180">I like to place the `$PSCmdlet.ShouldProcess` call as close to the change as possible.</span></span>

```powershell
## general logic and variable work
if ($PSCmdlet.ShouldProcess('TARGET','OPERATION')){
    # Change goes here
}
```

<span data-ttu-id="a2f24-181">항목 컬렉션을 처리할 때는 항목별로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-181">If I'm processing a collection of items, I call it for each item.</span></span> <span data-ttu-id="a2f24-182">따라서 호출은 foreach 루프 내에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-182">So the call gets placed inside the foreach loop.</span></span>

```powershell
foreach ($node in $collection){
    # general logic and variable work
    if ($PSCmdlet.ShouldProcess($node,'OPERATION')){
        # Change goes here
    }
}
```

<span data-ttu-id="a2f24-183">`ShouldProcess`를 변경하는 부분 근처에 배치하는 이유는 `-WhatIf`가 지정되면 최대한 많은 코드를 실행하고 싶기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-183">The reason why I place `ShouldProcess` tightly around the change, is that I want as much code to execute as possible when `-WhatIf` is specified.</span></span> <span data-ttu-id="a2f24-184">사용자가 이러한 오류를 확인할 수 있도록 가능하다면 설정 및 유효성 검사를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-184">I want the setup and validation to run if possible so the user gets to see those errors.</span></span>

<span data-ttu-id="a2f24-185">제 프로젝트의 유효성을 검사하는 Pester 테스트에서도 이 기능을 즐겨 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-185">I also like to use this in my Pester tests that validate my projects.</span></span> <span data-ttu-id="a2f24-186">Pester에서 모형을 만들기 어려운 로직이 있다면 `ShouldProcess`에서 이를 래핑한 다음 테스트에서 `-WhatIf`를 이용해 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-186">If I have a piece of logic that is hard to mock in pester, I can often wrap it in `ShouldProcess` and call it with `-WhatIf` in my tests.</span></span> <span data-ttu-id="a2f24-187">코드는 일부라도 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-187">It's better to test some of your code than none of it.</span></span>

### <a name="whatifpreference"></a><span data-ttu-id="a2f24-188">$WhatIfPreference</span><span class="sxs-lookup"><span data-stu-id="a2f24-188">$WhatIfPreference</span></span>

<span data-ttu-id="a2f24-189">우리에게 있는 첫 번째 기본 설정 변수는 `$WhatIfPreference`입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-189">The first preference variable we have is `$WhatIfPreference`.</span></span> <span data-ttu-id="a2f24-190">기본값은 `$false`입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-190">This is `$false` by default.</span></span> <span data-ttu-id="a2f24-191">`$true`로 설정하면 함수는 `-WhatIf`에서 지정한 대로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-191">If you set it to `$true` then your function executes as if you specified `-WhatIf`.</span></span> <span data-ttu-id="a2f24-192">이를 세션에서 설정하면 모든 명령이 `-WhatIf` 실행을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-192">If you set this in your session, all commands perform `-WhatIf` execution.</span></span>

<span data-ttu-id="a2f24-193">`-WhatIf`로 함수를 호출하면 `$WhatIfPreference` 값은 함수 범위 내에서 `$true`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-193">When you call a function with `-WhatIf`, the value of `$WhatIfPreference` gets set to `$true` inside the scope of your function.</span></span>

## <a name="confirmimpact"></a><span data-ttu-id="a2f24-194">ConfirmImpact</span><span class="sxs-lookup"><span data-stu-id="a2f24-194">ConfirmImpact</span></span>

<span data-ttu-id="a2f24-195">제 예제 대부분은 `-WhatIf`를 대상으로 하지만 지금까지 배운 모든 항목은 `-Confirm`를 사용하여 사용자에게 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-195">Most of my examples are for `-WhatIf` but everything so far also works with `-Confirm` to prompt the user.</span></span> <span data-ttu-id="a2f24-196">함수의 `ConfirmImpact`를 높음으로 설정하면 `-Confirm`으로 호출했을 때처럼 사용자에게 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-196">You can set the `ConfirmImpact` of the function to high and it prompts the user as if it was called with `-Confirm`.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param()

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="a2f24-197">이 `Test-ShouldProcess` 호출은 `High`의 영향 때문에 `-Confirm` 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-197">This call to `Test-ShouldProcess` is performing the `-Confirm` action because of the `High` impact.</span></span>

```powershell
PS> Test-ShouldProcess

Confirm
Are you sure you want to perform this action?
Performing the operation "Test-ShouldProcess" on target "TARGET".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y
Some Action
```

<span data-ttu-id="a2f24-198">하지만 사용자에게 메시지를 표시하지 않으면 다른 스크립트에서 사용하기 어렵다는 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-198">The obvious issue is that now it's harder to use in other scripts without prompting the user.</span></span> <span data-ttu-id="a2f24-199">이 경우 `$false`를 `-Confirm`으로 전달하면 메시지를 표시하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-199">In this case, we can pass a `$false` to `-Confirm` to suppress the prompt.</span></span>

```powershell
PS> Test-ShouldProcess -Confirm:$false
Some Action
```

<span data-ttu-id="a2f24-200">`-Force` 지원을 추가하는 방법은 이후 섹션에서 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-200">I'll cover how to add `-Force` support in a later section.</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="a2f24-201">$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="a2f24-201">$ConfirmPreference</span></span>

<span data-ttu-id="a2f24-202">`$ConfirmPreference`는 `ConfirmImpact`에서 실행 확인 메시지를 표시하는 시점을 제어하는 자동 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-202">`$ConfirmPreference` is an automatic variable that controls when `ConfirmImpact` asks you to confirm execution.</span></span> <span data-ttu-id="a2f24-203">다음은 `$ConfirmPreference`와 `ConfirmImpact` 모두에서 사용할 수 있는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-203">Here are the possible values for both `$ConfirmPreference` and `ConfirmImpact`.</span></span>

- `High`
- `Medium`
- `Low`
- `None`

<span data-ttu-id="a2f24-204">이러한 값을 사용하면 각 함수에 다양한 수준의 영향을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-204">With these values, you can specify different levels of impact for each function.</span></span> <span data-ttu-id="a2f24-205">`$ConfirmPreference`를 `ConfirmImpact`보다 높은 값으로 설정하면 실행 확인 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-205">If you have `$ConfirmPreference` set to a value higher than `ConfirmImpact`, then you aren't prompted to confirm execution.</span></span>

<span data-ttu-id="a2f24-206">기본적으로 `$ConfirmPreference`는 `High`로 설정되며 `ConfirmImpact`는 `Medium`입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-206">By default, `$ConfirmPreference` is set to `High` and `ConfirmImpact` is `Medium`.</span></span> <span data-ttu-id="a2f24-207">함수에서 사용자에게 메시지를 자동으로 표시되게 하려면 `ConfirmImpact`를 `High`로 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-207">If you want your function to automatically prompt the user, set your `ConfirmImpact` to `High`.</span></span> <span data-ttu-id="a2f24-208">그렇지 않다면 위험할 때는 `Medium`으로 설정하고 명령이 프로덕션 환경에서 항상 안전하게 실행될 때는 `Low`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-208">Otherwise set it to `Medium` if its destructive and use `Low` if the command is always safe run in production.</span></span> <span data-ttu-id="a2f24-209">`none`으로 설정하면 `-Confirm`을 지정해도 메시지가 표시되지 않습니다(하지만 `-WhatIf` 지원은 계속 제공됩니다).</span><span class="sxs-lookup"><span data-stu-id="a2f24-209">If you set it to `none`, it doesn't prompt even if `-Confirm` was specified (but it still gives you `-WhatIf` support).</span></span>

<span data-ttu-id="a2f24-210">`-Confirm`으로 함수를 호출하면 `$ConfirmPreference` 값은 함수 범위 내에서 `Low`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-210">When calling a function with `-Confirm`, the value of `$ConfirmPreference` gets set to `Low` inside the scope of your function.</span></span>

### <a name="suppressing-nested-confirm-prompts"></a><span data-ttu-id="a2f24-211">중첩된 확인 메시지 표시 안 함</span><span class="sxs-lookup"><span data-stu-id="a2f24-211">Suppressing nested confirm prompts</span></span>

<span data-ttu-id="a2f24-212">`$ConfirmPreference`를 이용하면 호출하는 함수를 기준으로 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-212">The `$ConfirmPreference` can get picked up by functions that you call.</span></span> <span data-ttu-id="a2f24-213">이렇게 하면 확인 메시지를 추가하는 시나리오를 만들 수 있고 호출하는 함수도 사용자에게 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-213">This can create scenarios where you add a confirm prompt and the function you call also prompts the user.</span></span>

<span data-ttu-id="a2f24-214">메시지 표시를 이미 처리했을 때 호출하는 명령에 `-Confirm:$false`를 지정하곤 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-214">What I tend to do is specify `-Confirm:$false` on the commands that I call when I have already handled the prompting.</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(SupportsShouldProcess)]
    param()

    $file = Get-ChildItem './myfile1.txt'
    if($PSCmdlet.ShouldProcess($file.Name)){
        Remove-Item -Path $file.FullName -Confirm:$false
    }
}
```

<span data-ttu-id="a2f24-215">이렇게 하면 이전 경고로 돌아갑니다. `-WhatIf`를 함수에 전달하지 않을 때와 `-Confirm`을 함수에 전달할 때는 미묘한 차이가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-215">This brings us back to an earlier warning: There are nuances as to when `-WhatIf` is not passed to a function and when `-Confirm` passes to a function.</span></span> <span data-ttu-id="a2f24-216">여기에 대해서는 나중에 다시 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-216">I promise I'll get back to this later.</span></span>

## <a name="pscmdletshouldcontinue"></a><span data-ttu-id="a2f24-217">$PSCmdlet.ShouldContinue</span><span class="sxs-lookup"><span data-stu-id="a2f24-217">$PSCmdlet.ShouldContinue</span></span>

<span data-ttu-id="a2f24-218">`ShouldProcess`에서 제공하는 것보다 더 높은 수준의 제어가 필요하다면 `ShouldContinue`를 이용해 메시지를 직접 트리거하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-218">If you need more control than `ShouldProcess` provides, you can trigger the prompt directly with `ShouldContinue`.</span></span> <span data-ttu-id="a2f24-219">`ShouldContinue`는 실행할 때마다 메시지를 표시하기 때문에 `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, `-WhatIf`는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-219">`ShouldContinue` ignores `$ConfirmPreference`, `ConfirmImpact`, `-Confirm`, `$WhatIfPreference`, and `-WhatIf` because it prompts every time it's executed.</span></span>

<span data-ttu-id="a2f24-220">얼핏 보면 `ShouldProcess`는 `ShouldContinue`와 혼동하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-220">At a quick glance, it's easy to confuse `ShouldProcess` and `ShouldContinue`.</span></span> <span data-ttu-id="a2f24-221">저는 `ShouldProcess`를 자주 사용하는데 매개 변수가 `CmdletBinding`의 `SupportsShouldProcess`에서 호출되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-221">I tend to remember to use `ShouldProcess` because the parameter is called `SupportsShouldProcess` in the `CmdletBinding`.</span></span>
<span data-ttu-id="a2f24-222">거의 모든 시나리오에서는 `ShouldProcess`를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-222">You should use `ShouldProcess` in almost every scenario.</span></span> <span data-ttu-id="a2f24-223">그래서 이 방법을 가장 먼저 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-223">That is why I covered that method first.</span></span>

<span data-ttu-id="a2f24-224">실제로 작동하는 `ShouldContinue`를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-224">Let's take a look at `ShouldContinue` in action.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    if($PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="a2f24-225">이것은 옵션이 적은 더 간단한 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-225">This provides us a simpler prompt with fewer options.</span></span>

```powershell
Test-ShouldContinue

Second
TARGET
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="a2f24-226">`ShouldContinue`의 가장 큰 문제는 항상 메시지를 표시하기 때문에 사용자가 상호적으로 실행해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-226">The biggest issue with `ShouldContinue` is that it requires the user to run it interactively because it always prompts the user.</span></span> <span data-ttu-id="a2f24-227">항상 다른 스크립트에서 사용할 수 있는 도구를 이용해 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-227">You should always be building tools that can be used by other scripts.</span></span> <span data-ttu-id="a2f24-228">이 작업을 수행하려면 `-Force`를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-228">The way you do this is by implementing `-Force`.</span></span> <span data-ttu-id="a2f24-229">이 방법은 나중에 다시 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-229">I'll revisit this idea later.</span></span>

### <a name="yes-to-all"></a><span data-ttu-id="a2f24-230">모두 예</span><span class="sxs-lookup"><span data-stu-id="a2f24-230">Yes to all</span></span>

<span data-ttu-id="a2f24-231">이것은 `ShouldProcess`에서는 자동으로 처리되지만 `ShouldContinue`에서는 약간의 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-231">This is automatically handled with `ShouldProcess` but we have to do a little more work for `ShouldContinue`.</span></span> <span data-ttu-id="a2f24-232">논리 제어를 위해 몇 가지 값을 참조로 전달해야 하는 두 번째 메서드 오버로드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-232">There's a second method overload where we have to pass in a few values by reference to control the logic.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param()

    $collection = 1..5
    $yesToAll = $false
    $noToAll = $false

    foreach($target in $collection) {

        $continue = $PSCmdlet.ShouldContinue(
                "TARGET_$target",
                'OPERATION',
                [ref]$yesToAll,
                [ref]$noToAll
            )

        if ($continue){
            Write-Output "Some Action [$target]"
        }
    }
}
```

<span data-ttu-id="a2f24-233">실행 중인 모습을 표시하고자 `foreach` 루프와 컬렉션을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-233">I added a `foreach` loop and a collection to show it in action.</span></span> <span data-ttu-id="a2f24-234">쉽게 읽을 수 있도록 `if` 문에서 `ShouldContinue` 호출을 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-234">I pulled the `ShouldContinue` call out of the `if` statement to make it easier to read.</span></span> <span data-ttu-id="a2f24-235">네 가지 매개 변수로 메서드를 호출하면 읽기가 어려워지기 시작하지만 최대한 깔끔하게 표시하고자 노력했습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-235">Calling a method with four parameters starts to get a little ugly, but I tried to make it look as clean as I could.</span></span>

## <a name="implementing--force"></a><span data-ttu-id="a2f24-236">-Force 구현</span><span class="sxs-lookup"><span data-stu-id="a2f24-236">Implementing -Force</span></span>

<span data-ttu-id="a2f24-237">`ShouldProcess`와 `ShouldContinue`는 서로 다른 방법으로 `-Force`를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-237">`ShouldProcess` and `ShouldContinue` need to implement `-Force` in different ways.</span></span> <span data-ttu-id="a2f24-238">이러한 구현의 어려운 점은 `ShouldProcess`는 언제나 실행해야 하지만 `ShouldContinue`는 `-Force`를 지정했다면 실행하지 않아야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-238">The trick to these implementations is that `ShouldProcess` should always get executed, but `ShouldContinue` should not get executed if `-Force` is specified.</span></span>

### <a name="shouldprocess--force"></a><span data-ttu-id="a2f24-239">ShouldProcess -Force</span><span class="sxs-lookup"><span data-stu-id="a2f24-239">ShouldProcess -Force</span></span>

<span data-ttu-id="a2f24-240">`ConfirmImpact`를 `high`로 설정한다면 사용자는 가장 먼저 `-Force`를 이용해 이를 무시하려 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-240">If you set your `ConfirmImpact` to `high`, the first thing your users are going to try is to suppress it with `-Force`.</span></span> <span data-ttu-id="a2f24-241">가장 먼저 하는 일이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-241">That's the first thing I do anyway.</span></span>

```powershell
Test-ShouldProcess -Force
Error: Test-ShouldProcess: A parameter cannot be found that matches parameter name 'force'.
```

<span data-ttu-id="a2f24-242">`ConfirmImpact` 섹션의 내용을 떠올려보면, 이것은 다음처럼 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-242">If you recall from the `ConfirmImpact` section, they actually need to call it like this:</span></span>

```powershell
Test-ShouldProcess -Confirm:$false
```

<span data-ttu-id="a2f24-243">이 작업을 수행해야 하며 `-Confirm:$false`가 `ShouldContinue`를 무시하지 않는다는 사실을 모르는 사람도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-243">Not everyone realizes they need to do that and `-Confirm:$false` doesn't suppress `ShouldContinue`.</span></span>
<span data-ttu-id="a2f24-244">따라서 사용자의 안전을 위해 `-Force`를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-244">So we should implement `-Force` for the sanity of our users.</span></span> <span data-ttu-id="a2f24-245">이 전체 예제를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="a2f24-245">Take a look at this full example here:</span></span>

```powershell
function Test-ShouldProcess {
    [CmdletBinding(
        SupportsShouldProcess,
        ConfirmImpact = 'High'
    )]
    param(
        [Switch]$Force
    )

    if ($Force -and -not $Confirm){
        $ConfirmPreference = 'None'
    }

    if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="a2f24-246">우리는 자체 `-Force` 스위치를 매개 변수로 추가하고, `CmdletBinding`에 `SupportsShouldProcess`를 추가할 때 사용할 수 있는 `$Confirm` 자동 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-246">We add our own `-Force` switch as a parameter and use the `$Confirm` automatic parameter that is available when adding `SupportsShouldProcess` in the `CmdletBinding`.</span></span>

```powershell
[CmdletBinding(
    SupportsShouldProcess,
    ConfirmImpact = 'High'
)]
param(
    [Switch]$Force
)
```

<span data-ttu-id="a2f24-247">여기서 `-Force`를 집중적으로 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-247">Focusing in on the `-Force` logic here:</span></span>

```powershell
if ($Force -and -not $Confirm){
    $ConfirmPreference = 'None'
}
```

<span data-ttu-id="a2f24-248">사용자가 `-Force`를 지정한다면 우리는 사용자가 `-Confirm`도 지정할 때까지는 확인 메시지를 표시하지 않으려 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-248">If the user specifies `-Force`, we want to suppress the confirm prompt unless they also specify `-Confirm`.</span></span> <span data-ttu-id="a2f24-249">이렇게 하면 사용자는 변경 내용을 적용하면서도 여전히 변경 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-249">This allows a user to force a change but still confirm the change.</span></span> <span data-ttu-id="a2f24-250">그러면 우리는 로컬 범위에 `$ConfirmPreference`를 설정하여 `ShouldProcess` 호출이 이를 발견하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-250">Then we set `$ConfirmPreference` in the local scope where our call to `ShouldProcess` discoverers it.</span></span>

```powershell
if ($PSCmdlet.ShouldProcess('TARGET')){
        Write-Output "Some Action"
    }
```

<span data-ttu-id="a2f24-251">사용자가 `-Force`와 `-WhatIf`를 모두 지정한다면 `-WhatIf`가 우선해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-251">If someone specifies both `-Force` and `-WhatIf`, then `-WhatIf` needs to take priority.</span></span> <span data-ttu-id="a2f24-252">이 방법은 `ShouldProcess` 처리를 유지하는데 `-WhatIf`는 항상 처리되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-252">This approach preserves `-WhatIf` processing because `ShouldProcess` always gets executed.</span></span>

<span data-ttu-id="a2f24-253">`ShouldProcess`가 있는 if 문에 `$Force` 값에 대한 검사를 추가하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-253">Do not add a check for the `$Force` value inside the if statement with the `ShouldProcess`.</span></span> <span data-ttu-id="a2f24-254">이 시나리오에는 안티 패턴에 해당하지만 `ShouldContinue`에 관한 다음 섹션에서 보여드리겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-254">That is an anti-pattern for this specific scenario even though that's what I show you in the next section for `ShouldContinue`.</span></span>

### <a name="shouldcontinue--force"></a><span data-ttu-id="a2f24-255">ShouldContinue -Force</span><span class="sxs-lookup"><span data-stu-id="a2f24-255">ShouldContinue -Force</span></span>

<span data-ttu-id="a2f24-256">이것은 `ShouldContinue`를 사용하여 `-Force`를 구현하는 올바른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-256">This is the correct way to implement `-Force` with `ShouldContinue`.</span></span>

```powershell
function Test-ShouldContinue {
    [CmdletBinding()]
    param(
        [Switch]$Force
    )

    if($Force -or $PSCmdlet.ShouldContinue('TARGET','OPERATION')){
        Write-Output "Some Action"
    }
}
```

<span data-ttu-id="a2f24-257">`$Force`를 `-or` 연산자 왼쪽에 배치하여 먼저 평가받게 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-257">By placing the `$Force` to the left of the `-or` operator, it gets evaluated first.</span></span> <span data-ttu-id="a2f24-258">이런 방식으로 작성하면 `if` 문의 실행을 단축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-258">Writing it this way short circuits the execution of the `if` statement.</span></span> <span data-ttu-id="a2f24-259">`$force`가 `$true`라면 `ShouldContinue`는 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-259">If `$force` is `$true`, then the `ShouldContinue` is not executed.</span></span>

```powershell
PS> Test-ShouldContinue -Force
Some Action
```

<span data-ttu-id="a2f24-260">`ShouldContinue`에서 지원하지 않으므로 이 시나리오에서는 `-Confirm`이나 `-WhatIf`에 대해서는 걱정하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-260">We don't have to worry about `-Confirm` or `-WhatIf` in this scenario because they're not supported by `ShouldContinue`.</span></span> <span data-ttu-id="a2f24-261">따라서 `ShouldProcess`와는 다르게 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-261">This is why it needs to be handled differently than `ShouldProcess`.</span></span>

## <a name="scope-issues"></a><span data-ttu-id="a2f24-262">범위 문제</span><span class="sxs-lookup"><span data-stu-id="a2f24-262">Scope issues</span></span>

<span data-ttu-id="a2f24-263">`-WhatIf`와 `-Confirm` 사용은 함수 내의 모든 요소와 함수가 호출하는 모든 요소에 적용되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-263">Using `-WhatIf` and `-Confirm` are supposed to apply to everything inside your functions and everything they call.</span></span> <span data-ttu-id="a2f24-264">이를 위해 함수의 로컬 범위에서 `$WhatIfPreference`을 `$true`로 설정하거나 `$ConfirmPreference`를 `Low`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-264">They do this by setting `$WhatIfPreference` to `$true` or setting `$ConfirmPreference` to `Low` in the local scope of the function.</span></span> <span data-ttu-id="a2f24-265">다른 함수를 호출하는 경우 `ShouldProcess` 호출은 이러한 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-265">When you call another function, calls to `ShouldProcess` use those values.</span></span>

<span data-ttu-id="a2f24-266">실제로 대부분의 경우에 올바르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-266">This actually works correctly most of the time.</span></span> <span data-ttu-id="a2f24-267">같은 범위에서 기본 제공 cmdlet 또는 함수를 호출한다면 언제나 올바르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-267">Anytime you call built-in cmdlet or a function in your same scope, it works.</span></span> <span data-ttu-id="a2f24-268">콘솔의 스크립트 모듈에 있는 스크립트나 함수를 호출할 때도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-268">It also works when you call a script or a function in a script module from the console.</span></span>

<span data-ttu-id="a2f24-269">제대로 작동하지 않는 경우는 스크립트 또는 스크립트 모듈이 다른 스크립트 모듈에서 함수를 호출할 때입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-269">The one specific place where it doesn't work is when a script or a script module calls a function in another script module.</span></span> <span data-ttu-id="a2f24-270">큰 문제가 아닌 것처럼 보일 수도 있지만 여러분이 생성하거나 PSGallery에서 가져오는 모듈은 대부분 스크립트 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-270">This may not sound like a big problem, but most of the modules you create or pull from the PSGallery are script modules.</span></span>

<span data-ttu-id="a2f24-271">가장 핵심적인 문제는 다른 스크립트 모듈의 함수에서 호출될 때는 스크립트 모듈이 `$WhatIfPreference` 또는 `$ConfirmPreference`(그리고 기타 다양한 요소)의 값을 상속하지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-271">The core issue is that script modules do not inherit the values for `$WhatIfPreference` or `$ConfirmPreference` (and several others) when called from functions in other script modules.</span></span>

<span data-ttu-id="a2f24-272">이를 일반 규칙으로 요약하는 가장 좋은 방법은 이진 모듈에 서는 제대로 작동하지만 스크립트 모듈에서는 그렇지 않을 수도 있다고 정리하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-272">The best way to summarize this as a general rule is that this works correctly for binary modules and never trust it to work for script modules.</span></span> <span data-ttu-id="a2f24-273">확신이 들지 않을 때 우리는 테스트해 보거나 제대로 작동하지 않을 것이라 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-273">If you aren't sure, either test it or just assume it doesn't work correctly.</span></span>

<span data-ttu-id="a2f24-274">개인적으로 이것이 대단히 위험하다고 생각하는데, 고립된 상태에서는 정상적으로 작동하지만 서로 호출하면 정상적으로 작동하지 못하는 여러 모듈에 `-WhatIf` 지원을 추가하는 상황이 발생하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-274">I personally feel this is very dangerous because it creates scenarios where you add `-WhatIf` support to multiple modules that work correctly in isolation, but fail to work correctly when they call each other.</span></span>

<span data-ttu-id="a2f24-275">우리는 GitHub RFC를 이용해 이 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-275">We do have a GitHub RFC working to get this issue fixed.</span></span> <span data-ttu-id="a2f24-276">자세한 내용은 [스크립트 모듈 범위 이상으로 실행 기본 설정 전파][RFC]를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2f24-276">See [Propagate execution preferences beyond script module scope][RFC] for more details.</span></span>

## <a name="in-closing"></a><span data-ttu-id="a2f24-277">맺음말</span><span class="sxs-lookup"><span data-stu-id="a2f24-277">In closing</span></span>

<span data-ttu-id="a2f24-278">사용해야 할 때마다 `ShouldProcess` 사용 방법을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-278">I have to look up how to use `ShouldProcess` every time I need to use it.</span></span> <span data-ttu-id="a2f24-279">`ShouldProcess`를 `ShouldContinue`와 구분하는 데 시간이 오래 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-279">It took me a long time to distinguish `ShouldProcess` from `ShouldContinue`.</span></span> <span data-ttu-id="a2f24-280">사용할 매개 변수를 거의 매번 조회해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-280">I almost always need to look up what parameters to use.</span></span> <span data-ttu-id="a2f24-281">그러니 혼란스러울 때가 있더라도 걱정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-281">So don't worry if you still get confused from time to time.</span></span> <span data-ttu-id="a2f24-282">이 문서는 필요할 때 여기서 참조하실 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-282">This article will be here when you need it.</span></span> <span data-ttu-id="a2f24-283">저도 자주 참조하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-283">I'm sure I will reference it often myself.</span></span>

<span data-ttu-id="a2f24-284">이 게시물이 마음에 든다면 아래 링크를 사용하여 Twitter에서 의견을 공유해 주세요.</span><span class="sxs-lookup"><span data-stu-id="a2f24-284">If you liked this post, please share your thoughts with me on Twitter using the link below.</span></span> <span data-ttu-id="a2f24-285">제 콘텐츠에서 도움을 얻은 사람들의 의견을 언제나 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="a2f24-285">I always like hearing from people that get value from my content.</span></span>

<!-- link references -->
[원래 버전]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[original version]: https://powershellexplained.com/2020-03-15-Powershell-shouldprocess-whatif-confirm-shouldcontinue-everything/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[공통 매개 변수]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[common parameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[해시 테이블에 대해 알고 싶은 모든 것]: everything-about-hashtable.md
[everything you wanted to know about hashtables]: everything-about-hashtable.md
[RFC]: https://github.com/PowerShell/PowerShell-RFC/pull/221#issuecomment-592954839
