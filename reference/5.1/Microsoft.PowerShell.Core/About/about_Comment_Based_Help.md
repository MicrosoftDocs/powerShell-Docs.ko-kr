---
description: 함수 및 스크립트에 대 한 주석 기반 도움말 항목을 작성 하는 방법에 대해 설명 합니다.
Locale: en-US
ms.date: 06/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comment_based_help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comment_Based_Help
ms.openlocfilehash: cc19b11322e8b2062f9659c3fbce92ad5c6eded0
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194226"
---
# <a name="about-comment-based-help"></a><span data-ttu-id="420cf-103">주석 기반 도움말 정보</span><span class="sxs-lookup"><span data-stu-id="420cf-103">About Comment-based Help</span></span>

## <a name="short-description"></a><span data-ttu-id="420cf-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="420cf-104">Short description</span></span>
<span data-ttu-id="420cf-105">함수 및 스크립트에 대 한 주석 기반 도움말 항목을 작성 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-105">Describes how to write comment-based help topics for functions and scripts.</span></span>

## <a name="long-description"></a><span data-ttu-id="420cf-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-106">Long description</span></span>

<span data-ttu-id="420cf-107">특수 도움말 주석 키워드를 사용 하 여 함수 및 스크립트에 대 한 주석 기반 도움말 항목을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-107">You can write comment-based help topics for functions and scripts by using special help comment keywords.</span></span>

<span data-ttu-id="420cf-108">[Get-help](xref:Microsoft.PowerShell.Core.Get-Help) CMDLET은 XML 파일에서 생성 된 cmdlet 도움말 항목을 표시 하는 것과 동일한 형식으로 주석 기반 도움말을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-108">The [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) cmdlet displays comment-based help in the same format in which it displays the cmdlet help topics that are generated from XML files.</span></span> <span data-ttu-id="420cf-109">사용자는 `Get-Help` **자세히**, **전체**, **예** 및 **온라인** 등의 모든 매개 변수를 사용 하 여 주석 기반 도움말의 내용을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-109">Users can use all of the parameters of `Get-Help`, such as **Detailed**, **Full**, **Examples**, and **Online**, to display the contents of comment-based help.</span></span>

<span data-ttu-id="420cf-110">함수 및 스크립트에 대 한 XML 기반 도움말 파일을 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-110">You can also write XML-based help files for functions and scripts.</span></span> <span data-ttu-id="420cf-111">Cmdlet을 사용 하 여 `Get-Help` 함수 또는 스크립트에 대 한 XML 기반 도움말 파일을 찾으려면 키워드를 사용 `.ExternalHelp` 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-111">To enable the `Get-Help` cmdlet to find the XML-based help file for a function or script, use the `.ExternalHelp` keyword.</span></span> <span data-ttu-id="420cf-112">이 키워드가 없으면 `Get-Help` 함수 또는 스크립트에 대 한 XML 기반 도움말 항목을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-112">Without this keyword, `Get-Help` cannot find XML-based help topics for functions or scripts.</span></span>

<span data-ttu-id="420cf-113">이 항목에서는 함수 및 스크립트에 대 한 도움말 항목을 작성 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-113">This topic explains how to write help topics for functions and scripts.</span></span> <span data-ttu-id="420cf-114">함수 및 스크립트에 대 한 도움말 항목을 표시 하는 방법에 대 한 자세한 내용은 [get-help](xref:Microsoft.PowerShell.Core.Get-Help)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="420cf-114">For information about how to display help topics for functions and scripts, see [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help).</span></span>

<span data-ttu-id="420cf-115">[Update-help](xref:Microsoft.PowerShell.Core.Update-Help) 및 [Save HELP](xref:Microsoft.PowerShell.Core.Save-Help) cmdlet은 XML 파일에 대해서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-115">The [Update-Help](xref:Microsoft.PowerShell.Core.Update-Help) and [Save-Help](xref:Microsoft.PowerShell.Core.Save-Help) cmdlets work only on XML files.</span></span> <span data-ttu-id="420cf-116">업데이트할 수 있는 도움말은 주석 기반 도움말 항목을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-116">Updatable Help does not support comment-based help topics.</span></span>

## <a name="syntax-for-comment-based-help"></a><span data-ttu-id="420cf-117">주석 기반 도움말 구문</span><span class="sxs-lookup"><span data-stu-id="420cf-117">Syntax for comment-based help</span></span>

<span data-ttu-id="420cf-118">주석 기반 도움말의 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-118">The syntax for comment-based help is as follows:</span></span>

```
# .<help keyword>
# <help content>
```

<span data-ttu-id="420cf-119">또는</span><span class="sxs-lookup"><span data-stu-id="420cf-119">or</span></span>

```
<#
.<help keyword>
<help content>
#>
```

<span data-ttu-id="420cf-120">주석 기반 도움말은 일련의 주석으로 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-120">Comment-based help is written as a series of comments.</span></span> <span data-ttu-id="420cf-121">주석의 각 줄 앞에 주석 기호를 입력 `#` 하거나 `<#` 및 기호를 사용 하 여 `#>` 주석 블록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-121">You can type a comment symbol `#` before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="420cf-122">주석 블록 내의 모든 줄은 주석으로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-122">All the lines within the comment block are interpreted as comments.</span></span>

<span data-ttu-id="420cf-123">주석 기반 도움말 항목의 모든 줄은 연속적 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-123">All of the lines in a comment-based help topic must be contiguous.</span></span> <span data-ttu-id="420cf-124">주석 기반 도움말 항목이 도움말 항목에 포함 되지 않은 주석을 따르는 경우에는 마지막으로 지원 되지 않는 주석 줄과 주석 기반 도움말의 시작 부분 사이에 하나 이상의 빈 줄이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-124">If a comment-based help topic follows a comment that is not part of the help topic, there must be at least one blank line between the last non-help comment line and the beginning of the comment-based help.</span></span>

