---
title: 문제 관리 방법
description: 이 문서에서는 PowerShell-Docs 팀이 끌어오기 요청을 관리하는 방법을 설명합니다.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: cd7aba83d42a6a2eba1ce73910fdd34096342c21
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "79060278"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="f12aa-103">문제 관리 방법</span><span class="sxs-lookup"><span data-stu-id="f12aa-103">How we manage issues</span></span>

<span data-ttu-id="f12aa-104">이 문서에서는 Microsoft가 PowerShell-Docs 리포지토리에서 문제를 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="f12aa-105">이 문서는 PowerShell-Docs 팀 구성원을 위한 작업 보조 도구이며,</span><span class="sxs-lookup"><span data-stu-id="f12aa-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="f12aa-106">일반 기여자에게 프로세스의 투명도를 공개하기 위해 게시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="f12aa-107">문제 출처</span><span class="sxs-lookup"><span data-stu-id="f12aa-107">Sources of issues</span></span>

- <span data-ttu-id="f12aa-108">커뮤니티 기여자</span><span class="sxs-lookup"><span data-stu-id="f12aa-108">Community contributors</span></span>
- <span data-ttu-id="f12aa-109">내부 기여자</span><span class="sxs-lookup"><span data-stu-id="f12aa-109">Internal contributors</span></span>
- <span data-ttu-id="f12aa-110">소셜 미디어 채널에 게시된 댓글 전사</span><span class="sxs-lookup"><span data-stu-id="f12aa-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="f12aa-111">Docs 피드백 양식을 통한 피드백</span><span class="sxs-lookup"><span data-stu-id="f12aa-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="f12aa-112">목표 응답 시간</span><span class="sxs-lookup"><span data-stu-id="f12aa-112">Response time targets</span></span>

- <span data-ttu-id="f12aa-113">심사 - 영업일 기준 5일</span><span class="sxs-lookup"><span data-stu-id="f12aa-113">Triaged - 5 business days</span></span>
- <span data-ttu-id="f12aa-114">수정 또는 변경 - 특정 목표 없음 - 최선의 노력 기울임</span><span class="sxs-lookup"><span data-stu-id="f12aa-114">Fix or change - no specific target - best effort only</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="f12aa-115">레이블 및 중요 시점</span><span class="sxs-lookup"><span data-stu-id="f12aa-115">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="f12aa-116">레이블 형식</span><span class="sxs-lookup"><span data-stu-id="f12aa-116">Label Types</span></span>

|<span data-ttu-id="f12aa-117">접두사</span><span class="sxs-lookup"><span data-stu-id="f12aa-117">Prefix</span></span>  | <span data-ttu-id="f12aa-118">Description</span><span class="sxs-lookup"><span data-stu-id="f12aa-118">Description</span></span>                                                         |
|------- | --------------------------------------------------------------------|
|<span data-ttu-id="f12aa-119">영역</span><span class="sxs-lookup"><span data-stu-id="f12aa-119">Area</span></span>    | <span data-ttu-id="f12aa-120">PowerShell 또는 문서에서 문제가 설명하는 부분을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-120">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="f12aa-121">기능 소유자가 해당 기능에 대한 문제를 찾는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-121">Useful for feature owners to find issues for their feature.</span></span>|
|<span data-ttu-id="f12aa-122">Pri</span><span class="sxs-lookup"><span data-stu-id="f12aa-122">Pri</span></span>     | <span data-ttu-id="f12aa-123">문제의 우선 순위를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-123">Used to indicate the priority of the issue.</span></span> <span data-ttu-id="f12aa-124">값 범위는 0~4입니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-124">Value range 0-4.</span></span>        |
|<span data-ttu-id="f12aa-125">문제</span><span class="sxs-lookup"><span data-stu-id="f12aa-125">Issue</span></span>   | <span data-ttu-id="f12aa-126">문제에 대한 피드백의 유형을 분류하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-126">Used to classify the type of feedback for issue</span></span>                     |
|<span data-ttu-id="f12aa-127">검토</span><span class="sxs-lookup"><span data-stu-id="f12aa-127">Review</span></span>  | <span data-ttu-id="f12aa-128">팀에서 추가로 검토해야 하는 문제에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-128">Used for issue that require further review by the team</span></span>              |
|<span data-ttu-id="f12aa-129">상태</span><span class="sxs-lookup"><span data-stu-id="f12aa-129">Status</span></span>  | <span data-ttu-id="f12aa-130">작업 항목의 상태를 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-130">Used to indicate the status of the work item</span></span>                        |
|<span data-ttu-id="f12aa-131">대기</span><span class="sxs-lookup"><span data-stu-id="f12aa-131">Waiting</span></span> | <span data-ttu-id="f12aa-132">무언가를 기다리는 중임을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-132">Used to indicate that we are waiting on something</span></span>                   |

