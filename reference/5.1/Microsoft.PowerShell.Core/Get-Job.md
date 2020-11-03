---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Job
ms.openlocfilehash: 0b9c76ca1e26adaa244473366c2eabdaaa28452c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212033"
---
# <span data-ttu-id="70ae9-103">Get-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-103">Get-Job</span></span>

## <span data-ttu-id="70ae9-104">개요</span><span class="sxs-lookup"><span data-stu-id="70ae9-104">SYNOPSIS</span></span>
<span data-ttu-id="70ae9-105">현재 세션에서 실행 중인 PowerShell 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-105">Gets PowerShell background jobs that are running in the current session.</span></span>

## <span data-ttu-id="70ae9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="70ae9-106">SYNTAX</span></span>

### <span data-ttu-id="70ae9-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="70ae9-107">SessionIdParameterSet (Default)</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [[-Id] <Int32[]>] [<CommonParameters>]
```

### <span data-ttu-id="70ae9-108">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="70ae9-108">CommandParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Command <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="70ae9-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="70ae9-109">InstanceIdParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="70ae9-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="70ae9-110">NameParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="70ae9-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="70ae9-111">StateParameterSet</span></span>

```
Get-Job [-IncludeChildJob] [-ChildJobState <JobState>] [-HasMoreData <Boolean>] [-Before <DateTime>]
 [-After <DateTime>] [-Newest <Int32>] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="70ae9-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="70ae9-112">FilterParameterSet</span></span>

```
Get-Job [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="70ae9-113">설명</span><span class="sxs-lookup"><span data-stu-id="70ae9-113">DESCRIPTION</span></span>

<span data-ttu-id="70ae9-114">**Get-Job** cmdlet은 현재 세션에서 시작된 백그라운드 작업을 나타내는 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-114">The **Get-Job** cmdlet gets objects that represent the background jobs that were started in the current session.</span></span>
<span data-ttu-id="70ae9-115">**작업 (job)** 을 사용 하 여 Start-Job cmdlet을 사용 하거나 Cmdlet의 *AsJob* 매개 변수를 사용 하 여 시작 된 작업을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-115">You can use **Get-Job** to get jobs that were started by using the Start-Job cmdlet, or by using the *AsJob* parameter of any cmdlet.</span></span>

<span data-ttu-id="70ae9-116">매개 변수가 없는 경우에는 **Get job** 명령이 현재 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-116">Without parameters, a **Get-Job** command gets all jobs in the current session.</span></span>
<span data-ttu-id="70ae9-117">**Get-Job** 의 매개 변수를 사용하여 특정 작업을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-117">You can use the parameters of **Get-Job** to get particular jobs.</span></span>

<span data-ttu-id="70ae9-118">**Get-Job** 에서 반환하는 작업 개체에는 작업에 대한 유용한 정보가 포함되지만 작업 결과는 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-118">The job object that **Get-Job** returns contains useful information about the job, but it does not contain the job results.</span></span>
<span data-ttu-id="70ae9-119">결과를 얻으려면 Receive-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-119">To get the results, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="70ae9-120">Windows PowerShell 백그라운드 작업은 현재 세션과 상호 작용 하지 않고 백그라운드에서 실행 되는 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-120">A Windows PowerShell background job is a command that runs in the background without interacting with the current session.</span></span>
<span data-ttu-id="70ae9-121">일반적으로 백그라운드 작업을 사용 하 여 완료 하는 데 오랜 시간이 걸리는 복잡 한 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-121">Typically, you use a background job to run a complex command that takes a long time to finish.</span></span>
<span data-ttu-id="70ae9-122">Windows PowerShell의 백그라운드 작업에 대한 자세한 내용은 about_Jobs를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-122">For more information about background jobs in Windows PowerShell, see about_Jobs.</span></span>

<span data-ttu-id="70ae9-123">Windows PowerShell 3.0부터 **Get-Job** cmdlet은 워크플로 작업 및 예약된 작업의 인스턴스와 같은 사용자 지정 작업 유형도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-123">Beginning in Windows PowerShell 3.0, the **Get-Job** cmdlet also gets custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="70ae9-124">작업의 작업 유형을 찾으려면 해당 작업의 **PSJobTypeName** 속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-124">To find the job type of a job, use the **PSJobTypeName** property of the job.</span></span>

<span data-ttu-id="70ae9-125">**작업** 자가 사용자 지정 작업 유형을 가져올 수 있도록 하려면 Import-Module cmdlet을 사용 하거나 모듈에서 cmdlet을 사용 하 여 **작업** 을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-125">To enable **Get-Job** to get a custom job type, import the module that supports the custom job type into the session before you run a **Get-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="70ae9-126">특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="70ae9-127">예제</span><span class="sxs-lookup"><span data-stu-id="70ae9-127">EXAMPLES</span></span>

### <span data-ttu-id="70ae9-128">예 1: 현재 세션에서 시작 된 모든 백그라운드 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-128">Example 1: Get all background jobs started in the current session</span></span>

```
PS C:\> Get-Job
```

<span data-ttu-id="70ae9-129">이 명령은 현재 세션에서 시작된 모든 백그라운드 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-129">This command gets all background jobs started in the current session.</span></span>
<span data-ttu-id="70ae9-130">다른 세션에서 만들어진 작업은 로컬 컴퓨터에서 실행되는 경우에도 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-130">It does not include jobs created in other sessions, even if the jobs run on the local computer.</span></span>

### <span data-ttu-id="70ae9-131">예 2: 인스턴스 ID를 사용 하 여 작업 중지</span><span class="sxs-lookup"><span data-stu-id="70ae9-131">Example 2: Stop a job by using an instance ID</span></span>

```
The first command uses the **Get-Job** cmdlet to get a job. It uses the *Name* parameter to identify the job. The command stores the job object that **Get-Job** returns in the $j variable. In this example, there is only one job with the specified name.
PS C:\> $j = Get-Job -Name Job1

