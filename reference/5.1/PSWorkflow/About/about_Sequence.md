---
description: '`Sequence`선택한 작업을 순차적으로 실행 하는 키워드에 대해 설명 합니다.'
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_sequence?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Sequence
ms.openlocfilehash: a9dd4fb24274fe4e1478ca69c734b43a2f196792
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221882"
---
# <a name="about-sequence"></a><span data-ttu-id="3372c-104">시퀀스 정보</span><span class="sxs-lookup"><span data-stu-id="3372c-104">About Sequence</span></span>

## <a name="short-description"></a><span data-ttu-id="3372c-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="3372c-105">Short description</span></span>

<span data-ttu-id="3372c-106">`Sequence`선택한 작업을 순차적으로 실행 하는 키워드에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-106">Describes the `Sequence` keyword that runs selected activities sequentially.</span></span>

## <a name="long-description"></a><span data-ttu-id="3372c-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-107">Long description</span></span>

<span data-ttu-id="3372c-108">`Sequence`키워드는 선택한 워크플로 활동을 순차적으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-108">The `Sequence` keyword runs selected workflow activities sequentially.</span></span> <span data-ttu-id="3372c-109">워크플로 작업은 표시 되는 순서 대로 실행 되며 동시에 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-109">Workflow activities run in the order that they appear and do not run concurrently.</span></span> <span data-ttu-id="3372c-110">`Sequence`키워드는 PowerShell 워크플로에서만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-110">The `Sequence` keyword is only valid in a PowerShell Workflow.</span></span>

<span data-ttu-id="3372c-111">`Sequence`키워드는 `Parallel` 스크립트 블록에서 선택 된 명령을 순차적으로 실행 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-111">The `Sequence` keyword is used in a `Parallel` script block to run selected commands sequentially.</span></span>

<span data-ttu-id="3372c-112">워크플로 작업은 기본적으로 순차적으로 실행 되므로 `Sequence` 키워드는 스크립트 블록 에서만 유효 `Parallel` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-112">Because workflow activities run sequentially by default, the `Sequence` keyword is only effective in a `Parallel` script block.</span></span> <span data-ttu-id="3372c-113">`Sequence`키워드가 스크립트 블록에 포함 되지 않은 경우 `Parallel` 유효 하지만 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-113">If the `Sequence` keyword isn't included in a `Parallel` script block, it's valid but ineffective.</span></span>

<span data-ttu-id="3372c-114">`Sequence`스크립트 블록을 사용 하면 종속 명령을 순차적으로 실행할 수 있으므로 더 많은 명령을 병렬로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-114">The `Sequence` script block lets you run more commands in parallel by allowing you to run dependent commands sequentially.</span></span>

## <a name="syntax"></a><span data-ttu-id="3372c-115">구문</span><span class="sxs-lookup"><span data-stu-id="3372c-115">Syntax</span></span>

### <a name="workflow-using-sequence"></a><span data-ttu-id="3372c-116">시퀀스를 사용 하는 워크플로</span><span class="sxs-lookup"><span data-stu-id="3372c-116">Workflow using Sequence</span></span>

```
workflow <Verb-Noun>
{
    Sequence
    {
        [<Activity>]
        [<Activity>]
        # ...
    }
}
```

### <a name="workflow-using-parallel-and-sequence"></a><span data-ttu-id="3372c-117">병렬 및 시퀀스를 사용 하는 워크플로</span><span class="sxs-lookup"><span data-stu-id="3372c-117">Workflow using Parallel and Sequence</span></span>

```
workflow <Verb-Noun>
{
    Parallel
    {
        [<Activity>]
        Sequence
        {
            [<Activity>]
            [<Activity>]
            # ...
        }
    }
}
```

## <a name="detailed-description"></a><span data-ttu-id="3372c-118">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="3372c-118">Detailed description</span></span>

<span data-ttu-id="3372c-119">`Parallel` 스크립트 블록의 명령은 동시에 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-119">The commands in a `Parallel` script block can run concurrently.</span></span> <span data-ttu-id="3372c-120">실행 순서가 정해져 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-120">The order in which they run is not determined.</span></span> <span data-ttu-id="3372c-121">이 기능은 스크립트 워크플로의 성능을 향상 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-121">This feature improves the performance of a script workflow.</span></span>

