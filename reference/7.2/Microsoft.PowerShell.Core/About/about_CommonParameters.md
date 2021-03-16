---
description: 모든 cmdlet에 사용할 수 있는 매개 변수에 대해 설명 합니다.
Locale: en-US
ms.date: 11/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_commonparameters?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_CommonParameters
ms.openlocfilehash: 44503e9c251cd3cccf9b879ceb71262c65d8e5e9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99602240"
---
# <a name="about-commonparameters"></a><span data-ttu-id="40715-103">CommonParameters 정보</span><span class="sxs-lookup"><span data-stu-id="40715-103">About CommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="40715-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="40715-104">SHORT DESCRIPTION</span></span>

<span data-ttu-id="40715-105">모든 cmdlet에 사용할 수 있는 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-105">Describes the parameters that can be used with any cmdlet.</span></span>

## <a name="long-description"></a><span data-ttu-id="40715-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="40715-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="40715-107">일반 매개 변수는 cmdlet에서 사용할 수 있는 cmdlet 매개 변수 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-107">The common parameters are a set of cmdlet parameters that you can use with any cmdlet.</span></span> <span data-ttu-id="40715-108">이러한 cmdlet은 cmdlet 개발자가 아닌 PowerShell에서 구현 되며 cmdlet에서 자동으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-108">They're implemented by PowerShell, not by the cmdlet developer, and they're automatically available to any cmdlet.</span></span>

<span data-ttu-id="40715-109">모든 cmdlet에는 일반 매개 변수를 사용할 수 있지만 모든 cmdlet에는 영향을 주지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-109">You can use the common parameters with any cmdlet, but they might not have an effect on all cmdlets.</span></span> <span data-ttu-id="40715-110">예를 들어 cmdlet이 자세한 정보 표시 출력을 생성 하지 않는 경우 **verbose** 일반 매개 변수를 사용 해도 아무런 효과가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-110">For example, if a cmdlet doesn't generate any verbose output, using the **Verbose** common parameter has no effect.</span></span>

<span data-ttu-id="40715-111">Common 매개 변수는 **Cmdletbinding** 특성 또는 **Parameter** 특성을 사용 하는 고급 함수 에서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-111">The common parameters are also available on advanced functions that use the **CmdletBinding** attribute or the **Parameter** attribute.</span></span>

<span data-ttu-id="40715-112">여러 일반 매개 변수가 시스템 기본값 또는 PowerShell 기본 설정 변수를 사용 하 여 설정 하는 기본 설정을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-112">Several common parameters override system defaults or preferences that you set by using the PowerShell preference variables.</span></span> <span data-ttu-id="40715-113">기본 설정 변수와 달리 일반 매개 변수는 해당 매개 변수가 사용 되는 명령에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="40715-113">Unlike the preference variables, the common parameters affect only the commands in which they're used.</span></span>