The second command gets the **InstanceId** property of the object in the $j variable and stores it in the $ID variable.
PS C:\> $ID = $j.InstanceID

The third command displays the value of the $ID variable.
PS C:\> $ID

Guid
----
03c3232e-1d23-453b-a6f4-ed73c9e29d55

The fourth command uses Stop-Job cmdlet to stop the job. It uses the *InstanceId* parameter to identify the job and $ID variable to represent the instance ID of the job.
PS C:\> Stop-Job -InstanceId $ID
```

<span data-ttu-id="70ae9-132">이들 명령은 작업의 인스턴스 ID를 가져온 다음 이 ID를 사용하여 작업을 중지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-132">These commands show how to get the instance ID of a job and then use it to stop a job.</span></span>
<span data-ttu-id="70ae9-133">고유하지 않은 작업의 이름과 달리 인스턴스 ID는 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-133">Unlike the name of a job, which is not unique, the instance ID is unique.</span></span>

### <span data-ttu-id="70ae9-134">예 3: 특정 명령이 포함 된 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-134">Example 3: Get jobs that include a specific command</span></span>

```
PS C:\> Get-Job -Command "*get-process*"
```

<span data-ttu-id="70ae9-135">이 명령은 Get-Process 명령을 포함 하는 시스템의 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-135">This command gets the jobs on the system that include a Get-Process command.</span></span>
<span data-ttu-id="70ae9-136">이 명령은 *Get-Job* 의 **Command** 매개 변수를 사용하여 검색된 작업을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-136">The command uses the *Command* parameter of **Get-Job** to limit the jobs retrieved.</span></span>
<span data-ttu-id="70ae9-137">이 명령은 와일드 카드 문자 (\*)를 사용 하 여 명령 문자열의 임의 위치에 **Get Process** 명령을 포함 하는 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-137">The command uses wildcard characters (\*) to get jobs that include a **Get-Process** command anywhere in the command string.</span></span>

### <span data-ttu-id="70ae9-138">예제 4: 파이프라인을 사용 하 여 특정 명령을 포함 하는 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-138">Example 4: Get jobs that include a specific command by using the pipeline</span></span>

```
PS C:\> "*get-process*" | Get-Job
```

<span data-ttu-id="70ae9-139">이전 예제의 명령과 마찬가지로이 명령은 시스템에서 **Get Process** 명령이 포함 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-139">Like the command in the previous example, this command gets the jobs on the system that include a **Get-Process** command.</span></span>
<span data-ttu-id="70ae9-140">이 명령은 파이프라인 연산자 (|)를 사용 하 여 문자열을 따옴표 안에 있는 **가져오기 작업** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-140">The command uses a pipeline operator (|) to send a string, in quotation marks, to the **Get-Job** cmdlet.</span></span>
<span data-ttu-id="70ae9-141">이 명령은 이전 명령과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-141">It is the equivalent of the previous command.</span></span>

### <span data-ttu-id="70ae9-142">예 5: 시작 되지 않은 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-142">Example 5: Get jobs that have not been started</span></span>

```
PS C:\> Get-Job -State NotStarted
```

<span data-ttu-id="70ae9-143">이 명령은 만들어졌지만 아직 시작되지 않은 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-143">This command gets only those jobs that have been created but have not yet been started.</span></span>
<span data-ttu-id="70ae9-144">여기에는 이후에 실행되도록 예약된 작업과 아직 예약되지 않은 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-144">This includes jobs that are scheduled to run in the future and those not yet scheduled.</span></span>

### <span data-ttu-id="70ae9-145">예 6: 이름이 할당 되지 않은 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-145">Example 6: Get jobs that have not been assigned a name</span></span>

```
PS C:\> Get-Job -Name Job*
```

<span data-ttu-id="70ae9-146">이 명령은 작업으로 시작 하는 작업 이름이 있는 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-146">This command gets all jobs that have job names that begin with job.</span></span>
<span data-ttu-id="70ae9-147">작업 \<number\> 은 작업의 기본 이름 이므로이 명령은 명시적으로 할당 된 이름이 없는 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-147">Because job\<number\> is the default name for a job, this command gets all jobs that do not have an explicitly assigned name.</span></span>

### <span data-ttu-id="70ae9-148">예 7: 작업 개체를 사용 하 여 명령에서 작업 표시</span><span class="sxs-lookup"><span data-stu-id="70ae9-148">Example 7: Use a job object to represent the job in a command</span></span>

```
The first command uses the **Start-Job** cmdlet to start a background job that runs a **Get-Process** command on the local computer. The command uses the *Name* parameter of **Start-Job** to assign a friendly name to the job.
PS C:\> Start-Job -ScriptBlock {Get-Process} -Name MyJob

