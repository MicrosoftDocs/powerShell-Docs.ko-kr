---
title: Functions
description: PowerShell 함수를 사용하면 스크립트에서 다시 사용할 수 있는 도구를 만들 수 있습니다.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: ca48f3020fa306f8a24328bd18648d5954c48a94
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438204"
---
# <a name="chapter-9---functions"></a><span data-ttu-id="b8a32-103">9장 - 함수</span><span class="sxs-lookup"><span data-stu-id="b8a32-103">Chapter 9 - Functions</span></span>

<span data-ttu-id="b8a32-104">PowerShell 원라이너 또는 스크립트를 작성 중이고 다른 시나리오를 위해 수정하는 경우가 자주 발생하면 다시 사용할 수 있는 함수로 전환하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-104">If you're writing PowerShell one-liners or scripts and find yourself often having to modify them for different scenarios, there's a good chance that it's a good candidate to be turned into a function that can be reused.</span></span>

<span data-ttu-id="b8a32-105">보다 도구 지향적이기 때문에 가능한 한 함수를 작성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-105">Whenever possible, I prefer to write functions because they are more tool oriented.</span></span> <span data-ttu-id="b8a32-106">스크립트 모듈에 함수를 추가하고, 해당 모듈을 `$env:PSModulePath`에 배치하고, 물리적으로 저장 위치를 찾을 필요 없이 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-106">I can put the functions in a script module, put that module in the `$env:PSModulePath`, and call the functions without needing to physically locate where they're saved.</span></span> <span data-ttu-id="b8a32-107">PowerShellGet 모듈을 사용하면 NuGet 리포지토리에서 이러한 모듈을 쉽게 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-107">Using the PowerShellGet module, it's easy to share those modules in a NuGet repository.</span></span> <span data-ttu-id="b8a32-108">PowerShellGet은 PowerShell 버전 5.0 이상에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-108">PowerShellGet ships with PowerShell version 5.0 and higher.</span></span> <span data-ttu-id="b8a32-109">PowerShell 버전 3.0 이상에서는 별도의 다운로드로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-109">It is available as a separate download for PowerShell version 3.0 and higher.</span></span>

<span data-ttu-id="b8a32-110">문제를 너무 복잡하게 만들지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-110">Don't over complicate things.</span></span> <span data-ttu-id="b8a32-111">작업을 수행하기 위한 가장 간단한 방법을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-111">Keep it simple and use the most straight forward way to accomplish a task.</span></span> <span data-ttu-id="b8a32-112">다시 사용하는 모든 코드에서는 별칭 및 위치 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-112">Avoid aliases and positional parameters in any code that you reuse.</span></span> <span data-ttu-id="b8a32-113">가독성을 위해 코드를 서식 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-113">Format your code for readability.</span></span> <span data-ttu-id="b8a32-114">값을 하드 코딩하지 말고 매개 변수 및 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-114">Don't hardcode values; use parameters and variables.</span></span> <span data-ttu-id="b8a32-115">불필요한 코드는 아무런 피해가 없더라도 작성하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-115">Don't write unnecessary code even if it doesn't hurt anything.</span></span> <span data-ttu-id="b8a32-116">불필요한 복잡성이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-116">It adds unnecessary complexity.</span></span> <span data-ttu-id="b8a32-117">PowerShell 코드를 작성할 때는 세부 사항에 대한 주의가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-117">Attention to detail goes a long way when writing any PowerShell code.</span></span>

## <a name="naming"></a><span data-ttu-id="b8a32-118">이름 지정</span><span class="sxs-lookup"><span data-stu-id="b8a32-118">Naming</span></span>

<span data-ttu-id="b8a32-119">PowerShell에서 함수 이름을 지정할 때 승인된 동사와 단수 명사를 포함하는 [파스칼식 대/소문자][] 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-119">When naming your functions in PowerShell, use a [Pascal case][] name with an approved verb and a singular noun.</span></span> <span data-ttu-id="b8a32-120">또한 명사에 접두사를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-120">I also recommend prefixing the noun.</span></span> <span data-ttu-id="b8a32-121">예: `<ApprovedVerb>-<Prefix><SingularNoun>`</span><span class="sxs-lookup"><span data-stu-id="b8a32-121">For example: `<ApprovedVerb>-<Prefix><SingularNoun>`.</span></span>

<span data-ttu-id="b8a32-122">PowerShell에는 `Get-Verb`를 실행하여 얻을 수 있는 승인된 동사의 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-122">In PowerShell, there's a specific list of approved verbs that can be obtained by running `Get-Verb`.</span></span>

```powershell
Get-Verb | Sort-Object -Property Verb
```

