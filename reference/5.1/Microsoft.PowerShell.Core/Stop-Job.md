---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: c581ae593e56716ba92b1be4082ddc994ec2e229
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94388487"
---
# <span data-ttu-id="6ab22-103">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-103">Stop-Job</span></span>

## <span data-ttu-id="6ab22-104">개요</span><span class="sxs-lookup"><span data-stu-id="6ab22-104">SYNOPSIS</span></span>
<span data-ttu-id="6ab22-105">PowerShell 백그라운드 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-105">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="6ab22-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6ab22-106">SYNTAX</span></span>

### <span data-ttu-id="6ab22-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="6ab22-107">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ab22-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ab22-108">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ab22-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ab22-109">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ab22-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ab22-110">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ab22-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ab22-111">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6ab22-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="6ab22-112">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6ab22-113">설명</span><span class="sxs-lookup"><span data-stu-id="6ab22-113">DESCRIPTION</span></span>

<span data-ttu-id="6ab22-114">`Stop-Job`Cmdlet은 진행 중인 PowerShell 백그라운드 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-114">The `Stop-Job` cmdlet stops PowerShell background jobs that are in progress.</span></span> <span data-ttu-id="6ab22-115">이 cmdlet을 사용 하 여 모든 작업을 중지 하거나 이름, ID, 인스턴스 ID 또는 상태를 기준으로 또는 작업 개체를에 전달 하 여 선택한 작업을 중지할 수 있습니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-115">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to `Stop-Job`.</span></span>

<span data-ttu-id="6ab22-116">Cmdlet을 사용 하 여 `Stop-Job` 시작한 것과 같은 백그라운드 작업 `Start-Job` 또는 Cmdlet의 **AsJob** 매개 변수를 사용 하 여 작업을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-116">You can use `Stop-Job` to stop background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span> <span data-ttu-id="6ab22-117">백그라운드 작업을 중지 하면 PowerShell은 해당 작업 큐에서 보류 중인 모든 작업을 완료 한 다음 작업을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-117">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span> <span data-ttu-id="6ab22-118">이 명령을 제출한 후에는 새 작업이 큐에 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-118">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="6ab22-119">이 cmdlet은 백그라운드 작업을 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-119">This cmdlet does not delete background jobs.</span></span> <span data-ttu-id="6ab22-120">작업을 삭제 하려면 cmdlet을 사용 `Remove-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-120">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="6ab22-121">Windows PowerShell 3.0부터에서는 `Stop-Job` 워크플로 작업 및 예약 된 작업 인스턴스 등의 사용자 지정 작업 유형도 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-121">Starting in Windows PowerShell 3.0, `Stop-Job` also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="6ab22-122">에서 `Stop-Job` 사용자 지정 작업 유형을 사용 하 여 작업을 중지 하려면 `Stop-Job` cmdlet을 사용 `Import-Module` 하거나 모듈에서 cmdlet을 사용 하 여 명령을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-122">To enable `Stop-Job` to stop a job with custom job type, import the module that supports the custom job type into the session before you run a `Stop-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="6ab22-123">특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab22-123">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="6ab22-124">예제</span><span class="sxs-lookup"><span data-stu-id="6ab22-124">EXAMPLES</span></span>

