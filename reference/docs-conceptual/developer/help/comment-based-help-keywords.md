---
ms.date: 06/09/2020
ms.topic: reference
title: 설명 기반 도움말 키워드
description: 설명 기반 도움말 키워드
ms.openlocfilehash: d87dde8700813767f6c09cfce70ed06c7964ebc7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645481"
---
# <a name="comment-based-help-keywords"></a><span data-ttu-id="6f9a6-103">설명 기반 도움말 키워드</span><span class="sxs-lookup"><span data-stu-id="6f9a6-103">Comment-Based Help Keywords</span></span>

<span data-ttu-id="6f9a6-104">이 항목에서는 주석 기반 도움말의 키워드를 나열 하 고 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-104">This topic lists and describes the keywords in comment-based help.</span></span>

## <a name="keywords-in-comment-based-help"></a><span data-ttu-id="6f9a6-105">Comment-Based 도움말의 키워드</span><span class="sxs-lookup"><span data-stu-id="6f9a6-105">Keywords in Comment-Based Help</span></span>

<span data-ttu-id="6f9a6-106">다음은 유효한 주석 기반 도움말 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-106">The following are valid comment-based Help keywords.</span></span> <span data-ttu-id="6f9a6-107">이러한 항목은 일반적으로 원하는 용도와 함께 도움말 항목에 표시 되는 순서 대로 나열 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-107">They are listed in the order in which they typically appear in a Help topic along with their intended use.</span></span> <span data-ttu-id="6f9a6-108">이러한 키워드는 주석 기반 도움말에서 순서에 관계 없이 나타날 수 있으며 대/소문자를 구분 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-108">These keywords can appear in any order in the comment-based Help, and they are not case-sensitive.</span></span>

<span data-ttu-id="6f9a6-109">`.EXTERNALHELP`키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-109">Note that the `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span>
<span data-ttu-id="6f9a6-110">`.EXTERNALHELP`가 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-110">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6f9a6-111">. 개요</span><span class="sxs-lookup"><span data-stu-id="6f9a6-111">.SYNOPSIS</span></span>

<span data-ttu-id="6f9a6-112">함수 또는 스크립트에 대 한 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-112">A brief description of the function or script.</span></span> <span data-ttu-id="6f9a6-113">이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-113">This keyword can be used only once in each topic.</span></span>

## <a name="description"></a><span data-ttu-id="6f9a6-114">. 한</span><span class="sxs-lookup"><span data-stu-id="6f9a6-114">.DESCRIPTION</span></span>

<span data-ttu-id="6f9a6-115">함수 또는 스크립트에 대 한 자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-115">A detailed description of the function or script.</span></span> <span data-ttu-id="6f9a6-116">이 키워드는 각 항목에서 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-116">This keyword can be used only once in each topic.</span></span>

## <a name="parameter-parameter-name"></a><span data-ttu-id="6f9a6-117">. 변수에 \<Parameter-Name></span><span class="sxs-lookup"><span data-stu-id="6f9a6-117">.PARAMETER \<Parameter-Name></span></span>

<span data-ttu-id="6f9a6-118">매개 변수에 대 한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-118">The description of a parameter.</span></span> <span data-ttu-id="6f9a6-119">`.PARAMETER`함수 또는 스크립트의 각 매개 변수에 대 한 키워드를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-119">You can include a `.PARAMETER` keyword for each parameter in the function or script.</span></span>

<span data-ttu-id="6f9a6-120">`.PARAMETER`키워드는 주석 블록에서 임의의 순서로 표시 될 수 있지만 매개 변수가 문이나 함수 선언에 표시 되는 순서에 `Param` 따라 매개 변수가 도움말 항목에 표시 되는 순서가 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-120">The `.PARAMETER` keywords can appear in any order in the comment block, but the order in which the parameters appear in the `Param` statement or function declaration determines the order in which the parameters appear in Help topic.</span></span> <span data-ttu-id="6f9a6-121">도움말 항목의 매개 변수 순서를 변경 하려면 문이나 함수 선언에서 매개 변수의 순서를 변경 `Param` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-121">To change the order of parameters in the Help topic, change the order of the parameters in the `Param` statement or function declaration.</span></span>

<span data-ttu-id="6f9a6-122">`Param`문에 주석을 매개 변수 이름 바로 앞에 배치 하 여 매개 변수 설명을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-122">You can also specify a parameter description by placing a comment in the `Param` statement immediately before the parameter variable name.</span></span> <span data-ttu-id="6f9a6-123">문 주석과 키워드를 모두 사용 하는 경우 `Param` `.PARAMETER` 키워드와 연결 된 설명이 사용 되 `.PARAMETER` 고 `Param` 문 주석은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-123">If you use both a `Param` statement comment and a `.PARAMETER` keyword, the description associated with the `.PARAMETER` keyword is used, and the `Param` statement comment is ignored.</span></span>

