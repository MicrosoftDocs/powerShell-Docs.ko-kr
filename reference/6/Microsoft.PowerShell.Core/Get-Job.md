---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: d61f1efc613b7628585e5090b9fad8d90333a291
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215050"
---
# <span data-ttu-id="14bd5-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="14bd5-103">Get-Job</span></span>

## <span data-ttu-id="14bd5-104">개요</span><span class="sxs-lookup"><span data-stu-id="14bd5-104">SYNOPSIS</span></span>
<span data-ttu-id="14bd5-105">현재 세션에서 실행 중인 PowerShell 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="14bd5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="14bd5-106">SYNTAX</span></span>

### <span data-ttu-id="14bd5-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="14bd5-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="14bd5-108">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="14bd5-108">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="14bd5-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="14bd5-109">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="14bd5-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="14bd5-110">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="14bd5-111">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="14bd5-111">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="14bd5-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="14bd5-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="14bd5-113">설명</span><span class="sxs-lookup"><span data-stu-id="14bd5-113">DESCRIPTION</span></span>

<span data-ttu-id="14bd5-114">**Get-Job** cmdlet은 현재 세션에서 시작된 백그라운드 작업을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span> <span data-ttu-id="14bd5-115">**작업 (job)** 을 사용 하 여 Start-Job cmdlet을 사용 하거나 Cmdlet의 *AsJob* 매개 변수를 사용 하 여 시작 된 작업을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="14bd5-116">매개 변수가 없는 경우에는 **Get job** 명령이 현재 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="14bd5-117">**Get-Job** 의 매개 변수를 사용하여 특정 작업을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="14bd5-118">**Get-Job** 에서 반환하는 작업 개체에는 작업에 대한 유용한 정보가 포함되지만 작업 결과는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span> <span data-ttu-id="14bd5-119">결과를 얻으려면 Receive-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="14bd5-120">PowerShell 백그라운드 작업은 현재 세션과 상호 작용 하지 않고 백그라운드에서 실행 되는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-120">A PowerShell background job is a command that runs in the background without interacting with the current session.</span></span> <span data-ttu-id="14bd5-121">일반적으로 백그라운드 작업을 사용 하 여 완료 하는 데 오랜 시간이 걸리는 복잡 한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span> <span data-ttu-id="14bd5-122">PowerShell의 백그라운드 작업에 대 한 자세한 내용은 about_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-122">For more information about background jobs in PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="14bd5-123">Windows PowerShell 3.0부터 **Get-Job** cmdlet은 워크플로 작업 및 예약된 작업의 인스턴스와 같은 사용자 지정 작업 유형도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="14bd5-124">작업의 작업 유형을 찾으려면 해당 작업의 **PSJobTypeName** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="14bd5-125">**작업** 자가 사용자 지정 작업 유형을 가져올 수 있도록 하려면 Import-Module cmdlet을 사용 하거나 모듈에서 cmdlet을 사용 하 여 **작업** 을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="14bd5-126">특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="14bd5-127">예제</span><span class="sxs-lookup"><span data-stu-id="14bd5-127">EXAMPLES</span></span>

### <span data-ttu-id="14bd5-128">예 1: 현재 세션에서 시작 된 모든 백그라운드 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-128">Example 1: Get all background jobs started in the current session</span></span>

```powershell
Get-Job
```

<span data-ttu-id="14bd5-129">이 명령은 현재 세션에서 시작된 모든 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="14bd5-130">다른 세션에서 만들어진 작업은 로컬 컴퓨터에서 실행되는 경우에도 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="14bd5-131">예 2: 인스턴스 ID를 사용 하 여 작업 중지</span><span class="sxs-lookup"><span data-stu-id="14bd5-131">Example 2: Stop a job by using an instance ID</span></span>

<span data-ttu-id="14bd5-132">이들 명령은 작업의 인스턴스 ID를 가져온 다음 이 ID를 사용하여 작업을 중지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="14bd5-133">고유하지 않은 작업의 이름과 달리 인스턴스 ID는 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

```powershell
$j = Get-Job -Name Job1
$ID = $j.InstanceID
$ID
```

```Output
Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55
```

```powershell
Stop-Job -InstanceId $ID
```