#### <a name="milestones"></a><span data-ttu-id="f12aa-133">중요 시점</span><span class="sxs-lookup"><span data-stu-id="f12aa-133">Milestones</span></span>

<span data-ttu-id="f12aa-134">문제 및 PR은 적절한 마일스톤으로 태그를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-134">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="f12aa-135">문제가 특정 버전을 대상으로 하지 않는 경우 마일스톤이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-135">If the issue is not targeted for a specific version then no milestone is used.</span></span> <span data-ttu-id="f12aa-136">PowerShell 코드베이스에 아직 병합되지 않은 변경 내용에 대한 Docs PR 문제는 **향후** 마일스톤에 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-136">Issues for Docs PRs for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="f12aa-137">코드 변경 내용이 병합된 이후에는 마일스톤을 적절한 버전으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-137">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="f12aa-138">Milestone</span><span class="sxs-lookup"><span data-stu-id="f12aa-138">Milestone</span></span>     |                    <span data-ttu-id="f12aa-139">Description</span><span class="sxs-lookup"><span data-stu-id="f12aa-139">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="f12aa-140">6.x</span><span class="sxs-lookup"><span data-stu-id="f12aa-140">6.x</span></span>              | <span data-ttu-id="f12aa-141">PowerShell 6.0~6.2.x 관련 작업 항목</span><span class="sxs-lookup"><span data-stu-id="f12aa-141">Work items related to PowerShell 6.0 through 6.2.x</span></span> |
| <span data-ttu-id="f12aa-142">7.0.0</span><span class="sxs-lookup"><span data-stu-id="f12aa-142">7.0.0</span></span>            | <span data-ttu-id="f12aa-143">PowerShell 7.0 관련 작업 항목</span><span class="sxs-lookup"><span data-stu-id="f12aa-143">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="f12aa-144">7.1.0</span><span class="sxs-lookup"><span data-stu-id="f12aa-144">7.1.0</span></span>            | <span data-ttu-id="f12aa-145">PowerShell 7.1 관련 작업 항목</span><span class="sxs-lookup"><span data-stu-id="f12aa-145">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="f12aa-146">미래</span><span class="sxs-lookup"><span data-stu-id="f12aa-146">Future</span></span>           | <span data-ttu-id="f12aa-147">PowerShell 향후 버전 작업 항목</span><span class="sxs-lookup"><span data-stu-id="f12aa-147">Work items a future version of PowerShell</span></span>          |
| <span data-ttu-id="f12aa-148">PSReadline-vNext</span><span class="sxs-lookup"><span data-stu-id="f12aa-148">PSReadline-vNext</span></span> | <span data-ttu-id="f12aa-149">PSReadline 향후 버전 작업 항목</span><span class="sxs-lookup"><span data-stu-id="f12aa-149">Work items a future version of PSReadline</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="f12aa-150">프로세스 심사</span><span class="sxs-lookup"><span data-stu-id="f12aa-150">Triage process</span></span>

<span data-ttu-id="f12aa-151">PowerShell Docs 팀은 매주 한 번 회의를 열고 마지막 회의 이후 추가된 문제에 대해 논의합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-151">The PowerShell docs team meets once per week to discuss any issues added since last meeting.</span></span> <span data-ttu-id="f12aa-152">문제는 레이블이나 소유자가 할당되면 심사된 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-152">An issue is considered to have been triaged when labels have been assigned or an owner has been assigned.</span></span> <span data-ttu-id="f12aa-153">PowerShell Docs 팀 구성원들은 매일 문제를 검토하고 새로운 문제가 도착하는 대로 심사하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-153">PowerShell docs team members are encouraged to review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="f12aa-154">그런 다음 주간 심사 회의에서 필요에 따라 새로운 문제를 더 자세히 논의합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-154">The weekly triage meeting can then be used to discuss the new issues in more detail, as needed.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="f12aa-155">잘못 배치된 제품 피드백</span><span class="sxs-lookup"><span data-stu-id="f12aa-155">Misplaced product feedback</span></span>

