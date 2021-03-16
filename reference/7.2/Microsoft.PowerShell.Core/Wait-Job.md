---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/28/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: ffcd0fba9fae9ed49e7f20fa5a971e6e50fc445f
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99602047"
---
# <span data-ttu-id="e768a-102">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="e768a-102">Wait-Job</span></span>

## <span data-ttu-id="e768a-103">개요</span><span class="sxs-lookup"><span data-stu-id="e768a-103">SYNOPSIS</span></span>
<span data-ttu-id="e768a-104">세션에서 실행 중인 PowerShell 작업 중 하나 또는 전체가 종료 상태일 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-104">Waits until one or all of the PowerShell jobs running in the session are in a terminating state.</span></span>

## <span data-ttu-id="e768a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e768a-105">SYNTAX</span></span>

### <span data-ttu-id="e768a-106">SessionIdParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="e768a-106">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="e768a-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="e768a-107">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="e768a-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="e768a-108">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="e768a-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="e768a-109">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="e768a-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="e768a-110">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="e768a-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="e768a-111">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="e768a-112">설명</span><span class="sxs-lookup"><span data-stu-id="e768a-112">DESCRIPTION</span></span>

<span data-ttu-id="e768a-113">`Wait-Job`Cmdlet은 실행을 계속 하기 전에 작업이 종료 상태가 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-113">The `Wait-Job` cmdlet waits for a job to be in a terminating state before continuing execution.</span></span>
<span data-ttu-id="e768a-114">종료 상태는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-114">The terminating states are:</span></span>

- <span data-ttu-id="e768a-115">Completed</span><span class="sxs-lookup"><span data-stu-id="e768a-115">Completed</span></span>
- <span data-ttu-id="e768a-116">실패</span><span class="sxs-lookup"><span data-stu-id="e768a-116">Failed</span></span>
- <span data-ttu-id="e768a-117">중지됨</span><span class="sxs-lookup"><span data-stu-id="e768a-117">Stopped</span></span>
- <span data-ttu-id="e768a-118">일시 중단</span><span class="sxs-lookup"><span data-stu-id="e768a-118">Suspended</span></span>
- <span data-ttu-id="e768a-119">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="e768a-119">Disconnected</span></span>

<span data-ttu-id="e768a-120">지정 된 작업 또는 모든 작업이 종료 상태가 될 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-120">You can wait until a specified job, or all jobs are in a terminating state.</span></span> <span data-ttu-id="e768a-121">**Timeout** 매개 변수를 사용 하 여 작업에 대 한 최대 대기 시간을 설정 하거나 **Force** 매개 변수를 사용 하 여 또는 상태의 작업을 대기할 수도 있습니다 `Suspended` `Disconnected` .</span><span class="sxs-lookup"><span data-stu-id="e768a-121">You can also set a maximum wait time for the job using the **Timeout** parameter, or use the **Force** parameter to wait for a job in the `Suspended` or `Disconnected` states.</span></span>

<span data-ttu-id="e768a-122">작업의 명령이 완료 되 면에서 `Wait-Job` 작업 개체를 반환 하 고 실행을 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-122">When the commands in the job are complete, `Wait-Job` returns a job object and continues execution.</span></span>

<span data-ttu-id="e768a-123">Cmdlet을 사용 하 여 cmdlet `Wait-Job` `Start-Job` 또는 Cmdlet의 **AsJob** 매개 변수를 사용 하 여 시작 된 작업을 대기할 수 있습니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e768a-123">You can use the `Wait-Job` cmdlet to wait for jobs started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="e768a-124">작업에 대한 자세한 내용은 [about_Jobs](./about/about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e768a-124">For more information about jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="e768a-125">Windows PowerShell 3.0부터 `Wait-Job` cmdlet은 워크플로 작업, 예약 된 작업 인스턴스 등의 사용자 지정 작업 유형도 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-125">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="e768a-126">를 사용 하 여 `Wait-Job` 특정 형식의 작업을 대기 하려면 cmdlet `Get-Job` 을 사용 `Import-Module` 하거나 모듈에서 cmdlet을 사용 하 여 cmdlet을 실행 하기 전에 사용자 지정 작업 유형을 지 원하는 모듈을 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-126">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="e768a-127">특정한 사용자 지정 작업 유형에 대한 자세한 내용은 사용자 지정 작업 유형 기능에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e768a-127">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="e768a-128">예제</span><span class="sxs-lookup"><span data-stu-id="e768a-128">EXAMPLES</span></span>