The second command uses Get-Job to get the job. It uses the *Name* parameter of **Get-Job** to identify the job. The command saves the resulting job object in the $j variable.
PS C:\> $j = Get-Job -Name MyJob

The third command displays the value of the job object in the $j variable. The value of the **State** property shows that the job is completed. The value of the **HasMoreData** property shows that there are results available from the job that have not yet been retrieved.
PS C:\> $j
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
6      MyJob           BackgroundJob   Completed     True            localhost            Get-Process

The fourth command uses the **Receive-Job** cmdlet to get the results of the job. It uses the job object in the $j variable to represent the job. You can also use a pipeline operator to send a job object to **Receive-Job**.
PS C:\> Receive-Job -Job $j
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    124       4    13572      12080    59            1140 audiodg
    783      16    11428      13636   100             548 CcmExec
     96       4     4252       3764    59            3856 ccmsetup
...
```

<span data-ttu-id="70ae9-149">이 예제에서는 **Get-Job** 을 사용하여 작업 개체를 가져오는 방법을 보여 준 다음 작업 개체를 사용하여 명령에 작업을 나타내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-149">This example shows how to use **Get-Job** to get a job object, and then it shows how to use the job object to represent the job in a command.</span></span>

### <span data-ttu-id="70ae9-150">예 8: 다른 방법으로 시작 된 작업을 포함 하 여 모든 작업 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-150">Example 8: Get all jobs including jobs started by a different method</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer.
PS C:\> Start-Job -ScriptBlock {Get-EventLog System}

The second command uses the *AsJob* parameter of the **Invoke-Command** cmdlet to start a job on the S1 computer. Even though the commands in the job run on the remote computer, the job object is created on the local computer, so you use local commands to manage the job.
PS C:\> Invoke-Command -ComputerName S1 -ScriptBlock {Get-EventLog System} -AsJob

The third command uses the **Invoke-Command** cmdlet to run a **Start-Job** command on the S2 computer. By using this method, the job object is created on the remote computer, so you use remote commands to manage the job.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}

The fourth command uses **Get-Job** to get the jobs stored on the local computer. The **PSJobTypeName** property of jobs, introduced in Windows PowerShell 3.0, shows that the local job started by using the **Start-Job** cmdlet is a background job and the job started in a remote session by using the **Invoke-Command** cmdlet is a remote job.
PS C:\> Get-Job
Id     Name       PSJobTypeName   State         HasMoreData     Location        Command
--     ----       -------------   -----         -----------     --------        -------
1      Job1       BackgroundJob   Running       True            localhost       Get-EventLog System
2      Job2       RemoteJob       Running       True            S1              Get-EventLog System

The fifth command uses **Invoke-Command** to run a **Get-Job** command on the S2 computer.The sample output shows the results of the Get-Job command. On the S2 computer, the job appears to be a local job. The computer name is localhost and the job type is a background job.For more information about how to run background jobs on remote computers, see about_Remote_Jobs.
PS C:\> Invoke-Command -ComputerName S2 -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Id    Name     PSJobTypeName  State      HasMoreData   Location   Command
--    ----     -------------  -----      -----------   -------    -------
4     Job4     BackgroundJob  Running    True          localhost  Get-Eventlog System
```

<span data-ttu-id="70ae9-151">이 예에서는 다른 방법을 사용 하 여 시작 된 경우에도 **작업** cmdlet이 현재 세션에서 시작 된 모든 작업을 가져올 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-151">This example demonstrates that the **Get-Job** cmdlet can get all of the jobs that were started in the current session, even if they were started by using different methods.</span></span>

### <span data-ttu-id="70ae9-152">예 9: 실패 한 작업 조사</span><span class="sxs-lookup"><span data-stu-id="70ae9-152">Example 9: Investigate a failed job</span></span>

