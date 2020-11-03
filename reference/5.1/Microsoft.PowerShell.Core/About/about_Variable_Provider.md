---
description: 변수
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_variable_provider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 변수 공급자
ms.openlocfilehash: ff3d457e8d057329544cf1265720fc041a804973
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223225"
---
# <a name="variable-provider"></a><span data-ttu-id="80021-104">변수 공급자</span><span class="sxs-lookup"><span data-stu-id="80021-104">Variable provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="80021-105">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="80021-105">Provider name</span></span>

<span data-ttu-id="80021-106">변수</span><span class="sxs-lookup"><span data-stu-id="80021-106">Variable</span></span>

## <a name="drives"></a><span data-ttu-id="80021-107">드라이브</span><span class="sxs-lookup"><span data-stu-id="80021-107">Drives</span></span>

`Variable:`

## <a name="capabilities"></a><span data-ttu-id="80021-108">기능</span><span class="sxs-lookup"><span data-stu-id="80021-108">Capabilities</span></span>

<span data-ttu-id="80021-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="80021-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="80021-110">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="80021-110">Short description</span></span>

<span data-ttu-id="80021-111">PowerShell 변수 및 해당 값에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-111">Provides access to the PowerShell variables and to their values.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="80021-112">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="80021-112">Detailed description</span></span>

<span data-ttu-id="80021-113">PowerShell **변수** 공급자를 통해 현재 콘솔에서 powershell 변수를 가져오고 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-113">The PowerShell **Variable** provider lets you get, add, change, clear, and delete PowerShell variables in the current console.</span></span>

<span data-ttu-id="80021-114">PowerShell **변수** 공급자는 자동 변수, 기본 설정 변수 및 사용자가 만드는 변수를 포함 하 여 powershell이 만드는 변수를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-114">The PowerShell **Variable** provider supports the variables that PowerShell creates, including the automatic variables, the preference variables, and the variables that you create.</span></span>

<span data-ttu-id="80021-115">**변수** 드라이브는 변수 개체만 포함 하는 플랫 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="80021-115">The **Variable** drive is a flat namespace that contains only the variable objects.</span></span> <span data-ttu-id="80021-116">변수에는 하위 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-116">The variables have no child items.</span></span>

<span data-ttu-id="80021-117">**변수** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-117">The **Variable** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="80021-118">Get-Location</span><span class="sxs-lookup"><span data-stu-id="80021-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="80021-119">Set-Location</span><span class="sxs-lookup"><span data-stu-id="80021-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="80021-120">Get-Item</span><span class="sxs-lookup"><span data-stu-id="80021-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="80021-121">New-Item</span><span class="sxs-lookup"><span data-stu-id="80021-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="80021-122">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="80021-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="80021-123">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="80021-123">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

<span data-ttu-id="80021-124">또한 PowerShell에는 변수를 보고 변경할 수 있도록 특별히 설계 된 cmdlet 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-124">PowerShell also includes a set of cmdlets designed especially to view and to change variables.</span></span> <span data-ttu-id="80021-125">**변수** cmdlet을 사용 하는 경우 이름에 드라이브를 지정할 필요가 없습니다 `Variable:` .</span><span class="sxs-lookup"><span data-stu-id="80021-125">When you use **Variable** cmdlets, you do not need to specify the `Variable:` drive in the name.</span></span> <span data-ttu-id="80021-126">이 문서에서는 **변수** cmdlet 작업에 대해 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-126">This article does not cover working with **Variable** cmdlets.</span></span>

- [<span data-ttu-id="80021-127">Get-Variable</span><span class="sxs-lookup"><span data-stu-id="80021-127">Get-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Get-Variable)
- [<span data-ttu-id="80021-128">New-Variable</span><span class="sxs-lookup"><span data-stu-id="80021-128">New-Variable</span></span>](xref:Microsoft.PowerShell.Utility.New-Variable)
- [<span data-ttu-id="80021-129">Set-Variable</span><span class="sxs-lookup"><span data-stu-id="80021-129">Set-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Set-Variable)
- [<span data-ttu-id="80021-130">Remove-Variable</span><span class="sxs-lookup"><span data-stu-id="80021-130">Remove-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Remove-Variable)
- [<span data-ttu-id="80021-131">Clear-Variable</span><span class="sxs-lookup"><span data-stu-id="80021-131">Clear-Variable</span></span>](xref:Microsoft.PowerShell.Utility.Clear-Variable)