```Output
Verb        Group
----        -----
Add         Common
Approve     Lifecycle
Assert      Lifecycle
Backup      Data
Block       Security
Checkpoint  Data
Clear       Common
Close       Common
Compare     Data
Complete    Lifecycle
Compress    Data
Confirm     Lifecycle
Connect     Communications
Convert     Data
ConvertFrom Data
ConvertTo   Data
Copy        Common
Debug       Diagnostic
Deny        Lifecycle
Disable     Lifecycle
Disconnect  Communications
Dismount    Data
Edit        Data
Enable      Lifecycle
Enter       Common
Exit        Common
Expand      Data
Export      Data
Find        Common
Format      Common
Get         Common
Grant       Security
Group       Data
Hide        Common
Import      Data
Initialize  Data
Install     Lifecycle
Invoke      Lifecycle
Join        Common
Limit       Data
Lock        Common
Measure     Diagnostic
Merge       Data
Mount       Data
Move        Common
New         Common
Open        Common
Optimize    Common
Out         Data
Ping        Diagnostic
Pop         Common
Protect     Security
Publish     Data
Push        Common
Read        Communications
Receive     Communications
Redo        Common
Register    Lifecycle
Remove      Common
Rename      Common
Repair      Diagnostic
Request     Lifecycle
Reset       Common
Resize      Common
Resolve     Diagnostic
Restart     Lifecycle
Restore     Data
Resume      Lifecycle
Revoke      Security
Save        Data
Search      Common
Select      Common
Send        Communications
Set         Common
Show        Common
Skip        Common
Split       Common
Start       Lifecycle
Step        Common
Stop        Lifecycle
Submit      Lifecycle
Suspend     Lifecycle
Switch      Common
Sync        Data
Test        Diagnostic
Trace       Diagnostic
Unblock     Security
Undo        Common
Uninstall   Lifecycle
Unlock      Common
Unprotect   Security
Unpublish   Data
Unregister  Lifecycle
Update      Data
Use         Other
Wait        Lifecycle
Watch       Common
Write       Communications
```

<span data-ttu-id="b8a32-123">이전 예제에서는 **Verb** 열을 기준으로 결과를 정렬했습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-123">In the previous example, I've sorted the results by the **Verb** column.</span></span> <span data-ttu-id="b8a32-124">**Group** 열은 이러한 동사를 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-124">The **Group** column gives you an idea of how these verbs are used.</span></span> <span data-ttu-id="b8a32-125">모듈에 함수를 추가할 때 PowerShell에서 승인된 동사를 선택하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-125">It's important to choose an approved verb in PowerShell when functions are added to a module.</span></span> <span data-ttu-id="b8a32-126">승인되지 않은 동사를 선택하면 로드 시 모듈에서 경고 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-126">The module generates a warning message at load time if you choose an unapproved verb.</span></span> <span data-ttu-id="b8a32-127">이러한 경고 메시지는 비전문가가 만든 함수처럼 보이게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-127">That warning message makes your functions look unprofessional.</span></span> <span data-ttu-id="b8a32-128">또한 승인되지 않은 동사는 함수 검색 가능성을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-128">Unapproved verbs also limit the discoverability of your functions.</span></span>

## <a name="a-simple-function"></a><span data-ttu-id="b8a32-129">간단한 함수</span><span class="sxs-lookup"><span data-stu-id="b8a32-129">A simple function</span></span>

<span data-ttu-id="b8a32-130">PowerShell의 함수는 함수 키워드와 함수 이름, 여는 중괄호 및 닫는 중괄호를 사용하여 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-130">A function in PowerShell is declared with the function keyword followed by the function name and then an open and closing curly brace.</span></span> <span data-ttu-id="b8a32-131">함수가 실행하는 코드는 이 중괄호 안에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-131">The code that the function will execute is contained within those curly braces.</span></span>

```powershell
function Get-Version {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="b8a32-132">표시된 함수는 PowerShell의 버전을 반환하는 간단한 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-132">The function shown is a simple example that returns the version of PowerShell.</span></span>

```powershell
Get-Version
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="b8a32-133">`Get-Version`과 같은 이름의 함수와 PowerShell 기본 명령 또는 다른 사용자가 작성할 수 있는 명령은 이름 충돌이 생길 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-133">There's a good chance of name conflict with functions named something like `Get-Version` and default commands in PowerShell or commands that others may write.</span></span> <span data-ttu-id="b8a32-134">함수의 명사 부분에 접두사를 지정하도록 권장하는 이유는 이름 충돌을 방지하는 데 도움이 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-134">This is why I recommend prefixing the noun portion of your functions to help prevent naming conflicts.</span></span> <span data-ttu-id="b8a32-135">다음 예제에서는 접두사 "PS"를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-135">In the following example, I'll use the prefix "PS".</span></span>

```powershell
function Get-PSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="b8a32-136">이름을 제외하면 이 함수는 이전 함수와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-136">Other than the name, this function is identical to the previous one.</span></span>

```powershell
Get-PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="b8a32-137">PS와 같은 명사를 접두사로 사용하는 경우에도 여전히 이름 충돌이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-137">Even when prefixing the noun with something like PS, there's still a good chance of having a name conflict.</span></span> <span data-ttu-id="b8a32-138">필자는 일반적으로 함수 명사에 이니셜을 접두사로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-138">I typically prefix my function nouns with my initials.</span></span> <span data-ttu-id="b8a32-139">표준을 개발하고 일관되게 적용하세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-139">Develop a standard and stick to it.</span></span>

```powershell
function Get-MrPSVersion {
    $PSVersionTable.PSVersion
}
```

<span data-ttu-id="b8a32-140">다음 함수는 다른 PowerShell 명령과의 이름 충돌을 방지하기 위해 보다 알기 쉬운 이름을 사용한다는 점을 제외하면 이전의 두 함수와 다르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-140">This function is no different than the previous two other than using a more sensible name to try to prevent naming conflicts with other PowerShell commands.</span></span>

```powershell
Get-MrPSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  693
```

<span data-ttu-id="b8a32-141">함수가 메모리에 로드되면 **Function** PSDrive에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-141">Once loaded into memory, you can see functions on the **Function** PSDrive.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Function        Get-Version
Function        Get-PSVersion
Function        Get-MrPSVersion
```

<span data-ttu-id="b8a32-142">현재 세션에서 이러한 함수를 제거하려면 **Function** PSDrive에서 제거하거나 PowerShell을 닫았다가 다시 열어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-142">If you want to remove these functions from your current session, you'll have to remove them from the **Function** PSDrive or close and reopen PowerShell.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version | Remove-Item
```

