---
description: PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 실험적 기능 정보
ms.openlocfilehash: e53af155c2a8691e2e4d4cc6f47bfd5932801db9
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223865"
---
# <a name="experimental-features"></a><span data-ttu-id="a20f0-104">실험적 기능</span><span class="sxs-lookup"><span data-stu-id="a20f0-104">Experimental Features</span></span>

<span data-ttu-id="a20f0-105">PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-105">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="a20f0-106">실험적 기능은 디자인이 완성되지 않은 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-106">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="a20f0-107">사용자는 이 기능을 테스트하고 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-107">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="a20f0-108">실험적 기능이 완성되면 해당 디자인 변경 내용은 호환성이 손상되는 변경이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-108">Once an experimental feature is finalized, the design changes become breaking changes.</span></span> <span data-ttu-id="a20f0-109">이로 인해 중단이 발생할 수 있으므로 실험적 기능은 프로덕션에서 사용하기에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-109">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span>

<span data-ttu-id="a20f0-110">실험적 기능은 기본적으로 사용 하지 않도록 설정 되며 시스템의 사용자 또는 관리자가 명시적으로 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-110">Experimental features are disabled by default and need to be explicitly enabled by the user or administrator of the system.</span></span>

<span data-ttu-id="a20f0-111">사용 하도록 설정 된 실험적 기능은 `powershell.config.json` `$PSHOME` 모든 사용자에 대 한의 파일 또는 특정 사용자에 대 한 사용자별 구성 파일에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-111">Enabled experimental features are listed in the `powershell.config.json` file in `$PSHOME` for all users or the user-specific configuration file for a specific user.</span></span>

> [!NOTE]
> <span data-ttu-id="a20f0-112">사용자 구성 파일에서 사용 하도록 설정 된 실험적 기능은 시스템 구성 파일에 나열 된 실험적 기능 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-112">Experimental features enabled in the user configuration file take precedence over experimental features listed in the system configuration file.</span></span>

## <a name="the-experimental-attribute"></a><span data-ttu-id="a20f0-113">실험적 특성</span><span class="sxs-lookup"><span data-stu-id="a20f0-113">The Experimental Attribute</span></span>

<span data-ttu-id="a20f0-114">특성을 사용 `Experimental` 하 여 일부 코드를 실험적으로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-114">Use the `Experimental` attribute to declare some code as experimental.</span></span>

<span data-ttu-id="a20f0-115">다음 구문을 사용 하 여 실험적 기능의 `Experimental` 이름을 제공 하는 특성과 실험적 기능을 사용 하도록 설정한 경우 수행할 작업을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-115">Use the following syntax to declare the `Experimental` attribute providing the name of the experimental feature and the action to take if the experimental feature is enabled:</span></span>

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

<span data-ttu-id="a20f0-116">모듈의 경우는 `NameOfExperimentalFeature` 의 형식을 따라야 합니다 `<modulename>.<experimentname>` .</span><span class="sxs-lookup"><span data-stu-id="a20f0-116">For modules, the `NameOfExperimentalFeature` must follow the form of `<modulename>.<experimentname>`.</span></span> <span data-ttu-id="a20f0-117">`ExperimentAction`매개 변수를 지정 해야 하며 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-117">The `ExperimentAction` parameter must be specified and the only valid values are:</span></span>

- <span data-ttu-id="a20f0-118">`Show` 기능이 사용 되는 경우이 실험적 기능을 표시 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-118">`Show` means to show this experimental feature if the feature is enabled</span></span>
- <span data-ttu-id="a20f0-119">`Hide` 기능이 사용 되는 경우이 실험적 기능을 숨기는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-119">`Hide` means to hide this experimental feature if the feature is enabled</span></span>

### <a name="declaring-experimental-features-in-modules-written-in-c"></a><span data-ttu-id="a20f0-120">C로 작성 된 모듈에서 실험적 기능 선언\#</span><span class="sxs-lookup"><span data-stu-id="a20f0-120">Declaring Experimental Features in Modules Written in C\#</span></span>

<span data-ttu-id="a20f0-121">실험적 기능 플래그를 사용 하려는 모듈 작성자는 특성을 사용 하 여 cmdlet을 실험적으로 선언할 수 있습니다 `Experimental` .</span><span class="sxs-lookup"><span data-stu-id="a20f0-121">Module authors who want to use the Experimental Feature flags can declare a cmdlet as experimental by using the `Experimental` attribute.</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a><span data-ttu-id="a20f0-122">PowerShell로 작성 된 모듈에서 실험적 기능 선언</span><span class="sxs-lookup"><span data-stu-id="a20f0-122">Declaring Experimental Features in Modules written in PowerShell</span></span>

<span data-ttu-id="a20f0-123">PowerShell로 작성 된 모듈은 특성을 사용 `Experimental` 하 여 실험적 cmdlet을 선언할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-123">Module written in PowerShell can also use the `Experimental` attribute to declare experimental cmdlets:</span></span>

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a><span data-ttu-id="a20f0-124">상호 배타적인 실험적 기능</span><span class="sxs-lookup"><span data-stu-id="a20f0-124">Mutually Exclusive Experimental Features</span></span>