### <span data-ttu-id="6ab22-125">예 1: Invoke-Command을 사용 하 여 원격 컴퓨터에서 작업 중지</span><span class="sxs-lookup"><span data-stu-id="6ab22-125">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="6ab22-126">이 예에서는 cmdlet을 사용 하 여 `Stop-Job` 원격 컴퓨터에서 실행 중인 작업을 중지 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-126">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="6ab22-127">작업은 cmdlet을 사용 하 여 원격으로 명령을 실행 하 여 시작 되었으므로 `Invoke-Command` `Start-Job` 작업 개체가 원격 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-127">Because the job was started by using the `Invoke-Command` cmdlet to run a `Start-Job` command remotely, the job object is stored on the remote computer.</span></span> <span data-ttu-id="6ab22-128">`Invoke-Command`명령을 원격으로 실행 하려면 다른 명령을 사용 해야 합니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-128">You must use another `Invoke-Command` command to run a `Stop-Job` command remotely.</span></span> <span data-ttu-id="6ab22-129">원격 백그라운드 작업에 대한 자세한 내용은 about_Remote_Jobs를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab22-129">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="6ab22-130">첫 번째 명령은 Server01 컴퓨터에 PowerShell 세션 ( **PSSession** )을 만든 다음 세션 개체를 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-130">The first command creates a PowerShell session ( **PSSession** ) on the Server01 computer, and then stores the session object in the `$s` variable.</span></span> <span data-ttu-id="6ab22-131">이 명령은 도메인 관리자의 자격 증명을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-131">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="6ab22-132">두 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` `Start-Job` 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-132">The second command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the session.</span></span> <span data-ttu-id="6ab22-133">작업의 명령은 시스템 이벤트 로그에 있는 모든 이벤트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-133">The command in the job gets all of the events in the System event log.</span></span> <span data-ttu-id="6ab22-134">결과 작업 개체는 변수에 저장 됩니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-134">The resulting job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="6ab22-135">세 번째 명령은 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-135">The third command stops the job.</span></span> <span data-ttu-id="6ab22-136">Cmdlet을 사용 하 여 `Invoke-Command` `Stop-Job` Server01의 **PSSession** 에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-136">It uses the `Invoke-Command` cmdlet to run a `Stop-Job` command in the **PSSession** on Server01.</span></span> <span data-ttu-id="6ab22-137">작업 개체는 `$j` 로컬 컴퓨터의 변수인에 저장 되므로 명령에서 Using 범위 한정자를 사용 하 여을 `$j` 지역 변수로 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-137">Because the job objects are stored in `$j`, which is a variable on the local computer, the command uses the Using scope modifier to identify `$j` as a local variable.</span></span>
<span data-ttu-id="6ab22-138">Using 범위 한정자에 대 한 자세한 내용은 [about_Remote_Variables](about/about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab22-138">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="6ab22-139">명령이 완료 되 면 작업이 중지 되 고의 **PSSession** 을 `$s` 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-139">When the command finishes, the job is stopped and the **PSSession** in `$s` is available for use.</span></span>

### <span data-ttu-id="6ab22-140">예 2: 백그라운드 작업 중지</span><span class="sxs-lookup"><span data-stu-id="6ab22-140">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="6ab22-141">이 명령은 Job1 백그라운드 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-141">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="6ab22-142">예제 3: 여러 백그라운드 작업 중지</span><span class="sxs-lookup"><span data-stu-id="6ab22-142">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="6ab22-143">이 명령은 작업 3개를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-143">This command stops three jobs.</span></span>
<span data-ttu-id="6ab22-144">해당 ID로 작업을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-144">It identifies them by their IDs.</span></span>

### <span data-ttu-id="6ab22-145">예제 4: 모든 백그라운드 작업 중지</span><span class="sxs-lookup"><span data-stu-id="6ab22-145">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="6ab22-146">이 명령은 현재 세션에서 모든 백그라운드 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-146">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="6ab22-147">예 5: 차단 된 모든 백그라운드 작업 중지</span><span class="sxs-lookup"><span data-stu-id="6ab22-147">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="6ab22-148">이 명령은 차단된 모든 작업을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-148">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="6ab22-149">예 6: 인스턴스 ID를 사용 하 여 작업 중지</span><span class="sxs-lookup"><span data-stu-id="6ab22-149">Example 6: Stop a job by using an instance ID</span></span>

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

<span data-ttu-id="6ab22-150">이 명령은 해당 인스턴스 ID를 기준으로 작업을 중지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-150">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="6ab22-151">첫 번째 명령은 cmdlet을 사용 하 여 `Get-Job` 현재 세션의 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-151">The first command uses the `Get-Job` cmdlet to get the jobs in the current session.</span></span> <span data-ttu-id="6ab22-152">이 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 작업을 명령으로 보냅니다 `Format-Table` .이 명령은 각 작업의 지정 된 속성 테이블을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-152">The command uses a pipeline operator (`|`) to send the jobs to a `Format-Table` command, which displays a table of the specified properties of each job.</span></span> <span data-ttu-id="6ab22-153">테이블에는 각 작업의 인스턴스 ID가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-153">The table includes the Instance ID of each job.</span></span> <span data-ttu-id="6ab22-154">또한 계산된 속성을 사용하여 작업 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-154">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="6ab22-155">두 번째 명령은 `Stop-Job` **InstanceID** 매개 변수가 있는 명령을 사용 하 여 선택한 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-155">The second command uses a `Stop-Job` command that has the **InstanceID** parameter to stop a selected job.</span></span>

### <span data-ttu-id="6ab22-156">예 7: 원격 컴퓨터에서 작업 중지</span><span class="sxs-lookup"><span data-stu-id="6ab22-156">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="6ab22-157">이 예에서는 cmdlet을 사용 하 여 `Stop-Job` 원격 컴퓨터에서 실행 중인 작업을 중지 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-157">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="6ab22-158">Cmdlet의 **AsJob** 매개 변수를 사용 하 여 작업을 시작 했으므로 작업이 `Invoke-Command` 원격 컴퓨터에서 실행 되더라도 작업 개체는 로컬 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-158">Because the job was started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span> <span data-ttu-id="6ab22-159">따라서 로컬 명령을 사용 하 여 작업을 중지할 수 있습니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-159">Therefore, you can use a local `Stop-Job` command to stop the job.</span></span>

<span data-ttu-id="6ab22-160">첫 번째 명령은 cmdlet을 사용 하 여 `Invoke-Command` Server01 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-160">The first command uses the `Invoke-Command` cmdlet to start a background job on the Server01 computer.</span></span> <span data-ttu-id="6ab22-161">**AsJob** 매개 변수를 사용하여 원격 명령을 백그라운드 작업으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-161">The command uses the **AsJob** parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="6ab22-162">이 명령은 cmdlet이 반환 하는 것과 동일한 작업 개체인 작업 개체를 반환 `Start-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-162">This command returns a job object, which is the same job object that the `Start-Job` cmdlet returns.</span></span>
<span data-ttu-id="6ab22-163">이 명령은 작업 개체를 `$j` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-163">The command saves the job object in the `$j` variable.</span></span>

<span data-ttu-id="6ab22-164">두 번째 명령은 파이프라인 연산자를 사용 하 여 변수에서 작업을 `$j` 로 보냅니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-164">The second command uses a pipeline operator to send the job in the `$j` variable to `Stop-Job`.</span></span> <span data-ttu-id="6ab22-165">이 명령은 **PassThru** 매개 변수를 사용 하 여 `Stop-Job` 작업 개체를 반환 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-165">The command uses the **PassThru** parameter to direct `Stop-Job` to return a job object.</span></span> <span data-ttu-id="6ab22-166">작업 개체 표시는 작업 상태가 중지 됨 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-166">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="6ab22-167">원격 백그라운드 작업에 대한 자세한 내용은 about_Remote_Jobs를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab22-167">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="6ab22-168">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6ab22-168">PARAMETERS</span></span>

### <span data-ttu-id="6ab22-169">-Filter</span><span class="sxs-lookup"><span data-stu-id="6ab22-169">-Filter</span></span>

<span data-ttu-id="6ab22-170">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-170">Specifies a hash table of conditions.</span></span> <span data-ttu-id="6ab22-171">이 cmdlet은 모든 조건을 충족 하는 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-171">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="6ab22-172">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-172">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="6ab22-173">이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-173">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="6ab22-174">Cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-174">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="6ab22-175">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab22-175">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="6ab22-176">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-177">-Id</span><span class="sxs-lookup"><span data-stu-id="6ab22-177">-Id</span></span>

<span data-ttu-id="6ab22-178">이 cmdlet이 중지 하는 작업의 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-178">Specifies the IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="6ab22-179">기본값은 현재 세션의 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-179">The default is all jobs in the current session.</span></span>

<span data-ttu-id="6ab22-180">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-180">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="6ab22-181">인스턴스 ID 보다 더 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="6ab22-182">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-182">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="6ab22-183">작업 ID를 찾으려면를 입력 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-183">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6ab22-184">-InstanceId</span></span>

<span data-ttu-id="6ab22-185">이 cmdlet이 중지 하는 작업의 인스턴스 Id를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-185">Specifies the instance IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="6ab22-186">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-186">The default is all jobs.</span></span>

<span data-ttu-id="6ab22-187">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="6ab22-188">작업의 인스턴스 ID를 찾으려면를 사용 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-188">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-189">-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-189">-Job</span></span>

<span data-ttu-id="6ab22-190">이 cmdlet이 중지 하는 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-190">Specifies the jobs that this cmdlet stops.</span></span> <span data-ttu-id="6ab22-191">작업이 포함된 변수 또는 작업을 가져오는 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-191">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="6ab22-192">파이프라인 연산자를 사용 하 여 작업을 cmdlet에 제출할 수도 있습니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="6ab22-192">You can also use a pipeline operator to submit jobs to the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="6ab22-193">기본적으로는 `Stop-Job` 현재 세션에서 시작 된 모든 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-193">By default, `Stop-Job` deletes all jobs that were started in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-194">-Name</span><span class="sxs-lookup"><span data-stu-id="6ab22-194">-Name</span></span>

<span data-ttu-id="6ab22-195">이 cmdlet이 중지 하는 작업의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-195">Specifies friendly names of jobs that this cmdlet stops.</span></span> <span data-ttu-id="6ab22-196">쉼표로 구분된 목록으로 작업 이름을 입력하거나 와일드카드 문자(\*)를 사용하여 작업 이름 패턴을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-196">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span> <span data-ttu-id="6ab22-197">기본적으로는 `Stop-Job` 현재 세션에서 만든 모든 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-197">By default, `Stop-Job` stops all jobs created in the current session.</span></span>

<span data-ttu-id="6ab22-198">이름이 고유 하지 않을 수 있으므로 작업을 이름별로 중지할 때 **WhatIf** 및 **Confirm** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-198">Because the friendly name is not guaranteed to be unique, use the **WhatIf** and **Confirm** parameters when stopping jobs by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="6ab22-199">-PassThru</span><span class="sxs-lookup"><span data-stu-id="6ab22-199">-PassThru</span></span>

<span data-ttu-id="6ab22-200">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-200">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="6ab22-201">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-201">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-202">-상태</span><span class="sxs-lookup"><span data-stu-id="6ab22-202">-State</span></span>

<span data-ttu-id="6ab22-203">작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-203">Specifies a job state.</span></span> <span data-ttu-id="6ab22-204">이 cmdlet은 지정 된 상태의 작업만 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-204">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="6ab22-205">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6ab22-206">NotStarted</span><span class="sxs-lookup"><span data-stu-id="6ab22-206">NotStarted</span></span>
- <span data-ttu-id="6ab22-207">실행 중</span><span class="sxs-lookup"><span data-stu-id="6ab22-207">Running</span></span>
- <span data-ttu-id="6ab22-208">완료됨</span><span class="sxs-lookup"><span data-stu-id="6ab22-208">Completed</span></span>
- <span data-ttu-id="6ab22-209">실패</span><span class="sxs-lookup"><span data-stu-id="6ab22-209">Failed</span></span>
- <span data-ttu-id="6ab22-210">중지됨</span><span class="sxs-lookup"><span data-stu-id="6ab22-210">Stopped</span></span>
- <span data-ttu-id="6ab22-211">차단</span><span class="sxs-lookup"><span data-stu-id="6ab22-211">Blocked</span></span>
- <span data-ttu-id="6ab22-212">일시 중단</span><span class="sxs-lookup"><span data-stu-id="6ab22-212">Suspended</span></span>
- <span data-ttu-id="6ab22-213">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="6ab22-213">Disconnected</span></span>
- <span data-ttu-id="6ab22-214">Suspending</span><span class="sxs-lookup"><span data-stu-id="6ab22-214">Suspending</span></span>
- <span data-ttu-id="6ab22-215">중지 중</span><span class="sxs-lookup"><span data-stu-id="6ab22-215">Stopping</span></span>

<span data-ttu-id="6ab22-216">작업 상태에 대 한 자세한 내용은 [JobState 열거](/dotnet/api/system.management.automation.jobstate)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab22-216">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6ab22-217">-Confirm</span></span>

<span data-ttu-id="6ab22-218">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-218">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6ab22-219">-WhatIf</span></span>

<span data-ttu-id="6ab22-220">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-220">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6ab22-221">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-221">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6ab22-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6ab22-222">CommonParameters</span></span>

<span data-ttu-id="6ab22-223">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6ab22-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6ab22-224">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6ab22-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6ab22-225">입력</span><span class="sxs-lookup"><span data-stu-id="6ab22-225">INPUTS</span></span>

### <span data-ttu-id="6ab22-226">System.web. Remorererea 작업</span><span class="sxs-lookup"><span data-stu-id="6ab22-226">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="6ab22-227">작업 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-227">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="6ab22-228">출력</span><span class="sxs-lookup"><span data-stu-id="6ab22-228">OUTPUTS</span></span>

### <span data-ttu-id="6ab22-229">없음, 시스템 관리.</span><span class="sxs-lookup"><span data-stu-id="6ab22-229">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="6ab22-230">**PassThru** 매개 변수를 지정 하는 경우이 cmdlet은 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-230">This cmdlet returns a job object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="6ab22-231">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ab22-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6ab22-232">참고</span><span class="sxs-lookup"><span data-stu-id="6ab22-232">NOTES</span></span>

## <span data-ttu-id="6ab22-233">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6ab22-233">RELATED LINKS</span></span>

[<span data-ttu-id="6ab22-234">Get-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="6ab22-235">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="6ab22-235">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="6ab22-236">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-236">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="6ab22-237">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-237">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="6ab22-238">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-238">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="6ab22-239">Start-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-239">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="6ab22-240">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-240">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="6ab22-241">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="6ab22-241">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="6ab22-242">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="6ab22-242">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="6ab22-243">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="6ab22-243">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="6ab22-244">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="6ab22-244">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="6ab22-245">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="6ab22-245">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="6ab22-246">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="6ab22-246">about_Scopes</span></span>](About/about_scopes.md)