### <span data-ttu-id="e768a-129">예 1: 모든 작업 대기</span><span class="sxs-lookup"><span data-stu-id="e768a-129">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="e768a-130">이 명령은 세션에서 실행 중인 모든 작업이 완료 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-130">This command waits for all of the jobs running in the session to finish.</span></span>

### <span data-ttu-id="e768a-131">예 2: Start-Job을 사용 하 여 원격 컴퓨터에서 시작 된 작업 대기</span><span class="sxs-lookup"><span data-stu-id="e768a-131">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="e768a-132">이 예에서는 cmdlet을 사용 하 `Wait-Job` 여 원격 컴퓨터에서 시작 된 작업과 cmdlet을 사용 하는 방법을 보여 줍니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="e768a-132">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="e768a-133">`Start-Job`및 `Wait-Job` 명령은 모두 cmdlet을 사용 하 여 원격 컴퓨터에 전송 됩니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e768a-133">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="e768a-134">이 예에서는 `Wait-Job` 를 사용 하 여 `Get-Date` 세 개의 컴퓨터에서 작업으로 실행 되는 명령이 완료 되었는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-134">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a job on three different computers is finished.</span></span>

<span data-ttu-id="e768a-135">첫 번째 명령은 각 원격 컴퓨터에 Windows PowerShell 세션 (**PSSession**)을 만든 다음 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="e768a-135">The first command creates a Windows PowerShell session (**PSSession**) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="e768a-136">두 번째 명령은 `Invoke-Command` 를 사용 하 여 `Start-Job` 에 있는 세 개의 세션에서를 실행 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-136">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="e768a-137">모든 작업은 날짜 1로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-137">All of the jobs are named Date1.</span></span>

<span data-ttu-id="e768a-138">세 번째 명령은 `Invoke-Command` 를 사용 하 여를 실행 `Wait-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-138">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="e768a-139">이 명령은 `Date1` 각 컴퓨터의 작업이 완료 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-139">This command waits for the `Date1` jobs on each computer to finish.</span></span> <span data-ttu-id="e768a-140">**작업** 개체의 결과 컬렉션 (**배열**)을 `$done` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-140">It stores the resulting collection (**array**) of **job** objects in the `$done` variable.</span></span>

<span data-ttu-id="e768a-141">네 번째 명령은 변수에 작업 개체 배열의 **Count** 속성을 사용 하 여 `$done` 완료 된 작업의 수를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-141">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="e768a-142">예 3: 첫 번째 작업이 완료 되는 시간 확인</span><span class="sxs-lookup"><span data-stu-id="e768a-142">Example 3: Determine when the first job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="e768a-143">이 예제에서는의 **Any** 매개 변수를 사용 하 여 `Wait-Job` 현재 세션에서 실행 중인 대부분의 작업이 종료 상태 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-143">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many jobs running in the current session are in a terminating state.</span></span> <span data-ttu-id="e768a-144">또한 cmdlet을 사용 하 여 `Wait-Job` 원격 작업이 완료 될 때까지 대기 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-144">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="e768a-145">첫 번째 명령은 Machines.txt 파일에 나열 된 각 컴퓨터에 **pssession** 을 만들고 **pssession** 개체를 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="e768a-145">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="e768a-146">이 명령은 cmdlet을 사용 하 여 `Get-Content` 파일의 내용을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-146">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="e768a-147">명령은 `Get-Content` 명령 전에 실행 되도록 괄호로 묶습니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e768a-147">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="e768a-148">두 번째 명령은 `Get-EventLog` 변수에 명령 문자열 (따옴표)을 저장 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="e768a-148">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="e768a-149">세 번째 명령은 cmdlet을 사용 하 여의 `Invoke-Command` `Start-Job` 각 세션에서를 실행 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-149">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="e768a-150">`Start-Job`명령은 `Get-EventLog` 변수에서 명령을 실행 하는 작업을 시작 합니다 `$c` .</span><span class="sxs-lookup"><span data-stu-id="e768a-150">The `Start-Job` command starts a job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="e768a-151">이 명령은 **Using** 범위 한정자를 사용 하 여 `$c` 변수가 로컬 컴퓨터에 정의 되어 있음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-151">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="e768a-152">**Using** 범위 한정자는 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-152">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="e768a-153">**Using** 범위 한정자에 대 한 자세한 내용은 [about_Remote_Variables](./about/about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e768a-153">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="e768a-154">네 번째 명령은 `Invoke-Command` 를 사용 하 여 `Wait-Job` 세션에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-154">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="e768a-155">**모든** 매개 변수를 사용 하 여 원격 컴퓨터의 첫 번째 작업이 종료 상태가 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-155">It uses the **Any** parameter to wait until the first job on the remote computers is terminating state.</span></span>

### <span data-ttu-id="e768a-156">예제 4: 원격 컴퓨터에서 작업에 대 한 대기 시간 설정</span><span class="sxs-lookup"><span data-stu-id="e768a-156">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
PS> $s = New-PSSession Server01, Server02, Server03
PS> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
PS>
```