```
The first command uses the **Start-Job** cmdlet to start a job on the local computer. The job object that **Start-Job** returns shows that the job failed. The value of the **State** property is Failed.
PS C:\> Start-Job -ScriptBlock {Get-Process}
Id     Name       PSJobTypeName   State       HasMoreData     Location             Command
--     ----       -------------   -----       -----------     --------             -------
1      Job1       BackgroundJob   Failed      False           localhost            Get-Process

The second command uses the **Get-Job** cmdlet to get the job. The command uses the dot method to get the value of the **JobStateInfo** property of the object. It uses a pipeline operator to send the object in the **JobStateInfo** property to the Format-List cmdlet, which formats all of the properties of the object (*) in a list.The result of the **Format-List** command shows that the value of the **Reason** property of the job is blank.
PS C:\> (Get-Job).JobStateInfo | Format-List -Property *
State  : Failed
Reason :

The third command investigates more. It uses a **Get-Job** command to get the job and then uses a pipeline operator to send the whole job object to the **Format-List** cmdlet, which displays all of the properties of the job in a list.The display of all properties in the job object shows that the job contains a child job named Job2.
PS C:\> Get-Job | Format-List -Property *
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

The fourth command uses **Get-Job** to get the job object that represents the Job2 child job. This is the job in which the command actually ran. It uses the dot method to get the **Reason** property of the **JobStateInfo** property.The result shows that the job failed because of an Access Denied error. In this case, the user forgot to use the Run as administrator option when starting Windows PowerShell.Because background jobs use the remoting features of Windows PowerShell, the computer must be configured for remoting to run a job, even when the job runs on the local computer.For information about requirements for remoting in Windows PowerShell, see about_Remote_Requirements. For troubleshooting tips, see about_Remote_Troubleshooting.
PS C:\> (Get-Job -Name job2).JobStateInfo.Reason
Connecting to remote server using WSManCreateShellEx api failed. The async callback gave the following error message: Access is denied.
```

<span data-ttu-id="70ae9-153">이 명령은 작업이 실패 한 이유를 조사 하기 위해 **Get 작업** 에서 반환 하는 작업 개체를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-153">This command shows how to use the job object that **Get-Job** returns to investigate why a job failed.</span></span>
<span data-ttu-id="70ae9-154">또한 각 작업의 하위 작업을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-154">It also shows how to get the child jobs of each job.</span></span>

### <span data-ttu-id="70ae9-155">예 10: 필터링 된 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-155">Example 10: Get filtered results</span></span>

```
The first command uses the **Workflow** keyword to create the WFProcess workflow.
PS C:\> Workflow WFProcess {Get-Process}

The second command uses the *AsJob* parameter of the WFProcess workflow to run the workflow as a background job. It uses the *JobName* parameter of the workflow to specify a name for the job, and the *PSPrivateMetadata* parameter of the workflow to specify a custom ID.
PS C:\> WFProcess -AsJob -JobName WFProcessJob -PSPrivateMetadata @{MyCustomId = 92107}

The third command uses the *Filter* parameter of **Get-Job** to get the job by custom ID that was specified in the *PSPrivateMetadata* parameter.
PS C:\> Get-Job -Filter @{MyCustomId = 92107}
Id     Name            State         HasMoreData     Location             Command
--     ----            -----         -----------     --------             -------
1      WFProcessJob    Completed     True            localhost            WFProcess
```

<span data-ttu-id="70ae9-156">이 예제에서는 *Filter* 매개 변수를 사용하여 워크플로 작업을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-156">This example shows how to use the *Filter* parameter to get a workflow job.</span></span>
<span data-ttu-id="70ae9-157">Windows PowerShell 3.0에서 도입된 *Filter* 매개 변수는 워크플로 작업 및 예약된 작업과 같은 사용자 지정 작업 유형에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-157">The *Filter* parameter, introduced in Windows PowerShell 3.0 is valid only on custom job types, such as workflow jobs and scheduled jobs.</span></span>

### <span data-ttu-id="70ae9-158">예 11: 자식 작업에 대 한 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="70ae9-158">Example 11: Get information about child jobs</span></span>

```
The first command gets the jobs in the current session. The output includes a background job, a remote job and several instances of a scheduled job. The remote job, Job4, appears to have failed.
PS C:\> Get-Job
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost            .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02   .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The second command uses the *IncludeChildJob* parameter of **Get-Job**. The output adds the child jobs of all jobs that have child jobs.In this case, the revised output shows that only the Job5 child job of Job4 failed.
PS C:\> Get-Job -IncludeChildJob
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

The third command uses the *ChildJobState* parameter with a value of Failed.The output includes all parent jobs and only the child jobs that failed.
PS C:\> Get-Job -Name Job4 -ChildJobState Failed
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
2      Job2            BackgroundJob   Completed     True            localhost           .\Get-Archive.ps1
4      Job4            RemoteJob       Failed        True            Server01, Server02  .\Get-Archive.ps1
5      Job5                            Failed        False           Server01            .\Get-Archive.ps1
7      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
8      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
9      UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help
10     UpdateHelpJob   PSScheduledJob  Completed     True            localhost            Update-Help

The fifth command uses the **JobStateInfo** property of jobs and its **Reason** property to discover why Job5 failed.
PS C:\> (Get-Job -Name Job5).JobStateInfo.Reason
Connecting to remote server Server01 failed with the following error message:
Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
```