<span data-ttu-id="420cf-125">키워드는 주석 기반 도움말의 각 섹션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-125">Keywords define each section of comment-based help.</span></span> <span data-ttu-id="420cf-126">각 주석 기반 도움말 키워드 앞에는 점이 `.` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-126">Each comment-based help keyword is preceded by a dot `.`.</span></span> <span data-ttu-id="420cf-127">키워드는 순서에 관계 없이 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-127">The keywords can appear in any order.</span></span> <span data-ttu-id="420cf-128">키워드 이름은 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-128">The keyword names are not case-sensitive.</span></span>

<span data-ttu-id="420cf-129">예를 들어 키워드는 함수 또는 스크립트에 대 한 설명 앞에와 야 `.Description` 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-129">For example, the `.Description` keyword precedes a description of a function or script.</span></span>

```
<#
.Description
Get-Function displays the name and syntax of all functions in the session.
#>
```

<span data-ttu-id="420cf-130">주석 블록은 키워드를 하나 이상 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-130">The comment block must contain at least one keyword.</span></span> <span data-ttu-id="420cf-131">과 같은 일부 키워드는 `.EXAMPLE` 동일한 주석 블록에 여러 번 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-131">Some of the keywords, such as `.EXAMPLE`, can appear many times in the same comment block.</span></span> <span data-ttu-id="420cf-132">각 키워드에 대 한 도움말 콘텐츠는 키워드 뒤의 줄에서 시작 하 여 여러 줄에 걸쳐 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-132">The help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

## <a name="syntax-for-comment-based-help-in-functions"></a><span data-ttu-id="420cf-133">함수의 주석 기반 도움말 구문</span><span class="sxs-lookup"><span data-stu-id="420cf-133">Syntax for comment-based help in functions</span></span>

<span data-ttu-id="420cf-134">함수에 대 한 주석 기반 도움말은 다음 세 위치 중 하나에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-134">Comment-based help for a function can appear in one of three locations:</span></span>

- <span data-ttu-id="420cf-135">함수 본문의 시작 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-135">At the beginning of the function body.</span></span>
- <span data-ttu-id="420cf-136">함수 본문의 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-136">At the end of the function body.</span></span>
- <span data-ttu-id="420cf-137">키워드 앞에 `function` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-137">Before the `function` keyword.</span></span> <span data-ttu-id="420cf-138">함수 도움말의 마지막 줄과 키워드 사이에는 빈 줄이 둘 이상 있을 수 없습니다 `function` .</span><span class="sxs-lookup"><span data-stu-id="420cf-138">There cannot be more than one blank line between the last line of the function help and the `function` keyword.</span></span>

<span data-ttu-id="420cf-139">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-139">For example:</span></span>

```powershell
function Get-Function
{
<#
.<help keyword>
<help content>
#>

  # function logic
}
```

<span data-ttu-id="420cf-140">또는</span><span class="sxs-lookup"><span data-stu-id="420cf-140">or</span></span>

```powershell
function Get-Function
{
   # function logic

<#
.<help keyword>
<help content>
#>
}
```

<span data-ttu-id="420cf-141">또는</span><span class="sxs-lookup"><span data-stu-id="420cf-141">or</span></span>

```powershell
<#
.<help keyword>
<help content>
#>
function Get-Function { }
```

## <a name="syntax-for-comment-based-help-in-scripts"></a><span data-ttu-id="420cf-142">스크립트의 주석 기반 도움말 구문</span><span class="sxs-lookup"><span data-stu-id="420cf-142">Syntax for comment-based help in scripts</span></span>

<span data-ttu-id="420cf-143">스크립트에 대 한 주석 기반 도움말은 스크립트의 다음 두 위치 중 하나에 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-143">Comment-based help for a script can appear in one of the following two locations in the script.</span></span>

- <span data-ttu-id="420cf-144">스크립트 파일의 시작 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-144">At the beginning of the script file.</span></span> <span data-ttu-id="420cf-145">스크립트 도움말은 주석 및 빈 줄만 스크립트에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-145">Script help can be preceded in the script only by comments and blank lines.</span></span>

  <span data-ttu-id="420cf-146">스크립트 본문의 첫 번째 항목 (도움말)이 함수 선언 인 경우 스크립트 도움말과 함수 선언 끝 사이에 두 개 이상의 빈 줄이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-146">If the first item in the script body (after the help) is a function declaration, there must be at least two blank lines between the end of the script help and the function declaration.</span></span> <span data-ttu-id="420cf-147">그렇지 않으면 도움말은 스크립트에 대 한 도움말이 아니라 함수에 대 한 도움말로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-147">Otherwise, the help is interpreted as being help for the function, not help for the script.</span></span>

- <span data-ttu-id="420cf-148">스크립트 파일의 끝에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-148">At the end of the script file.</span></span> <span data-ttu-id="420cf-149">그러나 스크립트가 서명 된 경우 스크립트 파일의 시작 부분에 주석 기반 도움말을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-149">However, if the script is signed, place Comment-based help at the beginning of the script file.</span></span> <span data-ttu-id="420cf-150">스크립트 끝은 서명 블록에 의해 점유 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-150">The end of the script is occupied by the signature block.</span></span>

<span data-ttu-id="420cf-151">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-151">For example:</span></span>

```powershell
<#
.<help keyword>
<help content>
#>


function Get-Function { }
```

<span data-ttu-id="420cf-152">또는</span><span class="sxs-lookup"><span data-stu-id="420cf-152">or</span></span>

```powershell
function Get-Function { }

<#
.<help keyword>
<help content>
#>
```