<span data-ttu-id="40715-114">자세한 내용은 [about_Preference_Variables](./about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40715-114">For more information, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

<span data-ttu-id="40715-115">다음 목록에는 일반 매개 변수가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-115">The following list displays the common parameters.</span></span> <span data-ttu-id="40715-116">해당 별칭은 괄호 안에 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-116">Their aliases are listed in parentheses.</span></span>

- <span data-ttu-id="40715-117">**Debug**(db)</span><span class="sxs-lookup"><span data-stu-id="40715-117">**Debug** (db)</span></span>
- <span data-ttu-id="40715-118">**Erroraction** (ea)</span><span class="sxs-lookup"><span data-stu-id="40715-118">**ErrorAction** (ea)</span></span>
- <span data-ttu-id="40715-119">**Errorvariable** (ev)</span><span class="sxs-lookup"><span data-stu-id="40715-119">**ErrorVariable** (ev)</span></span>
- <span data-ttu-id="40715-120">**Informationaction** (infa)</span><span class="sxs-lookup"><span data-stu-id="40715-120">**InformationAction** (infa)</span></span>
- <span data-ttu-id="40715-121">**Informationvariable** (iv)</span><span class="sxs-lookup"><span data-stu-id="40715-121">**InformationVariable** (iv)</span></span>
- <span data-ttu-id="40715-122">**OutVariable** (ov-es)</span><span class="sxs-lookup"><span data-stu-id="40715-122">**OutVariable** (ov)</span></span>
- <span data-ttu-id="40715-123">**OutBuffer** (ob)</span><span class="sxs-lookup"><span data-stu-id="40715-123">**OutBuffer** (ob)</span></span>
- <span data-ttu-id="40715-124">**PipelineVariable** (pv)</span><span class="sxs-lookup"><span data-stu-id="40715-124">**PipelineVariable** (pv)</span></span>
- <span data-ttu-id="40715-125">**자세한 정보** 표시 (vb)</span><span class="sxs-lookup"><span data-stu-id="40715-125">**Verbose** (vb)</span></span>
- <span data-ttu-id="40715-126">**WarningAction** (wa)</span><span class="sxs-lookup"><span data-stu-id="40715-126">**WarningAction** (wa)</span></span>
- <span data-ttu-id="40715-127">**WarningVariable** (wv)</span><span class="sxs-lookup"><span data-stu-id="40715-127">**WarningVariable** (wv)</span></span>

<span data-ttu-id="40715-128">**동작** 매개 변수는 **actionpreference** 형식 값입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-128">The **Action** parameters are **ActionPreference** type values.</span></span>
<span data-ttu-id="40715-129">**Actionpreference** 는 다음 값이 포함 된 열거형입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-129">**ActionPreference** is an enumeration with the following values:</span></span>

| <span data-ttu-id="40715-130">Name</span><span class="sxs-lookup"><span data-stu-id="40715-130">Name</span></span>             | <span data-ttu-id="40715-131">값</span><span class="sxs-lookup"><span data-stu-id="40715-131">Value</span></span> |
|------------------|-------|
| <span data-ttu-id="40715-132">일시 중지됨</span><span class="sxs-lookup"><span data-stu-id="40715-132">Suspend</span></span>          | <span data-ttu-id="40715-133">5</span><span class="sxs-lookup"><span data-stu-id="40715-133">5</span></span>     |
| <span data-ttu-id="40715-134">무시</span><span class="sxs-lookup"><span data-stu-id="40715-134">Ignore</span></span>           | <span data-ttu-id="40715-135">4</span><span class="sxs-lookup"><span data-stu-id="40715-135">4</span></span>     |
| <span data-ttu-id="40715-136">문의</span><span class="sxs-lookup"><span data-stu-id="40715-136">Inquire</span></span>          | <span data-ttu-id="40715-137">3</span><span class="sxs-lookup"><span data-stu-id="40715-137">3</span></span>     |
| <span data-ttu-id="40715-138">계속</span><span class="sxs-lookup"><span data-stu-id="40715-138">Continue</span></span>         | <span data-ttu-id="40715-139">2</span><span class="sxs-lookup"><span data-stu-id="40715-139">2</span></span>     |
| <span data-ttu-id="40715-140">중지</span><span class="sxs-lookup"><span data-stu-id="40715-140">Stop</span></span>             | <span data-ttu-id="40715-141">1</span><span class="sxs-lookup"><span data-stu-id="40715-141">1</span></span>     |
| <span data-ttu-id="40715-142">SilentlyContinue</span><span class="sxs-lookup"><span data-stu-id="40715-142">SilentlyContinue</span></span> | <span data-ttu-id="40715-143">0</span><span class="sxs-lookup"><span data-stu-id="40715-143">0</span></span>     |

<span data-ttu-id="40715-144">매개 변수를 사용 하 여 이름이 나 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-144">You may use the name or the value with the parameter.</span></span>

<span data-ttu-id="40715-145">일반 매개 변수 외에도 많은 cmdlet은 위험 완화 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-145">In addition to the common parameters, many cmdlets offer risk mitigation parameters.</span></span> <span data-ttu-id="40715-146">시스템이 나 사용자 데이터에 대 한 위험을 포함 하는 cmdlet은 일반적으로 이러한 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-146">Cmdlets that involve risk to the system or to user data usually offer these parameters.</span></span>

<span data-ttu-id="40715-147">위험 완화 매개 변수는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-147">The risk mitigation parameters are:</span></span>

- <span data-ttu-id="40715-148">**WhatIf** (wi)</span><span class="sxs-lookup"><span data-stu-id="40715-148">**WhatIf** (wi)</span></span>
- <span data-ttu-id="40715-149">**확인** (cf)</span><span class="sxs-lookup"><span data-stu-id="40715-149">**Confirm** (cf)</span></span>

### <a name="common-parameter-descriptions"></a><span data-ttu-id="40715-150">일반 매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="40715-150">COMMON PARAMETER DESCRIPTIONS</span></span>

#### <a name="debug"></a><span data-ttu-id="40715-151">디버그</span><span class="sxs-lookup"><span data-stu-id="40715-151">Debug</span></span>

<span data-ttu-id="40715-152">명령에 의해 수행 된 작업에 대 한 프로그래머 수준의 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-152">Displays programmer-level detail about the operation done by the command.</span></span> <span data-ttu-id="40715-153">이 매개 변수는 명령에서 디버깅 메시지를 생성 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-153">This parameter works only when the command generates a debugging message.</span></span> <span data-ttu-id="40715-154">예를 들어이 매개 변수는 명령에 cmdlet이 포함 되어 있을 때 작동 `Write-Debug` 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-154">For example, this parameter works when a command contains the `Write-Debug` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: db

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-155">기본적으로 `$DebugPreference` 변수 값이 **SilentlyContinue** 이므로 디버깅 메시지가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-155">By default, debugging messages aren't displayed because the value of the `$DebugPreference` variable is **SilentlyContinue**.</span></span>

<span data-ttu-id="40715-156">대화형 모드에서 **Debug** 매개 변수는 `$DebugPreference` 현재 명령의 변수 값을 재정의 하 여의 값을 `$DebugPreference` **Inquire** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-156">In interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Inquire**.</span></span>

<span data-ttu-id="40715-157">비 대화형 모드에서 **Debug** 매개 변수는 현재 명령의 변수 값을 재정의 `$DebugPreference` 하 고의 값을 `$DebugPreference` **계속** 로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-157">In non-interactive mode, the **Debug** parameter overrides the value of the `$DebugPreference` variable for the current command, setting the value of `$DebugPreference` to **Continue**.</span></span>

<span data-ttu-id="40715-158">`-Debug:$true` 와 동일한 효과가 `-Debug` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-158">`-Debug:$true` has the same effect as `-Debug`.</span></span> <span data-ttu-id="40715-159">`-Debug:$false`SilentlyContinue가 아닌 경우 (기본값) 디버깅 메시지를 표시 하지 않으려면를 사용 합니다 `$DebugPreference` . </span><span class="sxs-lookup"><span data-stu-id="40715-159">Use `-Debug:$false` to suppress the display of debugging messages when `$DebugPreference` isn't **SilentlyContinue**, which is the default.</span></span>

#### <a name="erroraction"></a><span data-ttu-id="40715-160">ErrorAction</span><span class="sxs-lookup"><span data-stu-id="40715-160">ErrorAction</span></span>

<span data-ttu-id="40715-161">Cmdlet이 명령에서 종료 되지 않는 오류에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-161">Determines how the cmdlet responds to a non-terminating error from the command.</span></span>
<span data-ttu-id="40715-162">이 매개 변수는 cmdlet의 경우와 같이 명령이 종료 되지 않는 오류를 생성 하는 경우에만 작동 합니다 `Write-Error` .</span><span class="sxs-lookup"><span data-stu-id="40715-162">This parameter works only when the command generates a non-terminating error, such as those from the `Write-Error` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: ea
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-163">**Erroraction** 매개 변수는 `$ErrorActionPreference` 현재 명령에 대 한 변수 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-163">The **ErrorAction** parameter overrides the value of the `$ErrorActionPreference` variable for the current command.</span></span> <span data-ttu-id="40715-164">변수의 기본값은 `$ErrorActionPreference` **계속** 되므로 **erroraction** 매개 변수를 사용 하지 않으면 오류 메시지가 표시 되 고 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-164">Because the default value of the `$ErrorActionPreference` variable is **Continue**, error messages are displayed and execution continues unless you use the **ErrorAction** parameter.</span></span>

<span data-ttu-id="40715-165">**Erroraction** 매개 변수는 명령이 성공적으로 완료 되지 않도록 하는 종료 오류 (예: 누락 된 데이터, 유효 하지 않은 매개 변수 또는 권한 부족)에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-165">The **ErrorAction** parameter has no effect on terminating errors (such as missing data, parameters that aren't valid, or insufficient permissions) that prevent a command from completing successfully.</span></span>

<span data-ttu-id="40715-166">`-ErrorAction:Continue` 오류 메시지를 표시 하 고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-166">`-ErrorAction:Continue` display the error message and continues executing the command.</span></span> <span data-ttu-id="40715-167">기본값은 `Continue`입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-167">`Continue` is the default.</span></span>

<span data-ttu-id="40715-168">`-ErrorAction:Ignore` 오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-168">`-ErrorAction:Ignore` suppresses the error message and continues executing the command.</span></span> <span data-ttu-id="40715-169">**SilentlyContinue** 와 달리 **Ignore** 는 자동 변수에 오류 메시지를 추가 하지 않습니다 `$Error` .</span><span class="sxs-lookup"><span data-stu-id="40715-169">Unlike **SilentlyContinue**, **Ignore** doesn't add the error message to the `$Error` automatic variable.</span></span> <span data-ttu-id="40715-170">**Ignore** 값은 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-170">The **Ignore** value is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="40715-171">`-ErrorAction:Inquire` 오류 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-171">`-ErrorAction:Inquire` displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="40715-172">이 값은 거의 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-172">This value is rarely used.</span></span>

<span data-ttu-id="40715-173">`-ErrorAction:SilentlyContinue` 오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-173">`-ErrorAction:SilentlyContinue` suppresses the error message and continues executing the command.</span></span>

<span data-ttu-id="40715-174">`-ErrorAction:Stop` 오류 메시지를 표시 하 고 명령 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-174">`-ErrorAction:Stop` displays the error message and stops executing the command.</span></span>

<span data-ttu-id="40715-175">`-ErrorAction:Suspend` 는 PowerShell 6 이상에서 지원 되지 않는 워크플로에 대해서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-175">`-ErrorAction:Suspend` is only available for workflows which aren't supported in PowerShell 6 and beyond.</span></span>

> [!NOTE]
> <span data-ttu-id="40715-176">**Erroraction** 매개 변수는를 재정의 하지만 `$ErrorAction` 매개 변수를 명령에서 사용 하 여 스크립트나 함수를 실행할 때 기본 설정 변수의 값을 대체 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-176">The **ErrorAction** parameter overrides, but does not replace the value of the `$ErrorAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="errorvariable"></a><span data-ttu-id="40715-177">ErrorVariable</span><span class="sxs-lookup"><span data-stu-id="40715-177">ErrorVariable</span></span>

<span data-ttu-id="40715-178">**Errorvariable** 은 명령에 대 한 오류 메시지를 지정 된 변수와 `$Error` 자동 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-178">**ErrorVariable** stores error messages about the command in the specified variable and in the `$Error` automatic variable.</span></span> <span data-ttu-id="40715-179">자세한 내용은 [about_Automatic_Variables](about_Automatic_Variables.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40715-179">For more information, see [about_Automatic_Variables](about_Automatic_Variables.md)</span></span>

```yaml
Type: String
Aliases: ev

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-180">기본적으로 새 오류 메시지는 변수에 이미 저장 된 오류 메시지를 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="40715-180">By default, new error messages overwrite error messages that are already stored in the variable.</span></span> <span data-ttu-id="40715-181">변수 내용에 오류 메시지를 추가 하려면 변수 이름 앞에 더하기 기호 ( `+` )를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-181">To append the error message to the variable content, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="40715-182">예를 들어 다음 명령은 변수를 만든 `$a` 다음 오류를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-182">For example, the following command creates the `$a` variable and then stores any errors in it:</span></span>

```powershell
Get-Process -Id 6 -ErrorVariable a
```

<span data-ttu-id="40715-183">다음 명령은 모든 오류 메시지를 변수에 추가 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="40715-183">The following command adds any error messages to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -ErrorVariable +a
```

<span data-ttu-id="40715-184">다음 명령은의 내용을 표시 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="40715-184">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="40715-185">이 매개 변수를 사용 하 여 특정 명령의 오류 메시지만 포함 하는 변수를 만들 수 있으며 자동 변수의 동작에는 영향을 주지 않습니다 `$Error` .</span><span class="sxs-lookup"><span data-stu-id="40715-185">You can use this parameter to create a variable that contains only error messages from specific commands and does not affect the behavior of the `$Error` automatic variable.</span></span> <span data-ttu-id="40715-186">`$Error`자동 변수에는 세션의 모든 명령에 포함 된 오류 메시지가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-186">The `$Error` automatic variable contains error messages from all the commands in the session.</span></span> <span data-ttu-id="40715-187">또는와 같은 배열 표기법을 사용 `$a[0]` 하 여 `$error[1,2]` 변수에 저장 된 특정 오류를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-187">You can use array notation, such as `$a[0]` or `$error[1,2]` to refer to specific errors stored in the variables.</span></span>

> [!NOTE]
> <span data-ttu-id="40715-188">사용자 지정 오류 변수에는 중첩 된 함수 또는 스크립트에 대 한 호출의 오류를 포함 하 여 명령에 의해 생성 된 모든 오류가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-188">The custom error variable contains all errors generated by the command, including errors from calls to nested functions or scripts.</span></span>

#### <a name="informationaction"></a><span data-ttu-id="40715-189">InformationAction</span><span class="sxs-lookup"><span data-stu-id="40715-189">InformationAction</span></span>

<span data-ttu-id="40715-190">PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-190">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="40715-191">사용 되는 명령 또는 스크립트 내에서 **Informationaction** 일반 매개 변수는 `$InformationPreference` 기본적으로 **SilentlyContinue** 로 설정 되는 기본 설정 변수의 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-191">Within the command or script in which it's used, the **InformationAction** common parameter overrides the value of the `$InformationPreference` preference variable, which by default is set to **SilentlyContinue**.</span></span> <span data-ttu-id="40715-192">`Write-Information` **Informationaction** 이 포함 된 스크립트에서를 사용 하는 경우 `Write-Information` **informationaction** 매개 변수의 값에 따라 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-192">When you use `Write-Information` in a script with **InformationAction**, `Write-Information` values are shown depending on the value of the **InformationAction** parameter.</span></span> <span data-ttu-id="40715-193">에 대 한 자세한 내용은 `$InformationPreference` [about_Preference_Variables](./about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40715-193">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

```yaml
Type: ActionPreference
Aliases: ia
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-194">`-InformationAction:Stop` 명령이 발생 한 경우 명령이 나 스크립트를 중지 `Write-Information` 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-194">`-InformationAction:Stop` stops a command or script at an occurrence of the `Write-Information` command.</span></span>

<span data-ttu-id="40715-195">`-InformationAction:Ignore` 정보 메시지를 표시 하지 않고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-195">`-InformationAction:Ignore` suppresses the informational message and continues running the command.</span></span> <span data-ttu-id="40715-196">**SilentlyContinue** 와 달리 **무시** 는 정보 메시지를 완전히 무시 합니다. 정보 스트림에 정보 메시지를 추가 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-196">Unlike **SilentlyContinue**, **Ignore** completely forgets the informational message; it doesn't add the informational message to the information stream.</span></span>

<span data-ttu-id="40715-197">`-InformationAction:Inquire` 명령에 지정한 정보 메시지를 표시 `Write-Information` 한 다음 계속할지 여부를 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-197">`-InformationAction:Inquire` displays the informational message that you specify in a `Write-Information` command, then asks whether you want to continue.</span></span>

<span data-ttu-id="40715-198">`-InformationAction:Continue` 정보 메시지를 표시 하 고 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-198">`-InformationAction:Continue` displays the informational message, and continues running.</span></span>

<span data-ttu-id="40715-199">`-InformationAction:Suspend` 는 워크플로에서만 사용할 수 있으므로 PowerShell Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-199">`-InformationAction:Suspend` isn't supported on PowerShell Core as it is only available for workflows.</span></span>

<span data-ttu-id="40715-200">`-InformationAction:SilentlyContinue` 정보 메시지 (기본값)는 표시 되지 않으며 스크립트는 중단 없이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-200">`-InformationAction:SilentlyContinue` no effect as the informational message aren't (Default) displayed, and the script continues without interruption.</span></span>

> [!NOTE]
> <span data-ttu-id="40715-201">**Informationaction** 매개 변수는를 재정의 하지만 `$InformationAction` 매개 변수를 명령에서 사용 하 여 스크립트나 함수를 실행할 때 기본 설정 변수의 값을 대체 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-201">The **InformationAction** parameter overrides, but does not replace the value of the `$InformationAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="informationvariable"></a><span data-ttu-id="40715-202">InformationVariable</span><span class="sxs-lookup"><span data-stu-id="40715-202">InformationVariable</span></span>

<span data-ttu-id="40715-203">PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-203">Introduced in PowerShell 5.0.</span></span> <span data-ttu-id="40715-204">사용 되는 명령 또는 스크립트 내에서 **informationvariable** 일반 매개 변수는 명령을 추가 하 여 지정한 문자열을 변수에 저장 합니다 `Write-Information` .</span><span class="sxs-lookup"><span data-stu-id="40715-204">Within the command or script in which it's used, the **InformationVariable** common parameter stores in a variable a string that you specify by adding the `Write-Information` command.</span></span> <span data-ttu-id="40715-205">`Write-Information` 값은 **Informationaction** 일반 매개 변수의 값에 따라 표시 됩니다. **Informationaction** 일반 매개 변수를 추가 하지 않으면 `Write-Information` 기본 설정 변수의 값에 따라 문자열이 표시 됩니다 `$InformationPreference` .</span><span class="sxs-lookup"><span data-stu-id="40715-205">`Write-Information` values are shown depending on the value of the **InformationAction** common parameter; if you don't add the **InformationAction** common parameter, `Write-Information` strings are shown depending on the value of the `$InformationPreference` preference variable.</span></span> <span data-ttu-id="40715-206">에 대 한 자세한 내용은 `$InformationPreference` [about_Preference_Variables](./about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40715-206">For more information about `$InformationPreference`, see [about_Preference_Variables](./about_Preference_Variables.md).</span></span>

> [!NOTE]
> <span data-ttu-id="40715-207">정보 변수에는 중첩 된 함수 또는 스크립트에 대 한 호출의 정보 메시지를 포함 하 여 명령에 의해 생성 된 모든 정보 메시지가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-207">The information variable contains all information messages generated by the command, including information messages from calls to nested functions or scripts.</span></span>

```yaml
Type: String
Aliases: iv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

#### <a name="outbuffer"></a><span data-ttu-id="40715-208">OutBuffer</span><span class="sxs-lookup"><span data-stu-id="40715-208">OutBuffer</span></span>

<span data-ttu-id="40715-209">파이프라인을 통해 개체가 전송 되기 전에 버퍼에 누적 되는 개체 수를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-209">Determines the number of objects to accumulate in a buffer before any objects are sent through the pipeline.</span></span> <span data-ttu-id="40715-210">이 매개 변수를 생략 하면 개체가 생성 될 때 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-210">If you omit this parameter, objects are sent as they're generated.</span></span>

```yaml
Type: Int32
Aliases: ob

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-211">이 리소스 관리 매개 변수는 고급 사용자를 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-211">This resource management parameter is designed for advanced users.</span></span> <span data-ttu-id="40715-212">이 매개 변수를 사용 하는 경우 PowerShell은의 일괄 처리로 데이터를 다음 cmdlet으로 보냅니다 `OutBuffer + 1` .</span><span class="sxs-lookup"><span data-stu-id="40715-212">When you use this parameter, PowerShell sends data to the next cmdlet in batches of `OutBuffer + 1`.</span></span>

<span data-ttu-id="40715-213">다음 예에서는 cmdlet을 사용 하 `ForEach-Object` 는 프로세스 블록 사이에를 표시 합니다 `Write-Host` .</span><span class="sxs-lookup"><span data-stu-id="40715-213">The following example alternates displays between to `ForEach-Object` process blocks that use the `Write-Host` cmdlet.</span></span> <span data-ttu-id="40715-214">표시는 2 또는의 일괄 처리로 대체 `OutBuffer + 1` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-214">The display alternates in batches of 2 or `OutBuffer + 1`.</span></span>

```powershell
1..4 | ForEach-Object {
        Write-Host "$($_): First"; $_
      } -OutBuffer 1 | ForEach-Object {
                        Write-Host "$($_): Second" }
```

```Output
1: First
2: First
1: Second
2: Second
3: First
4: First
3: Second
4: Second
```

#### <a name="outvariable"></a><span data-ttu-id="40715-215">OutVariable</span><span class="sxs-lookup"><span data-stu-id="40715-215">OutVariable</span></span>

<span data-ttu-id="40715-216">파이프라인을 따라 출력을 전송 하는 것 외에도 지정 된 변수에 명령의 출력 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-216">Stores output objects from the command in the specified variable in addition to sending the output along the pipeline.</span></span>

```yaml
Type: String
Aliases: ov

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-217">출력을 변수에 추가 하려면 이미 저장 되어 있을 수 있는 출력을 바꾸지 않고 변수 이름 앞에 더하기 기호 ()를 입력 `+` 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-217">To add the output to the variable, instead of replacing any output that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="40715-218">예를 들어 다음 명령은 변수를 만들고 `$out` 여기에 프로세스 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-218">For example, the following command creates the `$out` variable and stores the process object in it:</span></span>

```powershell
Get-Process PowerShell -OutVariable out
```

<span data-ttu-id="40715-219">다음 명령은 변수에 process 개체를 추가 합니다 `$out` .</span><span class="sxs-lookup"><span data-stu-id="40715-219">The following command adds the process object to the `$out` variable:</span></span>

```powershell
Get-Process iexplore -OutVariable +out
```

<span data-ttu-id="40715-220">다음 명령은 변수의 내용을 표시 합니다 `$out` .</span><span class="sxs-lookup"><span data-stu-id="40715-220">The following command displays the contents of the `$out` variable:</span></span>

```powershell
$out
```

> [!NOTE]
> <span data-ttu-id="40715-221">**OutVariable** 매개 변수에서 만든 변수는 `[System.Collections.ArrayList]` 입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-221">The variable created by the **OutVariable** parameter is a `[System.Collections.ArrayList]`.</span></span>

#### <a name="pipelinevariable"></a><span data-ttu-id="40715-222">PipelineVariable</span><span class="sxs-lookup"><span data-stu-id="40715-222">PipelineVariable</span></span>

<span data-ttu-id="40715-223">**PipelineVariable** 은 파이프라인을 통해 흐르는 모든 명명 된 명령에 대해 현재 파이프라인 요소의 값을 변수로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-223">**PipelineVariable** stores the value of the current pipeline element as a variable, for any named command as it flows through the pipeline.</span></span>

```yaml
Type: String
Aliases: pv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-224">유효한 값은 모든 변수 이름과 동일한 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-224">Valid values are strings, the same as for any variable names.</span></span>

<span data-ttu-id="40715-225">다음은 **PipelineVariable** 의 작동 방식에 대 한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-225">The following is an example of how **PipelineVariable** works.</span></span> <span data-ttu-id="40715-226">이 예에서는 명령에 명령 결과를 저장 하는 **PipelineVariable** 매개 변수가 명령에 추가 됩니다 `Foreach-Object` .</span><span class="sxs-lookup"><span data-stu-id="40715-226">In this example, the **PipelineVariable** parameter is added to a `Foreach-Object` command to store the results of the command in variables.</span></span> <span data-ttu-id="40715-227">숫자 범위 (1 ~ 10)는 첫 번째 명령으로 파이프 되며, `Foreach-Object` 결과는 **Left** 라는 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-227">A range of numbers, 1 to 10, are piped into the first `Foreach-Object` command, the results of which are stored in a variable named **Left**.</span></span>

<span data-ttu-id="40715-228">첫 번째 명령의 결과는 `Foreach-Object` 첫 번째 명령 `Foreach-Object` 에서 반환 된 개체를 필터링 하는 두 번째 명령으로 파이프 됩니다 `Foreach-Object` .</span><span class="sxs-lookup"><span data-stu-id="40715-228">The results of the first `Foreach-Object` command are piped into a second `Foreach-Object` command, which filters the objects returned by the first `Foreach-Object` command.</span></span> <span data-ttu-id="40715-229">두 번째 명령의 결과는 **Right** 라는 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-229">The results of the second command are stored in a variable named **Right**.</span></span>

<span data-ttu-id="40715-230">세 번째 `Foreach-Object` 명령에서 `Foreach-Object` **왼쪽** 및 **오른쪽** 변수로 표시 되는 처음 두 개의 파이프 된 명령의 결과는 곱하기 연산자를 사용 하 여 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-230">In the third `Foreach-Object` command, the results of the first two `Foreach-Object` piped commands, represented by the variables **Left** and **Right**, are processed by using a multiplication operator.</span></span> <span data-ttu-id="40715-231">이 명령은 **왼쪽** 변수와 **오른쪽** 변수에 저장 된 개체에 곱할 수 있도록 지시 하 고 결과를 "왼쪽 범위 멤버 \* 오른쪽 범위 member = product"로 표시 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-231">The command instructs objects stored in the **Left** and **Right** variables to be multiplied, and specifies that the results should be displayed as "Left range member \* Right range member = product".</span></span>

```powershell
1..10 | Foreach-Object -PipelineVariable Left -Process { $_ } |
  Foreach-Object -PV Right -Process { 1..10 } |
  Foreach-Object -Process { "$Left * $Right = " + ($Left*$Right) }
```

```output
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
1 * 4 = 4
1 * 5 = 5
...
```

#### <a name="verbose"></a><span data-ttu-id="40715-232">자세히</span><span class="sxs-lookup"><span data-stu-id="40715-232">Verbose</span></span>

<span data-ttu-id="40715-233">명령에서 수행한 작업에 대 한 자세한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-233">Displays detailed information about the operation done by the command.</span></span> <span data-ttu-id="40715-234">이 정보는 추적 또는 트랜잭션 로그의 정보와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-234">This information resembles the information in a trace or in a transaction log.</span></span> <span data-ttu-id="40715-235">이 매개 변수는 명령이 자세한 정보 메시지를 생성 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-235">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="40715-236">예를 들어이 매개 변수는 명령에 cmdlet이 포함 되어 있을 때 작동 `Write-Verbose` 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-236">For example, this parameter works when a command contains the `Write-Verbose` cmdlet.</span></span>

```yaml
Type: SwitchParameter
Aliases: vb

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-237">**Verbose** 매개 변수는 `$VerbosePreference` 현재 명령에 대 한 변수 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-237">The **Verbose** parameter overrides the value of the `$VerbosePreference` variable for the current command.</span></span> <span data-ttu-id="40715-238">변수의 기본값은 `$VerbosePreference` **SilentlyContinue** 이므로 자세한 정보 표시 메시지는 기본적으로 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-238">Because the default value of the `$VerbosePreference` variable is **SilentlyContinue**, verbose messages aren't displayed by default.</span></span>

<span data-ttu-id="40715-239">`-Verbose:$true` 는와 동일한 효과가 있습니다. `-Verbose`</span><span class="sxs-lookup"><span data-stu-id="40715-239">`-Verbose:$true` has the same effect as `-Verbose`</span></span>

<span data-ttu-id="40715-240">`-Verbose:$false` 자세한 정보 표시 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-240">`-Verbose:$false` suppresses the display of verbose messages.</span></span> <span data-ttu-id="40715-241">의 값이 `$VerbosePreference` **SilentlyContinue** (기본값)가 아닌 경우이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-241">Use this parameter when the value of `$VerbosePreference` isn't **SilentlyContinue** (the default).</span></span>

#### <a name="warningaction"></a><span data-ttu-id="40715-242">WarningAction</span><span class="sxs-lookup"><span data-stu-id="40715-242">WarningAction</span></span>

<span data-ttu-id="40715-243">Cmdlet이 명령의 경고에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-243">Determines how the cmdlet responds to a warning from the command.</span></span> <span data-ttu-id="40715-244">기본값은 **Continue** 입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-244">**Continue** is the default value.</span></span> <span data-ttu-id="40715-245">이 매개 변수는 명령에서 경고 메시지를 생성 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-245">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="40715-246">예를 들어이 매개 변수는 명령에 cmdlet이 포함 되어 있을 때 작동 `Write-Warning` 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-246">For example, this parameter works when a command contains the `Write-Warning` cmdlet.</span></span>

```yaml
Type: ActionPreference
Aliases: wa
Accepted values: Suspend, Ignore, Inquire, Continue, Stop, SilentlyContinue

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-247">**WarningAction** 매개 변수는 `$WarningPreference` 현재 명령에 대 한 변수 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-247">The **WarningAction** parameter overrides the value of the `$WarningPreference` variable for the current command.</span></span> <span data-ttu-id="40715-248">변수의 기본값은 `$WarningPreference` **Continue** 이므로 **WarningAction** 매개 변수를 사용 하지 않으면 경고가 표시 되 고 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-248">Because the default value of the `$WarningPreference` variable is **Continue**, warnings are displayed and execution continues unless you use the **WarningAction** parameter.</span></span>

<span data-ttu-id="40715-249">`-WarningAction:Continue` 경고 메시지를 표시 하 고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-249">`-WarningAction:Continue` displays the warning messages and continues executing the command.</span></span> <span data-ttu-id="40715-250">기본값은 `Continue`입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-250">`Continue` is the default.</span></span>

<span data-ttu-id="40715-251">`-WarningAction:Inquire` 경고 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-251">`-WarningAction:Inquire` displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="40715-252">이 값은 거의 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-252">This value is rarely used.</span></span>

<span data-ttu-id="40715-253">`-WarningAction:SilentlyContinue` 경고 메시지를 표시 하지 않고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-253">`-WarningAction:SilentlyContinue` suppresses the warning message and continues executing the command.</span></span>

<span data-ttu-id="40715-254">`-WarningAction:Stop` 경고 메시지를 표시 하 고 명령 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-254">`-WarningAction:Stop` displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="40715-255">**WarningAction** 매개 변수는를 재정의 하지만 `$WarningAction` 명령이 스크립트나 함수를 실행 하는 명령에 사용 되는 경우 기본 설정 변수의 값을 대체 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-255">The **WarningAction** parameter overrides, but does not replace the value of the `$WarningAction` preference variable when the parameter is used in a command to run a script or function.</span></span>

#### <a name="warningvariable"></a><span data-ttu-id="40715-256">WarningVariable</span><span class="sxs-lookup"><span data-stu-id="40715-256">WarningVariable</span></span>

<span data-ttu-id="40715-257">지정 된 변수에서 명령에 대 한 경고를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-257">Stores warnings about the command in the specified variable.</span></span>

```yaml
Type: String
Aliases: wv

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-258">생성 된 모든 경고는 사용자에 게 경고가 표시 되지 않는 경우에도 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-258">All generated warnings are saved in the variable even if the warnings aren't displayed to the user.</span></span>

<span data-ttu-id="40715-259">변수에 이미 저장 되어 있을 수 있는 경고를 대체 하는 대신 변수 내용에 경고를 추가 하려면 변수 이름 앞에 더하기 기호 ()를 입력 `+` 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-259">To append the warnings to the variable content, instead of replacing any warnings that might already be stored there, type a plus sign (`+`) before the variable name.</span></span>

<span data-ttu-id="40715-260">예를 들어 다음 명령은 변수를 만든 `$a` 다음 경고를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-260">For example, the following command creates the `$a` variable and then stores any warnings in it:</span></span>

```powershell
Get-Process -Id 6 -WarningVariable a
```

<span data-ttu-id="40715-261">다음 명령은 경고를 변수에 추가 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="40715-261">The following command adds any warnings to the `$a` variable:</span></span>

```powershell
Get-Process -Id 2 -WarningVariable +a
```

<span data-ttu-id="40715-262">다음 명령은의 내용을 표시 합니다 `$a` .</span><span class="sxs-lookup"><span data-stu-id="40715-262">The following command displays the contents of `$a`:</span></span>

```powershell
$a
```

<span data-ttu-id="40715-263">이 매개 변수를 사용 하 여 특정 명령의 경고만 포함 하는 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-263">You can use this parameter to create a variable that contains only warnings from specific commands.</span></span> <span data-ttu-id="40715-264">또는와 같은 배열 표기법을 사용 `$a[0]` 하 여 `$warning[1,2]` 변수에 저장 된 특정 경고를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-264">You can use array notation, such as `$a[0]` or `$warning[1,2]` to refer to specific warnings stored in the variable.</span></span>

> [!NOTE]
> <span data-ttu-id="40715-265">경고 변수에는 중첩 된 함수 또는 스크립트에 대 한 호출의 경고를 포함 하 여 명령에 의해 생성 된 모든 경고가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="40715-265">The warning variable contains all warnings generated by the command, including warnings from calls to nested functions or scripts.</span></span>

### <a name="risk-management-parameter-descriptions"></a><span data-ttu-id="40715-266">위험 관리 매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="40715-266">Risk Management Parameter Descriptions</span></span>

#### <a name="whatif"></a><span data-ttu-id="40715-267">WhatIf</span><span class="sxs-lookup"><span data-stu-id="40715-267">WhatIf</span></span>

<span data-ttu-id="40715-268">명령을 실행 하는 대신 명령의 효과를 설명 하는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-268">Displays a message that describes the effect of the command, instead of executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-269">**WhatIf** 매개 변수는 `$WhatIfPreference` 현재 명령에 대 한 변수 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-269">The **WhatIf** parameter overrides the value of the `$WhatIfPreference` variable for the current command.</span></span> <span data-ttu-id="40715-270">변수의 기본값은 `$WhatIfPreference` 0 (사용 안 함) **이므로 Whatif** 동작은 **whatif** 매개 변수 없이 수행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-270">Because the default value of the `$WhatIfPreference` variable is 0 (disabled), **WhatIf** behavior isn't done without the **WhatIf** parameter.</span></span> <span data-ttu-id="40715-271">자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40715-271">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="40715-272">`-WhatIf:$true` 와 동일한 효과가 `-WhatIf` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-272">`-WhatIf:$true` has the same effect as `-WhatIf`.</span></span>

<span data-ttu-id="40715-273">`-WhatIf:$false` 변수의 값이 1 인 경우 발생 하는 자동 WhatIf 동작을 표시 하지 않습니다 `$WhatIfPreference` .</span><span class="sxs-lookup"><span data-stu-id="40715-273">`-WhatIf:$false` suppresses the automatic WhatIf behavior that results when the value of the `$WhatIfPreference` variable is 1.</span></span>

<span data-ttu-id="40715-274">예를 들어 다음 명령은 `-WhatIf` 명령에 매개 변수를 사용 합니다 `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="40715-274">For example, the following command uses the `-WhatIf` parameter in a `Remove-Item` command:</span></span>

```powershell
Remove-Item Date.csv -WhatIf
```

<span data-ttu-id="40715-275">항목을 제거 하는 대신 PowerShell에서 수행 하는 작업과 영향을 받는 항목을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-275">Instead of removing the item, PowerShell lists the operations it would do and the items that would be affected.</span></span> <span data-ttu-id="40715-276">이 명령은 다음과 같은 출력을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-276">This command produces the following output:</span></span>

```output
What if: Performing operation "Remove File" on
Target "C:\ps-test\date.csv".
```

#### <a name="confirm"></a><span data-ttu-id="40715-277">확인</span><span class="sxs-lookup"><span data-stu-id="40715-277">Confirm</span></span>

<span data-ttu-id="40715-278">명령을 실행하기 전 확인 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-278">Prompts you for confirmation before executing the command.</span></span>

```yaml
Type: SwitchParameter
Aliases: cf

Required: False
Position: Named
Default value: Depends on preference variable
Accept pipeline input: False
Accept wildcard characters: False
```

<span data-ttu-id="40715-279">**Confirm** 매개 변수는 `$ConfirmPreference` 현재 명령에 대 한 변수 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-279">The **Confirm** parameter overrides the value of the `$ConfirmPreference` variable for the current command.</span></span> <span data-ttu-id="40715-280">기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-280">The default value is true.</span></span> <span data-ttu-id="40715-281">자세한 내용은 [about_Preference_Variables](about_Preference_Variables.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="40715-281">For more information, see [about_Preference_Variables](about_Preference_Variables.md)</span></span>

<span data-ttu-id="40715-282">`-Confirm:$true` 와 동일한 효과가 `-Confirm` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-282">`-Confirm:$true` has the same effect as `-Confirm`.</span></span>

<span data-ttu-id="40715-283">`-Confirm:$false` 의 값 `$ConfirmPreference` 이 cmdlet의 예상 위험 보다 작거나 같을 때 발생 하는 자동 확인을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-283">`-Confirm:$false` suppresses automatic confirmation, which occurs when the value of `$ConfirmPreference` is less than or equal to the estimated risk of the cmdlet.</span></span>

<span data-ttu-id="40715-284">예를 들어 다음 명령은 명령에 **Confirm** 매개 변수를 사용 합니다 `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="40715-284">For example, the following command uses the **Confirm** parameter with a `Remove-Item` command.</span></span> <span data-ttu-id="40715-285">항목을 제거 하기 전에 PowerShell에서 수행 하는 작업과 영향을 받는 항목을 나열 하 고 승인을 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-285">Before removing the item, PowerShell lists the operations it would do and the items that would be affected, and asks for approval.</span></span>

```
PS C:\ps-test> Remove-Item tmp*.txt -Confirm

Confirm
Are you sure you want to perform this action?
Performing operation "Remove File" on Target " C:\ps-test\tmp1.txt
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend
[?] Help (default is "Y"):
```

<span data-ttu-id="40715-286">확인 응답 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-286">The Confirm response options are as follows:</span></span>

|<span data-ttu-id="40715-287">응답</span><span class="sxs-lookup"><span data-stu-id="40715-287">Response</span></span>       |<span data-ttu-id="40715-288">결과</span><span class="sxs-lookup"><span data-stu-id="40715-288">Result</span></span>                                                     |
|---------------|-----------------------------------------------------------|
|<span data-ttu-id="40715-289">예 (Y)</span><span class="sxs-lookup"><span data-stu-id="40715-289">Yes (Y)</span></span>        |<span data-ttu-id="40715-290">작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-290">Perform the action.</span></span>                                        |
|<span data-ttu-id="40715-291">모두 예 (A)</span><span class="sxs-lookup"><span data-stu-id="40715-291">Yes to All (A)</span></span> |<span data-ttu-id="40715-292">모든 작업을 수행 하 고 후속 확인 쿼리를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-292">Perform all actions and suppress subsequent Confirm queries</span></span>|
|               |<span data-ttu-id="40715-293">이 명령에 대 한입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-293">for this command.</span></span>                                          |
|<span data-ttu-id="40715-294">아니요 (N):</span><span class="sxs-lookup"><span data-stu-id="40715-294">No (N):</span></span>        |<span data-ttu-id="40715-295">작업을 수행 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="40715-295">Do not perform the action.</span></span>                                 |
|<span data-ttu-id="40715-296">모두 아니요 (L):</span><span class="sxs-lookup"><span data-stu-id="40715-296">No to All (L):</span></span> |<span data-ttu-id="40715-297">작업을 수행 하지 않고 후속 확인을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-297">Do not perform any actions and suppress subsequent Confirm</span></span> |
|               |<span data-ttu-id="40715-298">이 명령에 대 한 쿼리입니다.</span><span class="sxs-lookup"><span data-stu-id="40715-298">queries for this command.</span></span>                                  |
|<span data-ttu-id="40715-299">일시 중단:</span><span class="sxs-lookup"><span data-stu-id="40715-299">Suspend (S):</span></span>   |<span data-ttu-id="40715-300">명령을 일시 중지 하 고 임시 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="40715-300">Pause the command and create a temporary session.</span></span>          |
|<span data-ttu-id="40715-301">도움말 (?)</span><span class="sxs-lookup"><span data-stu-id="40715-301">Help (?)</span></span>       |<span data-ttu-id="40715-302">이러한 옵션에 대 한 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-302">Display help for these options.</span></span>                            |

<span data-ttu-id="40715-303">**일시 중단** 옵션은 명령을 보류 중으로 설정 하 고 **확인** 옵션을 선택할 준비가 될 때까지 작업을 수행할 수 있는 임시 중첩 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="40715-303">The **Suspend** option places the command on hold and creates a temporary nested session in which you can work until you're ready to choose a **Confirm** option.</span></span> <span data-ttu-id="40715-304">중첩 된 세션에 대 한 명령 프롬프트에는 원래의 부모 명령의 자식 작업 임을 나타내는 두 개의 추가 캐럿 (>>)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-304">The command prompt for the nested session has two extra carets (>>) to indicate that it's a child operation of the original parent command.</span></span> <span data-ttu-id="40715-305">중첩 된 세션에서 명령 및 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40715-305">You can run commands and scripts in the nested session.</span></span> <span data-ttu-id="40715-306">중첩 된 세션을 종료 하 고 원래 명령의 확인 옵션으로 돌아가려면 "exit"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-306">To end the nested session and return to the Confirm options for the original command, type "exit".</span></span>

<span data-ttu-id="40715-307">다음 예에서는 사용자가 명령 매개 변수에 대 한 도움말을 확인 하는 동안 **일시 중단** 옵션을 사용 하 여 명령을 일시적으로 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-307">In the following example, the **Suspend** option (S) is used to halt a command temporarily while the user checks the help for a command parameter.</span></span> <span data-ttu-id="40715-308">필요한 정보를 구한 후 "끝내기"를 입력 하 여 중첩 된 프롬프트를 종료 한 다음 확인 쿼리에 대 한 예 (y) 응답을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40715-308">After obtaining the needed information, the user types "exit" to end the nested prompt and then selects the Yes (y) response to the Confirm query.</span></span>

```
PS C:\ps-test> New-Item -ItemType File -Name Test.txt -Confirm

Confirm
Are you sure you want to perform this action?

Performing operation "Create File" on Target "Destination:
C:\ps-test\test.txt".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default
is "Y"): s

PS C:\ps-test> Get-Help New-Item -Parameter ItemType

-ItemType <string>
Specifies the provider-specified type of the new item.

Required?                    false
Position?                    named
Default value
Accept pipeline input?       true (ByPropertyName)
Accept wildcard characters?  false

PS C:\ps-test> exit

Confirm
Are you sure you want to perform this action?
Performing operation "Create File" on Target "Destination: C:\ps-test\test
.txt".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (defau
lt is "Y"): y

