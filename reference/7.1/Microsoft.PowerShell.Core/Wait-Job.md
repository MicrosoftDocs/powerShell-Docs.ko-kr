---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: b69688891df70c396d19911624c58ae7733183d0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212665"
---
# <span data-ttu-id="a4ed9-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="a4ed9-103">Wait-Job</span></span>

## <span data-ttu-id="a4ed9-104">개요</span><span class="sxs-lookup"><span data-stu-id="a4ed9-104">SYNOPSIS</span></span>
<span data-ttu-id="a4ed9-105">세션에서 실행 중인 PowerShell 백그라운드 작업 중 하나 또는 모두가 완료 될 때까지 명령 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-105">Suppresses the command prompt until one or all of the PowerShell background jobs running in the session are completed.</span></span>

## <span data-ttu-id="a4ed9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a4ed9-106">SYNTAX</span></span>

### <span data-ttu-id="a4ed9-107">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="a4ed9-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="a4ed9-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="a4ed9-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="a4ed9-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="a4ed9-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="a4ed9-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="a4ed9-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="a4ed9-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="a4ed9-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="a4ed9-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="a4ed9-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="a4ed9-113">설명</span><span class="sxs-lookup"><span data-stu-id="a4ed9-113">DESCRIPTION</span></span>

<span data-ttu-id="a4ed9-114">**대기 작업** cmdlet은 명령 프롬프트를 표시 하기 전에 PowerShell 백그라운드 작업이 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-114">The **Wait-Job** cmdlet waits for PowerShell background jobs to finish before it displays the command prompt.</span></span>
<span data-ttu-id="a4ed9-115">백그라운드 작업 중 하나가 완료되거나 모든 백그라운드 작업이 완료될 때까지 기다릴 수 있으며 작업의 최대 대기 시간을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-115">You can wait until any background job is complete, or until all background jobs are complete, and you can set a maximum wait time for the job.</span></span>

<span data-ttu-id="a4ed9-116">작업의 명령이 완료되면 **Wait-Job** 은 명령 프롬프트를 표시하고 다른 명령으로 파이프할 수 있도록 작업 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-116">When the commands in the job are complete, **Wait-Job** displays the command prompt and returns a job object so that you can pipe it to another command.</span></span>

<span data-ttu-id="a4ed9-117">**Wait-Job** cmdlet을 사용 하 여 Start-Job cmdlet 또는 Invoke-Command Cmdlet의 *AsJob* 매개 변수를 사용 하 여 시작한 것과 같은 백그라운드 작업을 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-117">You can use **Wait-Job** cmdlet to wait for background jobs, such as those that were started by using the Start-Job cmdlet or the *AsJob* parameter of the Invoke-Command cmdlet.</span></span>
<span data-ttu-id="a4ed9-118">PowerShell 백그라운드 작업에 대 한 자세한 내용은 about_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-118">For more information about PowerShell background jobs, see about_Jobs.</span></span>

<span data-ttu-id="a4ed9-119">Windows PowerShell 3.0부터 **대기 작업** cmdlet은 워크플로 작업, 예약 된 작업 인스턴스 등의 사용자 지정 작업 유형도 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-119">Starting in Windows PowerShell 3.0, the **Wait-Job** cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="a4ed9-120">**대기 작업이** 특정 형식의 작업을 대기 하도록 설정 하려면 Import-Module cmdlet을 사용 하거나 모듈에서 cmdlet을 사용 하 여 Get-Job cmdlet을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-120">To enable **Wait-Job** to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the Get-Job cmdlet, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="a4ed9-121">특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-121">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="a4ed9-122">예제</span><span class="sxs-lookup"><span data-stu-id="a4ed9-122">EXAMPLES</span></span>

### <span data-ttu-id="a4ed9-123">예 1: 모든 작업 대기</span><span class="sxs-lookup"><span data-stu-id="a4ed9-123">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="a4ed9-124">이 명령은 세션에서 실행 중인 모든 백그라운드 작업이 완료 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-124">This command waits for all of the background jobs running in the session to finish.</span></span>

