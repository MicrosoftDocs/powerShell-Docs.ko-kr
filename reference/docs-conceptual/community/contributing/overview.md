---
title: PowerShell 설명서에 기여하기
description: 이 문서에서는 PowerShell 설명서에 참여하는 데 필요한 단계를 간략하게 설명합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 255b74a75b8412ed509f6da930eb722d54233711
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354408"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="78523-103">PowerShell 설명서에 기여하기</span><span class="sxs-lookup"><span data-stu-id="78523-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="78523-104">PowerShell을 지원해 주셔서 감사합니다!</span><span class="sxs-lookup"><span data-stu-id="78523-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="78523-105">기여자 가이드는 Microsoft에서 설명서를 만드는 데 사용하는 도구와 프로세스를 설명하는 문서 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="78523-105">The Contributor's Guide is a collection of articles that explain the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="78523-106">이러한 가이드 중 일부는 [docs.microsoft.com][docs]에 게시된 모든 문서 집합의 일반적인 정보를 다루며,</span><span class="sxs-lookup"><span data-stu-id="78523-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="78523-107">일부 가이드는 PowerShell 설명서 작성 방법과 관련되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="78523-108">일반 문서는 Microsoft의 통합 [기여자 가이드][contribute]에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="78523-109">PowerShell 관련 가이드는 여기에서 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="78523-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="78523-110">참가 방법</span><span class="sxs-lookup"><span data-stu-id="78523-110">Ways to contribute</span></span>

<span data-ttu-id="78523-111">두 가지 방법으로 기여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-111">There are two ways to contribute.</span></span> <span data-ttu-id="78523-112">두 방법 모두 큰 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78523-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="78523-113">[문제 제출][file-an-issue]은 Microsoft가 설명서의 문제와 공백을 식별하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="78523-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="78523-114">때로는 문제 해결이 어렵고 더 많은 조사와 연구가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="78523-115">이 경우 문제 프로세스를 통해 문제에 관해 대화하고 만족스러운 해결책을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="78523-116">새로운 콘텐츠를 제출하거나 기존 문서를 변경하는 프로세스에는 더욱 긴밀한 참여가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="78523-116">Submitting new content or changes to existing articles is a more involved process.</span></span> <span data-ttu-id="78523-117">다음 정보에는 설명서에 콘텐츠를 제출하기 위한 도구, 프로세스, 표준이 간략하게 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="78523-118">기여 준비</span><span class="sxs-lookup"><span data-stu-id="78523-118">Prepare to make a contribution</span></span>

<span data-ttu-id="78523-119">설명서에 기여하려면 GitHub 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="78523-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="78523-120">기여를 위한 도구를 획득하고 기여 프로세스를 이해하려면 다음 검사 목록을 활용하세요.</span><span class="sxs-lookup"><span data-stu-id="78523-120">Use the following checklist to get the tools and understand the processes we use for making contributions.</span></span>