<span data-ttu-id="b8a32-143">함수가 실제로 제거되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-143">Verify that the functions were indeed removed.</span></span>

```powershell
Get-ChildItem -Path Function:\Get-*Version
```

<span data-ttu-id="b8a32-144">함수가 모듈의 일부로 로드된 경우 모듈을 언로드하고 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-144">If the functions were loaded as part of a module, the module can be unloaded to remove them.</span></span>

```powershell
Remove-Module -Name <ModuleName>
```

<span data-ttu-id="b8a32-145">`Remove-Module` cmdlet은 현재 PowerShell 세션의 메모리에서 모듈을 제거하고 시스템 또는 디스크에서는 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-145">The `Remove-Module` cmdlet removes modules from memory in your current PowerShell session, it doesn't remove them from your system or from disk.</span></span>

## <a name="parameters"></a><span data-ttu-id="b8a32-146">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b8a32-146">Parameters</span></span>

<span data-ttu-id="b8a32-147">값을 정적으로 할당하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-147">Don't statically assign values!</span></span> <span data-ttu-id="b8a32-148">매개 변수와 변수를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-148">Use parameters and variables.</span></span> <span data-ttu-id="b8a32-149">매개 변수의 이름을 지정할 때는 가능한 한 매개 변수 이름에 기본 cmdlet과 동일한 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-149">When it comes to naming your parameters, use the same name as the default cmdlets for your parameter names whenever possible.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-150">매개 변수 이름에 **Computer**, **ServerName** 또는 **Host**가 아니라 **ComputerName**을 사용한 이유가 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="b8a32-150">Why did I use **ComputerName** and not **Computer**, **ServerName**, or **Host** for my parameter name?</span></span> <span data-ttu-id="b8a32-151">기본 cmdlet과 같이 함수를 표준화하려고 했기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-151">It's because I wanted my function standardized like the default cmdlets.</span></span>

<span data-ttu-id="b8a32-152">시스템의 모든 명령을 쿼리하고 특정 매개 변수 이름이 있는 값을 반환하는 함수를 만들겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-152">I'll create a function to query all of the commands on a system and return the number of them that have specific parameter names.</span></span>

```powershell
function Get-MrParameterCount {
    param (
        [string[]]$ParameterName
    )

    foreach ($Parameter in $ParameterName) {
        $Results = Get-Command -ParameterName $Parameter -ErrorAction SilentlyContinue

        [pscustomobject]@{
            ParameterName = $Parameter
            NumberOfCmdlets = $Results.Count
        }
    }
}
```

<span data-ttu-id="b8a32-153">아래에 표시된 결과에서 볼 수 있듯이 **ComputerName** 매개 변수가 있는 명령이 39개 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-153">As you can see in the results shown below, 39 commands that have a **ComputerName** parameter.</span></span> <span data-ttu-id="b8a32-154">**Computer**, **ServerName**, **Host** 또는 **Machine** 같은 매개 변수를 포함하는 cmdlet은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-154">There aren't any cmdlets that have parameters such as **Computer**, **ServerName**, **Host**, or **Machine**.</span></span>

```powershell
Get-MrParameterCount -ParameterName ComputerName, Computer, ServerName, Host, Machine
```

```Output
ParameterName NumberOfCmdlets
------------- ---------------
ComputerName               39
Computer                    0
ServerName                  0
Host                        0
Machine                     0
```

<span data-ttu-id="b8a32-155">또한 매개 변수 이름에 기본 cmdlet과 동일한 대/소문자를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-155">I also recommend using the same case for your parameter names as the default cmdlets.</span></span> <span data-ttu-id="b8a32-156">`computername`이 아니라 `ComputerName`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-156">Use `ComputerName`, not `computername`.</span></span> <span data-ttu-id="b8a32-157">이렇게 하면 함수는 기본 cmdlet과 비슷하게 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-157">This makes your functions look and feel like the default cmdlets.</span></span> <span data-ttu-id="b8a32-158">이미 PowerShell에 익숙한 사람이라면 매우 편안하게 느낄 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-158">People who are already familiar with PowerShell will feel right at home.</span></span>

## <a name="advanced-functions"></a><span data-ttu-id="b8a32-159">고급 함수</span><span class="sxs-lookup"><span data-stu-id="b8a32-159">Advanced Functions</span></span>

<span data-ttu-id="b8a32-160">PowerShell의 함수를 고급 함수로 설정하는 것은 매우 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-160">Turning a function in PowerShell into an advanced function is really simple.</span></span> <span data-ttu-id="b8a32-161">함수와 고급 함수 간의 차이점 중 하나는 고급 함수는 함수에 자동으로 추가되는 여러 공통 매개 변수를 포함한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-161">One of the differences between a function and an advanced function is that advanced functions have a number of common parameters that are added to the function automatically.</span></span> <span data-ttu-id="b8a32-162">이러한 공통 매개 변수에는 **Verbose** 및 **Debug** 같은 매개 변수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-162">These common parameters include parameters such as **Verbose** and **Debug**.</span></span>

<span data-ttu-id="b8a32-163">이전 섹션에서 사용된 `Test-MrParameter` 함수로 시작하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-163">I'll start out with the `Test-MrParameter` function that was used in the previous section.</span></span>