## <a name="syntax-for-comment-based-help-in-script-modules"></a><span data-ttu-id="420cf-153">스크립트 모듈의 주석 기반 도움말 구문</span><span class="sxs-lookup"><span data-stu-id="420cf-153">Syntax for comment-based help in script modules</span></span>

<span data-ttu-id="420cf-154">스크립트 모듈에서 `.psm1` 주석 기반 도움말은 스크립트에 대 한 구문이 아니라 함수의 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-154">In a script module `.psm1`, comment-based help uses the syntax for functions, not the syntax for scripts.</span></span> <span data-ttu-id="420cf-155">스크립트 모듈에 정의 된 모든 함수에 대 한 도움말을 제공 하기 위해 스크립트 구문을 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-155">You cannot use the script syntax to provide help for all functions defined in a script module.</span></span>

<span data-ttu-id="420cf-156">예를 들어 키워드를 사용 하 여 `.ExternalHelp` 스크립트 모듈의 함수에 대 한 XML 기반 도움말 파일을 식별 하는 경우 `.ExternalHelp` 각 함수에 주석을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-156">For example, if you are using the `.ExternalHelp` keyword to identify the XML-based help files for the functions in a script module, you must add an `.ExternalHelp` comment to each function.</span></span>

```powershell
# .ExternalHelp <XML-file-name>
function <function-name>
{
  ...
}
```

## <a name="comment-based-help-keywords"></a><span data-ttu-id="420cf-157">주석 기반 도움말 키워드</span><span class="sxs-lookup"><span data-stu-id="420cf-157">Comment-based help keywords</span></span>

<span data-ttu-id="420cf-158">다음은 유효한 주석 기반 도움말 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-158">The following are valid comment-based help keywords.</span></span> <span data-ttu-id="420cf-159">이러한 항목은 일반적으로 원하는 용도와 함께 도움말 항목에 표시 되는 순서 대로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-159">They are listed in the order in which they typically appear in a help topic along with their intended use.</span></span> <span data-ttu-id="420cf-160">이러한 키워드는 주석 기반 도움말에서 순서에 관계 없이 나타날 수 있으며 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-160">These keywords can appear in any order in the comment-based help, and they are not case-sensitive.</span></span>

### <a name="synopsis"></a><span data-ttu-id="420cf-161">. 개요</span><span class="sxs-lookup"><span data-stu-id="420cf-161">.SYNOPSIS</span></span>

<span data-ttu-id="420cf-162">함수 또는 스크립트에 대 한 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-162">A brief description of the function or script.</span></span> <span data-ttu-id="420cf-163">이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-163">This keyword can be used only once in each topic.</span></span>

### <a name="description"></a><span data-ttu-id="420cf-164">. 한</span><span class="sxs-lookup"><span data-stu-id="420cf-164">.DESCRIPTION</span></span>

<span data-ttu-id="420cf-165">함수 또는 스크립트에 대 한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-165">A detailed description of the function or script.</span></span> <span data-ttu-id="420cf-166">이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-166">This keyword can be used only once in each topic.</span></span>

### <a name="parameter"></a><span data-ttu-id="420cf-167">. 변수에</span><span class="sxs-lookup"><span data-stu-id="420cf-167">.PARAMETER</span></span>

<span data-ttu-id="420cf-168">매개 변수에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-168">The description of a parameter.</span></span> <span data-ttu-id="420cf-169">`.PARAMETER`함수 또는 스크립트 구문에서 각 매개 변수에 대 한 키워드를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-169">Add a `.PARAMETER` keyword for each parameter in the function or script syntax.</span></span>

<span data-ttu-id="420cf-170">키워드와 같은 줄에 매개 변수 이름을 입력 합니다 `.PARAMETER` .</span><span class="sxs-lookup"><span data-stu-id="420cf-170">Type the parameter name on the same line as the `.PARAMETER` keyword.</span></span> <span data-ttu-id="420cf-171">키워드 뒤의 줄에 매개 변수 설명을 입력 합니다 `.PARAMETER` .</span><span class="sxs-lookup"><span data-stu-id="420cf-171">Type the parameter description on the lines following the `.PARAMETER` keyword.</span></span> <span data-ttu-id="420cf-172">Windows PowerShell은 `.PARAMETER` 줄과 다음 키워드나 주석 블록의 끝 사이에 있는 모든 텍스트를 매개 변수 설명의 일부로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-172">Windows PowerShell interprets all text between the `.PARAMETER` line and the next keyword or the end of the comment block as part of the parameter description.</span></span>
<span data-ttu-id="420cf-173">설명에는 단락 나누기가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-173">The description can include paragraph breaks.</span></span>

```
.PARAMETER  <Parameter-Name>
```

<span data-ttu-id="420cf-174">매개 변수 키워드는 주석 블록에서 순서에 관계 없이 나타날 수 있지만 함수 또는 스크립트 구문은 도움말 항목에서 매개 변수 및 해당 설명이 표시 되는 순서를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-174">The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters (and their descriptions) appear in help topic.</span></span> <span data-ttu-id="420cf-175">순서를 변경 하려면 구문을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-175">To change the order, change the syntax.</span></span>

<span data-ttu-id="420cf-176">또한 함수에 주석을 추가 하거나 매개 변수 이름 바로 앞에 스크립트 구문을 추가 하 여 매개 변수 설명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-176">You can also specify a parameter description by placing a comment in the function or script syntax immediately before the parameter variable name.</span></span> <span data-ttu-id="420cf-177">이 작업을 수행 하려면 키워드를 하나 이상 포함 하는 주석 블록만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-177">For this to work, you must also have a comment block with at least one keyword.</span></span>

<span data-ttu-id="420cf-178">구문 주석과 키워드를 모두 사용 하는 경우 `.PARAMETER` 키워드와 연결 된 설명이 `.PARAMETER` 사용 되며 구문 주석이 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-178">If you use both a syntax comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the syntax comment is ignored.</span></span>

