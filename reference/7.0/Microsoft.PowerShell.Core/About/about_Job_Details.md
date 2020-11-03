---
description: 로컬 및 원격 컴퓨터의 백그라운드 작업에 대 한 세부 정보를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_job_details?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Job_Details
ms.openlocfilehash: 0d85cd242c8e79281fa8be153b0e140660f16c1a
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2020
ms.locfileid: "93224634"
---
# <a name="about-job-details"></a><span data-ttu-id="cc1a3-104">작업 정보 정보</span><span class="sxs-lookup"><span data-stu-id="cc1a3-104">About Job Details</span></span>

## <a name="short-description"></a><span data-ttu-id="cc1a3-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="cc1a3-105">Short description</span></span>
<span data-ttu-id="cc1a3-106">로컬 및 원격 컴퓨터의 백그라운드 작업에 대 한 세부 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-106">Provides details about background jobs on local and remote computers.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="cc1a3-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="cc1a3-107">Detailed description</span></span>

<span data-ttu-id="cc1a3-108">이 항목에서는 백그라운드 작업의 개념에 대해 설명 하 고 PowerShell에서 백그라운드 작업의 작동 방식에 대 한 기술 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-108">This topic explains the concept of a background job and provides technical information about how background jobs work in PowerShell.</span></span>

<span data-ttu-id="cc1a3-109">이 항목은 [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md)및 [about_Remote_Jobs](about_Remote_Jobs.md) 항목에 대 한 추가 자료입니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-109">This topic is a supplement to the [about_Jobs](about_Jobs.md), [about_Thread_Jobs](about_Thread_Jobs.md), and [about_Remote_Jobs](about_Remote_Jobs.md) topics.</span></span>

### <a name="about-background-jobs"></a><span data-ttu-id="cc1a3-110">백그라운드 작업 정보</span><span class="sxs-lookup"><span data-stu-id="cc1a3-110">About background jobs</span></span>

<span data-ttu-id="cc1a3-111">백그라운드 작업은 명령 또는 식을 비동기식으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-111">A background job runs a command or expression asynchronously.</span></span> <span data-ttu-id="cc1a3-112">Cmdlet, 함수, 스크립트 또는 다른 명령 기반 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-112">It might run a cmdlet, a function, a script, or any other command-based task.</span></span> <span data-ttu-id="cc1a3-113">이는 오랜 시간 동안 실행 되는 명령을 실행 하도록 설계 되었지만이를 사용 하 여 백그라운드에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-113">It is designed to run commands that take an extended period of time, but you can use it to run any command in the background.</span></span>

<span data-ttu-id="cc1a3-114">동기식 명령이 실행 되 면 명령이 완료 될 때까지 PowerShell 명령 프롬프트가 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-114">When a synchronous command runs, the PowerShell command prompt is suppressed until the command is complete.</span></span> <span data-ttu-id="cc1a3-115">그러나 백그라운드 작업은 PowerShell 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-115">But a background job does not suppress the PowerShell prompt.</span></span> <span data-ttu-id="cc1a3-116">백그라운드 작업을 시작 하는 명령은 job 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-116">A command to start a background job returns a job object.</span></span>
<span data-ttu-id="cc1a3-117">메시지가 즉시 반환 되므로 백그라운드 작업이 실행 되는 동안 다른 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-117">The prompt returns immediately so you can work on other tasks while the background job runs.</span></span>

<span data-ttu-id="cc1a3-118">그러나 백그라운드 작업을 시작 하면 작업이 매우 빠르게 실행 되더라도 결과가 즉시 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-118">However, when you start a background job, you do not get the results immediately even if the job runs very quickly.</span></span> <span data-ttu-id="cc1a3-119">반환 되는 작업 개체에는 작업에 대 한 유용한 정보가 포함 되어 있지만 작업 결과는 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-119">The job object that is returned contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="cc1a3-120">작업 결과를 가져오려면 별도의 명령을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-120">You must run a separate command to get the job results.</span></span> <span data-ttu-id="cc1a3-121">또한 명령을 실행 하 여 작업을 중지 하 고, 작업이 완료 될 때까지 기다리거나, 작업을 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-121">You can also run commands to stop the job, to wait for the job to be completed, and to delete the job.</span></span>