<span data-ttu-id="70ae9-159">이 예제에서는 *Get-Job* cmdlet의 *IncludeChildJob* 및 **ChildJobState** 매개 변수 사용 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-159">This example shows the effect of using the *IncludeChildJob* and *ChildJobState* parameters of the **Get-Job** cmdlet.</span></span>

## <span data-ttu-id="70ae9-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="70ae9-160">PARAMETERS</span></span>

### <span data-ttu-id="70ae9-161">-이후</span><span class="sxs-lookup"><span data-stu-id="70ae9-161">-After</span></span>

<span data-ttu-id="70ae9-162">지정된 날짜 및 시간 이후에 종료되어 완료된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-162">Gets completed jobs that ended after the specified date and time.</span></span>
<span data-ttu-id="70ae9-163">Get-Date cmdlet에서 반환 된 것과 같은 **datetime** 개체 또는 **datetime** 개체 (예: 또는)로 변환할 수 있는 문자열을 입력 `Dec 1, 2012 2:00 AM` `11/06` 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-163">Enter a **DateTime** object, such as one returned by the Get-Date cmdlet or a string that can be converted to a **DateTime** object, such as `Dec 1, 2012 2:00 AM` or `11/06`.</span></span>

<span data-ttu-id="70ae9-164">이 매개 변수는 워크플로 작업 및 예약된 작업과 같이 **EndTime** 속성이 있는 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-164">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="70ae9-165">**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-165">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="70ae9-166">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-166">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="70ae9-167">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-167">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70ae9-168">-이전</span><span class="sxs-lookup"><span data-stu-id="70ae9-168">-Before</span></span>

<span data-ttu-id="70ae9-169">지정된 날짜 및 시간 이전에 종료되어 완료된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-169">Gets completed jobs that ended before the specified date and time.</span></span>
<span data-ttu-id="70ae9-170">**DateTime** 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-170">Enter a **DateTime** object.</span></span>

<span data-ttu-id="70ae9-171">이 매개 변수는 워크플로 작업 및 예약된 작업과 같이 **EndTime** 속성이 있는 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-171">This parameter works only on custom job types, such as workflow jobs and scheduled jobs, that have an **EndTime** property.</span></span>
<span data-ttu-id="70ae9-172">**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-172">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="70ae9-173">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-173">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="70ae9-174">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-174">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70ae9-175">-ChildJobState</span><span class="sxs-lookup"><span data-stu-id="70ae9-175">-ChildJobState</span></span>

<span data-ttu-id="70ae9-176">지정된 상태가 있는 자식 개체만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-176">Gets only the child jobs that have the specified state.</span></span>
<span data-ttu-id="70ae9-177">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="70ae9-178">NotStarted</span><span class="sxs-lookup"><span data-stu-id="70ae9-178">NotStarted</span></span>
- <span data-ttu-id="70ae9-179">실행 중</span><span class="sxs-lookup"><span data-stu-id="70ae9-179">Running</span></span>
- <span data-ttu-id="70ae9-180">완료됨</span><span class="sxs-lookup"><span data-stu-id="70ae9-180">Completed</span></span>
- <span data-ttu-id="70ae9-181">실패</span><span class="sxs-lookup"><span data-stu-id="70ae9-181">Failed</span></span>
- <span data-ttu-id="70ae9-182">중지됨</span><span class="sxs-lookup"><span data-stu-id="70ae9-182">Stopped</span></span>
- <span data-ttu-id="70ae9-183">차단</span><span class="sxs-lookup"><span data-stu-id="70ae9-183">Blocked</span></span>
- <span data-ttu-id="70ae9-184">일시 중단</span><span class="sxs-lookup"><span data-stu-id="70ae9-184">Suspended</span></span>
- <span data-ttu-id="70ae9-185">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="70ae9-185">Disconnected</span></span>
- <span data-ttu-id="70ae9-186">Suspending</span><span class="sxs-lookup"><span data-stu-id="70ae9-186">Suspending</span></span>
- <span data-ttu-id="70ae9-187">중지 중</span><span class="sxs-lookup"><span data-stu-id="70ae9-187">Stopping</span></span>

<span data-ttu-id="70ae9-188">기본적으로 **Get-Job** 은 자식 작업을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-188">By default, **Get-Job** does not get child jobs.</span></span>
<span data-ttu-id="70ae9-189">*IncludeChildJob* 매개 변수를 사용 하 여 모든 자식 **작업을 가져옵니다** .</span><span class="sxs-lookup"><span data-stu-id="70ae9-189">By using the *IncludeChildJob* parameter, **Get-Job** gets all child jobs.</span></span>
<span data-ttu-id="70ae9-190">*ChildJobState* 매개 변수를 사용하는 경우 *IncludeChildJob* 매개 변수는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-190">If you use the *ChildJobState* parameter, the *IncludeChildJob* parameter has no effect.</span></span>

