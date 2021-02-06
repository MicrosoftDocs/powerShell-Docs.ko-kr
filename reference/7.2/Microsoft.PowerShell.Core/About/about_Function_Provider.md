---
description: 함수
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_function_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: 함수 공급자
ms.openlocfilehash: f72ad1e93e65848238afd9feacb38982b4986177
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601462"
---
# <a name="function-provider"></a><span data-ttu-id="60517-103">함수 공급자</span><span class="sxs-lookup"><span data-stu-id="60517-103">Function provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="60517-104">공급자 이름</span><span class="sxs-lookup"><span data-stu-id="60517-104">Provider name</span></span>
<span data-ttu-id="60517-105">함수</span><span class="sxs-lookup"><span data-stu-id="60517-105">Function</span></span>

## <a name="drives"></a><span data-ttu-id="60517-106">드라이브</span><span class="sxs-lookup"><span data-stu-id="60517-106">Drives</span></span>

`Function:`

## <a name="capabilities"></a><span data-ttu-id="60517-107">기능</span><span class="sxs-lookup"><span data-stu-id="60517-107">Capabilities</span></span>

<span data-ttu-id="60517-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="60517-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="60517-109">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="60517-109">Short description</span></span>

<span data-ttu-id="60517-110">PowerShell에 정의 된 함수에 대 한 액세스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-110">Provides access to the functions defined in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="60517-111">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="60517-111">Detailed description</span></span>

<span data-ttu-id="60517-112">PowerShell **함수** 공급자를 통해 powershell에서 함수 및 필터를 가져오고 추가, 변경 및 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-112">The PowerShell **Function** provider lets you get, add, change, clear, and delete the functions and filters in PowerShell.</span></span>

<span data-ttu-id="60517-113">함수는 작업을 수행하는 명명된 코드 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-113">A function is a named block of code that performs an action.</span></span> <span data-ttu-id="60517-114">함수 이름을 입력하면 함수 내의 코드가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="60517-114">When you type the function name, the code in the function runs.</span></span> <span data-ttu-id="60517-115">필터는 작업 조건을 설정하는 명명된 코드 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-115">A filter is a named block of code that establishes conditions for an action.</span></span> <span data-ttu-id="60517-116">명령에서와 같이 조건 대신 필터 이름을 입력할 수 있습니다 `Where-Object` .</span><span class="sxs-lookup"><span data-stu-id="60517-116">You can type the name of the filter in place of the condition, such as in a `Where-Object` command.</span></span>

<span data-ttu-id="60517-117">**함수** 드라이브는 함수 및 필터 개체만 포함 하는 플랫 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-117">The **Function** drive is a flat namespace that contains only the function and filter objects.</span></span> <span data-ttu-id="60517-118">함수와 필터에는 둘 다 하위 항목이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-118">Neither functions nor filters have child items.</span></span>

<span data-ttu-id="60517-119">**함수** 공급자는이 문서에서 설명 하는 다음과 같은 cmdlet을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-119">The **Function** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="60517-120">Get-Location</span><span class="sxs-lookup"><span data-stu-id="60517-120">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="60517-121">Set-Location</span><span class="sxs-lookup"><span data-stu-id="60517-121">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="60517-122">Get-Item</span><span class="sxs-lookup"><span data-stu-id="60517-122">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="60517-123">New-Item</span><span class="sxs-lookup"><span data-stu-id="60517-123">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="60517-124">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="60517-124">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="60517-125">Clear-Item</span><span class="sxs-lookup"><span data-stu-id="60517-125">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="60517-126">이 공급자가 노출 하는 형식</span><span class="sxs-lookup"><span data-stu-id="60517-126">Types exposed by this provider</span></span>

<span data-ttu-id="60517-127">각 함수는 System.web. c o [.](/dotnet/api/system.management.automation.functioninfo) c o. c o. c o.</span><span class="sxs-lookup"><span data-stu-id="60517-127">Each function is an instance of the [System.Management.Automation.FunctionInfo](/dotnet/api/system.management.automation.functioninfo) class.</span></span> <span data-ttu-id="60517-128">각 필터는 [system.web. FilterInfo](/dotnet/api/system.management.automation.filterinfo) 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-128">Each filter is an instance of the [System.Management.Automation.FilterInfo](/dotnet/api/system.management.automation.filterinfo) class.</span></span>