<span data-ttu-id="cc1a3-122">백그라운드 작업의 타이밍을 다른 명령과 독립적으로 만들기 위해 각 백그라운드 작업은 자체 PowerShell 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-122">To make the timing of a background job independent of other commands, each background job runs in its own PowerShell session.</span></span> <span data-ttu-id="cc1a3-123">그러나이는 작업을 실행 하는 경우에만 생성 되 고 삭제 되는 임시 연결 일 수 있습니다. 또는 여러 관련 작업 또는 명령을 실행 하는 데 사용할 수 있는 영구적인 **PSSession** 이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-123">However, this can be a temporary connection that is created only to run the job and is then destroyed, or it can be a persistent **PSSession** that you can use to run several related jobs or commands.</span></span>

### <a name="using-the-job-cmdlets"></a><span data-ttu-id="cc1a3-124">작업 cmdlet 사용</span><span class="sxs-lookup"><span data-stu-id="cc1a3-124">Using the job cmdlets</span></span>

<span data-ttu-id="cc1a3-125">명령을 사용 `Start-Job` 하 여 로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-125">Use a `Start-Job` command to start a background job on a local computer.</span></span>
<span data-ttu-id="cc1a3-126">`Start-Job` 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-126">`Start-Job` returns a job object.</span></span> <span data-ttu-id="cc1a3-127">Cmdlet을 사용 하 여 로컬 컴퓨터에서 시작 된 작업을 나타내는 개체를 가져올 수도 있습니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="cc1a3-127">You can also get objects representing the jobs that were started on the local computer using the `Get-Job` cmdlet.</span></span>

<span data-ttu-id="cc1a3-128">작업 결과를 가져오려면 `Receive-Job` 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-128">To get the job results, use a `Receive-Job` command.</span></span> <span data-ttu-id="cc1a3-129">작업이 완료 되지 않으면에서 `Receive-Job` 일부 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-129">If the job is not complete, `Receive-Job` returns partial results.</span></span> <span data-ttu-id="cc1a3-130">Cmdlet을 사용 하 여 `Wait-Job` 세션에서 시작 된 작업 중 하나 또는 모두가 완료 될 때까지 명령 프롬프트를 표시 하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-130">You can also use the `Wait-Job` cmdlet to suppress the command prompt until one or all of the jobs that were started in the session are complete.</span></span>