<span data-ttu-id="14bd5-134">첫 번째 명령은 **Get-Job** cmdlet을 사용하여 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-134">The first command uses the **Get-Job** cmdlet to get a job.</span></span> <span data-ttu-id="14bd5-135">*Name* 매개 변수를 사용 하 여 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-135">It uses the *Name* parameter to identify the job.</span></span> <span data-ttu-id="14bd5-136">**Get-Job** 이 $j 변수에 반환하는 작업 개체를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-136">The command stores the job object that **Get-Job** returns in the $j variable.</span></span> <span data-ttu-id="14bd5-137">이 예에는 지정된 이름의 작업이 하나만 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-137">In this example, there is only one job with the specified name.</span></span>

<span data-ttu-id="14bd5-138">두 번째 명령은 $j 변수에서 개체의 **InstanceId** 속성을 가져와 $ID 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-138">The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.</span></span>

<span data-ttu-id="14bd5-139">세 번째 명령은 $ID 변수의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-139">The third command displays the value of the $ID variable.</span></span>

<span data-ttu-id="14bd5-140">네 번째 명령은 Stop-Job cmdlet을 사용 하 여 작업을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-140">The fourth command uses Stop-Job cmdlet to stop the job.</span></span> <span data-ttu-id="14bd5-141">*InstanceId* 매개 변수를 사용하여 작업과 작업의 인스턴스 ID를 나타내는 $ID 변수를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-141">It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.</span></span>

### <span data-ttu-id="14bd5-142">예 3: 특정 명령이 포함 된 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-142">Example 3: Get jobs that include a specific command</span></span>

```powershell
Get-Job -Command "*get-process*"
```

<span data-ttu-id="14bd5-143">이 명령은 Get-Process 명령을 포함 하는 시스템의 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-143">This command gets the jobs on the system that include a Get-Process command.</span></span> <span data-ttu-id="14bd5-144">이 명령은 *Get-Job* 의 **Command** 매개 변수를 사용하여 검색된 작업을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-144">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span> <span data-ttu-id="14bd5-145">이 명령은 와일드 카드 문자 (\*)를 사용 하 여 명령 문자열의 임의 위치에 **Get Process** 명령을 포함 하는 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-145">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="14bd5-146">예제 4: 파이프라인을 사용 하 여 특정 명령을 포함 하는 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-146">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```powershell
"*get-process*" | Get-Job
```

<span data-ttu-id="14bd5-147">이전 예제의 명령과 마찬가지로이 명령은 시스템에서 **Get Process** 명령이 포함 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-147">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span> <span data-ttu-id="14bd5-148">이 명령은 파이프라인 연산자 (|)를 사용 하 여 문자열을 따옴표 안에 있는 **가져오기 작업** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-148">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span> <span data-ttu-id="14bd5-149">이 명령은 이전 명령과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-149">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="14bd5-150">예 5: 시작 되지 않은 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-150">Example 5: Get jobs that have not been started</span></span>

```powershell
Get-Job -State NotStarted
```

<span data-ttu-id="14bd5-151">이 명령은 만들어졌지만 아직 시작되지 않은 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-151">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="14bd5-152">여기에는 이후에 실행되도록 예약된 작업과 아직 예약되지 않은 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-152">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="14bd5-153">예 6: 이름이 할당 되지 않은 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-153">Example 6: Get jobs that have not been assigned a name</span></span>

```powershell
Get-Job -Name Job*
```

<span data-ttu-id="14bd5-154">이 명령은 작업으로 시작 하는 작업 이름이 있는 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-154">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="14bd5-155">작업 \<number\> 은 작업의 기본 이름 이므로이 명령은 명시적으로 할당 된 이름이 없는 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-155">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="14bd5-156">예 7: 작업 개체를 사용 하 여 명령에서 작업 표시</span><span class="sxs-lookup"><span data-stu-id="14bd5-156">Example 7: Use a job object to represent the job in a command</span></span>

<span data-ttu-id="14bd5-157">이 예제에서는 **Get-Job** 을 사용하여 작업 개체를 가져오는 방법을 보여 준 다음 작업 개체를 사용하여 명령에 작업을 나타내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-157">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process} -Name MyJob
$j = Get-Job -Name MyJob
$j
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process
```

```powershell
Receive-Job -Job $j
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="14bd5-158">첫 번째 명령은 **시작-작업** cmdlet을 사용 하 여 로컬 컴퓨터에서 **Get Process** 명령을 실행 하는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-158">The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer.</span></span> <span data-ttu-id="14bd5-159">이 명령은 *Start-Job* 의 **Name** 매개 변수를 사용하여 작업에 친숙한 이름을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-159">The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.</span></span>