## <a name="navigating-the-function-drive"></a><span data-ttu-id="60517-129">함수 드라이브 탐색</span><span class="sxs-lookup"><span data-stu-id="60517-129">Navigating the Function drive</span></span>

<span data-ttu-id="60517-130">**함수** 공급자는 드라이브에 해당 데이터 저장소를 노출 합니다 `Function:` .</span><span class="sxs-lookup"><span data-stu-id="60517-130">The **Function** provider exposes its data store in the `Function:` drive.</span></span> <span data-ttu-id="60517-131">함수를 사용 하 여 작업 하려면 위치를 드라이브 ()로 변경할 수 있습니다 `Function:` `Set-Location Function:` .</span><span class="sxs-lookup"><span data-stu-id="60517-131">To work with functions, you can change your location to the `Function:` drive (`Set-Location Function:`).</span></span> <span data-ttu-id="60517-132">또는 다른 PowerShell 드라이브에서 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-132">Or, you can work from another PowerShell drive.</span></span> <span data-ttu-id="60517-133">다른 위치에서 함수를 참조 하려면 경로에 드라이브 이름 ()을 사용 `Function:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-133">To reference a function from another location, use the drive name (`Function:`) in the path.</span></span>

```powershell
Set-Location Function:
```

<span data-ttu-id="60517-134">파일 시스템 드라이브로 돌아가려면 드라이브 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-134">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="60517-135">예를 들어 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-135">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="60517-136">다른 PowerShell 드라이브에서 **함수** 공급자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-136">You can also work with the **Function** provider from any other PowerShell drive.</span></span> <span data-ttu-id="60517-137">다른 위치에서 함수를 참조 하려면 경로에 드라이브 이름을 사용 `Function:` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-137">To reference an function from another location, use the drive name `Function:` in the path.</span></span>

> [!NOTE]
> <span data-ttu-id="60517-138">PowerShell은 별칭을 사용 하 여 공급자 경로 작업을 수행할 수 있는 친숙 한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-138">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="60517-139">`dir`및 등의 명령은 `ls` 이제 [Get childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem)에 대 한 별칭입니다 `cd` .는 [집합 위치](xref:Microsoft.PowerShell.Management.Set-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-139">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span> <span data-ttu-id="60517-140">및 `pwd` 은 [(는) 위치](xref:Microsoft.PowerShell.Management.Get-Location)에 대 한 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-140">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="getting-functions"></a><span data-ttu-id="60517-141">함수 가져오기</span><span class="sxs-lookup"><span data-stu-id="60517-141">Getting functions</span></span>

<span data-ttu-id="60517-142">이 명령은 현재 세션의 모든 함수 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="60517-142">This command gets the list of all the functions in the current session.</span></span> <span data-ttu-id="60517-143">모든 PowerShell 드라이브에서이 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-143">You can use this command from any PowerShell drive.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="60517-144">함수 공급자에는 컨테이너가 없으므로에서 사용 하는 경우 위의 명령이 동일한 결과를 가집니다 `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="60517-144">The Function provider has no containers, so the above command has the same effect when used with `Get-ChildItem`.</span></span>

```powershell
Get-ChildItem -Path Function:
```

<span data-ttu-id="60517-145">아래와 같이 **정의** 속성에 액세스 하 여 함수의 정의를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-145">You can retrieve a function's definition by accessing the **Definition** property, as shown below.</span></span>

```powershell
(Get-Item -Path function:more).Definition
```

<span data-ttu-id="60517-146">달러 기호 ()로 시작 하는 공급자 경로를 사용 하 여 함수의 정의를 검색할 수도 있습니다 `$` .</span><span class="sxs-lookup"><span data-stu-id="60517-146">You can also retrieve a function's definition using its provider path prefixed by the dollar sign (`$`).</span></span>