```powershell
<#
.SYNOPSIS
    Short description here
#>
function Verb-Noun {
    [CmdletBinding()]
    param (
        # This is the same as .Parameter
        [string]$Computername
    )
    # Verb the Noun on the computer
}
```

### <a name="example"></a><span data-ttu-id="420cf-179">. 예 들어</span><span class="sxs-lookup"><span data-stu-id="420cf-179">.EXAMPLE</span></span>

<span data-ttu-id="420cf-180">함수 또는 스크립트를 사용 하 고 선택적으로 샘플 출력과 설명을 차례로 사용 하는 샘플 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-180">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="420cf-181">각 예제에 대해이 키워드를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-181">Repeat this keyword for each example.</span></span>

### <a name="inputs"></a><span data-ttu-id="420cf-182">. 내용</span><span class="sxs-lookup"><span data-stu-id="420cf-182">.INPUTS</span></span>

<span data-ttu-id="420cf-183">함수 또는 스크립트로 파이프 될 수 있는 .NET 형식의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-183">The .NET types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="420cf-184">입력 개체에 대 한 설명을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-184">You can also include a description of the input objects.</span></span>

### <a name="outputs"></a><span data-ttu-id="420cf-185">. 출력</span><span class="sxs-lookup"><span data-stu-id="420cf-185">.OUTPUTS</span></span>

<span data-ttu-id="420cf-186">Cmdlet이 반환 하는 개체의 .NET 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-186">The .NET type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="420cf-187">반환 된 개체에 대 한 설명을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-187">You can also include a description of the returned objects.</span></span>

### <a name="notes"></a><span data-ttu-id="420cf-188">. 메모란</span><span class="sxs-lookup"><span data-stu-id="420cf-188">.NOTES</span></span>

<span data-ttu-id="420cf-189">함수 또는 스크립트에 대 한 추가 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-189">Additional information about the function or script.</span></span>

### <a name="link"></a><span data-ttu-id="420cf-190">. 링크나</span><span class="sxs-lookup"><span data-stu-id="420cf-190">.LINK</span></span>

<span data-ttu-id="420cf-191">관련 항목의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-191">The name of a related topic.</span></span> <span data-ttu-id="420cf-192">값은 "의 아래 줄에 표시 됩니다. LINK "키워드와 앞에는 주석 기호를 추가 `#` 하거나 주석 블록에 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-192">The value appears on the line below the ".LINK" keyword and must be preceded by a comment symbol `#` or included in the comment block.</span></span>

<span data-ttu-id="420cf-193">`.LINK`각 관련 항목에 대해 키워드를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-193">Repeat the `.LINK` keyword for each related topic.</span></span>

<span data-ttu-id="420cf-194">이 콘텐츠는 도움말 항목의 관련 링크 섹션에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-194">This content appears in the Related Links section of the help topic.</span></span>

<span data-ttu-id="420cf-195">`.Link`키워드 콘텐츠에는 동일한 도움말 항목의 온라인 버전에 대 한 URI (Uniform Resource Identifier)가 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-195">The `.Link` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same help topic.</span></span> <span data-ttu-id="420cf-196">온라인 버전은의 **online** 매개 변수를 사용할 때 열립니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="420cf-196">The online version opens when you use the **Online** parameter of `Get-Help`.</span></span> <span data-ttu-id="420cf-197">URI는 "http" 또는 "https"로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-197">The URI must begin with "http" or "https".</span></span>

### <a name="component"></a><span data-ttu-id="420cf-198">. 구성 요소</span><span class="sxs-lookup"><span data-stu-id="420cf-198">.COMPONENT</span></span>

<span data-ttu-id="420cf-199">함수나 스크립트에서 사용 하는 기술 또는 기능의 이름 또는 관련 된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-199">The name of the technology or feature that the function or script uses, or to which it is related.</span></span> <span data-ttu-id="420cf-200">의 **구성 요소** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="420cf-200">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="role"></a><span data-ttu-id="420cf-201">. 역할</span><span class="sxs-lookup"><span data-stu-id="420cf-201">.ROLE</span></span>

<span data-ttu-id="420cf-202">도움말 항목에 대 한 사용자 역할의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-202">The name of the user role for the help topic.</span></span> <span data-ttu-id="420cf-203">의 **Role** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="420cf-203">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="functionality"></a><span data-ttu-id="420cf-204">. 기능성</span><span class="sxs-lookup"><span data-stu-id="420cf-204">.FUNCTIONALITY</span></span>

<span data-ttu-id="420cf-205">함수의 용도를 설명 하는 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-205">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="420cf-206">의 **기능** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="420cf-206">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

### <a name="forwardhelptargetname"></a><span data-ttu-id="420cf-207">. FORWARDHELPTARGETNAME</span><span class="sxs-lookup"><span data-stu-id="420cf-207">.FORWARDHELPTARGETNAME</span></span>

<span data-ttu-id="420cf-208">지정 된 명령에 대 한 도움말 항목으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-208">Redirects to the help topic for the specified command.</span></span> <span data-ttu-id="420cf-209">함수, 스크립트, cmdlet 또는 공급자에 대 한 도움말 항목을 포함 하 여 사용자를 도움말 항목으로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-209">You can redirect users to any help topic, including help topics for a function, script, cmdlet, or provider.</span></span>

```powershell
# .FORWARDHELPTARGETNAME <Command-Name>
```

### <a name="forwardhelpcategory"></a><span data-ttu-id="420cf-210">. FORWARDHELPCATEGORY</span><span class="sxs-lookup"><span data-stu-id="420cf-210">.FORWARDHELPCATEGORY</span></span>

