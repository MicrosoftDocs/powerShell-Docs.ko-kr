---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 친숙한 명령 이름 사용
ms.openlocfilehash: 30b33bc8739975c1a40e51c04a3ee4e426c199e7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030901"
---
# <a name="using-familiar-command-names"></a><span data-ttu-id="61f51-103">친숙한 명령 이름 사용</span><span class="sxs-lookup"><span data-stu-id="61f51-103">Using familiar command names</span></span>

<span data-ttu-id="61f51-104">PowerShell은 대체 이름으로 명령을 참조하도록 별칭을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-104">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="61f51-105">별칭은 다른 셸을 사용해 본 경험이 있는 사용자가 이미 알고 있는 일반적인 명령 이름을 PowerShell의 유사한 작업에 사용할 수 있도록 해줍니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-105">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="61f51-106">별칭은 새 이름을 다른 명령과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-106">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="61f51-107">예를 들어 PowerShell에는 출력 창을 지우는 `Clear-Host`라는 내부 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-107">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="61f51-108">명령 프롬프트에서 `cls` 또는 `clear` 별칭을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-108">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="61f51-109">PowerShell은 이러한 별칭을 해석하고 `Clear-Host` 함수를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-109">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="61f51-110">이 기능은 사용자가 PowerShell을 익히는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-110">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="61f51-111">첫째, 대부분의 **cmd.exe** 및 Unix 사용자는 이름으로 이미 알고 있는 대규모 명령 모음을 보유하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-111">First, most **cmd.exe** and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="61f51-112">PowerShell의 해당 명령이 동일한 결과를 생성하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-112">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="61f51-113">그러나 결과는 사용자가 PowerShell 명령 이름을 모르는 상태로 사용해도 될만큼 충분히 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-113">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="61f51-114">"단순 반복 암기"는 새 명령 셸을 학습할 때 겪게 되는 또 다른 어려움입니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-114">"Finger memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="61f51-115">수년 동안 **cmd.exe**를 사용해왔다면 화면을 지우기 위해 반사적으로 `cls` 명령을 입력할 수 있을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-115">If you have used **cmd.exe** for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="61f51-116">`Clear-Host`에 대한 별칭이 없으면, 오류 메시지가 수신되고 출력을 지우기 위해 어떻게 해야 할지 알 수 없을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-116">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

<span data-ttu-id="61f51-117">다음은 PowerShell에서 사용할 수 있는 몇 가지 일반적인 **cmd.exe** 및 Unix 명령 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-117">The following list shows a few of the common **cmd.exe** and Unix commands that you can use in PowerShell:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="61f51-118">cat</span><span class="sxs-lookup"><span data-stu-id="61f51-118">cat</span></span>|<span data-ttu-id="61f51-119">dir</span><span class="sxs-lookup"><span data-stu-id="61f51-119">dir</span></span>|<span data-ttu-id="61f51-120">mount</span><span class="sxs-lookup"><span data-stu-id="61f51-120">mount</span></span>|<span data-ttu-id="61f51-121">rm</span><span class="sxs-lookup"><span data-stu-id="61f51-121">rm</span></span>|
|<span data-ttu-id="61f51-122">CD</span><span class="sxs-lookup"><span data-stu-id="61f51-122">cd</span></span>|<span data-ttu-id="61f51-123">echo</span><span class="sxs-lookup"><span data-stu-id="61f51-123">echo</span></span>|<span data-ttu-id="61f51-124">이동</span><span class="sxs-lookup"><span data-stu-id="61f51-124">move</span></span>|<span data-ttu-id="61f51-125">rmdir</span><span class="sxs-lookup"><span data-stu-id="61f51-125">rmdir</span></span>|
|<span data-ttu-id="61f51-126">chdir</span><span class="sxs-lookup"><span data-stu-id="61f51-126">chdir</span></span>|<span data-ttu-id="61f51-127">erase</span><span class="sxs-lookup"><span data-stu-id="61f51-127">erase</span></span>|<span data-ttu-id="61f51-128">popd</span><span class="sxs-lookup"><span data-stu-id="61f51-128">popd</span></span>|<span data-ttu-id="61f51-129">sleep</span><span class="sxs-lookup"><span data-stu-id="61f51-129">sleep</span></span>|
|<span data-ttu-id="61f51-130">지우기</span><span class="sxs-lookup"><span data-stu-id="61f51-130">clear</span></span>|<span data-ttu-id="61f51-131">h</span><span class="sxs-lookup"><span data-stu-id="61f51-131">h</span></span>|<span data-ttu-id="61f51-132">ps</span><span class="sxs-lookup"><span data-stu-id="61f51-132">ps</span></span>|<span data-ttu-id="61f51-133">sort</span><span class="sxs-lookup"><span data-stu-id="61f51-133">sort</span></span>|
|<span data-ttu-id="61f51-134">cls</span><span class="sxs-lookup"><span data-stu-id="61f51-134">cls</span></span>|<span data-ttu-id="61f51-135">history</span><span class="sxs-lookup"><span data-stu-id="61f51-135">history</span></span>|<span data-ttu-id="61f51-136">pushd</span><span class="sxs-lookup"><span data-stu-id="61f51-136">pushd</span></span>|<span data-ttu-id="61f51-137">tee</span><span class="sxs-lookup"><span data-stu-id="61f51-137">tee</span></span>|
|<span data-ttu-id="61f51-138">copy</span><span class="sxs-lookup"><span data-stu-id="61f51-138">copy</span></span>|<span data-ttu-id="61f51-139">kill</span><span class="sxs-lookup"><span data-stu-id="61f51-139">kill</span></span>|<span data-ttu-id="61f51-140">pwd</span><span class="sxs-lookup"><span data-stu-id="61f51-140">pwd</span></span>|<span data-ttu-id="61f51-141">type</span><span class="sxs-lookup"><span data-stu-id="61f51-141">type</span></span>|
|<span data-ttu-id="61f51-142">del</span><span class="sxs-lookup"><span data-stu-id="61f51-142">del</span></span>|<span data-ttu-id="61f51-143">lp</span><span class="sxs-lookup"><span data-stu-id="61f51-143">lp</span></span>|<span data-ttu-id="61f51-144">r</span><span class="sxs-lookup"><span data-stu-id="61f51-144">r</span></span>|<span data-ttu-id="61f51-145">쓰기</span><span class="sxs-lookup"><span data-stu-id="61f51-145">write</span></span>|
|<span data-ttu-id="61f51-146">diff</span><span class="sxs-lookup"><span data-stu-id="61f51-146">diff</span></span>|<span data-ttu-id="61f51-147">ls</span><span class="sxs-lookup"><span data-stu-id="61f51-147">ls</span></span>|<span data-ttu-id="61f51-148">ren</span><span class="sxs-lookup"><span data-stu-id="61f51-148">ren</span></span>||