<span data-ttu-id="e768a-157">이 예제에서는의 **Timeout** 매개 변수를 사용 하 여 `Wait-Job` 원격 컴퓨터에서 실행 되는 작업의 최대 대기 시간을 설정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-157">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="e768a-158">첫 번째 명령은 원격 컴퓨터 3 개 (Server01, Server02 및 Server03) 각각에 **pssession** 을 만든 다음, **pssession** 개체를 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="e768a-158">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="e768a-159">두 번째 명령은를 사용 하 여의 `Invoke-Command` `Start-Job` 각 **PSSession** 개체에서를 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="e768a-159">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="e768a-160">결과 작업 개체를 `$jobs` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-160">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="e768a-161">세 번째 명령은를 사용 하 여의 `Invoke-Command` `Wait-Job` 각 세션에서를 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="e768a-161">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="e768a-162">`Wait-Job`명령은 모든 명령이 30 초 이내에 완료 되었는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-162">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="e768a-163">**시간 제한** 매개 변수를 30 값으로 사용 하 여 최대 대기 시간을 설정 하 고 명령의 결과를 `$done` 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-163">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="e768a-164">이 경우 30초 후에 Server02 컴퓨터의 명령만 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-164">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="e768a-165">`Wait-Job` 대기를 종료 하 고 완료 된 작업을 나타내는 개체를 반환 하 고 명령 프롬프트를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-165">`Wait-Job` ends the wait, returns the object that represents the job that was completed, and displays the command prompt.</span></span>

<span data-ttu-id="e768a-166">`$done`변수에는 Server02에서 실행 된 작업을 나타내는 작업 개체가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-166">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="e768a-167">예 5: 여러 작업 중 하나가 완료 될 때까지 대기</span><span class="sxs-lookup"><span data-stu-id="e768a-167">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="e768a-168">이 명령은 Id로 세 작업을 식별 하 고 그 중 하나가 종료 상태일 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-168">This command identifies three jobs by their IDs and waits until any one of them are in a terminating state.</span></span> <span data-ttu-id="e768a-169">첫 번째 작업이 완료 되 면 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-169">Execution continues when the first job finishes.</span></span>

### <span data-ttu-id="e768a-170">예 6: 일정 기간 동안 기다린 후 작업이 백그라운드에서 계속 되도록 허용</span><span class="sxs-lookup"><span data-stu-id="e768a-170">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="e768a-171">이 명령은 DailyLog 작업이 완료 될 때까지 120 초 (2 분) 동안 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-171">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="e768a-172">작업이 다음 2 분 이내에 완료 되지 않으면 실행이 계속 되 고 작업은 백그라운드에서 계속 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-172">If the job does not finish in the next two minutes, execution continues, and the job continues to run in the background.</span></span>