<span data-ttu-id="420cf-211">항목의 도움말 범주를 지정 합니다 `.ForwardHelpTargetName` .</span><span class="sxs-lookup"><span data-stu-id="420cf-211">Specifies the help category of the item in `.ForwardHelpTargetName`.</span></span> <span data-ttu-id="420cf-212">유효한 값은,,,,,,,,,, `Alias` `Cmdlet` `HelpFile` `Function` `Provider` `General` `FAQ` `Glossary` `ScriptCommand` `ExternalScript` `Filter` 또는 `All` 입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-212">Valid values are `Alias`, `Cmdlet`, `HelpFile`, `Function`, `Provider`, `General`, `FAQ`, `Glossary`, `ScriptCommand`, `ExternalScript`, `Filter`, or `All`.</span></span> <span data-ttu-id="420cf-213">동일한 이름을 가진 명령이 있는 경우 충돌을 방지 하려면이 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-213">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

```powershell
# .FORWARDHELPCATEGORY <Category>
```

### <a name="remotehelprunspace"></a><span data-ttu-id="420cf-214">. REMOTEHELPRUNSPACE</span><span class="sxs-lookup"><span data-stu-id="420cf-214">.REMOTEHELPRUNSPACE</span></span>

<span data-ttu-id="420cf-215">도움말 항목을 포함 하는 세션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-215">Specifies a session that contains the help topic.</span></span> <span data-ttu-id="420cf-216">**PSSession** 개체를 포함 하는 변수를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-216">Enter a variable that contains a **PSSession** object.</span></span> <span data-ttu-id="420cf-217">이 키워드는 [내보내기 PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet에서 내보낸 명령에 대 한 도움말 항목을 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-217">This keyword is used by the [Export-PSSession](xref:Microsoft.PowerShell.Utility.Export-PSSession) cmdlet to find the help topics for the exported commands.</span></span>

```powershell
# .REMOTEHELPRUNSPACE <PSSession-variable>
```

### <a name="externalhelp"></a><span data-ttu-id="420cf-218">. .EXTERNALHELP 설명을</span><span class="sxs-lookup"><span data-stu-id="420cf-218">.EXTERNALHELP</span></span>

<span data-ttu-id="420cf-219">스크립트나 함수에 대 한 XML 기반 도움말 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-219">Specifies an XML-based help file for the script or function.</span></span>

```powershell
# .EXTERNALHELP <XML Help File>
```

<span data-ttu-id="420cf-220">`.ExternalHelp`키워드는 함수 또는 스크립트가 XML 파일에 설명 되어 있는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-220">The `.ExternalHelp` keyword is required when a function or script is documented in XML files.</span></span> <span data-ttu-id="420cf-221">이 키워드가 없으면 `Get-Help` 함수 또는 스크립트에 대 한 XML 기반 도움말 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-221">Without this keyword, `Get-Help` cannot find the XML-based help file for the function or script.</span></span>

<span data-ttu-id="420cf-222">`.ExternalHelp`키워드는 다른 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-222">The `.ExternalHelp` keyword takes precedence over other comment-based help keywords.</span></span> <span data-ttu-id="420cf-223">`.ExternalHelp`가 있는 경우는 `Get-Help` 키워드의 값과 일치 하는 도움말 항목을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다 `.ExternalHelp` .</span><span class="sxs-lookup"><span data-stu-id="420cf-223">If `.ExternalHelp` is present, `Get-Help` does not display comment-based help, even if it cannot find a help topic that matches the value of the `.ExternalHelp` keyword.</span></span>

<span data-ttu-id="420cf-224">모듈에서 함수를 내보내는 경우 키워드의 값을 `.ExternalHelp` 경로 없이 파일 이름으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-224">If the function is exported by a module, set the value of the `.ExternalHelp` keyword to a filename without a path.</span></span> <span data-ttu-id="420cf-225">`Get-Help` 모듈 디렉터리의 언어별 하위 디렉터리에서 지정 된 파일 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-225">`Get-Help` looks for the specified file name in a language-specific subdirectory of the module directory.</span></span> <span data-ttu-id="420cf-226">함수에 대 한 XML 기반 도움말 파일의 이름에 대 한 요구 사항은 없지만 다음 형식을 사용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-226">There are no requirements for the name of the XML-based help file for a function, but a best practice is to use the following format:</span></span>

```
<ScriptModule.psm1>-help.xml
```

<span data-ttu-id="420cf-227">함수가 모듈에 포함 되지 않은 경우 XML 기반 도움말 파일에 대 한 경로를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-227">If the function is not included in a module, include a path to the XML-based help file.</span></span> <span data-ttu-id="420cf-228">값에 경로가 포함 되 고 경로에 UI 문화권별 하위 디렉터리가 포함 된 경우는 `Get-Help` 모듈 디렉터리에서와 마찬가지로 Windows에 설정 된 언어 대체 표준에 따라 스크립트나 함수 이름을 사용 하 여 XML 파일에 대해 재귀적으로 하위 디렉터리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-228">If the value includes a path and the path contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does in a module directory.</span></span>

<span data-ttu-id="420cf-229">Cmdlet 도움말 XML 기반 도움말 파일 형식에 대 한 자세한 내용은 [Cmdlet 도움말을 작성 하는 방법](/powershell/scripting/developer/help/writing-comment-based-help-topics)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="420cf-229">For more information about the cmdlet help XML-based help file format, see [How to Write Cmdlet Help](/powershell/scripting/developer/help/writing-comment-based-help-topics).</span></span>

## <a name="autogenerated-content"></a><span data-ttu-id="420cf-230">자동으로 생성 되는 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="420cf-230">Autogenerated content</span></span>

<span data-ttu-id="420cf-231">이름, 구문, 매개 변수 목록, 매개 변수 특성 테이블, 일반 매개 변수 및 설명이 cmdlet에 의해 자동으로 생성 됩니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="420cf-231">The name, syntax, parameter list, parameter attribute table, common parameters, and remarks are automatically generated by the `Get-Help` cmdlet.</span></span>

### <a name="name"></a><span data-ttu-id="420cf-232">Name</span><span class="sxs-lookup"><span data-stu-id="420cf-232">Name</span></span>

<span data-ttu-id="420cf-233">함수 도움말 항목의 **name** 섹션은 함수 구문의 함수 이름에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-233">The **Name** section of a function help topic is taken from the function name in the function syntax.</span></span> <span data-ttu-id="420cf-234">스크립트 파일 이름에서 스크립트 도움말 항목의 **이름을** 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-234">The **Name** of a script help topic is taken from the script filename.</span></span> <span data-ttu-id="420cf-235">이름 또는 해당 대문자 표시를 변경 하려면 함수 구문이 나 스크립트 파일 이름을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-235">To change the name or its capitalization, change the function syntax or the script filename.</span></span>

### <a name="syntax"></a><span data-ttu-id="420cf-236">구문</span><span class="sxs-lookup"><span data-stu-id="420cf-236">Syntax</span></span>

<span data-ttu-id="420cf-237">도움말 항목의 **구문** 섹션은 함수 또는 스크립트 구문에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-237">The **Syntax** section of the help topic is generated from the function or script syntax.</span></span> <span data-ttu-id="420cf-238">도움말 항목 구문 (예: .NET 형식의 매개 변수)에 세부 정보를 추가 하려면 구문에 세부 정보를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-238">To add detail to the help topic syntax, such as the .NET type of a parameter, add the detail to the syntax.</span></span> <span data-ttu-id="420cf-239">매개 변수 형식을 지정 하지 않으면 **개체** 형식이 기본값으로 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-239">If you do not specify a parameter type, the **Object** type is inserted as the default value.</span></span>

### <a name="parameter-list"></a><span data-ttu-id="420cf-240">매개 변수 목록</span><span class="sxs-lookup"><span data-stu-id="420cf-240">Parameter List</span></span>

<span data-ttu-id="420cf-241">도움말 항목의 매개 변수 목록은 함수 또는 스크립트 구문과 키워드를 사용 하 여 추가 하는 설명에서 생성 됩니다 `.Parameter` .</span><span class="sxs-lookup"><span data-stu-id="420cf-241">The parameter list in the help topic is generated from the function or script syntax and from the descriptions that you add by using the `.Parameter` keyword.</span></span> <span data-ttu-id="420cf-242">함수 매개 변수는 함수 또는 스크립트 구문에 표시 되는 것과 동일한 순서로 도움말 항목의 **매개 변수** 섹션에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-242">The function parameters appear in the **Parameters** section of the help topic in the same order that they appear in the function or script syntax.</span></span> <span data-ttu-id="420cf-243">매개 변수 이름의 철자 및 대/소문자도 구문에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-243">The spelling and capitalization of parameter names is also taken from the syntax.</span></span> <span data-ttu-id="420cf-244">키워드에 지정 된 매개 변수 이름의 영향을 받지 않습니다 `.Parameter` .</span><span class="sxs-lookup"><span data-stu-id="420cf-244">It is not affected by the parameter name specified by the `.Parameter` keyword.</span></span>

### <a name="common-parameters"></a><span data-ttu-id="420cf-245">일반 매개 변수</span><span class="sxs-lookup"><span data-stu-id="420cf-245">Common Parameters</span></span>

<span data-ttu-id="420cf-246">**일반 매개 변수** 는 영향을 주지 않는 경우에도 도움말 항목의 구문 및 매개 변수 목록에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-246">The **Common parameters** are added to the syntax and parameter list of the help topic, even if they have no effect.</span></span> <span data-ttu-id="420cf-247">일반 매개 변수에 대 한 자세한 내용은 [about_CommonParameters](about_CommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="420cf-247">For more information about the common parameters, see [about_CommonParameters](about_CommonParameters.md).</span></span>

### <a name="parameter-attribute-table"></a><span data-ttu-id="420cf-248">Parameter 특성 표</span><span class="sxs-lookup"><span data-stu-id="420cf-248">Parameter Attribute Table</span></span>

<span data-ttu-id="420cf-249">`Get-Help` 의 **Full** 또는 **parameter** 매개 변수를 사용할 때 표시 되는 매개 변수 특성의 테이블을 생성 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="420cf-249">`Get-Help` generates the table of parameter attributes that appears when you use the **Full** or **Parameter** parameter of `Get-Help`.</span></span> <span data-ttu-id="420cf-250">**필수**, **위치** 및 **기본** 값 특성의 값은 함수 또는 스크립트 구문에서 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-250">The value of the **Required**, **Position**, and **Default** value attributes is taken from the function or script syntax.</span></span>

<span data-ttu-id="420cf-251">함수 또는 스크립트에서 정의 된 경우에도 기본값 및 **와일드 카드 문자 허용** 값은 매개 변수 특성 테이블에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-251">Default values and a value for **Accept Wildcard characters** do not appear in the parameter attribute table even when they are defined in the function or script.</span></span> <span data-ttu-id="420cf-252">사용자를 돕기 위해 매개 변수 설명에이 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-252">To help users, provide this information in the parameter description.</span></span>

### <a name="remarks"></a><span data-ttu-id="420cf-253">설명</span><span class="sxs-lookup"><span data-stu-id="420cf-253">Remarks</span></span>

<span data-ttu-id="420cf-254">도움말 항목의 **설명** 섹션은 함수 또는 스크립트 이름에서 자동으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-254">The **Remarks** section of the help topic is automatically generated from the function or script name.</span></span> <span data-ttu-id="420cf-255">콘텐츠를 변경 하거나 영향을 줄 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-255">You cannot change or affect its content.</span></span>

## <a name="examples"></a><span data-ttu-id="420cf-256">예</span><span class="sxs-lookup"><span data-stu-id="420cf-256">Examples</span></span>

### <a name="comment-based-help-for-a-function"></a><span data-ttu-id="420cf-257">함수에 대 한 주석 기반 도움말</span><span class="sxs-lookup"><span data-stu-id="420cf-257">Comment-based Help for a Function</span></span>

<span data-ttu-id="420cf-258">다음 샘플 함수는 주석 기반 도움말을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-258">The following sample function includes comment-based help:</span></span>

```powershell
function Add-Extension
{
param ([string]$Name,[string]$Extension = "txt")
$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name.
Takes any strings for the file name or extension.

.PARAMETER Name
Specifies the file name.

.PARAMETER Extension
Specifies the extension. "Txt" is the default.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension
or file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

<span data-ttu-id="420cf-259">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-259">The results are as follows:</span></span>

```powershell
Get-Help -Name "Add-Extension" -Full
```

```Output
NAME

Add-Extension

SYNOPSIS

Adds a file name extension to a supplied name.

SYNTAX

Add-Extension [[-Name] <String>] [[-Extension] <String>]
[<CommonParameters>]

DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

PARAMETERS

-Name
Specifies the file name.

Required?                    false
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-Extension
Specifies the extension. "Txt" is the default.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type
"get-help about_commonparameters".

INPUTS
None. You cannot pipe objects to Add-Extension.

OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

Example 1

PS> extension -name "File"
File.txt

Example 2

PS> extension -name "File" -extension "doc"
File.doc

Example 3

PS> extension "File" "doc"
File.doc

RELATED LINKS

http://www.fabrikam.com/extension.html
Set-Item
```

### <a name="parameter-descriptions-in-function-syntax"></a><span data-ttu-id="420cf-260">함수 구문의 매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="420cf-260">Parameter Descriptions in Function Syntax</span></span>

<span data-ttu-id="420cf-261">이 예제는 매개 변수 설명이 함수 구문에 삽입 된다는 점을 제외 하 고는 이전 예제와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-261">This example is the same as the previous one, except that the parameter descriptions are inserted in the function syntax.</span></span> <span data-ttu-id="420cf-262">이 형식은 설명이 간단한 경우에 가장 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-262">This format is most useful when the descriptions are brief.</span></span>

```powershell
function Add-Extension
{
param
(

[string]
#Specifies the file name.
$name,

[string]
#Specifies the file name extension. "Txt" is the default.
$extension = "txt"
)

$name = $name + "." + $extension
$name

<#
.SYNOPSIS

Adds a file name extension to a supplied name.

.DESCRIPTION

Adds a file name extension to a supplied name. Takes any strings for the
file name or extension.

.INPUTS

None. You cannot pipe objects to Add-Extension.

.OUTPUTS

System.String. Add-Extension returns a string with the extension or
file name.

.EXAMPLE

PS> extension -name "File"
File.txt

.EXAMPLE

PS> extension -name "File" -extension "doc"
File.doc

.EXAMPLE

PS> extension "File" "doc"
File.doc

.LINK

http://www.fabrikam.com/extension.html

.LINK

Set-Item
#>
}
```

### <a name="comment-based-help-for-a-script"></a><span data-ttu-id="420cf-263">스크립트에 대 한 주석 기반 도움말</span><span class="sxs-lookup"><span data-stu-id="420cf-263">Comment-based Help for a Script</span></span>

<span data-ttu-id="420cf-264">다음 샘플 스크립트는 주석 기반 도움말을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-264">The following sample script includes comment-based help.</span></span> <span data-ttu-id="420cf-265">Closing 문과 문 사이에 빈 줄을 확인 `#>` `Param` 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-265">Notice the blank lines between the closing `#>` and the `Param` statement.</span></span> <span data-ttu-id="420cf-266">문이 없는 스크립트에서 `Param` 도움말 항목의 마지막 주석과 첫 번째 함수 선언 사이에는 두 개 이상의 빈 줄이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-266">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the help topic and the first function declaration.</span></span> <span data-ttu-id="420cf-267">이러한 빈 줄이 없으면에서 `Get-Help` 도움말 항목을 스크립트가 아니라 함수와 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-267">Without these blank lines, `Get-Help` associates the help topic with the function, not the script.</span></span>

```powershell
<#
.SYNOPSIS

Performs monthly data updates.

.DESCRIPTION

The Update-Month.ps1 script updates the registry with new data generated
during the past month and generates a report.

.PARAMETER InputPath
Specifies the path to the CSV-based input file.

.PARAMETER OutputPath
Specifies the name and path for the CSV-based output file. By default,
MonthlyUpdates.ps1 generates a name from the date and time it runs, and
saves the output in the local directory.

.INPUTS

None. You cannot pipe objects to Update-Month.ps1.

.OUTPUTS

None. Update-Month.ps1 does not generate any output.

.EXAMPLE

PS> .\Update-Month.ps1

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

.EXAMPLE

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath `
C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
...
```

<span data-ttu-id="420cf-268">다음 명령은 스크립트 도움말을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-268">The following command gets the script help.</span></span> <span data-ttu-id="420cf-269">스크립트는 환경 변수에 나열 된 디렉터리에 있지 않기 때문에 스크립트 `$env:Path` `Get-Help` 도움말을 가져오는 명령은 스크립트 경로를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-269">Because the script is not in a directory that is listed in the `$env:Path` environment variable, the `Get-Help` command that gets the script help must specify the script path.</span></span>

```powershell
Get-Help -Path .\update-month.ps1 -Full
```

```Output
# NAME

C:\ps-test\Update-Month.ps1

# SYNOPSIS

Performs monthly data updates.

# SYNTAX

C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
<String>] [<CommonParameters>]

