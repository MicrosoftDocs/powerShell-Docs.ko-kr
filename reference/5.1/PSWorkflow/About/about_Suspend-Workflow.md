---
description: 활동이 표시 되는 `Suspend-Workflow` 워크플로를 일시 중단 하는 활동에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_suspend-workflow?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Suspend 워크플로
ms.openlocfilehash: cbe5386ae5aa4bd863079fde240ddf2ce5384727
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221865"
---
# <a name="about-suspend-workflow"></a><span data-ttu-id="52317-104">Suspend-Workflow 정보</span><span class="sxs-lookup"><span data-stu-id="52317-104">About Suspend-Workflow</span></span>

## <a name="short-description"></a><span data-ttu-id="52317-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="52317-105">Short description</span></span>

<span data-ttu-id="52317-106">활동이 표시 되는 `Suspend-Workflow` 워크플로를 일시 중단 하는 활동에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="52317-106">Describes the `Suspend-Workflow` activity, which suspends the workflow in which the activity appears.</span></span>

## <a name="long-description"></a><span data-ttu-id="52317-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="52317-107">Long description</span></span>

<span data-ttu-id="52317-108">`Suspend-Workflow`활동은 워크플로 내에서 워크플로 처리를 일시적으로 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="52317-108">The `Suspend-Workflow` activity temporarily stops workflow processing from within the workflow.</span></span> <span data-ttu-id="52317-109">일시 중단 하기 전에 Windows PowerShell 워크플로는 검사점을 사용 하 여 워크플로의 상태와 데이터가 유지 되 고 워크플로가 일시 중단 지점에서 다시 시작 될 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="52317-109">Before suspending, Windows PowerShell Workflow takes a checkpoint so the workflow's state and data are preserved and the workflow can resume from the suspension point.</span></span>

<span data-ttu-id="52317-110">워크플로를 다시 시작 하려면 워크플로를 실행 하는 사용자가 cmdlet을 사용 합니다 `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="52317-110">To resume the workflow, the user running the workflow uses the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="52317-111">워크플로 내에서 워크플로를 다시 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52317-111">You can't resume a workflow from within the workflow.</span></span>

## <a name="syntax"></a><span data-ttu-id="52317-112">구문</span><span class="sxs-lookup"><span data-stu-id="52317-112">Syntax</span></span>

```
workflow <Verb-Noun>
{
    Suspend-Workflow
}
```

## <a name="detailed-description"></a><span data-ttu-id="52317-113">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="52317-113">Detailed description</span></span>

<span data-ttu-id="52317-114">는 `Suspend-Workflow` 워크플로를 일시적으로 중지 하 고 워크플로 작업을 나타내는 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="52317-114">The `Suspend-Workflow` temporarily stops the workflow and returns a job object that represents the workflow job.</span></span> <span data-ttu-id="52317-115">작업으로 워크플로를 실행 하지 않은 경우에도 작업 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52317-115">A job object is returned even if you didn't run the workflow as a job.</span></span> <span data-ttu-id="52317-116">예를 들어 **AsJob** 워크플로 일반 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52317-116">For example, such as by using the **AsJob** workflow common parameter.</span></span> <span data-ttu-id="52317-117">작업 상태가 **일시 중단** 됨입니다.</span><span class="sxs-lookup"><span data-stu-id="52317-117">The job state is **Suspended**.</span></span>

<span data-ttu-id="52317-118">작업 cmdlet을 사용 하 여 일시 중단 된 워크플로 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52317-118">You can use the job cmdlets to manage the suspended workflow job.</span></span> <span data-ttu-id="52317-119">워크플로 작업을 다시 시작 하려면 cmdlet을 사용 합니다 `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="52317-119">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span>

<span data-ttu-id="52317-120">워크플로 작업을 다시 시작 하면 해당 활동 뒤에 오는 명령에서 워크플로가 다시 시작 `Suspend-Workflow` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52317-120">When you resume the workflow job, the workflow resumes at the command that follows the `Suspend-Workflow` activity.</span></span>

<span data-ttu-id="52317-121">예를 들어 다음 워크플로에는 활동이 포함 되어 있습니다 `Suspend-Workflow` .</span><span class="sxs-lookup"><span data-stu-id="52317-121">For example, the following workflow includes the `Suspend-Workflow` activity.</span></span>
<span data-ttu-id="52317-122">워크플로를 실행 하는 경우 작업을 실행 하 고 `Get-Date` 해당 출력 `$a` 을 변수에 저장 한 다음 워크플로를 일시 중단 하 고 일시 중단 된 워크플로를 나타내는 job 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="52317-122">When you run the workflow, it runs the `Get-Date` activity, saves its output in the `$a` variable, and then suspends the workflow, and returns a job object that represents the suspended workflow.</span></span> <span data-ttu-id="52317-123">작업 유형은 **PSWorkflowJob** 입니다.</span><span class="sxs-lookup"><span data-stu-id="52317-123">The job type is **PSWorkflowJob**.</span></span>

