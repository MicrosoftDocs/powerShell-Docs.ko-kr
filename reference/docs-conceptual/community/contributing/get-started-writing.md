---
title: PowerShell 설명서에 기여 시작
description: 이 문서는 PowerShell 설명서에 대한 기여자로 시작하는 방법을 간단히 설명합니다.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: ddcbf79de1ab05b901ce1abd67f65b2524ed164d
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99601037"
---
# <a name="get-started-contributing-to-powershell-documentation"></a><span data-ttu-id="39449-103">PowerShell 설명서에 기여 시작</span><span class="sxs-lookup"><span data-stu-id="39449-103">Get started contributing to PowerShell documentation</span></span>

<span data-ttu-id="39449-104">이 문서는 PowerShell 설명서에 대한 기여자로 시작하는 방법을 간단히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-104">This article is an overview of how to get started as a contributor to the PowerShell documentation.</span></span>

## <a name="powershell-docs-structure"></a><span data-ttu-id="39449-105">PowerShell-Docs 구조</span><span class="sxs-lookup"><span data-stu-id="39449-105">PowerShell-Docs structure</span></span>

<span data-ttu-id="39449-106">[PowerShell 문서 리포지토리][psdocs] 는 두 개의 콘텐츠 그룹인 참조 및 개념으로 나뉩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-106">The [PowerShell-Docs repository][psdocs] is divided into two groups of content: reference and conceptual.</span></span>

### <a name="reference-content"></a><span data-ttu-id="39449-107">참조 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="39449-107">Reference content</span></span>