<span data-ttu-id="cc1a3-131">백그라운드 작업을 중지 하려면 cmdlet을 사용 `Stop-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-131">To stop a background job, use the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="cc1a3-132">작업을 삭제 하려면 cmdlet을 사용 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-132">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="cc1a3-133">Cmdlet의 작동 방식에 대 한 자세한 내용은 각 cmdlet에 대 한 도움말 항목을 참조 하 고 [about_Jobs](about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-133">For more information about how the cmdlets work, see the Help topic for each cmdlet, and see [about_Jobs](about_Jobs.md).</span></span>

### <a name="starting-background-jobs-on-remote-computers"></a><span data-ttu-id="cc1a3-134">원격 컴퓨터에서 백그라운드 작업 시작</span><span class="sxs-lookup"><span data-stu-id="cc1a3-134">Starting background jobs on remote computers</span></span>

<span data-ttu-id="cc1a3-135">로컬 또는 원격 컴퓨터에서 백그라운드 작업을 만들고 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-135">You can create and manage background jobs on a local or remote computer.</span></span> <span data-ttu-id="cc1a3-136">백그라운드 작업을 원격으로 실행 하려면와 같은 cmdlet의 **AsJob** 매개 변수를 사용 `Invoke-Command` 하거나 cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-136">To run a background job remotely, use the **AsJob** parameter of a cmdlet such as `Invoke-Command`, or use the `Invoke-Command` cmdlet to run a `Start-Job` command remotely.</span></span> <span data-ttu-id="cc1a3-137">대화형 세션에서 백그라운드 작업을 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-137">You can also start a background job in an interactive session.</span></span>

<span data-ttu-id="cc1a3-138">원격 백그라운드 작업에 대 한 자세한 내용은 [about_Remote_Jobs](about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-138">For more information about remote background jobs, see [about_Remote_Jobs](about_Remote_Jobs.md).</span></span>

### <a name="child-jobs"></a><span data-ttu-id="cc1a3-139">자식 작업</span><span class="sxs-lookup"><span data-stu-id="cc1a3-139">Child jobs</span></span>

<span data-ttu-id="cc1a3-140">각 백그라운드 작업은 부모 작업과 하나 이상의 자식 작업으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-140">Each background job consists of a parent job and one or more child jobs.</span></span> <span data-ttu-id="cc1a3-141">`Start-Job`또는 **AsJob** 매개 변수를 사용 하 여 시작한 작업에서 `Invoke-Command` 부모 작업은 executive입니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-141">In jobs started using `Start-Job` or the **AsJob** parameter of `Invoke-Command`, the parent job is an executive.</span></span> <span data-ttu-id="cc1a3-142">명령을 실행 하거나 아무 결과도 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-142">It does not run any commands or return any results.</span></span> <span data-ttu-id="cc1a3-143">명령은 실제로 자식 작업에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-143">The commands are actually run by the child jobs.</span></span> <span data-ttu-id="cc1a3-144">다른 cmdlet을 사용 하 여 시작 하는 작업은 다르게 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-144">Jobs started using other cmdlets might work differently.</span></span>

<span data-ttu-id="cc1a3-145">자식 작업은 부모 작업 개체의 **childjobs** 속성에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-145">The child jobs are stored in the **ChildJobs** property of the parent job object.</span></span> <span data-ttu-id="cc1a3-146">**Childjobs** 속성은 하나 이상의 자식 작업 개체를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-146">The **ChildJobs** property can contain one or many child job objects.</span></span>
<span data-ttu-id="cc1a3-147">자식 작업 개체는 부모 작업과 다른 **이름** , **ID** 및 **InstanceId** 를 가지 므로 부모 및 자식 작업을 개별적으로 또는 하나의 단위로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-147">The child job objects have a **Name** , **ID** , and **InstanceId** that differ from the parent job so that you can manage the parent and child jobs individually or as a unit.</span></span>

<span data-ttu-id="cc1a3-148">작업의 부모 및 자식 작업을 가져오려면 cmdlet의 **IncludeChildJobs** 매개 변수를 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="cc1a3-148">To get the parent and child jobs of a job, use the **IncludeChildJobs** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="cc1a3-149">**IncludeChildJob** 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-149">The **IncludeChildJob** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -IncludeChildJob

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="cc1a3-150">부모 작업과 특정 **상태** 값을 가진 자식 작업만 가져오려면 Cmdlet의 **ChildJobState** 매개 변수를 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="cc1a3-150">To get the parent job and only the child jobs with a particular **State** value, use the **ChildJobState** parameter of the `Get-Job` cmdlet.</span></span> <span data-ttu-id="cc1a3-151">**ChildJobState** 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-151">The **ChildJobState** parameter was introduced in Windows PowerShell 3.0.</span></span>

```powershell
PS> Get-Job -ChildJobState Failed

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
1  Job1   RemoteJob     Failed     True          localhost   Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="cc1a3-152">모든 버전의 PowerShell에서 작업의 자식 작업을 가져오려면 부모 작업의 **childjob** 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-152">To get the child jobs of a job on all versions of PowerShell, use the **ChildJob** property of the parent job.</span></span>

```powershell
PS> (Get-Job Job1).ChildJobs

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
2  Job2                 Completed  True          Server01    Get-Process
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="cc1a3-153">`Get-Job`다음 명령에 표시 된 것 처럼 자식 작업에서 명령을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-153">You can also use a `Get-Job` command on the child job, as shown in the following command:</span></span>

```powershell
PS> Get-Job Job3