> [!NOTE]
> <span data-ttu-id="80021-132">Cmdlet을 사용 하지 않고 PowerShell 식 파서를 사용 하 여 변수 값을 만들고 확인 하 고 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-132">You can also use the PowerShell expression parser to create, view, and change the values of variables without using the cmdlets.</span></span> <span data-ttu-id="80021-133">변수를 직접 사용 하는 경우 달러 기호 ()를 사용 `$` 하 여 이름을 변수로 식별 하 고 대입 연산자 ()를 사용 하 여 `=` 해당 값을 설정 하 고 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-133">When working with variables directly, use a dollar sign (`$`) to identify the name as a variable and the assignment operator (`=`)to establish and change its value.</span></span> <span data-ttu-id="80021-134">예를 들어 `$p = Get-Process` 은 변수를 만들고 `p` 명령의 결과를 저장 `Get-Process` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-134">For example, `$p = Get-Process` creates the `p` variable and stores the results of a `Get-Process` command in it.</span></span>

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="80021-135">이 공급자가 노출 하는 형식</span><span class="sxs-lookup"><span data-stu-id="80021-135">Types exposed by this provider</span></span>

<span data-ttu-id="80021-136">변수는 여러 가지 형식 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-136">Variables can be one of several different types.</span></span> <span data-ttu-id="80021-137">대부분의 변수는 클래스의 인스턴스입니다 `PSVariable` .</span><span class="sxs-lookup"><span data-stu-id="80021-137">Most variables will be instances of the `PSVariable` class.</span></span> <span data-ttu-id="80021-138">다른 변수 및 해당 형식은 아래에 나열 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-138">Other variables and their types are listed below.</span></span>

- <span data-ttu-id="80021-139">`?`변수는 클래스의 인스턴스입니다 `QuestionMarkVariable` .</span><span class="sxs-lookup"><span data-stu-id="80021-139">The `?` variable is an instance of the `QuestionMarkVariable` class.</span></span>
- <span data-ttu-id="80021-140">`null`변수는 클래스의 인스턴스입니다 `NullVariable` .</span><span class="sxs-lookup"><span data-stu-id="80021-140">The `null` variable is an instance of the `NullVariable` class.</span></span>
- <span data-ttu-id="80021-141">최대 개수 변수는 클래스의 인스턴스입니다 `SessionStateCapacityVariable` .</span><span class="sxs-lookup"><span data-stu-id="80021-141">The maximum count variables are instances of the `SessionStateCapacityVariable` class.</span></span>
- <span data-ttu-id="80021-142">`LocalVariable` 인스턴스에는 다음과 같은 현재 실행에 대 한 정보가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80021-142">`LocalVariable` instances contain information about current execution, such as:</span></span>
  - `MyInvocation`
  - `PSCommandPath`
  - `PSScriptRoot`
  - `PSBoundParameters`
  - `args`
  - `input`

## <a name="navigating-the-variable-drives"></a><span data-ttu-id="80021-143">변수 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="80021-143">Navigating the Variable drives</span></span>

<span data-ttu-id="80021-144">**변수** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Variable:` .</span><span class="sxs-lookup"><span data-stu-id="80021-144">The **Variable** provider exposes its data store in the `Variable:` drive.</span></span> <span data-ttu-id="80021-145">변수를 사용 하려면 위치를 `Variable:` drive ()로 변경 `Set-Location Variable:` 하거나 다른 PowerShell 드라이브에서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-145">To work with variables, you can change your location to the `Variable:` drive (`Set-Location Variable:`), or you can work from any other PowerShell drive.</span></span> <span data-ttu-id="80021-146">다른 위치에서 변수를 참조 하려면 경로에 드라이브 이름 ()을 사용 `Variable:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-146">To reference a variable from another location, use the drive name (`Variable:`) in the path.</span></span>

