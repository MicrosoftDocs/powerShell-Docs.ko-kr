---
title: 문제 관리 방법
description: 이 문서에서는 PowerShell-Docs 팀이 문제를 관리하는 방법을 설명합니다.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/12/2020
ms.locfileid: "99599323"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="6b815-103">문제 관리 방법</span><span class="sxs-lookup"><span data-stu-id="6b815-103">How we manage issues</span></span>

<span data-ttu-id="6b815-104">이 문서에서는 Microsoft가 PowerShell-Docs 리포지토리에서 문제를 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="6b815-105">이 문서는 PowerShell-Docs 팀 구성원을 위한 작업 보조 도구이며,</span><span class="sxs-lookup"><span data-stu-id="6b815-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="6b815-106">공용 참가자에 대 한 프로세스 투명도를 제공 하기 위해 여기에 게시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-106">It's published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="6b815-107">문제 출처</span><span class="sxs-lookup"><span data-stu-id="6b815-107">Sources of issues</span></span>

- <span data-ttu-id="6b815-108">커뮤니티 기여자</span><span class="sxs-lookup"><span data-stu-id="6b815-108">Community contributors</span></span>
- <span data-ttu-id="6b815-109">내부 기여자</span><span class="sxs-lookup"><span data-stu-id="6b815-109">Internal contributors</span></span>
- <span data-ttu-id="6b815-110">소셜 미디어 채널에 게시된 댓글 전사</span><span class="sxs-lookup"><span data-stu-id="6b815-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="6b815-111">Docs 피드백 양식을 통한 피드백</span><span class="sxs-lookup"><span data-stu-id="6b815-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="6b815-112">목표 응답 시간</span><span class="sxs-lookup"><span data-stu-id="6b815-112">Response time targets</span></span>

<span data-ttu-id="6b815-113">80%의 새 문제는 영업일 3 일 이내에 종결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-113">80% of new issues are closed within 3 business days.</span></span>

- <span data-ttu-id="6b815-114">심사-영업일 1 일</span><span class="sxs-lookup"><span data-stu-id="6b815-114">Triaged - 1 business days</span></span>
- <span data-ttu-id="6b815-115">해결 또는 변경-영업일 10 일</span><span class="sxs-lookup"><span data-stu-id="6b815-115">Fix or change - 10 business days</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="6b815-116">레이블 및 중요 시점</span><span class="sxs-lookup"><span data-stu-id="6b815-116">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="6b815-117">레이블 형식</span><span class="sxs-lookup"><span data-stu-id="6b815-117">Label Types</span></span>

|   <span data-ttu-id="6b815-118">Type</span><span class="sxs-lookup"><span data-stu-id="6b815-118">Type</span></span>   | <span data-ttu-id="6b815-119">Description</span><span class="sxs-lookup"><span data-stu-id="6b815-119">Description</span></span>                                                         |
| -------- | ------------------------------------------------------------------- |
| <span data-ttu-id="6b815-120">영역</span><span class="sxs-lookup"><span data-stu-id="6b815-120">Area</span></span>     | <span data-ttu-id="6b815-121">PowerShell 또는 문서에서 문제가 설명하는 부분을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-121">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="6b815-122">기능 소유자가 해당 기능에 대한 문제를 찾는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-122">Useful for feature owners to find issues for their feature.</span></span> |
| <span data-ttu-id="6b815-123">문제</span><span class="sxs-lookup"><span data-stu-id="6b815-123">Issue</span></span>    | <span data-ttu-id="6b815-124">문제의 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-124">Indicates the type of issue</span></span>                                         |
| <span data-ttu-id="6b815-125">우선 순위</span><span class="sxs-lookup"><span data-stu-id="6b815-125">Priority</span></span> | <span data-ttu-id="6b815-126">문제의 우선 순위를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-126">Indicates the priority of the issue.</span></span> <span data-ttu-id="6b815-127">값 범위 0 (높음)-4 (낮음)</span><span class="sxs-lookup"><span data-stu-id="6b815-127">Value range 0 (high) -4 (low)</span></span>  |
| <span data-ttu-id="6b815-128">상태</span><span class="sxs-lookup"><span data-stu-id="6b815-128">Status</span></span>   | <span data-ttu-id="6b815-129">작업 항목의 상태 또는 종결 된 이유를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-129">Indicates the status of the work item or why it was closed</span></span>          |
| <span data-ttu-id="6b815-130">태그</span><span class="sxs-lookup"><span data-stu-id="6b815-130">Tag</span></span>      | <span data-ttu-id="6b815-131">추가 분류에 사용 되는 레이블</span><span class="sxs-lookup"><span data-stu-id="6b815-131">Labels used to for additional classification</span></span>                        |
| <span data-ttu-id="6b815-132">대기 중</span><span class="sxs-lookup"><span data-stu-id="6b815-132">Waiting</span></span>  | <span data-ttu-id="6b815-133">다른 이벤트에서 대기 중임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-133">Indicates that we're waiting on someone or some other event</span></span>         |

#### <a name="milestones"></a><span data-ttu-id="6b815-134">중요 시점</span><span class="sxs-lookup"><span data-stu-id="6b815-134">Milestones</span></span>