Id Name   PSJobTypeName State      HasMoreData   Location    Command
-- ----   ------------- -----      -----------   --------    -------
3  Job3                 Failed     False         localhost   Get-Process
```

<span data-ttu-id="cc1a3-154">자식 작업의 구성은 작업을 시작 하는 데 사용 하는 명령에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-154">The configuration of the child job depends on the command that you use to start the job.</span></span>

- <span data-ttu-id="cc1a3-155">를 사용 `Start-Job` 하 여 로컬 컴퓨터에서 작업을 시작 하는 경우이 작업은 executive 부모 작업과 명령을 실행 하는 자식 작업으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-155">When you use `Start-Job` to start a job on a local computer, the job consists of an executive parent job and a child job that runs the command.</span></span>

- <span data-ttu-id="cc1a3-156">의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` 하나 이상의 컴퓨터에서 작업을 시작 하는 경우이 작업은 executive 부모 작업과 각 컴퓨터에서 실행 되는 각 작업에 대 한 자식 작업으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-156">When you use the **AsJob** parameter of `Invoke-Command` to start a job on one or more computers, the job consists of an executive parent job and a child job for each job run on each computer.</span></span>

- <span data-ttu-id="cc1a3-157">`Invoke-Command`를 사용 하 여 하나 이상의 `Start-Job` 원격 컴퓨터에서 명령을 실행 하는 경우 결과는 각 원격 컴퓨터에서 실행 되는 로컬 명령과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-157">When you use `Invoke-Command` to run a `Start-Job` command on one or more remote computers, the result is the same as a local command run on each remote computer.</span></span> <span data-ttu-id="cc1a3-158">이 명령은 각 컴퓨터의 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-158">The command returns a job object for each computer.</span></span> <span data-ttu-id="cc1a3-159">작업 개체는 executive 부모 작업과 명령을 실행 하는 하나의 자식 작업으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-159">The job object consists of an executive parent job and one child job that runs the command.</span></span>

<span data-ttu-id="cc1a3-160">부모 작업은 모든 자식 작업을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-160">The parent job represents all of the child jobs.</span></span> <span data-ttu-id="cc1a3-161">부모 작업을 관리 하는 경우에도 연결 된 자식 작업을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-161">When you manage a parent job, you also manage the associated child jobs.</span></span> <span data-ttu-id="cc1a3-162">예를 들어 부모 작업을 중지 하면 모든 자식 작업이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-162">For example, if you stop a parent job, all child jobs are stopped.</span></span> <span data-ttu-id="cc1a3-163">부모 작업의 결과를 가져오는 경우 모든 자식 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-163">If you get the results of a parent job, you get the results of all child jobs.</span></span>

<span data-ttu-id="cc1a3-164">그러나 자식 작업을 개별적으로 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-164">However, you can also manage child jobs individually.</span></span> <span data-ttu-id="cc1a3-165">이는 작업의 문제를 조사 하거나의 **AsJob** 매개 변수를 사용 하 여 시작 된 여러 자식 작업 중 하나의 결과만 가져오는 경우에 가장 유용 합니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="cc1a3-165">This is most useful when you want to investigate a problem with a job or get the results of only one of a number of child jobs started using the **AsJob** parameter of `Invoke-Command`.</span></span>

<span data-ttu-id="cc1a3-166">다음 명령은의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` 로컬 컴퓨터와 두 개의 원격 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-166">The following command uses the **AsJob** parameter of `Invoke-Command` to start background jobs on the local computer and two remote computers.</span></span> <span data-ttu-id="cc1a3-167">이 명령은 작업을 `$j` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-167">The command saves the job in the `$j` variable.</span></span>

```powershell
PS> $j = Invoke-Command -ComputerName localhost, Server01, Server02 `
-Command {Get-Date} -AsJob
```

