---
description: PowerShell의 범위에 대 한 개념을 설명 하 고 요소의 범위를 설정 하 고 변경 하는 방법을 보여 줍니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_scopes?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_scopes
ms.openlocfilehash: 6dc416632a6948c60c8016df6066694ce01a8b5d
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354969"
---
# <a name="about-scopes"></a><span data-ttu-id="f637f-104">범위 정보</span><span class="sxs-lookup"><span data-stu-id="f637f-104">About Scopes</span></span>

## <a name="short-description"></a><span data-ttu-id="f637f-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="f637f-105">Short description</span></span>
<span data-ttu-id="f637f-106">PowerShell의 범위에 대 한 개념을 설명 하 고 요소의 범위를 설정 하 고 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-106">Explains the concept of scope in PowerShell and shows how to set and change the scope of elements.</span></span>

## <a name="long-description"></a><span data-ttu-id="f637f-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-107">Long description</span></span>

<span data-ttu-id="f637f-108">PowerShell은 읽고 변경할 수 있는 위치를 제한 하 여 변수, 별칭, 함수 및 PowerShell 드라이브 (PSDrives)에 대 한 액세스를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-108">PowerShell protects access to variables, aliases, functions, and PowerShell drives (PSDrives) by limiting where they can be read and changed.</span></span> <span data-ttu-id="f637f-109">PowerShell에서는 범위 규칙을 사용 하 여 변경 되지 않아야 하는 항목을 실수로 변경 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-109">PowerShell uses scope rules to ensure that you do not inadvertently change an item that should not be changed.</span></span>

<span data-ttu-id="f637f-110">다음은 범위의 기본 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-110">The following are the basic rules of scope:</span></span>

- <span data-ttu-id="f637f-111">범위는 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-111">Scopes may nest.</span></span> <span data-ttu-id="f637f-112">외부 범위를 부모 범위 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-112">An outer scope is referred to as a parent scope.</span></span> <span data-ttu-id="f637f-113">중첩 된 범위는 해당 부모의 자식 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-113">Any nested scopes are child scopes of that parent.</span></span>

- <span data-ttu-id="f637f-114">항목을 명시적으로 전용으로 설정 하지 않는 한 항목은 생성 된 범위와 모든 자식 범위에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-114">An item is visible in the scope in which it was created and in any child scopes, unless you explicitly make it private.</span></span> <span data-ttu-id="f637f-115">변수, 별칭, 함수 또는 PowerShell 드라이브를 하나 이상의 범위에 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-115">You can place variables, aliases, functions, or PowerShell drives in one or more scopes.</span></span>

- <span data-ttu-id="f637f-116">범위 내에서 만든 항목은 다른 범위를 명시적으로 지정 하지 않는 한 해당 항목을 만든 범위 에서만 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-116">An item that you created within a scope can be changed only in the scope in which it was created, unless you explicitly specify a different scope.</span></span>

<span data-ttu-id="f637f-117">범위에 항목을 만들고 항목의 이름을 다른 범위의 항목과 공유 하는 경우 원래 항목이 새 항목에서 숨겨질 수 있지만 재정의 되거나 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-117">If you create an item in a scope, and the item shares its name with an item in a different scope, the original item might be hidden under the new item, but it is not overridden or changed.</span></span>

## <a name="powershell-scopes"></a><span data-ttu-id="f637f-118">PowerShell 범위</span><span class="sxs-lookup"><span data-stu-id="f637f-118">PowerShell Scopes</span></span>

<span data-ttu-id="f637f-119">PowerShell은 다음과 같은 범위를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-119">PowerShell supports the following scopes:</span></span>

- <span data-ttu-id="f637f-120">Global: PowerShell이 시작 되거나 새 세션 또는 runspace를 만들 때 적용 되는 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-120">Global: The scope that is in effect when PowerShell starts or when you create a new session or runspace.</span></span> <span data-ttu-id="f637f-121">PowerShell이 시작 될 때 제공 되는 변수 및 함수는 자동 변수 및 기본 설정 변수와 같은 전역 범위에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-121">Variables and functions that are present when PowerShell starts have been created in the global scope, such as automatic variables and preference variables.</span></span> <span data-ttu-id="f637f-122">PowerShell 프로필의 변수, 별칭 및 함수도 전역 범위에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-122">The variables, aliases, and functions in your PowerShell profiles are also created in the global scope.</span></span> <span data-ttu-id="f637f-123">전역 범위는 세션의 루트 부모 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-123">The global scope is the root parent scope in a session.</span></span>

- <span data-ttu-id="f637f-124">Local: 현재 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-124">Local: The current scope.</span></span> <span data-ttu-id="f637f-125">로컬 범위는 전역 범위 또는 다른 범위 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-125">The local scope can be the global scope or any other scope.</span></span>

- <span data-ttu-id="f637f-126">스크립트: 스크립트 파일을 실행 하는 동안 생성 되는 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-126">Script: The scope that is created while a script file runs.</span></span> <span data-ttu-id="f637f-127">스크립트의 명령만 스크립트 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-127">Only the commands in the script run in the script scope.</span></span> <span data-ttu-id="f637f-128">스크립트의 명령에 대 한 스크립트 범위는 로컬 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-128">To the commands in a script, the script scope is the local scope.</span></span>