# DESCRIPTION

The Update-Month.ps1 script updates the registry with new data
generated during the past month and generates a report.

# PARAMETERS

-InputPath
Specifies the path to the CSV-based input file.

Required?                    true
Position?                    0
Default value
Accept pipeline input?       false
Accept wildcard characters?

-OutputPath
Specifies the name and path for the CSV-based output file. By
default, MonthlyUpdates.ps1 generates a name from the date
and time it runs, and saves the output in the local directory.

Required?                    false
Position?                    1
Default value
Accept pipeline input?       false
Accept wildcard characters?

<CommonParameters>
This cmdlet supports the common parameters: -Verbose, -Debug,
-ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
-OutBuffer and -OutVariable. For more information, type,
"get-help about_commonparameters".

# INPUTS

None. You cannot pipe objects to Update-Month.ps1.

# OUTPUTS

None. Update-Month.ps1 does not generate any output.

Example 1

PS> .\Update-Month.ps1

Example 2

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

Example 3

PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
C:\Reports\2009\January.csv

# RELATED LINKS
```

### <a name="redirecting-to-an-xml-file"></a><span data-ttu-id="420cf-270">XML 파일로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="420cf-270">Redirecting to an XML File</span></span>

<span data-ttu-id="420cf-271">함수 및 스크립트에 대 한 XML 기반 도움말 항목을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-271">You can write XML-based help topics for functions and scripts.</span></span> <span data-ttu-id="420cf-272">주석 기반 도움말을 보다 쉽게 구현할 수 있지만 업데이트할 수 있는 도움말에는 XML 기반 도움말이 필요 하며 여러 언어로 된 도움말 항목을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-272">Although comment-based help is easier to implement, XML-based help is required for Updatable Help and to provide help topics in multiple languages.</span></span>

<span data-ttu-id="420cf-273">다음 예에서는 Update-Month.ps1 스크립트의 처음 몇 줄을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-273">The following example shows the first few lines of the Update-Month.ps1 script.</span></span>
<span data-ttu-id="420cf-274">스크립트는 키워드를 사용 하 여 `.ExternalHelp` 스크립트에 대 한 XML 기반 도움말 항목의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-274">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based help topic for the script.</span></span>

<span data-ttu-id="420cf-275">키워드 값은 `.ExternalHelp` 키워드와 같은 줄에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-275">Note that the value of the `.ExternalHelp` keyword appears on the same line as the keyword.</span></span> <span data-ttu-id="420cf-276">다른 모든 배치가 비효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-276">Any other placement is ineffective.</span></span>

```powershell
# .ExternalHelp C:\MyScripts\Update-Month-Help.xml

