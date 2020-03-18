---
title: 끌어오기 요청 관리 방법
description: 이 문서에서는 PowerShell-Docs 팀이 끌어오기 요청을 관리하는 방법을 설명합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b9b37816dfdf38e4d8b7c2d66799164d0e97d257
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060388"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="6c8f7-103">끌어오기 요청 관리</span><span class="sxs-lookup"><span data-stu-id="6c8f7-103">Managing pull requests</span></span>

<span data-ttu-id="6c8f7-104">이 문서에서는 Microsoft가 PowerShell-Docs 리포지토리에서 끌어오기 요청을 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-104">This article documents how we manage pull requests in the PowerShell-Docs repo.</span></span> <span data-ttu-id="6c8f7-105">이 문서는 PowerShell-Docs 팀 구성원을 위한 작업 보조 도구이며,</span><span class="sxs-lookup"><span data-stu-id="6c8f7-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="6c8f7-106">일반 기여자에게 프로세스의 투명도를 공개하기 위해 게시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="6c8f7-107">모범 사례</span><span class="sxs-lookup"><span data-stu-id="6c8f7-107">Best practices</span></span>

- <span data-ttu-id="6c8f7-108">PR을 제출하는 사람은 피어 검토 없이 PR을 병합해서는 안됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-108">The person submitting the PR should not merge the PR without a peer review.</span></span>
- <span data-ttu-id="6c8f7-109">PR을 제출할 때 피어 검토자를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="6c8f7-110">조기에 할당하면 검토자가 편집 설명을 사용하여 더 빨리 응답할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="6c8f7-111">설명을 사용하여 변경의 특성 또는 요청하는 검토의 유형을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="6c8f7-112">검토자를 @mention해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="6c8f7-113">예를 들어 변경 내용이 사소하고 전체 기술 검토가 필요하지 않은 경우 주석에서 설명하세요.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="6c8f7-114">PR 프로세스 단계</span><span class="sxs-lookup"><span data-stu-id="6c8f7-114">PR Process steps</span></span>

1. <span data-ttu-id="6c8f7-115">작성자: PR 만들기</span><span class="sxs-lookup"><span data-stu-id="6c8f7-115">Writer: Create PR</span></span>
   - <span data-ttu-id="6c8f7-116">PR에서 해결된 문제를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="6c8f7-117">GitHub의 [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) 기능을 사용하여 문제를 종결합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="6c8f7-118">작성자: 피어 검토자 할당</span><span class="sxs-lookup"><span data-stu-id="6c8f7-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="6c8f7-119">검토자: 교정 및 설명(필요한 경우)</span><span class="sxs-lookup"><span data-stu-id="6c8f7-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="6c8f7-120">작성자: 검토 피드백 통합</span><span class="sxs-lookup"><span data-stu-id="6c8f7-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="6c8f7-121">둘 다: 미리 보기 렌더링 검토</span><span class="sxs-lookup"><span data-stu-id="6c8f7-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="6c8f7-122">둘 다: 유효성 검사 보고서 검토 - 경고 및 오류 수정</span><span class="sxs-lookup"><span data-stu-id="6c8f7-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="6c8f7-123">작성자: 로그오프 설명 추가(Acrolinx 정보 포함)</span><span class="sxs-lookup"><span data-stu-id="6c8f7-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="6c8f7-124">검토자: 검토 "승인됨" 표시</span><span class="sxs-lookup"><span data-stu-id="6c8f7-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="6c8f7-125">리포지토리 관리자: PR 병합(아래 기준 참조)</span><span class="sxs-lookup"><span data-stu-id="6c8f7-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="6c8f7-126">콘텐츠 검토자 검사 목록</span><span class="sxs-lookup"><span data-stu-id="6c8f7-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="6c8f7-127">보다 포괄적인 목록은 [편집 검사 목록](editorial-checklist.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="6c8f7-128">문법, 스타일, 간명성, 기술 정확도 교정</span><span class="sxs-lookup"><span data-stu-id="6c8f7-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="6c8f7-129">예제가 대상 버전에 계속 적용되는지 확인</span><span class="sxs-lookup"><span data-stu-id="6c8f7-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="6c8f7-130">미리 보기 렌더링 확인</span><span class="sxs-lookup"><span data-stu-id="6c8f7-130">Check Preview rendering</span></span>
