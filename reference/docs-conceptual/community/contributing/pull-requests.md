---
title: 끌어오기 요청 제출 방법
description: 이 문서에서는 PowerShell-Docs 리포지토리에 끌어오기 요청을 제출하는 방법을 설명합니다.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "99602035"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="85a61-103">끌어오기 요청 제출 방법</span><span class="sxs-lookup"><span data-stu-id="85a61-103">How to submit pull requests</span></span>

<span data-ttu-id="85a61-104">콘텐츠를 변경하려면 포크에서 끌어오기 요청(PR)을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="85a61-105">끌어오기 요청을 병합 하려면 먼저 검토 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-105">A pull request must be reviewed before it can be merged.</span></span> <span data-ttu-id="85a61-106">최상의 결과를 위해 끌어오기 요청을 제출하기 전에 [편집 검사 목록](editorial-checklist.md)을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="using-git-branches"></a><span data-ttu-id="85a61-107">Git 분기 사용</span><span class="sxs-lookup"><span data-stu-id="85a61-107">Using git branches</span></span>

<span data-ttu-id="85a61-108">PowerShell-Docs에 대 한 기본 분기는 `staging` 분기입니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-108">The default branch for PowerShell-Docs is the `staging` branch.</span></span> <span data-ttu-id="85a61-109">작업 분기에서 변경한 내용은 `staging` 게시 되기 전에 분기로 병합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-109">Changes made in working branches are merged into the `staging` branch before then being published.</span></span> <span data-ttu-id="85a61-110">`staging`분기는 `live` 평일 3:00 PM (태평양 표준시)에 분기 마다 병합 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-110">The `staging` branch is merged into the `live` branch every weekday at 3:00 PM (Pacific Time).</span></span> <span data-ttu-id="85a61-111">`live`분기는 docs.microsoft.com에 게시 된 콘텐츠를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-111">The `live` branch contains the content that is published to docs.microsoft.com.</span></span>

<span data-ttu-id="85a61-112">변경을 시작 하기 전에 PowerShell-Docs 리포지토리의 로컬 복사본에 작업 분기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-112">Before starting any changes, create a working branch in your local copy of the PowerShell-Docs repository.</span></span> <span data-ttu-id="85a61-113">로컬에서 작업 하는 경우 작업 분기를 만들기 전에 로컬 리포지토리를 동기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-113">When working locally, be sure to synchronize your local repository before creating your working branch.</span></span> <span data-ttu-id="85a61-114">분기의 업데이트-날짜 복사본에서 작업 분기를 만들어야 합니다 `staging` .</span><span class="sxs-lookup"><span data-stu-id="85a61-114">The working branch should be created from an update-to-date copy of the `staging` branch.</span></span>

<span data-ttu-id="85a61-115">모든 끌어오기 요청은 `staging` 분기를 대상으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-115">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="85a61-116">분기에 변경 내용을 전송 하지 않습니다 `live` .</span><span class="sxs-lookup"><span data-stu-id="85a61-116">Don't submit change to the `live` branch.</span></span>
<span data-ttu-id="85a61-117">`staging` 분기에서 수행된 변경 내용은 `live`에 병합되어 `live`에 대한 변경 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-117">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="85a61-118">끌어오기 요청 프로세스를 모든 사용자가 더 잘 작동할 수 있도록 설정</span><span class="sxs-lookup"><span data-stu-id="85a61-118">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="85a61-119">PR을 더 간단하고 더 중점적으로 만들수록 더 빠르게 검토 및 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-119">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="85a61-120">많은 수의 파일을 업데이트 하거나 관련 없는 변경 내용을 포함 하는 끌어오기 요청 방지</span><span class="sxs-lookup"><span data-stu-id="85a61-120">Avoid pull requests that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="85a61-121">관련이 없는 변경 내용을 포함하는 PR을 만들지 마세요.</span><span class="sxs-lookup"><span data-stu-id="85a61-121">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="85a61-122">기존 문서에 대한 부 업데이트를 새 문서 또는 주요 다시 쓰기와 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-122">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="85a61-123">이러한 변경 작업은 별도의 작업 분기에서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-123">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="85a61-124">대량 변경은 변경된 파일이 많은 PR을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-124">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="85a61-125">PR을 최대 50개의 변경된 파일로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-125">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="85a61-126">대량 PR은 검토하기 어렵고 오류를 포함할 가능성이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-126">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="85a61-127">파일 이름 바꾸기 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="85a61-127">Renaming or deleting files</span></span>