<span data-ttu-id="70ae9-191">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-191">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70ae9-192">-Command</span><span class="sxs-lookup"><span data-stu-id="70ae9-192">-Command</span></span>

<span data-ttu-id="70ae9-193">명령 배열을 문자열로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-193">Specifies an array of commands as strings.</span></span>
<span data-ttu-id="70ae9-194">이 cmdlet은 지정 된 명령을 포함 하는 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-194">This cmdlet gets the jobs that include the specified commands.</span></span>
<span data-ttu-id="70ae9-195">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-195">The default is all jobs.</span></span>
<span data-ttu-id="70ae9-196">와일드 카드 문자를 사용 하 여 명령 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-196">You can use wildcard characters to specify a command pattern.</span></span>

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

### <span data-ttu-id="70ae9-197">-Filter</span><span class="sxs-lookup"><span data-stu-id="70ae9-197">-Filter</span></span>

<span data-ttu-id="70ae9-198">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-198">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="70ae9-199">이 cmdlet은 모든 조건을 충족 하는 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-199">This cmdlet gets jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="70ae9-200">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-200">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="70ae9-201">이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-201">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="70ae9-202">**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-202">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="70ae9-203">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-203">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="70ae9-204">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-204">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="70ae9-205">-HasMoreData</span><span class="sxs-lookup"><span data-stu-id="70ae9-205">-HasMoreData</span></span>

<span data-ttu-id="70ae9-206">이 cmdlet이 지정 된 **HasMoreData** 속성 값을 가진 작업만 가져오는 지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-206">Indicates whether this cmdlet gets only jobs that have the specified **HasMoreData** property value.</span></span>
<span data-ttu-id="70ae9-207">**HasMoreData** 속성은 모든 작업 결과가 현재 세션에서 수신되었는지를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-207">The **HasMoreData** property indicates whether all job results have been received in the current session.</span></span>
<span data-ttu-id="70ae9-208">더 많은 결과를 포함 하는 작업을 가져오려면 $True 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-208">To get jobs that have more results, specify a value of $True.</span></span>
<span data-ttu-id="70ae9-209">더 이상 결과가 없는 작업을 가져오려면 $False 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-209">To get jobs that do not have more results, specify a value of $False.</span></span>

<span data-ttu-id="70ae9-210">작업의 결과를 가져오려면 Receive-Job cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-210">To get the results of a job, use the Receive-Job cmdlet.</span></span>

<span data-ttu-id="70ae9-211">**수신 작업** cmdlet을 사용 하면 반환 된 결과를 메모리 내 세션 관련 저장소에서 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-211">When you use the **Receive-Job** cmdlet, it deletes from its in-memory, session-specific storage the results that it returned.</span></span>
<span data-ttu-id="70ae9-212">작업의 모든 결과를 현재 세션에서 반환 하는 경우 작업의 **HasMoreData** 속성 값을 $False)로 설정 하 여 현재 세션에서 작업에 대 한 결과가 더 이상 없음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-212">When it has returned all results of the job in the current session, it sets the value of the **HasMoreData** property of the job to $False) to indicate that it has no more results for the job in the current session.</span></span>
<span data-ttu-id="70ae9-213">*Receive-Job* 의 **Keep** 매개 변수를 사용하여 **Receive-Job** 에서 결과를 삭제하고 **HasMoreData** 속성의 값을 변경할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-213">Use the *Keep* parameter of **Receive-Job** to prevent **Receive-Job** from deleting results and changing the value of the **HasMoreData** property.</span></span>
<span data-ttu-id="70ae9-214">자세한 내용을 보려면 `Get-Help Receive-Job`를 입력하십시오.</span><span class="sxs-lookup"><span data-stu-id="70ae9-214">For more information, type `Get-Help Receive-Job`.</span></span>

<span data-ttu-id="70ae9-215">**HasMoreData** 속성은 현재 세션에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-215">The **HasMoreData** property is specific to the current session.</span></span>
<span data-ttu-id="70ae9-216">작업 결과를 디스크에 저장 하는 예약 된 작업 유형과 같이 사용자 지정 작업 유형에 대 한 결과가 세션 외부에 저장 된 경우 **HasMoreData** 의 값이 $False 경우에도 다른 세션에서 **Receive-job** cmdlet을 사용 하 여 작업 결과를 다시 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-216">If results for a custom job type are saved outside of the session, such as the scheduled job type, which saves job results on disk, you can use the **Receive-Job** cmdlet in a different session to get the job results again, even if the value of **HasMoreData** is $False.</span></span>
<span data-ttu-id="70ae9-217">자세한 내용은 사용자 지정 작업 유형에 대한 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-217">For more information, see the help topics for the custom job type.</span></span>