- <span data-ttu-id="6c8f7-131">메타데이터(ms.date, remove ms.assetid)를 확인하고 필수 필드가 입력되었는지 확인</span><span class="sxs-lookup"><span data-stu-id="6c8f7-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="6c8f7-132">Markdown 정확성 검증</span><span class="sxs-lookup"><span data-stu-id="6c8f7-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="6c8f7-133">특정 콘텐츠를 서식 지정하기 위한 스타일 가이드를 참조</span><span class="sxs-lookup"><span data-stu-id="6c8f7-133">See style guide for formatting specific content</span></span>
- <span data-ttu-id="6c8f7-134">다음과 같이 예제를 다시 구성</span><span class="sxs-lookup"><span data-stu-id="6c8f7-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="6c8f7-135">소개 문장</span><span class="sxs-lookup"><span data-stu-id="6c8f7-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="6c8f7-136">코드 및 출력</span><span class="sxs-lookup"><span data-stu-id="6c8f7-136">Code and output</span></span>
  - <span data-ttu-id="6c8f7-137">코드에 대한 자세한 설명(필요한 경우)</span><span class="sxs-lookup"><span data-stu-id="6c8f7-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="6c8f7-138">하이퍼링크 정확성 검사</span><span class="sxs-lookup"><span data-stu-id="6c8f7-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="6c8f7-139">TechNet/MSDN 링크를 교체 또는 제거</span><span class="sxs-lookup"><span data-stu-id="6c8f7-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="6c8f7-140">대상으로 리디렉션을 최소화</span><span class="sxs-lookup"><span data-stu-id="6c8f7-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="6c8f7-141">HTTPS 확인</span><span class="sxs-lookup"><span data-stu-id="6c8f7-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="6c8f7-142">올바른 링크 형식</span><span class="sxs-lookup"><span data-stu-id="6c8f7-142">Correct link type</span></span>
    - <span data-ttu-id="6c8f7-143">로컬 파일에 대한 파일 링크</span><span class="sxs-lookup"><span data-stu-id="6c8f7-143">File links for local files</span></span>
    - <span data-ttu-id="6c8f7-144">docset 외부 파일에 대한 URL 링크</span><span class="sxs-lookup"><span data-stu-id="6c8f7-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="6c8f7-145">URL에서 로캘 제거</span><span class="sxs-lookup"><span data-stu-id="6c8f7-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="6c8f7-146">`docs.microsoft.com`을 가리키는 URL을 간소화</span><span class="sxs-lookup"><span data-stu-id="6c8f7-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="6c8f7-147">분기 병합 프로세스</span><span class="sxs-lookup"><span data-stu-id="6c8f7-147">Branch Merge Process</span></span>

<span data-ttu-id="6c8f7-148">스테이징 분기는 라이브로 병합되어야 하는 유일한 분기입니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-148">The staging branch is the only branch that should ever be merged into live.</span></span> <span data-ttu-id="6c8f7-149">단기 (작업) 분기의 병합은 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="6c8f7-150">*Merge from/to*</span><span class="sxs-lookup"><span data-stu-id="6c8f7-150">*Merge from/to*</span></span>  | <span data-ttu-id="6c8f7-151">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="6c8f7-151">*release-branch*</span></span> | <span data-ttu-id="6c8f7-152">*staging*</span><span class="sxs-lookup"><span data-stu-id="6c8f7-152">*staging*</span></span>        | <span data-ttu-id="6c8f7-153">*live*</span><span class="sxs-lookup"><span data-stu-id="6c8f7-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="6c8f7-154">*working-branch*</span><span class="sxs-lookup"><span data-stu-id="6c8f7-154">*working-branch*</span></span> | <span data-ttu-id="6c8f7-155">제거 및 병합</span><span class="sxs-lookup"><span data-stu-id="6c8f7-155">squash and merge</span></span> | <span data-ttu-id="6c8f7-156">제거 및 병합</span><span class="sxs-lookup"><span data-stu-id="6c8f7-156">squash and merge</span></span> | <span data-ttu-id="6c8f7-157">허용되지 않음</span><span class="sxs-lookup"><span data-stu-id="6c8f7-157">Not allowed</span></span> |
| <span data-ttu-id="6c8f7-158">*release-branch*</span><span class="sxs-lookup"><span data-stu-id="6c8f7-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="6c8f7-159">merge</span><span class="sxs-lookup"><span data-stu-id="6c8f7-159">merge</span></span>            | <span data-ttu-id="6c8f7-160">허용되지 않음</span><span class="sxs-lookup"><span data-stu-id="6c8f7-160">Not allowed</span></span> |
| <span data-ttu-id="6c8f7-161">*staging*</span><span class="sxs-lookup"><span data-stu-id="6c8f7-161">*staging*</span></span>        | <span data-ttu-id="6c8f7-162">rebase</span><span class="sxs-lookup"><span data-stu-id="6c8f7-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="6c8f7-163">merge</span><span class="sxs-lookup"><span data-stu-id="6c8f7-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="6c8f7-164">PR 병합기 검사 목록</span><span class="sxs-lookup"><span data-stu-id="6c8f7-164">PR Merger checklist</span></span>