## <a name="example"></a><span data-ttu-id="6f9a6-124">. 예 들어</span><span class="sxs-lookup"><span data-stu-id="6f9a6-124">.EXAMPLE</span></span>

<span data-ttu-id="6f9a6-125">함수 또는 스크립트를 사용 하 고 선택적으로 샘플 출력과 설명을 차례로 사용 하는 샘플 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-125">A sample command that uses the function or script, optionally followed by sample output and a description.</span></span> <span data-ttu-id="6f9a6-126">각 예제에 대해이 키워드를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-126">Repeat this keyword for each example.</span></span>

## <a name="inputs"></a><span data-ttu-id="6f9a6-127">. 내용</span><span class="sxs-lookup"><span data-stu-id="6f9a6-127">.INPUTS</span></span>

<span data-ttu-id="6f9a6-128">함수 또는 스크립트로 파이프 될 수 있는 개체의 Microsoft .NET 프레임 워크 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-128">The Microsoft .NET Framework types of objects that can be piped to the function or script.</span></span> <span data-ttu-id="6f9a6-129">입력 개체에 대 한 설명을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-129">You can also include a description of the input objects.</span></span>

## <a name="outputs"></a><span data-ttu-id="6f9a6-130">. 출력</span><span class="sxs-lookup"><span data-stu-id="6f9a6-130">.OUTPUTS</span></span>

<span data-ttu-id="6f9a6-131">Cmdlet이 반환 하는 개체의 .NET Framework 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-131">The .NET Framework type of the objects that the cmdlet returns.</span></span> <span data-ttu-id="6f9a6-132">반환 된 개체에 대 한 설명을 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-132">You can also include a description of the returned objects.</span></span>

## <a name="notes"></a><span data-ttu-id="6f9a6-133">. 메모란</span><span class="sxs-lookup"><span data-stu-id="6f9a6-133">.NOTES</span></span>

<span data-ttu-id="6f9a6-134">함수 또는 스크립트에 대 한 추가 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-134">Additional information about the function or script.</span></span>

## <a name="link"></a><span data-ttu-id="6f9a6-135">. 링크나</span><span class="sxs-lookup"><span data-stu-id="6f9a6-135">.LINK</span></span>

<span data-ttu-id="6f9a6-136">관련 항목의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-136">The name of a related topic.</span></span> <span data-ttu-id="6f9a6-137">관련 된 각 항목에 대해이 키워드를 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-137">Repeat this keyword for each related topic.</span></span> <span data-ttu-id="6f9a6-138">이 콘텐츠는 도움말 항목의 관련 링크 섹션에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-138">This content appears in the Related Links section of the Help topic.</span></span>

<span data-ttu-id="6f9a6-139">`.LINK`키워드 콘텐츠에는 동일한 도움말 항목의 온라인 버전에 대 한 URI (Uniform Resource Identifier)가 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-139">The `.LINK` keyword content can also include a Uniform Resource Identifier (URI) to an online version of the same Help topic.</span></span> <span data-ttu-id="6f9a6-140">의 매개 변수를 사용할 때 온라인 버전이 열립니다 `Online` `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="6f9a6-140">The online version opens when you use the `Online` parameter of `Get-Help`.</span></span> <span data-ttu-id="6f9a6-141">URI는 "http" 또는 "https"로 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-141">The URI must begin with "http" or "https".</span></span>

## <a name="component"></a><span data-ttu-id="6f9a6-142">. 구성 요소</span><span class="sxs-lookup"><span data-stu-id="6f9a6-142">.COMPONENT</span></span>

<span data-ttu-id="6f9a6-143">함수나 스크립트에서 사용 하는 기술 또는 기능의 이름 또는 관련 된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-143">The name of the technology or feature that the function or script uses, or to which it is related.</span></span>
<span data-ttu-id="6f9a6-144">의 **구성 요소** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="6f9a6-144">The **Component** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="role"></a><span data-ttu-id="6f9a6-145">. 역할</span><span class="sxs-lookup"><span data-stu-id="6f9a6-145">.Role</span></span>

<span data-ttu-id="6f9a6-146">도움말 항목에 대 한 사용자 역할의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-146">The name of the user role for the help topic.</span></span> <span data-ttu-id="6f9a6-147">의 **Role** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="6f9a6-147">The **Role** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="functionality"></a><span data-ttu-id="6f9a6-148">. 기능성</span><span class="sxs-lookup"><span data-stu-id="6f9a6-148">.FUNCTIONALITY</span></span>

