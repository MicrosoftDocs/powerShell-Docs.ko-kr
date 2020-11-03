---
description: PowerShell의 동작을 사용자 지정 하는 변수입니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_preference_variables?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Preference_Variables
ms.openlocfilehash: 6f23e016131901ed78b223a4d23dfa12416d970b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221370"
---
# <a name="about-preference-variables"></a><span data-ttu-id="ff9cf-104">기본 설정 변수 정보</span><span class="sxs-lookup"><span data-stu-id="ff9cf-104">About Preference Variables</span></span>

## <a name="short-description"></a><span data-ttu-id="ff9cf-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ff9cf-105">Short description</span></span>

<span data-ttu-id="ff9cf-106">PowerShell의 동작을 사용자 지정 하는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-106">Variables that customize the behavior of PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ff9cf-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-107">Long description</span></span>

<span data-ttu-id="ff9cf-108">PowerShell에는 해당 동작을 사용자 지정할 수 있는 변수 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-108">PowerShell includes a set of variables that enable you to customize its behavior.</span></span> <span data-ttu-id="ff9cf-109">이러한 기본 설정 변수는 GUI 기반 시스템의 옵션과 같은 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-109">These preference variables work like the options in GUI-based systems.</span></span>

<span data-ttu-id="ff9cf-110">기본 설정 변수는 PowerShell 운영 환경 및 환경에서 실행 되는 모든 명령에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-110">The preference variables affect the PowerShell operating environment and all commands run in the environment.</span></span> <span data-ttu-id="ff9cf-111">대부분의 경우 cmdlet에는 특정 명령의 기본 설정 동작을 재정의 하는 데 사용할 수 있는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-111">In many cases, the cmdlets have parameters that you can use to override the preference behavior for a specific command.</span></span>

<span data-ttu-id="ff9cf-112">다음 표에서는 기본 설정 변수와 해당 기본값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-112">The following table lists the preference variables and their default values.</span></span>