### <span data-ttu-id="e768a-173">예 7: 이름으로 작업 대기</span><span class="sxs-lookup"><span data-stu-id="e768a-173">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="e768a-174">이 명령은 작업 이름을 사용 하 여 기다릴 작업을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-174">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="e768a-175">예 8: Start-Job 시작 하 여 로컬 컴퓨터에서 작업 대기</span><span class="sxs-lookup"><span data-stu-id="e768a-175">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_.lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="e768a-176">이 예에서는를 `Wait-Job` 사용 하 여 로컬 컴퓨터에서 시작 된 작업에 cmdlet을 사용 하는 방법을 보여 줍니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="e768a-176">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="e768a-177">이 명령은 지난주에 추가 또는 업데이트된 Windows PowerShell 스크립트 파일을 가져오는 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-177">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="e768a-178">첫 번째 명령은 `Start-Job` 를 사용 하 여 로컬 컴퓨터에서 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-178">The first command uses `Start-Job` to start a job on the local computer.</span></span> <span data-ttu-id="e768a-179">작업은 `Get-ChildItem` 지난 주에 추가 되거나 업데이트 된 ps1 파일 이름 확장명을 가진 모든 파일을 가져오는 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-179">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="e768a-180">세 번째 명령은를 사용 하 여 `Wait-Job` 작업이 종료 상태가 될 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-180">The third command uses `Wait-Job` to wait until the job is in a terminating state.</span></span> <span data-ttu-id="e768a-181">작업이 완료 되 면 명령에서 작업에 대 한 정보가 포함 된 작업 개체를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-181">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="e768a-182">예 9: Invoke-Command을 사용 하 여 원격 컴퓨터에서 시작 된 작업 대기</span><span class="sxs-lookup"><span data-stu-id="e768a-182">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="e768a-183">이 예에서는 `Wait-Job` 의 **AsJob** 매개 변수를 사용 하 여 원격 컴퓨터에서 시작 된 작업과 함께를 사용 하는 방법을 보여 줍니다 `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="e768a-183">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="e768a-184">**AsJob** 을 사용할 경우 작업이 원격 컴퓨터에서 실행 되는 경우에도 로컬 컴퓨터에 작업이 만들어지고 결과가 로컬 컴퓨터에 자동으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-184">When using **AsJob**, the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="e768a-185">이 예에서는 `Wait-Job` 를 사용 하 여 `Get-Process` 원격 컴퓨터 3 대의 세션에서 실행 중인 명령이 종료 상태 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-185">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is in a terminating state.</span></span>

<span data-ttu-id="e768a-186">첫 번째 명령은 3 대의 컴퓨터에 **PSSession** 개체를 만든 후 변수에 저장 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="e768a-186">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="e768a-187">두 번째 명령은 `Invoke-Command` 를 사용 하 여 `Get-Process` 에 있는 세 개의 세션에서를 실행 `$s` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-187">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="e768a-188">이 명령은 **AsJob** 매개 변수를 사용 하 여 작업으로 비동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-188">The command uses the **AsJob** parameter to run the command asynchronously as a job.</span></span> <span data-ttu-id="e768a-189">를 사용 하 여 시작 된 작업과 마찬가지로 작업 개체가 반환 `Start-Job` 되 고 작업 개체가 변수에 저장 됩니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="e768a-189">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="e768a-190">세 번째 명령은 파이프라인 연산자 ()를 사용 하 여 `|` 작업 개체를 `$j` cmdlet으로 보냅니다 `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="e768a-190">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="e768a-191">`Invoke-Command`작업이 로컬 컴퓨터에 있기 때문에이 경우에는 명령이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-191">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="e768a-192">예 10: ID가 있는 작업 대기</span><span class="sxs-lookup"><span data-stu-id="e768a-192">Example 10: Wait for a job that has an ID</span></span>

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

<span data-ttu-id="e768a-193">이 명령은 ID 값이 1인 작업이 완료될 때까지 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-193">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="e768a-194">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e768a-194">PARAMETERS</span></span>

### <span data-ttu-id="e768a-195">-Any</span><span class="sxs-lookup"><span data-stu-id="e768a-195">-Any</span></span>

<span data-ttu-id="e768a-196">이 cmdlet은 작업 개체를 반환 하 고 작업이 완료 되 면 실행을 계속 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-196">Indicates that this cmdlet returns the job object and continues execution when any job finishes.</span></span> <span data-ttu-id="e768a-197">기본적으로는 `Wait-Job` 지정 된 모든 작업이 완료 될 때까지 기다렸다가 프롬프트가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-197">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="e768a-198">-Filter</span><span class="sxs-lookup"><span data-stu-id="e768a-198">-Filter</span></span>

<span data-ttu-id="e768a-199">조건에 대 한 해시 테이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-199">Specifies a hash table of conditions.</span></span> <span data-ttu-id="e768a-200">이 cmdlet은 해시 테이블의 모든 조건을 충족 하는 작업을 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-200">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="e768a-201">키는 작업 속성이고 값은 작업 속성 값인 해시 테이블을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-201">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="e768a-202">이 매개 변수는 워크플로 작업, 예약된 작업 등의 사용자 지정 작업 유형에서만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-202">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="e768a-203">Cmdlet을 사용 하 여 만든 것과 같은 표준 작업에서는 작동 하지 않습니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="e768a-203">It does not work on standard jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="e768a-204">이 매개 변수 지원에 대한 자세한 내용은 작업 유형 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e768a-204">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="e768a-205">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-205">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e768a-206">-Force</span><span class="sxs-lookup"><span data-stu-id="e768a-206">-Force</span></span>

<span data-ttu-id="e768a-207">이 cmdlet이 일시 중단 되었거나 연결 되지 않은 상태의 작업을 계속 대기 하 고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-207">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="e768a-208">기본적으로는 `Wait-Job` 작업이 다음 상태 중 하나일 때 대기를 반환 하거나 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-208">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="e768a-209">Completed</span><span class="sxs-lookup"><span data-stu-id="e768a-209">Completed</span></span>
- <span data-ttu-id="e768a-210">실패</span><span class="sxs-lookup"><span data-stu-id="e768a-210">Failed</span></span>
- <span data-ttu-id="e768a-211">중지됨</span><span class="sxs-lookup"><span data-stu-id="e768a-211">Stopped</span></span>
- <span data-ttu-id="e768a-212">일시 중단</span><span class="sxs-lookup"><span data-stu-id="e768a-212">Suspended</span></span>
- <span data-ttu-id="e768a-213">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="e768a-213">Disconnected</span></span>

<span data-ttu-id="e768a-214">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-214">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="e768a-215">-Id</span><span class="sxs-lookup"><span data-stu-id="e768a-215">-Id</span></span>

<span data-ttu-id="e768a-216">이 cmdlet이 대기 하는 작업의 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-216">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="e768a-217">ID는 현재 세션에서 작업을 고유 하 게 식별 하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-217">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="e768a-218">인스턴스 ID 보다 더 쉽게 기억할 수 있으며, 입력은 현재 세션 에서만 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-218">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="e768a-219">하나 이상의 Id를 쉼표로 구분 하 여 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-219">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="e768a-220">작업 ID를 찾으려면를 입력 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-220">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="e768a-221">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="e768a-221">-InstanceId</span></span>

<span data-ttu-id="e768a-222">이 cmdlet이 대기 하는 작업의 인스턴스 Id 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-222">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="e768a-223">기본값은 모든 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-223">The default is all jobs.</span></span>

<span data-ttu-id="e768a-224">인스턴스 ID는 컴퓨터에서 작업을 고유하게 식별하는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-224">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="e768a-225">작업의 인스턴스 ID를 찾으려면를 사용 `Get-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-225">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="e768a-226">-Job</span><span class="sxs-lookup"><span data-stu-id="e768a-226">-Job</span></span>