- <span data-ttu-id="f12aa-156">고객에게 해당 내용이 제품 피드백이라는 설명을 입력하고 적절한 피드백 채널에 대한 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-156">Enter a comment for the customer indicating it is product feedback and provide a link to the appropriate feedback channel.</span></span>
- <span data-ttu-id="f12aa-157">선택 사항: 문제를 적절한 제품 피드백 위치로 복사하고 복사된 항목에 대한 링크를 추가한 다음 문제를 종결합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-157">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="f12aa-158">문제를 UserVoice로 복사하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f12aa-158">DO NOT copy issues to UserVoice.</span></span>

  | <span data-ttu-id="f12aa-159">DocSet</span><span class="sxs-lookup"><span data-stu-id="f12aa-159">DocSet</span></span>    | <span data-ttu-id="f12aa-160">제품 피드백 URL</span><span class="sxs-lookup"><span data-stu-id="f12aa-160">Product Feedback URL</span></span>                                         |
  | --------- | ------------------------------------------------------------ |
  | <span data-ttu-id="f12aa-161">developer</span><span class="sxs-lookup"><span data-stu-id="f12aa-161">developer</span></span> | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | <span data-ttu-id="f12aa-162">dsc</span><span class="sxs-lookup"><span data-stu-id="f12aa-162">dsc</span></span>       | https://windowsserver.uservoice.com/forums/301869-powershell |
  | <span data-ttu-id="f12aa-163">gallery</span><span class="sxs-lookup"><span data-stu-id="f12aa-163">gallery</span></span>   | https://github.com/powershell/powershellgallery/issues/new   |
  | <span data-ttu-id="f12aa-164">jea</span><span class="sxs-lookup"><span data-stu-id="f12aa-164">jea</span></span>       | https://github.com/powershell/jea/issues/new                 |
  | <span data-ttu-id="f12aa-165">reference</span><span class="sxs-lookup"><span data-stu-id="f12aa-165">reference</span></span> | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | <span data-ttu-id="f12aa-166">wmf</span><span class="sxs-lookup"><span data-stu-id="f12aa-166">wmf</span></span>       | https://windowsserver.uservoice.com/forums/301869-powershell |

### <a name="support-requests"></a><span data-ttu-id="f12aa-167">지원 요청</span><span class="sxs-lookup"><span data-stu-id="f12aa-167">Support requests</span></span>

- <span data-ttu-id="f12aa-168">지원 질문이 단순한 경우 정중히 답변하고 문제를 종결합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-168">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="f12aa-169">질문이 더 복잡하거나 제출자가 추가 질문으로 회신하는 경우 포럼 및 지원 채널로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-169">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="f12aa-170">포럼으로 리디렉션하기 위한 텍스트 제안:</span><span class="sxs-lookup"><span data-stu-id="f12aa-170">Suggested text for redirecting to forums:</span></span>

    > <span data-ttu-id="f12aa-171">이 포럼은 이러한 종류의 질문에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-171">This is not the right forum for these kinds of questions.</span></span> <span data-ttu-id="f12aa-172">커뮤니티 지원 포럼에 질문을 게시해 보세요.</span><span class="sxs-lookup"><span data-stu-id="f12aa-172">Try posting your question in a community support forum.</span></span> <span data-ttu-id="f12aa-173">커뮤니티 포럼 목록은 다음을 참조하세요. https://docs.microsoft.com/powershell/scripting/community/community-support</span><span class="sxs-lookup"><span data-stu-id="f12aa-173">For a list of community forums see: https://docs.microsoft.com/powershell/scripting/community/community-support</span></span>

### <a name="code-of-conduct-violations"></a><span data-ttu-id="f12aa-174">사용 규정 위반</span><span class="sxs-lookup"><span data-stu-id="f12aa-174">Code of conduct violations</span></span>

- <span data-ttu-id="f12aa-175">필요한 경우 문제를 편집하여 악의적인 콘텐츠를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-175">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="f12aa-176">해당 문제가 스팸이라는 설명을 입력하고, 문제를 종결한 다음 잠가 의견 추가를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-176">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="f12aa-177">이러한 사례가 발생할 때마다 주간 심사에서 논의하여 추가 조치(GitHub 또는 Microsoft 법률 부서에 보고)가 필요한지 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f12aa-177">Each occurrence of this should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