```powershell
Set-Location Variable:
```

<span data-ttu-id="80021-147">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-147">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="80021-148">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-148">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="80021-149">다른 PowerShell 드라이브에서 **변수** 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-149">You can also work with the **Variable** provider from any other PowerShell drive.</span></span> <span data-ttu-id="80021-150">다른 위치에서 변수를 참조 하려면 경로에 드라이브 이름을 사용 `Variable:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-150">To reference an variable from another location, use the drive name `Variable:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="80021-151">PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-151">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="80021-152">`dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="80021-152">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="80021-153">및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="80021-153">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-value-of-variables"></a><span data-ttu-id="80021-154">변수의 값 표시</span><span class="sxs-lookup"><span data-stu-id="80021-154">Displaying the value of variables</span></span>

### <a name="get-all-variables-in-the-current-session"></a><span data-ttu-id="80021-155">현재 세션의 모든 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="80021-155">Get all variables in the current session</span></span>

<span data-ttu-id="80021-156">이 명령은 현재 세션의 모든 변수 및 변수 값 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="80021-156">This command gets the list of all the variables and their values in the current session.</span></span> <span data-ttu-id="80021-157">모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-157">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:
```

### <a name="get-a-variable-using-its-provider-path"></a><span data-ttu-id="80021-158">공급자 경로를 사용 하 여 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="80021-158">Get a variable using its provider path</span></span>

<span data-ttu-id="80021-159">이 명령은 달러 기호 ()로 시작 하는 공급자 경로를 사용 하 여 변수 값을 검색 `$` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-159">This command retrieves a variables value using its provider path prefixed by the dollar sign (`$`).</span></span> <span data-ttu-id="80021-160">이는 변수 이름 앞에 달러 기호 ()를 접두사로 사용 하는 것과 동일한 효과를 가집니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="80021-160">This has the same effect as prefixing the variables name with the dollar sign (`$`).</span></span>

```powershell
$variable:home
```

### <a name="get-variables-using-wildcards"></a><span data-ttu-id="80021-161">와일드 카드를 사용 하 여 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="80021-161">Get variables using wildcards</span></span>

<span data-ttu-id="80021-162">이 명령은 이름이 "max"로 시작하는 변수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="80021-162">This command gets the variables with names that begin with "max".</span></span> <span data-ttu-id="80021-163">모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-163">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Variable:max*
```

### <a name="get-the-value-of-the--variable"></a><span data-ttu-id="80021-164">의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="80021-164">Get the value of the ?</span></span> <span data-ttu-id="80021-165">변수</span><span class="sxs-lookup"><span data-stu-id="80021-165">variable</span></span>

<span data-ttu-id="80021-166">이 명령은 `-LiteralPath` [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) 의 매개 변수를 사용 하 여 `?` 드라이브 내에서 변수 값을 가져옵니다 `Variable:` .</span><span class="sxs-lookup"><span data-stu-id="80021-166">This command uses the `-LiteralPath` parameter of [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) to get the value of the `?` variable from within the `Variable:` drive.</span></span> <span data-ttu-id="80021-167">는 `?` 경로에서 와일드 카드 이지만 `Get-ChildItem` 매개 변수 값에서 와일드 카드를 확인 하려고 시도 하지 않습니다 `-LiteralPath` .</span><span class="sxs-lookup"><span data-stu-id="80021-167">The `?` is a wildcard in paths, but `Get-ChildItem` does not attempt to resolve any wildcards in the values of the `-LiteralPath` parameter.</span></span>

```powershell
Get-ChildItem -Literalpath ?
```

### <a name="get-readonly-and-constant-variables"></a><span data-ttu-id="80021-168">ReadOnly 및 상수 변수 가져오기</span><span class="sxs-lookup"><span data-stu-id="80021-168">Get ReadOnly and Constant variables</span></span>

