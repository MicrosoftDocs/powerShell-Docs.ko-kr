---
ms.date: 09/13/2016
ms.topic: reference
title: 백그라운드 작업
description: 백그라운드 작업
ms.openlocfilehash: 5478789a2ee1f2eabc71a46673e3a707643cdba8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648626"
---
# <a name="background-jobs"></a><span data-ttu-id="66611-103">백그라운드 작업</span><span class="sxs-lookup"><span data-stu-id="66611-103">Background Jobs</span></span>

<span data-ttu-id="66611-104">Cmdlet은 내부적으로 또는 Windows PowerShell *백그라운드 작업* 으로 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66611-104">Cmdlets can perform their action internally or as a Windows PowerShell *background job*.</span></span> <span data-ttu-id="66611-105">Cmdlet이 백그라운드 작업으로 실행 되는 경우 cmdlet에서 사용 하는 파이프라인 스레드와는 별도의 스레드에서 비동기적으로 작업이 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66611-105">When a cmdlet runs as a background job, the work is done asynchronously in its own thread separate from the pipeline thread that the cmdlet is using.</span></span> <span data-ttu-id="66611-106">사용자 관점에서 cmdlet이 백그라운드 작업으로 실행 되는 경우 작업을 완료 하는 데 시간이 오래 걸리고 사용자가 작업을 실행 하는 동안 중단 없이 계속할 수 있는 경우에도 명령 프롬프트가 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66611-106">From the user perspective, when a cmdlet runs as a background job, the command prompt returns immediately even if the job takes an extended amount of time to complete, and the user can continue without interruption while the job runs.</span></span>

## <a name="background-jobs-child-jobs-and-the-job-repository"></a><span data-ttu-id="66611-107">백그라운드 작업, 자식 작업 및 작업 리포지토리</span><span class="sxs-lookup"><span data-stu-id="66611-107">Background Jobs, Child Jobs, and the Job Repository</span></span>

<span data-ttu-id="66611-108">백그라운드 작업을 지 원하는 cmdlet에 의해 반환 되는 작업 개체는 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-108">The job object that is returned by the cmdlets that support background jobs defines the job.</span></span> <span data-ttu-id="66611-109">[시작-작업](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet은 작업 개체를 반환 하기도 합니다. 작업 이름, 작업을 지정 하는 데 사용 되는 식별자, 상태 정보 및 자식 작업이이 정의에 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66611-109">(The [Start-Job](/powershell/module/Microsoft.PowerShell.Core/Start-Job) cmdlet also returns a job object.) The name of the job, an identifier that is used to specify the job, the state information, and the child jobs are included in this definition.</span></span> <span data-ttu-id="66611-110">작업은 작업을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66611-110">The job does not perform any of the work.</span></span> <span data-ttu-id="66611-111">자식 작업에서 실제 작업을 수행 하기 때문에 각 백그라운드 작업에는 자식 작업이 하나 이상 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66611-111">Each background job has at least one child job because the child job performs the actual work.</span></span> <span data-ttu-id="66611-112">작업을 백그라운드 작업으로 수행 하기 위해 cmdlet을 실행 하는 경우 cmdlet은 작업 및 자식 작업을 *작업 리포지토리* 라고 하는 공용 리포지토리에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-112">When you run a cmdlet so that the work is performed as a background job, the cmdlet must add the job and the child jobs to a common repository, referred to as the *job repository*.</span></span>

<span data-ttu-id="66611-113">명령줄에서 백그라운드 작업을 처리 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66611-113">For more information about how background jobs are handled at the command line, see the following:</span></span>

- [<span data-ttu-id="66611-114">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="66611-114">about_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_jobs)

- [<span data-ttu-id="66611-115">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="66611-115">about_Job_Details</span></span>](/powershell/module/microsoft.powershell.core/about/about_job_details)

- [<span data-ttu-id="66611-116">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="66611-116">about_Remote_Jobs</span></span>](/powershell/module/microsoft.powershell.core/about/about_remote_jobs)

## <a name="writing-a-cmdlet-that-runs-as-a-background-job"></a><span data-ttu-id="66611-117">백그라운드 작업으로 실행 되는 Cmdlet 작성</span><span class="sxs-lookup"><span data-stu-id="66611-117">Writing a Cmdlet That Runs as a Background Job</span></span>

<span data-ttu-id="66611-118">백그라운드 작업으로 실행할 수 있는 cmdlet을 작성 하려면 다음 작업을 완료 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-118">To write a cmdlet that can be run as a background job, you must complete the following tasks:</span></span>

- <span data-ttu-id="66611-119">`asJob`사용자가 cmdlet을 백그라운드 작업으로 실행할지 여부를 결정할 수 있도록 switch 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-119">Define an `asJob` switch parameter so that the user can decide whether to run the cmdlet as a background job.</span></span>

- <span data-ttu-id="66611-120">[System.object](/dotnet/api/System.Management.Automation.Job) 클래스에서 파생 되는 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="66611-120">Create an object that derives from the [System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) class.</span></span> <span data-ttu-id="66611-121">이 개체는 사용자 지정 작업 개체 이거나 Windows PowerShell에서 제공 하는 작업 개체 (예: [Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) 개체) 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66611-121">This object can be a custom job object or a job object provided by Windows PowerShell, such as a [System.Management.Automation.Pseventjob](/dotnet/api/System.Management.Automation.PSEventJob) object.</span></span>

- <span data-ttu-id="66611-122">레코드 처리 방법에서 `if` cmdlet을 백그라운드 작업으로 실행할지 여부를 검색 하는 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-122">In a record processing method, add an `if` statement that detects whether the cmdlet should run as a background job.</span></span>