<span data-ttu-id="14bd5-160">두 번째 명령은 Get-Job을 사용하여 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-160">The second command uses Get-Job to get the job.</span></span> <span data-ttu-id="14bd5-161">이 명령은 *Get-Job* 의 **Name** 매개 변수를 사용하여 작업을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-161">It uses the *Name* parameter of **Get-Job** to identify the job.</span></span> <span data-ttu-id="14bd5-162">결과 작업 개체를 $j 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-162">The command saves the resulting job object in the $j variable.</span></span>

<span data-ttu-id="14bd5-163">세 번째 명령은 $j 변수에 있는 작업 개체의 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-163">The third command displays the value of the job object in the $j variable.</span></span> <span data-ttu-id="14bd5-164">**State** 속성의 값은 작업이 완료 되었음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-164">The value of the **State** property shows that the job is completed.</span></span> <span data-ttu-id="14bd5-165">**HasMoreData** 속성의 값은 아직 검색되지 않은 작업에서 사용할 수 있는 결과가 있음을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-165">The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.</span></span>

<span data-ttu-id="14bd5-166">네 번째 명령은 **수신 작업** cmdlet을 사용 하 여 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-166">The fourth command uses the **Receive-Job** cmdlet to get the results of the job.</span></span> <span data-ttu-id="14bd5-167">이 명령은 $j 변수의 작업 개체를 사용하여 작업을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-167">It uses the job object in the $j variable to represent the job.</span></span> <span data-ttu-id="14bd5-168">파이프라인 연산자를 사용 하 여 작업 개체를 **수신 작업** 에 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-168">You can also use a pipeline operator to send a job object to **Receive-Job** .</span></span>

### <span data-ttu-id="14bd5-169">예 8: 다른 방법으로 시작 된 작업을 포함 하 여 모든 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-169">Example 8: Get all jobs including jobs started by a different method</span></span>

<span data-ttu-id="14bd5-170">이 예에서는 다른 방법을 사용 하 여 시작 된 경우에도 **작업** cmdlet이 현재 세션에서 시작 된 모든 작업을 가져올 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-170">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

```powershell
Start-Job -ScriptBlock {Get-EventLog System}
Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Get-Job
```

```Output
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System
```

```powershell
Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
```

```Output
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="14bd5-171">첫 번째 명령은 **시작-작업** cmdlet을 사용 하 여 로컬 컴퓨터에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-171">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span>

<span data-ttu-id="14bd5-172">두 번째 명령은 **Invoke 명령** Cmdlet의 *AsJob* 매개 변수를 사용 하 여 S1 컴퓨터에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-172">The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer.</span></span> <span data-ttu-id="14bd5-173">작업의 명령이 원격 컴퓨터에서 실행되는 경우에도 작업 개체가 로컬 컴퓨터에 만들어지므로 로컬 명령을 사용하여 작업을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-173">Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.</span></span>

<span data-ttu-id="14bd5-174">세 번째 명령은 **Invoke-Command** cmdlet을 사용하여 S2 컴퓨터에서 **Start-Job** 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-174">The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer.</span></span> <span data-ttu-id="14bd5-175">이 방법을 사용 하 여 작업 개체가 원격 컴퓨터에 만들어지므로 원격 명령을 사용 하 여 작업을 관리 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-175">By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.</span></span>

<span data-ttu-id="14bd5-176">네 번째 명령은 **Get-Job** 을 사용하여 로컬 컴퓨터에 저장된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-176">The fourth command uses **Get-Job** to get the jobs stored on the local computer.</span></span> <span data-ttu-id="14bd5-177">Windows PowerShell 3.0에 도입 된 작업의 **PSJobTypeName** 속성은 **시작-작업** cmdlet을 사용 하 여 시작한 로컬 작업이 백그라운드 작업 이며, **호출 명령** cmdlet을 사용 하 여 원격 세션에서 시작 된 작업이 원격 작업 임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-177">The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.</span></span>

<span data-ttu-id="14bd5-178">다섯 번째 명령은 **Invoke 명령을** 사용 하 여 S2 컴퓨터에서 **작업 가져오기** 명령을 실행 합니다. 샘플 출력은 Get-Job 명령의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-178">The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command.</span></span> <span data-ttu-id="14bd5-179">S2 컴퓨터에서 작업은 로컬 작업인 것 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-179">On the S2 computer, the job appears to be a local job.</span></span> <span data-ttu-id="14bd5-180">컴퓨터 이름은 localhost이 고 작업 유형은 백그라운드 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-180">The computer name is localhost and the job type is a background job.</span></span>

<span data-ttu-id="14bd5-181">원격 컴퓨터에서 백그라운드 작업을 실행 하는 방법에 대 한 자세한 내용은 about_Remote_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-181">For more information about how to run background jobs on remote computers, see about_Remote_Jobs.</span></span>

### <span data-ttu-id="14bd5-182">예 9: 실패 한 작업 조사</span><span class="sxs-lookup"><span data-stu-id="14bd5-182">Example 9: Investigate a failed job</span></span>

```powershell
Start-Job -ScriptBlock {Get-Process}
```

```Output
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process
```

```powershell
(Get-Job).JobStateInfo | Format-List -Property *
```

```Output
State  : Failed
Reason :
```

```powershell
Get-Job | Format-List -Property *
```

```Output
HasMoreData   : False
StatusMessage :
Location      : localhost
Command       : get-process
JobStateInfo  : Failed
Finished      : System.Threading.ManualReset
EventInstanceId    : fb792295-1318-4f5d-8ac8-8a89c5261507
Id            : 1
Name          : Job1
ChildJobs     : {Job2}
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
StateChanged  :
```

```powershell
(Get-Job -Name job2).JobStateInfo.Reason
```

```Output
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.

