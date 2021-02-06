---
description: PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.
Locale: en-US
ms.date: 03/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_experimental_features?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 실험적 기능 정보
ms.openlocfilehash: 82f5ef9838fcbb98e71e362ad00b1ec68f9a9f67
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99605509"
---
# <a name="experimental-features"></a><span data-ttu-id="afea5-103">실험적 기능</span><span class="sxs-lookup"><span data-stu-id="afea5-103">Experimental Features</span></span>

<span data-ttu-id="afea5-104">PowerShell의 실험적 기능 지원에서는 PowerShell 또는 PowerShell 모듈에서 기존의 안정적인 기능과 함께 실험적 기능을 사용할 수 있는 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-104">The Experimental Features support in PowerShell provides a mechanism for experimental features to coexist with existing stable features in PowerShell or PowerShell modules.</span></span>

<span data-ttu-id="afea5-105">실험적 기능은 디자인이 완성되지 않은 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-105">An experimental feature is one where the design is not finalized.</span></span> <span data-ttu-id="afea5-106">사용자는 이 기능을 테스트하고 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-106">The feature is available for users to test and provide feedback.</span></span> <span data-ttu-id="afea5-107">실험적 기능이 완성되면 해당 디자인 변경 내용은 호환성이 손상되는 변경이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-107">Once an experimental feature is finalized, the design changes become breaking changes.</span></span> <span data-ttu-id="afea5-108">이로 인해 중단이 발생할 수 있으므로 실험적 기능은 프로덕션에서 사용하기에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-108">Experimental features aren't intended to be used in production since the changes are allowed to be breaking.</span></span>

<span data-ttu-id="afea5-109">실험적 기능은 기본적으로 사용 하지 않도록 설정 되며 시스템의 사용자 또는 관리자가 명시적으로 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-109">Experimental features are disabled by default and need to be explicitly enabled by the user or administrator of the system.</span></span>

<span data-ttu-id="afea5-110">사용 하도록 설정 된 실험적 기능은 `powershell.config.json` `$PSHOME` 모든 사용자에 대 한의 파일 또는 특정 사용자에 대 한 사용자별 구성 파일에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-110">Enabled experimental features are listed in the `powershell.config.json` file in `$PSHOME` for all users or the user-specific configuration file for a specific user.</span></span>

> [!NOTE]
> <span data-ttu-id="afea5-111">사용자 구성 파일에서 사용 하도록 설정 된 실험적 기능은 시스템 구성 파일에 나열 된 실험적 기능 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-111">Experimental features enabled in the user configuration file take precedence over experimental features listed in the system configuration file.</span></span>

## <a name="the-experimental-attribute"></a><span data-ttu-id="afea5-112">실험적 특성</span><span class="sxs-lookup"><span data-stu-id="afea5-112">The Experimental Attribute</span></span>

<span data-ttu-id="afea5-113">특성을 사용 `Experimental` 하 여 일부 코드를 실험적으로 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-113">Use the `Experimental` attribute to declare some code as experimental.</span></span>

<span data-ttu-id="afea5-114">다음 구문을 사용 하 여 실험적 기능의 `Experimental` 이름을 제공 하는 특성과 실험적 기능을 사용 하도록 설정한 경우 수행할 작업을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-114">Use the following syntax to declare the `Experimental` attribute providing the name of the experimental feature and the action to take if the experimental feature is enabled:</span></span>

```csharp
[Experimental(NameOfExperimentalFeature, ExperimentAction)]
```

<span data-ttu-id="afea5-115">모듈의 경우는 `NameOfExperimentalFeature` 의 형식을 따라야 합니다 `<modulename>.<experimentname>` .</span><span class="sxs-lookup"><span data-stu-id="afea5-115">For modules, the `NameOfExperimentalFeature` must follow the form of `<modulename>.<experimentname>`.</span></span> <span data-ttu-id="afea5-116">`ExperimentAction`매개 변수를 지정 해야 하며 유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-116">The `ExperimentAction` parameter must be specified and the only valid values are:</span></span>

- <span data-ttu-id="afea5-117">`Show` 기능이 사용 되는 경우이 실험적 기능을 표시 하는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-117">`Show` means to show this experimental feature if the feature is enabled</span></span>
- <span data-ttu-id="afea5-118">`Hide` 기능이 사용 되는 경우이 실험적 기능을 숨기는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-118">`Hide` means to hide this experimental feature if the feature is enabled</span></span>