<span data-ttu-id="80021-169">이 명령은 Options 속성 값이 또는 인 변수를 `ReadOnly` 가져옵니다 `Constant` . **Options**</span><span class="sxs-lookup"><span data-stu-id="80021-169">This command gets the variables that have the values of `ReadOnly` or `Constant` for their **Options** property.</span></span>

```powershell
Get-ChildItem -Path Variable: | Where-Object {
   $_.options -Match "Constant" `
   -or $_.options -Match "ReadOnly"
 } | Format-List -Property name, value, options
```

## <a name="creating-variables"></a><span data-ttu-id="80021-170">변수 만들기</span><span class="sxs-lookup"><span data-stu-id="80021-170">Creating variables</span></span>

### <a name="create-a-new-variable"></a><span data-ttu-id="80021-171">새 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="80021-171">Create a new variable</span></span>

<span data-ttu-id="80021-172">이 명령은 변수를 만들고 `services` 명령 결과를 저장 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-172">This command creates the `services` variable and stores the results of a `Get-Service` command in it.</span></span> <span data-ttu-id="80021-173">현재 위치가 드라이브에 있기 때문에 `Variable:` `-Path` 매개 변수 값은 `.` 현재 위치를 나타내는 점 ()입니다.</span><span class="sxs-lookup"><span data-stu-id="80021-173">Because the current location is in the `Variable:` drive, the value of the `-Path` parameter is a dot (`.`), which represents the current location.</span></span>

<span data-ttu-id="80021-174">명령을 둘러싼 괄호는 `Get-Service` 변수가 만들어지기 전에 명령이 실행 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-174">The parentheses around the `Get-Service` command ensure that the command is executed before the variable is created.</span></span> <span data-ttu-id="80021-175">괄호가 없으면 새 변수 값이 "Get-Service" 문자열이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="80021-175">Without the parentheses, the value of the new variable is a "Get-Service" string.</span></span>

```powershell
New-Item -Path . -Name services -Value (Get-Service)
```

### <a name="create-a-variable-using-an-absolute-path"></a><span data-ttu-id="80021-176">절대 경로를 사용 하 여 변수 만들기</span><span class="sxs-lookup"><span data-stu-id="80021-176">Create a variable using an absolute path</span></span>

<span data-ttu-id="80021-177">이 명령은 변수를 만들고 `services` 명령 결과를 저장 `Get-Service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-177">This command creates a `services` variable and stores the result of a `Get-Service` command in it.</span></span>

```powershell
New-Item -Path Variable:services -Value Get-Service
```

 <span data-ttu-id="80021-178">값 없는 변수를 만들려면 대입 연산자를 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-178">To create a variable without a value, omit the assignment operator.</span></span>

## <a name="changing-variables"></a><span data-ttu-id="80021-179">변수 변경</span><span class="sxs-lookup"><span data-stu-id="80021-179">Changing variables</span></span>

### <a name="rename-a-variable"></a><span data-ttu-id="80021-180">변수 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="80021-180">Rename a variable</span></span>

<span data-ttu-id="80021-181">이 명령은 cmdlet을 사용 하 여 `Rename-Item` 변수 이름을로 변경 `a` `processes` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-181">This command uses the `Rename-Item` cmdlet to change the name of the `a` variable to `processes`.</span></span>

```powershell
Rename-Item -Path Variable:a -NewName processes
```

### <a name="change-the-value-of-a-variable"></a><span data-ttu-id="80021-182">변수 값 변경</span><span class="sxs-lookup"><span data-stu-id="80021-182">Change the value of a variable</span></span>

<span data-ttu-id="80021-183">이 명령은 cmdlet을 사용 하 여 `Set-Item` 변수 값을 `ErrorActionPreference` "Stop"으로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-183">This command uses the `Set-Item` cmdlet to change the value of the `ErrorActionPreference` variable to "Stop".</span></span>

```powershell
Set-Item -Path Variable:ErrorActionPreference -Value Stop
```