For information about requirements for remoting in PowerShell, see about_Remote_Requirements. For
troubleshooting tips, see about_Remote_Troubleshooting.
```

<span data-ttu-id="14bd5-183">이 명령은 작업이 실패 한 이유를 조사 하기 위해 **Get 작업** 에서 반환 하는 작업 개체를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-183">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="14bd5-184">또한 각 작업의 하위 작업을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-184">It also shows how to get the child jobs of each job.</span></span>

<span data-ttu-id="14bd5-185">첫 번째 명령은 **시작-작업** cmdlet을 사용 하 여 로컬 컴퓨터에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-185">The first command uses the **Start-Job** cmdlet to start a job on the local computer.</span></span> <span data-ttu-id="14bd5-186">**Start-Job** 이 반환하는 작업 개체는 작업이 실패했음을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-186">The job object that **Start-Job** returns shows that the job failed.</span></span> <span data-ttu-id="14bd5-187">**상태** 속성의 값이 Failed입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-187">The value of the **State** property is Failed.</span></span>

<span data-ttu-id="14bd5-188">두 번째 명령은 **Get-Job** cmdlet을 사용하여 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-188">The second command uses the **Get-Job** cmdlet to get the job.</span></span> <span data-ttu-id="14bd5-189">이 명령은 점 메서드를 사용하여 개체의 **JobStateInfo** 속성 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-189">The command uses the dot method to get the value of the **JobStateInfo** property of the object.</span></span> <span data-ttu-id="14bd5-190">파이프라인 연산자를 사용 하 여 **Jobstateinfo** 속성의 개체를 Format-List cmdlet으로 보냅니다 .이 cmdlet은 목록에 있는 개체 (\*)의 모든 속성을 포맷 합니다. **서식 목록** 명령의 결과는 작업의 **Reason** 속성 값이 비어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-190">It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (\*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.</span></span>

<span data-ttu-id="14bd5-191">세 번째 명령은 자세히 조사 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-191">The third command investigates more.</span></span> <span data-ttu-id="14bd5-192">작업 **을 가져온** 다음 파이프라인 연산자를 사용 하 여 작업의 모든 속성을 목록으로 표시 하는 **Format-list** cmdlet으로 전체 작업 개체를 전송 합니다. 작업 개체의 모든 속성을 표시 하면 작업에 이름이 Job2 인 자식 작업이 포함 되어 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-192">It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.</span></span>

<span data-ttu-id="14bd5-193">네 번째 명령은 **Get-Job** 을 사용하여 Job2 자식 작업을 나타내는 작업 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-193">The fourth command uses **Get-Job** to get the job object that represents the Job2 child job.</span></span> <span data-ttu-id="14bd5-194">이 작업은 이 명령이 실제로 실행한 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-194">This is the job in which the command actually ran.</span></span> <span data-ttu-id="14bd5-195">점 메서드를 사용 하 여 **Jobstateinfo** 속성의 **Reason** 속성을 가져옵니다. 액세스 거부 오류로 인해 작업이 실패 한 것으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-195">It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error.</span></span> <span data-ttu-id="14bd5-196">이 경우 사용자는 PowerShell을 시작할 때 관리자 권한으로 실행 옵션을 사용 하지 않습니다. 백그라운드 작업은 PowerShell의 원격 기능을 사용 하므로 작업을 로컬 컴퓨터에서 실행 하는 경우에도 원격 작업을 실행 하도록 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-196">In this case, the user forgot to use the Run as administrator option when starting PowerShell.Because background jobs use the remoting features of PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.</span></span>

### <span data-ttu-id="14bd5-197">예 10: 필터링 된 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-197">Example 10: Get filtered results</span></span>

<span data-ttu-id="14bd5-198">이 예제에서는 *Filter* 매개 변수를 사용하여 워크플로 작업을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-198">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="14bd5-199">Windows PowerShell 3.0에서 도입된 *Filter* 매개 변수는 워크플로 작업 및 예약된 작업과 같은 사용자 지정 작업 유형에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-199">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

```powershell
Workflow WFProcess {Get-Process}
WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}
Get-Job -Filter @{MyCustomId = 92107}
```

```Output
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="14bd5-200">첫 번째 명령은 **workflow** 키워드를 사용 하 여 WFProcess 워크플로를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-200">The first command uses the **Workflow** keyword to create the WFProcess workflow.</span></span>