<span data-ttu-id="3372c-122">`Sequence`활동을 스크립트 블록에 표시 하더라도 스크립트 블록을 사용 하 여 선택한 활동을 순차적으로 실행할 수 있습니다 `Parallel` .</span><span class="sxs-lookup"><span data-stu-id="3372c-122">You can use a `Sequence` script block to run selected activities sequentially, even though the activities appear in a `Parallel` script block.</span></span>

<span data-ttu-id="3372c-123">스크립트 블록의 활동은 `Sequence` 나열 된 순서 대로 연속적으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-123">The activities in a `Sequence` script block run consecutively in the order that they are listed.</span></span> <span data-ttu-id="3372c-124">스크립트 블록의 작업은 `Sequence` 이전 작업이 완료 된 후에만 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-124">An activity in a `Sequence` script block starts only after the previous activity completes.</span></span>

<span data-ttu-id="3372c-125">그러나 스크립트 블록이 스크립트 블록에 표시 되 면 스크립트 블록을 실행 하는 `Sequence` `Parallel` 순서는 `Sequence` 결정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-125">However, when the `Sequence` script block appears in a `Parallel` script block, the order in which the `Sequence` script block runs isn't determined.</span></span> <span data-ttu-id="3372c-126">스크립트 블록에서 다른 작업을 수행 하기 전이나 후에 실행 될 수 있습니다 `Parallel` .</span><span class="sxs-lookup"><span data-stu-id="3372c-126">It might run before, after, or concurrent with other activities in the `Parallel` script block.</span></span>

<span data-ttu-id="3372c-127">예를 들어 다음 워크플로에는 `Parallel` 컴퓨터의 프로세스 및 서비스를 가져오는 활동을 실행 하는 스크립트 블록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-127">For example, the following workflow includes a `Parallel` script block that runs activities that get processes and services on the computer.</span></span> <span data-ttu-id="3372c-128">`Parallel`스크립트 블록에는 `Sequence` 파일에서 정보를 가져오고 스크립트에 대 한 입력으로 정보를 사용 하는 스크립트 블록이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-128">The `Parallel` script block contains a `Sequence` script block that gets information from a file and uses the information as input to a script.</span></span>

<span data-ttu-id="3372c-129">`Get-Process`, `Get-Service` 및 핫픽스 관련 명령은 서로 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-129">The `Get-Process`, `Get-Service`, and hotfix-related commands are independent of each other.</span></span> <span data-ttu-id="3372c-130">명령은 순서에 관계 없이 동시에 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-130">The commands can run concurrently or in any order.</span></span> <span data-ttu-id="3372c-131">그러나 핫픽스 정보를 가져오는 명령은이 명령을 사용 하는 명령을 실행 하기 전에 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3372c-131">But, the command that gets the hotfix information must run before the command that uses it.</span></span>

```powershell
workflow Test-Workflow
{
    Parallel
    {
    Get-Process
    Get-Service

    Sequence
    {
        $Hotfix = Get-Content 'D:\HotFixes\Required.txt'
        Foreach ($h in $Hotfix) {'D:\Scripts\Verify-Hotfix' -Hotfix $h}
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="3372c-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3372c-132">See also</span></span>

[<span data-ttu-id="3372c-133">about_ForEach</span><span class="sxs-lookup"><span data-stu-id="3372c-133">about_ForEach</span></span>](../../Microsoft.PowerShell.Core/About/about_Foreach.md)

[<span data-ttu-id="3372c-134">about_ForEach-병렬</span><span class="sxs-lookup"><span data-stu-id="3372c-134">about_ForEach-Parallel</span></span>](about_ForEach-Parallel.md)

[<span data-ttu-id="3372c-135">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="3372c-135">about_Language_Keywords</span></span>](../../Microsoft.PowerShell.Core/About/about_Language_Keywords.md)

[<span data-ttu-id="3372c-136">about_Parallel</span><span class="sxs-lookup"><span data-stu-id="3372c-136">about_Parallel</span></span>](about_Parallel.md)

[<span data-ttu-id="3372c-137">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="3372c-137">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="3372c-138">Windows PowerShell 스크립트를 사용하여 워크플로 만들기</span><span class="sxs-lookup"><span data-stu-id="3372c-138">Creating a Workflow by Using a Windows PowerShell Script</span></span>](/previous-versions/powershell/scripting/developer/workflow/creating-a-workflow-by-using-a-windows-powershell-script)