## <a name="copy-a-variable"></a><span data-ttu-id="80021-184">변수 복사</span><span class="sxs-lookup"><span data-stu-id="80021-184">Copy a variable</span></span>

<span data-ttu-id="80021-185">이 명령은 cmdlet을 사용 하 여 `Copy-Item` `processes` 변수를로 복사 `old_processes` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-185">This command uses the `Copy-Item` cmdlet to copy the `processes` variable to `old_processes`.</span></span> <span data-ttu-id="80021-186">그러면 변수와 동일한 값을 가진 라는 새 변수가 만들어집니다 `old_processes` `processes` .</span><span class="sxs-lookup"><span data-stu-id="80021-186">This creates a new variable named `old_processes` that has the same value as the `processes` variable.</span></span>

```powershell
Copy-Item -Path Variable:processes -Destination Variable:old_processes
```

## <a name="delete-a-variable"></a><span data-ttu-id="80021-187">변수 삭제</span><span class="sxs-lookup"><span data-stu-id="80021-187">Delete a variable</span></span>

<span data-ttu-id="80021-188">이 명령은 `serv` 현재 세션에서 변수를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-188">This command deletes the `serv` variable from the current session.</span></span> <span data-ttu-id="80021-189">PowerShell 드라이브에서이 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-189">You can use this command in any PowerShell drive.</span></span>

```powershell
Remove-Variable -Path Variable:serv
```

### <a name="delete-variables-using-the--force-parameter"></a><span data-ttu-id="80021-190">-Force 매개 변수를 사용 하 여 변수 삭제</span><span class="sxs-lookup"><span data-stu-id="80021-190">Delete variables using the -Force parameter</span></span>

<span data-ttu-id="80021-191">이 명령은 **Options** 속성 값이 인 변수를 제외 하 고 현재 세션에서 모든 변수를 삭제 `Constant` 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-191">This command deletes all variables from the current session except for the variables whose **Options** property has a value of `Constant`.</span></span> <span data-ttu-id="80021-192">`-Force`매개 변수가 없으면 **Options** 속성의 값이 인 변수는 삭제 되지 않습니다 `ReadOnly` .</span><span class="sxs-lookup"><span data-stu-id="80021-192">Without the `-Force` parameter, the command does not delete variables whose **Options** property has a value of `ReadOnly`.</span></span>

```powershell
Remove-Item Variable:* -Force
```

## <a name="setting-the-value-of-a-variable-to-null"></a><span data-ttu-id="80021-193">변수 값을 NULL로 설정</span><span class="sxs-lookup"><span data-stu-id="80021-193">Setting the value of a variable to NULL</span></span>

<span data-ttu-id="80021-194">이 명령은 cmdlet을 사용 하 여 `Clear-Item` 변수 값을 `processes` NULL로 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-194">This command uses the `Clear-Item` cmdlet to change the value of the `processes` variable to NULL.</span></span>

```powershell
Clear-Item -Path Variable:processes
```

## <a name="using-the-pipeline"></a><span data-ttu-id="80021-195">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="80021-195">Using the pipeline</span></span>

<span data-ttu-id="80021-196">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-196">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="80021-197">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-197">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="80021-198">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="80021-198">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="80021-199">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="80021-199">Getting help</span></span>

<span data-ttu-id="80021-200">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="80021-200">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="80021-201">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="80021-201">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path variable:
```

## <a name="see-also"></a><span data-ttu-id="80021-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="80021-202">See also</span></span>

[<span data-ttu-id="80021-203">about_Variables</span><span class="sxs-lookup"><span data-stu-id="80021-203">about_Variables</span></span>](../About/about_Variables.md)

[<span data-ttu-id="80021-204">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="80021-204">about_Automatic_Variables</span></span>](../About/about_Automatic_Variables.md)

[<span data-ttu-id="80021-205">about_Providers</span><span class="sxs-lookup"><span data-stu-id="80021-205">about_Providers</span></span>](../About/about_Providers.md)