```powershell
$function:more
```

### <a name="getting-selected-functions"></a><span data-ttu-id="60517-147">선택한 함수 가져오기</span><span class="sxs-lookup"><span data-stu-id="60517-147">Getting selected functions</span></span>

<span data-ttu-id="60517-148">이 명령은 `man` 드라이브에서 함수를 가져옵니다 `Function:` .</span><span class="sxs-lookup"><span data-stu-id="60517-148">This command gets the `man` function from the `Function:` drive.</span></span> <span data-ttu-id="60517-149">Cmdlet을 사용 하 여 `Get-Item` 함수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="60517-149">It uses the `Get-Item` cmdlet to get the function.</span></span> <span data-ttu-id="60517-150">파이프라인 연산자 ( `|` )는 결과를로 보냅니다 `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="60517-150">The pipeline operator (`|`) sends the result to `Format-Table`.</span></span> <span data-ttu-id="60517-151">`-Wrap`매개 변수는 줄에 맞지 않는 텍스트를 다음 줄로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="60517-151">The `-Wrap` parameter directs text that does not fit on the line onto the next line.</span></span> <span data-ttu-id="60517-152">`-Autosize`매개 변수는 텍스트에 맞게 테이블 열의 크기를 조정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-152">The `-Autosize` parameter resizes the table columns to accommodate the text.</span></span>

```powershell
Get-Item -Path man | Format-Table -Wrap -Autosize
```

### <a name="working-with-function-provider-paths"></a><span data-ttu-id="60517-153">함수 공급자 경로 작업</span><span class="sxs-lookup"><span data-stu-id="60517-153">Working with Function provider paths</span></span>

<span data-ttu-id="60517-154">이러한 명령은 모두 이라는 함수를 가져옵니다 `c:` .</span><span class="sxs-lookup"><span data-stu-id="60517-154">These commands both get the function named `c:`.</span></span> <span data-ttu-id="60517-155">첫 번째 명령은 모든 드라이브에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-155">The first command can be used in any drive.</span></span> <span data-ttu-id="60517-156">두 번째 명령은 드라이브에서 사용 됩니다 `Function:` .</span><span class="sxs-lookup"><span data-stu-id="60517-156">The second command is used in the `Function:` drive.</span></span> <span data-ttu-id="60517-157">이름이 드라이브의 구문인 콜론으로 끝나기 때문에 드라이브 이름으로 경로를 한정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-157">Because the name ends in a colon, which is the syntax for a drive, you must qualify the path with the drive name.</span></span> <span data-ttu-id="60517-158">드라이브 내에서 `Function:` 두 형식 중 하나를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-158">Within the `Function:` drive, you can use either format.</span></span> <span data-ttu-id="60517-159">두 번째 명령에서 점 ()은 `.` 현재 위치를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="60517-159">In the second command, the dot (`.`) represents the current location.</span></span>

```
PS C:\> Get-Item -Path Function:c:
PS Function:\> Get-Item -Path .\c:
```

## <a name="creating-a-function"></a><span data-ttu-id="60517-160">함수 만들기</span><span class="sxs-lookup"><span data-stu-id="60517-160">Creating a function</span></span>

<span data-ttu-id="60517-161">이 명령은 cmdlet을 사용 하 여 `New-Item` 라는 함수를 만듭니다 `Win32:` .</span><span class="sxs-lookup"><span data-stu-id="60517-161">This command uses the `New-Item` cmdlet to create a function called `Win32:`.</span></span>
<span data-ttu-id="60517-162">괄호로 묶은 식은 함수 이름으로 표시되는 스크립트 블록입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-162">The expression in braces is the script block that is represented by the function name.</span></span>

```powershell
New-Item -Path Function:Win32: -Value {Set-Location C:\Windows\System32}
```

<span data-ttu-id="60517-163">PowerShell 명령줄에 함수를 입력 하 여 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-163">You can also create a function by typing it at the PowerShell command line.</span></span> <span data-ttu-id="60517-164">예: tpe `Function:Win32: {Set-Location C:\Windows\System32}` .</span><span class="sxs-lookup"><span data-stu-id="60517-164">For example, tpe `Function:Win32: {Set-Location C:\Windows\System32}`.</span></span> <span data-ttu-id="60517-165">드라이브에 있는 경우 `Function:` 드라이브 이름을 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-165">If you are in the `Function:` drive, you can omit the drive name.</span></span>

## <a name="deleting-a-function"></a><span data-ttu-id="60517-166">함수 삭제</span><span class="sxs-lookup"><span data-stu-id="60517-166">Deleting a function</span></span>

<span data-ttu-id="60517-167">이 명령은 `more:` 현재 세션에서 함수를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-167">This command deletes the `more:` function from the current session.</span></span>

```powershell
Remove-Item Function:more:
```

## <a name="changing-a-function"></a><span data-ttu-id="60517-168">함수 변경</span><span class="sxs-lookup"><span data-stu-id="60517-168">Changing a function</span></span>

<span data-ttu-id="60517-169">이 명령은 cmdlet을 사용 하 여 `Set-Item` `prompt` 경로 앞에 시간을 표시 하도록 함수를 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-169">This command uses the `Set-Item` cmdlet to change the `prompt` function so that it displays the time before the path.</span></span>

```powershell
Set-Item -Path Function:prompt -Value {
  'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '
  }