<span data-ttu-id="e768a-227">이 cmdlet이 대기 하는 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-227">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="e768a-228">작업 개체가 포함된 변수 또는 작업 개체를 가져오는 명령을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="e768a-228">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="e768a-229">파이프라인 연산자를 사용 하 여 작업 개체를 cmdlet으로 보낼 수도 있습니다 `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="e768a-229">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="e768a-230">기본적으로는 `Wait-Job` 현재 세션에서 생성 된 모든 작업을 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-230">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="e768a-231">-Name</span><span class="sxs-lookup"><span data-stu-id="e768a-231">-Name</span></span>

<span data-ttu-id="e768a-232">이 cmdlet이 대기 하는 작업의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-232">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

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

### <span data-ttu-id="e768a-233">-상태</span><span class="sxs-lookup"><span data-stu-id="e768a-233">-State</span></span>

<span data-ttu-id="e768a-234">작업 상태를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-234">Specifies a job state.</span></span> <span data-ttu-id="e768a-235">이 cmdlet은 지정 된 상태의 작업만 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-235">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="e768a-236">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-236">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="e768a-237">NotStarted</span><span class="sxs-lookup"><span data-stu-id="e768a-237">NotStarted</span></span>
- <span data-ttu-id="e768a-238">실행 중</span><span class="sxs-lookup"><span data-stu-id="e768a-238">Running</span></span>
- <span data-ttu-id="e768a-239">완료됨</span><span class="sxs-lookup"><span data-stu-id="e768a-239">Completed</span></span>
- <span data-ttu-id="e768a-240">실패</span><span class="sxs-lookup"><span data-stu-id="e768a-240">Failed</span></span>
- <span data-ttu-id="e768a-241">중지됨</span><span class="sxs-lookup"><span data-stu-id="e768a-241">Stopped</span></span>
- <span data-ttu-id="e768a-242">차단</span><span class="sxs-lookup"><span data-stu-id="e768a-242">Blocked</span></span>
- <span data-ttu-id="e768a-243">일시 중단</span><span class="sxs-lookup"><span data-stu-id="e768a-243">Suspended</span></span>
- <span data-ttu-id="e768a-244">연결 끊김</span><span class="sxs-lookup"><span data-stu-id="e768a-244">Disconnected</span></span>
- <span data-ttu-id="e768a-245">Suspending</span><span class="sxs-lookup"><span data-stu-id="e768a-245">Suspending</span></span>
- <span data-ttu-id="e768a-246">중지 중</span><span class="sxs-lookup"><span data-stu-id="e768a-246">Stopping</span></span>