<span data-ttu-id="85a61-128">파일의 이름을 바꾸거나 삭제 하는 경우 PR과 관련 된 문제가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-128">When renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="85a61-129">이 문제는 파일의 이름을 바꾸거나 파일을 삭제해야 하는 이유를 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-129">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="85a61-130">파일 이름 바꾸기 및 삭제를 사용하여 콘텐츠를 추가하거나 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="85a61-130">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="85a61-131">이름이 바뀌거나 삭제 된 파일은 전역 리디렉션 파일에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-131">Any file that is renamed or deleted must be added to the global redirection file.</span></span> <span data-ttu-id="85a61-132">가능 하면 이름이 바뀌거나 삭제 된 콘텐츠 (TOC 파일 포함)에 연결 된 모든 파일을 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-132">When possible, update any files that link to the renamed or deleted content, including any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="85a61-133">Docs PR 유효성 검사 서비스</span><span class="sxs-lookup"><span data-stu-id="85a61-133">Docs PR validation service</span></span>

<span data-ttu-id="85a61-134">문서 PR 유효성 검사 서비스는 변경 내용에 대 한 유효성 검사 규칙을 실행 하는 GitHub 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-134">The Docs PR validation service is a GitHub app that runs validation rules on your changes.</span></span> <span data-ttu-id="85a61-135">유효성 검사 서비스에서 보고 한 오류 또는 경고를 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-135">You must fix any errors or warnings reported by the validation service.</span></span>

<span data-ttu-id="85a61-136">다음 동작을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-136">You'll see the following behavior:</span></span>

1. <span data-ttu-id="85a61-137">PR을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-137">You submit a PR.</span></span>
1. <span data-ttu-id="85a61-138">PR의 상태를 나타내는 GitHub 설명에서 리포지토리에서 사용하도록 설정된 “검사”의 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-138">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="85a61-139">이 예제에서는 "Commit Validation" 및 "OpenPublishing. Build"의 두 가지 검사를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-139">In this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![유효성 검사 상태 - 일부 검사가 실패함](media/pull-requests/validation-failed.png)

   <span data-ttu-id="85a61-141">커밋 유효성 검사에 실패한 경우에도 빌드가 통과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-141">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="85a61-142">자세한 내용은 **세부 정보** 를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85a61-142">Click **Details** for more information.</span></span>
1. <span data-ttu-id="85a61-143">세부 정보 페이지에는 문제를 해결하는 방법에 대한 정보와 함께 실패한 모든 유효성 검사가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-143">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="85a61-144">유효성 검사에 성공하면 다음과 같은 주석이 PR에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-144">When validation succeeds, the following comment is added to the PR:</span></span>

   ![유효성 검사 상태: 성공](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="85a61-146">외부(Microsoft 직원이 아닌) 기여자인 경우에는 자세한 빌드 보고서 또는 미리 보기 링크에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-146">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="85a61-147">PR을 검토할 때 변경 내용을 적용 하거나 유효성 검사 경고 메시지를 수정 하 라는 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-147">When the PR is reviewed, you may be asked to make changes or fix validation warning messages.</span></span> <span data-ttu-id="85a61-148">PowerShell-Docs 팀은 유효성 검사 오류 및 편집 요구 사항을 이해 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85a61-148">The PowerShell-Docs team can help you understand validation errors and editorial requirements.</span></span>

## <a name="next-steps"></a><span data-ttu-id="85a61-149">다음 단계</span><span class="sxs-lookup"><span data-stu-id="85a61-149">Next steps</span></span>

[<span data-ttu-id="85a61-150">PowerShell-Docs 스타일 가이드</span><span class="sxs-lookup"><span data-stu-id="85a61-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="85a61-151">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="85a61-151">Additional resources</span></span>

[<span data-ttu-id="85a61-152">끌어오기 요청 관리 방법</span><span class="sxs-lookup"><span data-stu-id="85a61-152">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