```powershell
function Test-MrParameter {

    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-164">`Test-MrParameter` 함수에는 공통 매개 변수가 없다는 것을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-164">What I want you to notice is that the `Test-MrParameter` function doesn't have any common parameters.</span></span> <span data-ttu-id="b8a32-165">몇 가지 방법으로 공통 매개 변수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-165">There are a couple of different ways to see the common parameters.</span></span> <span data-ttu-id="b8a32-166">한 방법은 `Get-Command`를 사용하여 구문을 보는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-166">One is by viewing the syntax using `Get-Command`.</span></span>

```powershell
Get-Command -Name Test-MrParameter -Syntax
```

```Output
Test-MrParameter [[-ComputerName] <Object>]
```

<span data-ttu-id="b8a32-167">다른 방법은 `Get-Command`를 사용하여 매개 변수로 드릴다운하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-167">Another is to drill down into the parameters with `Get-Command`.</span></span>

```powershell
(Get-Command -Name Test-MrParameter).Parameters.Keys
```

```Output
ComputerName
```

<span data-ttu-id="b8a32-168">함수를 고급 함수로 전환하려면 `CmdletBinding`을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-168">Add `CmdletBinding` to turn the function into an advanced function.</span></span>

```powershell
function Test-MrCmdletBinding {

    [CmdletBinding()] #<<-- This turns a regular function into an advanced function
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-169">`CmdletBinding`을 추가하면 공통 매개 변수가 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-169">Adding `CmdletBinding` adds the common parameters automatically.</span></span> <span data-ttu-id="b8a32-170">`CmdletBinding`에는 `param` 블록이 필요하지만 `param` 블록은 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-170">`CmdletBinding` requires a `param` block, but the `param` block can be empty.</span></span>

```powershell
Get-Command -Name Test-MrCmdletBinding -Syntax
```

```Output
Test-MrCmdletBinding [[-ComputerName] <Object>] [<CommonParameters>]
```

<span data-ttu-id="b8a32-171">`Get-Command` 매개 변수로 드릴다운하면 공통 매개 변수 이름을 포함하여 실제 매개 변수 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-171">Drilling down into the parameters with `Get-Command` shows the actual parameter names including the common ones.</span></span>

```powershell
(Get-Command -Name Test-MrCmdletBinding).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
```

## <a name="supportsshouldprocess"></a><span data-ttu-id="b8a32-172">SupportsShouldProcess</span><span class="sxs-lookup"><span data-stu-id="b8a32-172">SupportsShouldProcess</span></span>

<span data-ttu-id="b8a32-173">`SupportsShouldProcess`는 **WhatIf** 및 **Confirm** 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-173">`SupportsShouldProcess` adds **WhatIf** and **Confirm** parameters.</span></span> <span data-ttu-id="b8a32-174">이러한 매개 변수는 변경하는 명령에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-174">These are only needed for commands that make changes.</span></span>

```powershell
function Test-MrSupportsShouldProcess {

    [CmdletBinding(SupportsShouldProcess)]
    param (
        $ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-175">이제 **WhatIf** 및 **Confirm** 매개 변수가 있는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-175">Notice that there are now **WhatIf** and **Confirm** parameters.</span></span>

```powershell
Get-Command -Name Test-MrSupportsShouldProcess -Syntax
```

```Output
Test-MrSupportsShouldProcess [[-ComputerName] <Object>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="b8a32-176">다시 한 번 `Get-Command`를 사용하여 WhatIf 및 Confirm과 함께 공통 매개 변수 이름을 포함하는 실제 매개 변수 이름의 목록을 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-176">Once again, you can also use `Get-Command` to return a list of the actual parameter names including the common ones along with WhatIf and Confirm.</span></span>

```powershell
(Get-Command -Name Test-MrSupportsShouldProcess).Parameters.Keys
```

```Output
ComputerName
Verbose
Debug
ErrorAction
WarningAction
InformationAction
ErrorVariable
WarningVariable
InformationVariable
OutVariable
OutBuffer
PipelineVariable
WhatIf
Confirm
```

## <a name="parameter-validation"></a><span data-ttu-id="b8a32-177">매개 변수 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="b8a32-177">Parameter Validation</span></span>

<span data-ttu-id="b8a32-178">조기에 입력의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-178">Validate input early on.</span></span> <span data-ttu-id="b8a32-179">유효한 입력 없이 실행될 수 없는 경우 경로에서 코드가 계속되도록 허용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-179">Why allow your code to continue on a path when it's not possible to run without valid input?</span></span>

<span data-ttu-id="b8a32-180">항상 매개 변수에 사용되는 변수를 입력하세요(데이터 형식을 지정).</span><span class="sxs-lookup"><span data-stu-id="b8a32-180">Always type the variables that are being used for your parameters (specify a datatype).</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-181">이전 예제에서는 **ComputerName** 매개 변수의 데이터 형식으로 **String**을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-181">In the previous example, I've specified **String** as the datatype for the **ComputerName** parameter.</span></span> <span data-ttu-id="b8a32-182">이렇게 하면 단일 컴퓨터 이름만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-182">This causes it to allow only a single computer name to be specified.</span></span> <span data-ttu-id="b8a32-183">쉼표로 구분된 목록을 통해 둘 이상의 컴퓨터 이름을 지정하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-183">If more than one computer name is specified via a comma-separated list, an error is generated.</span></span>

```powershell
Test-MrParameterValidation -ComputerName Server01, Server02
```

```Output
Test-MrParameterValidation : Cannot process argument transformation on parameter
'ComputerName'. Cannot convert value to type System.String.
At line:1 char:42
+ Test-MrParameterValidation -ComputerName Server01, Server02
+
    + CategoryInfo          : InvalidData: (:) [Test-MrParameterValidation], ParameterBindingArg
     umentTransformationException
    + FullyQualifiedErrorId : ParameterArgumentTransformationError,Test-MrParameterValidation
```

<span data-ttu-id="b8a32-184">현재 정의에서 문제는 **ComputerName** 매개 변수의 값을 생략해도 함수는 유효하지만 함수를 성공적으로 완료하려면 값이 필요하다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-184">The problem with the current definition is that it's valid to omit the value of the **ComputerName** parameter, but a value is required for the function to complete successfully.</span></span> <span data-ttu-id="b8a32-185">여기에서 `Mandatory` 매개 변수 특성이 유용해집니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-185">This is where the `Mandatory` parameter attribute comes in handy.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-186">이전 예제에 사용된 구문은 PowerShell 버전 3.0 이상과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-186">The syntax used in the previous example is PowerShell version 3.0 and higher compatible.</span></span>
<span data-ttu-id="b8a32-187">`[Parameter(Mandatory=$true)]`를 대신 지정하면 함수를 PowerShell 버전 2.0 이상과 호환되도록 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-187">`[Parameter(Mandatory=$true)]` could be specified instead to make the function compatible with PowerShell version 2.0 and higher.</span></span> <span data-ttu-id="b8a32-188">**ComputerName**은 필수이므로 값이 하나 지정되지 않으면 함수는 값을 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-188">Now that the **ComputerName** is required, if one isn't specified, the function will prompt for one.</span></span>

```powershell
Test-MrParameterValidation
```

```Output
cmdlet Test-MrParameterValidation at command pipeline position 1
Supply values for the following parameters:
ComputerName:
```

<span data-ttu-id="b8a32-189">**ComputerName** 매개 변수에 둘 이상의 값을 허용하려면 **String** 데이터 형식을 사용하되 문자열 배열을 허용하도록 여는 대괄호와 닫는 대괄호를 데이터 형식에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-189">If you want to allow for more than one value for the **ComputerName** parameter, use the **String** datatype but add open and closed square brackets to the datatype to allow for an array of strings.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory)]
        [string[]]$ComputerName
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-190">**ComputerName** 매개 변수가 지정되지 않은 경우 이 매개 변수에 대한 기본값을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-190">Maybe you want to specify a default value for the **ComputerName** parameter if one isn't specified.</span></span>
<span data-ttu-id="b8a32-191">문제는 기본값을 필수 매개 변수와 함께 사용할 수 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-191">The problem is that default values can't be used with mandatory parameters.</span></span> <span data-ttu-id="b8a32-192">대신 `ValidateNotNullOrEmpty` 매개 변수 유효성 검사 특성을 기본값과 함께 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-192">Instead, you'll need to use the `ValidateNotNullOrEmpty` parameter validation attribute with a default value.</span></span>

```powershell
function Test-MrParameterValidation {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    Write-Output $ComputerName

}
```

<span data-ttu-id="b8a32-193">기본값을 설정하는 경우에도 정적 값을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-193">Even when setting a default value, try not to use static values.</span></span> <span data-ttu-id="b8a32-194">이전 예제에서는 값이 제공되지 않은 경우 자동으로 로컬 컴퓨터 이름으로 변환되는 `$env:COMPUTERNAME`이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-194">In the previous example, `$env:COMPUTERNAME` is used as the default value, which is automatically translated into the local computer name if a value is not provided.</span></span>

## <a name="verbose-output"></a><span data-ttu-id="b8a32-195">자세한 정보 출력</span><span class="sxs-lookup"><span data-stu-id="b8a32-195">Verbose Output</span></span>

<span data-ttu-id="b8a32-196">인라인 주석은 특히 복잡한 코드를 작성하는 경우에는 유용하지만 사용자가 코드 자체를 확인하지 않는 한 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-196">While inline comments are useful, especially if you're writing some complex code, they never get seen by users unless they look into the code itself.</span></span>

<span data-ttu-id="b8a32-197">다음 예제에 표시된 함수는 `foreach` 루프에 인라인 주석이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-197">The function shown in the following example has an inline comment in the `foreach` loop.</span></span> <span data-ttu-id="b8a32-198">이 주석은 찾기가 그다지 어렵지 않을 수 있지만, 함수가 수백 개의 코드 줄을 포함한다고 가정해 보세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-198">While this particular comment may not be that difficult to locate, imagine if the function included hundreds of lines of code.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        #Attempting to perform some action on $Computer <<-- Don't use
        #inline comments like this, use write verbose instead.
        Write-Output $Computer
    }

}
```

<span data-ttu-id="b8a32-199">더 나은 옵션은 인라인 주석 대신 `Write-Verbose`를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-199">A better option is to use `Write-Verbose` instead of inline comments.</span></span>

```powershell
function Test-MrVerboseOutput {

    [CmdletBinding()]
    param (
        [ValidateNotNullOrEmpty()]
        [string[]]$ComputerName = $env:COMPUTERNAME
    )

    foreach ($Computer in $ComputerName) {
        Write-Verbose -Message "Attempting to perform some action on $Computer"
        Write-Output $Computer
    }

}
```

<span data-ttu-id="b8a32-200">**Verbose** 매개 변수 없이 함수를 호출하면 자세한 정보 출력이 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-200">When the function is called without the **Verbose** parameter, the verbose output won't be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02
```

