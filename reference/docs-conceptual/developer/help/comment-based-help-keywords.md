---
title: 설명 기반 도움말 키워드
ms.date: 06/09/2020
ms.openlocfilehash: fb737c19d7b7f4d003af3ba36bb396bac52d94e7
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893155"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="07eff-102">설명 기반 도움말 키워드</span><span class="sxs-lookup"><span data-stu-id="07eff-102">Comment-Based Help Keywords</span></span>

<span data-ttu-id="07eff-103">이 항목에서는 주석 기반 도움말의 키워드를 나열 하 고 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-103">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="07eff-104">주석 기반 도움말의 키워드</span><span class="sxs-lookup"><span data-stu-id="07eff-104">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="07eff-105">다음은 유효한 주석 기반 도움말 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-105">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="07eff-106">이러한 항목은 일반적으로 원하는 용도와 함께 도움말 항목에 표시 되는 순서 대로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-106">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="07eff-107">이러한 키워드는 주석 기반 도움말에서 순서에 관계 없이 나타날 수 있으며 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-107">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="07eff-108">`.EXTERNALHELP`키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-108">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="07eff-109">`.EXTERNALHELP`가 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-109">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="07eff-110">. 개요</span><span class="sxs-lookup"><span data-stu-id="07eff-110">.SYNOPSIS</span></span>

<span data-ttu-id="07eff-111">함수 또는 스크립트에 대 한 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-111">A brief description of the function or script.</span></span> <span data-ttu-id="07eff-112">이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-112">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="07eff-113">. 한</span><span class="sxs-lookup"><span data-stu-id="07eff-113">.DESCRIPTION</span></span>

<span data-ttu-id="07eff-114">함수 또는 스크립트에 대 한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-114">A detailed description of the function or script.</span></span> <span data-ttu-id="07eff-115">이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-115">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="07eff-116">. 변수에\<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="07eff-116">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="07eff-117">매개 변수에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-117">The description of a parameter.</span></span> <span data-ttu-id="07eff-118">`.PARAMETER`함수 또는 스크립트의 각 매개 변수에 대 한 키워드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-118">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="07eff-119">`.PARAMETER`키워드는 주석 블록에서 임의의 순서로 표시 될 수 있지만 매개 변수가 문이나 함수 선언에 표시 되는 순서에 `Param` 따라 매개 변수가 도움말 항목에 표시 되는 순서가 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-119">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="07eff-120">도움말 항목의 매개 변수 순서를 변경 하려면 문이나 함수 선언에서 매개 변수의 순서를 변경 `Param` 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-120">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="07eff-121">`Param`문에 주석을 매개 변수 이름 바로 앞에 배치 하 여 매개 변수 설명을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-121">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="07eff-122">문 주석과 키워드를 모두 사용 하는 경우 `Param` `.PARAMETER` 키워드와 연결 된 설명이 사용 되 `.PARAMETER` 고 `Param` 문 주석은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-122">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="07eff-123">. 예 들어</span><span class="sxs-lookup"><span data-stu-id="07eff-123">.EXAMPLE</span></span>

<span data-ttu-id="07eff-124">함수 또는 스크립트를 사용 하 고 선택적으로 샘플 출력과 설명을 차례로 사용 하는 샘플 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-124">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="07eff-125">각 예제에 대해이 키워드를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-125">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="07eff-126">. 내용</span><span class="sxs-lookup"><span data-stu-id="07eff-126">.INPUTS</span></span>

<span data-ttu-id="07eff-127">함수 또는 스크립트로 파이프 될 수 있는 개체의 Microsoft .NET 프레임 워크 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-127">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="07eff-128">입력 개체에 대 한 설명을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-128">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="07eff-129">. 출력</span><span class="sxs-lookup"><span data-stu-id="07eff-129">.OUTPUTS</span></span>

<span data-ttu-id="07eff-130">Cmdlet이 반환 하는 개체의 .NET Framework 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-130">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="07eff-131">반환 된 개체에 대 한 설명을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-131">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="07eff-132">. 메모란</span><span class="sxs-lookup"><span data-stu-id="07eff-132">.NOTES</span></span>

<span data-ttu-id="07eff-133">함수 또는 스크립트에 대 한 추가 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-133">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="07eff-134">. 링크나</span><span class="sxs-lookup"><span data-stu-id="07eff-134">.LINK</span></span>