### <a name="declaring-experimental-features-in-modules-written-in-c"></a><span data-ttu-id="afea5-119">C로 작성 된 모듈에서 실험적 기능 선언\#</span><span class="sxs-lookup"><span data-stu-id="afea5-119">Declaring Experimental Features in Modules Written in C\#</span></span>

<span data-ttu-id="afea5-120">실험적 기능 플래그를 사용 하려는 모듈 작성자는 특성을 사용 하 여 cmdlet을 실험적으로 선언할 수 있습니다 `Experimental` .</span><span class="sxs-lookup"><span data-stu-id="afea5-120">Module authors who want to use the Experimental Feature flags can declare a cmdlet as experimental by using the `Experimental` attribute.</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }
```

### <a name="declaring-experimental-features-in-modules-written-in-powershell"></a><span data-ttu-id="afea5-121">PowerShell로 작성 된 모듈에서 실험적 기능 선언</span><span class="sxs-lookup"><span data-stu-id="afea5-121">Declaring Experimental Features in Modules written in PowerShell</span></span>

<span data-ttu-id="afea5-122">PowerShell로 작성 된 모듈은 특성을 사용 `Experimental` 하 여 실험적 cmdlet을 선언할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-122">Module written in PowerShell can also use the `Experimental` attribute to declare experimental cmdlets:</span></span>

```powershell
function Enable-SSHRemoting {
    [Experimental("MyRemoting.PSSSHRemoting", "Show")]
    [CmdletBinding()]
    param()
    ...
}
```

### <a name="mutually-exclusive-experimental-features"></a><span data-ttu-id="afea5-123">상호 배타적인 실험적 기능</span><span class="sxs-lookup"><span data-stu-id="afea5-123">Mutually Exclusive Experimental Features</span></span>

<span data-ttu-id="afea5-124">실험적 기능이 기존 기능 또는 다른 실험적 기능과 함께 공존할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-124">There are cases where an experimental feature cannot co-exist side-by-side with an existing feature or another experimental feature.</span></span>

<span data-ttu-id="afea5-125">예를 들어 기존 cmdlet을 재정의 하는 실험적 cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-125">For example, you can have an experimental cmdlet that overrides an existing cmdlet.</span></span> <span data-ttu-id="afea5-126">두 버전은 나란히 공존할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-126">The two versions can't coexist side by side.</span></span> <span data-ttu-id="afea5-127">설정에는 `ExperimentAction.Hide` 한 번에 두 cmdlet 중 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-127">The `ExperimentAction.Hide` setting allows only one of the two cmdlets to be enabled at one time.</span></span>

<span data-ttu-id="afea5-128">이 예에서는 새 실험적 cmdlet을 만듭니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="afea5-128">In this example, we create a new experimental `Invoke-WebRequest` cmdlet.</span></span>
<span data-ttu-id="afea5-129">`InvokeWebRequestCommand` 실험적이 아닌 구현을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-129">`InvokeWebRequestCommand` contains the non-experimental implementation.</span></span>
<span data-ttu-id="afea5-130">`InvokeWebRequestCommandV2` 에는 cmdlet의 실험적 버전이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-130">`InvokeWebRequestCommandV2` contains the experimental version of the cmdlet.</span></span>

<span data-ttu-id="afea5-131">를 사용 하면 `ExperimentAction.Hide` 한 번에 두 기능 중 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-131">The use of `ExperimentAction.Hide` will allow only one of the two features to be enabled at one time:</span></span>

```csharp
[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Show)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommandV2 : WebCmdletBaseV2 { ... }

[Experimental("MyWebCmdlets.PSWebCmdletV2", ExperimentAction.Hide)]
[Cmdlet(Verbs.Invoke, "WebRequest")]
public class InvokeWebRequestCommand : WebCmdletBase { ... }
```

<span data-ttu-id="afea5-132">`MyWebCmdlets.PSWebCmdletV2`실험적 기능을 사용 하도록 설정 하면 기존 `InvokeWebRequestCommand` 구현이 숨겨지고에서 `InvokeWebRequestCommandV2` 의 구현을 제공 합니다 `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="afea5-132">When the `MyWebCmdlets.PSWebCmdletV2` experimental feature is enabled, the existing `InvokeWebRequestCommand` implementation is hidden and the `InvokeWebRequestCommandV2` provides the implementation of `Invoke-WebRequest`.</span></span>