<span data-ttu-id="b8a32-201">**Verbose** 매개 변수를 사용하여 호출하면 자세한 정보 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-201">When it's called with the **Verbose** parameter, the verbose output will be displayed.</span></span>

```powershell
Test-MrVerboseOutput -ComputerName Server01, Server02 -Verbose
```

## <a name="pipeline-input"></a><span data-ttu-id="b8a32-202">파이프라인 입력</span><span class="sxs-lookup"><span data-stu-id="b8a32-202">Pipeline Input</span></span>

<span data-ttu-id="b8a32-203">함수에서 파이프라인 입력을 허용하도록 하려면 몇 가지 추가 코딩이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-203">When you want your function to accept pipeline input, some additional coding is necessary.</span></span> <span data-ttu-id="b8a32-204">이 책의 앞부분에서 설명한 것처럼 명령은 **값 기준**(형식 기준) 또는 **속성 이름 기준**으로 파이프라인 입력을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-204">As mentioned earlier in this book, commands can accept pipeline input **by value** (by type) or **by property name**.</span></span> <span data-ttu-id="b8a32-205">네이티브 명령과 마찬가지로 함수를 작성하여 이러한 유형의 입력 중 하나 또는 둘 모두를 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-205">You can write your functions just like the native commands so that they accept either one or both of these types of input.</span></span>