<span data-ttu-id="61f51-149">`Get-Alias` cmdlet은 별칭과 연결된 네이티브 PowerShell 명령의 실제 이름을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-149">The `Get-Alias` cmdlet shows you the real name of the native PowerShell command associated with an alias.</span></span>

```powershell
PS> Get-Alias cls
```

```Output
CommandType     Name                               Version    Source
-----------     ----                               -------    ------
Alias           cls -> Clear-Host
```

## <a name="interpreting-standard-aliases"></a><span data-ttu-id="61f51-150">표준 별칭 해석</span><span class="sxs-lookup"><span data-stu-id="61f51-150">Interpreting standard aliases</span></span>

<span data-ttu-id="61f51-151">앞서 설명한 별칭은 다른 명령 셸에 대한 이름 호환성을 유지하기 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-151">The aliases we described previously were designed for name-compatibility with other command shells.</span></span>
<span data-ttu-id="61f51-152">PowerShell에 기본 제공된 대부분의 별칭은 간결하게 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-152">Most aliases built into PowerShell are designed for brevity.</span></span> <span data-ttu-id="61f51-153">이름이 짧을수록 입력하기가 더 쉽지만, 어떤 명령을 나타내는지 잘 모르면 이해하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-153">Shorter names are easier to type, but are difficult to read if you don't know what they refer to.</span></span>

<span data-ttu-id="61f51-154">PowerShell 별칭은 명확성과 간결성 간에 균형을 유지하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-154">PowerShell aliases try to compromise between clarity and brevity.</span></span> <span data-ttu-id="61f51-155">PowerShell은 일반 noun가 verb에 대한 표준 별칭 집합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-155">PowerShell uses a standard set of aliases for common nouns and verbs.</span></span>

<span data-ttu-id="61f51-156">예제 약어:</span><span class="sxs-lookup"><span data-stu-id="61f51-156">Example abbreviations:</span></span>