<span data-ttu-id="cc1a3-168">에서 작업의 Name 및 **childjob** 속성을 표시 하면 `$j` 명령에서 각 컴퓨터에 대해 하나씩 세 개의 자식 작업이 있는 작업 개체를 반환 하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-168">When you display the Name and **ChildJob** properties of the job in `$j`, it shows that the command returned a job object with three child jobs, one for each computer.</span></span>

```powershell
PS> $j | Format-List Name, ChildJobs

Name      : Job3
ChildJobs : {Job4, Job5, Job6}
```

<span data-ttu-id="cc1a3-169">부모 작업을 표시 하면 작업이 실패 한 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-169">When you display the parent job, it shows that the job failed.</span></span>

```powershell
PS> $j

Id Name   PSJobTypeName State      HasMoreData   Location
-- ----   ------------- -----      -----------   --------
3  Job3   RemotingJob   Failed     False         localhost,Server...
```

<span data-ttu-id="cc1a3-170">그러나 `Get-Job` 자식 작업을 가져오는 명령을 실행 하면 하나의 자식 작업만 실패 한 것으로 출력에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-170">But when you run a `Get-Job` command that gets the child jobs, the output shows that only one child job failed.</span></span>

```powershell
PS> Get-Job -IncludeChildJobs

Id  Name   PSJobTypeName State      HasMoreData   Location    Command
--  ----   ------------- -----      -----------   --------    -------
3   Job3   RemotingJob   Failed     False         localhost,Server...
4   Job4                 Completed  True          localhost   Get-Date
5   Job5                 Failed     False         Server01    Get-Date
6   Job6                 Completed  True          Server02    Get-Date
```

<span data-ttu-id="cc1a3-171">모든 자식 작업의 결과를 가져오려면 cmdlet을 사용 `Receive-Job` 하 여 부모 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-171">To get the results of all child jobs, use the `Receive-Job` cmdlet to get the results of the parent job.</span></span> <span data-ttu-id="cc1a3-172">그러나 다음 명령에 표시 된 것 처럼 특정 자식 작업의 결과를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-172">But you can also get the results of a particular child job, as shown in the following command.</span></span>

```powershell
PS> Receive-Job -Name Job6 -Keep | Format-Table ComputerName,
>> DateTime -AutoSize
ComputerName DateTime
------------ --------
Server02     Thursday, March 13, 2008 4:16:03 PM
```

<span data-ttu-id="cc1a3-173">PowerShell 백그라운드 작업의 자식 작업 기능을 사용 하면 실행 하는 작업을 보다 효과적으로 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-173">The child jobs feature of PowerShell background jobs gives you more control over the jobs that you run.</span></span>

### <a name="job-types"></a><span data-ttu-id="cc1a3-174">작업 유형</span><span class="sxs-lookup"><span data-stu-id="cc1a3-174">Job types</span></span>

<span data-ttu-id="cc1a3-175">PowerShell은 작업 마다 다른 유형의 작업을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-175">PowerShell supports different types of jobs for different tasks.</span></span> <span data-ttu-id="cc1a3-176">Windows PowerShell 3.0부터 개발자는 새 작업 유형을 PowerShell에 추가 하 고 작업 원본 어댑터를 모듈에 포함 하는 "작업 원본 어댑터"를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-176">Beginning in Windows PowerShell 3.0, developers can write "job source adapters" that add new job types to PowerShell and include the job source adapters in modules.</span></span>
<span data-ttu-id="cc1a3-177">모듈을 가져올 때 세션에서 새 작업 유형을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-177">When you import the module, you can use the new job type in your session.</span></span>

<span data-ttu-id="cc1a3-178">예를 들어 PSScheduledJob 모듈은 예약 된 작업을 추가 하 고 PSWorkflow 모듈은 워크플로 작업을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-178">For example, the PSScheduledJob module adds scheduled jobs and the PSWorkflow module adds workflow jobs.</span></span>