### <span data-ttu-id="a4ed9-125">예 2: Start-Job을 사용 하 여 원격 컴퓨터에서 시작 된 작업 대기</span><span class="sxs-lookup"><span data-stu-id="a4ed9-125">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="a4ed9-126">이 예제에서는 **시작-** 작업 cmdlet을 사용 하 여 원격 컴퓨터에서 시작 된 작업과 함께 **대기 작업** cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-126">This example shows how to use the **Wait-Job** cmdlet with jobs started on remote computers by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="a4ed9-127">**시작-작업** 및 **대기 작업** 명령은 모두 **호출 명령** cmdlet을 사용 하 여 원격 컴퓨터에 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-127">Both **Start-Job** and **Wait-Job** commands are submitted to the remote computer by using the **Invoke-Command** cmdlet.</span></span>

<span data-ttu-id="a4ed9-128">이 예에서는 **대기 작업** 을 사용 하 여 서로 다른 세 컴퓨터에서 백그라운드 작업으로 실행 되는 Get-Date 명령이 완료 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-128">This example uses **Wait-Job** to determine whether a Get-Date command running as a background job on three different computers is finished.</span></span>

<span data-ttu-id="a4ed9-129">첫 번째 명령은 각 원격 컴퓨터에 PowerShell 세션 ( **PSSession** )을 만든 다음 $s 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-129">The first command creates a PowerShell session ( **PSSession** ) on each of the three remote computers and stores them in the $s variable.</span></span>

<span data-ttu-id="a4ed9-130">두 번째 명령은 **Invoke 명령을** 사용 하 여 $s에 있는 세 개의 세션에서 각각 **시작 작업** 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-130">The second command uses **Invoke-Command** to run **Start-Job** in each of the three sessions in $s.</span></span>
<span data-ttu-id="a4ed9-131">모든 작업은 날짜 1로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-131">All of the jobs are named Date1.</span></span>

<span data-ttu-id="a4ed9-132">세 번째 명령은 **Invoke 명령을** 사용 하 여 **Wait 작업** 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-132">The third command uses **Invoke-Command** to run **Wait-Job** .</span></span>
<span data-ttu-id="a4ed9-133">이 명령은 각 컴퓨터에서 Date1 작업이 완료 될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-133">This command waits for the Date1 jobs on each computer to finish.</span></span>
<span data-ttu-id="a4ed9-134">작업 개체로 이루어진 결과 컬렉션(배열)을 $done 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-134">It stores the resulting collection (array) of job objects in the $done variable.</span></span>

<span data-ttu-id="a4ed9-135">네 번째 명령은 $done 변수에 있는 작업 개체 배열의 **Count** 속성을 사용 하 여 완료 된 작업의 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-135">The fourth command uses the **Count** property of the array of job objects in the $done variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="a4ed9-136">예 3: 첫 번째 백그라운드 작업이 완료 되는 시점 결정</span><span class="sxs-lookup"><span data-stu-id="a4ed9-136">Example 3: Determine when the first background job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="a4ed9-137">이 예에서는 **대기 작업** 의 *Any* 매개 변수를 사용 하 여 현재 세션에서 실행 되는 여러 백그라운드 작업의 첫 번째 작업이 완료 된 시기를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-137">This example uses the *Any* parameter of **Wait-Job** to determine when the first of many background jobs running in the current session are completed.</span></span>
<span data-ttu-id="a4ed9-138">또한 **대기 작업** cmdlet을 사용 하 여 원격 작업이 완료 될 때까지 대기 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-138">It also shows how to use the **Wait-Job** cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="a4ed9-139">첫 번째 명령은 Machines.txt 파일에 나열 된 각 컴퓨터에 **pssession** 을 만든 다음 $S 변수에 **pssession** 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-139">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the $s variable.</span></span>
<span data-ttu-id="a4ed9-140">이 명령은 Get-Content cmdlet을 사용 하 여 파일의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-140">The command uses the Get-Content cmdlet to get the contents of the file.</span></span>
<span data-ttu-id="a4ed9-141">**Get Content** 명령은 New-PSSession 명령 전에 실행 되도록 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-141">The **Get-Content** command is enclosed in parentheses to make sure that it runs before the New-PSSession command.</span></span>

<span data-ttu-id="a4ed9-142">두 번째 명령은 **Get EventLog** 명령 문자열을 따옴표로 묶어 $c 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-142">The second command stores a **Get-EventLog** command string, in quotation marks, in the $c variable.</span></span>