<span data-ttu-id="e768a-247">작업 상태에 대 한 자세한 내용은 [JobState 열거](/dotnet/api/system.management.automation.jobstate)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e768a-247">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="e768a-248">-시간 제한</span><span class="sxs-lookup"><span data-stu-id="e768a-248">-Timeout</span></span>

<span data-ttu-id="e768a-249">각 작업의 최대 대기 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-249">Specifies the maximum wait time for each job, in seconds.</span></span> <span data-ttu-id="e768a-250">기본값-1은 작업이 완료 될 때까지 cmdlet이 대기 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-250">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="e768a-251">타이밍은 명령이 아니라 명령을 제출할 때 시작 됩니다 `Wait-Job` `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="e768a-251">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="e768a-252">이 시간이 초과 되 면 작업이 계속 실행 중인 경우에도 대기가 종료 되 고 실행이 계속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-252">If this time is exceeded, the wait ends and execution continues, even if the job is still running.</span></span>
<span data-ttu-id="e768a-253">이 명령은 오류 메시지를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-253">The command does not display any error message.</span></span>

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

### <span data-ttu-id="e768a-254">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e768a-254">CommonParameters</span></span>

<span data-ttu-id="e768a-255">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e768a-255">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e768a-256">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e768a-256">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e768a-257">입력</span><span class="sxs-lookup"><span data-stu-id="e768a-257">INPUTS</span></span>

### <span data-ttu-id="e768a-258">System.web. Remorererea 작업</span><span class="sxs-lookup"><span data-stu-id="e768a-258">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="e768a-259">작업 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-259">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="e768a-260">출력</span><span class="sxs-lookup"><span data-stu-id="e768a-260">OUTPUTS</span></span>

### <span data-ttu-id="e768a-261">System.web. a p.</span><span class="sxs-lookup"><span data-stu-id="e768a-261">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="e768a-262">이 cmdlet은 종료 상태로 작업을 나타내는 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-262">This cmdlet returns job objects that represent the jobs in a terminating state.</span></span> <span data-ttu-id="e768a-263">**Timeout** 매개 변수의 값이 초과 되어 대기가 종료 되는 경우는 `Wait-Job` 개체를 반환 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-263">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="e768a-264">참고</span><span class="sxs-lookup"><span data-stu-id="e768a-264">NOTES</span></span>

<span data-ttu-id="e768a-265">기본적으로는 `Wait-Job` 작업이 다음 상태 중 하나일 때 대기를 반환 하거나 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-265">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="e768a-266">Completed</span><span class="sxs-lookup"><span data-stu-id="e768a-266">Completed</span></span>
- <span data-ttu-id="e768a-267">실패</span><span class="sxs-lookup"><span data-stu-id="e768a-267">Failed</span></span>
- <span data-ttu-id="e768a-268">중지됨</span><span class="sxs-lookup"><span data-stu-id="e768a-268">Stopped</span></span>
- <span data-ttu-id="e768a-269">일시 중단</span><span class="sxs-lookup"><span data-stu-id="e768a-269">Suspended</span></span>
- <span data-ttu-id="e768a-270">직접 이동 하 여 `Wait-Job` 일시 중단 되 고 연결 되지 않은 작업을 계속 대기 하려면 **Force** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e768a-270">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="e768a-271">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e768a-271">RELATED LINKS</span></span>

[<span data-ttu-id="e768a-272">Get-Job</span><span class="sxs-lookup"><span data-stu-id="e768a-272">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="e768a-273">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e768a-273">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="e768a-274">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="e768a-274">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="e768a-275">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="e768a-275">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="e768a-276">Start-Job</span><span class="sxs-lookup"><span data-stu-id="e768a-276">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="e768a-277">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="e768a-277">Stop-Job</span></span>](Stop-Job.md)