<span data-ttu-id="6f9a6-149">함수의 용도를 설명 하는 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-149">The keywords that describe the intended use of the function.</span></span> <span data-ttu-id="6f9a6-150">의 **기능** 매개 변수는 `Get-Help` 이 값을 사용 하 여에서 반환 되는 검색 결과를 필터링 합니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="6f9a6-150">The **Functionality** parameter of `Get-Help` uses this value to filter the search results returned by `Get-Help`.</span></span>

## <a name="forwardhelptargetname-command-name"></a><span data-ttu-id="6f9a6-151">. FORWARDHELPTARGETNAME \<Command-Name></span><span class="sxs-lookup"><span data-stu-id="6f9a6-151">.FORWARDHELPTARGETNAME \<Command-Name></span></span>

<span data-ttu-id="6f9a6-152">지정 된 명령에 대 한 도움말 항목으로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-152">Redirects to the Help topic for the specified command.</span></span> <span data-ttu-id="6f9a6-153">함수, 스크립트, cmdlet 또는 공급자에 대 한 도움말 항목을 포함 하 여 사용자를 도움말 항목으로 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-153">You can redirect users to any Help topic, including Help topics for a function, script, cmdlet, or provider.</span></span>

## <a name="forwardhelpcategory-category"></a><span data-ttu-id="6f9a6-154">. FORWARDHELPCATEGORY \<Category></span><span class="sxs-lookup"><span data-stu-id="6f9a6-154">.FORWARDHELPCATEGORY \<Category></span></span>

<span data-ttu-id="6f9a6-155">항목의 도움말 범주를 지정 합니다 `.FORWARDHELPTARGETNAME` .</span><span class="sxs-lookup"><span data-stu-id="6f9a6-155">Specifies the Help category of the item in `.FORWARDHELPTARGETNAME`.</span></span> <span data-ttu-id="6f9a6-156">동일한 이름을 가진 명령이 있는 경우 충돌을 방지 하려면이 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-156">Use this keyword to avoid conflicts when there are commands with the same name.</span></span>

<span data-ttu-id="6f9a6-157">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-157">Valid values are:</span></span>

- <span data-ttu-id="6f9a6-158">Alias</span><span class="sxs-lookup"><span data-stu-id="6f9a6-158">Alias</span></span>
- <span data-ttu-id="6f9a6-159">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6f9a6-159">Cmdlet</span></span>
- <span data-ttu-id="6f9a6-160">HelpFile</span><span class="sxs-lookup"><span data-stu-id="6f9a6-160">HelpFile</span></span>
- <span data-ttu-id="6f9a6-161">함수</span><span class="sxs-lookup"><span data-stu-id="6f9a6-161">Function</span></span>
- <span data-ttu-id="6f9a6-162">공급자</span><span class="sxs-lookup"><span data-stu-id="6f9a6-162">Provider</span></span>
- <span data-ttu-id="6f9a6-163">일반</span><span class="sxs-lookup"><span data-stu-id="6f9a6-163">General</span></span>
- <span data-ttu-id="6f9a6-164">FAQ</span><span class="sxs-lookup"><span data-stu-id="6f9a6-164">FAQ</span></span>
- <span data-ttu-id="6f9a6-165">용어</span><span class="sxs-lookup"><span data-stu-id="6f9a6-165">Glossary</span></span>
- <span data-ttu-id="6f9a6-166">ScriptCommand</span><span class="sxs-lookup"><span data-stu-id="6f9a6-166">ScriptCommand</span></span>
- <span data-ttu-id="6f9a6-167">ExternalScript</span><span class="sxs-lookup"><span data-stu-id="6f9a6-167">ExternalScript</span></span>
- <span data-ttu-id="6f9a6-168">Assert</span><span class="sxs-lookup"><span data-stu-id="6f9a6-168">Filter</span></span>
- <span data-ttu-id="6f9a6-169">모두</span><span class="sxs-lookup"><span data-stu-id="6f9a6-169">All</span></span>

## <a name="remotehelprunspace-pssession-variable"></a><span data-ttu-id="6f9a6-170">. REMOTEHELPRUNSPACE \<PSSession-variable></span><span class="sxs-lookup"><span data-stu-id="6f9a6-170">.REMOTEHELPRUNSPACE \<PSSession-variable></span></span>

<span data-ttu-id="6f9a6-171">도움말 항목을 포함 하는 세션을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-171">Specifies a session that contains the Help topic.</span></span> <span data-ttu-id="6f9a6-172">PSSession이 포함 된 변수를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-172">Enter a variable that contains a PSSession.</span></span> <span data-ttu-id="6f9a6-173">이 키워드는 `Export-PSSession` cmdlet에서 내보낸 명령에 대 한 도움말 항목을 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-173">This keyword is used by the `Export-PSSession` cmdlet to find the Help topics for the exported commands.</span></span>

