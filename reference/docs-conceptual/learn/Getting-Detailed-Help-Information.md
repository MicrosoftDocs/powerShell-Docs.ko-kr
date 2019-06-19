---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: 자세한 도움말 정보 보기
ms.openlocfilehash: 3f52de8c9963618c154b119d5f4859a92d61fbda
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030410"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="ecf04-103">자세한 도움말 정보 보기</span><span class="sxs-lookup"><span data-stu-id="ecf04-103">Getting detailed help information</span></span>

<span data-ttu-id="ecf04-104">PowerShell에는 PowerShell 개념과 PowerShell 언어를 설명하는 자세한 도움말 문서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="ecf04-105">각 cmdlet 및 공급자에 대한 도움말 문서와 많은 함수 및 스크립트에 대한 도움말 문서도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="ecf04-106">명령 프롬프트에서 이러한 도움말 문서를 표시하거나 [PowerShell](/powershell/scripting/overview)온라인 설명서에서 이러한 문서의 가장 최근 업데이트 버전을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="ecf04-107">cmdlet에 대한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="ecf04-107">Getting help for cmdlets</span></span>

<span data-ttu-id="ecf04-108">PowerShell cmdlet에 대한 도움말을 보려면 [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="ecf04-109">예를 들어 `Get-ChildItem` cmdlet에 대한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="ecf04-110">또는</span><span class="sxs-lookup"><span data-stu-id="ecf04-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="ecf04-111">Get-Help cmdlet에 대한 도움말을 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="ecf04-112">예:</span><span class="sxs-lookup"><span data-stu-id="ecf04-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="ecf04-113">세션에 있는 모든 cmdlet 도움말 문서의 목록을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="ecf04-114">각 도움말 문서를 한 번에 한 페이지씩 표시하려면 `help` 함수 또는 해당 별칭 `man`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="ecf04-115">예를 들어 `Get-ChildItem` cmdlet에 대한 도움말을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="ecf04-116">또는</span><span class="sxs-lookup"><span data-stu-id="ecf04-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="ecf04-117">자세한 정보를 표시하려면 `Get-Help` cmdlet의 **Detailed** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ecf04-118">예를 들어 `Get-ChildItem` cmdlet에 대한 자세한 정보를 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="ecf04-119">도움말 문서의 모든 내용을 표시하려면 `Get-Help` cmdlet의 **Full** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ecf04-120">예를 들어 `Get-ChildItem` cmdlet에 대한 도움말 문서의 모든 내용을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="ecf04-121">cmdlet의 매개 변수에 대한 자세한 도움말을 보려면 `Get-Help` cmdlet의 **Parameter** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ecf04-122">예를 들어 `Get-ChildItem` cmdlet의 모든 매개 변수에 대한 자세한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="ecf04-123">도움말 문서의 예제만 표시하려면 `Get-Help`의 **Example** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="ecf04-124">예를 들어 `Get-ChildItem` cmdlet에 대한 도움말 문서의 예제만 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="ecf04-125">작성하는 cmdlet의 도움말 문서를 작성하는 방법에 대한 자세한 내용은 [Cmdlet 도움말 작성 방법](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecf04-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="ecf04-126">개념 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="ecf04-126">Getting conceptual help</span></span>

<span data-ttu-id="ecf04-127">`Get-Help` cmdlet은 PowerShell 언어에 대한 문서를 포함하여 PowerShell의 개념 항목에 대한 정보도 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="ecf04-128">개념 도움말 문서는 "about_" 접두사로 시작합니다(예: about_line_editing).</span><span class="sxs-lookup"><span data-stu-id="ecf04-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="ecf04-129">개념 문서의 이름은 영어가 아닌 PowerShell 버전에서도 영어로 입력해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="ecf04-130">개념 문서 목록을 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="ecf04-131">특정 도움말 문서를 표시하려면 다음과 같이 문서 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="ecf04-132">**Detailed**, **Parameter** 및 **Examples**와 같은 `Get-Help`의 매개 변수는 개념 도움말 문서의 표시에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="ecf04-133">공급자에 대한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="ecf04-133">Getting help about providers</span></span>

<span data-ttu-id="ecf04-134">`Get-Help` cmdlet은 PowerShell 공급자에 대한 정보를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="ecf04-135">공급자에 대한 도움말을 보려면 "`Get-Help`"를 입력한 다음, 공급자 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="ecf04-136">예를 들어 레지스트리 공급자에 대한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="ecf04-137">세션에 있는 모든 공급자 도움말 문서의 목록을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="ecf04-138">**Detailed**, **Parameter** 및 **Examples**와 같은 `Get-Help`의 매개 변수는 공급자 도움말 문서의 표시에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="ecf04-139">스크립트 및 함수에 대한 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="ecf04-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="ecf04-140">PowerShell의 많은 스크립트 및 함수에는 도움말 문서가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="ecf04-141">`Get-Help` cmdlet을 사용하여 스크립트 및 함수에 대한 도움말 문서를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="ecf04-142">함수에 대한 도움말을 표시하려면 "`Get-Help`"를 입력한 다음, 함수 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="ecf04-143">예를 들어 `Disable-PSRemoting` 함수에 대한 도움말을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="ecf04-144">스크립트에 대한 도움말을 표시하려면 스크립트 파일의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="ecf04-145">스크립트가 Path 환경 변수에 나열된 경로에 없는 경우 정규화된 경로를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="ecf04-146">예를 들어 C:\\PS-Test 디렉터리에 "TestScript.ps1"이라는 스크립트가 있는 경우 이 스크립트의 도움말 문서를 표시하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="ecf04-147">cmdlet 도움말을 표시하도록 디자인된 매개 변수는 스크립트 및 함수 도움말에도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="ecf04-148">그러나 `Get-Help *`를 표시할 때 함수 및 스크립트에 대한 도움말은 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="ecf04-149">함수 및 스크립트에 대한 도움말 문서 작성에 대한 내용은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecf04-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="ecf04-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ecf04-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="ecf04-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="ecf04-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="ecf04-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="ecf04-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="ecf04-153">온라인 도움말 보기</span><span class="sxs-lookup"><span data-stu-id="ecf04-153">Getting help online</span></span>

<span data-ttu-id="ecf04-154">온라인 도움말 문서는 도움말을 보는 가장 좋은 방법 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="ecf04-155">온라인 문서는 업데이트하기가 더 쉽고 가장 최신 콘텐츠를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="ecf04-156">온라인 도움말을 보려면 `Get-Help` cmdlet의 **Online** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ecf04-157">공급자 도움말 및 개념(정보) 도움말을 포함하여 Powershell에 함께 제공되는 모든 도움말 문서는 온라인 [PowerShell](/powershell/scripting/powershell-scripting) 설명서에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="ecf04-158">개념(about_\*) 또는 공급자 도움말 문서에서는 **Online** 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="ecf04-159">온라인 도움말은 선택 항목이기 때문에 일부 cmdlet, 함수 또는 스크립트에는 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="ecf04-160">예를 들어 `Get-ChildItem` cmdlet에 대한 온라인 버전의 도움말 문서를 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="ecf04-161">PowerShell은 기본 브라우저에서 문서를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="ecf04-162">도움말 문서에 대해 온라인 도움말이 지원되는 경우 도움말 문서의 URL도 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="ecf04-163">URL은 도움말 문서의 관련 링크 섹션에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="ecf04-164">예를 들어 Add-Computer cmdlet의 온라인 버전에 대한 URL을 보려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="ecf04-165">문서의 관련 링크 섹션에 있는 첫 번째 줄은 아래와 같이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ecf04-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="ecf04-166">도움말 문서에 대한 온라인 지원을 제공하는 방법에 대한 내용은 [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ecf04-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="ecf04-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ecf04-167">See also</span></span>

- [<span data-ttu-id="ecf04-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ecf04-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="ecf04-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="ecf04-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="ecf04-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="ecf04-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="ecf04-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="ecf04-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