- <span data-ttu-id="66611-123">사용자 지정 작업 개체의 경우 작업 클래스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-123">For custom job objects, implement the job class.</span></span>

- <span data-ttu-id="66611-124">Cmdlet이 백그라운드 작업으로 실행 되는지 여부에 따라 적절 한 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-124">Return the appropriate objects, depending on whether the cmdlet is run as a background job.</span></span>

<span data-ttu-id="66611-125">코드 예제는 [작업을 지 원하는 방법](./how-to-support-jobs.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66611-125">For a code example, see [How to Support Jobs](./how-to-support-jobs.md).</span></span>

## <a name="background-job-related-apis"></a><span data-ttu-id="66611-126">백그라운드 Job-Related Api</span><span class="sxs-lookup"><span data-stu-id="66611-126">Background Job-Related APIs</span></span>

<span data-ttu-id="66611-127">백그라운드 작업을 관리 하기 위해 Windows PowerShell에서 제공 하는 Api는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="66611-127">The following APIs are provided by Windows PowerShell to manage background jobs.</span></span>

<span data-ttu-id="66611-128">[System.object](/dotnet/api/System.Management.Automation.Job) 는 사용자 지정 작업 개체를 파생 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-128">[System.Management.Automation.Job](/dotnet/api/System.Management.Automation.Job) Derives custom job objects.</span></span> <span data-ttu-id="66611-129">이 클래스는 추상 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="66611-129">This is an abstract class.</span></span>

<span data-ttu-id="66611-130">[System.object 리포지토리](/dotnet/api/System.Management.Automation.JobRepository) 는 현재 활성 백그라운드 작업에 대 한 정보를 관리 하 고 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-130">[System.Management.Automation.Jobrepository](/dotnet/api/System.Management.Automation.JobRepository) Manages and provides information about the current active background jobs.</span></span>

<span data-ttu-id="66611-131">[Jobstate](/dotnet/api/System.Management.Automation.JobState) 는 백그라운드 작업의 상태를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-131">[System.Management.Automation.Jobstate](/dotnet/api/System.Management.Automation.JobState) Defines the state of the background job.</span></span> <span data-ttu-id="66611-132">상태에는 시작 됨, 실행 중, 중지 됨이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66611-132">States include Started, Running, and Stopped.</span></span>

<span data-ttu-id="66611-133">[System.object](/dotnet/api/System.Management.Automation.JobStateInfo) 는 백그라운드 작업의 상태에 대 한 정보를 제공 하 고, 마지막 상태 변경이 오류로 인해 발생 한 경우, 작업이 현재 상태로 들어간 이유를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-133">[System.Management.Automation.Jobstateinfo](/dotnet/api/System.Management.Automation.JobStateInfo) Provides information about the state of a background job and, if the last state change was caused by an error, the reason the job entered its current state.</span></span>

<span data-ttu-id="66611-134">[System.object](/dotnet/api/System.Management.Automation.JobStateEventArgs) 는 백그라운드 작업의 상태가 변경 될 때 발생 하는 이벤트에 대 한 인수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-134">[System.Management.Automation.Jobstateeventargs](/dotnet/api/System.Management.Automation.JobStateEventArgs) Provides the arguments for an event that is raised when a background job changes state.</span></span>

## <a name="windows-powershell-job-cmdlets"></a><span data-ttu-id="66611-135">Windows PowerShell 작업 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="66611-135">Windows PowerShell Job Cmdlets</span></span>

<span data-ttu-id="66611-136">다음 cmdlet은 Windows PowerShell에서 백그라운드 작업을 관리 하는 데 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66611-136">The following cmdlets are provided by Windows PowerShell to manage background jobs.</span></span>

[<span data-ttu-id="66611-137">Get-Job</span><span class="sxs-lookup"><span data-stu-id="66611-137">Get-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Get-Job)

<span data-ttu-id="66611-138">현재 세션에서 실행되는 Windows PowerShell 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="66611-138">Gets Windows PowerShell background jobs that are running in the current session.</span></span>

[<span data-ttu-id="66611-139">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="66611-139">Receive-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Receive-Job)

<span data-ttu-id="66611-140">현재 세션의 Windows PowerShell 백그라운드 작업에 대한 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="66611-140">Gets the results of the Windows PowerShell background jobs in the current session.</span></span>

[<span data-ttu-id="66611-141">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="66611-141">Remove-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Remove-Job)

<span data-ttu-id="66611-142">Windows PowerShell 백그라운드 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-142">Deletes a Windows PowerShell background job.</span></span>

[<span data-ttu-id="66611-143">Start-Job</span><span class="sxs-lookup"><span data-stu-id="66611-143">Start-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Start-Job)

<span data-ttu-id="66611-144">Windows PowerShell 백그라운드 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-144">Starts a Windows PowerShell background job.</span></span>

[<span data-ttu-id="66611-145">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="66611-145">Stop-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Stop-Job)

<span data-ttu-id="66611-146">Windows PowerShell 백그라운드 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="66611-146">Stops a Windows PowerShell background job.</span></span>

[<span data-ttu-id="66611-147">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="66611-147">Wait-Job</span></span>](/powershell/module/Microsoft.PowerShell.Core/Wait-Job)

<span data-ttu-id="66611-148">세션에서 실행 중인 Windows PowerShell 백그라운드 작업 중 하나 또는 모두가 완료될 때까지 명령 프롬프트를 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66611-148">Suppresses the command prompt until one or all of the Windows PowerShell background jobs running in the session are complete.</span></span>

## <a name="see-also"></a><span data-ttu-id="66611-149">관련 항목</span><span class="sxs-lookup"><span data-stu-id="66611-149">See Also</span></span>

[<span data-ttu-id="66611-150">Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="66611-150">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