<span data-ttu-id="52317-124">작업 cmdlet (예:)을 사용 `Get-Job` 하 여 워크플로 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52317-124">You can use the job cmdlets, such as `Get-Job`, to manage the workflow job.</span></span>

```powershell
Workflow Test-Suspend
{
    $a = Get-Date
    Suspend-Workflow
    (Get-Date)- $a
}

Test-Suspend
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Suspended  True         localhost Test-Suspend
```

## <a name="resuming-a-workflow-job"></a><span data-ttu-id="52317-125">워크플로 작업 다시 시작</span><span class="sxs-lookup"><span data-stu-id="52317-125">Resuming a workflow job</span></span>

<span data-ttu-id="52317-126">워크플로 작업을 다시 시작 하려면 cmdlet을 사용 합니다 `Resume-Job` .</span><span class="sxs-lookup"><span data-stu-id="52317-126">To resume the workflow job, use the `Resume-Job` cmdlet.</span></span> <span data-ttu-id="52317-127">`Resume-Job` cmdlet은 아직 다시 시작할 수 없는 경우에도 워크플로 작업 개체를 즉시 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52317-127">The `Resume-Job` cmdlet returns the workflow job object immediately, even though it might not yet be resumed.</span></span> <span data-ttu-id="52317-128">작업이 다시 시작 될 때까지 기다리려면 **wait** 매개 변수를 사용 하거나 cmdlet을 사용 `Get-Job` 하 여 현재 작업 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52317-128">To wait for the job to be resumed, use the **Wait** parameter, or use the `Get-Job` cmdlet to get the current job object.</span></span>

```powershell
Resume-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State    HasMoreData  Location  Command
--  ----  -------------  -----    -----------  --------  -------
8   Job8  PSWorkflowJob  Running  True         localhost Test-Suspend
```

```powershell
Get-Job -Name Job8
```

```Output
Id  Name  PSJobTypeName  State      HasMoreData  Location  Command
--  ----  -------------  -----      -----------  --------  -------
8   Job8  PSWorkflowJob  Completed  True         localhost Test-Suspend
```

## <a name="getting-the-output-of-a-workflow-job"></a><span data-ttu-id="52317-129">워크플로 작업의 출력 가져오기</span><span class="sxs-lookup"><span data-stu-id="52317-129">Getting the output of a workflow job</span></span>

<span data-ttu-id="52317-130">워크플로 작업의 출력을 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="52317-130">To get the output of a workflow job, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="52317-131">출력은 cmdlet을 수행한 명령에서 워크플로를 다시 시작 했음을 보여 줍니다 `Suspend-Workflow` .</span><span class="sxs-lookup"><span data-stu-id="52317-131">The output shows that the workflow resumed at the command that followed the `Suspend-Workflow` cmdlet.</span></span> <span data-ttu-id="52317-132">`$a`일시 중단 전에 채워진 변수의 값은 워크플로를 다시 시작할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52317-132">The value of the `$a` variable, which was populated before the suspension, is available to the workflow when it resumes.</span></span>

```powershell
Get-Job -Name Job8 | Receive-Job
```

```Output
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 19
Milliseconds      : 823
Ticks             : 198230041
TotalDays         : 0.000229432917824074
TotalHours        : 0.00550639002777778
TotalMinutes      : 0.330383401666667
TotalSeconds      : 19.8230041
TotalMilliseconds : 19823.0041
PSComputerName    : localhost
```

## <a name="see-also"></a><span data-ttu-id="52317-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52317-133">See also</span></span>

[<span data-ttu-id="52317-134">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="52317-134">about_Workflows</span></span>](about_Workflows.md)

[<span data-ttu-id="52317-135">about_WorkflowCommonParameters</span><span class="sxs-lookup"><span data-stu-id="52317-135">about_WorkflowCommonParameters</span></span>](about_WorkflowCommonParameters.md)

<span data-ttu-id="52317-136">[Psworkflow](xref:PSWorkflow) cmdlet</span><span class="sxs-lookup"><span data-stu-id="52317-136">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="52317-137">워크플로 가이드</span><span class="sxs-lookup"><span data-stu-id="52317-137">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="52317-138">Windows PowerShell 워크플로 작성</span><span class="sxs-lookup"><span data-stu-id="52317-138">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