<span data-ttu-id="cc1a3-179">사용자 지정 작업 유형은 표준 PowerShell 백그라운드 작업과 크게 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-179">Custom jobs types might differ significantly from standard PowerShell background jobs.</span></span> <span data-ttu-id="cc1a3-180">예를 들어 예약 된 작업은 디스크에 저장 됩니다. 특정 세션에만 존재 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-180">For example, scheduled jobs are saved on disk; they do not exist only in a particular session.</span></span> <span data-ttu-id="cc1a3-181">워크플로 작업을 일시 중단 하 고 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-181">Workflow jobs can be suspended and resumed.</span></span>

<span data-ttu-id="cc1a3-182">사용자 지정 작업을 관리 하는 데 사용 하는 cmdlet은 작업 유형에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-182">The cmdlets that you use to manage custom jobs depend on the job type.</span></span> <span data-ttu-id="cc1a3-183">일부 경우에는 및와 같은 표준 작업 cmdlet을 사용 `Get-Job` `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-183">For some, you use the standard job cmdlets, such as `Get-Job` and `Start-Job`.</span></span> <span data-ttu-id="cc1a3-184">다른 작업은 특정 유형의 작업을 관리 하는 특수 한 cmdlet과 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-184">Others come with specialized cmdlets that manage only a particular type of job.</span></span> <span data-ttu-id="cc1a3-185">사용자 지정 작업 유형에 대 한 자세한 내용은 작업 유형에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-185">For detailed information about custom job types, see the help topics about the job type.</span></span>

<span data-ttu-id="cc1a3-186">작업의 작업 유형을 찾으려면 cmdlet을 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="cc1a3-186">To find the job type of a job, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="cc1a3-187">`Get-Job` 는 다른 작업 유형에 대해 서로 다른 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-187">`Get-Job` returns different job objects for different types of jobs.</span></span> <span data-ttu-id="cc1a3-188">가 반환 하는 작업 개체의 **PSJobTypeName** 속성 값은 `Get-Job` 작업 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-188">The value of the **PSJobTypeName** property of the job objects that `Get-Job` returns indicates the job type.</span></span>

<span data-ttu-id="cc1a3-189">다음 표에서는 PowerShell과 함께 제공 되는 작업 유형을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-189">The following table lists the job types that come with PowerShell.</span></span>

|    <span data-ttu-id="cc1a3-190">작업 유형</span><span class="sxs-lookup"><span data-stu-id="cc1a3-190">Job Type</span></span>    |                       <span data-ttu-id="cc1a3-191">Description</span><span class="sxs-lookup"><span data-stu-id="cc1a3-191">Description</span></span>                        |
| -------------- | -------------------------------------------------------- |
| <span data-ttu-id="cc1a3-192">BackgroundJob</span><span class="sxs-lookup"><span data-stu-id="cc1a3-192">BackgroundJob</span></span>  | <span data-ttu-id="cc1a3-193">Cmdlet을 사용 하 여 시작 되었습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="cc1a3-193">Started using the `Start-Job` cmdlet.</span></span>                    |
| <span data-ttu-id="cc1a3-194">RemoteJob</span><span class="sxs-lookup"><span data-stu-id="cc1a3-194">RemoteJob</span></span>      | <span data-ttu-id="cc1a3-195">의 **AsJob** 매개 변수를 사용 하 여 시작 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-195">Started using the **AsJob** parameter of the</span></span>             |
|                | <span data-ttu-id="cc1a3-196">`Invoke-Command` cmdlet</span><span class="sxs-lookup"><span data-stu-id="cc1a3-196">`Invoke-Command` cmdlet.</span></span>                                 |
| <span data-ttu-id="cc1a3-197">PSWorkflowJob</span><span class="sxs-lookup"><span data-stu-id="cc1a3-197">PSWorkflowJob</span></span>  | <span data-ttu-id="cc1a3-198">워크플로의 **AsJob** 매개 변수를 사용 하 여 시작 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-198">Started using the **AsJob** parameter of a workflow.</span></span>     |
| <span data-ttu-id="cc1a3-199">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="cc1a3-199">PSScheduledJob</span></span> | <span data-ttu-id="cc1a3-200">작업 트리거에서 시작한 예약 된 작업의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-200">An instance of a scheduled job started by a job trigger.</span></span> |
| <span data-ttu-id="cc1a3-201">CIMJob</span><span class="sxs-lookup"><span data-stu-id="cc1a3-201">CIMJob</span></span>         | <span data-ttu-id="cc1a3-202">에서 cmdlet의 **AsJob** 매개 변수를 사용 하기 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-202">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="cc1a3-203">CDXML 모듈.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-203">CDXML module.</span></span>                                            |
| <span data-ttu-id="cc1a3-204">WMIJob</span><span class="sxs-lookup"><span data-stu-id="cc1a3-204">WMIJob</span></span>         | <span data-ttu-id="cc1a3-205">에서 cmdlet의 **AsJob** 매개 변수를 사용 하기 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-205">Started using the **AsJob** parameter of a cmdlet from a</span></span> |
|                | <span data-ttu-id="cc1a3-206">WMI 모듈.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-206">WMI module.</span></span>                                              |
| <span data-ttu-id="cc1a3-207">PSEventJob</span><span class="sxs-lookup"><span data-stu-id="cc1a3-207">PSEventJob</span></span>     | <span data-ttu-id="cc1a3-208">를 사용 하 여 만든 `Register-ObjectEvent` 다음를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-208">Created using`Register-ObjectEvent` and specifying an</span></span>    |
|                | <span data-ttu-id="cc1a3-209">**action 매개 변수** 를 사용 하는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-209">action with the **Action** parameter.</span></span>                    |