| <span data-ttu-id="61f51-157">Noun 또는 Verb</span><span class="sxs-lookup"><span data-stu-id="61f51-157">Noun or Verb</span></span> | <span data-ttu-id="61f51-158">약어</span><span class="sxs-lookup"><span data-stu-id="61f51-158">Abbreviation</span></span> |
|--------------|--------------|
| <span data-ttu-id="61f51-159">가져오기</span><span class="sxs-lookup"><span data-stu-id="61f51-159">Get</span></span>          | <span data-ttu-id="61f51-160">g</span><span class="sxs-lookup"><span data-stu-id="61f51-160">g</span></span>            |
| <span data-ttu-id="61f51-161">설정</span><span class="sxs-lookup"><span data-stu-id="61f51-161">Set</span></span>          | <span data-ttu-id="61f51-162">s</span><span class="sxs-lookup"><span data-stu-id="61f51-162">s</span></span>            |
| <span data-ttu-id="61f51-163">항목</span><span class="sxs-lookup"><span data-stu-id="61f51-163">Item</span></span>         | <span data-ttu-id="61f51-164">i</span><span class="sxs-lookup"><span data-stu-id="61f51-164">i</span></span>            |
| <span data-ttu-id="61f51-165">위치</span><span class="sxs-lookup"><span data-stu-id="61f51-165">Location</span></span>     | <span data-ttu-id="61f51-166">l</span><span class="sxs-lookup"><span data-stu-id="61f51-166">l</span></span>            |
| <span data-ttu-id="61f51-167">명령</span><span class="sxs-lookup"><span data-stu-id="61f51-167">Command</span></span>      | <span data-ttu-id="61f51-168">cm</span><span class="sxs-lookup"><span data-stu-id="61f51-168">cm</span></span>           |
| <span data-ttu-id="61f51-169">Alias</span><span class="sxs-lookup"><span data-stu-id="61f51-169">Alias</span></span>        | <span data-ttu-id="61f51-170">al</span><span class="sxs-lookup"><span data-stu-id="61f51-170">al</span></span>           |

<span data-ttu-id="61f51-171">이러한 별칭은 축약 이름을 아는 경우 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-171">These aliases are understandable when you know the shorthand names.</span></span>

| <span data-ttu-id="61f51-172">Cmdlet 이름</span><span class="sxs-lookup"><span data-stu-id="61f51-172">Cmdlet name</span></span>    | <span data-ttu-id="61f51-173">Alias</span><span class="sxs-lookup"><span data-stu-id="61f51-173">Alias</span></span> |
|----------------|-------|
| `Get-Item`     | <span data-ttu-id="61f51-174">gi</span><span class="sxs-lookup"><span data-stu-id="61f51-174">gi</span></span>    |
| `Set-Item`     | <span data-ttu-id="61f51-175">si</span><span class="sxs-lookup"><span data-stu-id="61f51-175">si</span></span>    |
| `Get-Location` | <span data-ttu-id="61f51-176">gl</span><span class="sxs-lookup"><span data-stu-id="61f51-176">gl</span></span>    |
| `Set-Location` | <span data-ttu-id="61f51-177">sl</span><span class="sxs-lookup"><span data-stu-id="61f51-177">sl</span></span>    |
| `Get-Command`  | <span data-ttu-id="61f51-178">gcm</span><span class="sxs-lookup"><span data-stu-id="61f51-178">gcm</span></span>   |
| `Get-Alias`    | <span data-ttu-id="61f51-179">gal</span><span class="sxs-lookup"><span data-stu-id="61f51-179">gal</span></span>   |

<span data-ttu-id="61f51-180">PowerShell 별칭에 익숙한 경우 **sal** 별칭이 `Set-Alias`를 나타낼 것으로 쉽게 추측할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-180">Once you're familiar with PowerShell aliasing, it's easy to guess that the **sal** alias refers to `Set-Alias`.</span></span>

## <a name="creating-new-aliases"></a><span data-ttu-id="61f51-181">새 별칭 만들기</span><span class="sxs-lookup"><span data-stu-id="61f51-181">Creating new aliases</span></span>

<span data-ttu-id="61f51-182">`Set-Alias` cmdlet을 사용하여 사용자 고유의 별칭을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-182">You can create your own aliases using the `Set-Alias` cmdlet.</span></span> <span data-ttu-id="61f51-183">예를 들어 다음 문은 앞서 설명한 표준 cmdlet 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-183">For example, the following statements create the standard cmdlet aliases previously discussed:</span></span>

```powershell
Set-Alias -Name gi -Value Get-Item
Set-Alias -Name si -Value Set-Item
Set-Alias -Name gl -Value Get-Location
Set-Alias -Name sl -Value Set-Location
Set-Alias -Name gcm -Value Get-Command
```

<span data-ttu-id="61f51-184">내부적으로 PowerShell은 시작할 때 비슷한 명령을 사용하지만 이러한 별칭은 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-184">Internally, PowerShell uses similar commands during startup, but these aliases are not changeable.</span></span>
<span data-ttu-id="61f51-185">이러한 명령 중 하나를 실행하려고 하면 별칭을 수정할 수 없다는 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-185">If you try to execute one of these commands, you get an error explaining that the alias can't be modified.</span></span> <span data-ttu-id="61f51-186">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="61f51-186">For example:</span></span>

```
PS> Set-Alias -Name gi -Value Get-Item
Set-Alias : Alias is not writeable because alias gi is read-only or constant and cannot be written to.
At line:1 char:10
+ Set-Alias  <<<< -Name gi -Value Get-Item
```