<span data-ttu-id="39449-108">참조 콘텐츠는 PowerShell에서 제공 하는 cmdlet에 대 한 PowerShell cmdlet 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="39449-108">The reference content is the PowerShell cmdlet reference for the cmdlets that ship in PowerShell.</span></span>
<span data-ttu-id="39449-109">[참조][ref] 는 버전 폴더 (5.1, 7.0, 7.1 및 7.2)에서 수집 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-109">The [reference][ref] is collected in versions folders (5.1, 7.0, 7.1, and 7.2).</span></span> <span data-ttu-id="39449-110">이 콘텐츠에는 PowerShell과 함께 제공 되는 모듈에 대 한 cmdlet 참조만 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-110">This content contains cmdlet reference only for the modules that ship with PowerShell.</span></span> <span data-ttu-id="39449-111">이 콘텐츠는 cmdlet에서 표시 하는 도움말 정보를 만드는 데도 사용 됩니다 `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="39449-111">This content is also used to create the help information displayed by the `Get-Help` cmdlet.</span></span>

### <a name="conceptual-content"></a><span data-ttu-id="39449-112">개념적 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="39449-112">Conceptual content</span></span>

<span data-ttu-id="39449-113">개념 설명서에는 다음과 같은 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-113">The conceptual documentation includes the following content:</span></span>

- <span data-ttu-id="39449-114">릴리스 정보</span><span class="sxs-lookup"><span data-stu-id="39449-114">Release notes</span></span>
- <span data-ttu-id="39449-115">설치 지침</span><span class="sxs-lookup"><span data-stu-id="39449-115">Setup instructions</span></span>
- <span data-ttu-id="39449-116">샘플 스크립트 및 방법 문서</span><span class="sxs-lookup"><span data-stu-id="39449-116">Sample scripts and how-to articles</span></span>
- <span data-ttu-id="39449-117">DSC 설명서</span><span class="sxs-lookup"><span data-stu-id="39449-117">DSC documentation</span></span>
- <span data-ttu-id="39449-118">SDK 설명서</span><span class="sxs-lookup"><span data-stu-id="39449-118">SDK documentation</span></span>

<span data-ttu-id="39449-119">[개념 설명서][conceptual] 는 버전 별로 구성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-119">The [conceptual documentation][conceptual] is not organized by version.</span></span> <span data-ttu-id="39449-120">모든 아티클이 모든 버전의 PowerShell에 대해 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-120">All articles are displayed for every version of PowerShell.</span></span> <span data-ttu-id="39449-121">버전별 문서를 만들기 위해 노력 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-121">We're working to create version-specific articles.</span></span> <span data-ttu-id="39449-122">설명서에서이 기능을 사용할 수 있는 경우이 가이드가 적절 한 정보로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-122">When that feature is available in our documentation, this guide will be update with the appropriate information.</span></span>

> [!NOTE]
> <span data-ttu-id="39449-123">개념 문서를 추가, 제거 또는 이름을 변경할 때마다 TOC를 업데이트 하 고 끌어오기 요청에 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-123">Anytime a conceptual article is added, removed, or renamed, the TOC must be updated and included in the pull request.</span></span>

## <a name="creating-new-articles"></a><span data-ttu-id="39449-124">새 문서 만들기</span><span class="sxs-lookup"><span data-stu-id="39449-124">Creating new articles</span></span>

<span data-ttu-id="39449-125">참가 하려는 새 문서에 대 한 GitHub 문제를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-125">A GitHub issue must be created for any new document you want to contribute.</span></span> <span data-ttu-id="39449-126">기존 문제를 확인 하 여 노력이 중복 되지 않는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-126">Check for existing issues to make sure you're not duplicating efforts.</span></span> <span data-ttu-id="39449-127">할당 된 문제는로 간주 됩니다 `in progress` .</span><span class="sxs-lookup"><span data-stu-id="39449-127">Assigned issues are considered to be `in progress`.</span></span> <span data-ttu-id="39449-128">문제에 대 한 공동 작업을 하려는 경우 해당 문제에 할당 된 담당자에 게 문의 하세요.</span><span class="sxs-lookup"><span data-stu-id="39449-128">If you wish to collaborate on an issue, contact the person assigned to the issue.</span></span>

<span data-ttu-id="39449-129">PowerShell [RFC 프로세스][rfc]와 마찬가지로 콘텐츠를 작성 하기 전에 문제를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="39449-129">Similar to the PowerShell [RFC process][rfc], create an issue before you write the content.</span></span> <span data-ttu-id="39449-130">이 문제는 PowerShell-Docs 팀에서 거부 하는 작업에 대 한 시간과 노력을 낭비 하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-130">The issue ensures you don't waste time and effort on work that gets rejected by the PowerShell-Docs team.</span></span> <span data-ttu-id="39449-131">이 문제를 통해 콘텐츠의 범위를 확인 하 고 PowerShell 설명서에 맞는 위치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-131">The issue allows us to consult with you on the scope of the content and where it fits in the PowerShell documentation.</span></span> <span data-ttu-id="39449-132">모든 아티클은 TOC (목차)에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-132">All articles must be included in the Table of Contents (TOC).</span></span> <span data-ttu-id="39449-133">제안 된 TOC 위치는 문제 토론에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-133">The proposed TOC location should be included in the issue discussion.</span></span>

> [!NOTE]
> <span data-ttu-id="39449-134">참조 콘텐츠의 TOC는 게시 시스템에서 자동으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-134">The TOC for reference content is autogenerated by the publishing system.</span></span> <span data-ttu-id="39449-135">TOC를 업데이트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-135">You don't have to update the TOC.</span></span>

## <a name="updating-existing-articles"></a><span data-ttu-id="39449-136">기존 아티클 업데이트</span><span class="sxs-lookup"><span data-stu-id="39449-136">Updating existing articles</span></span>

<span data-ttu-id="39449-137">해당 하는 경우이 리포지토리에서 관리 되는 모든 버전의 PowerShell에서 cmdlet 참조 문서가 중복 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-137">Where applicable, cmdlet reference articles are duplicated across all versions of PowerShell maintained in this repository.</span></span> <span data-ttu-id="39449-138">Cmdlet 참조 또는 아티클에 대 한 문제를 보고할 때 `About_` 문제의 영향을 받는 버전을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-138">When reporting an issue about a cmdlet reference or an `About_` article, you must specify which versions are affected by the issue.</span></span> <span data-ttu-id="39449-139">GitHub의 문제 템플릿에는 버전의 검사 목록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-139">The issue template in GitHub includes a checklist of versions.</span></span> <span data-ttu-id="39449-140">확인란을 사용 하 여 영향을 받는 콘텐츠의 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-140">Use the checkboxes to specify which versions of the content are affected.</span></span>

<span data-ttu-id="39449-141">모든 버전의 문서를 확인 하 여 다른 버전에서 동일한 변경이 필요한 지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-141">Check all version of the article to see if the same change is needed in the other versions.</span></span> <span data-ttu-id="39449-142">파일의 각 버전에 적절 한 변경 내용을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-142">Apply the appropriate change to each version of the file.</span></span>

## <a name="localized-content"></a><span data-ttu-id="39449-143">지역화 된 콘텐츠</span><span class="sxs-lookup"><span data-stu-id="39449-143">Localized content</span></span>

<span data-ttu-id="39449-144">PowerShell 설명서는 영어로 작성 되었으며 17 개의 다른 언어로 번역 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-144">The PowerShell documentation is written in English and translated into 17 other languages.</span></span> <span data-ttu-id="39449-145">영어 콘텐츠는 이라는 GitHub 리포지토리에 저장 됩니다 `MicrosoftDocs/PowerShell-Docs` .</span><span class="sxs-lookup"><span data-stu-id="39449-145">The English content is stored in the GitHub repository named `MicrosoftDocs/PowerShell-Docs`.</span></span> <span data-ttu-id="39449-146">지역화 된 콘텐츠는 각 언어에 대해 별도의 리포지토리에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-146">The localized content is stored in a separate repository for each language.</span></span> <span data-ttu-id="39449-147">리포지토리는 동일한 basename를 사용 하지만 끝에 로캘 이름을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-147">The repositories use the same basename but add the locale name to the end.</span></span> <span data-ttu-id="39449-148">예를 들어에는 `MicrosoftDocs/PowerShell-Docs.de-de` 독일어로 번역 된 콘텐츠가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-148">For example, `MicrosoftDocs/PowerShell-Docs.de-de` contains the content that was translated to German.</span></span>

<span data-ttu-id="39449-149">일반적으로 문제 및 변경 내용은 영어 리포지토리로 제출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-149">In general, issues and changes should be submitted to the English repository.</span></span> <span data-ttu-id="39449-150">모든 번역은 먼저 영어 콘텐츠에서 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-150">All translations start from the English content first.</span></span> <span data-ttu-id="39449-151">사용자와 기계 번역을 모두 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-151">We use both human and machine translation.</span></span>

| <span data-ttu-id="39449-152">Translation 메서드</span><span class="sxs-lookup"><span data-stu-id="39449-152">Translation method</span></span>  |                              <span data-ttu-id="39449-153">언어</span><span class="sxs-lookup"><span data-stu-id="39449-153">Languages</span></span>                               |
| ------------------- | -------------------------------------------------------------------- |
| <span data-ttu-id="39449-154">사용자 변환</span><span class="sxs-lookup"><span data-stu-id="39449-154">Human translation</span></span>   | <span data-ttu-id="39449-155">de-de, es, fr-fr, it, ja-jp, ko-kr, ko-kr-KR, pt-BR, zh-cn,, zh-cn</span><span class="sxs-lookup"><span data-stu-id="39449-155">de-DE, es-ES, fr-FR, it-IT, ja-JP, ko-KR, pt-BR, ru-RU, zh-CN, zh-TW</span></span> |
| <span data-ttu-id="39449-156">기계 번역</span><span class="sxs-lookup"><span data-stu-id="39449-156">Machine translation</span></span> | <span data-ttu-id="39449-157">cs-CZ, hu-hu-HU-HU, nl-NL, pl, pt-PT, sv-SE, tr-TR</span><span class="sxs-lookup"><span data-stu-id="39449-157">cs-CZ, hu-HU, nl-NL, pl-PL, pt-PT, sv-SE, tr-TR</span></span>                      |

<span data-ttu-id="39449-158">기계 번역으로 변환 된 콘텐츠가 항상 올바른 단어 선택 및 문법을 초래 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-158">The content translated by machine translation may not always result in correct word choices and grammar.</span></span> <span data-ttu-id="39449-159">문서에 대 한 기술 세부 정보가 아니라 모든 언어에 대 한 번역에서 오류를 발견 한 경우 지역화 된 리포지토리에서 문제를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="39449-159">If you find an error in translation for any language, rather than in the technical details of the article, open an issue in the localized repository.</span></span> <span data-ttu-id="39449-160">번역이 잘못 된 것으로 생각 하는 이유를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-160">Explain why you think the translation is incorrect.</span></span> <span data-ttu-id="39449-161">Microsoft의 지역화 팀은 이러한 문제를 검토 하 고 대응 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-161">Our localization team reviews and responds to these issues.</span></span>

## <a name="next-steps"></a><span data-ttu-id="39449-162">다음 단계</span><span class="sxs-lookup"><span data-stu-id="39449-162">Next steps</span></span>

<span data-ttu-id="39449-163">GitHub에서 변경 내용을 전송 하는 일반적인 방법에는 두 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-163">There are two common ways of submitting changes in GitHub.</span></span> <span data-ttu-id="39449-164">두 방법 모두 중앙 참가자 가이드에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-164">Both methods are described in the central Contributor's Guide:</span></span>

1. <span data-ttu-id="39449-165">GitHub 웹 인터페이스에서 [기존 문서를 신속 하 게 편집할](/contribute/#quick-edits-to-existing-documents) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="39449-165">You can make [quick edits to existing documents](/contribute/#quick-edits-to-existing-documents) in the GitHub web interface.</span></span>
1. <span data-ttu-id="39449-166">[전체 GitHub 워크플로][making-changes] 를 사용 하 여 새 문서를 추가 하거나 여러 파일을 업데이트 하거나 기타 많은 변경 내용을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-166">Use the [full GitHub workflow][making-changes] for adding new articles, updating multiple files, or other large changes.</span></span>

<span data-ttu-id="39449-167">변경을 시작 하기 전에 PowerShell-Docs 리포지토리의 포크를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-167">Before starting any changes, you should create a fork of the PowerShell-Docs repository.</span></span> <span data-ttu-id="39449-168">PowerShell 문서 복사본의 작업 분기에서 변경 해야 합니다. GitHub에서 **빠른 편집** 방법을 사용 하는 경우 이러한 단계가 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39449-168">The changes should be made in a working branch in you copy of the PowerShell-Docs. If you're using the **quick edit** method in GitHub, these steps are handled for you.</span></span> <span data-ttu-id="39449-169">**전체 GitHub 워크플로** 를 사용 하는 경우 [로컬에서 작동][fork]하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="39449-169">If you're using the **full GitHub workflow**, you must be set up to [work locally][fork].</span></span>

<span data-ttu-id="39449-170">두 메서드는 모두 끌어오기 요청 (PR) 만들기로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="39449-170">Both methods end with the creation of a Pull Request (PR).</span></span> <span data-ttu-id="39449-171">자세한 내용은 [끌어오기 요청 제출](pull-requests.md) 및 모범 사례를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="39449-171">See [Submitting a pull request](pull-requests.md) for more information and best practices.</span></span>

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