<span data-ttu-id="14bd5-201">두 번째 명령은 WFProcess 워크플로의 *AsJob* 매개 변수를 사용 하 여 워크플로를 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-201">The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job.</span></span> <span data-ttu-id="14bd5-202">이 명령은 워크플로의 *JobName* 매개 변수를 사용하여 작업의 이름을 지정하고 워크플로의 *PSPrivateMetadata* 매개 변수를 사용하여 사용자 지정 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-202">It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.</span></span>

<span data-ttu-id="14bd5-203">세 번째 명령은 *Get-Job* 의 **Filter** 매개 변수를 사용하여 *PSPrivateMetadata* 매개 변수에 지정된 사용자 지정 ID 별로 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-203">The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.</span></span>

### <span data-ttu-id="14bd5-204">예 11: 자식 작업에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="14bd5-204">Example 11: Get information about child jobs</span></span>

<span data-ttu-id="14bd5-205">이 예제에서는 *Get-Job* cmdlet의 *IncludeChildJob* 및 **ChildJobState** 매개 변수 사용 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-205">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

```powershell
Get-Job
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -IncludeChildJob
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
3      Job3                            Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
6      Job6                            Completed     True            Server02            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
Get-Job -Name Job4 -ChildJobState Failed
```

```Output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
```

```powershell
(Get-Job -Name Job5).JobStateInfo.Reason
```