<span data-ttu-id="70ae9-218">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-218">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Boolean
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70ae9-219">-Id</span><span class="sxs-lookup"><span data-stu-id="70ae9-219">-Id</span></span>

<span data-ttu-id="70ae9-220">이 cmdlet이 가져오는 작업의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-220">Specifies an array of IDs of jobs that this cmdlet gets.</span></span>

<span data-ttu-id="70ae9-221">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-221">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="70ae9-222">인스턴스 ID 보다 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-222">It is easier to remember and to type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="70ae9-223">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-223">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="70ae9-224">작업의 ID를 찾으려면 `Get-Job` 매개 변수 없이를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-224">To find the ID of a job, type `Get-Job` without parameters.</span></span>

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

### <span data-ttu-id="70ae9-225">-IncludeChildJob</span><span class="sxs-lookup"><span data-stu-id="70ae9-225">-IncludeChildJob</span></span>

<span data-ttu-id="70ae9-226">부모 작업 외에도이 cmdlet이 자식 작업을 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-226">Indicates that this cmdlet returns child jobs, in addition to parent jobs.</span></span>

<span data-ttu-id="70ae9-227">이 매개 변수는 워크플로 작업을 조사 하는 데 특히 유용 합니다 .이 경우 실패 이유는 자식 작업의 속성에 저장 되므로 작업에서 컨테이너 부모 작업 및 작업 실패 **를 반환 합니다** .</span><span class="sxs-lookup"><span data-stu-id="70ae9-227">This parameter is especially useful for investigating workflow jobs, for which **Get-Job** returns a container parent job, and job failures, because the reason for the failure is saved in a property of the child job.</span></span>

<span data-ttu-id="70ae9-228">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70ae9-229">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="70ae9-229">-InstanceId</span></span>

<span data-ttu-id="70ae9-230">이 cmdlet이 가져오는 작업의 인스턴스 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-230">Specifies an array of instance IDs of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="70ae9-231">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-231">The default is all jobs.</span></span>

<span data-ttu-id="70ae9-232">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-232">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="70ae9-233">작업의 인스턴스 ID를 찾으려면 **Get-Job** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-233">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="70ae9-234">-Name</span><span class="sxs-lookup"><span data-stu-id="70ae9-234">-Name</span></span>

<span data-ttu-id="70ae9-235">이 cmdlet이 가져오는 작업의 인스턴스 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-235">Specifies an array of instance friendly names of jobs that this cmdlet gets.</span></span>
<span data-ttu-id="70ae9-236">작업 이름을 입력하거나 와일드카드 문자를 사용하여 작업 이름 패턴을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-236">Enter a job name, or use wildcard characters to enter a job name pattern.</span></span>
<span data-ttu-id="70ae9-237">기본적으로 **Get-Job** 은 현재 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-237">By default, **Get-Job** gets all jobs in the current session.</span></span>

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

### <span data-ttu-id="70ae9-238">-최신</span><span class="sxs-lookup"><span data-stu-id="70ae9-238">-Newest</span></span>

<span data-ttu-id="70ae9-239">가져올 작업 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-239">Specifies a number of jobs to get.</span></span>
<span data-ttu-id="70ae9-240">이 cmdlet은 가장 최근에 종료 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-240">This cmdlet gets the jobs that ended most recently.</span></span>

<span data-ttu-id="70ae9-241">*Newest* 매개 변수는 최신 작업을 종료 시간 순서대로 정렬하거나 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-241">The *Newest* parameter does not sort or return the newest jobs in end-time order.</span></span>
<span data-ttu-id="70ae9-242">출력을 정렬 하려면 Sort-Object cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-242">To sort the output, use the Sort-Object cmdlet.</span></span>

<span data-ttu-id="70ae9-243">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-243">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: SessionIdParameterSet, CommandParameterSet, InstanceIdParameterSet, NameParameterSet, StateParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70ae9-244">-상태</span><span class="sxs-lookup"><span data-stu-id="70ae9-244">-State</span></span>