```

### <a name="rename-a-function"></a><span data-ttu-id="60517-170">함수 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="60517-170">Rename a function</span></span>

<span data-ttu-id="60517-171">이 명령은 cmdlet을 사용 하 여 `Rename-Item` 함수의 이름을로 변경 `help` `gh` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-171">This command uses the `Rename-Item` cmdlet to change the name of the `help` function to `gh`.</span></span>

```powershell
Rename-Item -Path Function:help -NewName gh
```

## <a name="copying-a-function"></a><span data-ttu-id="60517-172">함수 복사</span><span class="sxs-lookup"><span data-stu-id="60517-172">Copying a function</span></span>

<span data-ttu-id="60517-173">이 명령은 `prompt` 에 함수를 복사 하 여 `oldPrompt` 프롬프트 함수와 연결 된 스크립트 블록의 새 이름을 효과적으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60517-173">This command copies the `prompt` function to `oldPrompt`, effectively creating a new name for the script block that is associated with the prompt function.</span></span>
<span data-ttu-id="60517-174">프롬프트 함수를 변경하려는 경우 이 명령을 사용하여 원래 프롬프트 함수를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-174">You can use this to save the original prompt function if you plan to change it.</span></span>
<span data-ttu-id="60517-175">새 함수의 **Options** 속성 값은 `None` 입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-175">The **Options** property of the new function has a value of `None`.</span></span> <span data-ttu-id="60517-176">**Options** 속성의 값을 변경 하려면를 사용 `Set-Item` 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-176">To change the value of the **Options** property, use `Set-Item`.</span></span>

```powershell
Copy-Item -Path Function:prompt -Destination Function:oldPrompt
```

## <a name="dynamic-parameters"></a><span data-ttu-id="60517-177">동적 매개 변수</span><span class="sxs-lookup"><span data-stu-id="60517-177">Dynamic parameters</span></span>

<span data-ttu-id="60517-178">동적 매개 변수는 PowerShell 공급자가 추가 하는 cmdlet 매개 변수 이며, 공급자 사용 드라이브에서 cmdlet을 사용 하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-178">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="options-systemmanagementautomationscopeditemoptions"></a><span data-ttu-id="60517-179">옵션 < [ScopedItemOptions] ></span><span class="sxs-lookup"><span data-stu-id="60517-179">Options <[System.Management.Automation.ScopedItemOptions]></span></span>

<span data-ttu-id="60517-180">함수의 **Options** 속성 값을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-180">Determines the value of the **Options** property of a function.</span></span>

- <span data-ttu-id="60517-181">`None`: 옵션이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-181">`None`: No options.</span></span> <span data-ttu-id="60517-182">기본값은 `None`입니다.</span><span class="sxs-lookup"><span data-stu-id="60517-182">`None` is the default.</span></span>
- <span data-ttu-id="60517-183">`Constant`: 함수는 삭제할 수 없으며 해당 속성을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-183">`Constant`: The function cannot be deleted, and its properties cannot be changed.</span></span> <span data-ttu-id="60517-184">`Constant` 는 함수를 만들 때만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-184">`Constant` is available only when you are creating a function.</span></span>
  <span data-ttu-id="60517-185">기존 함수의 옵션을로 변경할 수는 없습니다 `Constant` .</span><span class="sxs-lookup"><span data-stu-id="60517-185">You cannot change the option of an existing function to `Constant`.</span></span>
- <span data-ttu-id="60517-186">`Private`: 함수는 현재 범위 에서만 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-186">`Private`: The function is visible only in the current scope</span></span>
- <span data-ttu-id="60517-187">(자식 범위에 없음).</span><span class="sxs-lookup"><span data-stu-id="60517-187">(not in child scopes).</span></span>
- <span data-ttu-id="60517-188">`ReadOnly`: 매개 변수를 사용 하는 경우를 제외 하 고 함수의 속성을 변경할 수 없습니다 `-Force` .</span><span class="sxs-lookup"><span data-stu-id="60517-188">`ReadOnly`: The properties of the function cannot be changed except by using the `-Force` parameter.</span></span> <span data-ttu-id="60517-189">를 사용 하 여 함수를 삭제할 수 있습니다 `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="60517-189">You can use `Remove-Item` to delete the function.</span></span>
- <span data-ttu-id="60517-190">`AllScope`: 함수는 생성 된 모든 새 범위로 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60517-190">`AllScope`: The function is copied to any new scopes that are created.</span></span>