```Output
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="14bd5-206">첫 번째 명령은 현재 세션에서 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-206">The first command gets the jobs in the current session.</span></span> <span data-ttu-id="14bd5-207">출력에는 백그라운드 작업, 원격 작업 및 예약된 작업의 여러 인스턴스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-207">The output includes a background job, a remote job and several instances of a scheduled job.</span></span> <span data-ttu-id="14bd5-208">원격 작업 Job4는 실패한 것처럼 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-208">The remote job, Job4, appears to have failed.</span></span>

<span data-ttu-id="14bd5-209">두 번째 명령은 *Get-Job* 의 **IncludeChildJob** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-209">The second command uses the *IncludeChildJob* parameter of **Get-Job** .</span></span> <span data-ttu-id="14bd5-210">출력은 자식 작업을 포함 하는 모든 작업의 자식 작업을 추가 합니다. 이 경우 수정 된 출력에는 Job4의 Job5 자식 작업 실패만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-210">The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.</span></span>

<span data-ttu-id="14bd5-211">세 번째 명령은 *ChildJobState* 매개 변수를 failed 값과 함께 사용 합니다. 출력에는 모든 부모 작업과 실패 한 자식 작업만 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-211">The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.</span></span>

<span data-ttu-id="14bd5-212">네 번째 명령은 작업의 **Jobstateinfo** 속성과 해당 **Reason** 속성을 사용 하 여 Job5가 실패 한 이유를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-212">The fourth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.</span></span>

## <span data-ttu-id="14bd5-213">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="14bd5-213">PARAMETERS</span></span>

### <span data-ttu-id="14bd5-214">-이후</span><span class="sxs-lookup"><span data-stu-id="14bd5-214">-After</span></span>

<span data-ttu-id="14bd5-215">지정된 날짜 및 시간 이후에 종료되어 완료된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-215">Gets completed jobs that ended after the specified date and time.</span></span> <span data-ttu-id="14bd5-216">Get-Date cmdlet에서 반환 된 것과 같은 **datetime** 개체 또는 **datetime** 개체 (예: 또는)로 변환할 수 있는 문자열을 입력 `Dec 1, 2012 2:00 AM` `11/06` 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-216">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="14bd5-217">이 매개 변수는 워크플로 작업 및 예약된 작업과 같이 **EndTime** 속성이 있는 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-217">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="14bd5-218">**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-218">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="14bd5-219">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-219">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="14bd5-220">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-221">-이전</span><span class="sxs-lookup"><span data-stu-id="14bd5-221">-Before</span></span>

<span data-ttu-id="14bd5-222">지정된 날짜 및 시간 이전에 종료되어 완료된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-222">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="14bd5-223">**DateTime** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-223">Enter a **DateTime** object.</span></span>

<span data-ttu-id="14bd5-224">이 매개 변수는 워크플로 작업 및 예약된 작업과 같이 **EndTime** 속성이 있는 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-224">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span> <span data-ttu-id="14bd5-225">**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-225">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span> <span data-ttu-id="14bd5-226">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-226">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="14bd5-227">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-227">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-228">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="14bd5-228">-ChildJobState</span></span>

<span data-ttu-id="14bd5-229">지정된 상태가 있는 자식 개체만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-229">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="14bd5-230">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="14bd5-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="14bd5-231">NotStarted</span></span>
- <span data-ttu-id="14bd5-232">실행 중</span><span class="sxs-lookup"><span data-stu-id="14bd5-232">Running</span></span>
- <span data-ttu-id="14bd5-233">완료됨</span><span class="sxs-lookup"><span data-stu-id="14bd5-233">Completed</span></span>
- <span data-ttu-id="14bd5-234">실패</span><span class="sxs-lookup"><span data-stu-id="14bd5-234">Failed</span></span>
- <span data-ttu-id="14bd5-235">중지됨</span><span class="sxs-lookup"><span data-stu-id="14bd5-235">Stopped</span></span>
- <span data-ttu-id="14bd5-236">차단</span><span class="sxs-lookup"><span data-stu-id="14bd5-236">Blocked</span></span>
- <span data-ttu-id="14bd5-237">일시 중단</span><span class="sxs-lookup"><span data-stu-id="14bd5-237">Suspended</span></span>
- <span data-ttu-id="14bd5-238">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="14bd5-238">Disconnected</span></span>
- <span data-ttu-id="14bd5-239">Suspending</span><span class="sxs-lookup"><span data-stu-id="14bd5-239">Suspending</span></span>
- <span data-ttu-id="14bd5-240">중지 중</span><span class="sxs-lookup"><span data-stu-id="14bd5-240">Stopping</span></span>

<span data-ttu-id="14bd5-241">기본적으로 **Get-Job** 은 자식 작업을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-241">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="14bd5-242">*IncludeChildJob* 매개 변수를 사용 하 여 모든 자식 **작업을 가져옵니다** .</span><span class="sxs-lookup"><span data-stu-id="14bd5-242">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="14bd5-243">*ChildJobState* 매개 변수를 사용하는 경우 *IncludeChildJob* 매개 변수는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-243">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="14bd5-244">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-244">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-245">-Command</span><span class="sxs-lookup"><span data-stu-id="14bd5-245">-Command</span></span>

<span data-ttu-id="14bd5-246">명령 배열을 문자열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-246">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="14bd5-247">이 cmdlet은 지정 된 명령을 포함 하는 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-247">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="14bd5-248">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-248">The default is all jobs.</span></span>
<span data-ttu-id="14bd5-249">와일드 카드 문자를 사용 하 여 명령 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-249">You can use wildcard characters to specify a command pattern.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="14bd5-250">-Filter</span><span class="sxs-lookup"><span data-stu-id="14bd5-250">-Filter</span></span>

<span data-ttu-id="14bd5-251">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-251">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="14bd5-252">이 cmdlet은 모든 조건을 충족 하는 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-252">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="14bd5-253">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-253">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="14bd5-254">이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-254">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="14bd5-255">**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-255">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="14bd5-256">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-256">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="14bd5-257">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-257">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="14bd5-258">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="14bd5-258">-HasMoreData</span></span>

<span data-ttu-id="14bd5-259">이 cmdlet이 지정 된 **HasMoreData** 속성 값을 가진 작업만 가져오는 지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-259">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="14bd5-260">**HasMoreData** 속성은 모든 작업 결과가 현재 세션에서 수신되었는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-260">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="14bd5-261">더 많은 결과를 포함 하는 작업을 가져오려면 $True 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-261">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="14bd5-262">더 이상 결과가 없는 작업을 가져오려면 $False 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-262">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="14bd5-263">작업의 결과를 가져오려면 Receive-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-263">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="14bd5-264">**수신 작업** cmdlet을 사용 하면 반환 된 결과를 메모리 내 세션 관련 저장소에서 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-264">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span> <span data-ttu-id="14bd5-265">작업의 모든 결과를 현재 세션에서 반환 하는 경우 작업의 **HasMoreData** 속성 값을 $False)로 설정 하 여 현재 세션에서 작업에 대 한 결과가 더 이상 없음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-265">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span> <span data-ttu-id="14bd5-266">*Receive-Job* 의 **Keep** 매개 변수를 사용하여 **Receive-Job** 에서 결과를 삭제하고 **HasMoreData** 속성의 값을 변경할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-266">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span> <span data-ttu-id="14bd5-267">자세한 내용을 보려면 `Get-Help Receive-Job`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="14bd5-267">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="14bd5-268">**HasMoreData** 속성은 현재 세션에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-268">The **HasMoreData** property is specific to the current session.</span></span> <span data-ttu-id="14bd5-269">작업 결과를 디스크에 저장 하는 예약 된 작업 유형과 같이 사용자 지정 작업 유형에 대 한 결과가 세션 외부에 저장 된 경우 **HasMoreData** 의 값이 $False 경우에도 다른 세션에서 **Receive-job** cmdlet을 사용 하 여 작업 결과를 다시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-269">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span> <span data-ttu-id="14bd5-270">자세한 내용은 사용자 지정 작업 유형에 대한 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-270">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="14bd5-271">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-272">-Id</span><span class="sxs-lookup"><span data-stu-id="14bd5-272">-Id</span></span>

<span data-ttu-id="14bd5-273">이 cmdlet이 가져오는 작업의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-273">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="14bd5-274">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-274">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="14bd5-275">인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-275">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="14bd5-276">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-276">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="14bd5-277">작업의 ID를 찾으려면 `Get-Job` 매개 변수 없이를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-277">To find the ID of a job, type `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-278">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="14bd5-278">-IncludeChildJob</span></span>