<span data-ttu-id="b8a32-206">**값 기준**으로 파이프라인 입력을 허용하려면 해당 매개 변수에 `ValueFromPipeline` 매개 변수 특성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-206">To accept pipeline input **by value**, specified the `ValueFromPipeline` parameter attribute for that particular parameter.</span></span> <span data-ttu-id="b8a32-207">각 데이터 형식 중 하나에서만 **값 기준**으로 파이프라인 입력을 수락할 수 있다는 데 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-207">Keep in mind that you can only accept pipeline input **by value** from one of each datatype.</span></span> <span data-ttu-id="b8a32-208">예를 들어 문자열 입력을 허용하는 두 개의 매개 변수가 있는 경우 이 중 하나만 **값 기준**으로 파이프라인 입력을 허용할 수 있습니다. 두 문자열 매개 변수 모두에 지정할 경우 파이프라인 입력이 어느 매개 변수에 바인딩할지 알 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-208">For example, if you have two parameters that accept string input, only one of those can accept pipeline input **by value** because if you specified it for both of the string parameters, the pipeline input wouldn't know which one to bind to.</span></span> <span data-ttu-id="b8a32-209">이것이 필자가 이 유형의 파이프라인 입력을 **값 기준** 대신 _형식 기준_으로 부르는 또 다른 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-209">This is another reason I call this type of pipeline input _by type_ instead of **by value**.</span></span>

<span data-ttu-id="b8a32-210">파이프라인 입력은 `foreach` 루프에서 항목이 처리되는 방식과 비슷하게 한 번에 한 항목으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-210">Pipeline input comes in one item at a time similar to the way items are handled in a `foreach` loop.</span></span>
<span data-ttu-id="b8a32-211">배열을 입력으로 허용하는 경우 최소한 `process` 블록이 이들 각 항목을 처리하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-211">At a minimum, a `process` block is required to process each of these items if you're accepting an array as input.</span></span> <span data-ttu-id="b8a32-212">단일 값만 입력으로 허용하는 경우에는 `process` 블록이 필요하지 않지만 일관성을 위해 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-212">If you're only accepting a single value as input, a `process` block isn't necessary, but I still recommend specifying it for consistency.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline)]
        [string[]]$ComputerName
    )

    PROCESS {
        Write-Output $ComputerName
    }

}
```

<span data-ttu-id="b8a32-213">**속성 이름 기준**으로 파이프라인 입력을 허용하는 것은 비슷하지만 `ValueFromPipelineByPropertyName` 매개 변수 특성을 사용하여 지정되고 데이터 형식에 관계없이 원하는 수의 매개 변수에 지정될 수 있다는 점만 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-213">Accepting pipeline input **by property name** is similar except it's specified with the `ValueFromPipelineByPropertyName` parameter attribute and it can be specified for any number of parameters regardless of datatype.</span></span> <span data-ttu-id="b8a32-214">핵심은 파이프되는 명령의 출력이 매개 변수 이름 또는 함수의 매개 변수 별칭과 일치하는 속성 이름을 포함해야 한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-214">The key is that the output of the command that's being piped in has to have a property name that matches the name of the parameter or a parameter alias of your function.</span></span>

```powershell
function Test-MrPipelineInput {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
            Write-Output $ComputerName
    }

}
```

<span data-ttu-id="b8a32-215">`BEGIN` 및 `END` 블록은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-215">`BEGIN` and `END` blocks are optional.</span></span> <span data-ttu-id="b8a32-216">`BEGIN`은 `PROCESS` 블록 앞에 지정되고 파이프라인에서 수신되는 항목 이전에 초기 작업을 수행하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-216">`BEGIN` would be specified before the `PROCESS` block and is used to perform any initial work prior to the items being received from the pipeline.</span></span> <span data-ttu-id="b8a32-217">다음을 이해하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-217">This is important to understand.</span></span> <span data-ttu-id="b8a32-218">파이프되는 값은 `BEGIN` 블록에서 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-218">Values that are piped in are not accessible in the `BEGIN` block.</span></span> <span data-ttu-id="b8a32-219">`END` 블록은 `PROCESS` 블록 다음에 지정되고, 파이프된 항목이 모두 처리되면 정리에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-219">The `END` block would be specified after the `PROCESS` block and is used for cleanup once all of the items that are piped in have been processed.</span></span>

## <a name="error-handling"></a><span data-ttu-id="b8a32-220">오류 처리</span><span class="sxs-lookup"><span data-stu-id="b8a32-220">Error Handling</span></span>

<span data-ttu-id="b8a32-221">다음 예제에 표시된 함수는 컴퓨터에 연결할 수 없을 때 처리되지 않은 예외를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-221">The function shown in the following example generates an unhandled exception when a computer can't be contacted.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            Test-WSMan -ComputerName $Computer
        }
    }

}
```