## <a name="externalhelp-xml-help-file"></a><span data-ttu-id="6f9a6-174">. .EXTERNALHELP 설명을 \<XML Help File></span><span class="sxs-lookup"><span data-stu-id="6f9a6-174">.EXTERNALHELP \<XML Help File></span></span>

<span data-ttu-id="6f9a6-175">스크립트나 함수에 대 한 XML 기반 도움말 파일의 경로 및/또는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-175">Specifies the path and/or name of an XML-based Help file for the script or function.</span></span>

<span data-ttu-id="6f9a6-176">`.EXTERNALHELP`키워드는 XML 기반 파일에서 스크립트나 함수에 대 한 도움말을 가져오기 위해 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-176">The `.EXTERNALHELP` keyword tells the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet to get help for the script or function in an XML-based file.</span></span> <span data-ttu-id="6f9a6-177">`.EXTERNALHELP`키워드는 스크립트나 함수에 대 한 XML 기반 도움말 파일을 사용 하는 경우에 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-177">The `.EXTERNALHELP` keyword is required when using an XML-based help file for a script or function.</span></span> <span data-ttu-id="6f9a6-178">없는 경우 `Get-Help` 는 함수 또는 스크립트에 대 한 도움말 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-178">Without it, `Get-Help` will not find a help file for the function or script.</span></span>

<span data-ttu-id="6f9a6-179">`.EXTERNALHELP`키워드는 다른 모든 주석 기반 도움말 키워드 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-179">The `.EXTERNALHELP` keyword takes precedence over all other comment-based help keywords.</span></span> <span data-ttu-id="6f9a6-180">`.EXTERNALHELP`가 있는 경우 [GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet은 키워드의 값과 일치 하는 도움말 파일을 찾을 수 없는 경우에도 주석 기반 도움말을 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-180">When `.EXTERNALHELP` is present, the [Microsoft.PowerShell.Commands.GetHelpCommand](/dotnet/api/Microsoft.PowerShell.Commands.gethelpcommand) cmdlet does not display comment-based help, even when it cannot find a help file that matches the value of the keyword.</span></span>

<span data-ttu-id="6f9a6-181">스크립트 모듈에서 함수를 내보내는 경우 값은 `.EXTERNALHELP` 경로 없이 파일 이름 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-181">When the function is exported by a script module, the value of `.EXTERNALHELP` should be a filename without a path.</span></span> <span data-ttu-id="6f9a6-182">`Get-Help` 모듈 디렉터리의 로캘별 하위 디렉터리에서 파일을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-182">`Get-Help` looks for the file in a locale-specific subdirectory of the module directory.</span></span> <span data-ttu-id="6f9a6-183">파일 이름에 대 한 요구 사항은 없지만 파일 이름 형식를 사용 하는 것이 가장 좋습니다 `<ScriptModule>.psm1-help.xml` .</span><span class="sxs-lookup"><span data-stu-id="6f9a6-183">There are no requirements for the filename, but a best practice is to use the following filename format: `<ScriptModule>.psm1-help.xml`.</span></span>

<span data-ttu-id="6f9a6-184">함수가 모듈과 연결 되어 있지 않으면 키워드의 값에 경로 및 파일 이름을 포함 `.EXTERNALHELP` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-184">When the function is not associated with a module, include a path and filename in the value of the `.EXTERNALHELP` keyword.</span></span> <span data-ttu-id="6f9a6-185">XML 파일에 대 한 지정 된 경로에 UI 문화권별 하위 디렉터리가 포함 된 경우는 `Get-Help` 모든 xml 기반 도움말 항목과 마찬가지로 Windows에 설정 된 언어 대체 표준에 따라 스크립트나 함수 이름을 사용 하 여 하위 디렉터리에서 xml 파일을 재귀적으로 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-185">If the specified path to the XML file contains UI-culture-specific subdirectories, `Get-Help` searches the subdirectories recursively for an XML file with the name of the script or function in accordance with the language fallback standards established for Windows, just as it does for all XML-based Help topics.</span></span>

<span data-ttu-id="6f9a6-186">Cmdlet 도움말 XML 기반 도움말 파일 형식에 대 한 자세한 내용은 [Windows PowerShell Cmdlet 도움말 작성](./writing-help-for-windows-powershell-cmdlets.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f9a6-186">For more information about the cmdlet Help XML-based Help file format, see [Writing Windows PowerShell Cmdlet Help](./writing-help-for-windows-powershell-cmdlets.md).</span></span>