<span data-ttu-id="14bd5-279">부모 작업 외에도이 cmdlet이 자식 작업을 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-279">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="14bd5-280">이 매개 변수는 워크플로 작업을 조사 하는 데 특히 유용 합니다 .이 경우 실패 이유는 자식 작업의 속성에 저장 되므로 작업에서 컨테이너 부모 작업 및 작업 실패 **를 반환 합니다** .</span><span class="sxs-lookup"><span data-stu-id="14bd5-280">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="14bd5-281">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-281">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-282">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="14bd5-282">-InstanceId</span></span>

<span data-ttu-id="14bd5-283">이 cmdlet이 가져오는 작업의 인스턴스 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-283">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="14bd5-284">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-284">The default is all jobs.</span></span>

<span data-ttu-id="14bd5-285">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-285">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="14bd5-286">작업의 인스턴스 ID를 찾으려면 **Get-Job** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-286">To find the instance ID of a job, use **Get-Job** .</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-287">-Name</span><span class="sxs-lookup"><span data-stu-id="14bd5-287">-Name</span></span>

<span data-ttu-id="14bd5-288">이 cmdlet이 가져오는 작업의 인스턴스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-288">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="14bd5-289">작업 이름을 입력하거나 와일드카드 문자를 사용하여 작업 이름 패턴을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-289">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="14bd5-290">기본적으로 **Get-Job** 은 현재 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-290">By default, **Get-Job** gets all jobs in the current session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="14bd5-291">-최신</span><span class="sxs-lookup"><span data-stu-id="14bd5-291">-Newest</span></span>

<span data-ttu-id="14bd5-292">가져올 작업 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-292">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="14bd5-293">이 cmdlet은 가장 최근에 종료 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-293">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="14bd5-294">*Newest* 매개 변수는 최신 작업을 종료 시간 순서대로 정렬하거나 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-294">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="14bd5-295">출력을 정렬 하려면 Sort-Object cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-295">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="14bd5-296">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-296">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet, CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-297">-상태</span><span class="sxs-lookup"><span data-stu-id="14bd5-297">-State</span></span>