param ([string]$InputPath, [string]$OutPutPath)
function Get-Data { }
...
```

<span data-ttu-id="420cf-277">다음 예에서는 `.ExternalHelp` 함수에 있는 키워드의 세 가지 유효한 위치를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-277">The following examples show three valid placements of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
# .ExternalHelp C:\ps-test\Add-Extension.xml

param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

```powershell
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name

# .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

```powershell
# .ExternalHelp C:\ps-test\Add-Extension.xml
function Add-Extension
{
param ([string] $name, [string]$extension = "txt")
$name = $name + "." + $extension
$name
}
```

### <a name="redirecting-to-a-different-help-topic"></a><span data-ttu-id="420cf-278">다른 도움말 항목으로 리디렉션</span><span class="sxs-lookup"><span data-stu-id="420cf-278">Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="420cf-279">다음 코드는 한 번에 하나의 도움말 텍스트 화면을 표시 하는 PowerShell의 기본 제공 도움말 함수 시작 부분에서 발췌 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-279">The following code is an excerpt from the beginning of the built-in help function in PowerShell, which displays one screen of help text at a time.</span></span>
<span data-ttu-id="420cf-280">Cmdlet에 대 한 도움말 항목에서는 `Get-Help` 도움말 함수를 설명 하므로 도움말 함수는 및 키워드를 사용 하 여 `.ForwardHelpTargetName` `.ForwardHelpCategory` 사용자를 `Get-Help` cmdlet 도움말 항목으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-280">Because the help topic for the `Get-Help` cmdlet describes the help function, the help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the `Get-Help` cmdlet help topic.</span></span>

