---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 51cf0abc1a6362122f18812cd90e59a6ca7dc4ab
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93217073"
---
# <span data-ttu-id="ce0d4-103">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="ce0d4-103">Receive-Job</span></span>

## <span data-ttu-id="ce0d4-104">개요</span><span class="sxs-lookup"><span data-stu-id="ce0d4-104">SYNOPSIS</span></span>
<span data-ttu-id="ce0d4-105">현재 세션의 PowerShell 백그라운드 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-105">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="ce0d4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ce0d4-106">SYNTAX</span></span>

### <span data-ttu-id="ce0d4-107">Location (기본값)</span><span class="sxs-lookup"><span data-stu-id="ce0d4-107">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="ce0d4-108">컴퓨터 이름</span><span class="sxs-lookup"><span data-stu-id="ce0d4-108">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="ce0d4-109">세션</span><span class="sxs-lookup"><span data-stu-id="ce0d4-109">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="ce0d4-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="ce0d4-110">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="ce0d4-111">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="ce0d4-111">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="ce0d4-112">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="ce0d4-112">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="ce0d4-113">설명</span><span class="sxs-lookup"><span data-stu-id="ce0d4-113">DESCRIPTION</span></span>

<span data-ttu-id="ce0d4-114">Cmdlet은 cmdlet `Receive-Job` `Start-Job` 또는 **AsJob** 매개 변수를 사용 하 여 시작 된 것과 같은 PowerShell 백그라운드 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-114">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="ce0d4-115">모든 작업의 결과를 가져오거나, 이름, ID, 인스턴스 ID, 컴퓨터 이름, 위치 또는 세션으로 또는 작업 개체를 전송하여 작업을 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-115">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="ce0d4-116">PowerShell 백그라운드 작업을 시작 하면 작업이 시작 되지만 결과가 즉시 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-116">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="ce0d4-117">대신 이 명령은 백그라운드 작업을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-117">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="ce0d4-118">작업 개체에는 작업에 대한 유용한 정보가 포함되어 있지만 결과는 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-118">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="ce0d4-119">이 방법을 사용 하면 작업이 실행 되는 동안 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-119">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="ce0d4-120">PowerShell의 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](./About/about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-120">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="ce0d4-121">`Receive-Job`Cmdlet은 명령이 전송 된 시간에 의해 생성 된 결과를 가져옵니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="ce0d4-121">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="ce0d4-122">결과가 아직 완료 되지 않았으면 추가 `Receive-Job` 명령을 실행 하 여 나머지 결과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-122">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="ce0d4-123">기본적으로 작업 결과는 해당 결과를 받을 때 시스템에서 삭제되지만 **Keep** 매개 변수를 사용하여 결과를 다시 받을 수 있도록 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-123">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="ce0d4-124">작업 결과를 삭제 하려면 `Receive-Job` **Keep** 매개 변수 없이 명령을 다시 실행 하거나, 세션을 닫거나, cmdlet을 사용 `Remove-Job` 하 여 세션에서 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-124">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="ce0d4-125">Windows PowerShell 3.0부터는 `Receive-Job` 워크플로 작업 및 예약 된 작업 인스턴스와 같은 사용자 지정 작업 유형의 결과도 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-125">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="ce0d4-126">에서 `Receive-Job` 결과를 사용자 지정 작업 형식으로 가져오도록 하려면 `Receive-Job` cmdlet을 사용 `Import-Module` 하거나 모듈에서 cmdlet을 사용 하 여 명령을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-126">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="ce0d4-127">특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-127">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="ce0d4-128">예제</span><span class="sxs-lookup"><span data-stu-id="ce0d4-128">EXAMPLES</span></span>

### <span data-ttu-id="ce0d4-129">예 1: 특정 작업에 대 한 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="ce0d4-129">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="ce0d4-130">이러한 명령은의 **job** 매개 변수를 사용 `Receive-Job` 하 여 특정 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-130">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="ce0d4-131">첫 번째 명령은를 사용 하 여 작업을 시작 `Start-Job` 하 고 해당 개체를 변수에 저장 합니다 `$job` .</span><span class="sxs-lookup"><span data-stu-id="ce0d4-131">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="ce0d4-132">두 번째 명령은 cmdlet을 사용 하 여 `Receive-Job` 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-132">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="ce0d4-133">**Job** 매개 변수를 사용하여 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-133">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="ce0d4-134">예제 2: Keep 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="ce0d4-134">Example 2: Use the Keep parameter</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="ce0d4-135">이 예에서는 작업을 변수에 저장 `$job` 하 고 작업을 cmdlet으로 파이프 `Receive-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-135">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="ce0d4-136">`-Keep`매개 변수를 사용 하 여 첫 번째 뷰 후 집계 된 모든 스트림 데이터를 다시 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-136">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="ce0d4-137">예제 3: 여러 백그라운드 작업의 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="ce0d4-137">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="ce0d4-138">의 **AsJob** 매개 변수를 사용 하 여 작업을 시작 하는 경우 작업이 `Invoke-Command` 원격 컴퓨터에서 실행 되더라도 작업 개체는 로컬 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-138">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="ce0d4-139">따라서 로컬 명령을 사용하여 작업을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-139">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="ce0d4-140">또한 **AsJob** 을 사용 하는 경우 PowerShell은 시작 된 각 작업에 대 한 자식 작업을 포함 하는 하나의 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-140">Also, when you use **AsJob** , PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="ce0d4-141">여기서는 작업 개체에 각 원격 컴퓨터의 작업마다 하나씩 세 개의 자식 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-141">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### <span data-ttu-id="ce0d4-142">예제 4: 여러 원격 컴퓨터에서 백그라운드 작업의 결과 가져오기</span><span class="sxs-lookup"><span data-stu-id="ce0d4-142">Example 4: Get results of background jobs on multiple remote computers</span></span>

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

<span data-ttu-id="ce0d4-143">이 예제에서는 세 개의 원격 컴퓨터에서 실행되는 백그라운드 작업의 결과를 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-143">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="ce0d4-144">이전 예제와 달리를 사용 하 여 명령을 실행 하는 것은 `Invoke-Command` `Start-Job` 실제로 세 컴퓨터 각각에 대해 3 개의 독립적인 작업을 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-144">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="ce0d4-145">따라서 이 명령은 세 컴퓨터에서 로컬로 실행된 세 작업을 나타내는 세 작업 개체를 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-145">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="ce0d4-146">마지막 명령에서 `$j` 는 지역 변수 이기 때문에 스크립트 블록은 **Using** 범위 한정자를 사용 하 여 변수를 식별 `$j` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-146">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="ce0d4-147">**Using** 범위 한정자에 대 한 자세한 내용은 [about_Remote_Variables](./About/about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="ce0d4-148">예 5: 자식 작업 액세스</span><span class="sxs-lookup"><span data-stu-id="ce0d4-148">Example 5: Access child jobs</span></span>

<span data-ttu-id="ce0d4-149">`-Keep`매개 변수는 작업을 다시 볼 수 있도록 집계 된 스트림의 상태를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-149">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="ce0d4-150">이 매개 변수를 사용 하지 않으면 집계 된 모든 스트림 데이터가 작업이 수신 될 때 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-150">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="ce0d4-151">자세한 내용은 [about_Job_Details](About/about_Job_Details.md#child-jobs) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-151">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="ce0d4-152">집계 스트림은 모든 자식 작업의 스트림을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-152">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="ce0d4-153">작업 개체 및 자식 작업 개체를 통해 데이터의 개별 스트림에 계속 도달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-153">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="ce0d4-154">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="ce0d4-154">PARAMETERS</span></span>

### <span data-ttu-id="ce0d4-155">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="ce0d4-155">-AutoRemoveJob</span></span>

<span data-ttu-id="ce0d4-156">이 cmdlet이 작업 결과를 반환한 후 작업을 삭제 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-156">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="ce0d4-157">작업에 더 많은 결과가 포함 된 경우에도 작업이 삭제 되지만 `Receive-Job` 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-157">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="ce0d4-158">이 매개 변수는 사용자 지정 작업 유형에서만 사용할 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="ce0d4-158">This parameter works only on custom job types.</span></span>
<span data-ttu-id="ce0d4-159">작업을 저장하는 작업 유형 또는 세션에서 벗어난 유형의 인스턴스(예: 예약된 작업의 인스턴스)용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-159">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="ce0d4-160">이 매개 변수는 **Wait** 매개 변수 없이 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-160">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="ce0d4-161">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-161">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ce0d4-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="ce0d4-162">-ComputerName</span></span>

<span data-ttu-id="ce0d4-163">컴퓨터 이름 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-163">Specifies an array of names of computers.</span></span>

<span data-ttu-id="ce0d4-164">이 매개 변수는 로컬 컴퓨터에 저장된 작업 결과 중에서 선택하며,</span><span class="sxs-lookup"><span data-stu-id="ce0d4-164">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="ce0d4-165">원격 컴퓨터에서 실행 되는 작업에 대 한 데이터는 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-165">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="ce0d4-166">원격 컴퓨터에 저장 된 작업 결과를 가져오려면 cmdlet을 사용 하 여 원격 `Invoke-Command` `Receive-Job` 으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-166">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ce0d4-167">-Force</span><span class="sxs-lookup"><span data-stu-id="ce0d4-167">-Force</span></span>

<span data-ttu-id="ce0d4-168">작업이 **일시 중단** 되거나 **연결** 되지 않은 상태에 있는 경우이 cmdlet이 계속 대기 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-168">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="ce0d4-169">기본적으로의 **wait** 매개 변수는 `Receive-Job` 작업이 다음 상태 중 하나일 때을 반환 하거나 대기를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-169">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="ce0d4-170">Completed</span><span class="sxs-lookup"><span data-stu-id="ce0d4-170">Completed</span></span>
- <span data-ttu-id="ce0d4-171">실패</span><span class="sxs-lookup"><span data-stu-id="ce0d4-171">Failed</span></span>
- <span data-ttu-id="ce0d4-172">중지됨</span><span class="sxs-lookup"><span data-stu-id="ce0d4-172">Stopped</span></span>
- <span data-ttu-id="ce0d4-173">일시 중단</span><span class="sxs-lookup"><span data-stu-id="ce0d4-173">Suspended</span></span>
- <span data-ttu-id="ce0d4-174">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="ce0d4-174">Disconnected.</span></span>

<span data-ttu-id="ce0d4-175">**Force** 매개 변수는 명령에 **Wait** 변수가 사용된 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-175">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="ce0d4-176">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ce0d4-177">-Id</span><span class="sxs-lookup"><span data-stu-id="ce0d4-177">-Id</span></span>

<span data-ttu-id="ce0d4-178">ID 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-178">Specifies an array of IDs.</span></span>
<span data-ttu-id="ce0d4-179">이 cmdlet은 지정 된 Id의 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-179">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="ce0d4-180">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-180">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="ce0d4-181">인스턴스 ID 보다 더 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="ce0d4-182">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-182">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="ce0d4-183">작업 ID를 찾으려면를 사용 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-183">To find the ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce0d4-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="ce0d4-184">-InstanceId</span></span>

<span data-ttu-id="ce0d4-185">인스턴스 Id의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-185">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="ce0d4-186">이 cmdlet은 지정한 인스턴스 Id를 가진 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-186">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="ce0d4-187">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="ce0d4-188">작업의 인스턴스 ID를 확인 하려면 cmdlet을 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="ce0d4-188">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce0d4-189">-Job</span><span class="sxs-lookup"><span data-stu-id="ce0d4-189">-Job</span></span>

<span data-ttu-id="ce0d4-190">결과를 검색할 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-190">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="ce0d4-191">작업이 포함된 변수나 작업을 가져오는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-191">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="ce0d4-192">작업 개체를로 파이프 할 수도 있습니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="ce0d4-192">You can also pipe a job object to `Receive-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ce0d4-193">-유지</span><span class="sxs-lookup"><span data-stu-id="ce0d4-193">-Keep</span></span>

<span data-ttu-id="ce0d4-194">이 cmdlet을 받은 후에도이 cmdlet이 집계 된 스트림 데이터를 시스템에 저장 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-194">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="ce0d4-195">기본적으로 집계 된 스트림 데이터는로 본 후에 지워집니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="ce0d4-195">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="ce0d4-196">세션을 닫거나 cmdlet을 사용 하 여 작업을 제거 하면 `Remove-Job` 집계 된 스트림 데이터도 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-196">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

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

### <span data-ttu-id="ce0d4-197">-Location</span><span class="sxs-lookup"><span data-stu-id="ce0d4-197">-Location</span></span>

<span data-ttu-id="ce0d4-198">위치 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-198">Specifies an array of locations.</span></span>
<span data-ttu-id="ce0d4-199">이 cmdlet은 지정 된 위치에 있는 작업의 결과만 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-199">This cmdlet gets only the results of jobs in the specified locations.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce0d4-200">-Name</span><span class="sxs-lookup"><span data-stu-id="ce0d4-200">-Name</span></span>

<span data-ttu-id="ce0d4-201">이름 배열을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-201">Specifies an array of friendly names.</span></span>
<span data-ttu-id="ce0d4-202">이 cmdlet은 지정 된 이름의 작업 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-202">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="ce0d4-203">와일드카드 문자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-203">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="ce0d4-204">-NoRecurse</span><span class="sxs-lookup"><span data-stu-id="ce0d4-204">-NoRecurse</span></span>

<span data-ttu-id="ce0d4-205">이 cmdlet이 지정 된 작업 에서만 결과를 가져오는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-205">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="ce0d4-206">기본적으로는 `Receive-Job` 지정 된 작업의 모든 자식 작업에 대 한 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-206">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

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

### <span data-ttu-id="ce0d4-207">-Session</span><span class="sxs-lookup"><span data-stu-id="ce0d4-207">-Session</span></span>

<span data-ttu-id="ce0d4-208">세션의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-208">Specifies an array of sessions.</span></span>
<span data-ttu-id="ce0d4-209">이 cmdlet은 지정 된 PowerShell 세션 ( **PSSession** )에서 실행 된 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-209">This cmdlet gets the results of jobs that were run in the specified PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="ce0d4-210">**Pssession** 이 포함 된 변수를 입력 하거나 **pssession** 을 가져오는 명령 (예: 명령)을 입력 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="ce0d4-210">Enter a variable that contains the **PSSession** or a command that gets the **PSSession** , such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ce0d4-211">-Wait</span><span class="sxs-lookup"><span data-stu-id="ce0d4-211">-Wait</span></span>

<span data-ttu-id="ce0d4-212">모든 작업 결과를 받을 때까지이 cmdlet이 명령 프롬프트를 표시 하지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-212">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="ce0d4-213">기본적으로는 `Receive-Job` 사용 가능한 결과를 즉시 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-213">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="ce0d4-214">**Wait** 매개 변수는 기본적으로 작업이 다음 상태 중 하나일 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-214">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="ce0d4-215">Completed</span><span class="sxs-lookup"><span data-stu-id="ce0d4-215">Completed</span></span>
- <span data-ttu-id="ce0d4-216">실패</span><span class="sxs-lookup"><span data-stu-id="ce0d4-216">Failed</span></span>
- <span data-ttu-id="ce0d4-217">중지됨</span><span class="sxs-lookup"><span data-stu-id="ce0d4-217">Stopped</span></span>
- <span data-ttu-id="ce0d4-218">일시 중단</span><span class="sxs-lookup"><span data-stu-id="ce0d4-218">Suspended</span></span>
- <span data-ttu-id="ce0d4-219">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="ce0d4-219">Disconnected.</span></span>

<span data-ttu-id="ce0d4-220">작업 상태가 일시 중단 되거나 연결이 끊어진 경우 **대기 매개 변수를 계속** 대기 하려면 **wait** 매개 변수와 함께 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-220">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="ce0d4-221">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-221">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ce0d4-222">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="ce0d4-222">-WriteEvents</span></span>

<span data-ttu-id="ce0d4-223">작업이 완료 되기를 기다리는 동안이 cmdlet이 작업 상태의 변경 내용을 보고 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-223">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="ce0d4-224">이 매개 변수는 명령에서 **Wait** 매개 변수를 사용하고 **Keep** 매개 변수를 생략하는 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-224">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="ce0d4-225">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-225">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ce0d4-226">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="ce0d4-226">-WriteJobInResults</span></span>

<span data-ttu-id="ce0d4-227">이 cmdlet은 작업 개체를 반환 하 고 그 뒤에 결과를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-227">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="ce0d4-228">이 매개 변수는 명령에서 **Wait** 매개 변수를 사용하고 **Keep** 매개 변수를 생략하는 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-228">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="ce0d4-229">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ce0d4-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ce0d4-230">CommonParameters</span></span>

<span data-ttu-id="ce0d4-231">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-231">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ce0d4-232">자세한 내용은 [about_CommonParameters](./About/about_CommonParameters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-232">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ce0d4-233">입력</span><span class="sxs-lookup"><span data-stu-id="ce0d4-233">INPUTS</span></span>

### <span data-ttu-id="ce0d4-234">System.object.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-234">System.Management.Automation.Job</span></span>

<span data-ttu-id="ce0d4-235">작업 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-235">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="ce0d4-236">출력</span><span class="sxs-lookup"><span data-stu-id="ce0d4-236">OUTPUTS</span></span>

### <span data-ttu-id="ce0d4-237">PSObject</span><span class="sxs-lookup"><span data-stu-id="ce0d4-237">PSObject</span></span>

<span data-ttu-id="ce0d4-238">이 cmdlet은 작업의 명령 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce0d4-238">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="ce0d4-239">참고</span><span class="sxs-lookup"><span data-stu-id="ce0d4-239">NOTES</span></span>

## <span data-ttu-id="ce0d4-240">관련 링크</span><span class="sxs-lookup"><span data-stu-id="ce0d4-240">RELATED LINKS</span></span>

[<span data-ttu-id="ce0d4-241">Get-Job</span><span class="sxs-lookup"><span data-stu-id="ce0d4-241">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="ce0d4-242">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="ce0d4-242">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="ce0d4-243">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="ce0d4-243">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="ce0d4-244">Start-Job</span><span class="sxs-lookup"><span data-stu-id="ce0d4-244">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="ce0d4-245">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="ce0d4-245">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="ce0d4-246">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="ce0d4-246">Wait-Job</span></span>](Wait-Job.md)