### <a name="cmdlets-supported"></a><span data-ttu-id="60517-191">Cmdlet 지원</span><span class="sxs-lookup"><span data-stu-id="60517-191">Cmdlets supported</span></span>

- [<span data-ttu-id="60517-192">New-Item</span><span class="sxs-lookup"><span data-stu-id="60517-192">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

- [<span data-ttu-id="60517-193">Set-Item</span><span class="sxs-lookup"><span data-stu-id="60517-193">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)

## <a name="using-the-pipeline"></a><span data-ttu-id="60517-194">파이프라인 사용</span><span class="sxs-lookup"><span data-stu-id="60517-194">Using the pipeline</span></span>

<span data-ttu-id="60517-195">공급자 cmdlet은 파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-195">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="60517-196">파이프라인을 사용 하 여 cmdlet 간에 공급자 데이터를 전송 하 여 작업을 간소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-196">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="60517-197">공급자 cmdlet에서 파이프라인을 사용 하는 방법에 대 한 자세한 내용은이 문서 전체에서 제공 되는 cmdlet 참조를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60517-197">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="60517-198">도움말 보기</span><span class="sxs-lookup"><span data-stu-id="60517-198">Getting help</span></span>

<span data-ttu-id="60517-199">Windows PowerShell 3.0부터는 이러한 cmdlet이 파일 시스템 드라이브에서 동작하는 방식을 설명하는 공급자 cmdlet에 대한 사용자 지정된 도움말 항목을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60517-199">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="60517-200">파일 시스템 드라이브에 맞게 사용자 지정 된 도움말 항목을 보려면 파일 시스템 드라이브에서 [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 명령을 실행 하거나 `-Path` [get-help](xref:Microsoft.PowerShell.Core.Get-Help) 의 매개 변수를 사용 하 여 파일 시스템 드라이브를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60517-200">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path function:
```

## <a name="see-also"></a><span data-ttu-id="60517-201">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60517-201">See also</span></span>

[<span data-ttu-id="60517-202">about_Functions</span><span class="sxs-lookup"><span data-stu-id="60517-202">about_Functions</span></span>](../About/about_Functions.md)

[<span data-ttu-id="60517-203">about_Providers</span><span class="sxs-lookup"><span data-stu-id="60517-203">about_Providers</span></span>](../About/about_Providers.md)