<span data-ttu-id="cc1a3-210">참고: cmdlet을 사용 하 여 `Get-Job` 특정 유형의 작업을 가져오기 전에 작업 유형을 추가 하는 모듈을 현재 세션으로 가져왔는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-210">NOTE: Before using the `Get-Job` cmdlet to get jobs of a particular type, verify that the module that adds the job type is imported into the current session.</span></span>
<span data-ttu-id="cc1a3-211">그렇지 않으면 `Get-Job` 는 해당 형식의 작업을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-211">Otherwise, `Get-Job` does not get jobs of that type.</span></span>

## <a name="examples"></a><span data-ttu-id="cc1a3-212">예</span><span class="sxs-lookup"><span data-stu-id="cc1a3-212">Examples</span></span>

<span data-ttu-id="cc1a3-213">다음 명령은 로컬 백그라운드 작업, 원격 백그라운드 작업, 워크플로 작업 및 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-213">The following commands create a local background job, a remote background job, a workflow job, and a scheduled job.</span></span> <span data-ttu-id="cc1a3-214">그런 다음 cmdlet을 사용 하 여 `Get-Job` 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-214">Then, it uses the `Get-Job` cmdlet to get the jobs.</span></span> <span data-ttu-id="cc1a3-215">`Get-Job` 는 예약 된 작업을 가져오지 않지만 예약 된 작업의 시작 된 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-215">`Get-Job` does not get the scheduled job, but it gets any started instances of the scheduled job.</span></span>

<span data-ttu-id="cc1a3-216">로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-216">Start a background job on the local computer.</span></span>

```powershell
PS> Start-Job -Name LocalData {Get-Process}

Id Name        PSJobTypeName   State   HasMoreData   Location   Command
-- ----        -------------   -----   -----------   --------   -------
2  LocalData   BackgroundJob   Running        True   localhost  Get-Process
```

<span data-ttu-id="cc1a3-217">원격 컴퓨터에서 실행 되는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-217">Start a background job that runs on a remote computer.</span></span>

```powershell
PS> Invoke-Command -ComputerName Server01 {Get-Process} `
-AsJob -JobName RemoteData

Id  Name        PSJobTypeName  State   HasMoreData   Location   Command
--  ----        -------------  -----   -----------   --------   -------
2   RemoteData  RemoteJob      Running        True   Server01   Get-Process
```

<span data-ttu-id="cc1a3-218">예약된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="cc1a3-218">Create a scheduled job</span></span>

```powershell
PS>  Register-ScheduledJob -Name ScheduledJob -ScriptBlock `
 {Get-Process} -Trigger (New-JobTrigger -Once -At "3 PM")

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

<span data-ttu-id="cc1a3-219">워크플로를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-219">Create a workflow.</span></span>

```powershell
PS> workflow Test-Workflow {Get-Process}
```

<span data-ttu-id="cc1a3-220">워크플로를 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-220">Run the workflow as a job.</span></span>

```powershell