<span data-ttu-id="b8a32-222">PowerShell에서는 오류를 처리하는 몇 가지 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-222">There are a couple of different ways to handle errors in PowerShell.</span></span> <span data-ttu-id="b8a32-223">`Try/Catch`는 오류를 처리하는 최신 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-223">`Try/Catch` is the more modern way to handle errors.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="b8a32-224">이전 예제에 표시된 함수는 오류 처리를 사용하지만 처리되지 않은 예외도 생성합니다. 명령이 종료 오류를 생성하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-224">Although the function shown in the previous example uses error handling, it also generates an unhandled exception because the command doesn't generate a terminating error.</span></span> <span data-ttu-id="b8a32-225">이를 이해하는 것도 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-225">This is also important to understand.</span></span> <span data-ttu-id="b8a32-226">종료 오류만 catch됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-226">Only terminating errors are caught.</span></span> <span data-ttu-id="b8a32-227">종료되지 않는 오류를 종료하는 오류로 설정하려면 **Stop**을 값으로 사용하여 **ErrorAction** 매개 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-227">Specify the **ErrorAction** parameter with **Stop** as the value to turn a non-terminating error into a terminating one.</span></span>

```powershell
function Test-MrErrorHandling {

    [CmdletBinding()]
    param (
        [Parameter(Mandatory,
                   ValueFromPipeline,
                   ValueFromPipelineByPropertyName)]
        [string[]]$ComputerName
    )

    PROCESS {
        foreach ($Computer in $ComputerName) {
            try {
                Test-WSMan -ComputerName $Computer -ErrorAction Stop
            }
            catch {
                Write-Warning -Message "Unable to connect to Computer: $Computer"
            }
        }
    }

}
```

<span data-ttu-id="b8a32-228">반드시 필요한 경우가 아니면 전역 `$ErrorActionPreference` 변수를 수정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-228">Don't modify the global `$ErrorActionPreference` variable unless absolutely necessary.</span></span> <span data-ttu-id="b8a32-229">PowerShell 함수 내에서 직접 .NET과 같은 항목을 사용하는 경우 명령 자체에서 **ErrorAction**을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-229">If you're using something like .NET directly from within your PowerShell function, you can't specify the **ErrorAction** on the command itself.</span></span> <span data-ttu-id="b8a32-230">이 시나리오에서는 전역 `$ErrorActionPreference` 변수를 변경해야 할 수 있지만, 변경하는 경우 명령을 시도해본 후 즉시 다시 변경하세요.</span><span class="sxs-lookup"><span data-stu-id="b8a32-230">In that scenario, you might need to change the global `$ErrorActionPreference` variable, but if you do change it, change it back immediately after trying the command.</span></span>

## <a name="comment-based-help"></a><span data-ttu-id="b8a32-231">주석 기반 도움말</span><span class="sxs-lookup"><span data-stu-id="b8a32-231">Comment-Based Help</span></span>

<span data-ttu-id="b8a32-232">함수를 공유하는 다른 사용자가 사용 방법을 알 수 있도록 함수에 주석 기반 도움말을 추가하는 것이 모범 사례로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-232">It's considered to be a best practice to add comment based help to your functions so the people you're sharing them with will know how to use them.</span></span>

```powershell
function Get-MrAutoStoppedService {

<#
.SYNOPSIS
    Returns a list of services that are set to start automatically, are not
    currently running, excluding the services that are set to delayed start.

.DESCRIPTION
    Get-MrAutoStoppedService is a function that returns a list of services from
    the specified remote computer(s) that are set to start automatically, are not
    currently running, and it excludes the services that are set to start automatically
    with a delayed startup.

.PARAMETER ComputerName
    The remote computer(s) to check the status of the services on.

.PARAMETER Credential
    Specifies a user account that has permission to perform this action. The default
    is the current user.

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1', 'Server2'

.EXAMPLE
     'Server1', 'Server2' | Get-MrAutoStoppedService

.EXAMPLE
     Get-MrAutoStoppedService -ComputerName 'Server1' -Credential (Get-Credential)

.INPUTS
    String

.OUTPUTS
    PSCustomObject

.NOTES
    Author:  Mike F Robbins
    Website: http://mikefrobbins.com
    Twitter: @mikefrobbins
#>

    [CmdletBinding()]
    param (

    )

    #Function Body

}
```

<span data-ttu-id="b8a32-233">함수에 주석 기반 도움말을 추가하는 경우 기본 제공 명령과 마찬가지로 도움말을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-233">When you add comment based help to your functions, help can be retrieved for them just like the default built-in commands.</span></span>