> [!NOTE]
> <span data-ttu-id="f637f-129">**Private** 이 범위가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-129">**Private** is not a scope.</span></span> <span data-ttu-id="f637f-130">항목이 정의 된 범위를 벗어나는 항목의 표시 유형을 변경 하는 [옵션](#private-option) 입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-130">It is an [option](#private-option) that changes the visibility of an item outside of the scope where the item is defined.</span></span>

## <a name="parent-and-child-scopes"></a><span data-ttu-id="f637f-131">부모 및 자식 범위</span><span class="sxs-lookup"><span data-stu-id="f637f-131">Parent and Child Scopes</span></span>

<span data-ttu-id="f637f-132">스크립트나 함수를 호출 하 여 새 자식 범위를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-132">You can create a new child scope by calling a script or function.</span></span> <span data-ttu-id="f637f-133">호출 범위는 부모 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-133">The calling scope is the parent scope.</span></span> <span data-ttu-id="f637f-134">호출 된 스크립트나 함수는 자식 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-134">The called script or function is the child scope.</span></span>
<span data-ttu-id="f637f-135">호출 하는 함수 또는 스크립트는 다른 함수를 호출 하 여 루트 범위가 전역 범위인 자식 범위의 계층 구조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-135">The functions or scripts you call may call other functions, creating a hierarchy of child scopes whose root scope is the global scope.</span></span>

<span data-ttu-id="f637f-136">항목을 비공개로 명시적으로 설정 하지 않으면 부모 범위의 항목을 자식 범위에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-136">Unless you explicitly make the items private, the items in the parent scope are available to the child scope.</span></span> <span data-ttu-id="f637f-137">그러나 항목을 만들 때 범위를 명시적으로 지정 하지 않는 한 자식 범위에서 만들고 변경 하는 항목은 부모 범위에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-137">However, items that you create and change in the child scope do not affect the parent scope, unless you explicitly specify the scope when you create the items.</span></span>

> [!NOTE]
> <span data-ttu-id="f637f-138">모듈의 함수는 호출 범위의 자식 범위에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-138">Functions from a module do not run in a child scope of the calling scope.</span></span>
> <span data-ttu-id="f637f-139">모듈에는 전역 범위에 연결 되는 자체 세션 상태가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-139">Modules have their own session state that is linked to the global scope.</span></span>
> <span data-ttu-id="f637f-140">모든 모듈 코드는 자체 루트 범위가 있는 모듈별 범위 계층에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-140">All module code runs in a module-specific hierarchy of scopes that has its own root scope.</span></span>

## <a name="inheritance"></a><span data-ttu-id="f637f-141">상속</span><span class="sxs-lookup"><span data-stu-id="f637f-141">Inheritance</span></span>

<span data-ttu-id="f637f-142">자식 범위는 부모 범위에서 변수, 별칭 및 함수를 상속 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-142">A child scope does not inherit the variables, aliases, and functions from the parent scope.</span></span> <span data-ttu-id="f637f-143">항목이 개인 항목이 아닌 경우 자식 범위에서 부모 범위의 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-143">Unless an item is private, the child scope can view the items in the parent scope.</span></span> <span data-ttu-id="f637f-144">부모 범위를 명시적으로 지정 하 여 항목을 변경할 수 있지만 항목은 자식 범위의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-144">And, it can change the items by explicitly specifying the parent scope, but the items are not part of the child scope.</span></span>

<span data-ttu-id="f637f-145">그러나 항목 집합을 사용 하 여 자식 범위를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-145">However, a child scope is created with a set of items.</span></span> <span data-ttu-id="f637f-146">일반적으로 **AllScope** 옵션을 포함 하는 모든 별칭을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-146">Typically, it includes all the aliases that have the **AllScope** option.</span></span> <span data-ttu-id="f637f-147">이 옵션은이 문서의 뒷부분에서 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-147">This option is discussed later in this article.</span></span> <span data-ttu-id="f637f-148">**AllScope** 옵션을 포함 하는 모든 변수와 일부 자동 변수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-148">It includes all the variables that have the **AllScope** option, plus some automatic variables.</span></span>

<span data-ttu-id="f637f-149">특정 범위의 항목을 찾으려면 또는의 범위 매개 변수를 사용 `Get-Variable` `Get-Alias` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-149">To find the items in a particular scope, use the Scope parameter of `Get-Variable` or `Get-Alias`.</span></span>

<span data-ttu-id="f637f-150">예를 들어 로컬 범위의 모든 변수를 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-150">For example, to get all the variables in the local scope, type:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="f637f-151">전역 범위의 모든 변수를 가져오려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-151">To get all the variables in the global scope, type:</span></span>

```powershell
Get-Variable -Scope global
```

## <a name="scope-modifiers"></a><span data-ttu-id="f637f-152">범위 한정자</span><span class="sxs-lookup"><span data-stu-id="f637f-152">Scope Modifiers</span></span>

<span data-ttu-id="f637f-153">변수, 별칭 또는 함수 이름에는 다음과 같은 선택적 범위 한정자 중 하나가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-153">A variable, alias, or function name can include any one of the following optional scope modifiers:</span></span>

- <span data-ttu-id="f637f-154">`global:` -이름이 **전역** 범위에 존재 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-154">`global:` - Specifies that the name exists in the **Global** scope.</span></span>
- <span data-ttu-id="f637f-155">`local:` -이름이 **로컬** 범위에 있는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-155">`local:` - Specifies that the name exists in the **Local** scope.</span></span> <span data-ttu-id="f637f-156">현재 범위는 항상 **로컬** 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-156">The current scope is always the **Local** scope.</span></span>
- <span data-ttu-id="f637f-157">`private:` -이름이 **Private** 이며 현재 범위에만 표시 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-157">`private:` - Specifies that the name is **Private** and only visible to the current scope.</span></span>
- <span data-ttu-id="f637f-158">`script:` -이름이 **스크립트** 범위에 존재 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-158">`script:` - Specifies that the name exists in the **Script** scope.</span></span>
  <span data-ttu-id="f637f-159">**스크립트** 범위는 가장 가까운 상위 스크립트 파일의 범위 이거나 가장 가까운 상위 스크립트 파일이 없는 경우 **전역** 입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-159">**Script** scope is the nearest ancestor script file's scope or **Global** if there is no nearest ancestor script file.</span></span>
- <span data-ttu-id="f637f-160">`using:` -및와 같은 cmdlet을 통해 스크립트를 실행 하는 동안 다른 범위에 정의 된 변수에 액세스 하는 데 사용 `Start-Job` `Invoke-Command` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-160">`using:` - Used to access variables defined in another scope while running scripts via cmdlets like `Start-Job` and `Invoke-Command`.</span></span>
- <span data-ttu-id="f637f-161">`workflow:` -이름이 워크플로 내에 존재 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-161">`workflow:` - Specifies that the name exists within a workflow.</span></span> <span data-ttu-id="f637f-162">참고: 워크플로는 PowerShell Core에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-162">Note: Workflows are not supported in PowerShell Core.</span></span>
- <span data-ttu-id="f637f-163">`<variable-namespace>` -PowerShell PSDrive 공급자가 만든 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-163">`<variable-namespace>` - A modifier created by a PowerShell PSDrive provider.</span></span>
  <span data-ttu-id="f637f-164">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-164">For example:</span></span>

  |  <span data-ttu-id="f637f-165">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="f637f-165">Namespace</span></span>  |                    <span data-ttu-id="f637f-166">Description</span><span class="sxs-lookup"><span data-stu-id="f637f-166">Description</span></span>                     |
  | ----------- | -------------------------------------------------- |
  | `Alias:`    | <span data-ttu-id="f637f-167">현재 범위에 정의 된 별칭</span><span class="sxs-lookup"><span data-stu-id="f637f-167">Aliases defined in the current scope</span></span>               |
  | `Env:`      | <span data-ttu-id="f637f-168">현재 범위에 정의 된 환경 변수</span><span class="sxs-lookup"><span data-stu-id="f637f-168">Environment variables defined in the current scope</span></span> |
  | `Function:` | <span data-ttu-id="f637f-169">현재 범위에 정의 된 함수</span><span class="sxs-lookup"><span data-stu-id="f637f-169">Functions defined in the current scope</span></span>             |
  | `Variable:` | <span data-ttu-id="f637f-170">현재 범위에 정의 된 변수</span><span class="sxs-lookup"><span data-stu-id="f637f-170">Variables defined in the current scope</span></span>             |

<span data-ttu-id="f637f-171">스크립트의 기본 범위는 스크립트 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-171">The default scope for scripts is the script scope.</span></span> <span data-ttu-id="f637f-172">함수 및 별칭의 기본 범위는 스크립트에서 정의 된 경우에도 로컬 범위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-172">The default scope for functions and aliases is the local scope, even if they are defined in a script.</span></span>

### <a name="using-scope-modifiers"></a><span data-ttu-id="f637f-173">범위 한정자 사용</span><span class="sxs-lookup"><span data-stu-id="f637f-173">Using scope modifiers</span></span>

<span data-ttu-id="f637f-174">새 변수, 별칭 또는 함수의 범위를 지정 하려면 범위 한정자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-174">To specify the scope of a new variable, alias, or function, use a scope modifier.</span></span>

<span data-ttu-id="f637f-175">변수의 범위 한정자에 대 한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-175">The syntax for a scope modifier in a variable is:</span></span>

```
$[<scope-modifier>:]<name> = <value>
```

<span data-ttu-id="f637f-176">함수의 범위 한정자에 대 한 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-176">The syntax for a scope modifier in a function is:</span></span>

```
function [<scope-modifier>:]<name> {<function-body>}
```

<span data-ttu-id="f637f-177">범위 한정자를 사용 하지 않는 다음 명령은 현재 또는 **지역** 범위에서 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-177">The following command, which does not use a scope modifier, creates a variable in the current or **local** scope:</span></span>

```powershell
$a = "one"
```

<span data-ttu-id="f637f-178">**전역** 범위에서 동일한 변수를 만들려면 범위 한정자를 사용 합니다 `global:` .</span><span class="sxs-lookup"><span data-stu-id="f637f-178">To create the same variable in the **global** scope, use the scope `global:` modifier:</span></span>

```powershell
$global:a = "one"
```

<span data-ttu-id="f637f-179">**스크립트** 범위에서 동일한 변수를 만들려면 범위 한정자를 사용 합니다 `script:` .</span><span class="sxs-lookup"><span data-stu-id="f637f-179">To create the same variable in the **script** scope, use the `script:` scope modifier:</span></span>

```powershell
$script:a = "one"
```

<span data-ttu-id="f637f-180">범위 한정자를 함수와 함께 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-180">You can also use a scope modifier with functions.</span></span> <span data-ttu-id="f637f-181">다음 함수 정의는 **전역** 범위에서 함수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-181">The following function definition creates a function in the **global** scope:</span></span>

```powershell
function global:Hello {
  Write-Host "Hello, World"
}
```

<span data-ttu-id="f637f-182">범위 한정자를 사용 하 여 다른 범위의 변수를 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-182">You can also use scope modifiers to refer to a variable in a different scope.</span></span>
<span data-ttu-id="f637f-183">다음 명령은 `$test` 먼저 로컬 범위에서 변수를 참조 한 다음 전역 범위에서 변수를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-183">The following command refers to the `$test` variable, first in the local scope and then in the global scope:</span></span>

```powershell
$test
$global:test
```

### <a name="the-using-scope-modifier"></a><span data-ttu-id="f637f-184">`Using:`범위 한정자</span><span class="sxs-lookup"><span data-stu-id="f637f-184">The `Using:` scope modifier</span></span>

<span data-ttu-id="f637f-185">Using은 원격 명령의 지역 변수를 식별 하는 특수 범위 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-185">Using is a special scope modifier that identifies a local variable in a remote command.</span></span> <span data-ttu-id="f637f-186">한정자가 없으면 PowerShell은 원격 세션에서 원격 명령의 변수를 정의할 것으로 예상 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-186">Without a modifier, PowerShell expects variables in remote commands to be defined in the remote session.</span></span>

<span data-ttu-id="f637f-187">`Using`범위 한정자는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-187">The `Using` scope modifier is introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="f637f-188">세션에서 실행 되지 않는 스크립트나 명령의 경우 범위 한정자를 사용 하 여 `Using` 호출 세션 범위의 변수 값을 포함 해야 합니다. 이렇게 하면 세션 외부 코드에서 해당 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-188">For any script or command that executes out of session, you need the `Using` scope modifier to embed variable values from the calling session scope, so that out of session code can access them.</span></span> <span data-ttu-id="f637f-189">`Using`범위 한정자는 다음 컨텍스트에서 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-189">The `Using` scope modifier is supported in the following contexts:</span></span>

- <span data-ttu-id="f637f-190">원격으로 실행 되는 명령, `Invoke-Command` **ComputerName** , **HostName** , **SSHConnection** 또는 **Session** 매개 변수를 사용 하 여 시작 (원격 세션)</span><span class="sxs-lookup"><span data-stu-id="f637f-190">Remotely executed commands, started with `Invoke-Command` using the **ComputerName** , **HostName** , **SSHConnection** or **Session** parameters (remote session)</span></span>
- <span data-ttu-id="f637f-191">백그라운드 작업, 시작 `Start-Job` (out-of-process 세션)</span><span class="sxs-lookup"><span data-stu-id="f637f-191">Background jobs, started with `Start-Job` (out-of-process session)</span></span>
- <span data-ttu-id="f637f-192">스레드 작업, `Start-ThreadJob` 또는 `ForEach-Object -Parallel` (개별 스레드 세션)를 통해 시작</span><span class="sxs-lookup"><span data-stu-id="f637f-192">Thread jobs, started via `Start-ThreadJob` or `ForEach-Object -Parallel` (separate thread session)</span></span>

<span data-ttu-id="f637f-193">컨텍스트에 따라 포함 된 변수 값은 호출자의 범위에 있는 데이터의 독립적인 복사본 이거나이에 대 한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-193">Depending on the context, embedded variable values are either independent copies of the data in the caller's scope or references to it.</span></span> <span data-ttu-id="f637f-194">원격 및 out-of-process 세션에서 항상 독립적인 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-194">In remote and out-of-process sessions, they are always independent copies.</span></span>

<span data-ttu-id="f637f-195">자세한 내용은 [about_Remote_Variables](about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f637f-195">For more information, see [about_Remote_Variables](about_Remote_Variables.md).</span></span>

<span data-ttu-id="f637f-196">스레드 세션에서는 참조로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-196">In thread sessions, they are passed by reference.</span></span> <span data-ttu-id="f637f-197">즉, 다른 스레드에서 호출 범위 변수를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-197">This means it is possible to modify call scope variables in a different thread.</span></span> <span data-ttu-id="f637f-198">변수를 안전 하 게 수정 하려면 스레드를 동기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-198">To safely modify variables requires thread synchronization.</span></span>

<span data-ttu-id="f637f-199">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f637f-199">For more information see:</span></span>

- [<span data-ttu-id="f637f-200">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="f637f-200">Start-ThreadJob</span></span>](xref:ThreadJob.Start-ThreadJob)
- [<span data-ttu-id="f637f-201">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="f637f-201">ForEach-Object</span></span>](xref:Microsoft.PowerShell.Core.ForEach-Object)

#### <a name="serialization-of-variable-values"></a><span data-ttu-id="f637f-202">변수 값의 Serialization</span><span class="sxs-lookup"><span data-stu-id="f637f-202">Serialization of variable values</span></span>

<span data-ttu-id="f637f-203">원격으로 실행 되는 명령 및 백그라운드 작업은 out-of-process로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-203">Remotely executed commands and background jobs run out-of-process.</span></span>
<span data-ttu-id="f637f-204">Out-of-process 세션은 XML 기반 serialization 및 deserialization을 사용 하 여 프로세스 경계를 넘어 변수 값을 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-204">Out-of-process sessions use XML-based serialization and deserialization to make the values of variables available across the process boundaries.</span></span> <span data-ttu-id="f637f-205">Serialization 프로세스는 개체를 원래 개체 속성이 있지만 메서드는 포함 하지 않는 **PSObject** 로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-205">The serialization process converts objects to a **PSObject** that contains the original objects properties but not its methods.</span></span>

<span data-ttu-id="f637f-206">제한 된 형식 집합의 경우 deserialization 리하이드레이션 할 개체를 원래 형식으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-206">For a limited set of types, deserialization rehydrates objects back to the original type.</span></span> <span data-ttu-id="f637f-207">원래 개체 인스턴스의 복사본입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-207">The rehydrated object is a copy of the original object instance.</span></span>
<span data-ttu-id="f637f-208">형식 속성 및 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-208">It has the type properties and methods.</span></span> <span data-ttu-id="f637f-209">**System.object** 와 같은 단순 형식의 경우 복사본은 정확 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-209">For simple types, such as **System.Version** , the copy is exact.</span></span> <span data-ttu-id="f637f-210">복합 형식의 경우 복사본은 아직까지 완벽입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-210">For complex types, the copy is imperfect.</span></span> <span data-ttu-id="f637f-211">예를 들어, 공개 된 인증서 개체에는 개인 키가 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-211">For example, rehydrated certificate objects do not include the private key.</span></span>

<span data-ttu-id="f637f-212">다른 모든 형식의 인스턴스는 **PSObject** 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-212">Instances of all other types are **PSObject** instances.</span></span> <span data-ttu-id="f637f-213">**PSTypeNames** 속성에는 **deserialize** (예:Deserialized.System) 접두사가 붙은 원래 형식 이름이 포함 **됩니다. 데이터 DataTable**</span><span class="sxs-lookup"><span data-stu-id="f637f-213">The **PSTypeNames** property contains the original type name prefixed with **Deserialized** , for example, **Deserialized.System.Data.DataTable**</span></span>

### <a name="the-allscope-option"></a><span data-ttu-id="f637f-214">AllScope 옵션</span><span class="sxs-lookup"><span data-stu-id="f637f-214">The AllScope Option</span></span>

<span data-ttu-id="f637f-215">변수와 별칭에는 **AllScope** 값을 사용할 수 있는 **Option** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-215">Variables and aliases have an **Option** property that can take a value of **AllScope**.</span></span> <span data-ttu-id="f637f-216">**AllScope** 속성을 포함 하는 항목은 부모 범위에서 상속 소급 되지 않지만 사용자가 만드는 모든 자식 범위의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-216">Items that have the **AllScope** property become part of any child scopes that you create, although they are not retroactively inherited by parent scopes.</span></span>

<span data-ttu-id="f637f-217">**AllScope** 속성이 있는 항목은 자식 범위에 표시 되 고 해당 범위의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-217">An item that has the **AllScope** property is visible in the child scope, and it is part of that scope.</span></span> <span data-ttu-id="f637f-218">모든 범위에서 항목을 변경 하면 변수가 정의 된 모든 범위에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-218">Changes to the item in any scope affect all the scopes in which the variable is defined.</span></span>

### <a name="managing-scope"></a><span data-ttu-id="f637f-219">범위 관리</span><span class="sxs-lookup"><span data-stu-id="f637f-219">Managing Scope</span></span>

<span data-ttu-id="f637f-220">여러 cmdlet에는 특정 범위의 항목을 가져오거나 설정 (생성 및 변경) 할 수 있도록 하는 **범위** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-220">Several cmdlets have a **Scope** parameter that lets you get or set (create and change) items in a particular scope.</span></span> <span data-ttu-id="f637f-221">다음 명령을 사용 하 여 **범위** 매개 변수가 있는 세션의 모든 cmdlet을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-221">Use the following command to find all the cmdlets in your session that have a **Scope** parameter:</span></span>

```powershell
Get-Help * -Parameter scope
```

<span data-ttu-id="f637f-222">특정 범위에 표시 되는 변수를 찾으려면 `Scope` 의 매개 변수를 사용 `Get-Variable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-222">To find the variables that are visible in a particular scope, use the `Scope` parameter of `Get-Variable`.</span></span> <span data-ttu-id="f637f-223">표시 되는 변수에는 전역 변수, 부모 범위의 변수 및 현재 범위의 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-223">The visible variables include global variables, variables in the parent scope, and variables in the current scope.</span></span>

<span data-ttu-id="f637f-224">예를 들어 다음 명령은 로컬 범위에 표시 되는 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-224">For example, the following command gets the variables that are visible in the local scope:</span></span>

```powershell
Get-Variable -Scope local
```

<span data-ttu-id="f637f-225">특정 범위에서 변수를 만들려면의 범위 한정자 나 **범위** 매개 변수를 사용 `Set-Variable` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-225">To create a variable in a particular scope, use a scope modifier or the **Scope** parameter of `Set-Variable`.</span></span> <span data-ttu-id="f637f-226">다음 명령은 전역 범위에서 변수를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-226">The following command creates a variable in the global scope:</span></span>

```powershell
New-Variable -Scope global -Name a -Value "One"
```

<span data-ttu-id="f637f-227">, 또는 cmdlet의 범위 매개 변수를 사용 `New-Alias` 하 여 범위를 지정할 수도 있습니다 `Set-Alias` `Get-Alias` .</span><span class="sxs-lookup"><span data-stu-id="f637f-227">You can also use the Scope parameter of the `New-Alias`, `Set-Alias`, or `Get-Alias` cmdlets to specify the scope.</span></span> <span data-ttu-id="f637f-228">다음 명령은 전역 범위에서 별칭을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-228">The following command creates an alias in the global scope:</span></span>

```powershell
New-Alias -Scope global -Name np -Value Notepad.exe
```

<span data-ttu-id="f637f-229">특정 범위의 함수를 가져오려면 `Get-Item` 범위 내에 있는 경우 cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-229">To get the functions in a particular scope, use the `Get-Item` cmdlet when you are in the scope.</span></span> <span data-ttu-id="f637f-230">`Get-Item`Cmdlet에 **범위** 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-230">The `Get-Item` cmdlet does not have a **Scope** parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="f637f-231">**Scope** 매개 변수를 사용 하는 cmdlet의 경우 숫자를 기준으로 범위를 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-231">For the cmdlets that use the **Scope** parameter, you can also refer to scopes by number.</span></span> <span data-ttu-id="f637f-232">이 숫자는 한 범위의 상대 위치를 다른 범위에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-232">The number describes the relative position of one scope to another.</span></span> <span data-ttu-id="f637f-233">범위 0은 현재 또는 지역 범위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-233">Scope 0 represents the current, or local, scope.</span></span> <span data-ttu-id="f637f-234">범위 1은 직계 부모 범위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-234">Scope 1 indicates the immediate parent scope.</span></span> <span data-ttu-id="f637f-235">범위 2는 부모 범위의 부모를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-235">Scope 2 indicates the parent of the parent scope, and so on.</span></span> <span data-ttu-id="f637f-236">번호가 매겨진 범위는 많은 재귀 범위를 만든 경우 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-236">Numbered scopes are useful if you have created many recursive scopes.</span></span>

### <a name="using-dot-source-notation-with-scope"></a><span data-ttu-id="f637f-237">범위에 점 소스 표기법 사용</span><span class="sxs-lookup"><span data-stu-id="f637f-237">Using Dot Source Notation with Scope</span></span>

<span data-ttu-id="f637f-238">스크립트 및 함수는 모든 범위의 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-238">Scripts and functions follow all the rules of scope.</span></span> <span data-ttu-id="f637f-239">이를 특정 범위에서 만들면 cmdlet 매개 변수나 범위 한정자를 사용 하 여 해당 범위를 변경 하지 않는 한 해당 범위에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-239">You create them in a particular scope, and they affect only that scope unless you use a cmdlet parameter or a scope modifier to change that scope.</span></span>

<span data-ttu-id="f637f-240">그러나 점 원본 표기법을 사용 하 여 현재 범위에 스크립트나 함수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-240">But, you can add a script or function to the current scope by using dot source notation.</span></span> <span data-ttu-id="f637f-241">그런 다음 현재 범위에서 스크립트를 실행할 때 스크립트에서 만드는 모든 함수, 별칭 및 변수를 현재 범위에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-241">Then, when a script runs in the current scope, any functions, aliases, and variables that the script creates are available in the current scope.</span></span>

<span data-ttu-id="f637f-242">현재 범위에 함수를 추가 하려면 함수 호출에서 함수의 경로와 이름 앞에 점 (.)과 공백을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-242">To add a function to the current scope, type a dot (.) and a space before the path and name of the function in the function call.</span></span>

<span data-ttu-id="f637f-243">예를 들어 스크립트 범위의 C:\Scripts 디렉터리 (스크립트의 기본값)에서 Sample.ps1 스크립트를 실행 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-243">For example, to run the Sample.ps1 script from the C:\Scripts directory in the script scope (the default for scripts), use the following command:</span></span>

```powershell
c:\scripts\sample.ps1
```

<span data-ttu-id="f637f-244">로컬 범위에서 Sample.ps1 스크립트를 실행 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-244">To run the Sample.ps1 script in the local scope, use the following command:</span></span>

```powershell
. c:\scripts.sample.ps1
```

<span data-ttu-id="f637f-245">Call 연산자 (&)를 사용 하 여 함수 또는 스크립트를 실행 하는 경우 현재 범위에 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-245">When you use the call operator (&) to run a function or script, it is not added to the current scope.</span></span> <span data-ttu-id="f637f-246">다음 예에서는 call 연산자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-246">The following example uses the call operator:</span></span>

```powershell
& c:\scripts.sample.ps1
```

<span data-ttu-id="f637f-247">[About_operators](about_operators.md)에서 호출 연산자에 대 한 자세한 내용을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-247">You can read more about the call operator in [about_operators](about_operators.md).</span></span>

<span data-ttu-id="f637f-248">Sample.ps1 스크립트에서 만드는 모든 별칭, 함수 또는 변수는 현재 범위에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-248">Any aliases, functions, or variables that the Sample.ps1 script creates are not available in the current scope.</span></span>

## <a name="restricting-without-scope"></a><span data-ttu-id="f637f-249">범위 없이 제한</span><span class="sxs-lookup"><span data-stu-id="f637f-249">Restricting Without Scope</span></span>

<span data-ttu-id="f637f-250">몇 가지 PowerShell 개념은 범위를 포함 하거나 범위와 상호 작용 하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-250">A few PowerShell concepts are similar to scope or interact with scope.</span></span> <span data-ttu-id="f637f-251">이러한 개념은 범위 또는 범위 동작과 혼동 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-251">These concepts may be confused with scope or the behavior of scope.</span></span>

<span data-ttu-id="f637f-252">세션, 모듈 및 중첩 된 프롬프트는 독립적인 환경 이지만 세션에서 전역 범위의 자식 범위가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-252">Sessions, modules, and nested prompts are self-contained environments, but they are not child scopes of the global scope in the session.</span></span>

### <a name="sessions"></a><span data-ttu-id="f637f-253">세션</span><span class="sxs-lookup"><span data-stu-id="f637f-253">Sessions</span></span>

<span data-ttu-id="f637f-254">세션은 PowerShell을 실행 하는 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-254">A session is an environment in which PowerShell runs.</span></span> <span data-ttu-id="f637f-255">원격 컴퓨터에서 세션을 만들 때 PowerShell은 원격 컴퓨터에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-255">When you create a session on a remote computer, PowerShell establishes a persistent connection to the remote computer.</span></span> <span data-ttu-id="f637f-256">영구 연결을 사용 하면 여러 관련 명령에 세션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-256">The persistent connection lets you use the session for multiple related commands.</span></span>

<span data-ttu-id="f637f-257">세션은 포함 된 환경 이기 때문에 자체 범위를 갖지만 세션이 만들어진 세션의 자식 범위가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-257">Because a session is a contained environment, it has its own scope, but a session is not a child scope of the session in which it was created.</span></span> <span data-ttu-id="f637f-258">세션은 고유한 전역 범위를 사용 하 여 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-258">The session starts with its own global scope.</span></span> <span data-ttu-id="f637f-259">이 범위는 세션의 전역 범위와는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-259">This scope is independent of the global scope of the session.</span></span> <span data-ttu-id="f637f-260">세션에서 자식 범위를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-260">You can create child scopes in the session.</span></span> <span data-ttu-id="f637f-261">예를 들어 스크립트를 실행 하 여 세션에서 자식 범위를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-261">For example, you can run a script to create a child scope in a session.</span></span>

### <a name="modules"></a><span data-ttu-id="f637f-262">모듈</span><span class="sxs-lookup"><span data-stu-id="f637f-262">Modules</span></span>

<span data-ttu-id="f637f-263">Powershell 모듈을 사용 하 여 PowerShell 도구를 공유 하 고 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-263">You can use a PowerShell module to share and deliver PowerShell tools.</span></span> <span data-ttu-id="f637f-264">모듈은 cmdlet, 스크립트, 함수, 변수, 별칭 및 기타 유용한 항목을 포함할 수 있는 단위입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-264">A module is a unit that can contain cmdlets, scripts, functions, variables, aliases, and other useful items.</span></span> <span data-ttu-id="f637f-265">명시적으로 정의 되지 않은 경우 모듈의 항목은 모듈 외부에서 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-265">Unless explicitly defined, the items in a module are not accessible outside the module.</span></span> <span data-ttu-id="f637f-266">따라서 세션에 모듈을 추가 하 고 다른 항목이 세션의 cmdlet, 스크립트, 함수 및 기타 항목을 재정의할 수 있는 걱정 없이 공용 항목을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-266">Therefore, you can add the module to your session and use the public items without worrying that the other items might override the cmdlets, scripts, functions, and other items in your session.</span></span>

<span data-ttu-id="f637f-267">기본적으로 모듈은 현재 _범위가_ 아닌 현재 _세션 상태의_ 최상위 수준에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-267">By default, modules are loaded into the top-level of the current _session state_ not the current _scope_.</span></span> <span data-ttu-id="f637f-268">현재 세션 상태는 모듈 세션 상태 또는 전역 세션 상태일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-268">The current session state could be a module session state or the global session state.</span></span> <span data-ttu-id="f637f-269">세션에 모듈을 추가 해도 범위는 변경 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-269">Adding a module to a session does not change the scope.</span></span> <span data-ttu-id="f637f-270">전역 범위에 있으면 모듈이 전역 세션 상태에 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-270">If you are in the global scope, then modules are loaded into the global session state.</span></span> <span data-ttu-id="f637f-271">모든 내보내기는 전역 테이블에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-271">Any exports are placed into the global tables.</span></span>
<span data-ttu-id="f637f-272">Module1 _내_ 에서 module2를 로드 하는 경우 module2는 전역 세션 상태가 아닌 module1의 세션 상태로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-272">If you load module2 from _within_ module1, module2 is loaded into the session state of module1 not the global session state.</span></span> <span data-ttu-id="f637f-273">Module2에서의 모든 내보내기는 module1 세션 상태의 맨 위에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-273">Any exports from module2 are placed at the top of the module1 session state.</span></span> <span data-ttu-id="f637f-274">를 사용 하는 경우 `Import-Module -Scope local` 내보내기는 최상위 수준 대신 현재 범위 개체에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-274">If you use `Import-Module -Scope local`, then the exports are placed into the current scope object rather than at the top level.</span></span> <span data-ttu-id="f637f-275">_모듈에_ 있고 `Import-Module -Scope global` (또는)를 사용 하 여 `Import-Module -Global` 다른 모듈을 로드 하는 경우 해당 모듈 및 내보내기는 모듈의 로컬 세션 상태 대신 전역 세션 상태로 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-275">If you are _in a module_ and use `Import-Module -Scope global` (or `Import-Module -Global`) to load another module, that module and it's exports are loaded into the global session state instead of the module's local session state.</span></span> <span data-ttu-id="f637f-276">이 기능은 모듈을 조작 하는 모듈을 작성 하기 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-276">This feature was designed for writing module that manipulate modules.</span></span> <span data-ttu-id="f637f-277">**Windowscompatibility** 모듈은이를 통해 프록시 모듈을 전역 세션 상태로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-277">The **WindowsCompatibility** module does this to import proxy modules into the global session state.</span></span>

<span data-ttu-id="f637f-278">세션 상태 내에서 모듈은 고유한 범위를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-278">Within the session state, modules have their own scope.</span></span> <span data-ttu-id="f637f-279">다음 모듈을 참조 `C:\temp\mod1.psm1` 하세요.</span><span class="sxs-lookup"><span data-stu-id="f637f-279">Consider the following module `C:\temp\mod1.psm1`:</span></span>

```powershell
$a = "Hello"

function foo {
    "`$a = $a"
    "`$global:a = $global:a"
}
```

<span data-ttu-id="f637f-280">이제 전역 변수 `$a` 를 만들고 값을 지정 하 고 **foo** 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-280">Now we create a global variable `$a`, give it a value and call the function **foo**.</span></span>

```powershell
$a = "Goodbye"
foo
```

<span data-ttu-id="f637f-281">모듈은 모듈 범위에서 변수를 선언 하 `$a` 고 함수 **foo** 는 두 범위 모두에서 변수 값을 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-281">The module declares the variable `$a` in the module scope then the function **foo** outputs the value of the variable in both scopes.</span></span>

```Output
$a = Hello
$global:a = Goodbye
```

### <a name="nested-prompts"></a><span data-ttu-id="f637f-282">중첩 프롬프트</span><span class="sxs-lookup"><span data-stu-id="f637f-282">Nested Prompts</span></span>

<span data-ttu-id="f637f-283">중첩 된 프롬프트에는 고유한 범위가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-283">Nested prompts do not have their own scope.</span></span> <span data-ttu-id="f637f-284">중첩 된 프롬프트를 입력 하는 경우 중첩 된 프롬프트는 환경의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-284">When you enter a nested prompt, the nested prompt is a subset of the environment.</span></span> <span data-ttu-id="f637f-285">그러나 로컬 범위 내에 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-285">But, you remain within the local scope.</span></span>

<span data-ttu-id="f637f-286">스크립트에는 고유한 범위가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-286">Scripts do have their own scope.</span></span> <span data-ttu-id="f637f-287">스크립트를 디버깅 하는 경우 스크립트의 중단점에 도달 하면 스크립트 범위를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-287">If you are debugging a script, and you reach a breakpoint in the script, you enter the script scope.</span></span>

### <a name="private-option"></a><span data-ttu-id="f637f-288">개인 옵션</span><span class="sxs-lookup"><span data-stu-id="f637f-288">Private Option</span></span>

<span data-ttu-id="f637f-289">별칭 및 변수에는 **Private** 값을 사용할 수 있는 **Option** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-289">Aliases and variables have an **Option** property that can take a value of **Private**.</span></span> <span data-ttu-id="f637f-290">**개인** 옵션을 포함 하는 항목은 생성 된 범위에서 표시 하 고 변경할 수 있지만 해당 범위 외부에서 보거나 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-290">Items that have the **Private** option can be viewed and changed in the scope in which they are created, but they cannot be viewed or changed outside that scope.</span></span>

<span data-ttu-id="f637f-291">예를 들어 전역 범위에 개인 옵션을 포함 하는 변수를 만든 다음 스크립트를 실행 하는 경우 `Get-Variable` 스크립트의 명령은 private 변수를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-291">For example, if you create a variable that has a private option in the global scope and then run a script, `Get-Variable` commands in the script do not display the private variable.</span></span> <span data-ttu-id="f637f-292">이 인스턴스에서 전역 범위 한정자를 사용 해도 전용 변수가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-292">Using the global scope modifier in this instance does not display the private variable.</span></span>

<span data-ttu-id="f637f-293">,, 및 cmdlet의 option 매개 변수를 사용 `New-Variable` `Set-Variable` 하 여 `New-Alias` `Set-Alias` option 속성의 값을 Private으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-293">You can use the Option parameter of the `New-Variable`, `Set-Variable`, `New-Alias`, and `Set-Alias` cmdlets to set the value of the Option property to Private.</span></span>

### <a name="visibility"></a><span data-ttu-id="f637f-294">가시 거리</span><span class="sxs-lookup"><span data-stu-id="f637f-294">Visibility</span></span>

<span data-ttu-id="f637f-295">변수 또는 별칭의 **Visibility** 속성은 컨테이너가 만들어진 컨테이너 외부에서 항목을 볼 수 있는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-295">The **Visibility** property of a variable or alias determines whether you can see the item outside the container, in which it was created.</span></span> <span data-ttu-id="f637f-296">컨테이너는 모듈, 스크립트 또는 스냅인 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-296">A container could be a module, script, or snap-in.</span></span> <span data-ttu-id="f637f-297">표시 유형은 **Option** 속성의 **전용** 값이 범위에 대해 디자인 된 것과 동일한 방식으로 컨테이너를 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-297">Visibility is designed for containers in the same way that the **Private** value of the **Option** property is designed for scopes.</span></span>

<span data-ttu-id="f637f-298">**Visibility** 속성은 **Public** 및 **Private** 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-298">The **Visibility** property takes the **Public** and **Private** values.</span></span> <span data-ttu-id="f637f-299">비공개 표시를 포함 하는 항목은 해당 항목을 만든 컨테이너 에서만 보고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-299">Items that have private visibility can be viewed and changed only in the container in which they were created.</span></span> <span data-ttu-id="f637f-300">컨테이너를 추가 하거나 가져올 경우 개인 표시 유형을 포함 하는 항목을 보거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-300">If the container is added or imported, the items that have private visibility cannot be viewed or changed.</span></span>

<span data-ttu-id="f637f-301">표시 유형은 컨테이너를 위해 설계 되었으므로 범위에서 다르게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-301">Because visibility is designed for containers, it works differently in a scope.</span></span>

- <span data-ttu-id="f637f-302">전역 범위에서 비공개로 표시 되는 항목을 만드는 경우 모든 범위에서 항목을 보거나 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-302">If you create an item that has private visibility in the global scope, you cannot view or change the item in any scope.</span></span>
- <span data-ttu-id="f637f-303">전용 표시 유형이 있는 변수의 값을 보거나 변경 하려고 하면 PowerShell에서 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-303">If you try to view or change the value of a variable that has private visibility, PowerShell returns an error message.</span></span>

<span data-ttu-id="f637f-304">및 cmdlet을 사용 `New-Variable` `Set-Variable` 하 여 개인 표시 유형을 포함 하는 변수를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-304">You can use the `New-Variable` and `Set-Variable` cmdlets to create a variable that has private visibility.</span></span>

## <a name="examples"></a><span data-ttu-id="f637f-305">예제</span><span class="sxs-lookup"><span data-stu-id="f637f-305">Examples</span></span>

### <a name="example-1-change-a-variable-value-only-in-a-script"></a><span data-ttu-id="f637f-306">예제 1: 스크립트 에서만 변수 값 변경</span><span class="sxs-lookup"><span data-stu-id="f637f-306">Example 1: Change a Variable Value Only in a Script</span></span>

<span data-ttu-id="f637f-307">다음 명령은 스크립트의 변수 값을 변경 합니다 `$ConfirmPreference` .</span><span class="sxs-lookup"><span data-stu-id="f637f-307">The following command changes the value of the `$ConfirmPreference` variable in a script.</span></span> <span data-ttu-id="f637f-308">변경 내용은 전역 범위에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-308">The change does not affect the global scope.</span></span>

<span data-ttu-id="f637f-309">먼저 `$ConfirmPreference` 로컬 범위에서 변수의 값을 표시 하려면 다음 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-309">First, to display the value of the `$ConfirmPreference` variable in the local scope, use the following command:</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="f637f-310">다음 명령을 포함 하는 Scope.ps1 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-310">Create a Scope.ps1 script that contains the following commands:</span></span>

```powershell
$ConfirmPreference = "Low"
"The value of `$ConfirmPreference is $ConfirmPreference."
```

<span data-ttu-id="f637f-311">스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-311">Run the script.</span></span> <span data-ttu-id="f637f-312">스크립트는 변수의 값을 변경한 `$ConfirmPreference` 다음 스크립트 범위에서 해당 값을 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-312">The script changes the value of the `$ConfirmPreference` variable and then reports its value in the script scope.</span></span> <span data-ttu-id="f637f-313">출력은 다음 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-313">The output should resemble the following output:</span></span>

```output
The value of $ConfirmPreference is Low.
```

<span data-ttu-id="f637f-314">다음으로 `$ConfirmPreference` 현재 범위에서 변수의 현재 값을 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-314">Next, test the current value of the `$ConfirmPreference` variable in the current scope.</span></span>

```
PS>  $ConfirmPreference
High
```

<span data-ttu-id="f637f-315">이 예에서는 스크립트 범위의 변수 값에 대 한 변경 내용이 부모 범위의 변수 값에 영향을 주지 않는다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-315">This example shows that changes to the value of a variable in the script scope does not affect the variable\`s value in the parent scope.</span></span>

### <a name="example-2-view-a-variable-value-in-different-scopes"></a><span data-ttu-id="f637f-316">예 2: 다른 범위에서 변수 값 보기</span><span class="sxs-lookup"><span data-stu-id="f637f-316">Example 2: View a Variable Value in Different Scopes</span></span>

<span data-ttu-id="f637f-317">범위 한정자를 사용 하 여 로컬 범위와 부모 범위에서 변수의 값을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-317">You can use scope modifiers to view the value of a variable in the local scope and in a parent scope.</span></span>

<span data-ttu-id="f637f-318">먼저 `$test` 전역 범위에서 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-318">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="f637f-319">다음으로 변수를 정의 하는 Sample.ps1 스크립트를 만듭니다 `$test` .</span><span class="sxs-lookup"><span data-stu-id="f637f-319">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="f637f-320">스크립트에서 범위 한정자를 사용 하 여 변수의 전역 또는 로컬 버전을 참조 `$test` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-320">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="f637f-321">Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="f637f-321">In Sample.ps1:</span></span>

```powershell
$test = "Local"
"The local value of `$test is $test."
"The global value of `$test is $global:test."
```

<span data-ttu-id="f637f-322">Sample.ps1를 실행 하는 경우 출력은 다음 출력과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-322">When you run Sample.ps1, the output should resemble the following output:</span></span>

```output
The local value of $test is Local.
The global value of $test is Global.
```

<span data-ttu-id="f637f-323">스크립트가 완료 되 면 세션에의 전역 값만 `$test` 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-323">When the script is complete, only the global value of `$test` is defined in the session.</span></span>

```
PS>  $test
Global
```

### <a name="example-3-change-the-value-of-a-variable-in-a-parent-scope"></a><span data-ttu-id="f637f-324">예 3: 부모 범위에서 변수 값 변경</span><span class="sxs-lookup"><span data-stu-id="f637f-324">Example 3: Change the Value of a Variable in a Parent Scope</span></span>

<span data-ttu-id="f637f-325">개인 옵션 또는 다른 방법을 사용 하 여 항목을 보호 하지 않는 한 부모 범위에서 변수 값을 보고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-325">Unless you protect an item by using the Private option or another method, you can view and change the value of a variable in a parent scope.</span></span>

<span data-ttu-id="f637f-326">먼저 `$test` 전역 범위에서 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-326">First, define a `$test` variable in the global scope.</span></span>

```powershell
$test = "Global"
```

<span data-ttu-id="f637f-327">다음으로 변수를 정의 하는 Sample.ps1 스크립트를 만듭니다 `$test` .</span><span class="sxs-lookup"><span data-stu-id="f637f-327">Next, create a Sample.ps1 script that defines the `$test` variable.</span></span> <span data-ttu-id="f637f-328">스크립트에서 범위 한정자를 사용 하 여 변수의 전역 또는 로컬 버전을 참조 `$test` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-328">In the script, use a scope modifier to refer to either the global or local versions of the `$test` variable.</span></span>

<span data-ttu-id="f637f-329">Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="f637f-329">In Sample.ps1:</span></span>

```powershell
$global:test = "Local"
"The global value of `$test is $global:test."
```

<span data-ttu-id="f637f-330">스크립트가 완료 되 면의 전역 값 `$test` 이 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-330">When the script is complete, the global value of `$test` is changed.</span></span>

```
PS>  $test
Local
```

### <a name="example-4-creating-a-private-variable"></a><span data-ttu-id="f637f-331">예제 4: 전용 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="f637f-331">Example 4: Creating a Private Variable</span></span>

<span data-ttu-id="f637f-332">Private 변수는 값이 *private* 인 **Option** 속성이 있는 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-332">A private variable is a variable that has an **Option** property that has a value of *Private*.</span></span> <span data-ttu-id="f637f-333">*Private* 변수는 자식 범위에 의해 상속 되지만 해당 변수는 생성 된 범위 에서만 보거나 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-333">*Private* variables are inherited by the child scope, but they can only be viewed or changed in the scope in which they were created.</span></span>

<span data-ttu-id="f637f-334">다음 명령은 로컬 범위에서 이라는 private 변수를 만듭니다 `$ptest` .</span><span class="sxs-lookup"><span data-stu-id="f637f-334">The following command creates a private variable called `$ptest` in the local scope.</span></span>

```powershell
New-Variable -Name ptest -Value 1 -Option private
```

<span data-ttu-id="f637f-335">로컬 범위에서 값을 표시 하 고 변경할 수 있습니다 `$ptest` .</span><span class="sxs-lookup"><span data-stu-id="f637f-335">You can display and change the value of `$ptest` in the local scope.</span></span>

```
PS>  $ptest
1

PS>  $ptest = 2
PS>  $ptest
2
```

<span data-ttu-id="f637f-336">다음 명령을 포함 하는 Sample.ps1 스크립트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-336">Next, create a Sample.ps1 script that contains the following commands.</span></span> <span data-ttu-id="f637f-337">명령은를 표시 하 고 값을 변경 하려고 `$ptest` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-337">The command tries to display and change the value of `$ptest`.</span></span>

<span data-ttu-id="f637f-338">Sample.ps1:</span><span class="sxs-lookup"><span data-stu-id="f637f-338">In Sample.ps1:</span></span>

```powershell
"The value of `$Ptest is $Ptest."
"The value of `$Ptest is $global:Ptest."
```

<span data-ttu-id="f637f-339">`$ptest`변수는 스크립트 범위에 표시 되지 않으며 출력은 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-339">The `$ptest` variable is not visible in the script scope, the output is empty.</span></span>

```powershell
"The value of $Ptest is ."
"The value of $Ptest is ."
```

### <a name="example-5-using-a-local-variable-in-a-remote-command"></a><span data-ttu-id="f637f-340">예 5: 원격 명령에서 지역 변수 사용</span><span class="sxs-lookup"><span data-stu-id="f637f-340">Example 5: Using a Local Variable in a Remote Command</span></span>

<span data-ttu-id="f637f-341">로컬 세션에서 만든 원격 명령의 변수에는 `Using` 범위 한정자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-341">For variables in a remote command created in the local session, use the `Using` scope modifier.</span></span> <span data-ttu-id="f637f-342">PowerShell에서는 원격 명령의 변수가 원격 세션에서 만들어진 것으로 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-342">PowerShell assumes that the variables in remote commands were created in the remote session.</span></span>

<span data-ttu-id="f637f-343">구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-343">The syntax is:</span></span>

```
$Using:<VariableName>
```

<span data-ttu-id="f637f-344">예를 들어 다음 명령은 `$Cred` 로컬 세션에서 변수를 만든 다음 `$Cred` 원격 명령에 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-344">For example, the following commands create a `$Cred` variable in the local session and then use the `$Cred` variable in a remote command:</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {Remove-Item .\Test*.ps1 -Credential $Using:Cred}
```

<span data-ttu-id="f637f-345">Using 범위는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-345">The Using scope was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="f637f-346">PowerShell 2.0에서 로컬 세션에 변수가 생성 되었음을 나타내려면 다음 명령 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f637f-346">In PowerShell 2.0, to indicate that a variable was created in the local session, use the following command format.</span></span>

```powershell
$Cred = Get-Credential
Invoke-Command $s {
  param($c)
  Remove-Item .\Test*.ps1 -Credential $c
} -ArgumentList $Cred
```

## <a name="see-also"></a><span data-ttu-id="f637f-347">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f637f-347">See also</span></span>

[<span data-ttu-id="f637f-348">about_Variables</span><span class="sxs-lookup"><span data-stu-id="f637f-348">about_Variables</span></span>](about_Variables.md)

[<span data-ttu-id="f637f-349">about_Environment_Variables</span><span class="sxs-lookup"><span data-stu-id="f637f-349">about_Environment_Variables</span></span>](about_Environment_Variables.md)

[<span data-ttu-id="f637f-350">about_Functions</span><span class="sxs-lookup"><span data-stu-id="f637f-350">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="f637f-351">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="f637f-351">about_Script_Blocks</span></span>](about_Script_Blocks.md)

[<span data-ttu-id="f637f-352">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="f637f-352">Start-ThreadJob</span></span>](/powershell/module/ThreadJob/Start-ThreadJob)