PS> Test-Workflow -AsJob -JobName TestWFJob

Id  Name       PSJobTypeName   State   HasMoreData   Location   Command
--  ----       -------------   -----   -----------   --------   -------
2   TestWFJob  PSWorkflowJob   NotStarted     True   localhost  Get-Process
```

<span data-ttu-id="cc1a3-221">작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-221">Get the jobs.</span></span> <span data-ttu-id="cc1a3-222">`Get-Job`이 명령은 예약 된 작업을 가져오지 않지만 시작 된 예약 된 작업의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-222">The `Get-Job` command does not get scheduled jobs, but it gets instances of the scheduled job that are started.</span></span>

```powershell
PS> Get-Job

Id  Name         PSJobTypeName  State     HasMoreData  Location  Command
--  ----         -------------  -----     -----------  --------  -------
2   LocalData    BackgroundJob  Completed True         localhost Get-Process
4   RemoteData   RemoteJob      Completed True         Server01  Get-Process
6   TestWFJob    PSWorkflowJob  Completed True         localhost WorkflowJob
8   ScheduledJob PSScheduledJob Completed True         localhost Get-Process
```

<span data-ttu-id="cc1a3-223">예약 된 작업을 가져오려면 cmdlet을 사용 `Get-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc1a3-223">To get scheduled jobs, use the `Get-ScheduledJob` cmdlet.</span></span>

```powershell
PS> Get-ScheduledJob

Id         Name            JobTriggers     Command       Enabled
--         ----            -----------     -------       -------
1          ScheduledJob    1               Get-Process   True
```

## <a name="see-also"></a><span data-ttu-id="cc1a3-224">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cc1a3-224">See also</span></span>

- [<span data-ttu-id="cc1a3-225">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="cc1a3-225">about_Jobs</span></span>](about_Jobs.md)
- [<span data-ttu-id="cc1a3-226">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="cc1a3-226">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)
- [<span data-ttu-id="cc1a3-227">about_Thread_Jobs</span><span class="sxs-lookup"><span data-stu-id="cc1a3-227">about_Thread_Jobs</span></span>](about_Thread_Jobs.md)
- [<span data-ttu-id="cc1a3-228">about_Remote</span><span class="sxs-lookup"><span data-stu-id="cc1a3-228">about_Remote</span></span>](about_Remote.md)
- [<span data-ttu-id="cc1a3-229">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="cc1a3-229">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [<span data-ttu-id="cc1a3-230">Start-Job</span><span class="sxs-lookup"><span data-stu-id="cc1a3-230">Start-Job</span></span>](xref:Microsoft.PowerShell.Core.Start-Job)
- [<span data-ttu-id="cc1a3-231">Get-Job</span><span class="sxs-lookup"><span data-stu-id="cc1a3-231">Get-Job</span></span>](xref:Microsoft.PowerShell.Core.Get-Job)
- [<span data-ttu-id="cc1a3-232">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="cc1a3-232">Wait-Job</span></span>](xref:Microsoft.PowerShell.Core.Wait-Job)
- [<span data-ttu-id="cc1a3-233">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="cc1a3-233">Stop-Job</span></span>](xref:Microsoft.PowerShell.Core.Stop-Job)
- [<span data-ttu-id="cc1a3-234">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="cc1a3-234">Remove-Job</span></span>](xref:Microsoft.PowerShell.Core.Remove-Job)
- [<span data-ttu-id="cc1a3-235">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="cc1a3-235">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
- [<span data-ttu-id="cc1a3-236">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="cc1a3-236">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [<span data-ttu-id="cc1a3-237">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="cc1a3-237">Exit-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Exit-PSSession)