- <span data-ttu-id="6c8f7-165">콘텐츠 검토 완료</span><span class="sxs-lookup"><span data-stu-id="6c8f7-165">Content review complete</span></span>
- <span data-ttu-id="6c8f7-166">변경에 대한 대상 분기 수정</span><span class="sxs-lookup"><span data-stu-id="6c8f7-166">Correct target branch for the change</span></span>
- <span data-ttu-id="6c8f7-167">병합 충돌 없음</span><span class="sxs-lookup"><span data-stu-id="6c8f7-167">No merge conflicts</span></span>
- <span data-ttu-id="6c8f7-168">모든 유효성 검사 및 빌드 단계 통과</span><span class="sxs-lookup"><span data-stu-id="6c8f7-168">All validation and build step pass</span></span>
  - <span data-ttu-id="6c8f7-169">경고 및 제안을 수정해야 합니다(예외는 [참고](#notes) 참조).</span><span class="sxs-lookup"><span data-stu-id="6c8f7-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="6c8f7-170">끊어진 링크 없음</span><span class="sxs-lookup"><span data-stu-id="6c8f7-170">No broken links</span></span>
- <span data-ttu-id="6c8f7-171">테이블에 따라 병합</span><span class="sxs-lookup"><span data-stu-id="6c8f7-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="6c8f7-172">메모</span><span class="sxs-lookup"><span data-stu-id="6c8f7-172">Notes</span></span>

<span data-ttu-id="6c8f7-173">다음 경고는 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="6c8f7-174">PR을 병합하면 대상 분기의 HEAD가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="6c8f7-175">이전 HEAD를 기반으로 하던 모든 미해결 PR은 이제 만료된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="6c8f7-176">만료된 PR은 GitHub에서 병합 경고를 재정의하기 위해 관리자 권한을 사용하여 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="6c8f7-177">이전에 병합된 PR이 같은 파일에 작업을 수행하지 않은 경우에는 이 작업을 수행해도 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="6c8f7-178">그러나 **분기 업데이트** 단추를 클릭하는 것이 가장 안전한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="6c8f7-179">수정해야 할 충돌이 해결되지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="6c8f7-180">라이브에 게시</span><span class="sxs-lookup"><span data-stu-id="6c8f7-180">Publishing to Live</span></span>

<span data-ttu-id="6c8f7-181">정기적으로 `staging` 분기에 누적된 변경 내용을 라이브 웹 사이트에 게시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span> <span data-ttu-id="6c8f7-182">이렇게 하려면 `staging` 분기를 `live` 분기에 병합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-182">This require merging the `staging` branch into the `live` branch.</span></span>

- <span data-ttu-id="6c8f7-183">매주 한 번 이상 `staging` 분기를 `live`에 병합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-183">The `staging` branch should be merged to `live` at least once per week.</span></span>
- <span data-ttu-id="6c8f7-184">`staging` 분기는 모든 주요 변경 후에 `live`에 병합되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c8f7-184">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="6c8f7-185">50개 이상 파일에 대한 변경</span><span class="sxs-lookup"><span data-stu-id="6c8f7-185">Changes to 50 or more files</span></span>
  - <span data-ttu-id="6c8f7-186">릴리스 분기를 병합한 후</span><span class="sxs-lookup"><span data-stu-id="6c8f7-186">After merging a release branch</span></span>
  - <span data-ttu-id="6c8f7-187">리포지토리 또는 docset 구성(docset.json, OPS 구성, 빌드 스크립트 등) 변경</span><span class="sxs-lookup"><span data-stu-id="6c8f7-187">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="6c8f7-188">리디렉션 파일 변경</span><span class="sxs-lookup"><span data-stu-id="6c8f7-188">Changes to the redirection file</span></span>
  - <span data-ttu-id="6c8f7-189">TOC 변경</span><span class="sxs-lookup"><span data-stu-id="6c8f7-189">Changes to the TOC</span></span>
  - <span data-ttu-id="6c8f7-190">"프로젝트" 분기 병합 후(콘텐츠 재구성, 대량 업데이트 등)</span><span class="sxs-lookup"><span data-stu-id="6c8f7-190">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>