Directory: C:\ps-test

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         8/27/2010   2:41 PM          0 test.txt
```

## <a name="keywords"></a><span data-ttu-id="40715-309">어</span><span class="sxs-lookup"><span data-stu-id="40715-309">KEYWORDS</span></span>

<span data-ttu-id="40715-310">about_Common_Parameters</span><span class="sxs-lookup"><span data-stu-id="40715-310">about_Common_Parameters</span></span>

## <a name="see-also"></a><span data-ttu-id="40715-311">참고 항목</span><span class="sxs-lookup"><span data-stu-id="40715-311">SEE ALSO</span></span>

[<span data-ttu-id="40715-312">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="40715-312">about_Preference_Variables</span></span>](about_Preference_Variables.md)

[<span data-ttu-id="40715-313">Write-Debug</span><span class="sxs-lookup"><span data-stu-id="40715-313">Write-Debug</span></span>](xref:Microsoft.PowerShell.Utility.Write-Debug)

[<span data-ttu-id="40715-314">Write-Warning</span><span class="sxs-lookup"><span data-stu-id="40715-314">Write-Warning</span></span>](xref:Microsoft.PowerShell.Utility.Write-Warning)

[<span data-ttu-id="40715-315">Write-Error</span><span class="sxs-lookup"><span data-stu-id="40715-315">Write-Error</span></span>](xref:Microsoft.PowerShell.Utility.Write-Error)

[<span data-ttu-id="40715-316">Write-Verbose</span><span class="sxs-lookup"><span data-stu-id="40715-316">Write-Verbose</span></span>](xref:Microsoft.PowerShell.Utility.Write-Verbose)