1. [<span data-ttu-id="78523-121">GitHub에 등록</span><span class="sxs-lookup"><span data-stu-id="78523-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="78523-122">Git 및 Markdown 도구 설치</span><span class="sxs-lookup"><span data-stu-id="78523-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="78523-123">Docs Authoring Pack 설치</span><span class="sxs-lookup"><span data-stu-id="78523-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="78523-124">[Posh-Git 설치][posh-git] - 필수는 아니지만 권장 사항</span><span class="sxs-lookup"><span data-stu-id="78523-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="78523-125">로컬 Git 리포지토리 설정</span><span class="sxs-lookup"><span data-stu-id="78523-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="78523-126">Git 및 GitHub 기본 사항 검토</span><span class="sxs-lookup"><span data-stu-id="78523-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="78523-127">문서 작성 시작</span><span class="sxs-lookup"><span data-stu-id="78523-127">Get started writing docs</span></span>

<span data-ttu-id="78523-128">다음 두 가지 방법으로 설명서에 변경 내용을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="78523-129">기존 문서의 빠른 편집</span><span class="sxs-lookup"><span data-stu-id="78523-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="78523-130">사소한 교정, 오타 수정 또는 약간의 내용 추가</span><span class="sxs-lookup"><span data-stu-id="78523-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="78523-131">문서의 전체 GitHub 워크플로</span><span class="sxs-lookup"><span data-stu-id="78523-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="78523-132">대규모 변경, 여러 버전 작성, 이미지 추가나 변경 또는 새 문서 작성</span><span class="sxs-lookup"><span data-stu-id="78523-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="78523-133">통합 기여자 가이드의 [문서 작성 필수 정보](/contribute/style-quick-start) 섹션도 참조해 보세요.</span><span class="sxs-lookup"><span data-stu-id="78523-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="78523-134">또 다른 훌륭한 리소스는 [Microsoft 문서 작성 스타일 가이드][style-guide]입니다.</span><span class="sxs-lookup"><span data-stu-id="78523-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="78523-135">Microsoft 문서 작성 스타일 가이드의 목표는 편집자, 기술 작성자, 개발자, 마케터 및 IT 분야에 있는 그 밖의 모든 사람이 더 나은 콘텐츠를 작성하도록 돕는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="78523-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="78523-136">공개 리포지토리의 설명서 및 코드 예시의 사소한 수정이나 설명은 docs.microsoft.com의 [사용 약관][terms-of-use]에서 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="78523-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="78523-137">중요한 변경을 적용하는 경우에는 전체 GitHub 워크플로를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="78523-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="78523-138">Microsoft 직원이 아니라면 중요한 변경 내용을 적용할 경우 [기여 라이센스 규약(CLA)][cla] 제출을 요청하는 주석이 끌어오기 요청에 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="78523-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="78523-139">Microsoft가 끌어오기 요청을 검토하거나 수락하려면 기여자가 먼저 온라인 양식을 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78523-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="78523-140">사용 규정</span><span class="sxs-lookup"><span data-stu-id="78523-140">Code of conduct</span></span>

<span data-ttu-id="78523-141">docs.microsoft.com에 게시되는 모든 리포지토리는 [Microsoft 오픈 소스 사용 규정](https://opensource.microsoft.com/codeofconduct/) 또는 [.NET Foundation 사용 규정](https://dotnetfoundation.org/code-of-conduct)을 채택하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="78523-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="78523-142">자세한 내용은 [사용 규정 FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78523-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="78523-143">다음 단계</span><span class="sxs-lookup"><span data-stu-id="78523-143">Next steps</span></span>

<span data-ttu-id="78523-144">다음 문서에서는 PowerShell 설명서 관련 정보를 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="78523-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="78523-145">통합 기여자 가이드의 지침과 중복되는 부분이 발견되면, Microsoft는 이러한 규칙이 PowerShell 콘텐츠의 경우 어떻게 적용되는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="78523-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="78523-146">다음 문서를 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="78523-146">Review the following documents:</span></span>

- [<span data-ttu-id="78523-147">문제 제출 방법</span><span class="sxs-lookup"><span data-stu-id="78523-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="78523-148">문서 작성 시작하기</span><span class="sxs-lookup"><span data-stu-id="78523-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="78523-149">끌어오기 요청 제출하기</span><span class="sxs-lookup"><span data-stu-id="78523-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="78523-150">PowerShell-Docs 스타일 가이드</span><span class="sxs-lookup"><span data-stu-id="78523-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)
- [<span data-ttu-id="78523-151">cmdlet 참조 편집하기</span><span class="sxs-lookup"><span data-stu-id="78523-151">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<span data-ttu-id="78523-152">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="78523-152">Additional resources</span></span>

- [<span data-ttu-id="78523-153">편집 검사 목록</span><span class="sxs-lookup"><span data-stu-id="78523-153">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="78523-154">문제 관리 방법</span><span class="sxs-lookup"><span data-stu-id="78523-154">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="78523-155">끌어오기 요청 관리 방법</span><span class="sxs-lookup"><span data-stu-id="78523-155">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