```powershell
function help
{

<#
.FORWARDHELPTARGETNAME Get-Help
.FORWARDHELPCATEGORY Cmdlet
#>
[CmdletBinding(DefaultParameterSetName='AllUsersView')]
param(
[Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
[System.String]
${Name},
...
```

<span data-ttu-id="420cf-281">다음 명령은이 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="420cf-281">The following command uses this feature:</span></span>

```powershell
Get-Help -Name help
```

```Output
NAME

Get-Help

SYNOPSIS

Displays information about PowerShell cmdlets and concepts.
...
```

## <a name="see-also"></a><span data-ttu-id="420cf-282">참고 항목</span><span class="sxs-lookup"><span data-stu-id="420cf-282">See also</span></span>

[<span data-ttu-id="420cf-283">about_Functions</span><span class="sxs-lookup"><span data-stu-id="420cf-283">about_Functions</span></span>](about_Functions.md)

[<span data-ttu-id="420cf-284">about_Functions_Advanced_Parameters</span><span class="sxs-lookup"><span data-stu-id="420cf-284">about_Functions_Advanced_Parameters</span></span>](about_Functions_Advanced_Parameters.md)

[<span data-ttu-id="420cf-285">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="420cf-285">about_Scripts</span></span>](about_Scripts.md)

[<span data-ttu-id="420cf-286">Cmdlet 도움말을 작성 하는 방법</span><span class="sxs-lookup"><span data-stu-id="420cf-286">How to Write Cmdlet Help</span></span>](https://go.microsoft.com/fwlink/?LinkID=123415)