<span data-ttu-id="afea5-133">이렇게 하면 사용자가 새 cmdlet을 사용 하 여 피드백을 제공 하 고 필요한 경우 실험적이 아닌 버전으로 되돌릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-133">This allows users to try out the new cmdlet and provide feedback then revert to the non-experimental version when needed.</span></span>

### <a name="experimental-parameters-in-cmdlets"></a><span data-ttu-id="afea5-134">Cmdlet의 실험적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="afea5-134">Experimental Parameters in Cmdlets</span></span>

<span data-ttu-id="afea5-135">`Experimental`특성은 개별 매개 변수에도 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-135">The `Experimental` attribute can also be applied to individual parameters.</span></span> <span data-ttu-id="afea5-136">이를 통해 완전히 새로운 cmdlet이 아닌 기존 cmdlet에 대 한 실험 매개 변수 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-136">This allows you to create an experimental set of parameters for an existing cmdlet rather than an entirely new cmdlet.</span></span>

<span data-ttu-id="afea5-137">C #의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-137">Here is an example in C#:</span></span>

```csharp
[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Show)]
[Parameter(ParameterSet = "NewCompilation")]
public CompilationParameters CompileParameters { ... }

[Experimental("MyModule.PSNewAddTypeCompilation", ExperimentAction.Hide)]
[Parameter()]
public CodeDom CodeDom { ... }
```

<span data-ttu-id="afea5-138">PowerShell 스크립트의 다른 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-138">Here is a different example in PowerShell script:</span></span>

```powershell
param(
    [Experimental("MyModule.PSNewFeature", "Show")]
    [string] $NewName,

    [Experimental("MyModule.PSNewFeature", "Hide")]
    [string] $OldName
)
```

## <a name="checking-if-an-experimental-feature-is-enabled"></a><span data-ttu-id="afea5-139">실험적 기능이 활성화 되어 있는지 확인 하는 중</span><span class="sxs-lookup"><span data-stu-id="afea5-139">Checking if an Experimental Feature is Enabled</span></span>

<span data-ttu-id="afea5-140">코드에서 적절 한 작업을 수행 하기 전에 실험적 기능을 사용할 수 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-140">In your code, you will need to check if your experimental feature is enabled before taking appropriate action.</span></span> <span data-ttu-id="afea5-141">클래스의 정적 메서드를 사용 하 여 실험적 기능을 사용할 수 있는지 확인할 수 있습니다 `IsEnabled()` `System.Management.Automation.ExperimentalFeature` .</span><span class="sxs-lookup"><span data-stu-id="afea5-141">You can determine if an experimental feature is enabled using the static `IsEnabled()` method on the `System.Management.Automation.ExperimentalFeature` class.</span></span>

<span data-ttu-id="afea5-142">C #의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-142">Here is an example in C#:</span></span>

```csharp
if (ExperimentalFeature.IsEnabled("MyModule.MyExperimentalFeature"))
{
   // code specific to the experimental feature
}
```

<span data-ttu-id="afea5-143">PowerShell 스크립트의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="afea5-143">Here is an example in PowerShell script:</span></span>

```powershell
if ([ExperimentalFeature]::IsEnabled("MyModule.MyExperimentalFeature"))
{
  # code specific to the experimental feature
}
```

## <a name="see-also"></a><span data-ttu-id="afea5-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="afea5-144">See also</span></span>

[<span data-ttu-id="afea5-145">Enable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="afea5-145">Enable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Enable-ExperimentalFeature)

[<span data-ttu-id="afea5-146">Disable-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="afea5-146">Disable-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Disable-ExperimentalFeature)

[<span data-ttu-id="afea5-147">Get-ExperimentalFeature</span><span class="sxs-lookup"><span data-stu-id="afea5-147">Get-ExperimentalFeature</span></span>](xref:Microsoft.PowerShell.Core.Get-ExperimentalFeature)