|             <span data-ttu-id="ff9cf-113">변수</span><span class="sxs-lookup"><span data-stu-id="ff9cf-113">Variable</span></span>             |       <span data-ttu-id="ff9cf-114">기본값</span><span class="sxs-lookup"><span data-stu-id="ff9cf-114">Default Value</span></span>       |
| -------------------------------- | ------------------------- |
| `$ConfirmPreference`             | <span data-ttu-id="ff9cf-115">높음</span><span class="sxs-lookup"><span data-stu-id="ff9cf-115">High</span></span>                      |
| `$DebugPreference`               | <span data-ttu-id="ff9cf-116">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="ff9cf-116">SilentlyContinue</span></span>          |
| `$ErrorActionPreference`         | <span data-ttu-id="ff9cf-117">계속</span><span class="sxs-lookup"><span data-stu-id="ff9cf-117">Continue</span></span>                  |
| `$ErrorView`                     | <span data-ttu-id="ff9cf-118">NormalView</span><span class="sxs-lookup"><span data-stu-id="ff9cf-118">NormalView</span></span>                |
| `$FormatEnumerationLimit`        | <span data-ttu-id="ff9cf-119">4</span><span class="sxs-lookup"><span data-stu-id="ff9cf-119">4</span></span>                         |
| `$InformationPreference`         | <span data-ttu-id="ff9cf-120">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="ff9cf-120">SilentlyContinue</span></span>          |
| `$LogCommandHealthEvent`         | <span data-ttu-id="ff9cf-121">False (로깅되지 않음)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-121">False (not logged)</span></span>        |
| `$LogCommandLifecycleEvent`      | <span data-ttu-id="ff9cf-122">False (로깅되지 않음)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-122">False (not logged)</span></span>        |
| `$LogEngineHealthEvent`          | <span data-ttu-id="ff9cf-123">True (기록 됨)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-123">True (logged)</span></span>             |
| `$LogEngineLifecycleEvent`       | <span data-ttu-id="ff9cf-124">True (기록 됨)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-124">True (logged)</span></span>             |
| `$LogProviderLifecycleEvent`     | <span data-ttu-id="ff9cf-125">True (기록 됨)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-125">True (logged)</span></span>             |
| `$LogProviderHealthEvent`        | <span data-ttu-id="ff9cf-126">True (기록 됨)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-126">True (logged)</span></span>             |
| `$MaximumHistoryCount`           | <span data-ttu-id="ff9cf-127">4096</span><span class="sxs-lookup"><span data-stu-id="ff9cf-127">4096</span></span>                      |
| `$OFS`                           | <span data-ttu-id="ff9cf-128">(공백 문자 ( `" "` ))</span><span class="sxs-lookup"><span data-stu-id="ff9cf-128">(Space character (`" "`))</span></span> |
| `$OutputEncoding`                | <span data-ttu-id="ff9cf-129">**UTF8Encoding** 개체</span><span class="sxs-lookup"><span data-stu-id="ff9cf-129">**UTF8Encoding** object</span></span>   |
| `$ProgressPreference`            | <span data-ttu-id="ff9cf-130">계속</span><span class="sxs-lookup"><span data-stu-id="ff9cf-130">Continue</span></span>                  |
| `$PSDefaultParameterValues`      | <span data-ttu-id="ff9cf-131">(없음-빈 해시 테이블)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-131">(None - empty hash table)</span></span> |
| `$PSEmailServer`                 | <span data-ttu-id="ff9cf-132">(없음)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-132">(None)</span></span>                    |
| `$PSModuleAutoLoadingPreference` | <span data-ttu-id="ff9cf-133">모두</span><span class="sxs-lookup"><span data-stu-id="ff9cf-133">All</span></span>                       |
| `$PSSessionApplicationName`      | <span data-ttu-id="ff9cf-134">wsman</span><span class="sxs-lookup"><span data-stu-id="ff9cf-134">wsman</span></span>                     |
| `$PSSessionConfigurationName`    | `http://schemas.microsoft.com/powershell/Microsoft.PowerShell` |
| `$PSSessionOption`               | <span data-ttu-id="ff9cf-135">[$PSSessionOption](#pssessionoption) 참조</span><span class="sxs-lookup"><span data-stu-id="ff9cf-135">See [$PSSessionOption](#pssessionoption)</span></span> |
| `$Transcript`                    | <span data-ttu-id="ff9cf-136">(없음)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-136">(none)</span></span>                    |
| `$VerbosePreference`             | <span data-ttu-id="ff9cf-137">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="ff9cf-137">SilentlyContinue</span></span>          |
| `$WarningPreference`             | <span data-ttu-id="ff9cf-138">계속</span><span class="sxs-lookup"><span data-stu-id="ff9cf-138">Continue</span></span>                  |
| `$WhatIfPreference`              | <span data-ttu-id="ff9cf-139">거짓</span><span class="sxs-lookup"><span data-stu-id="ff9cf-139">False</span></span>                     |

<span data-ttu-id="ff9cf-140">PowerShell은 사용자 기본 설정을 저장 하는 다음과 같은 환경 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-140">PowerShell includes the following environment variables that store user preferences.</span></span> <span data-ttu-id="ff9cf-141">이러한 환경 변수에 대 한 자세한 내용은 [about_Environment_Variables](about_Environment_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-141">For more information about these environment variables, see [about_Environment_Variables](about_Environment_Variables.md).</span></span>

- `env:PSExecutionPolicyPreference`
- `$env:PSModulePath`

> [!NOTE]
> <span data-ttu-id="ff9cf-142">기본 설정 변수에 대 한 변경 내용은 해당 스크립트나 함수가 기본 설정이 사용 된 범위와 동일한 범위에서 정의 된 경우에만 스크립트 및 함수에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-142">Changes to preference variable only take effect in scripts and functions if those scripts or functions are defined in the same scope as the scope in which preference was used.</span></span> <span data-ttu-id="ff9cf-143">자세한 내용은 [about_Scopes](about_Scopes.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-143">For more information, see [about_Scopes](about_Scopes.md).</span></span>

## <a name="working-with-preference-variables"></a><span data-ttu-id="ff9cf-144">기본 설정 변수 작업</span><span class="sxs-lookup"><span data-stu-id="ff9cf-144">Working with preference variables</span></span>

<span data-ttu-id="ff9cf-145">이 문서에서는 각 기본 설정 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-145">This document describes each of the preference variables.</span></span>

<span data-ttu-id="ff9cf-146">특정 기본 설정 변수의 현재 값을 표시 하려면 변수의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-146">To display the current value of a specific preference variable, type the variable's name.</span></span> <span data-ttu-id="ff9cf-147">예를 들어 다음 명령은 변수의 값을 표시 합니다 `$ConfirmPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-147">For example, the following command displays the `$ConfirmPreference` variable's value.</span></span>

```powershell
 $ConfirmPreference
```

```Output
High
```

<span data-ttu-id="ff9cf-148">변수의 값을 변경 하려면 대입문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-148">To change a variable's value, use an assignment statement.</span></span> <span data-ttu-id="ff9cf-149">예를 들어 다음 문은 `$ConfirmPreference` 매개 변수의 값을 **Medium** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-149">For example, the following statement changes the `$ConfirmPreference` parameter's value to **Medium**.</span></span>

```powershell
$ConfirmPreference = "Medium"
```

<span data-ttu-id="ff9cf-150">사용자가 설정 하는 값은 현재 PowerShell 세션에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-150">The values that you set are specific to the current PowerShell session.</span></span> <span data-ttu-id="ff9cf-151">모든 PowerShell 세션에서 변수를 유효 하 게 만들려면 PowerShell 프로필에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-151">To make variables effective in all PowerShell sessions, add them to your PowerShell profile.</span></span> <span data-ttu-id="ff9cf-152">자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-152">For more information, see [about_Profiles](about_Profiles.md).</span></span>

## <a name="working-remotely"></a><span data-ttu-id="ff9cf-153">원격으로 작업</span><span class="sxs-lookup"><span data-stu-id="ff9cf-153">Working remotely</span></span>

<span data-ttu-id="ff9cf-154">원격 컴퓨터에서 명령을 실행 하는 경우 원격 명령은 원격 컴퓨터의 PowerShell 클라이언트에 설정 된 기본 설정에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-154">When you run commands on a remote computer, the remote commands are only subject to the preferences set in the remote computer's PowerShell client.</span></span> <span data-ttu-id="ff9cf-155">예를 들어 원격 명령을 실행 하는 경우 원격 컴퓨터의 변수 값은 PowerShell에서 `$DebugPreference` 디버깅 메시지에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-155">For example, when you run a remote command, the value of the remote computer's `$DebugPreference` variable determines how PowerShell responds to debugging messages.</span></span>

<span data-ttu-id="ff9cf-156">원격 명령에 대 한 자세한 내용은 [about_Remote](about_Remote.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-156">For more information about remote commands, see [about_Remote](about_Remote.md).</span></span>

### <a name="confirmpreference"></a><span data-ttu-id="ff9cf-157">\$ConfirmPreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-157">\$ConfirmPreference</span></span>

<span data-ttu-id="ff9cf-158">Cmdlet 또는 함수를 실행 하기 전에 PowerShell에서 자동으로 확인 메시지를 표시할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-158">Determines whether PowerShell automatically prompts you for confirmation before running a cmdlet or function.</span></span>

<span data-ttu-id="ff9cf-159">`$ConfirmPreference`변수의 유효한 값은 **높음** , **보통** 또는 **낮음** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-159">The `$ConfirmPreference` variable's valid values are **High** , **Medium** , or **Low**.</span></span> <span data-ttu-id="ff9cf-160">Cmdlet 및 함수에는 **높음** , **중간** 또는 **낮음** 의 위험이 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-160">Cmdlets and functions are assigned a risk of **High** , **Medium** , or **Low**.</span></span> <span data-ttu-id="ff9cf-161">`$ConfirmPreference`변수 값이 cmdlet 또는 함수에 할당 된 위험 보다 작거나 같으면 PowerShell에서 cmdlet 또는 함수를 실행 하기 전에 확인 메시지를 자동으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-161">When the value of the `$ConfirmPreference` variable is less than or equal to the risk assigned to a cmdlet or function, PowerShell automatically prompts you for confirmation before running the cmdlet or function.</span></span>

<span data-ttu-id="ff9cf-162">`$ConfirmPreference`변수 값이 **None** 이면 PowerShell에서 cmdlet 또는 함수를 실행 하기 전에 자동으로 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-162">If the value of the `$ConfirmPreference` variable is **None** , PowerShell never automatically prompts you before running a cmdlet or function.</span></span>

<span data-ttu-id="ff9cf-163">세션의 모든 cmdlet 및 함수에 대 한 확인 동작을 변경 하려면 `$ConfirmPreference` 변수의 값을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-163">To change the confirming behavior for all cmdlets and functions in the session, change `$ConfirmPreference` variable's value.</span></span>

<span data-ttu-id="ff9cf-164">`$ConfirmPreference`단일 명령에 대 한를 재정의 하려면 cmdlet의 또는 함수의 **Confirm** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-164">To override the `$ConfirmPreference` for a single command, use a cmdlet's or function's **Confirm** parameter.</span></span> <span data-ttu-id="ff9cf-165">확인을 요청 하려면를 사용 `-Confirm` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-165">To request confirmation, use `-Confirm`.</span></span> <span data-ttu-id="ff9cf-166">확인을 표시 하지 않으려면를 사용 `-Confirm:$false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-166">To suppress confirmation, use `-Confirm:$false`.</span></span>

<span data-ttu-id="ff9cf-167">유효한 값 `$ConfirmPreference` :</span><span class="sxs-lookup"><span data-stu-id="ff9cf-167">Valid values of `$ConfirmPreference`:</span></span>

- <span data-ttu-id="ff9cf-168">**없음** : PowerShell에서 자동으로 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-168">**None** : PowerShell doesn't prompt automatically.</span></span> <span data-ttu-id="ff9cf-169">특정 명령에 대 한 확인을 요청 하려면 cmdlet 또는 함수의 **Confirm** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-169">To request confirmation of a particular command, use the **Confirm** parameter of the cmdlet or function.</span></span>
- <span data-ttu-id="ff9cf-170">**낮음** : PowerShell을 실행 하기 전에 확인 메시지를 표시 하거나 낮음, 중간 또는 높은 위험으로 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-170">**Low** : PowerShell prompts for confirmation before running cmdlets or functions with a low, medium, or high risk.</span></span>
- <span data-ttu-id="ff9cf-171">**보통** : PowerShell에서 중간 또는 높은 위험으로 cmdlet 또는 함수를 실행 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-171">**Medium** : PowerShell prompts for confirmation before running cmdlets or functions with a medium, or high risk.</span></span>
- <span data-ttu-id="ff9cf-172">**High** : cmdlet을 실행 하기 전에 PowerShell에서 확인 메시지를 표시 하거나 높은 위험 수준으로 함수를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-172">**High** : PowerShell prompts for confirmation before running cmdlets or functions with a high risk.</span></span>

#### <a name="detailed-explanation"></a><span data-ttu-id="ff9cf-173">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ff9cf-173">Detailed explanation</span></span>

<span data-ttu-id="ff9cf-174">PowerShell에서 작업을 수행 하기 전에 확인 메시지를 자동으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-174">PowerShell can automatically prompt you for confirmation before doing an action.</span></span> <span data-ttu-id="ff9cf-175">예를 들어 cmdlet 또는 함수가 시스템에서 데이터를 삭제 하거나 많은 양의 시스템 리소스를 사용 하는 데 상당한 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-175">For example, when cmdlet or function significantly affects the system to delete data or use a significant amount of system resources.</span></span>

```powershell
Remove-Item -Path C:\file.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\file.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"):
```

<span data-ttu-id="ff9cf-176">위험도의 예측은 해당 기능에 **영향을 주는** cmdlet 또는 함수의 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-176">The estimate of the risk is an attribute of the cmdlet or function known as its **ConfirmImpact**.</span></span> <span data-ttu-id="ff9cf-177">이 설정은 사용자가 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-177">Users can't change it.</span></span>

<span data-ttu-id="ff9cf-178">시스템에 위험을 초래할 수 있는 cmdlet 및 함수에는 단일 명령에 대 한 확인을 요청 하거나 표시 하지 않는 **확인** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-178">Cmdlets and functions that might pose a risk to the system have a **Confirm** parameter that you can use to request or suppress confirmation for a single command.</span></span>

<span data-ttu-id="ff9cf-179">대부분의 cmdlet 및 함수는 기본 위험 값을 사용 하기 때문에 **중간** 의 기능 및 **기본값을 사용** 하므로 `$ConfirmPreference` 자동 **High** 확인이 거의 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-179">Because most cmdlets and functions use the default risk value, **ConfirmImpact** , of **Medium** , and the default value of `$ConfirmPreference` is **High** , automatic confirmation rarely occurs.</span></span> <span data-ttu-id="ff9cf-180">그러나의 값을 `$ConfirmPreference` **보통** 또는 **낮음** 으로 변경 하 여 자동 확인을 활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-180">However, you can activate automatic confirmation by changing the value of `$ConfirmPreference` to **Medium** or **Low**.</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-181">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-181">Examples</span></span>

<span data-ttu-id="ff9cf-182">이 예에서는 `$ConfirmPreference` 변수의 기본값 **높음** 이 미치는 영향을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-182">This example shows the effect of the `$ConfirmPreference` variable's default value, **High**.</span></span> <span data-ttu-id="ff9cf-183">**높은** 값은 높은 위험 수준의 cmdlet 및 함수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-183">The **High** value only confirms high-risk cmdlets and functions.</span></span> <span data-ttu-id="ff9cf-184">대부분의 cmdlet과 함수는 보통 위험 하므로 자동으로 확인 되 고 `Remove-Item` 파일을 삭제 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-184">Since most cmdlets and functions are medium risk, they aren't automatically confirmed and `Remove-Item` deletes the file.</span></span> <span data-ttu-id="ff9cf-185">`-Confirm`명령에를 추가 하면 사용자에 게 확인 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-185">Adding `-Confirm` to the command prompts the user for confirmation.</span></span>

```powershell
$ConfirmPreference
```

```Output
High
```

```powershell
Remove-Item -Path C:\temp1.txt
```

<span data-ttu-id="ff9cf-186">`-Confirm`확인을 요청 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-186">Use `-Confirm` to request confirmation.</span></span>

```powershell
Remove-Item -Path C:\temp2.txt -Confirm
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

<span data-ttu-id="ff9cf-187">다음 예에서는의 값을 보통으로 변경 하는 경우의 효과를 보여 줍니다 `$ConfirmPreference` . **Medium**</span><span class="sxs-lookup"><span data-stu-id="ff9cf-187">The following example shows the effect of changing the value of `$ConfirmPreference` to **Medium**.</span></span> <span data-ttu-id="ff9cf-188">대부분의 cmdlet과 함수는 보통 위험 하므로 자동으로 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-188">Because most cmdlets and function are medium risk, they're automatically confirmed.</span></span> <span data-ttu-id="ff9cf-189">단일 명령에 대 한 확인 메시지를 표시 하지 않으려면 **Confirm** 매개 변수를 값으로 사용 `$false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-189">To suppress the confirmation prompt for a single command, use the **Confirm** parameter with a value of `$false`.</span></span>

```powershell
$ConfirmPreference = "Medium"
Remove-Item -Path C:\temp2.txt
```

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target "C:\temp2.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All
[?] Help (default is "Y"):
```

```powershell
Remove-Item -Path C:\temp3.txt -Confirm:$false
```

### <a name="debugpreference"></a><span data-ttu-id="ff9cf-190">\$DebugPreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-190">\$DebugPreference</span></span>

<span data-ttu-id="ff9cf-191">PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 디버깅 메시지에 응답 하는 방법 또는 명령줄에서 명령을 통해 응답 하는 방법을 결정 합니다 `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-191">Determines how PowerShell responds to debugging messages generated by a script, cmdlet or provider, or by a `Write-Debug` command at the command line.</span></span>

<span data-ttu-id="ff9cf-192">일부 cmdlet은 프로그래머 및 기술 지원 전문가 용으로 설계 된 기술 메시지를 표시 하는 디버깅 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-192">Some cmdlets display debugging messages, which are typically technical messages designed for programmers and technical support professionals.</span></span> <span data-ttu-id="ff9cf-193">기본적으로 디버깅 메시지는 표시 되지 않지만의 값을 변경 하 여 디버깅 메시지를 표시할 수 있습니다 `$DebugPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-193">By default, debugging messages aren't displayed, but you can display debugging messages by changing the value of `$DebugPreference`.</span></span>

<span data-ttu-id="ff9cf-194">Cmdlet의 **Debug** 일반 매개 변수를 사용 하 여 특정 명령에 대 한 디버깅 메시지를 표시 하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-194">You can use the **Debug** common parameter of a cmdlet to display or hide the debugging messages for a specific command.</span></span> <span data-ttu-id="ff9cf-195">자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-195">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="ff9cf-196">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-196">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-197">**Stop** : 디버그 메시지를 표시 하 고 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-197">**Stop** : Displays the debug message and stops executing.</span></span> <span data-ttu-id="ff9cf-198">콘솔에 오류를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-198">Writes an error to the console.</span></span>
- <span data-ttu-id="ff9cf-199">**Inquire** : 디버그 메시지를 표시 하 고 계속할지 여부를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-199">**Inquire** : Displays the debug message and asks you whether you want to continue.</span></span> <span data-ttu-id="ff9cf-200">명령에 **Debug** 일반 매개 변수를 추가 하 여 디버깅 메시지를 생성 하도록 명령이 구성 된 경우 변수 값을 `$DebugPreference` **Inquire** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-200">Adding the **Debug** common parameter to a command, when the command is configured to generate a debugging message, changes the value of the `$DebugPreference` variable to **Inquire**.</span></span>
- <span data-ttu-id="ff9cf-201">**Continue** : 디버그 메시지를 표시 하 고 실행을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-201">**Continue** : Displays the debug message and continues with execution.</span></span>
- <span data-ttu-id="ff9cf-202">**SilentlyContinue** : (기본값) 아무런 영향도 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-202">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="ff9cf-203">디버그 메시지는 표시 되지 않으며 중단 없이 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-203">The debug message isn't displayed and execution continues without interruption.</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-204">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-204">Examples</span></span>

<span data-ttu-id="ff9cf-205">다음 예에서는 명령줄 `$DebugPreference` 에서 명령을 입력 하는 경우의 값을 변경할 경우의 결과를 보여 줍니다 `Write-Debug` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-205">The following examples show the effect of changing the values of `$DebugPreference` when a `Write-Debug` command is entered at the command line.</span></span>
<span data-ttu-id="ff9cf-206">변경 내용은 cmdlet 및 스크립트에 의해 생성 된 메시지를 포함 하 여 모든 디버깅 메시지에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-206">The change affects all debugging messages, including messages generated by cmdlets and scripts.</span></span> <span data-ttu-id="ff9cf-207">예제에서는 단일 명령과 관련 된 디버깅 메시지를 표시 하거나 숨기는 **Debug** 매개 변수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-207">The examples show the **Debug** parameter, which displays or hides the debugging messages related to a single command.</span></span>

<span data-ttu-id="ff9cf-208">이 예에서는 `$DebugPreference` 변수의 기본값 **SilentlyContinue** 의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-208">This example shows the effect of the `$DebugPreference` variable's default value, **SilentlyContinue**.</span></span> <span data-ttu-id="ff9cf-209">기본적으로 `Write-Debug` cmdlet의 디버그 메시지가 표시 되지 않고 처리가 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-209">By default, the `Write-Debug` cmdlet's debug message isn't displayed and processing continues.</span></span> <span data-ttu-id="ff9cf-210">**디버그** 매개 변수를 사용 하는 경우 단일 명령에 대 한 기본 설정을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-210">When the **Debug** parameter is used, it overrides the preference for a single command.</span></span> <span data-ttu-id="ff9cf-211">디버그 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-211">The debug message is displayed.</span></span>

```powershell
$DebugPreference
```

```Output
SilentlyContinue
```

```powershell
Write-Debug -Message "Hello, World"
```

```powershell
Write-Debug -Message "Hello, World" -Debug
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="ff9cf-212">이 예에서는 Continue 값을 사용한 결과를 보여 줍니다 `$DebugPreference` . **Continue**</span><span class="sxs-lookup"><span data-stu-id="ff9cf-212">This example shows the effect of `$DebugPreference` with the **Continue** value.</span></span> <span data-ttu-id="ff9cf-213">디버그 메시지가 표시 되 고 명령이 계속 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-213">The debug message is displayed and the command continues to process.</span></span>

```powershell
$DebugPreference = "Continue"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
```

<span data-ttu-id="ff9cf-214">이 예제에서는 값이 인 **Debug** 매개 변수 `$false` 를 사용 하 여 단일 명령에 대 한 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-214">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="ff9cf-215">디버그 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-215">The debug message isn't displayed.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="ff9cf-216">이 예에서는 `$DebugPreference` **중지** 값으로 설정 되는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-216">This example shows the effect of `$DebugPreference` being set to the **Stop** value.</span></span> <span data-ttu-id="ff9cf-217">디버그 메시지가 표시 되 고 명령이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-217">The debug message is displayed and the command is stopped.</span></span>

```powershell
$DebugPreference = "Stop"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World
Write-Debug : The running command stopped because the preference variable
 "DebugPreference" or common parameter is set to Stop: Hello, World
At line:1 char:1
+ Write-Debug -Message "Hello, World"
```

<span data-ttu-id="ff9cf-218">이 예제에서는 값이 인 **Debug** 매개 변수 `$false` 를 사용 하 여 단일 명령에 대 한 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-218">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="ff9cf-219">디버그 메시지가 표시 되지 않고 처리가 중지 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-219">The debug message isn't displayed and processing isn't stopped.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

<span data-ttu-id="ff9cf-220">이 예에서는 `$DebugPreference` **Inquire** 값으로 설정 되는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-220">This example shows the effect of `$DebugPreference` being set to the **Inquire** value.</span></span> <span data-ttu-id="ff9cf-221">디버그 메시지가 표시 되 고 사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-221">The debug message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$DebugPreference = "Inquire"
Write-Debug -Message "Hello, World"
```

```Output
DEBUG: Hello, World

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="ff9cf-222">이 예제에서는 값이 인 **Debug** 매개 변수 `$false` 를 사용 하 여 단일 명령에 대 한 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-222">This example uses the **Debug** parameter with a value of `$false` to suppress the message for a single command.</span></span> <span data-ttu-id="ff9cf-223">디버그 메시지가 표시 되지 않고 처리가 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-223">The debug message isn't displayed and processing continues.</span></span>

```powershell
Write-Debug -Message "Hello, World" -Debug:$false
```

### <a name="erroractionpreference"></a><span data-ttu-id="ff9cf-224">\$ErrorActionPreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-224">\$ErrorActionPreference</span></span>

<span data-ttu-id="ff9cf-225">PowerShell이 종료 되지 않는 오류에 응답 하는 방법, 즉 cmdlet 처리를 중지 하지 않는 오류를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-225">Determines how PowerShell responds to a non-terminating error, an error that doesn't stop the cmdlet processing.</span></span> <span data-ttu-id="ff9cf-226">예를 들어, 명령줄 또는 cmdlet에 의해 생성 된 오류와 같은 스크립트, cmdlet 또는 공급자에 `Write-Error` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-226">For example, at the command line or in a script, cmdlet, or provider, such as the errors generated by the `Write-Error` cmdlet.</span></span>

<span data-ttu-id="ff9cf-227">Cmdlet의 **Erroraction** 일반 매개 변수를 사용 하 여 특정 명령에 대 한 기본 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-227">You can use a cmdlet's **ErrorAction** common parameter to override the preference for a specific command.</span></span>

<span data-ttu-id="ff9cf-228">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-228">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-229">**Continue** : (기본값) 오류 메시지를 표시 하 고 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-229">**Continue** : (Default) Displays the error message and continues executing.</span></span>
- <span data-ttu-id="ff9cf-230">**Ignore** : 오류 메시지를 표시 하지 않고 계속 해 서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-230">**Ignore** : Suppresses the error message and continues to execute the command.</span></span> <span data-ttu-id="ff9cf-231">**무시** 값은 명령 당 사용을 위한 것 이며 저장 된 기본 설정으로 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-231">The **Ignore** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="ff9cf-232">**Ignore** 는 변수의 올바른 값이 아닙니다 `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-232">**Ignore** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>
- <span data-ttu-id="ff9cf-233">**Inquire** : 오류 메시지를 표시 하 고 계속할지 여부를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-233">**Inquire** : Displays the error message and asks you whether you want to continue.</span></span>
- <span data-ttu-id="ff9cf-234">**SilentlyContinue** : 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-234">**SilentlyContinue** : No effect.</span></span> <span data-ttu-id="ff9cf-235">오류 메시지가 표시 되지 않으며 중단 없이 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-235">The error message isn't displayed and execution continues without interruption.</span></span>
- <span data-ttu-id="ff9cf-236">**Stop** : 오류 메시지를 표시 하 고 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-236">**Stop** : Displays the error message and stops executing.</span></span> <span data-ttu-id="ff9cf-237">오류를 생성 하는 것 외에도 **Stop** 값은 오류 스트림에 ActionPreferenceStopException 개체를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-237">In addition to the error generated, the **Stop** value generates an ActionPreferenceStopException object to the error stream.</span></span>
  <span data-ttu-id="ff9cf-238">스트림(stream)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-238">stream</span></span>
- <span data-ttu-id="ff9cf-239">**Suspend** : 추가 조사를 허용 하도록 워크플로 작업을 자동으로 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-239">**Suspend** : Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="ff9cf-240">조사 후 워크플로를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-240">After investigation, the workflow can be resumed.</span></span> <span data-ttu-id="ff9cf-241">**일시 중단** 값은 저장 된 기본 설정으로 사용 되지 않고 명령 당 사용을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-241">The **Suspend** value is intended for per-command use, not for use as saved preference.</span></span> <span data-ttu-id="ff9cf-242">**Suspend** 는 변수의 올바른 값이 아닙니다 `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-242">**Suspend** isn't a valid value for the `$ErrorActionPreference` variable.</span></span>

<span data-ttu-id="ff9cf-243">`$ErrorActionPreference`**Erroraction** 매개 변수는 PowerShell이 cmdlet 처리를 중지 하는 종료 오류에 응답 하는 방법에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-243">`$ErrorActionPreference` and the **ErrorAction** parameter don't affect how PowerShell responds to terminating errors that stop cmdlet processing.</span></span> <span data-ttu-id="ff9cf-244">**Erroraction** 일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-244">For more information about the **ErrorAction** common parameter, see [about_CommonParameters](about_CommonParameters.md).</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-245">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-245">Examples</span></span>

<span data-ttu-id="ff9cf-246">이 예에서는 변수 값이 다른 값의 영향을 보여 줍니다 `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-246">These examples show the effect of the different values of the `$ErrorActionPreference` variable.</span></span> <span data-ttu-id="ff9cf-247">**Erroraction** 매개 변수는 값을 재정의 하는 데 사용 됩니다 `$ErrorActionPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-247">The **ErrorAction** parameter is used to override the `$ErrorActionPreference` value.</span></span>

<span data-ttu-id="ff9cf-248">이 예에서는 `$ErrorActionPreference` 기본값인 **Continue** 를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-248">This example shows the `$ErrorActionPreference` default value, **Continue**.</span></span> <span data-ttu-id="ff9cf-249">종료 되지 않는 오류가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-249">A non-terminating error is generated.</span></span> <span data-ttu-id="ff9cf-250">메시지가 표시 되 고 처리가 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-250">The message is displayed and processing continues.</span></span>

```powershell
# Change the ErrorActionPreference to 'Continue'
$ErrorActionPreference = 'Continue'
# Generate a non-terminating error and continue processing the script.
Write-Error -Message  'Test Error' ; Write-Host 'Hello World'
```

```Output
Write-Error -Message  'Test Error' ; Write-Host 'Hello World' : Test Error
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

Hello World
```

<span data-ttu-id="ff9cf-251">이 예에서는 `$ErrorActionPreference` 기본 값인 **Inquire** 를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-251">This example shows the `$ErrorActionPreference` default value, **Inquire**.</span></span> <span data-ttu-id="ff9cf-252">오류가 생성 되 고 동작에 대 한 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-252">An error is generated and a prompt for action is shown.</span></span>

```powershell
# Change the ErrorActionPreference to 'Inquire'
$ErrorActionPreference = 'Inquire'
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
```

```Output
Confirm
Test Error
[Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="ff9cf-253">이 예에서는를 `$ErrorActionPreference` **SilentlyContinue** 로 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-253">This example shows the `$ErrorActionPreference` set to **SilentlyContinue**.</span></span>
<span data-ttu-id="ff9cf-254">오류 메시지는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-254">The error message is suppressed.</span></span>

```powershell
# Change the ErrorActionPreference to 'SilentlyContinue'
$ErrorActionPreference = 'SilentlyContinue'
# Generate an error message
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
# Error message is suppressed and script continues processing
```

```Output
Hello World
```

<span data-ttu-id="ff9cf-255">이 예에서는 `$ErrorActionPreference` **Stop** 으로 설정 된를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-255">This example shows the `$ErrorActionPreference` set to **Stop**.</span></span> <span data-ttu-id="ff9cf-256">변수에 생성 된 추가 개체도 보여 줍니다 `$Error` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-256">It also shows the extra object generated to the `$Error` variable.</span></span>

```powershell
# Change the ErrorActionPreference to 'Stop'
$ErrorActionPreference = 'Stop'
# Error message is is generated and script stops processing
Write-Error -Message 'Test Error' ; Write-Host 'Hello World'

# Show the ActionPreferenceStopException and the error generated
$Error[0]
$Error[1]
```

```Output
Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

The running command stopped because the preference variable "ErrorActionPreference"
or common parameter is set to Stop: Test Error

Write-Error -Message 'Test Error' ; Write-Host 'Hello World' : Test Error
At line:1 char:1
+ Write-Error -Message 'Test Error' ; Write-Host 'Hello World'
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
    + FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

### <a name="errorview"></a><span data-ttu-id="ff9cf-257">\$ErrorView</span><span class="sxs-lookup"><span data-stu-id="ff9cf-257">\$ErrorView</span></span>

<span data-ttu-id="ff9cf-258">PowerShell에서 오류 메시지의 표시 형식을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-258">Determines the display format of error messages in PowerShell.</span></span>

<span data-ttu-id="ff9cf-259">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-259">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-260">기본 **보기** : (기본값) 대부분의 사용자를 위해 설계 된 상세 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-260">**NormalView** : (Default) A detailed view designed for most users.</span></span> <span data-ttu-id="ff9cf-261">오류에 대 한 설명 및 오류와 관련 된 개체의 이름으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-261">Consists of a description of the error and the name of the object involved in the error.</span></span>
- <span data-ttu-id="ff9cf-262">**Categoryview** : 프로덕션 환경을 위해 설계 된 간결한 구조화 된 뷰입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-262">**CategoryView** : A succinct, structured view designed for production environments.</span></span> <span data-ttu-id="ff9cf-263">형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-263">The format is as follows:</span></span>

  <span data-ttu-id="ff9cf-264">{Category}: ({TargetName}: {TargetType}): [{Activity}], {Reason}</span><span class="sxs-lookup"><span data-stu-id="ff9cf-264">{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}</span></span>

<span data-ttu-id="ff9cf-265">**Categoryview** 의 필드에 대 한 자세한 내용은 [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) 클래스를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-265">For more information about the fields in **CategoryView** , see [ErrorCategoryInfo](/dotnet/api/system.management.automation.errorcategoryinfo) class.</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-266">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-266">Examples</span></span>

<span data-ttu-id="ff9cf-267">이 예에서는의 값이 `$ErrorView` 기본값인 **normalview** 인 경우 오류를 표시 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-267">This example shows how an error appears when the value of `$ErrorView` is the default, **NormalView**.</span></span> <span data-ttu-id="ff9cf-268">`Get-ChildItem` 존재 하지 않는 파일을 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-268">`Get-ChildItem` is used to find a non-existent file.</span></span>

```powershell
Get-ChildItem -Path C:\nofile.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\nofile.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path C:\nofile.txt
```

<span data-ttu-id="ff9cf-269">이 예에서는의 값 `$ErrorView` 이 **categoryview** 로 변경 될 때 동일한 오류가 표시 되는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-269">This example shows how the same error appears when the value of `$ErrorView` is changed to **CategoryView**.</span></span>

```powershell
$ErrorView = "CategoryView"
Get-ChildItem -Path C:\nofile.txt
```

```Output
ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem], ItemNotFoundException
```

<span data-ttu-id="ff9cf-270">이 예에서는의 값이 `$ErrorView` 오류 표시에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-270">This example demonstrates that the value of `$ErrorView` only affects the error display.</span></span> <span data-ttu-id="ff9cf-271">자동 변수에 저장 된 오류 개체의 구조는 변경 되지 않습니다 `$Error` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-271">It doesn't change the structure of the error object that is stored in the `$Error` automatic variable.</span></span> <span data-ttu-id="ff9cf-272">자동 변수에 대 한 자세한 내용은 `$Error` [about_automatic_variables](about_Automatic_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-272">For information about the `$Error` automatic variable, see [about_automatic_variables](about_Automatic_Variables.md).</span></span>

<span data-ttu-id="ff9cf-273">다음 명령은 오류 배열에서 가장 최근 오류와 연결 된 **ErrorRecord** 개체, **요소 0** 을 사용 하 고 목록에 있는 모든 error 개체의 속성에 대 한 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-273">The following command takes the **ErrorRecord** object associated with the most recent error in the error array, **element 0** , and formats all the error object's properties in a list.</span></span>

```powershell
$Error[0] | Format-List -Property * -Force
```

```Output
PSMessageDetails      :
Exception             : System.Management.Automation.ItemNotFoundException:
                          Cannot find path 'C:\nofile.txt' because it does
                          not exist.
                        at System.Management.Automation.SessionStateInternal.
                          GetChildItems(String path, Boolean recurse, UInt32
                          depth, CmdletProviderContext context)
                        at System.Management.Automation.ChildItemCmdlet
                          ProviderIntrinsics.Get(String path, Boolean
                          recurse, UInt32 depth, CmdletProviderContext context)
                        at Microsoft.PowerShell.Commands.GetChildItemCommand.
                          ProcessRecord()
TargetObject          : C:\nofile.txt
CategoryInfo          : ObjectNotFound: (C:\nofile.txt:String) [Get-ChildItem],
                          ItemNotFoundException
FullyQualifiedErrorId : PathNotFound,
                          Microsoft.PowerShell.Commands.GetChildItemCommand
ErrorDetails          :
InvocationInfo        : System.Management.Automation.InvocationInfo
ScriptStackTrace      : at <ScriptBlock>, <No file>: line 1
PipelineIterationInfo : {0, 1}
```

### <a name="formatenumerationlimit"></a><span data-ttu-id="ff9cf-274">\$FormatEnumerationLimit</span><span class="sxs-lookup"><span data-stu-id="ff9cf-274">\$FormatEnumerationLimit</span></span>

<span data-ttu-id="ff9cf-275">표시에 포함 되는 열거 된 항목 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-275">Determines how many enumerated items are included in a display.</span></span> <span data-ttu-id="ff9cf-276">이 변수는 기본 개체에는 영향을 주지 않으며 표시 되는 경우에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-276">This variable doesn't affect the underlying objects, only the display.</span></span> <span data-ttu-id="ff9cf-277">의 값 `$FormatEnumerationLimit` 이 열거 된 항목 수보다 적으면 PowerShell은 `...` 표시 되지 않는 항목을 나타내기 위해 줄임표 ()를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-277">When the value of `$FormatEnumerationLimit` is fewer than the number of enumerated items, PowerShell adds an ellipsis (`...`) to indicate items not shown.</span></span>

<span data-ttu-id="ff9cf-278">**유효한 값** : 정수 ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="ff9cf-278">**Valid values** : Integers (`Int32`)</span></span>

<span data-ttu-id="ff9cf-279">**기본값** : 4</span><span class="sxs-lookup"><span data-stu-id="ff9cf-279">**Default value** : 4</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-280">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-280">Examples</span></span>

<span data-ttu-id="ff9cf-281">이 예제에서는 변수를 사용 하 여 `$FormatEnumerationLimit` 열거 된 항목의 표시를 개선 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-281">This example shows how to use the `$FormatEnumerationLimit` variable to improve the display of enumerated items.</span></span>

<span data-ttu-id="ff9cf-282">이 예제의 명령은 **실행 중인** 서비스와 **중지** 된 서비스용으로 하나씩, 두 그룹의 컴퓨터에서 실행 되는 모든 서비스를 나열 하는 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-282">The command in this example generates a table that lists all the services running on the computer in two groups: one for **running** services and one for **stopped** services.</span></span> <span data-ttu-id="ff9cf-283">명령을 사용 하 여 `Get-Service` 모든 서비스를 가져온 다음 파이프라인을 통해 결과를 cmdlet에 보냅니다 `Group-Object` .이 cmdlet은 서비스 상태별로 결과를 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-283">It uses a `Get-Service` command to get all the services, and then sends the results through the pipeline to the `Group-Object` cmdlet, which groups the results by the service status.</span></span>

<span data-ttu-id="ff9cf-284">결과는 **이름** 열의 상태와 **그룹** 열의 프로세스를 나열 하는 테이블입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-284">The result is a table that lists the status in the **Name** column, and the processes in the **Group** column.</span></span> <span data-ttu-id="ff9cf-285">열 레이블을 변경 하려면 해시 테이블을 사용 하십시오. [about_Hash_Tables](about_Hash_Tables.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-285">To change the column labels, use a hash table, see [about_Hash_Tables](about_Hash_Tables.md).</span></span> <span data-ttu-id="ff9cf-286">자세한 내용은 [형식-테이블](xref:Microsoft.PowerShell.Utility.Format-Table)의 예제를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-286">For more information, see the examples in [Format-Table](xref:Microsoft.PowerShell.Utility.Format-Table).</span></span>

<span data-ttu-id="ff9cf-287">의 현재 값을 찾습니다 `$FormatEnumerationLimit` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-287">Find the current value of `$FormatEnumerationLimit`.</span></span>

```powershell
$FormatEnumerationLimit
```

```Output
4
```

<span data-ttu-id="ff9cf-288">**상태별** 로 그룹화 된 모든 서비스를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-288">List all services grouped by **Status**.</span></span> <span data-ttu-id="ff9cf-289">의 값은 4 이기 때문에 각 상태에 대 한 **그룹** 열에는 최대 4 개의 서비스가 나열 됩니다 `$FormatEnumerationLimit` . **4**</span><span class="sxs-lookup"><span data-stu-id="ff9cf-289">There are a maximum of four services listed in the **Group** column for each status because `$FormatEnumerationLimit` has a value of **4**.</span></span>

```powershell
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv...}
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart...}
```

<span data-ttu-id="ff9cf-290">나열 된 항목 수를 늘리려면 값을 `$FormatEnumerationLimit` **1000** 로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-290">To increase the number of items listed, increase the value of `$FormatEnumerationLimit` to **1000**.</span></span> <span data-ttu-id="ff9cf-291">`Get-Service`및 `Group-Object` 를 사용 하 여 서비스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-291">Use `Get-Service` and `Group-Object` to display the services.</span></span>

```powershell
$FormatEnumerationLimit = 1000
Get-Service | Group-Object -Property Status
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec...
41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc...
```

<span data-ttu-id="ff9cf-292">`Format-Table` **Wrap** 매개 변수와 함께 사용 하 여 서비스 목록을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-292">Use `Format-Table` with the **Wrap** parameter to display the list of services.</span></span>

```powershell
Get-Service | Group-Object -Property Status | Format-Table -Wrap
```

```Output
Count  Name       Group
-----  ----       -----
60     Running    {AdtAgent, ALG, Ati HotKey Poller, AudioSrv, BITS, CcmExec,
                  Client for NFS, CryptSvc, DcomLaunch, Dhcp, dmserver,
                  Dnscache, ERSvc, Eventlog, EventSystem, FwcAgent, helpsvc,
                  HidServ, IISADMIN, InoRPC, InoRT, InoTask, lanmanserver,
                  lanmanworkstation, LmHosts, MDM, Netlogon, Netman, Nla,
                  NtLmSsp, PlugPlay, PolicyAgent, ProtectedStorage, RasMan,
                  RemoteRegistry, RpcSs, SamSs, Schedule, seclogon, SENS,
                  SharedAccess, ShellHWDetection, SMT PSVC, Spooler,
                  srservice, SSDPSRV, stisvc, TapiSrv, TermService, Themes,
                  TrkWks, UMWdf, W32Time, W3SVC, WebClient, winmgmt, wscsvc,
                  wuauserv, WZCSVC, zzInterix}

41     Stopped    {Alerter, AppMgmt, aspnet_state, ATI Smart, Browser, CiSvc,
                  ClipSrv, clr_optimization_v2.0.50727_32, COMSysApp,
                  CronService, dmadmin, FastUserSwitchingCompatibility,
                  HTTPFilter, ImapiService, Mapsvc, Messenger, mnmsrvc,
                  MSDTC, MSIServer, msvsmon80, NetDDE, NetDDEdsdm, NtmsSvc,
                  NVSvc, ose, RasAuto, RDSessMgr, RemoteAccess, RpcLocator,
                  SCardSvr, SwPrv, SysmonLog, TlntSvr, upnphost, UPS, VSS,
                  WmdmPmSN, Wmi, WmiApSrv, xmlprov}
```

### <a name="informationpreference"></a><span data-ttu-id="ff9cf-293">\$InformationPreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-293">\$InformationPreference</span></span>

<span data-ttu-id="ff9cf-294">`$InformationPreference`변수를 사용 하면 사용자에 게 표시할 정보 스트림 기본 설정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-294">The `$InformationPreference` variable lets you set information stream preferences that you want displayed to users.</span></span> <span data-ttu-id="ff9cf-295">특히 [쓰기 정보](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet을 추가 하 여 명령 또는 스크립트에 추가한 정보 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-295">Specifically, informational messages that you added to commands or scripts by adding the [Write-Information](xref:Microsoft.PowerShell.Utility.Write-Information) cmdlet.</span></span> <span data-ttu-id="ff9cf-296">**Informationaction** 매개 변수를 사용 하는 경우 해당 값은 변수의 값을 재정의 `$InformationPreference` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-296">If the **InformationAction** parameter is used, its value overrides the value of the `$InformationPreference` variable.</span></span> <span data-ttu-id="ff9cf-297">`Write-Information` 는 PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-297">`Write-Information` was introduced in PowerShell 5.0.</span></span>

<span data-ttu-id="ff9cf-298">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-298">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-299">**Stop** : 명령이 발생 하면 명령이 나 스크립트를 중지 합니다. `Write-Information`</span><span class="sxs-lookup"><span data-stu-id="ff9cf-299">**Stop** : Stops a command or script at an occurrence of the `Write-Information` command.</span></span>
- <span data-ttu-id="ff9cf-300">**Inquire** : 명령에 지정 하는 정보 메시지를 표시 `Write-Information` 한 다음 계속할지 여부를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-300">**Inquire** : Displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>
- <span data-ttu-id="ff9cf-301">**Continue** : 정보 메시지를 표시 하 고 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-301">**Continue** : Displays the informational message, and continues running.</span></span>
- <span data-ttu-id="ff9cf-302">**일시 중단** 은 PowerShell 6 이상에서 지원 되지 않는 워크플로에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-302">**Suspend** is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>
- <span data-ttu-id="ff9cf-303">**SilentlyContinue** : (기본값) 아무런 영향도 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-303">**SilentlyContinue** : (Default) No effect.</span></span> <span data-ttu-id="ff9cf-304">정보 메시지는 표시 되지 않으며 스크립트는 중단 없이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-304">The informational messages aren't displayed, and the script continues without interruption.</span></span>

### <a name="logevent"></a><span data-ttu-id="ff9cf-305">\$Log \* 이벤트</span><span class="sxs-lookup"><span data-stu-id="ff9cf-305">\$Log\*Event</span></span>

<span data-ttu-id="ff9cf-306">**Log \* 이벤트** 기본 설정 변수는 이벤트 뷰어의 PowerShell 이벤트 로그에 기록 되는 이벤트 유형을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-306">The **Log\*Event** preference variables determine which types of events are written to the PowerShell event log in Event Viewer.</span></span> <span data-ttu-id="ff9cf-307">기본적으로 엔진 및 공급자 이벤트만 로깅됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-307">By default, only engine and provider events are logged.</span></span> <span data-ttu-id="ff9cf-308">그러나 **log \* 이벤트** 기본 설정 변수를 사용 하 여 로그를 사용자 지정할 수 있습니다 (예: 명령에 대 한 로깅 이벤트).</span><span class="sxs-lookup"><span data-stu-id="ff9cf-308">But, you can use the **Log\*Event** preference variables to customize your log, such as logging events about commands.</span></span>

<span data-ttu-id="ff9cf-309">**Log \* 이벤트** 기본 설정 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-309">The **Log\*Event** preference variables are as follows:</span></span>

- <span data-ttu-id="ff9cf-310">`$LogCommandHealthEvent`: 명령 초기화 및 처리에서 오류 및 예외를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-310">`$LogCommandHealthEvent`: Logs errors and exceptions in command initialization and processing.</span></span> <span data-ttu-id="ff9cf-311">기본값은 `$false` (로깅되지 않음)입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-311">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="ff9cf-312">`$LogCommandLifecycleEvent`: 명령 검색에서 명령 및 명령 파이프라인의 시작과 중지 및 보안 예외를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-312">`$LogCommandLifecycleEvent`: Logs the starting and stopping of commands and command pipelines and security exceptions in command discovery.</span></span> <span data-ttu-id="ff9cf-313">기본값은 `$false` (로깅되지 않음)입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-313">The default is `$false` (not logged).</span></span>
- <span data-ttu-id="ff9cf-314">`$LogEngineHealthEvent`: 세션의 오류 및 실패를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-314">`$LogEngineHealthEvent`: Logs errors and failures of sessions.</span></span> <span data-ttu-id="ff9cf-315">기본값은 `$true` (기록)입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-315">The default is `$true` (logged).</span></span>
- <span data-ttu-id="ff9cf-316">`$LogEngineLifecycleEvent`: 세션의 열기 및 닫기를 로깅합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-316">`$LogEngineLifecycleEvent`: Logs the opening and closing of sessions.</span></span> <span data-ttu-id="ff9cf-317">기본값은 `$true` (기록)입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-317">The default is `$true` (logged).</span></span>
- <span data-ttu-id="ff9cf-318">`$LogProviderHealthEvent`: 읽기 및 쓰기 오류, 조회 오류, 호출 오류 등의 공급자 오류를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-318">`$LogProviderHealthEvent`: Logs provider errors, such as read and write errors, lookup errors, and invocation errors.</span></span> <span data-ttu-id="ff9cf-319">기본값은 `$true` (기록)입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-319">The default is `$true` (logged).</span></span>
- <span data-ttu-id="ff9cf-320">`$LogProviderLifecycleEvent`: PowerShell 공급자 추가 및 제거를 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-320">`$LogProviderLifecycleEvent`: Logs adding and removing of PowerShell providers.</span></span> <span data-ttu-id="ff9cf-321">기본값은 `$true` (기록)입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-321">The default is `$true` (logged).</span></span> <span data-ttu-id="ff9cf-322">PowerShell 공급자에 대 한 자세한 내용은 [about_Providers](about_Providers.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-322">For information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

<span data-ttu-id="ff9cf-323">**Log \* 이벤트** 를 사용 하도록 설정 하려면 값이 인 변수를 입력 합니다 `$true` . 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-323">To enable a **Log\*Event** , type the variable with a value of `$true`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $true
```

<span data-ttu-id="ff9cf-324">이벤트 유형을 사용 하지 않도록 설정 하려면 값이 인 변수를 입력 합니다 `$false` . 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-324">To disable an event type, type the variable with a value of `$false`, for example:</span></span>

```powershell
$LogCommandLifeCycleEvent = $false
```

<span data-ttu-id="ff9cf-325">사용 하도록 설정 하는 이벤트는 현재 PowerShell 콘솔에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-325">The events that you enable are effective only for the current PowerShell console.</span></span> <span data-ttu-id="ff9cf-326">모든 콘솔에 구성을 적용 하려면 변수 설정을 PowerShell 프로필에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-326">To apply the configuration to all consoles, save the variable settings in your PowerShell profile.</span></span> <span data-ttu-id="ff9cf-327">자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-327">For more information, see [about_Profiles](about_Profiles.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="ff9cf-328">\$MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="ff9cf-328">\$MaximumHistoryCount</span></span>

<span data-ttu-id="ff9cf-329">현재 세션에 대 한 명령 기록에 저장 되는 명령 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-329">Determines how many commands are saved in the command history for the current session.</span></span>

<span data-ttu-id="ff9cf-330">**유효한 값** : 1-32768 ( `Int32` )</span><span class="sxs-lookup"><span data-stu-id="ff9cf-330">**Valid values** : 1 - 32768 (`Int32`)</span></span>

<span data-ttu-id="ff9cf-331">**기본값** : 4096</span><span class="sxs-lookup"><span data-stu-id="ff9cf-331">**Default** : 4096</span></span>

<span data-ttu-id="ff9cf-332">명령 기록에 현재 저장 된 명령의 수를 확인 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-332">To determine the number of commands current saved in the command history, type:</span></span>

```powershell
(Get-History).Count
```

<span data-ttu-id="ff9cf-333">세션 기록에 저장 된 명령을 보려면 cmdlet을 사용 합니다 `Get-History` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-333">To see the commands saved in your session history, use the `Get-History` cmdlet.</span></span> <span data-ttu-id="ff9cf-334">자세한 내용은 [about_History](about_History.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-334">For more information, see [about_History](about_History.md).</span></span>

### <a name="ofs"></a><span data-ttu-id="ff9cf-335">\$OFS</span><span class="sxs-lookup"><span data-stu-id="ff9cf-335">\$OFS</span></span>

<span data-ttu-id="ff9cf-336">출력 필드 구분 기호 (.OFS)는 문자열로 변환 된 배열의 요소를 구분 하는 문자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-336">The Output Field Separator (OFS) specifies the character that separates the elements of an array that is converted to a string.</span></span>

<span data-ttu-id="ff9cf-337">**유효한 값** : 모든 문자열</span><span class="sxs-lookup"><span data-stu-id="ff9cf-337">**Valid values** : Any string.</span></span>

<span data-ttu-id="ff9cf-338">**기본값** : Space</span><span class="sxs-lookup"><span data-stu-id="ff9cf-338">**Default** : Space</span></span>

<span data-ttu-id="ff9cf-339">기본적으로 변수는 `$OFS` 존재 하지 않으며 출력 파일 구분 기호는 공백 이지만이 변수를 추가 하 고 임의의 문자열로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-339">By default, the `$OFS` variable doesn't exist and the output file separator is a space, but you can add this variable and set it to any string.</span></span> <span data-ttu-id="ff9cf-340">을 `$OFS` 입력 하 여 세션의 값을 변경할 수 있습니다 `$OFS="<value>"` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-340">You can change the value of `$OFS` in your session, by typing `$OFS="<value>"`.</span></span>

> [!NOTE]
> <span data-ttu-id="ff9cf-341">`" "`스크립트, 모듈 또는 구성 출력에 공백 ()의 기본값이 필요한 경우 `$OFS` 코드의 다른 위치에서 기본값이 변경 되지 않은 것으로 주의 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-341">If you're expecting the default value of a space (`" "`) in your script, module, or configuration output, be careful that the `$OFS` default value hasn't been changed elsewhere in your code.</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-342">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-342">Examples</span></span>

<span data-ttu-id="ff9cf-343">이 예제에서는 배열이 문자열로 변환 될 때 공백을 사용 하 여 값을 구분 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-343">This example shows that a space is used to separate the values when an array is converted to a string.</span></span> <span data-ttu-id="ff9cf-344">이 경우 정수 배열이 변수에 저장 된 다음 변수가 문자열로 캐스팅 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-344">In this case, an array of integers is stored in a variable and then the variable is cast as a string.</span></span>

```powershell
$array = 1,2,3,4
[string]$array
```

```Output
1 2 3 4
```

<span data-ttu-id="ff9cf-345">구분 기호를 변경 하려면 값을 `$OFS` 할당 하 여 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-345">To change the separator, add the `$OFS` variable by assigning a value to it.</span></span>
<span data-ttu-id="ff9cf-346">변수에 이름을 지정 해야 합니다 `$OFS` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-346">The variable must be named `$OFS`.</span></span>

```powershell
$OFS = "+"
[string]$array
```

```Output
1+2+3+4
```

<span data-ttu-id="ff9cf-347">기본 동작을 복원 하려면 값에 공백 ()을 할당 `" "` `$OFS` 하거나 변수를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-347">To restore the default behavior, you can assign a space (`" "`) to the value of `$OFS` or delete the variable.</span></span> <span data-ttu-id="ff9cf-348">다음 명령은 변수를 삭제 한 다음 구분 기호가 공백 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-348">The following commands delete the variable and then verify that the separator is a space.</span></span>

```powershell
Remove-Variable OFS
[string]$array
```

```Output
1 2 3 4
```

### <a name="outputencoding"></a><span data-ttu-id="ff9cf-349">\$OutputEncoding</span><span class="sxs-lookup"><span data-stu-id="ff9cf-349">\$OutputEncoding</span></span>

<span data-ttu-id="ff9cf-350">다른 응용 프로그램에 텍스트를 보낼 때 PowerShell에서 사용 하는 문자 인코딩 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-350">Determines the character encoding method that PowerShell uses when it sends text to other applications.</span></span>

<span data-ttu-id="ff9cf-351">예를 들어 응용 프로그램이 유니코드 문자열을 PowerShell로 반환 하는 경우 문자를 올바르게 보내기 위해 값을 **UnicodeEncoding** 로 변경 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-351">For example, if an application returns Unicode strings to PowerShell, you might need to change the value to **UnicodeEncoding** to send the characters correctly.</span></span>

<span data-ttu-id="ff9cf-352">유효한 값은 **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** 및 **UnicodeEncoding** 와 같이 Encoding 클래스에서 파생 된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-352">The valid values are as follows: Objects derived from an Encoding class, such as **ASCIIEncoding** , **SBCSCodePageEncoding** , **UTF7Encoding** , **UTF8Encoding** , **UTF32Encoding** , and **UnicodeEncoding**.</span></span>

<span data-ttu-id="ff9cf-353">**기본값** : UTF8Encoding 개체 (UTF8Encoding)</span><span class="sxs-lookup"><span data-stu-id="ff9cf-353">**Default** : UTF8Encoding object (System.Text.UTF8Encoding)</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-354">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-354">Examples</span></span>

<span data-ttu-id="ff9cf-355">이 예제에서는 유니코드 문자를 사용 하는 언어 (예: 중국어)로 지역화 된 컴퓨터에서 Windows **findstr.exe** 명령을 PowerShell에서 작동 하 게 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-355">This example shows how to make the Windows **findstr.exe** command work in PowerShell on a computer that is localized for a language that uses Unicode characters, such as Chinese.</span></span>

<span data-ttu-id="ff9cf-356">첫 번째 명령은의 값을 찾습니다 `$OutputEncoding` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-356">The first command finds the value of `$OutputEncoding`.</span></span> <span data-ttu-id="ff9cf-357">이 값은 인코딩 개체 이므로 해당 **EncodingName** 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-357">Because the value is an encoding object, display only its **EncodingName** property.</span></span>

```powershell
$OutputEncoding.EncodingName
```

<span data-ttu-id="ff9cf-358">이 예제에서는 **findstr.exe** 명령을 사용 하 여 파일에 있는 두 개의 중국어 문자를 검색 `Test.txt` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-358">In this example, a **findstr.exe** command is used to search for two Chinese characters that are present in the `Test.txt` file.</span></span> <span data-ttu-id="ff9cf-359">이 **findstr.exe** 명령이 Windows 명령 프롬프트 ( **cmd.exe** )에서 실행 되는 경우 **findstr.exe** 는 텍스트 파일에서 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-359">When this **findstr.exe** command is run in the Windows Command Prompt ( **cmd.exe** ), **findstr.exe** finds the characters in the text file.</span></span> <span data-ttu-id="ff9cf-360">그러나 PowerShell에서 동일한 **findstr.exe** 명령을 실행 하는 경우 Powershell에서 유니코드 텍스트가 아닌 ASCII 텍스트의 **findstr.exe** 으로 보내기 때문에 문자를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-360">However, when you run the same **findstr.exe** command in PowerShell, the characters aren't found because the PowerShell sends them to **findstr.exe** in ASCII text, instead of in Unicode text.</span></span>

```powershell
findstr <Unicode-characters>
```

<span data-ttu-id="ff9cf-361">PowerShell에서 명령을 작동 하도록 하려면의 값을 `$OutputEncoding` 콘솔의 **outputencoding** 속성 값으로 설정 합니다 .이 속성은 Windows에 대해 선택한 로캘을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-361">To make the command work in PowerShell, set the value of `$OutputEncoding` to the value of the **OutputEncoding** property of the console, that is based on the locale selected for Windows.</span></span> <span data-ttu-id="ff9cf-362">**Outputencoding** 이 콘솔의 정적 속성 이므로 명령에 이중 콜론 ()을 사용 `::` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-362">Because **OutputEncoding** is a static property of the console, use double-colons (`::`) in the command.</span></span>

```powershell
$OutputEncoding = [console]::OutputEncoding
$OutputEncoding.EncodingName
```

```Output
OEM United States
```

<span data-ttu-id="ff9cf-363">인코딩이 변경 된 후 **findstr.exe** 명령은 유니코드 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-363">After the encoding change, the **findstr.exe** command finds the Unicode characters.</span></span>

```powershell
findstr <Unicode-characters>
```

```Output
test.txt:         <Unicode-characters>
```

### <a name="progresspreference"></a><span data-ttu-id="ff9cf-364">\$ProgressPreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-364">\$ProgressPreference</span></span>

<span data-ttu-id="ff9cf-365">PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 진행률 업데이트 (예: [쓰기 진행률](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet에 의해 생성 된 진행률 표시줄)에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-365">Determines how PowerShell responds to progress updates generated by a script, cmdlet, or provider, such as the progress bars generated by the [Write-Progress](xref:Microsoft.PowerShell.Utility.Write-Progress) cmdlet.</span></span>
<span data-ttu-id="ff9cf-366">`Write-Progress`Cmdlet은 명령의 상태를 표시 하는 진행률 표시줄을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-366">The `Write-Progress` cmdlet creates progress bars that show a command's status.</span></span>

<span data-ttu-id="ff9cf-367">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-367">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-368">**중지** : 진행률 표시줄을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-368">**Stop** : Doesn't display the progress bar.</span></span> <span data-ttu-id="ff9cf-369">대신 오류 메시지를 표시 하 고 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-369">Instead, it displays an error message and stops executing.</span></span>
- <span data-ttu-id="ff9cf-370">**Inquire** : 진행률 표시줄을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-370">**Inquire** : Doesn't display the progress bar.</span></span> <span data-ttu-id="ff9cf-371">계속할 수 있는 권한을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-371">Prompts for permission to continue.</span></span> <span data-ttu-id="ff9cf-372">또는로 회신 하 `Y` `A` 는 경우 진행률 표시줄이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-372">If you reply with `Y` or `A`, it displays the progress bar.</span></span>
- <span data-ttu-id="ff9cf-373">**Continue** : (기본값) 진행률 표시줄을 표시 하 고 실행을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-373">**Continue** : (Default) Displays the progress bar and continues with execution.</span></span>
- <span data-ttu-id="ff9cf-374">**SilentlyContinue** : 명령을 실행 하지만 진행률 표시줄을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-374">**SilentlyContinue** : Executes the command, but doesn't display the progress bar.</span></span>

### <a name="psemailserver"></a><span data-ttu-id="ff9cf-375">\$PSEmailServer</span><span class="sxs-lookup"><span data-stu-id="ff9cf-375">\$PSEmailServer</span></span>

<span data-ttu-id="ff9cf-376">전자 메일 메시지를 보내는 데 사용 되는 기본 전자 메일 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-376">Specifies the default e-mail server that is used to send email messages.</span></span> <span data-ttu-id="ff9cf-377">이 기본 설정 변수는 [send-mailmessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet과 같은 전자 메일을 보내는 cmdlet에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-377">This preference variable is used by cmdlets that send email, such as the [Send-MailMessage](xref:Microsoft.PowerShell.Utility.Send-MailMessage) cmdlet.</span></span>

### <a name="psdefaultparametervalues"></a><span data-ttu-id="ff9cf-378">\$PSDefaultParameterValues</span><span class="sxs-lookup"><span data-stu-id="ff9cf-378">\$PSDefaultParameterValues</span></span>

<span data-ttu-id="ff9cf-379">Cmdlet 및 고급 함수의 매개 변수에 대 한 기본값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-379">Specifies default values for the parameters of cmdlets and advanced functions.</span></span>
<span data-ttu-id="ff9cf-380">값은 `$PSDefaultParameterValues` 키가 cmdlet 이름 및 콜론 ()으로 구분 된 매개 변수 이름으로 구성 되는 해시 테이블입니다 `:` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-380">The value of `$PSDefaultParameterValues` is a hash table where the key consists of the cmdlet name and parameter name separated by a colon (`:`).</span></span> <span data-ttu-id="ff9cf-381">값은 사용자가 지정 하는 사용자 지정 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-381">The value is a custom default value that you specify.</span></span>

<span data-ttu-id="ff9cf-382">`$PSDefaultParameterValues` 는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-382">`$PSDefaultParameterValues` was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="ff9cf-383">이 기본 설정 변수에 대 한 자세한 내용은 [about_Parameters_Default_Values](about_Parameters_Default_Values.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-383">For more information about this preference variable, see [about_Parameters_Default_Values](about_Parameters_Default_Values.md).</span></span>

### <a name="psmoduleautoloadingpreference"></a><span data-ttu-id="ff9cf-384">\$PSModuleAutoloadingPreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-384">\$PSModuleAutoloadingPreference</span></span>

<span data-ttu-id="ff9cf-385">세션에서 모듈 자동 가져오기를 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-385">Enables and disables automatic importing of modules in the session.</span></span> <span data-ttu-id="ff9cf-386">**All** 이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-386">**All** is the default.</span></span> <span data-ttu-id="ff9cf-387">변수 값에 관계 [없이 import-module을 사용 하](xref:Microsoft.PowerShell.Core.Import-Module) 여 모듈을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-387">Regardless of the variable's value, you can use [Import-Module](xref:Microsoft.PowerShell.Core.Import-Module) to import a module.</span></span>

<span data-ttu-id="ff9cf-388">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-388">Valid values are:</span></span>

- <span data-ttu-id="ff9cf-389">**All** : 처음 사용할 때 자동으로 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-389">**All** : Modules are imported automatically on first-use.</span></span> <span data-ttu-id="ff9cf-390">모듈을 가져오려면 모듈에서 명령을 가져오거나 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-390">To import a module, get or use any command in the module.</span></span> <span data-ttu-id="ff9cf-391">예를 들면 `Get-Command`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-391">For example, use `Get-Command`.</span></span>
- <span data-ttu-id="ff9cf-392">**ModuleQualified** : 사용자가 모듈의 명령에 대 한 모듈의 정규화 된 이름을 사용 하는 경우에만 모듈을 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-392">**ModuleQualified** : Modules are imported automatically only when a user uses the module-qualified name of a command in the module.</span></span> <span data-ttu-id="ff9cf-393">예를 들어 사용자가 형식이 면 `MyModule\MyCommand` PowerShell에서 **MyModule** 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-393">For example, if the user types `MyModule\MyCommand`, PowerShell imports the **MyModule** module.</span></span>
- <span data-ttu-id="ff9cf-394">**없음** : 모듈 자동 가져오기가 세션에서 사용 하지 않도록 설정 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-394">**None** : Automatic importing of modules is disabled in the session.</span></span> <span data-ttu-id="ff9cf-395">모듈을 가져오려면 cmdlet을 사용 `Import-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-395">To import a module, use the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="ff9cf-396">모듈 자동 가져오기에 대 한 자세한 내용은 [about_Modules](about_Modules.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-396">For more information about automatic importing of modules, see [about_Modules](about_Modules.md).</span></span>

### <a name="pssessionapplicationname"></a><span data-ttu-id="ff9cf-397">\$PSSessionApplicationName</span><span class="sxs-lookup"><span data-stu-id="ff9cf-397">\$PSSessionApplicationName</span></span>

<span data-ttu-id="ff9cf-398">WS-MANAGEMENT (관리용 웹 서비스) 기술을 사용 하는 원격 명령의 기본 응용 프로그램 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-398">Specifies the default application name for a remote command that uses Web Services for Management (WS-Management) technology.</span></span> <span data-ttu-id="ff9cf-399">자세한 내용은 [Windows 원격 관리 정보](/windows/win32/winrm/about-windows-remote-management)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-399">For more information, see [About Windows Remote Management](/windows/win32/winrm/about-windows-remote-management).</span></span>

<span data-ttu-id="ff9cf-400">시스템 기본 응용 프로그램 이름은 이지만 `WSMAN` 이 기본 설정 변수를 사용 하 여 기본값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-400">The system default application name is `WSMAN`, but you can use this preference variable to change the default.</span></span>

<span data-ttu-id="ff9cf-401">응용 프로그램 이름은 연결 URI의 마지막 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-401">The application name is the last node in a connection URI.</span></span> <span data-ttu-id="ff9cf-402">예를 들어 다음 샘플 URI의 응용 프로그램 이름은 `WSMAN` 입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-402">For example, the application name in the following sample URI is `WSMAN`.</span></span>

`http://Server01:8080/WSMAN`

<span data-ttu-id="ff9cf-403">기본 응용 프로그램 이름은 원격 명령에서 연결 URI 또는 응용 프로그램 이름을 지정 하지 않을 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-403">The default application name is used when the remote command doesn't specify a connection URI or an application name.</span></span>

<span data-ttu-id="ff9cf-404">**WinRM** 서비스는 응용 프로그램 이름을 사용 하 여 연결 요청을 처리 하는 수신기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-404">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="ff9cf-405">매개 변수의 값은 원격 컴퓨터에 있는 수신기의 **Urlprefix** 속성 값과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-405">The parameter's value should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

<span data-ttu-id="ff9cf-406">시스템 기본값과이 변수의 값을 재정의 하 고 특정 세션에 대해 다른 응용 프로그램 이름을 선택 하려면 [새-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-Pssession](xref:Microsoft.PowerShell.Core.Enter-PSSession)또는 [Invoke 명령](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlet의 **connectionuri** 또는 **ApplicationName** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-406">To override the system default and the value of this variable, and select a different application name for a particular session, use the **ConnectionURI** or **ApplicationName** parameters of the [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession), [Enter-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession), or [Invoke-Command](xref:Microsoft.PowerShell.Core.Invoke-Command) cmdlets.</span></span>

<span data-ttu-id="ff9cf-407">`$PSSessionApplicationName`기본 설정 변수는 로컬 컴퓨터에 설정 되지만 원격 컴퓨터의 수신기를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-407">The `$PSSessionApplicationName` preference variable is set on the local computer, but it specifies a listener on the remote computer.</span></span> <span data-ttu-id="ff9cf-408">지정 하는 응용 프로그램 이름이 원격 컴퓨터에 존재 하지 않는 경우 세션을 설정 하는 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-408">If the application name that you specify doesn't exist on the remote computer, the command to establish the session fails.</span></span>

### <a name="pssessionconfigurationname"></a><span data-ttu-id="ff9cf-409">\$PSSessionConfigurationName</span><span class="sxs-lookup"><span data-stu-id="ff9cf-409">\$PSSessionConfigurationName</span></span>

<span data-ttu-id="ff9cf-410">현재 세션에서 생성 된 **pssessions** 에 사용 되는 기본 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-410">Specifies the default session configuration that is used for **PSSessions** created in the current session.</span></span>

<span data-ttu-id="ff9cf-411">이 기본 설정 변수는 로컬 컴퓨터에 설정 되지만 원격 컴퓨터에 있는 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-411">This preference variable is set on the local computer, but it specifies a session configuration that's located on the remote computer.</span></span>

<span data-ttu-id="ff9cf-412">변수의 값은 정규화 된 `$PSSessionConfigurationName` 리소스 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-412">The value of the `$PSSessionConfigurationName` variable is a fully qualified resource URI.</span></span>

<span data-ttu-id="ff9cf-413">기본값은 `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` 원격 컴퓨터의 **Microsoft PowerShell** 세션 구성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-413">The default value `http://schemas.microsoft.com/PowerShell/microsoft.PowerShell` indicates the **Microsoft.PowerShell** session configuration on the remote computer.</span></span>

<span data-ttu-id="ff9cf-414">구성 이름만 지정 하는 경우 다음 스키마 URI가 앞에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-414">If you specify only a configuration name, the following schema URI is prepended:</span></span>

`http://schemas.microsoft.com/PowerShell/`

<span data-ttu-id="ff9cf-415">, 또는 cmdlet의 **ConfigurationName** 매개 변수를 사용 하 여 기본값을 재정의 하 고 특정 세션에 대해 다른 세션 구성을 선택할 수 있습니다 `New-PSSession` `Enter-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-415">You can override the default and select a different session configuration for a particular session by using the **ConfigurationName** parameter of the `New-PSSession`, `Enter-PSSession`, or `Invoke-Command` cmdlets.</span></span>

<span data-ttu-id="ff9cf-416">언제 든 지이 변수의 값을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-416">You can change the value of this variable at any time.</span></span> <span data-ttu-id="ff9cf-417">이 작업을 수행 하는 경우 선택한 세션 구성이 원격 컴퓨터에 존재 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-417">When you do, remember that the session configuration that you select must exist on the remote computer.</span></span> <span data-ttu-id="ff9cf-418">그렇지 않으면 세션 구성을 사용 하는 세션을 만드는 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-418">If it doesn't, the command to create a session that uses the session configuration fails.</span></span>

<span data-ttu-id="ff9cf-419">이 기본 설정 변수는 원격 사용자가이 컴퓨터에 연결 되는 세션을 만들 때 사용 되는 로컬 세션 구성을 결정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-419">This preference variable doesn't determine which local session configurations are used when remote users create a session that connects to this computer.</span></span>
<span data-ttu-id="ff9cf-420">그러나 로컬 세션 구성에 대 한 사용 권한을 사용 하 여 사용자가 사용할 수 있는 사용자를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-420">However, you can use the permissions for the local session configurations to determine which users may use them.</span></span>

### <a name="pssessionoption"></a><span data-ttu-id="ff9cf-421">\$PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="ff9cf-421">\$PSSessionOption</span></span>

<span data-ttu-id="ff9cf-422">원격 세션의 고급 사용자 옵션에 대 한 기본값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-422">Establishes the default values for advanced user options in a remote session.</span></span>
<span data-ttu-id="ff9cf-423">이러한 옵션 기본 설정은 세션 옵션에 대 한 시스템 기본값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-423">These option preferences override the system default values for session options.</span></span>

<span data-ttu-id="ff9cf-424">`$PSSessionOption`변수는 **Pssessionoption** 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-424">The `$PSSessionOption` variable contains a **PSSessionOption** object.</span></span> <span data-ttu-id="ff9cf-425">자세한 내용은 System.web. n a m p. n a m a [옵션](/dotnet/api/system.management.automation.remoting.pssessionoption)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-425">For more information, see [System.Management.Automation.Remoting.PSSessionOption](/dotnet/api/system.management.automation.remoting.pssessionoption).</span></span>
<span data-ttu-id="ff9cf-426">개체의 각 속성은 session 옵션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-426">Each property of the object represents a session option.</span></span> <span data-ttu-id="ff9cf-427">예를 들어 **Nocompression** 속성은 세션 중에 데이터 압축을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-427">For example, the **NoCompression** property turns of data compression during the session.</span></span>

<span data-ttu-id="ff9cf-428">기본적으로이 `$PSSessionOption` 변수는 아래와 같이 모든 옵션에 대 한 기본값을 포함 하는 **Pssessionoption** 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-428">By default, the `$PSSessionOption` variable contains a **PSSessionOption** object with the default values for all options, as shown below.</span></span>

```Output
MaximumConnectionRedirectionCount : 5
NoCompression                     : False
NoMachineProfile                  : False
ProxyAccessType                   : None
ProxyAuthentication               : Negotiate
ProxyCredential                   :
SkipCACheck                       : False
SkipCNCheck                       : False
SkipRevocationCheck               : False
OperationTimeout                  : 00:03:00
NoEncryption                      : False
UseUTF16                          : False
IncludePortInSPN                  : False
OutputBufferingMode               : None
Culture                           :
UICulture                         :
MaximumReceivedDataSizePerCommand :
MaximumReceivedObjectSize         : 209715200
ApplicationArguments              :
OpenTimeout                       : 00:03:00
CancelTimeout                     : 00:01:00
IdleTimeout                       : -00:00:00.0010000
```

<span data-ttu-id="ff9cf-429">이러한 옵션에 대 한 설명 및 자세한 내용은 [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-429">For descriptions of these options and more information, see [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span> <span data-ttu-id="ff9cf-430">원격 명령 및 세션에 대 한 자세한 내용은 [about_Remote](about_Remote.md) 및 [about_PSSessions](about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-430">For more information about remote commands and sessions, see [about_Remote](about_Remote.md) and [about_PSSessions](about_PSSessions.md).</span></span>

<span data-ttu-id="ff9cf-431">기본 설정 변수의 값을 변경 하려면 `$PSSessionOption` cmdlet을 사용 하 여 `New-PSSessionOption` 원하는 옵션 값을 사용 하 여 **pssessionoption** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-431">To change the value of the `$PSSessionOption` preference variable, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object with the option values you prefer.</span></span> <span data-ttu-id="ff9cf-432">출력을 이라는 변수에 저장 `$PSSessionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-432">Save the output in a variable called `$PSSessionOption`.</span></span>

```powershell
$PSSessionOption = New-PSSessionOption -NoCompression
```

<span data-ttu-id="ff9cf-433">`$PSSessionOption`모든 powershell 세션에서 기본 설정 변수를 사용 하려면 `New-PSSessionOption` `$PSSessionOption` powershell 프로필에 변수를 만드는 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-433">To use the `$PSSessionOption` preference variable in every PowerShell session, add a `New-PSSessionOption` command that creates the `$PSSessionOption` variable to your PowerShell profile.</span></span> <span data-ttu-id="ff9cf-434">자세한 내용은 [about_Profiles](about_Profiles.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-434">For more information, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="ff9cf-435">특정 원격 세션에 대 한 사용자 지정 옵션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-435">You can set custom options for a particular remote session.</span></span> <span data-ttu-id="ff9cf-436">설정 하는 옵션은 시스템 기본값 및 기본 설정 변수의 값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-436">The options that you set take precedence over the system defaults and the value of the `$PSSessionOption` preference variable.</span></span>

<span data-ttu-id="ff9cf-437">사용자 지정 세션 옵션을 설정 하려면 cmdlet을 사용 `New-PSSessionOption` 하 여 **Pssessionoption** 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-437">To set custom session options, use the `New-PSSessionOption` cmdlet to create a **PSSessionOption** object.</span></span> <span data-ttu-id="ff9cf-438">그런 다음 세션을 만드는 cmdlet의 **sessionoption** 매개 변수 값으로 **pssessionoption** 개체를 사용 합니다 (예: `New-PSSession` , 및) `Enter-PSSession` `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-438">Then, use the **PSSessionOption** object as the value of the **SessionOption** parameter in cmdlets that create a session, such as `New-PSSession`, `Enter-PSSession`, and `Invoke-Command`.</span></span>

### <a name="transcript"></a><span data-ttu-id="ff9cf-439">$Transcript</span><span class="sxs-lookup"><span data-stu-id="ff9cf-439">$Transcript</span></span>

<span data-ttu-id="ff9cf-440">에서 기록 `Start-Transcript` 파일의 이름과 위치를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-440">Used by `Start-Transcript` to specify the name and location of the transcript file.</span></span> <span data-ttu-id="ff9cf-441">**Path** 매개 변수의 값을 지정 하지 않으면는 `Start-Transcript` 전역 변수 값의 경로를 사용 합니다 `$Transcript` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-441">If you do not specify a value for the **Path** parameter, `Start-Transcript` uses the path in the value of the `$Transcript` global variable.</span></span> <span data-ttu-id="ff9cf-442">이 변수를 만들지 않은 경우는 `Start-Transcript` 디렉터리에 있는 기록을 파일로 저장 합니다 `$Home\My Documents` `\PowerShell_transcript.<time-stamp>.txt` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-442">If you have not created this variable, `Start-Transcript` stores the transcripts in the `$Home\My Documents` directory as `\PowerShell_transcript.<time-stamp>.txt` files.</span></span>

### <a name="verbosepreference"></a><span data-ttu-id="ff9cf-443">\$VerbosePreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-443">\$VerbosePreference</span></span>

<span data-ttu-id="ff9cf-444">PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 자세한 정보 메시지 (예: [쓰기 세부 정보](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet에 의해 생성 된 메시지)에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-444">Determines how PowerShell responds to verbose messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Verbose](xref:Microsoft.PowerShell.Utility.Write-Verbose) cmdlet.</span></span>
<span data-ttu-id="ff9cf-445">자세한 정보 메시지는 명령을 실행 하기 위해 수행 된 작업을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-445">Verbose messages describe the actions performed to execute a command.</span></span>

<span data-ttu-id="ff9cf-446">기본적으로 자세한 정보 표시 메시지는 표시 되지 않지만 값을 변경 하 여이 동작을 변경할 수 있습니다 `$VerbosePreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-446">By default, verbose messages aren't displayed, but you can change this behavior by changing the value of `$VerbosePreference`.</span></span>

<span data-ttu-id="ff9cf-447">Cmdlet의 **verbose** 일반 매개 변수를 사용 하 여 특정 명령에 대 한 자세한 정보 메시지를 표시 하거나 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-447">You can use the **Verbose** common parameter of a cmdlet to display or hide the verbose messages for a specific command.</span></span> <span data-ttu-id="ff9cf-448">자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-448">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="ff9cf-449">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-449">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-450">**Stop** : 자세한 정보 메시지와 오류 메시지를 표시 한 후 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-450">**Stop** : Displays the verbose message and an error message and then stops executing.</span></span>
- <span data-ttu-id="ff9cf-451">**Inquire** : 자세한 정보 표시 메시지를 표시 한 다음 계속할지 여부를 묻는 프롬프트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-451">**Inquire** : Displays the verbose message and then displays a prompt that asks you whether you want to continue.</span></span>
- <span data-ttu-id="ff9cf-452">**Continue** : 자세한 정보 메시지를 표시 한 다음 실행을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-452">**Continue** : Displays the verbose message and then continues with execution.</span></span>
- <span data-ttu-id="ff9cf-453">**SilentlyContinue** : (기본값)는 자세한 정보 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-453">**SilentlyContinue** : (Default) Doesn't display the verbose message.</span></span> <span data-ttu-id="ff9cf-454">계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-454">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-455">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-455">Examples</span></span>

<span data-ttu-id="ff9cf-456">이러한 예제에서는의 여러 값 `$VerbosePreference` 과 **Verbose** 매개 변수를 통해 기본 설정 값을 재정의 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-456">These examples show the effect of the different values of `$VerbosePreference` and the **Verbose** parameter to override the preference value.</span></span>

<span data-ttu-id="ff9cf-457">이 예에서는 기본값 인 **SilentlyContinue** 값의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-457">This example shows the effect of the **SilentlyContinue** value, that is the default.</span></span> <span data-ttu-id="ff9cf-458">이 명령은 **message** 매개 변수를 사용 하지만 PowerShell 콘솔에는 메시지를 쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-458">The command uses the **Message** parameter, but doesn't write a message to the PowerShell console.</span></span>

```powershell
Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="ff9cf-459">**Verbose** 매개 변수를 사용 하면 메시지가 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-459">When the **Verbose** parameter is used, the message is written.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="ff9cf-460">이 예에서는 **Continue** 값의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-460">This example shows the effect of the **Continue** value.</span></span> <span data-ttu-id="ff9cf-461">`$VerbosePreference`변수가 **Continue** 로 설정 되 고 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-461">The `$VerbosePreference` variable is set to **Continue** and the message is displayed.</span></span>

```powershell
$VerbosePreference = "Continue"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
```

<span data-ttu-id="ff9cf-462">이 예에서는 Continue 값을 재정의 하는 값을 사용 하 여 **Verbose** 매개 변수를 사용 `$false` 합니다. **Continue**</span><span class="sxs-lookup"><span data-stu-id="ff9cf-462">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Continue** value.</span></span> <span data-ttu-id="ff9cf-463">메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-463">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="ff9cf-464">이 예에서는 **Stop** 값의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-464">This example shows the effect of the **Stop** value.</span></span> <span data-ttu-id="ff9cf-465">`$VerbosePreference`변수가 **Stop** 으로 설정 되 고 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-465">The `$VerbosePreference` variable is set to **Stop** and the message is displayed.</span></span> <span data-ttu-id="ff9cf-466">명령이 중지 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-466">The command is stopped.</span></span>

```powershell
$VerbosePreference = "Stop"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.
Write-Verbose : The running command stopped because the preference variable
  "VerbosePreference" or common parameter is set to Stop: Verbose message test.
At line:1 char:1
+ Write-Verbose -Message "Verbose message test."
```

<span data-ttu-id="ff9cf-467">이 예에서는 Stop 값을 재정의 하는 값을 사용 하 여 **Verbose** 매개 변수를 사용 `$false` 합니다. **Stop**</span><span class="sxs-lookup"><span data-stu-id="ff9cf-467">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Stop** value.</span></span> <span data-ttu-id="ff9cf-468">메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-468">The message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

<span data-ttu-id="ff9cf-469">이 예에서는 **Inquire** 값의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-469">This example shows the effect of the **Inquire** value.</span></span> <span data-ttu-id="ff9cf-470">`$VerbosePreference`변수가 **Inquire** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-470">The `$VerbosePreference` variable is set to **Inquire**.</span></span> <span data-ttu-id="ff9cf-471">메시지가 표시 되 고 사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-471">The message is displayed and the user is prompted for confirmation.</span></span>

```powershell
$VerbosePreference = "Inquire"
Write-Verbose -Message "Verbose message test."
```

```Output
VERBOSE: Verbose message test.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="ff9cf-472">이 예에서는 Inquire 값을 재정의 하는 값을 사용 하 여 **Verbose** 매개 변수를 사용 `$false` 합니다. **Inquire**</span><span class="sxs-lookup"><span data-stu-id="ff9cf-472">This example uses the **Verbose** parameter with a value of `$false` that overrides the **Inquire** value.</span></span> <span data-ttu-id="ff9cf-473">사용자에 게 메시지가 표시 되지 않고 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-473">The user isn't prompted and the message isn't displayed.</span></span>

```powershell
Write-Verbose -Message "Verbose message test." -Verbose:$false
```

### <a name="warningpreference"></a><span data-ttu-id="ff9cf-474">\$WarningPreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-474">\$WarningPreference</span></span>

<span data-ttu-id="ff9cf-475">PowerShell에서 스크립트, cmdlet 또는 공급자에 의해 생성 된 경고 메시지 (예: [쓰기-경고](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet에 의해 생성 된 메시지)에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-475">Determines how PowerShell responds to warning messages generated by a script, cmdlet, or provider, such as the messages generated by the [Write-Warning](xref:Microsoft.PowerShell.Utility.Write-Warning) cmdlet.</span></span>

<span data-ttu-id="ff9cf-476">기본적으로 경고 메시지가 표시 되 고 실행이 계속 되지만의 값을 변경 하 여이 동작을 변경할 수 있습니다 `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-476">By default, warning messages are displayed and execution continues, but you can change this behavior by changing the value of `$WarningPreference`.</span></span>

<span data-ttu-id="ff9cf-477">Cmdlet의 **WarningAction** 일반 매개 변수를 사용 하 여 PowerShell이 특정 명령의 경고에 응답 하는 방법을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-477">You can use the **WarningAction** common parameter of a cmdlet to determine how PowerShell responds to warnings from a particular command.</span></span> <span data-ttu-id="ff9cf-478">자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-478">For more information, see [about_CommonParameters](about_CommonParameters.md).</span></span>

<span data-ttu-id="ff9cf-479">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-479">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-480">**Stop** : 경고 메시지와 오류 메시지를 표시 한 다음 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-480">**Stop** : Displays the warning message and an error message and then stops executing.</span></span>
- <span data-ttu-id="ff9cf-481">**Inquire** : 경고 메시지를 표시 한 다음 사용 권한을 계속 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-481">**Inquire** : Displays the warning message and then prompts for permission to continue.</span></span>
- <span data-ttu-id="ff9cf-482">**Continue** : (기본값) 경고 메시지를 표시 한 다음 실행을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-482">**Continue** : (Default) Displays the warning message and then continues executing.</span></span>
- <span data-ttu-id="ff9cf-483">**SilentlyContinue** : 경고 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-483">**SilentlyContinue** : Doesn't display the warning message.</span></span> <span data-ttu-id="ff9cf-484">계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-484">Continues executing.</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-485">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-485">Examples</span></span>

<span data-ttu-id="ff9cf-486">이러한 예제에서는의 다른 값에 대 한 결과를 보여 줍니다 `$WarningPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-486">These examples show the effect of the different values of `$WarningPreference`.</span></span>
<span data-ttu-id="ff9cf-487">**WarningAction** 매개 변수는 기본 설정 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-487">The **WarningAction** parameter overrides the preference value.</span></span>

<span data-ttu-id="ff9cf-488">이 예에서는 기본 값인 **Continue** 를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-488">This example shows the effect of the default value, **Continue**.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
```

<span data-ttu-id="ff9cf-489">이 예제에서는 값이 **SilentlyContinue** 인 **WarningAction** 매개 변수를 사용 하 여 경고를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-489">This example uses the **WarningAction** parameter with the value **SilentlyContinue** to suppress the warning.</span></span> <span data-ttu-id="ff9cf-490">메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-490">The message isn't displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="ff9cf-491">이 예에서는 `$WarningPreference` 변수를 **SilentlyContinue** 값으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-491">This example changes the `$WarningPreference` variable to the **SilentlyContinue** value.</span></span> <span data-ttu-id="ff9cf-492">메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-492">The message isn't displayed.</span></span>

```powershell
$WarningPreference = "SilentlyContinue"
$m = "This action can delete data."
Write-Warning -Message $m
```

<span data-ttu-id="ff9cf-493">이 예에서는 **WarningAction** 매개 변수를 사용 하 여 경고가 생성 되 면 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-493">This example uses the **WarningAction** parameter to stop when a warning is generated.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Stop
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m -WarningAction Stop
```

<span data-ttu-id="ff9cf-494">이 예에서는 `$WarningPreference` 변수를 **Inquire** 값으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-494">This example changes the `$WarningPreference` variable to the **Inquire** value.</span></span> <span data-ttu-id="ff9cf-495">사용자에 게 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-495">The user is prompted for confirmation.</span></span>

```powershell
$WarningPreference = "Inquire"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

<span data-ttu-id="ff9cf-496">이 예제에서는 값이 **SilentlyContinue** 인 **WarningAction** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-496">This example uses the **WarningAction** parameter with the value **SilentlyContinue**.</span></span> <span data-ttu-id="ff9cf-497">명령은 계속 실행 되며 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-497">The command continues to execute and no message is displayed.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction SilentlyContinue
```

<span data-ttu-id="ff9cf-498">이 예에서는 `$WarningPreference` 값을 **중지** 로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-498">This example changes the `$WarningPreference` value to **Stop**.</span></span>

```powershell
$WarningPreference = "Stop"
$m = "This action can delete data."
Write-Warning -Message $m
```

```Output
WARNING: This action can delete data.
Write-Warning : The running command stopped because the preference variable
  "WarningPreference" or common parameter is set to Stop:
    This action can delete data.
At line:1 char:1
+ Write-Warning -Message $m
```

<span data-ttu-id="ff9cf-499">이 예에서는 **WarningAction** 를 **Inquire** 값과 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-499">This example uses the **WarningAction** with the **Inquire** value.</span></span> <span data-ttu-id="ff9cf-500">경고가 발생 하면 사용자에 게 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-500">The user is prompted when a warning occurs.</span></span>

```powershell
$m = "This action can delete data."
Write-Warning -Message $m -WarningAction Inquire
```

```Output
WARNING: This action can delete data.

Confirm
Continue with this operation?
[Y] Yes  [A] Yes to All  [H] Halt Command  [?] Help (default is "Y"):
```

### <a name="whatifpreference"></a><span data-ttu-id="ff9cf-501">\$방식으로 whatifpreference</span><span class="sxs-lookup"><span data-stu-id="ff9cf-501">\$WhatIfPreference</span></span>

<span data-ttu-id="ff9cf-502">이를 지 원하는 모든 명령에 대해 **WhatIf** 를 자동으로 사용할지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-502">Determines whether **WhatIf** is automatically enabled for every command that supports it.</span></span> <span data-ttu-id="ff9cf-503">**WhatIf** 를 사용 하는 경우 cmdlet은 명령의 예상 효과를 보고 하지만 명령을 실행 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-503">When **WhatIf** is enabled, the cmdlet reports the expected effect of the command, but doesn't execute the command.</span></span>

<span data-ttu-id="ff9cf-504">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-504">The valid values are as follows:</span></span>

- <span data-ttu-id="ff9cf-505">**False** ( **0** , 사용 안 함): (기본값) **WhatIf** 가 자동으로 사용 하도록 설정 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-505">**False** ( **0** , not enabled): (Default) **WhatIf** isn't automatically enabled.</span></span> <span data-ttu-id="ff9cf-506">수동으로 사용 하도록 설정 하려면 cmdlet의 **WhatIf** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-506">To enable it manually, use the cmdlet's **WhatIf** parameter.</span></span>
- <span data-ttu-id="ff9cf-507">**True** ( **1** , enabled): **WhatIf** 는이를 지 원하는 모든 명령에서 자동으로 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-507">**True** ( **1** , enabled): **WhatIf** is automatically enabled on any command that supports it.</span></span> <span data-ttu-id="ff9cf-508">사용자는 값이 **False** 인 **WhatIf** 매개 변수를 사용 하 여와 같이 수동으로 비활성화할 수 있습니다 `-WhatIf:$false` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-508">Users can use the **WhatIf** parameter with a value of **False** to disable it manually, such as `-WhatIf:$false`.</span></span>

#### <a name="examples"></a><span data-ttu-id="ff9cf-509">예</span><span class="sxs-lookup"><span data-stu-id="ff9cf-509">Examples</span></span>

<span data-ttu-id="ff9cf-510">이러한 예제에서는의 다른 값에 대 한 결과를 보여 줍니다 `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-510">These examples show the effect of the different values of `$WhatIfPreference`.</span></span>
<span data-ttu-id="ff9cf-511">**WhatIf** 매개 변수를 사용 하 여 특정 명령에 대 한 기본 설정 값을 재정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-511">They show how to use the **WhatIf** parameter to override the preference value for a specific command.</span></span>

<span data-ttu-id="ff9cf-512">이 예에서는 `$WhatIfPreference` 변수를 기본값인 **False** 로 설정 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-512">This example shows the effect of the `$WhatIfPreference` variable set to the default value, **False**.</span></span> <span data-ttu-id="ff9cf-513">`Get-ChildItem`파일이 있는지 확인 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-513">Use `Get-ChildItem` to verify that the file exists.</span></span>
<span data-ttu-id="ff9cf-514">`Remove-Item` 파일을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-514">`Remove-Item` deletes the file.</span></span> <span data-ttu-id="ff9cf-515">파일이 삭제 된 후에는를 사용 하 여 삭제를 확인할 수 있습니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-515">After the file is deleted, you can verify the deletion with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path .\test.txt
Remove-Item -Path ./test.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           9/13/2019    10:53             10 test.txt
```

```powershell
Get-ChildItem -Path .\test.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -File test.txt
```

<span data-ttu-id="ff9cf-516">이 예에서는의 값이 **WhatIf** `$WhatIfPreference` **False** 인 경우 WhatIf 매개 변수를 사용 하는 경우의 효과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-516">This example shows the effect of using the **WhatIf** parameter when the value of `$WhatIfPreference` is **False**.</span></span>

<span data-ttu-id="ff9cf-517">파일이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-517">Verify that the file exists.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="ff9cf-518">**WhatIf** 매개 변수를 사용 하 여 파일을 삭제 하려는 시도의 결과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-518">Use the **WhatIf** parameter to determine the result of attempting to delete the file.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
``````

<span data-ttu-id="ff9cf-519">파일이 삭제 되지 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-519">Verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="ff9cf-520">이 예에서는 `$WhatIfPreference` 변수 값을 **True** 로 설정 하는 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-520">This example shows the effect of the `$WhatIfPreference` variable set to the value, **True**.</span></span> <span data-ttu-id="ff9cf-521">를 사용 하 여 파일을 삭제 하면 파일 `Remove-Item` 의 경로가 표시 되지만 파일은 삭제 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-521">When you use `Remove-Item` to delete a file, the file's path is displayed, but the file isn't deleted.</span></span>

<span data-ttu-id="ff9cf-522">파일을 삭제 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-522">Attempt to delete a file.</span></span> <span data-ttu-id="ff9cf-523">`Remove-Item`가 실행 되었지만 파일이 삭제 되지 않은 경우 발생 하는 상황에 대 한 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-523">A message is displayed about what would happen if `Remove-Item` was run, but the file isn't deleted.</span></span>

```powershell
$WhatIfPreference = "True"
Remove-Item -Path .\test2.txt
```

```Output
What if: Performing the operation "Remove File" on target "C:\Test\test2.txt".
```

<span data-ttu-id="ff9cf-524">`Get-ChildItem`를 사용 하 여 파일이 삭제 되지 않았는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-524">Use `Get-ChildItem` to verify that the file wasn't deleted.</span></span>

```powershell
Get-ChildItem -Path .\test2.txt
```

```Output
    Directory: C:\Test

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/28/2019    17:06             12 test2.txt
```

<span data-ttu-id="ff9cf-525">이 예에서는의 값이 True 일 때 파일을 삭제 하는 방법을 보여 줍니다 `$WhatIfPreference` . **True**</span><span class="sxs-lookup"><span data-stu-id="ff9cf-525">This example shows how to delete a file when the value of `$WhatIfPreference` is **True**.</span></span> <span data-ttu-id="ff9cf-526">이 메서드는 값이 인 **WhatIf** 매개 변수를 사용 `$false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-526">It uses the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="ff9cf-527">`Get-ChildItem`파일이 삭제 되었는지 확인 하는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-527">Use `Get-ChildItem` to verify the file was deleted.</span></span>

```powershell
Remove-Item -Path .\test2.txt -WhatIf:$false
Get-ChildItem -Path .\test2.txt
```

```Output
Get-ChildItem : Cannot find path 'C:\Test\test2.txt' because it does not exist.
At line:1 char:1
+ Get-ChildItem -Path .\test2.txt
```

<span data-ttu-id="ff9cf-528">다음은 whatif `Get-Process` 를 지원 하지 **WhatIf** 않고 `Stop-Process` **whatif** 를 지 원하는 cmdlet의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-528">The following are examples of the `Get-Process` cmdlet that doesn't support **WhatIf** and `Stop-Process` that does support **WhatIf**.</span></span> <span data-ttu-id="ff9cf-529">`$WhatIfPreference`변수의 값이 **True** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-529">The `$WhatIfPreference` variable's value is **True**.</span></span>

<span data-ttu-id="ff9cf-530">`Get-Process` 는 **WhatIf** 를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-530">`Get-Process` doesn't support **WhatIf**.</span></span> <span data-ttu-id="ff9cf-531">명령이 실행 되 면 **winword.exe** 프로세스를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-531">When the command is executed, it displays the **Winword** process.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    130   119.84     173.38       8.39   15024   4 WINWORD
```

<span data-ttu-id="ff9cf-532">`Stop-Process` 는 **WhatIf** 를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-532">`Stop-Process` does support **WhatIf**.</span></span> <span data-ttu-id="ff9cf-533">**Winword.exe** 프로세스가 중지 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-533">The **Winword** process isn't stopped.</span></span>

```powershell
Stop-Process -Name Winword
```

```Output
What if: Performing the operation "Stop-Process" on target "WINWORD (15024)".
```

<span data-ttu-id="ff9cf-534">`Stop-Process`값과 함께 **whatif** 매개 변수를 사용 하 여 **whatif** 동작을 재정의할 수 있습니다 `$false` .</span><span class="sxs-lookup"><span data-stu-id="ff9cf-534">You can override the `Stop-Process` **WhatIf** behavior by using the **WhatIf** parameter with a value of `$false`.</span></span> <span data-ttu-id="ff9cf-535">**Winword.exe** 프로세스가 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-535">The **Winword** process is stopped.</span></span>

```powershell
Stop-Process -Name Winword -WhatIf:$false
```

<span data-ttu-id="ff9cf-536">**Winword.exe** 프로세스가 중지 되었는지 확인 하려면를 사용 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff9cf-536">To verify that the **Winword** process was stopped, use `Get-Process`.</span></span>

```powershell
Get-Process -Name Winword
```

```Output
Get-Process : Cannot find a process with the name "Winword".
  Verify the process name and call the cmdlet again.
At line:1 char:1
+ Get-Process -Name Winword
```

## <a name="see-also"></a><span data-ttu-id="ff9cf-537">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff9cf-537">See also</span></span>

[<span data-ttu-id="ff9cf-538">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="ff9cf-538">about_Automatic_Variables</span></span>](about_Automatic_Variables.md)

[<span data-ttu-id="ff9cf-539">about_CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff9cf-539">about_CommonParameters</span></span>](about_CommonParameters.md)

[<span data-ttu-id="ff9cf-540">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="ff9cf-540">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="ff9cf-541">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="ff9cf-541">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="ff9cf-542">about_Remote</span><span class="sxs-lookup"><span data-stu-id="ff9cf-542">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="ff9cf-543">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="ff9cf-543">about_Scopes</span></span>](about_Scopes.md)

[<span data-ttu-id="ff9cf-544">about_Variables</span><span class="sxs-lookup"><span data-stu-id="ff9cf-544">about_Variables</span></span>](about_Variables.md)