<span data-ttu-id="b8a32-234">PowerShell에서 함수를 작성하는 모든 구문은 특히 이제 막 시작하는 사용자에게는 압도적으로 느껴질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-234">All of the syntax for writing a function in PowerShell can seem overwhelming especially for someone who is just getting started.</span></span> <span data-ttu-id="b8a32-235">필자는 가끔 특정 구문이 기억나지 않을 때 별도의 모니터에서 ISE의 두 번째 복사본을 열고 함수의 코드를 입력하는 동안 "Cmdlet(고급 함수) -전체" 코드 조각을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-235">Often times if I can't remember the syntax for something, I'll open a second copy of the ISE on a separate monitor and view the "Cmdlet (advanced function) - Complete" snippet while typing in the code for my function.</span></span> <span data-ttu-id="b8a32-236">PowerShell ISE에서 <kbd>Ctrl</kbd>+<kbd>J</kbd> 키 조합을 사용하여 이 코드 조각에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-236">Snippets can be accessed in the PowerShell ISE using the <kbd>Ctrl</kbd>+<kbd>J</kbd> key combination.</span></span>

## <a name="summary"></a><span data-ttu-id="b8a32-237">요약</span><span class="sxs-lookup"><span data-stu-id="b8a32-237">Summary</span></span>

<span data-ttu-id="b8a32-238">이 장에서는 함수를 고급 함수로 전환하는 방법과 매개 변수 유효성 검사, 자세한 정보 출력, 파이프라인 입력, 오류 처리, 주석 기반 도움말 등 PowerShell 함수를 작성할 때 고려해야 할 중요한 요소 몇 가지를 포함하여 PowerShell에서 함수를 작성하는 기본 사항을 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a32-238">In this chapter you've learned the basics of writing functions in PowerShell to include how to turn a function into an advanced function and some of the more important elements that you should consider when writing PowerShell functions such as parameter validation, verbose output, pipeline input, error handling, and comment based help.</span></span>

## <a name="review"></a><span data-ttu-id="b8a32-239">검토</span><span class="sxs-lookup"><span data-stu-id="b8a32-239">Review</span></span>

1. <span data-ttu-id="b8a32-240">PowerShell에서 승인된 동사 목록을 얻으려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="b8a32-240">How do you obtain a list of approved verbs in PowerShell?</span></span>
1. <span data-ttu-id="b8a32-241">PowerShell 함수를 고급 함수로 전환하려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="b8a32-241">How do you turn a PowerShell function into an advanced function?</span></span>
1. <span data-ttu-id="b8a32-242">**WhatIf** 및 **Confirm** 매개 변수는 언제 PowerShell 함수에 추가해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="b8a32-242">When should **WhatIf** and **Confirm** parameters be added to your PowerShell functions?</span></span>
1. <span data-ttu-id="b8a32-243">종료되지 않는 오류를 종료하는 오류로 전환하려면 어떻게 하나요?</span><span class="sxs-lookup"><span data-stu-id="b8a32-243">How do you turn a non-terminating error into a terminating one?</span></span>
1. <span data-ttu-id="b8a32-244">주석 기반 도움말을 함수에 추가해야 하는 이유는 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="b8a32-244">Why should you add comment based help to your functions?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="b8a32-245">권장 참조 항목</span><span class="sxs-lookup"><span data-stu-id="b8a32-245">Recommended Reading</span></span>

- <span data-ttu-id="b8a32-246">[about_Functions][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-246">[about_Functions][]</span></span>
- <span data-ttu-id="b8a32-247">[about_Functions_Advanced_Parameters][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-247">[about_Functions_Advanced_Parameters][]</span></span>
- <span data-ttu-id="b8a32-248">[about_CommonParameters][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-248">[about_CommonParameters][]</span></span>
- <span data-ttu-id="b8a32-249">[about_Functions_CmdletBindingAttribute][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-249">[about_Functions_CmdletBindingAttribute][]</span></span>
- <span data-ttu-id="b8a32-250">[about_Functions_Advanced][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-250">[about_Functions_Advanced][]</span></span>
- <span data-ttu-id="b8a32-251">[about_Try_Catch_Finally][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-251">[about_Try_Catch_Finally][]</span></span>
- <span data-ttu-id="b8a32-252">[about_Comment_Based_Help][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-252">[about_Comment_Based_Help][]</span></span>
- <span data-ttu-id="b8a32-253">[비디오: 고급 함수 및 스크립트 모듈을 사용하여 PowerShell 도구 작성][]</span><span class="sxs-lookup"><span data-stu-id="b8a32-253">[Video: PowerShell Toolmaking with Advanced Functions and Script Modules][]</span></span>

<!-- link references -->
[about_Functions]: /powershell/module/microsoft.powershell.core/about/about_functions
[about_Functions_Advanced_Parameters]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced_parameters
[about_CommonParameters]: /powershell/module/microsoft.powershell.core/about/about_commonparameters
[about_Functions_CmdletBindingAttribute]: /powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute
[about_Functions_Advanced]: /powershell/module/microsoft.powershell.core/about/about_functions_advanced
[about_Try_Catch_Finally]: /powershell/module/microsoft.powershell.core/about/about_try_catch_finally
[about_Comment_Based_Help]: /powershell/module/microsoft.powershell.core/about/about_comment_based_help
[비디오: 고급 함수 및 스크립트 모듈을 사용하여 PowerShell 도구 작성]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [파스칼식 대/소문자]: /dotnet/standard/design-guidelines/capitalization-conventions
[Video: PowerShell Toolmaking with Advanced Functions and Script Modules]: https://mikefrobbins.com/2016/05/26/video-powershell-toolmaking-with-advanced-functions-and-script-modules/) [Pascal case]: /dotnet/standard/design-guidelines/capitalization-conventionss