<span data-ttu-id="a4ed9-143">세 번째 명령은 Invoke-Command cmdlet을 사용 하 여 $s의 각 세션에서 **시작 작업** 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-143">The third command uses Invoke-Command cmdlet to run **Start-Job** in each of the sessions in $s.</span></span>
<span data-ttu-id="a4ed9-144">**시작-작업** 명령은 $C 변수의 **Get EventLog** 명령을 실행 하는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-144">The **Start-Job** command starts a background job that runs the **Get-EventLog** command in the $c variable.</span></span>

<span data-ttu-id="a4ed9-145">**Using** 범위 한정자를 사용하여 $c 변수가 로컬 컴퓨터에서 정의되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-145">The command uses the **Using** scope modifier to indicate that the $c variable was defined on the local computer.</span></span>
<span data-ttu-id="a4ed9-146">**Using** 범위 한정자는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-146">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span>
<span data-ttu-id="a4ed9-147">**Using** 범위 한정자에 대 한 자세한 내용은 [about_Remote_Variables](about/about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="a4ed9-148">네 번째 명령은 **Invoke 명령을** 사용 하 여 세션에서 **대기 작업** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-148">The fourth command uses **Invoke-Command** to run a **Wait-Job** command in the sessions.</span></span>
<span data-ttu-id="a4ed9-149">*모든* 매개 변수를 사용 하 여 원격 컴퓨터의 첫 번째 작업이 완료 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-149">It uses the *Any* parameter to wait until the first job on the remote computers is completed.</span></span>

### <span data-ttu-id="a4ed9-150">예제 4: 원격 컴퓨터에서 작업에 대 한 대기 시간 설정</span><span class="sxs-lookup"><span data-stu-id="a4ed9-150">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

<span data-ttu-id="a4ed9-151">이 예제에서는 **Wait 작업** 의 *Timeout* 매개 변수를 사용 하 여 원격 컴퓨터에서 실행 되는 작업의 최대 대기 시간을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-151">This example shows how to use the *Timeout* parameter of **Wait-Job** to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="a4ed9-152">첫 번째 명령은 원격 컴퓨터 3 개 (Server01, Server02 및 Server03) 각각에 **pssession** 을 만든 다음 $S 변수에 **pssession** 개체를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-152">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the $s variable.</span></span>

<span data-ttu-id="a4ed9-153">두 번째 명령은 **Invoke 명령을** 사용 하 여 $s의 각 **PSSession** 개체에서 **시작 작업** 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-153">The second command uses **Invoke-Command** to run **Start-Job** in each of the **PSSession** objects in $s.</span></span>
<span data-ttu-id="a4ed9-154">결과 작업 개체를 $jobs 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-154">It stores the resulting job objects in the $jobs variable.</span></span>

<span data-ttu-id="a4ed9-155">세 번째 명령은 $s의 각 세션에서 **호출 명령을** 사용 하 여 **대기 작업** 을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-155">The third command uses **Invoke-Command** to run **Wait-Job** in each of the sessions in $s.</span></span>
<span data-ttu-id="a4ed9-156">**대기 작업** 명령은 모든 명령이 30 초 이내에 완료 되었는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-156">The **Wait-Job** command determines whether all of the commands have completed within 30 seconds.</span></span>
<span data-ttu-id="a4ed9-157">*시간 제한* 매개 변수를 30 값으로 사용 하 여 최대 대기 시간을 설정 하 고 명령 결과를 $done 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-157">It uses the *Timeout* parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the $done variable.</span></span>

<span data-ttu-id="a4ed9-158">이 경우 30초 후에 Server02 컴퓨터의 명령만 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-158">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span>
<span data-ttu-id="a4ed9-159">**대기 작업이** 대기를 종료 하 고 명령 프롬프트를 표시 한 다음 완료 된 작업을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-159">**Wait-Job** ends the wait, displays the command prompt, and returns the object that represents the job that was completed.</span></span>

<span data-ttu-id="a4ed9-160">$done 변수에는 Server02에서 실행된 작업을 나타내는 작업 개체가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-160">The $done variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="a4ed9-161">예 5: 여러 작업 중 하나가 완료 될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="a4ed9-161">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="a4ed9-162">이 명령은 Id로 세 가지 작업을 식별 하 고 그 중 하나가 완료 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-162">This command identifies three jobs by their IDs and waits until any one of them are completed.</span></span>
<span data-ttu-id="a4ed9-163">첫 번째 작업이 완료 되 면 명령 프롬프트가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-163">The command prompt returns when the first job finishes.</span></span>

### <span data-ttu-id="a4ed9-164">예 6: 일정 기간 동안 기다린 후 작업이 백그라운드에서 계속 되도록 허용</span><span class="sxs-lookup"><span data-stu-id="a4ed9-164">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="a4ed9-165">이 명령은 DailyLog 작업이 완료 될 때까지 120 초 (2 분) 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-165">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span>
<span data-ttu-id="a4ed9-166">작업이 다음 2 분 이내에 완료 되지 않으면 명령 프롬프트가 반환 되 고 작업은 백그라운드에서 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-166">If the job does not finish in the next two minutes, the command prompt returns anyway, and the job continues to run in the background.</span></span>

### <span data-ttu-id="a4ed9-167">예 7: 이름으로 작업 대기</span><span class="sxs-lookup"><span data-stu-id="a4ed9-167">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="a4ed9-168">이 명령은 작업 이름을 사용 하 여 기다릴 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-168">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="a4ed9-169">예 8: Start-Job 시작 하 여 로컬 컴퓨터에서 작업 대기</span><span class="sxs-lookup"><span data-stu-id="a4ed9-169">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="a4ed9-170">이 예제에서는 **시작 작업** 을 사용 하 여 로컬 컴퓨터에서 시작 된 작업과 함께 **대기 작업** cmdlet을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-170">This example shows how to use the **Wait-Job** cmdlet with jobs started on the local computer by using **Start-Job** .</span></span>

<span data-ttu-id="a4ed9-171">이러한 명령은 지난 주에 추가 되거나 업데이트 된 PowerShell 스크립트 파일을 가져오는 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-171">These commands start a job that gets the PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="a4ed9-172">첫 번째 명령은 **시작 작업** 을 사용 하 여 로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-172">The first command uses **Start-Job** to start a background job on the local computer.</span></span>
<span data-ttu-id="a4ed9-173">작업은 지난 주에 추가 되거나 업데이트 된 파일 이름 확장명이 ps1 인 파일을 모두 가져오는 Get-ChildItem 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-173">The job runs a Get-ChildItem command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="a4ed9-174">세 번째 명령은 **대기 작업** 을 사용 하 여 작업이 완료 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-174">The third command uses **Wait-Job** to wait until the job is completed.</span></span>
<span data-ttu-id="a4ed9-175">작업이 완료 되 면 명령에서 작업에 대 한 정보가 포함 된 작업 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-175">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="a4ed9-176">예 9: Invoke-Command을 사용 하 여 원격 컴퓨터에서 시작 된 작업 대기</span><span class="sxs-lookup"><span data-stu-id="a4ed9-176">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="a4ed9-177">이 예제에서는 **호출 명령의** *AsJob* 매개 변수를 사용 하 여 원격 컴퓨터에서 시작 된 작업과 함께 **대기 작업** 을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-177">This example shows how to use **Wait-Job** with jobs started on remote computers by using the *AsJob* parameter of **Invoke-Command** .</span></span>
<span data-ttu-id="a4ed9-178">*AsJob* 을 사용할 경우 작업이 원격 컴퓨터에서 실행 되는 경우에도 로컬 컴퓨터에 작업이 만들어지고 결과가 로컬 컴퓨터에 자동으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-178">When using *AsJob* , the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="a4ed9-179">이 예에서는 **대기 작업** 을 사용 하 여 원격 컴퓨터 3 대의 세션에서 실행 중인 **Get Process** 명령이 완료 되었는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-179">This example uses **Wait-Job** to determine whether a **Get-Process** command running in the sessions on three remote computers is completed.</span></span>

<span data-ttu-id="a4ed9-180">첫 번째 명령은 3 대의 컴퓨터에 **PSSession** 개체를 만들어 $s 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-180">The first command creates **PSSession** objects on three computers and stores them in the $s variable.</span></span>

<span data-ttu-id="a4ed9-181">두 번째 명령은 **Invoke 명령을** 사용 하 여 $s에 있는 세 개의 세션에서 각각 **Get Process** 를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-181">The second command uses **Invoke-Command** to run **Get-Process** in each of the three sessions in $s.</span></span>
<span data-ttu-id="a4ed9-182">이 명령은 *AsJob* 매개 변수를 사용 하 여 백그라운드 작업으로 비동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-182">The command uses the *AsJob* parameter to run the command asynchronously as a background job.</span></span>
<span data-ttu-id="a4ed9-183">이 명령은 **시작 작업** 을 사용 하 여 시작 된 작업과 마찬가지로 작업 개체를 반환 하 고, 작업 개체는 $j 변수에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-183">The command returns a job object, just like the jobs started by using **Start-Job** , and the job object is stored in the $j variable.</span></span>

<span data-ttu-id="a4ed9-184">세 번째 명령은 파이프라인 연산자 (|)를 사용 하 여 $j의 작업 개체를 **대기 작업** cmdlet으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-184">The third command uses a pipeline operator (|) to send the job object in $j to the **Wait-Job** cmdlet.</span></span>
<span data-ttu-id="a4ed9-185">작업이 로컬 컴퓨터에 있기 때문에이 경우에는 **명령 호출** 명령이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-185">An **Invoke-Command** command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="a4ed9-186">예 10: ID가 있는 작업 대기</span><span class="sxs-lookup"><span data-stu-id="a4ed9-186">Example 10: Wait for a job that has an ID</span></span>

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

<span data-ttu-id="a4ed9-187">이 명령은 ID 값이 1인 작업이 완료될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-187">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="a4ed9-188">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a4ed9-188">PARAMETERS</span></span>

### <span data-ttu-id="a4ed9-189">-Any</span><span class="sxs-lookup"><span data-stu-id="a4ed9-189">-Any</span></span>

<span data-ttu-id="a4ed9-190">작업이 완료 되 면이 cmdlet이 명령 프롬프트를 표시 하 고 작업 개체를 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-190">Indicates that this cmdlet displays the command prompt, and returns the job object, when any job finishes.</span></span>
<span data-ttu-id="a4ed9-191">기본적으로 **대기 작업** 은 지정 된 모든 작업이 완료 될 때까지 대기한 후 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-191">By default, **Wait-Job** waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="a4ed9-192">-Filter</span><span class="sxs-lookup"><span data-stu-id="a4ed9-192">-Filter</span></span>

<span data-ttu-id="a4ed9-193">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-193">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="a4ed9-194">이 cmdlet은 해시 테이블의 모든 조건을 충족 하는 작업을 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-194">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span>
<span data-ttu-id="a4ed9-195">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-195">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="a4ed9-196">이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-196">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="a4ed9-197">**시작 작업** cmdlet을 사용 하 여 만든 것과 같은 표준 백그라운드 작업에서는 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-197">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="a4ed9-198">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-198">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="a4ed9-199">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a4ed9-200">-Force</span><span class="sxs-lookup"><span data-stu-id="a4ed9-200">-Force</span></span>

<span data-ttu-id="a4ed9-201">이 cmdlet이 일시 중단 되었거나 연결 되지 않은 상태의 작업을 계속 대기 하 고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-201">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span>
<span data-ttu-id="a4ed9-202">기본적으로 **Wait 작업** 은 작업이 다음 상태 중 하나일 때 대기를 반환 하거나 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-202">By default, **Wait-Job** returns, or ends  the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="a4ed9-203">Completed</span><span class="sxs-lookup"><span data-stu-id="a4ed9-203">Completed</span></span>
- <span data-ttu-id="a4ed9-204">실패</span><span class="sxs-lookup"><span data-stu-id="a4ed9-204">Failed</span></span>
- <span data-ttu-id="a4ed9-205">중지됨</span><span class="sxs-lookup"><span data-stu-id="a4ed9-205">Stopped</span></span>
- <span data-ttu-id="a4ed9-206">일시 중단</span><span class="sxs-lookup"><span data-stu-id="a4ed9-206">Suspended</span></span>
- <span data-ttu-id="a4ed9-207">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="a4ed9-207">Disconnected</span></span>

<span data-ttu-id="a4ed9-208">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a4ed9-209">-Id</span><span class="sxs-lookup"><span data-stu-id="a4ed9-209">-Id</span></span>

<span data-ttu-id="a4ed9-210">이 cmdlet이 대기 하는 작업의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-210">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="a4ed9-211">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-211">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="a4ed9-212">인스턴스 ID 보다 더 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-212">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="a4ed9-213">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-213">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="a4ed9-214">작업 ID를 찾으려면를 입력 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-214">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="a4ed9-215">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="a4ed9-215">-InstanceId</span></span>

<span data-ttu-id="a4ed9-216">이 cmdlet이 대기 하는 작업의 인스턴스 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-216">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span>
<span data-ttu-id="a4ed9-217">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-217">The default is all jobs.</span></span>

<span data-ttu-id="a4ed9-218">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-218">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="a4ed9-219">작업의 인스턴스 ID를 찾으려면 **Get-Job** 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-219">To find the instance ID of a job, use **Get-Job** .</span></span>

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

### <span data-ttu-id="a4ed9-220">-Job</span><span class="sxs-lookup"><span data-stu-id="a4ed9-220">-Job</span></span>

<span data-ttu-id="a4ed9-221">이 cmdlet이 대기 하는 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-221">Specifies the jobs for which this cmdlet waits.</span></span>
<span data-ttu-id="a4ed9-222">작업 개체가 포함된 변수 또는 작업 개체를 가져오는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-222">Enter a variable that contains the job objects or a command that gets the job objects.</span></span>
<span data-ttu-id="a4ed9-223">파이프라인 연산자를 사용 하 여 작업 개체를 **대기 작업** cmdlet으로 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-223">You can also use a pipeline operator to send job objects to the **Wait-Job** cmdlet.</span></span>
<span data-ttu-id="a4ed9-224">기본적으로 **대기 작업** 은 현재 세션에서 생성 된 모든 작업을 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-224">By default, **Wait-Job** waits for all jobs created in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a4ed9-225">-Name</span><span class="sxs-lookup"><span data-stu-id="a4ed9-225">-Name</span></span>

<span data-ttu-id="a4ed9-226">이 cmdlet이 대기 하는 작업의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-226">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a4ed9-227">-상태</span><span class="sxs-lookup"><span data-stu-id="a4ed9-227">-State</span></span>

<span data-ttu-id="a4ed9-228">작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-228">Specifies a job state.</span></span>
<span data-ttu-id="a4ed9-229">이 cmdlet은 지정 된 상태의 작업만 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-229">This cmdlet waits only for jobs in the specified state.</span></span>
<span data-ttu-id="a4ed9-230">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a4ed9-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="a4ed9-231">NotStarted</span></span>
- <span data-ttu-id="a4ed9-232">실행 중</span><span class="sxs-lookup"><span data-stu-id="a4ed9-232">Running</span></span>
- <span data-ttu-id="a4ed9-233">완료됨</span><span class="sxs-lookup"><span data-stu-id="a4ed9-233">Completed</span></span>
- <span data-ttu-id="a4ed9-234">실패</span><span class="sxs-lookup"><span data-stu-id="a4ed9-234">Failed</span></span>
- <span data-ttu-id="a4ed9-235">중지됨</span><span class="sxs-lookup"><span data-stu-id="a4ed9-235">Stopped</span></span>
- <span data-ttu-id="a4ed9-236">차단</span><span class="sxs-lookup"><span data-stu-id="a4ed9-236">Blocked</span></span>
- <span data-ttu-id="a4ed9-237">일시 중단</span><span class="sxs-lookup"><span data-stu-id="a4ed9-237">Suspended</span></span>
- <span data-ttu-id="a4ed9-238">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="a4ed9-238">Disconnected</span></span>
- <span data-ttu-id="a4ed9-239">Suspending</span><span class="sxs-lookup"><span data-stu-id="a4ed9-239">Suspending</span></span>
- <span data-ttu-id="a4ed9-240">중지 중</span><span class="sxs-lookup"><span data-stu-id="a4ed9-240">Stopping</span></span>

<span data-ttu-id="a4ed9-241">작업 상태에 대 한 자세한 내용은 MSDN library에서 [JobState 열거](https://msdn.microsoft.com/library/system.management.automation.jobstate) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-241">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="a4ed9-242">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="a4ed9-242">-Timeout</span></span>

<span data-ttu-id="a4ed9-243">각 백그라운드 작업에 대 한 최대 대기 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-243">Specifies the maximum wait time for each background job, in seconds.</span></span>
<span data-ttu-id="a4ed9-244">기본값-1은 작업이 완료 될 때까지 cmdlet이 대기 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-244">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span>
<span data-ttu-id="a4ed9-245">타이밍은 **시작-** 작업 명령이 아닌 **대기 작업** 명령을 제출할 때 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-245">The timing starts when you submit the **Wait-Job** command, not the **Start-Job** command.</span></span>

<span data-ttu-id="a4ed9-246">이 시간을 초과할 경우 작업이 여전히 실행 중이어도 대기가 종료되고 명령 프롬프트가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-246">If this time is exceeded, the wait ends and the command prompt returns, even if the job is still running.</span></span>
<span data-ttu-id="a4ed9-247">이 명령은 오류 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-247">The command does not display any error message.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a4ed9-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a4ed9-248">CommonParameters</span></span>

<span data-ttu-id="a4ed9-249">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a4ed9-250">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a4ed9-251">입력</span><span class="sxs-lookup"><span data-stu-id="a4ed9-251">INPUTS</span></span>

### <span data-ttu-id="a4ed9-252">System.web. Remorererea 작업</span><span class="sxs-lookup"><span data-stu-id="a4ed9-252">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="a4ed9-253">작업 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-253">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="a4ed9-254">출력</span><span class="sxs-lookup"><span data-stu-id="a4ed9-254">OUTPUTS</span></span>

### <span data-ttu-id="a4ed9-255">System.web. a p.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-255">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="a4ed9-256">이 cmdlet은 완료 된 작업을 나타내는 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-256">This cmdlet returns job objects that represent the completed jobs.</span></span>
<span data-ttu-id="a4ed9-257">*Timeout* 매개 변수의 값이 초과 되어 대기가 종료 되 면 **wait-Job** 은 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-257">If the wait ends because the value of the *Timeout* parameter is exceeded, **Wait-Job** does not return any objects.</span></span>

## <span data-ttu-id="a4ed9-258">참고</span><span class="sxs-lookup"><span data-stu-id="a4ed9-258">NOTES</span></span>

* <span data-ttu-id="a4ed9-259">기본적으로 **Wait 작업** 은 작업이 다음 상태 중 하나일 때 대기를 반환 하거나 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-259">By default, **Wait-Job** returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="a4ed9-260">Completed</span><span class="sxs-lookup"><span data-stu-id="a4ed9-260">Completed</span></span>
- <span data-ttu-id="a4ed9-261">실패</span><span class="sxs-lookup"><span data-stu-id="a4ed9-261">Failed</span></span>
- <span data-ttu-id="a4ed9-262">중지됨</span><span class="sxs-lookup"><span data-stu-id="a4ed9-262">Stopped</span></span>
- <span data-ttu-id="a4ed9-263">일시 중단</span><span class="sxs-lookup"><span data-stu-id="a4ed9-263">Suspended</span></span>
- <span data-ttu-id="a4ed9-264">일시 중단 된 작업 및 연결 되지 않은 작업을 계속 대기 하기 위해 직접 **대기 작업** 으로의 연결을 끊었습니다. *Force* 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a4ed9-264">Disconnected To direct **Wait-Job** to continue to wait for Suspended and Disconnected jobs, use the *Force* parameter.</span></span>

## <span data-ttu-id="a4ed9-265">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a4ed9-265">RELATED LINKS</span></span>

[<span data-ttu-id="a4ed9-266">Get-Job</span><span class="sxs-lookup"><span data-stu-id="a4ed9-266">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="a4ed9-267">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a4ed9-267">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="a4ed9-268">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="a4ed9-268">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="a4ed9-269">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="a4ed9-269">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="a4ed9-270">Start-Job</span><span class="sxs-lookup"><span data-stu-id="a4ed9-270">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="a4ed9-271">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="a4ed9-271">Stop-Job</span></span>](Stop-Job.md)

