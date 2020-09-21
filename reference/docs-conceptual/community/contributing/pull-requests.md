---
title: 끌어오기 요청 제출 방법
description: 이 문서에서는 PowerShell-Docs 리포지토리에 끌어오기 요청을 제출하는 방법을 설명합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 8b392a36c9469b83cf4f088c1799720a091434b4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782653"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="efb30-103">끌어오기 요청 제출 방법</span><span class="sxs-lookup"><span data-stu-id="efb30-103">How to submit pull requests</span></span>

<span data-ttu-id="efb30-104">콘텐츠를 변경하려면 포크에서 끌어오기 요청(PR)을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="efb30-105">끌어오기 요청은 검토가 완료되어야 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="efb30-106">최상의 결과를 위해 끌어오기 요청을 제출하기 전에 [편집 검사 목록](editorial-checklist.md)을 검토합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="efb30-107">올바른 분기를 대상으로 지정</span><span class="sxs-lookup"><span data-stu-id="efb30-107">Target the correct branch</span></span>

<span data-ttu-id="efb30-108">모든 끌어오기 요청은 `staging` 분기를 대상으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="efb30-109">변경 내용이 `live` 분기로 제출되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="efb30-110">`staging` 분기에서 수행된 변경 내용은 `live`에 병합되어 `live`에 대한 변경 내용을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="efb30-111">릴리스되지 않은 버전의 PowerShell에만 적용되는 변경 내용을 제출하는 경우 해당 버전에 대한 릴리스 분기가 있는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="efb30-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="efb30-112">PR은 릴리스 분기를 대상으로 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="efb30-113">릴리스 분기의 이름 패턴은 `release-<version>`입니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="efb30-114">끌어오기 요청 프로세스를 모든 사용자가 더 잘 작동할 수 있도록 설정</span><span class="sxs-lookup"><span data-stu-id="efb30-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="efb30-115">PR을 더 간단하고 더 중점적으로 만들수록 더 빠르게 검토 및 병합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="efb30-116">대량으로 파일을 업데이트하거나 관련 없는 변경 내용을 포함하는 분기를 방지</span><span class="sxs-lookup"><span data-stu-id="efb30-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="efb30-117">관련이 없는 변경 내용을 포함하는 PR을 만들지 마세요.</span><span class="sxs-lookup"><span data-stu-id="efb30-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="efb30-118">기존 문서에 대한 부 업데이트를 새 문서 또는 주요 다시 쓰기와 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="efb30-119">이러한 변경 작업은 별도의 작업 분기에서 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="efb30-120">대량 변경은 변경된 파일이 많은 PR을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="efb30-121">PR을 최대 50개의 변경된 파일로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="efb30-122">대량 PR은 검토하기 어렵고 오류를 포함할 가능성이 더 높습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="efb30-123">파일 이름 바꾸기 또는 삭제</span><span class="sxs-lookup"><span data-stu-id="efb30-123">Renaming or deleting files</span></span>

<span data-ttu-id="efb30-124">파일의 이름을 바꾸거나 삭제하는 경우 해당 PR과 연결된 문제가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="efb30-125">이 문제는 파일의 이름을 바꾸거나 파일을 삭제해야 하는 이유를 설명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="efb30-126">파일 이름 바꾸기 및 삭제를 사용하여 콘텐츠를 추가하거나 변경하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="efb30-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="efb30-127">이름이 바뀌거나 삭제된 파일은 모두 마스터 리디렉션 파일에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="efb30-128">가능하면 이름이 바뀌거나 삭제된 콘텐츠에 연결된 파일도 모두 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="efb30-129">여기에는 모든 TOC 파일이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="efb30-130">Docs PR 유효성 검사 서비스</span><span class="sxs-lookup"><span data-stu-id="efb30-130">Docs PR validation service</span></span>

<span data-ttu-id="efb30-131">Docs PR 유효성 검사 서비스는 PR에 포함된 파일에 대한 유효성 검사 규칙을 실행하는 GitHub 앱입니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="efb30-132">유효성 검사 서비스에서 보고한 오류 또는 경고(예외 참조)는 모두 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="efb30-133">다음 경고는 무시해도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="efb30-134">다음 동작을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="efb30-135">PR을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-135">You submit a PR.</span></span>
1. <span data-ttu-id="efb30-136">PR의 상태를 나타내는 GitHub 설명에서 리포지토리에서 사용하도록 설정된 “검사”의 상태를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="efb30-137">이 예제에서는 "Commit Validation" 및 "OpenPublishing.Build"의 두 가지 검사가 사용하도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![유효성 검사 상태 - 일부 검사가 실패함](media/pull-requests/validation-failed.png)

   <span data-ttu-id="efb30-139">커밋 유효성 검사에 실패한 경우에도 빌드가 통과할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="efb30-140">자세한 내용은 **세부 정보**를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efb30-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="efb30-141">세부 정보 페이지에는 문제를 해결하는 방법에 대한 정보와 함께 실패한 모든 유효성 검사가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="efb30-142">유효성 검사에 성공하면 다음과 같은 주석이 PR에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![유효성 검사 상태: 성공](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="efb30-144">외부(Microsoft 직원이 아닌) 기여자인 경우에는 자세한 빌드 보고서 또는 미리 보기 링크에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="efb30-145">PowerShell-Docs 팀 구성원이 PR을 검토할 때, 유효성 검사 보고서에 플래그가 지정된 문제를 변경 또는 수정하라는 요청을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="efb30-146">PowerShell-Docs 팀은 향후의 제출에서 이러한 문제를 해결하고 방지하는 방법을 이해하는 데 도움을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb30-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="efb30-147">다음 단계</span><span class="sxs-lookup"><span data-stu-id="efb30-147">Next steps</span></span>

[<span data-ttu-id="efb30-148">PowerShell-Docs 스타일 가이드</span><span class="sxs-lookup"><span data-stu-id="efb30-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="efb30-149">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="efb30-149">Additional resources</span></span>

[<span data-ttu-id="efb30-150">끌어오기 요청 관리 방법</span><span class="sxs-lookup"><span data-stu-id="efb30-150">How we manage pull requests</span></span>](managing-pull-requests.md)