<span data-ttu-id="6b815-135">문제 및 PR은 적절한 마일스톤으로 태그를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-135">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="6b815-136">문제가 특정 버전에 적용 되지 않는 경우에는 마일스 톤이 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-136">If the issue doesn't apply to a specific version, then no milestone is used.</span></span> <span data-ttu-id="6b815-137">PowerShell 코드 베이스에 아직 병합 되지 않은 변경 내용에 대 한 Pr 및 관련 문제는 **이후** 마일스 톤에 할당 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-137">PRs and related issues for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="6b815-138">코드 변경 내용이 병합된 이후에는 마일스톤을 적절한 버전으로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-138">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="6b815-139">Milestone</span><span class="sxs-lookup"><span data-stu-id="6b815-139">Milestone</span></span>     |                    <span data-ttu-id="6b815-140">Description</span><span class="sxs-lookup"><span data-stu-id="6b815-140">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="6b815-141">7.0.0</span><span class="sxs-lookup"><span data-stu-id="6b815-141">7.0.0</span></span>            | <span data-ttu-id="6b815-142">PowerShell 7.0 관련 작업 항목</span><span class="sxs-lookup"><span data-stu-id="6b815-142">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="6b815-143">7.1.0</span><span class="sxs-lookup"><span data-stu-id="6b815-143">7.1.0</span></span>            | <span data-ttu-id="6b815-144">PowerShell 7.1 관련 작업 항목</span><span class="sxs-lookup"><span data-stu-id="6b815-144">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="6b815-145">7.2.0</span><span class="sxs-lookup"><span data-stu-id="6b815-145">7.2.0</span></span>            | <span data-ttu-id="6b815-146">PowerShell 7.2 관련 작업 항목</span><span class="sxs-lookup"><span data-stu-id="6b815-146">Work items related to PowerShell 7.2</span></span>               |
| <span data-ttu-id="6b815-147">미래</span><span class="sxs-lookup"><span data-stu-id="6b815-147">Future</span></span>           | <span data-ttu-id="6b815-148">PowerShell 향후 버전 작업 항목</span><span class="sxs-lookup"><span data-stu-id="6b815-148">Work items a future version of PowerShell</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="6b815-149">프로세스 심사</span><span class="sxs-lookup"><span data-stu-id="6b815-149">Triage process</span></span>

<span data-ttu-id="6b815-150">PowerShell docs 팀 구성원은 문제를 매일 검토 하 고 새로운 문제가 도착 하면이를 심사 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-150">PowerShell docs team members review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="6b815-151">팀에서 심사가 필요한 문제를 논의 하거나 해결 되지 않은 상태를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-151">The team meets weekly to discuss issues that need triage or remain unresolved.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="6b815-152">잘못 배치된 제품 피드백</span><span class="sxs-lookup"><span data-stu-id="6b815-152">Misplaced product feedback</span></span>

- <span data-ttu-id="6b815-153">고객을 올바른 피드백 채널로 리디렉션하는 메모를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-153">Enter a comment redirecting the customer to the correct feedback channel.</span></span>
- <span data-ttu-id="6b815-154">선택 사항: 문제를 적절한 제품 피드백 위치로 복사하고 복사된 항목에 대한 링크를 추가한 다음 문제를 종결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-154">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="6b815-155">문제를 UserVoice로 복사하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="6b815-155">DO NOT copy issues to UserVoice.</span></span>

  <span data-ttu-id="6b815-156">PowerShell 문제에 대 한 기본 위치는 [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) 입니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-156">The default location for PowerShell issues is [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

  <span data-ttu-id="6b815-157">다음 주제 영역에는 문제에 대 한 여러 위치가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-157">The following subject areas have different locations for issues:</span></span>

  | <span data-ttu-id="6b815-158">제목</span><span class="sxs-lookup"><span data-stu-id="6b815-158">Subjects</span></span> |                                                     <span data-ttu-id="6b815-159">제품 피드백 URL</span><span class="sxs-lookup"><span data-stu-id="6b815-159">Product Feedback URL</span></span>                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | <span data-ttu-id="6b815-160">dsc</span><span class="sxs-lookup"><span data-stu-id="6b815-160">dsc</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | <span data-ttu-id="6b815-161">gallery</span><span class="sxs-lookup"><span data-stu-id="6b815-161">gallery</span></span>  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | <span data-ttu-id="6b815-162">jea</span><span class="sxs-lookup"><span data-stu-id="6b815-162">jea</span></span>      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | <span data-ttu-id="6b815-163">wmf</span><span class="sxs-lookup"><span data-stu-id="6b815-163">wmf</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a><span data-ttu-id="6b815-164">지원 요청</span><span class="sxs-lookup"><span data-stu-id="6b815-164">Support requests</span></span>

- <span data-ttu-id="6b815-165">지원 질문이 단순한 경우 정중히 답변하고 문제를 종결합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-165">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="6b815-166">질문이 더 복잡하거나 제출자가 추가 질문으로 회신하는 경우 포럼 및 지원 채널로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-166">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="6b815-167">포럼으로 리디렉션하기 위한 텍스트 제안:</span><span class="sxs-lookup"><span data-stu-id="6b815-167">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="6b815-168">사용 규정 위반</span><span class="sxs-lookup"><span data-stu-id="6b815-168">Code of conduct violations</span></span>

- <span data-ttu-id="6b815-169">필요한 경우 문제를 편집하여 악의적인 콘텐츠를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-169">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="6b815-170">해당 문제가 스팸이라는 설명을 입력하고, 문제를 종결한 다음 잠가 의견 추가를 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-170">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="6b815-171">각 위반을 주간 심사에서 논의 하 여 추가 작업 (GitHub 또는 Microsoft 법률 보고서)에 대 한 필요성을 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b815-171">Each violation should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
