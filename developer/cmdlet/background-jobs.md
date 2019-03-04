---
title: 백그라운드 작업 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a0ef5ac9-8254-4832-ace8-84b356c10f08
caps.latest.revision: 13
ms.openlocfilehash: 9aff23647e55e8c9c41c54e5b62cedc15fb28a2d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857169"
---
# <a name="background-jobs"></a><span data-ttu-id="f82a5-102">백그라운드 작업</span><span class="sxs-lookup"><span data-stu-id="f82a5-102">Background Jobs</span></span>

<span data-ttu-id="f82a5-103">내부적으로 또는 Windows PowerShell Cmdlet이 해당 작업을 수행할 수 있습니다*백그라운드 작업*합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-103">Cmdlets can perform their action internally or as a Windows PowerShell*background job*.</span></span> <span data-ttu-id="f82a5-104">Cmdlet을 백그라운드 작업으로 실행 되 면 작업 cmdlet을 사용 하는 파이프라인 스레드에서 별도 자체 스레드에서 비동기적으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-104">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="f82a5-105">사용자 관점에서 cmdlet을 백그라운드 작업으로 실행 될 때 명령 프롬프트 바로 반환 작업은 완료 하는 데는 오랜된 시간 및 작업이 실행 되는 동안은 사용자가 중단 없이 계속 하는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-105">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="f82a5-106">백그라운드 작업, 자식 작업 및 작업 저장소</span><span class="sxs-lookup"><span data-stu-id="f82a5-106">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="f82a5-107">백그라운드 작업을 지 원하는 cmdlet에서 반환 되는 작업 개체는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-107">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="f82a5-108">(합니다 [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet도 작업 개체를 반환 합니다.) 작업, 작업, 상태 정보 및 자식 작업을 지정 하는 데 사용 되는 식별자의 이름은이 정의에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-108">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="f82a5-109">작업 작업은 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-109">The job does not perform any of the work.</span></span> <span data-ttu-id="f82a5-110">각 백그라운드 작업에는 하나 이상의 자식 작업이 자식 작업 실제 작업을 수행 하기 때문에</span><span class="sxs-lookup"><span data-stu-id="f82a5-110">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="f82a5-111">백그라운드 작업으로 수행 됩니다 있도록 cmdlet을 실행 하면 cmdlet을 추가 해야 작업 및 자식 작업 이라고 공용 리포지토리에 *작업 리포지토리가*합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-111">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>
<span data-ttu-id="f82a5-112">백그라운드 작업을 지 원하는 cmdlet에서 반환 되는 작업 개체는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-112">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="f82a5-113">(합니다 [Start-job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet도 작업 개체를 반환 합니다.) 작업, 작업, 상태 정보 및 자식 작업을 지정 하는 데 사용 되는 식별자의 이름은이 정의에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-113">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="f82a5-114">작업 작업은 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-114">The job does not perform any of the work.</span></span> <span data-ttu-id="f82a5-115">각 백그라운드 작업에는 하나 이상의 자식 작업이 자식 작업 실제 작업을 수행 하기 때문에</span><span class="sxs-lookup"><span data-stu-id="f82a5-115">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="f82a5-116">백그라운드 작업으로 수행 됩니다 있도록 cmdlet을 실행 하면 cmdlet을 추가 해야 작업 및 자식 작업 이라고 공용 리포지토리에 *작업 리포지토리가*합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-116">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="f82a5-117">명령줄에서 백그라운드 작업은 처리 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f82a5-117">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="f82a5-118">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f82a5-118">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="f82a5-119">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="f82a5-119">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="f82a5-120">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="f82a5-120">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="f82a5-121">백그라운드 작업으로 실행 되는 Cmdlet를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-121">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="f82a5-122">백그라운드 작업으로 실행할 수 있는 cmdlet를 작성 하려면 다음 작업을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-122">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="f82a5-123">정의 `asJob` 스위치 매개 변수를 cmdlet을 백그라운드 작업으로 실행할지 여부를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-123">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="f82a5-124">파생 되는 개체를 만들 합니다 [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-124">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="f82a5-125">이 개체는 사용자 지정 작업 개체 또는 같은 Windows PowerShell에서 제공 하는 작업 개체 수를 [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-125">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="f82a5-126">추가 레코드 처리 메서드에서 `if` cmdlet을 백그라운드 작업으로 실행할지 여부를 검색 하는 문.</span><span class="sxs-lookup"><span data-stu-id="f82a5-126">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="f82a5-127">사용자 지정 작업 개체에 대 한 작업 클래스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-127">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="f82a5-128">Cmdlet을 백그라운드 작업으로 실행 되는 여부에 따라 적절 한 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-128">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="f82a5-129">코드 예제를 참조 하세요 [지원 작업 방법](./how-to-support-jobs.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-129">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="f82a5-130">백그라운드 작업 관련 Api</span><span class="sxs-lookup"><span data-stu-id="f82a5-130">Background Job-Related APIs</span></span>

<span data-ttu-id="f82a5-131">다음 Api는 Windows PowerShell 백그라운드 작업을 관리 하 여 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-131">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="f82a5-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) 사용자 지정 작업 개체를 파생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-132">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="f82a5-133">이 클래스는 추상 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-133">This is an abstract class.</span></span>

<span data-ttu-id="f82a5-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) 관리 하 고 현재 활성 상태인 백그라운드 작업에 대 한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-134">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="f82a5-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) 백그라운드 작업의 상태를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-135">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="f82a5-136">상태 시작, 실행 및 중지를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-136">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="f82a5-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) 백그라운드 작업의 상태에 대 한 정보를 제공 하 고 마지막 상태를 변경 하는 경우 오류가 작업의 현재 상태가 된 이유를 인해 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-137">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="f82a5-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) 백그라운드 작업 상태가 변경 될 때 발생 하는 이벤트에 대 한 인수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-138">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="f82a5-139">Windows PowerShell 작업 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f82a5-139">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="f82a5-140">다음 cmdlet은 Windows PowerShell 백그라운드 작업을 관리 하 여 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-140">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="f82a5-141">Get-Job</span><span class="sxs-lookup"><span data-stu-id="f82a5-141">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="f82a5-142">현재 세션에서 실행되는 Windows PowerShell 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-142">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="f82a5-143">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="f82a5-143">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="f82a5-144">현재 세션의 Windows PowerShell 백그라운드 작업에 대한 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-144">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="f82a5-145">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="f82a5-145">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="f82a5-146">Windows PowerShell 백그라운드 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-146">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f82a5-147">Start-Job</span><span class="sxs-lookup"><span data-stu-id="f82a5-147">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="f82a5-148">Windows PowerShell 백그라운드 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-148">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f82a5-149">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f82a5-149">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="f82a5-150">Windows PowerShell 백그라운드 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-150">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="f82a5-151">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f82a5-151">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="f82a5-152">세션에서 실행 중인 Windows PowerShell 백그라운드 작업 중 하나 또는 모두가 완료될 때까지 명령 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f82a5-152">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="f82a5-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f82a5-153">See Also</span></span>

<span data-ttu-id="f82a5-154">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="f82a5-154">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