<span data-ttu-id="70ae9-245">작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-245">Specifies a job state.</span></span>
<span data-ttu-id="70ae9-246">이 cmdlet은 지정 된 상태의 작업만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-246">This cmdlet gets only jobs in the specified state.</span></span>
<span data-ttu-id="70ae9-247">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-247">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="70ae9-248">NotStarted</span><span class="sxs-lookup"><span data-stu-id="70ae9-248">NotStarted</span></span>
- <span data-ttu-id="70ae9-249">실행 중</span><span class="sxs-lookup"><span data-stu-id="70ae9-249">Running</span></span>
- <span data-ttu-id="70ae9-250">완료됨</span><span class="sxs-lookup"><span data-stu-id="70ae9-250">Completed</span></span>
- <span data-ttu-id="70ae9-251">실패</span><span class="sxs-lookup"><span data-stu-id="70ae9-251">Failed</span></span>
- <span data-ttu-id="70ae9-252">중지됨</span><span class="sxs-lookup"><span data-stu-id="70ae9-252">Stopped</span></span>
- <span data-ttu-id="70ae9-253">차단</span><span class="sxs-lookup"><span data-stu-id="70ae9-253">Blocked</span></span>
- <span data-ttu-id="70ae9-254">일시 중단</span><span class="sxs-lookup"><span data-stu-id="70ae9-254">Suspended</span></span>
- <span data-ttu-id="70ae9-255">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="70ae9-255">Disconnected</span></span>
- <span data-ttu-id="70ae9-256">Suspending</span><span class="sxs-lookup"><span data-stu-id="70ae9-256">Suspending</span></span>
- <span data-ttu-id="70ae9-257">중지 중</span><span class="sxs-lookup"><span data-stu-id="70ae9-257">Stopping</span></span>

<span data-ttu-id="70ae9-258">기본적으로 **Get-Job** 은 현재 세션의 모든 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-258">By default, **Get-Job** gets all the jobs in the current session.</span></span>

<span data-ttu-id="70ae9-259">작업 상태에 대 한 자세한 내용은 MSDN library에서 [JobState 열거](https://msdn.microsoft.com/library/system.management.automation.jobstate) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-259">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="70ae9-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70ae9-260">CommonParameters</span></span>

<span data-ttu-id="70ae9-261">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="70ae9-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70ae9-262">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="70ae9-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70ae9-263">입력</span><span class="sxs-lookup"><span data-stu-id="70ae9-263">INPUTS</span></span>

### <span data-ttu-id="70ae9-264">없음</span><span class="sxs-lookup"><span data-stu-id="70ae9-264">None</span></span>

<span data-ttu-id="70ae9-265">이 cmdlet에 입력을 파이프할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-265">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="70ae9-266">출력</span><span class="sxs-lookup"><span data-stu-id="70ae9-266">OUTPUTS</span></span>

### <span data-ttu-id="70ae9-267">System.web. Remorererea 작업</span><span class="sxs-lookup"><span data-stu-id="70ae9-267">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="70ae9-268">이 cmdlet은 세션의 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-268">This cmdlet returns objects that represent the jobs in the session.</span></span>

## <span data-ttu-id="70ae9-269">참고</span><span class="sxs-lookup"><span data-stu-id="70ae9-269">NOTES</span></span>

* <span data-ttu-id="70ae9-270">작업의 **PSJobTypeName** 속성은 작업의 작업 유형을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-270">The **PSJobTypeName** property of jobs indicates the job type of the job.</span></span> <span data-ttu-id="70ae9-271">속성 값은 작업 유형 작성자에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-271">The property value is determined by the job type author.</span></span> <span data-ttu-id="70ae9-272">다음 목록에서는 일반적인 작업 유형을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-272">The following list shows common job types.</span></span>

  - <span data-ttu-id="70ae9-273">**BackgroundJob** .</span><span class="sxs-lookup"><span data-stu-id="70ae9-273">**BackgroundJob** .</span></span>
<span data-ttu-id="70ae9-274">**시작-작업** 을 사용 하 여 로컬 작업을 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-274">Local job started by using **Start-Job** .</span></span>

  - <span data-ttu-id="70ae9-275">**Remotejob** .</span><span class="sxs-lookup"><span data-stu-id="70ae9-275">**RemoteJob** .</span></span>
<span data-ttu-id="70ae9-276">Invoke-Command cmdlet의 *AsJob* 매개 변수를 사용 하 여 **PSSession** 에서 작업을 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-276">Job started in a **PSSession** by using the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>

  - <span data-ttu-id="70ae9-277">**PSWorkflowJob** .</span><span class="sxs-lookup"><span data-stu-id="70ae9-277">**PSWorkflowJob** .</span></span>
<span data-ttu-id="70ae9-278">워크플로의 *AsJob* 일반 매개 변수를 사용하여 시작된 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="70ae9-278">Job started by using the *AsJob* common parameter of workflows.</span></span>

## <span data-ttu-id="70ae9-279">관련 링크</span><span class="sxs-lookup"><span data-stu-id="70ae9-279">RELATED LINKS</span></span>

[<span data-ttu-id="70ae9-280">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="70ae9-280">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="70ae9-281">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-281">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="70ae9-282">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-282">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="70ae9-283">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-283">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="70ae9-284">Start-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-284">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="70ae9-285">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-285">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="70ae9-286">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-286">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="70ae9-287">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="70ae9-287">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="70ae9-288">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="70ae9-288">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="70ae9-289">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="70ae9-289">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="70ae9-290">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="70ae9-290">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="70ae9-291">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="70ae9-291">about_Scheduled_Jobs</span></span>](../PSScheduledJob/About/about_Scheduled_Jobs.md)