<span data-ttu-id="07eff-135">관련 항목의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-135">The name of a related topic.</span></span> <span data-ttu-id="07eff-136">관련 된 각 항목에 대해이 키워드를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-136">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="07eff-137">이 콘텐츠는 도움말 항목의 관련 링크 섹션에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-137">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="07eff-138">`.LINK`키워드 콘텐츠에는 동일한 도움말 항목의 온라인 버전에 대 한 URI (Uniform Resource Identifier)가 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-138">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="07eff-139">의 매개 변수를 사용할 때 온라인 버전이 열립니다 `Online` `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="07eff-139">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="07eff-140">URI는 "http" 또는 "https"로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-140">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="07eff-141">. 구성 요소</span><span class="sxs-lookup"><span data-stu-id="07eff-141">.COMPONENT</span></span>

<span data-ttu-id="07eff-142">함수나 스크립트에서 사용 하는 기술 또는 기능의 이름 또는 관련 된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-142">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="07eff-143">의 **구성 요소** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="07eff-143">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="07eff-144">. 역할</span><span class="sxs-lookup"><span data-stu-id="07eff-144">.Role</span></span>

<span data-ttu-id="07eff-145">도움말 항목에 대 한 사용자 역할의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-145">The name of the user role for the help topic.</span></span> <span data-ttu-id="07eff-146">의 **Role** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="07eff-146">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="07eff-147">. 기능성</span><span class="sxs-lookup"><span data-stu-id="07eff-147">.FUNCTIONALITY</span></span>

<span data-ttu-id="07eff-148">함수의 용도를 설명 하는 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-148">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="07eff-149">의 **기능** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="07eff-149">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="07eff-150">. FORWARDHELPTARGETNAME\<Command-Name></span><span class="sxs-lookup"><span data-stu-id="07eff-150">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="07eff-151">지정 된 명령에 대 한 도움말 항목으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-151">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="07eff-152">함수, 스크립트, cmdlet 또는 공급자에 대 한 도움말 항목을 포함 하 여 사용자를 도움말 항목으로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-152">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="07eff-153">. FORWARDHELPCATEGORY\<Category></span><span class="sxs-lookup"><span data-stu-id="07eff-153">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="07eff-154">항목의 도움말 범주를 지정 합니다 `.FORWARDHELPTARGETNAME` .</span><span class="sxs-lookup"><span data-stu-id="07eff-154">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="07eff-155">동일한 이름을 가진 명령이 있는 경우 충돌을 방지 하려면이 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-155">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="07eff-156">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-156">Valid values are:</span></span>

- <span data-ttu-id="07eff-157">Alias</span><span class="sxs-lookup"><span data-stu-id="07eff-157">Alias</span></span>
- <span data-ttu-id="07eff-158">cmdlet</span><span class="sxs-lookup"><span data-stu-id="07eff-158">Cmdlet</span></span>
- <span data-ttu-id="07eff-159">HelpFile</span><span class="sxs-lookup"><span data-stu-id="07eff-159">HelpFile</span></span>
- <span data-ttu-id="07eff-160">함수</span><span class="sxs-lookup"><span data-stu-id="07eff-160">Function</span></span>
- <span data-ttu-id="07eff-161">공급자</span><span class="sxs-lookup"><span data-stu-id="07eff-161">Provider</span></span>
- <span data-ttu-id="07eff-162">일반</span><span class="sxs-lookup"><span data-stu-id="07eff-162">General</span></span>
- <span data-ttu-id="07eff-163">FAQ</span><span class="sxs-lookup"><span data-stu-id="07eff-163">FAQ</span></span>
- <span data-ttu-id="07eff-164">용어</span><span class="sxs-lookup"><span data-stu-id="07eff-164">Glossary</span></span>
- <span data-ttu-id="07eff-165">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="07eff-165">ScriptCommand</span></span>
- <span data-ttu-id="07eff-166">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="07eff-166">ExternalScript</span></span>
- <span data-ttu-id="07eff-167">필터</span><span class="sxs-lookup"><span data-stu-id="07eff-167">Filter</span></span>
- <span data-ttu-id="07eff-168">모두</span><span class="sxs-lookup"><span data-stu-id="07eff-168">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="07eff-169">. REMOTEHELPRUNSPACE\<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="07eff-169">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="07eff-170">도움말 항목을 포함 하는 세션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-170">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="07eff-171">PSSession이 포함 된 변수를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-171">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="07eff-172">이 키워드는 `Export-PSSession` cmdlet에서 내보낸 명령에 대 한 도움말 항목을 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-172">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="07eff-173">. .EXTERNALHELP 설명을\<XML Help File></span><span class="sxs-lookup"><span data-stu-id="07eff-173">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="07eff-174">스크립트나 함수에 대 한 XML 기반 도움말 파일의 경로 및/또는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-174">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="07eff-175">`.EXTERNALHELP`키워드는 XML 기반 파일에서 스크립트나 함수에 대 한 도움말을 가져오기 위해 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-175">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="07eff-176">`.EXTERNALHELP`키워드는 스크립트나 함수에 대 한 XML 기반 도움말 파일을 사용 하는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-176">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="07eff-177">없는 경우 `Get-Help` 는 함수 또는 스크립트에 대 한 도움말 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-177">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="07eff-178">`.EXTERNALHELP`키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-178">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="07eff-179">`.EXTERNALHELP`가 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-179">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="07eff-180">스크립트 모듈에서 함수를 내보내는 경우 값은 `.EXTERNALHELP` 경로 없이 파일 이름 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-180">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="07eff-181">`Get-Help`모듈 디렉터리의 로캘별 하위 디렉터리에서 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-181">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="07eff-182">파일 이름에 대 한 요구 사항은 없지만 파일 이름 형식를 사용 하는 것이 가장 좋습니다 `<ScriptModule>.psm1-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="07eff-182">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="07eff-183">함수가 모듈과 연결 되어 있지 않으면 키워드의 값에 경로 및 파일 이름을 포함 `.EXTERNALHELP` 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-183">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="07eff-184">XML 파일에 대 한 지정 된 경로에 UI 문화권별 하위 디렉터리가 포함 된 경우는 `Get-Help` 모든 xml 기반 도움말 항목과 마찬가지로 Windows에 설정 된 언어 대체 표준에 따라 스크립트나 함수 이름을 사용 하 여 하위 디렉터리에서 xml 파일을 재귀적으로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="07eff-184">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="07eff-185">Cmdlet 도움말 XML 기반 도움말 파일 형식에 대 한 자세한 내용은 [Windows PowerShell Cmdlet 도움말 작성](./writing-help-for-windows-powershell-cmdlets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="07eff-185">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