<span data-ttu-id="14bd5-298">작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-298">Specifies a job state.</span></span>
<span data-ttu-id="14bd5-299">이 cmdlet은 지정 된 상태의 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-299">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="14bd5-300">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-300">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="14bd5-301">NotStarted</span><span class="sxs-lookup"><span data-stu-id="14bd5-301">NotStarted</span></span>
- <span data-ttu-id="14bd5-302">실행 중</span><span class="sxs-lookup"><span data-stu-id="14bd5-302">Running</span></span>
- <span data-ttu-id="14bd5-303">완료됨</span><span class="sxs-lookup"><span data-stu-id="14bd5-303">Completed</span></span>
- <span data-ttu-id="14bd5-304">실패</span><span class="sxs-lookup"><span data-stu-id="14bd5-304">Failed</span></span>
- <span data-ttu-id="14bd5-305">중지됨</span><span class="sxs-lookup"><span data-stu-id="14bd5-305">Stopped</span></span>
- <span data-ttu-id="14bd5-306">차단</span><span class="sxs-lookup"><span data-stu-id="14bd5-306">Blocked</span></span>
- <span data-ttu-id="14bd5-307">일시 중단</span><span class="sxs-lookup"><span data-stu-id="14bd5-307">Suspended</span></span>
- <span data-ttu-id="14bd5-308">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="14bd5-308">Disconnected</span></span>
- <span data-ttu-id="14bd5-309">Suspending</span><span class="sxs-lookup"><span data-stu-id="14bd5-309">Suspending</span></span>
- <span data-ttu-id="14bd5-310">중지 중</span><span class="sxs-lookup"><span data-stu-id="14bd5-310">Stopping</span></span>

<span data-ttu-id="14bd5-311">기본적으로 **Get-Job** 은 현재 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-311">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="14bd5-312">작업 상태에 대 한 자세한 내용은 MSDN library에서 [JobState 열거](https://msdn.microsoft.com/library/system.management.automation.jobstate) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-312">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="14bd5-313">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="14bd5-313">CommonParameters</span></span>

<span data-ttu-id="14bd5-314">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="14bd5-314">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="14bd5-315">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14bd5-315">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="14bd5-316">입력</span><span class="sxs-lookup"><span data-stu-id="14bd5-316">INPUTS</span></span>

### <span data-ttu-id="14bd5-317">없음</span><span class="sxs-lookup"><span data-stu-id="14bd5-317">None</span></span>

<span data-ttu-id="14bd5-318">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-318">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="14bd5-319">출력</span><span class="sxs-lookup"><span data-stu-id="14bd5-319">OUTPUTS</span></span>

### <span data-ttu-id="14bd5-320">System.web. Remorererea 작업</span><span class="sxs-lookup"><span data-stu-id="14bd5-320">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="14bd5-321">이 cmdlet은 세션의 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-321">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="14bd5-322">참고</span><span class="sxs-lookup"><span data-stu-id="14bd5-322">NOTES</span></span>

* <span data-ttu-id="14bd5-323">작업의 **PSJobTypeName** 속성은 작업의 작업 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-323">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="14bd5-324">속성 값은 작업 유형 작성자에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-324">The property value is determined by the job type author.</span></span> <span data-ttu-id="14bd5-325">다음 목록에서는 일반적인 작업 유형을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-325">The following list shows common job types.</span></span>

  - <span data-ttu-id="14bd5-326">**BackgroundJob** .</span><span class="sxs-lookup"><span data-stu-id="14bd5-326">**BackgroundJob** .</span></span>
<span data-ttu-id="14bd5-327">**시작-작업** 을 사용 하 여 로컬 작업을 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-327">Local job started by using **Start-Job** .</span></span>

  - <span data-ttu-id="14bd5-328">**Remotejob** .</span><span class="sxs-lookup"><span data-stu-id="14bd5-328">**RemoteJob** .</span></span>
<span data-ttu-id="14bd5-329">Invoke-Command cmdlet의 *AsJob* 매개 변수를 사용 하 여 **PSSession** 에서 작업을 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="14bd5-329">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

## <span data-ttu-id="14bd5-330">관련 링크</span><span class="sxs-lookup"><span data-stu-id="14bd5-330">RELATED LINKS</span></span>

[<span data-ttu-id="14bd5-331">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="14bd5-331">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="14bd5-332">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="14bd5-332">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="14bd5-333">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="14bd5-333">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="14bd5-334">Start-Job</span><span class="sxs-lookup"><span data-stu-id="14bd5-334">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="14bd5-335">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="14bd5-335">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="14bd5-336">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="14bd5-336">Wait-Job</span></span>](Wait-Job.md)