<span data-ttu-id="a20f0-125">실험적 기능이 기존 기능 또는 다른 실험적 기능과 함께 공존할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-125">There are cases where an experimental feature cannot co-exist side-by-side with an existing feature or another experimental feature.</span></span>

<span data-ttu-id="a20f0-126">예를 들어 기존 cmdlet을 재정의 하는 실험적 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-126">For example, you can have an experimental cmdlet that overrides an existing cmdlet.</span></span> <span data-ttu-id="a20f0-127">두 버전은 나란히 공존할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-127">The two versions can't coexist side by side.</span></span> <span data-ttu-id="a20f0-128">설정에는 `ExperimentAction.Hide` 한 번에 두 cmdlet 중 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-128">The `ExperimentAction.Hide` setting allows only one of the two cmdlets to be enabled at one time.</span></span>

<span data-ttu-id="a20f0-129">이 예에서는 새 실험적 cmdlet을 만듭니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="a20f0-129">In this example, we create a new experimental `Invoke-WebRequest` cmdlet.</span></span>
<span data-ttu-id="a20f0-130">`InvokeWebRequestCommand` 실험적이 아닌 구현을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-130">`InvokeWebRequestCommand` contains the non-experimental implementation.</span></span>
<span data-ttu-id="a20f0-131">`InvokeWebRequestCommandV2` 에는 cmdlet의 실험적 버전이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-131">`InvokeWebRequestCommandV2` contains the experimental version of the cmdlet.</span></span>

<span data-ttu-id="a20f0-132">를 사용 하면 `ExperimentAction.Hide` 한 번에 두 기능 중 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-132">The use of `ExperimentAction.Hide` will allow only one of the two features to be enabled at one time:</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

<span data-ttu-id="a20f0-133">`MyWebCmdlets.PSWebCmdletV2`실험적 기능을 사용 하도록 설정 하면 기존 `InvokeWebRequestCommand` 구현이 숨겨지고에서 `InvokeWebRequestCommandV2` 의 구현을 제공 합니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="a20f0-133">When the `MyWebCmdlets.PSWebCmdletV2` experimental feature is enabled, the existing `InvokeWebRequestCommand` implementation is hidden and the `InvokeWebRequestCommandV2` provides the implementation of `Invoke-WebRequest`.</span></span>

<span data-ttu-id="a20f0-134">이렇게 하면 사용자가 새 cmdlet을 사용 하 여 피드백을 제공 하 고 필요한 경우 실험적이 아닌 버전으로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-134">This allows users to try out the new cmdlet and provide feedback then revert to the non-experimental version when needed.</span></span>

### <a name="experimental-parameters-in-cmdlets"></a><span data-ttu-id="a20f0-135">Cmdlet의 실험적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a20f0-135">Experimental Parameters in Cmdlets</span></span>

<span data-ttu-id="a20f0-136">`Experimental`특성은 개별 매개 변수에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-136">The `Experimental` attribute can also be applied to individual parameters.</span></span> <span data-ttu-id="a20f0-137">이를 통해 완전히 새로운 cmdlet이 아닌 기존 cmdlet에 대 한 실험 매개 변수 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-137">This allows you to create an experimental set of parameters for an existing cmdlet rather than an entirely new cmdlet.</span></span>

<span data-ttu-id="a20f0-138">C #의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-138">Here is an example in C#:</span></span>

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

<span data-ttu-id="a20f0-139">PowerShell 스크립트의 다른 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-139">Here is a different example in PowerShell script:</span></span>

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a><span data-ttu-id="a20f0-140">실험적 기능이 활성화 되어 있는지 확인 하는 중</span><span class="sxs-lookup"><span data-stu-id="a20f0-140">Checking if an Experimental Feature is Enabled</span></span>

<span data-ttu-id="a20f0-141">코드에서 적절 한 작업을 수행 하기 전에 실험적 기능을 사용할 수 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-141">In your code, you will need to check if your experimental feature is enabled before taking appropriate action.</span></span> <span data-ttu-id="a20f0-142">클래스의 정적 메서드를 사용 하 여 실험적 기능을 사용할 수 있는지 확인할 수 있습니다 `IsEnabled()` `System.Management.Automation.ExperimentalFeature` .</span><span class="sxs-lookup"><span data-stu-id="a20f0-142">You can determine if an experimental feature is enabled using the static `IsEnabled()` method on the `System.Management.Automation.ExperimentalFeature` class.</span></span>

<span data-ttu-id="a20f0-143">C #의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-143">Here is an example in C#:</span></span>

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

<span data-ttu-id="a20f0-144">PowerShell 스크립트의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a20f0-144">Here is an example in PowerShell script:</span></span>

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a><span data-ttu-id="a20f0-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a20f0-145">See also</span></span>

[<span data-ttu-id="a20f0-146">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="a20f0-146">Enable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[<span data-ttu-id="a20f0-147">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="a20f0-147">Disable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[<span data-ttu-id="a20f0-148">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="a20f0-148">Get-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)
