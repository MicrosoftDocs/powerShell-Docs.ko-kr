---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 10/25/2019
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/register-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ScheduledJob
ms.openlocfilehash: 89887474142490a71d372577576fb0059b4ff12e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213417"
---
# <span data-ttu-id="a7813-103">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a7813-103">Register-ScheduledJob</span></span>

## <span data-ttu-id="a7813-104">개요</span><span class="sxs-lookup"><span data-stu-id="a7813-104">SYNOPSIS</span></span>
<span data-ttu-id="a7813-105">예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-105">Creates a scheduled job.</span></span>

## <span data-ttu-id="a7813-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a7813-106">SYNTAX</span></span>

### <span data-ttu-id="a7813-107">ScriptBlock (기본값)</span><span class="sxs-lookup"><span data-stu-id="a7813-107">ScriptBlock (Default)</span></span>

```
Register-ScheduledJob [-ScriptBlock] <ScriptBlock> [-Name] <String>
 [-Trigger <ScheduledJobTrigger[]>] [-InitializationScript <ScriptBlock>] [-RunAs32]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-ScheduledJobOption <ScheduledJobOptions>] [-ArgumentList <Object[]>] [-MaxResultCount <Int32>]
 [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a7813-108">FilePath</span><span class="sxs-lookup"><span data-stu-id="a7813-108">FilePath</span></span>

```
Register-ScheduledJob [-FilePath] <String> [-Name] <String> [-Trigger <ScheduledJobTrigger[]>]
 [-InitializationScript <ScriptBlock>] [-RunAs32] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-ScheduledJobOption <ScheduledJobOptions>]
 [-ArgumentList <Object[]>] [-MaxResultCount <Int32>] [-RunNow] [-RunEvery <TimeSpan>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a7813-109">설명</span><span class="sxs-lookup"><span data-stu-id="a7813-109">DESCRIPTION</span></span>

<span data-ttu-id="a7813-110">`Register-ScheduledJob`Cmdlet은 로컬 컴퓨터에 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-110">The `Register-ScheduledJob` cmdlet creates scheduled jobs on the local computer.</span></span>

<span data-ttu-id="a7813-111">예약 된 작업은 일회성 또는 되풀이 일정에 따라 자동으로 시작 될 수 있는 Windows PowerShell 백그라운드 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-111">A scheduled job is a Windows PowerShell background job that can be started automatically on a one-time or recurring schedule.</span></span> <span data-ttu-id="a7813-112">예약 된 작업은 디스크에 저장 되 고 작업 스케줄러에 등록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-112">Scheduled jobs are stored on disk and registered in Task Scheduler.</span></span>
<span data-ttu-id="a7813-113">작업은 작업 스케줄러에서 관리 하거나 Windows PowerShell에서 예약 된 작업 cmdlet을 사용 하 여 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-113">The jobs can be managed in Task Scheduler or by using the Scheduled Job cmdlets in Windows PowerShell.</span></span>

<span data-ttu-id="a7813-114">예약 된 작업이 시작 되 면 예약 된 작업의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-114">When a scheduled job starts, it creates an instance of the scheduled job.</span></span> <span data-ttu-id="a7813-115">예약된 작업 인스턴스는 결과가 디스크에 저장된다는 점을 제외하고 Windows PowerShell 백그라운드 작업과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-115">Scheduled job instances are identical to Windows PowerShell background jobs, except that the results are saved on disk.</span></span> <span data-ttu-id="a7813-116">작업 cmdlet (예:, 및)을 사용 `Start-Job` `Get-Job` 하 여 `Receive-Job` 작업 인스턴스의 결과를 시작, 확인 및 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-116">Use the Job cmdlets, such as `Start-Job`, `Get-Job`, and `Receive-Job` to start, view, and get the results of the job instances.</span></span>

<span data-ttu-id="a7813-117">`Register-ScheduledJob`를 사용 하 여 새 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-117">Use `Register-ScheduledJob` to create a new scheduled job.</span></span> <span data-ttu-id="a7813-118">예약 된 작업이 실행 하는 명령을 지정 하려면 **ScriptBlock** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-118">To specify the commands that the scheduled job runs, use the **ScriptBlock** parameter.</span></span> <span data-ttu-id="a7813-119">작업이 실행 하는 스크립트를 지정 하려면 **FilePath** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-119">To specify a script that the job runs, use the **FilePath** parameter.</span></span>

<span data-ttu-id="a7813-120">Windows PowerShell-예약 된 작업은 작업 스케줄러에서 예약 된 작업에 사용 하는 것과 동일한 작업 트리거 및 작업 옵션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-120">Windows PowerShell-scheduled jobs use the same job triggers and job options that Task Scheduler uses for scheduled tasks.</span></span>

<span data-ttu-id="a7813-121">의 **Trigger** 매개 변수는 `Register-ScheduledJob` 작업을 시작 하는 하나 이상의 작업 트리거를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-121">The **Trigger** parameter of `Register-ScheduledJob` adds one or more job triggers that start the job.</span></span> <span data-ttu-id="a7813-122">**Trigger** 매개 변수는 선택 사항 이므로 예약 된 작업을 만들고, 나중에 작업 트리거를 추가 하 고, **runnow** 매개 변수를 추가 하 여 즉시 작업을 시작 하거나, cmdlet을 사용 하 여 `Start-Job` 언제 든 지 작업을 즉시 시작 하거나, instead of 트리거된 예약 된 작업을 다른 작업의 템플릿으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-122">The **Trigger** parameter is optional, so you can add triggers when you create the scheduled job, add job triggers later, add the **RunNow** parameter to start the job immediately, use the `Start-Job` cmdlet to start the job immediately at any time, or save the untriggered scheduled job as a template for other jobs.</span></span>

<span data-ttu-id="a7813-123">**Options** 매개 변수를 사용하면 예약된 작업에 대한 옵션 설정을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-123">The **Options** parameter lets you customize the options settings for the scheduled job.</span></span> <span data-ttu-id="a7813-124">**옵션** 매개 변수는 선택 사항 이므로 예약 된 작업을 만들 때 작업 옵션을 설정 하거나 언제 든 지 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-124">The **Options** parameter is optional, so you can set job options when you create the scheduled job or change them at any time.</span></span> <span data-ttu-id="a7813-125">작업 옵션 설정에 따라 예약된 작업이 실행되지 않을 수 있으므로 작업 옵션을 검토하여 신중하게 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-125">Because job option settings can prevent the scheduled job from running, review the job options and set them carefully.</span></span>

<span data-ttu-id="a7813-126">`Register-ScheduledJob` 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-126">`Register-ScheduledJob` is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="a7813-127">예약 된 작업에 대 한 자세한 내용은 **PSScheduledJob** 모듈의 about 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7813-127">For more information about Scheduled Jobs, see the About articles in the **PSScheduledJob** module.</span></span>
<span data-ttu-id="a7813-128">**PSScheduledJob** 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 [about_Scheduled_Jobs](./about/about_scheduled_jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7813-128">Import the **PSScheduledJob** module and then type: `Get-Help about_Scheduled*` or see [about_Scheduled_Jobs](./about/about_scheduled_jobs.md).</span></span>

<span data-ttu-id="a7813-129">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-129">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="a7813-130">예제</span><span class="sxs-lookup"><span data-stu-id="a7813-130">EXAMPLES</span></span>

### <span data-ttu-id="a7813-131">예제 1: 예약 된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="a7813-131">Example 1: Create a scheduled job</span></span>

<span data-ttu-id="a7813-132">이 예에서는 로컬 컴퓨터에 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-132">This example creates a scheduled job on the local computer.</span></span>

```powershell
Register-ScheduledJob -Name "Archive-Scripts" -ScriptBlock {
  Get-ChildItem $home\*.ps1 -Recurse |
    Copy-Item -Destination "\\Server\Share\PSScriptArchive"
}
```

<span data-ttu-id="a7813-133">`Register-ScheduledJob`**Name** 매개 변수를 사용 하 여 **보관-스크립트** 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-133">`Register-ScheduledJob` uses the **Name** parameter to create the **Archive-Scripts** scheduled job.</span></span>
<span data-ttu-id="a7813-134">**ScriptBlock** 매개 변수는 `Get-ChildItem` `$home` 디렉터리에서 파일을 재귀적으로 검색 하는를 실행 합니다 `.ps1` .</span><span class="sxs-lookup"><span data-stu-id="a7813-134">The **ScriptBlock** parameter runs `Get-ChildItem` that searches the `$home` directory recursively for `.ps1` files.</span></span> <span data-ttu-id="a7813-135">`Copy-Item`Cmdlet은 **Destination** 매개 변수로 지정 된 디렉터리에 파일을 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-135">The `Copy-Item` cmdlet copies the files to a directory specified by the **Destination** parameter.</span></span>

<span data-ttu-id="a7813-136">예약 된 작업은 트리거를 포함 하지 않으므로 자동으로 시작 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-136">Because the scheduled job doesn't contain a trigger, it's not started automatically.</span></span> <span data-ttu-id="a7813-137">를 사용 하 여 작업 트리거 `Add-JobTrigger` 를 추가 하거나, cmdlet을 사용 `Start-Job` 하 여 요청 시 작업을 시작 하거나, 예약 된 작업을 다른 예약 된 작업의 템플릿으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-137">You can add job triggers with `Add-JobTrigger`, use the `Start-Job` cmdlet to start the job on demand, or use the scheduled job as a template for other scheduled jobs.</span></span>

### <span data-ttu-id="a7813-138">예 2: 트리거와 사용자 지정 옵션을 사용 하 여 예약 된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="a7813-138">Example 2: Create a scheduled job with triggers and custom options</span></span>

<span data-ttu-id="a7813-139">이 예제에서는 작업 트리거와 사용자 지정 작업 옵션이 있는 예약된 작업을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-139">This example shows how to create a scheduled job that has a job trigger and custom job options.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
$path = "\\Srv01\Scripts\UpdateVersion.ps1"
Register-ScheduledJob -Name "UpdateVersion" -FilePath $path -ScheduledJobOption $O -Trigger $T
```

<span data-ttu-id="a7813-140">`$O`변수는 cmdlet이 만든 작업 옵션 개체를 저장 `New-ScheduledJobOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-140">The `$O` variable stores the job option object that the `New-ScheduledJobOption` cmdlet created.</span></span> <span data-ttu-id="a7813-141">옵션은 컴퓨터가 유휴 상태가 아닌 경우에도 예약 된 작업을 시작 하 고, 필요한 경우 작업을 실행 하기 위해 컴퓨터의 절전 모드를 해제 하 고, 작업의 여러 인스턴스를 일련의 작업으로 실행할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-141">The options start the scheduled job even if the computer isn't idle, wakes the computer to run the job, if necessary, and allows multiple instances of the job to run in a series.</span></span>

<span data-ttu-id="a7813-142">`$T`변수는 cmdlet의 결과를 저장 `New-JobTrigger` 하 여 월요일부터 오후 9:00 마다 작업을 시작 하는 작업 트리거를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-142">The `$T` variable stores the result from the `New-JobTrigger` cmdlet to create job trigger that starts a job every other Monday at 9:00 PM.</span></span>

<span data-ttu-id="a7813-143">`$path`변수는 스크립트 파일에 대 한 경로를 저장 `UpdateVersion.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-143">The `$path` variable stores the path to the `UpdateVersion.ps1` script file.</span></span>

<span data-ttu-id="a7813-144">`Register-ScheduledJob`**Name** 매개 변수를 사용 하 여 예약 된 **updateversion** 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-144">`Register-ScheduledJob` uses the **Name** paramter to create the **UpdateVersion** scheduled job.</span></span>
<span data-ttu-id="a7813-145">**FilePath** 매개 변수는를 사용 하 여 `$path` 작업이 실행 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-145">The **FilePath** parameter uses `$path` to specify the script that the job runs.</span></span> <span data-ttu-id="a7813-146">**Set-scheduledjoboption** 매개 변수는에 저장 된 작업 옵션을 사용 합니다 `$O` .</span><span class="sxs-lookup"><span data-stu-id="a7813-146">The **ScheduledJobOption** parameter uses the job options stored in `$O`.</span></span> <span data-ttu-id="a7813-147">**Trigger** 매개 변수는에 저장 된 작업 트리거를 사용 합니다 `$T` .</span><span class="sxs-lookup"><span data-stu-id="a7813-147">The **Trigger** parameter uses the job triggers stored in `$T`.</span></span>

### <span data-ttu-id="a7813-148">예 3: 해시 테이블을 사용 하 여 트리거 및 예약 된 작업 옵션 지정</span><span class="sxs-lookup"><span data-stu-id="a7813-148">Example 3: Use hash tables to specify a trigger and scheduled job options</span></span>

<span data-ttu-id="a7813-149">이 예는 예제 2의 명령과 동일한 결과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-149">This example has the same effect as the command in Example 2.</span></span> <span data-ttu-id="a7813-150">**트리거** 및 **set-scheduledjoboption** 매개 변수의 값을 지정 하는 해시 테이블을 사용 하 여 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-150">It creates a scheduled job, using hash tables to specify the values of the **Trigger** and **ScheduledJobOption** parameters.</span></span> <span data-ttu-id="a7813-151">`$O` `$T` 예 2에 정의 된 및 변수가 해시 테이블로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-151">The `$O` and `$T`variables defined in Example 2 are replaced with hash tables.</span></span>

```powershell
$T = @{
  Frequency="Weekly"
  At="9:00PM"
  DaysOfWeek="Monday"
  Interval=2
}
$O = @{
  WakeToRun=$true
  StartIfNotIdle=$false
  MultipleInstancePolicy="Queue"
}
Register-ScheduledJob -Trigger $T -ScheduledJobOption $O -Name UpdateVersion -FilePath "\\Srv01\Scripts\Update-Version.ps1"
```

### <span data-ttu-id="a7813-152">예제 4: 원격 컴퓨터에서 예약 된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="a7813-152">Example 4: Create scheduled jobs on remote computers</span></span>

<span data-ttu-id="a7813-153">이 예제에서는 **energydata.ps1** 예약 된 작업이 여러 원격 컴퓨터에 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-153">In this example, the **EnergyData** scheduled job is created on multiple remote computers.</span></span> <span data-ttu-id="a7813-154">예약 된 작업은 원시 데이터를 수집 하 여 원격 컴퓨터의 실행 중인 로그에 저장 하는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-154">The scheduled job runs a script that gathers raw data and saves it in a running log on the remote computer.</span></span>

```powershell
$Cred = Get-Credential
$O = New-ScheduledJobOption -WakeToRun -StartIfIdle -MultipleInstancePolicy Queue
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Invoke-Command -ComputerName (Get-Content Servers.txt) -Credential $Cred -ScriptBlock {
  $params = @{
      Name = "Get-EnergyData"
      FilePath = "\\Srv01\Scripts\Get-EnergyData.ps1"
      ScheduledJobOption = $using:O
      Trigger = $using:T
  }
  Register-ScheduledJob @params
}
```

<span data-ttu-id="a7813-155">`$Cred`변수는 예약 된 작업을 만들 수 있는 권한이 있는 사용자에 대해 **PSCredential** 개체에 자격 증명을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-155">The `$Cred` variable stores credentials in a **PSCredential** object for a user with permissions to create scheduled jobs.</span></span> <span data-ttu-id="a7813-156">`$O`변수는를 사용 하 여 만든 작업 옵션을 저장 `New-ScheduledJobOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-156">The `$O` variable stores the job options created with `New-ScheduledJobOption`.</span></span> <span data-ttu-id="a7813-157">`$T`변수는를 사용 하 여 만든 작업 트리거를 저장 `New-JobTrigger` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-157">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="a7813-158">`Invoke-Command`Cmdlet은 **ComputerName** 매개 변수를 사용 하 여 파일에서 서버 이름 목록을 가져옵니다 `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="a7813-158">The `Invoke-Command` cmdlet uses the **ComputerName** parameter to get a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="a7813-159">**Credential** 매개 변수는에 저장 된 자격 증명 개체를 가져옵니다 `$Cred` .</span><span class="sxs-lookup"><span data-stu-id="a7813-159">The **Credential** parameter gets the credential object stored in `$Cred`.</span></span>
<span data-ttu-id="a7813-160">**ScriptBlock** 매개 변수는 `Register-ScheduledJob` 파일의 컴퓨터에서 명령을 실행 합니다 `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="a7813-160">The **ScriptBlock** parameter runs a `Register-ScheduledJob` command on the computers in the `Servers.txt` file.</span></span>

<span data-ttu-id="a7813-161">에 대 한 매개 변수는에 `Register-ScheduledJob` 의해 정의 됩니다 `$params` .</span><span class="sxs-lookup"><span data-stu-id="a7813-161">The parameters for `Register-ScheduledJob` are defined by `$params`.</span></span> <span data-ttu-id="a7813-162">**Name** 매개 변수는 각 원격 컴퓨터에서 작업 이름을 **energydata.ps1** 로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-162">The **Name** parameters specifies the job is named **Get-EnergyData** on each remote computer.</span></span> <span data-ttu-id="a7813-163">**FilePath** 는 스크립트의 위치를 제공 합니다 `EnergyData.ps1` .</span><span class="sxs-lookup"><span data-stu-id="a7813-163">**FilePath** provides the location of the `EnergyData.ps1` script.</span></span> <span data-ttu-id="a7813-164">스크립트는 모든 참여 컴퓨터에서 사용할 수 있는 파일 서버에 있습니다. 작업은의 작업 트리거와의 작업 옵션에 지정 된 일정에 따라 실행 됩니다 `$T` `$O` .</span><span class="sxs-lookup"><span data-stu-id="a7813-164">The script is located on a file server that is available to all participating computers.The job runs on the schedule specified by the job triggers in `$T` and the job options in `$O`.</span></span>

<span data-ttu-id="a7813-165">이 `Register-ScheduledJob @params` 명령은 스크립트 블록에서 매개 변수를 사용 하 여 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-165">The `Register-ScheduledJob @params` command creates the scheduled job with the parameters from the script block.</span></span>

### <span data-ttu-id="a7813-166">예 5: 원격 컴퓨터에서 스크립트를 실행 하는 예약 된 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="a7813-166">Example 5: Create a scheduled job that runs a script on remote computers</span></span>

<span data-ttu-id="a7813-167">이 예에서는 로컬 컴퓨터에 **CollectEnergyData** 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-167">This example creates the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="a7813-168">작업은 여러 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-168">The job runs on multiple remote computers.</span></span>

```powershell
$Admin = Get-Credential
$T = New-JobTrigger -Weekly -At "9:00 PM" -DaysOfWeek Monday -WeeksInterval 2
Register-ScheduledJob -Name "CollectEnergyData" -Trigger $T -MaxResultCount 99 -ScriptBlock {
  $params = @{
    AsJob = $true
    ComputerName = (Get-Content Servers.txt)
    FilePath = '\\Srv01\Scripts\Get-EnergyData.ps1'
    Credential = $using:Admin
    Authentication = 'CredSSP'
  }
  Invoke-Command @params
}
```

<span data-ttu-id="a7813-169">`$Admin`변수는 **PSCredential** 개체에서 명령을 실행할 수 있는 권한이 있는 사용자에 대 한 자격 증명을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-169">The `$Admin` variable stores credentials for a user with permissions to run the commands in a **PSCredential** object.</span></span> <span data-ttu-id="a7813-170">`$T`변수는를 사용 하 여 만든 작업 트리거를 저장 `New-JobTrigger` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-170">The `$T` variable stores the job triggers created with `New-JobTrigger`.</span></span>

<span data-ttu-id="a7813-171">이 `Register-ScheduledJob` cmdlet은 **Name** 매개 변수를 사용 하 여 로컬 컴퓨터에서 **CollectEnergyData** 예약 된 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-171">The `Register-ScheduledJob` cmdlet uses the **Name** parameter to create the **CollectEnergyData** scheduled job on the local computer.</span></span> <span data-ttu-id="a7813-172">**Trigger** 매개 변수는의 작업 트리거를 지정 하 `$T` 고 **MaxResultCount** 매개 변수는 저장 된 결과의 수를 99로 늘립니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-172">The **Trigger** parameter specifies the job triggers in `$T` and the **MaxResultCount** parameter increases the number of saved results to 99.</span></span>

<span data-ttu-id="a7813-173">**ScriptBlock** 매개 변수는 `Invoke-Command` 를 사용 하 여 매개 변수를 정의 합니다 `$params` .</span><span class="sxs-lookup"><span data-stu-id="a7813-173">The **ScriptBlock** parameter defines the `Invoke-Command` parameters with `$params`.</span></span> <span data-ttu-id="a7813-174">**AsJob** 매개 변수는 `Energydata.ps1` 원격 컴퓨터에서 스크립트가 실행 되는 경우에도 로컬 컴퓨터에 백그라운드 작업 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-174">The **AsJob** parameter creates the background job object on the local computer, even though the `Energydata.ps1` script runs on the remote computers.</span></span> <span data-ttu-id="a7813-175">**ComputerName** 매개 변수는 파일에서 서버 이름 목록을 가져옵니다 `Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="a7813-175">The **ComputerName** parameter gets a list of server names from the `Servers.txt` file.</span></span> <span data-ttu-id="a7813-176">**Credential** 매개 변수는 원격 컴퓨터에서 스크립트를 실행할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-176">The **Credential** parameter specifies a user account that has permission to run scripts on the remote computers.</span></span> <span data-ttu-id="a7813-177">그리고 **인증** 매개 변수는 위임 된 자격 증명을 허용 하는 **CredSSP** 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-177">And, the **Authentication** parameter specifies a value of **CredSSP** to allow delegated credentials.</span></span>

<span data-ttu-id="a7813-178">는 `Invoke-Command @params` 스크립트 블록에서 매개 변수를 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-178">The `Invoke-Command @params` runs the command with the parameters from the script block.</span></span>

## <span data-ttu-id="a7813-179">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a7813-179">PARAMETERS</span></span>

### <span data-ttu-id="a7813-180">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="a7813-180">-ArgumentList</span></span>

<span data-ttu-id="a7813-181">**FilePath** 매개 변수에 지정된 스크립트의 매개 변수 값이나 **ScriptBlock** 매개 변수에 지정된 명령의 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-181">Specifies values for the parameters of the script that is specified by the **FilePath** parameter or for the command that is specified by the **ScriptBlock** parameter.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-182">-인증</span><span class="sxs-lookup"><span data-stu-id="a7813-182">-Authentication</span></span>

<span data-ttu-id="a7813-183">사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-183">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="a7813-184">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-184">The default value is Default.</span></span>

<span data-ttu-id="a7813-185">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-185">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a7813-186">기본값</span><span class="sxs-lookup"><span data-stu-id="a7813-186">Default</span></span>
- <span data-ttu-id="a7813-187">Basic</span><span class="sxs-lookup"><span data-stu-id="a7813-187">Basic</span></span>
- <span data-ttu-id="a7813-188">Credssp</span><span class="sxs-lookup"><span data-stu-id="a7813-188">Credssp</span></span>
- <span data-ttu-id="a7813-189">다이제스트</span><span class="sxs-lookup"><span data-stu-id="a7813-189">Digest</span></span>
- <span data-ttu-id="a7813-190">Kerberos</span><span class="sxs-lookup"><span data-stu-id="a7813-190">Kerberos</span></span>
- <span data-ttu-id="a7813-191">Negotiate</span><span class="sxs-lookup"><span data-stu-id="a7813-191">Negotiate</span></span>
- <span data-ttu-id="a7813-192">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="a7813-192">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="a7813-193">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a7813-193">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="a7813-194">사용자 자격 증명이 인증할 원격 컴퓨터로 전달되는 CredSSP(Credential Security Service Provider) 인증은 원격 네트워크 공유 액세스 등 두 개 이상의 리소스에서 인증이 필요한 명령에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-194">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="a7813-195">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-195">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="a7813-196">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-196">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: (All)
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-197">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a7813-197">-Confirm</span></span>

<span data-ttu-id="a7813-198">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-198">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a7813-199">-Credential</span><span class="sxs-lookup"><span data-stu-id="a7813-199">-Credential</span></span>

<span data-ttu-id="a7813-200">예약된 작업을 실행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-200">Specifies a user account that has permission to run the scheduled job.</span></span> <span data-ttu-id="a7813-201">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-201">The default is the current user.</span></span>

<span data-ttu-id="a7813-202">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나, cmdlet의 개체와 같은 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="a7813-202">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object, such as one from the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="a7813-203">사용자 이름만 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-203">If you enter only a user name, you're prompted for a password.</span></span>

<span data-ttu-id="a7813-204">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-204">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="a7813-205">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="a7813-205">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-206">-FilePath</span><span class="sxs-lookup"><span data-stu-id="a7813-206">-FilePath</span></span>

<span data-ttu-id="a7813-207">예약된 작업이 실행하는 스크립트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-207">Specifies a script that the scheduled job runs.</span></span> <span data-ttu-id="a7813-208">로컬 컴퓨터에 있는 파일의 경로를 입력 `.ps1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-208">Enter the path to a `.ps1` file on the local computer.</span></span> <span data-ttu-id="a7813-209">스크립트 매개 변수의 기본값을 지정하려면 **ArgumentList** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-209">To specify default values for the script parameters, use the **ArgumentList** parameter.</span></span>
<span data-ttu-id="a7813-210">모든 `Register-ScheduledJob` 명령은 **ScriptBlock** 또는 **FilePath** 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-210">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-211">-또한 initializationscript</span><span class="sxs-lookup"><span data-stu-id="a7813-211">-InitializationScript</span></span>

<span data-ttu-id="a7813-212">Windows PowerShell 스크립트에 대 한 정규화 된 경로를 지정 합니다 ( `.ps1` ).</span><span class="sxs-lookup"><span data-stu-id="a7813-212">Specifies the fully qualified path to a Windows PowerShell script (`.ps1`).</span></span> <span data-ttu-id="a7813-213">초기화 스크립트는 백그라운드 작업에 대해 만들어진 세션에서 **ScriptBlock** 매개 변수에 지정된 명령이나 **FilePath** 매개 변수에 지정된 스크립트보다 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-213">The initialization script runs in the session that is created for the background job before the commands that are specified by the **ScriptBlock** parameter or the script that is specified by the **FilePath** parameter.</span></span> <span data-ttu-id="a7813-214">초기화 스크립트를 사용하여 파일, 함수 또는 별칭 추가, 디렉터리 만들기, 필수 조건 확인 등 세션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-214">You can use the initialization script to configure the session, such as adding files, functions, or aliases, creating directories, or checking for prerequisites.</span></span>

<span data-ttu-id="a7813-215">주요 작업 명령을 실행하는 스크립트를 지정하려면 **FilePath** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-215">To specify a script that runs the primary job commands, use the **FilePath** parameter.</span></span>

<span data-ttu-id="a7813-216">초기화 스크립트에서 종료 되지 않는 오류가 발생 해도 오류가 발생 하면 예약 된 작업의 현재 인스턴스가 실행 되지 않으며 상태는 **실패** 입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-216">If the initialization script generates an error, even a non-terminating error, the current instance of the scheduled job doesn't run and its status is **Failed** .</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-217">-MaxResultCount</span><span class="sxs-lookup"><span data-stu-id="a7813-217">-MaxResultCount</span></span>

<span data-ttu-id="a7813-218">예약된 작업에 대해 유지 관리할 작업 결과 항목 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-218">Specifies how many job result entries are maintained for the scheduled job.</span></span> <span data-ttu-id="a7813-219">기본값은 32입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-219">The default value is 32.</span></span>

<span data-ttu-id="a7813-220">Windows PowerShell은 트리거된 각 예약된 작업 인스턴스의 실행 기록과 결과를 디스크에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-220">Windows PowerShell saves the execution history and results of each triggered instance of the scheduled job on disk.</span></span> <span data-ttu-id="a7813-221">이 매개 변수 값은 이 예약된 작업에 대해 저장되는 작업 인스턴스 결과 수를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-221">The value of this parameter determines the number of job instance results that are saved for this scheduled job.</span></span> <span data-ttu-id="a7813-222">작업 인스턴스 결과 수가 이 값을 초과할 경우 Windows PowerShell은 가장 오래된 작업 인스턴스 결과를 삭제하여 최신 작업 인스턴스 결과를 저장할 공간을 확보합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-222">When the number of job instance results exceeds this value, Windows PowerShell deletes the results of the oldest job instance to make room for the results of the newest job instance.</span></span>

<span data-ttu-id="a7813-223">작업 실행 기록과 작업 결과는 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span><span class="sxs-lookup"><span data-stu-id="a7813-223">The job execution history and job results are saved in the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs\<JobName>\Output\<Timestamp>`</span></span>
<span data-ttu-id="a7813-224">작업이 생성 된 컴퓨터의 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-224">directories on the computer on which the job is created.</span></span> <span data-ttu-id="a7813-225">실행 기록을 보려면 cmdlet을 사용 합니다 `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="a7813-225">To see the execution history, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="a7813-226">작업 결과를 가져오려면 cmdlet을 사용 합니다 `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="a7813-226">To get the job results, use the `Receive-Job` cmdlet.</span></span>

<span data-ttu-id="a7813-227">**MaxResultCount** 매개 변수는 예약된 작업의 ExecutionHistoryLength 속성 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-227">The **MaxResultCount** parameter sets the value of the ExecutionHistoryLength property of the scheduled job.</span></span>

<span data-ttu-id="a7813-228">현재 실행 기록과 작업 결과를 삭제 하려면 cmdlet의 **ClearExecutionHistory** 매개 변수를 사용 합니다 `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="a7813-228">To delete the current execution history and job results, use the **ClearExecutionHistory** parameter of the `Set-ScheduledJob` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 32
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-229">-Name</span><span class="sxs-lookup"><span data-stu-id="a7813-229">-Name</span></span>

<span data-ttu-id="a7813-230">예약된 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-230">Specifies a name for the scheduled job.</span></span> <span data-ttu-id="a7813-231">이 이름은 시작된 모든 예약된 작업 인스턴스에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-231">The name is also used for all started instances of the scheduled job.</span></span> <span data-ttu-id="a7813-232">이름은 컴퓨터에서 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-232">The name must be unique on the computer.</span></span> <span data-ttu-id="a7813-233">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-233">This parameter is required.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-234">-체제가 있어도 runas32</span><span class="sxs-lookup"><span data-stu-id="a7813-234">-RunAs32</span></span>

<span data-ttu-id="a7813-235">32비트 프로세스로 예약된 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-235">Runs the scheduled job in a 32-bit process.</span></span>

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

### <span data-ttu-id="a7813-236">-RunEvery</span><span class="sxs-lookup"><span data-stu-id="a7813-236">-RunEvery</span></span>

<span data-ttu-id="a7813-237">작업 실행 빈도를 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-237">Used to specify how often to run the job.</span></span> <span data-ttu-id="a7813-238">예를 들어이 옵션을 사용 하 여 15 분 마다 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-238">For example, use this option to run a job every 15 minutes.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-239">-RunNow</span><span class="sxs-lookup"><span data-stu-id="a7813-239">-RunNow</span></span>

<span data-ttu-id="a7813-240">Cmdlet이 실행 되는 즉시 작업을 시작 `Register-ScheduledJob` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-240">Starts a job immediately, as soon as the `Register-ScheduledJob` cmdlet is run.</span></span> <span data-ttu-id="a7813-241">이 매개 변수는 등록 후 즉시 Windows PowerShell 스크립트를 실행 하기 위해 작업 스케줄러를 트리거할 필요가 없으며 사용자가 시작 날짜 및 시간을 지정 하는 트리거를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-241">This parameter eliminates the need to trigger Task Scheduler to run a Windows PowerShell script immediately after registration, and doesn't require users to create a trigger that specifies a starting date and time.</span></span>

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

### <span data-ttu-id="a7813-242">-Set-scheduledjoboption</span><span class="sxs-lookup"><span data-stu-id="a7813-242">-ScheduledJobOption</span></span>

<span data-ttu-id="a7813-243">예약된 작업에 대한 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-243">Sets options for the scheduled job.</span></span> <span data-ttu-id="a7813-244">Cmdlet을 사용 하 여 만든 개체 또는 해시 테이블 값과 같은 **ScheduledJobOptions** 개체를 입력 `New-ScheduledJobOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-244">Enter a **ScheduledJobOptions** object, such as one that you create by using the `New-ScheduledJobOption` cmdlet, or a hash table value.</span></span>

<span data-ttu-id="a7813-245">예약 작업을 등록할 때 예약 된 작업에 대 한 옵션을 설정 하거나 또는 cmdlet을 사용 하 여 옵션을 변경할 수 있습니다 `Set-ScheduledJobOption` `Set-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="a7813-245">You can set options for a scheduled job when you register the schedule job or use the `Set-ScheduledJobOption` or `Set-ScheduledJob` cmdlets to change the options.</span></span>

<span data-ttu-id="a7813-246">많은 옵션과 해당 기본값은 예약된 작업의 실행 여부와 시기를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-246">Many of the options and their default values determine whether and when a scheduled job runs.</span></span> <span data-ttu-id="a7813-247">작업을 예약하기 전에 이러한 옵션을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-247">Be sure to review these options before scheduling a job.</span></span> <span data-ttu-id="a7813-248">기본 값을 포함 하 여 예약 된 작업 옵션에 대 한 설명은를 참조 하십시오 `New-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="a7813-248">For a description of the scheduled job options, including the default values, see `New-ScheduledJobOption`.</span></span>

<span data-ttu-id="a7813-249">해시 테이블을 제출하려면 다음 키를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-249">To submit a hash table, use the following keys.</span></span> <span data-ttu-id="a7813-250">다음 해시 테이블에 키와 해당 기본값이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-250">In the following hash table, the keys are shown with their default values.</span></span>

`@{StartIfOnBattery=$False; StopIfGoingOnBattery=$True; WakeToRun=$False; StartIfNotIdle=$False; IdleDuration="00:10:00"; IdleTimeout="01:00:00"; StopIfGoingOffIdle=$True; RestartOnIdleResume=$False; ShowInTaskScheduler=$True; RunElevated=$False; RunWithoutNetwork=$False; DoNotAllowDemandStart=$False; MultipleInstancePolicy="IgnoreNew"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-251">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="a7813-251">-ScriptBlock</span></span>

<span data-ttu-id="a7813-252">예약된 작업이 실행하는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-252">Specifies the commands that the scheduled job runs.</span></span> <span data-ttu-id="a7813-253">명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-253">Enclose the commands in curly braces (`{}`) to create a script block.</span></span> <span data-ttu-id="a7813-254">명령 매개 변수의 기본값을 지정하려면 **ArgumentList** 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-254">To specify default values for command parameters, use the **ArgumentList** parameter.</span></span>

<span data-ttu-id="a7813-255">모든 `Register-ScheduledJob` 명령은 **ScriptBlock** 또는 **FilePath** 매개 변수를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-255">Every `Register-ScheduledJob` command must use either the **ScriptBlock** or **FilePath** parameters.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-256">-트리거</span><span class="sxs-lookup"><span data-stu-id="a7813-256">-Trigger</span></span>

<span data-ttu-id="a7813-257">예약된 작업의 트리거를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-257">Specifies the triggers for the scheduled job.</span></span> <span data-ttu-id="a7813-258">Cmdlet이 반환 하 **ScheduledJobTrigger** 는 개체 `New-JobTrigger` 또는 작업 트리거 키 및 값의 해시 테이블 같은 ScheduledJobTrigger 개체를 하나 이상 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-258">Enter one or more **ScheduledJobTrigger** objects, such as the objects that the `New-JobTrigger` cmdlet returns, or a hash table of job trigger keys and values.</span></span>

<span data-ttu-id="a7813-259">작업 트리거는 일정 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-259">A job trigger starts the schedule job.</span></span> <span data-ttu-id="a7813-260">트리거는 사용자가 로그온하거나 Windows가 시작되는 경우와 같은 이벤트나 일회성 또는 되풀이 일정을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-260">The trigger can specify a one-time or recurring scheduled or an event, such as when a user logs on or Windows starts.</span></span>

<span data-ttu-id="a7813-261">**Trigger** 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-261">The **Trigger** parameter is optional.</span></span> <span data-ttu-id="a7813-262">예약 된 작업을 만들 때 트리거를 추가 `Add-JobTrigger` 하거나,, `Set-JobTrigger` 또는 cmdlet을 사용 하 여 `Set-ScheduledJob` 나중에 작업 트리거를 추가 하거나 변경 하거나, cmdlet을 사용 하 여 `Start-Job` 예약 된 작업을 즉시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-262">You can add a trigger when you create the scheduled job, use the `Add-JobTrigger`, `Set-JobTrigger`, or `Set-ScheduledJob` cmdlets to add or change job triggers later, or use the `Start-Job` cmdlet to start the scheduled job immediately.</span></span> <span data-ttu-id="a7813-263">템플릿으로 사용되는 트리거 없는 예약된 작업을 만들어 유지 관리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-263">You can also create and maintain a scheduled job without a trigger that is used as a template.</span></span>

<span data-ttu-id="a7813-264">해시 테이블을 제출 하려면 다음 키를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-264">To submit a hash table, use the following keys:</span></span>

- <span data-ttu-id="a7813-265">**빈도** : 매일, 매주, Atstartup, atstartup</span><span class="sxs-lookup"><span data-stu-id="a7813-265">**Frequency** : Daily, Weekly, AtStartup, AtLogon</span></span>
- <span data-ttu-id="a7813-266">**At** : 모든 유효한 시간 문자열</span><span class="sxs-lookup"><span data-stu-id="a7813-266">**At** : Any valid time string</span></span>
- <span data-ttu-id="a7813-267">**DaysOfWeek** -요일 이름 조합</span><span class="sxs-lookup"><span data-stu-id="a7813-267">**DaysOfWeek** - Any combination of day names</span></span>
- <span data-ttu-id="a7813-268">**Interval** -유효한 모든 빈도 간격</span><span class="sxs-lookup"><span data-stu-id="a7813-268">**Interval** - Any valid frequency interval</span></span>
- <span data-ttu-id="a7813-269">**RandomDelay** : 모든 유효한 timespan 문자열</span><span class="sxs-lookup"><span data-stu-id="a7813-269">**RandomDelay** : Any valid timespan string</span></span>
- <span data-ttu-id="a7813-270">**사용자** : 모든 유효한 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-270">**User** : Any valid user.</span></span> <span data-ttu-id="a7813-271">AtLogon 빈도 값에만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-271">Used only with the AtLogon frequency value</span></span>

<span data-ttu-id="a7813-272">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="a7813-272">For example:</span></span>

`@{Frequency="Once"; At="3am"; DaysOfWeek="Monday", "Wednesday"; Interval=2; RandomDelay="30minutes"; User="Domain1\User01"}`

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a7813-273">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a7813-273">-WhatIf</span></span>

<span data-ttu-id="a7813-274">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-274">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a7813-275">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-275">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="a7813-276">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a7813-276">CommonParameters</span></span>

<span data-ttu-id="a7813-277">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a7813-277">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a7813-278">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7813-278">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a7813-279">입력</span><span class="sxs-lookup"><span data-stu-id="a7813-279">INPUTS</span></span>

### <span data-ttu-id="a7813-280">없음</span><span class="sxs-lookup"><span data-stu-id="a7813-280">None</span></span>

<span data-ttu-id="a7813-281">파이프라인에서이 cmdlet에 대 한 입력을 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-281">You can't send input down the pipeline to this cmdlet.</span></span>

## <span data-ttu-id="a7813-282">출력</span><span class="sxs-lookup"><span data-stu-id="a7813-282">OUTPUTS</span></span>

### <span data-ttu-id="a7813-283">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="a7813-283">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>

## <span data-ttu-id="a7813-284">참고</span><span class="sxs-lookup"><span data-stu-id="a7813-284">NOTES</span></span>

<span data-ttu-id="a7813-285">각 예약 된 작업은 로컬 컴퓨터에 있는 디렉터리의 하위 디렉터리에 저장 됩니다 `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` .</span><span class="sxs-lookup"><span data-stu-id="a7813-285">Each scheduled job is saved in a subdirectory of the `$home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs` directory on the local computer.</span></span>
<span data-ttu-id="a7813-286">하위 디렉터리는 예약 된 작업에 대해 이름이 지정 되며 예약 된 작업에 대 한 XML 파일과 실행 기록 레코드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-286">The subdirectory is named for the scheduled job and contains an XML file for the scheduled job and records of its execution history.</span></span> <span data-ttu-id="a7813-287">디스크의 예약 된 작업에 대 한 자세한 내용은 [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7813-287">For more information about scheduled jobs on disk, see [about_Scheduled_Jobs_Advanced](./about/about_scheduled_jobs_advanced.md).</span></span>

<span data-ttu-id="a7813-288">Windows PowerShell에서 만든 예약 된 작업은 작업 스케줄러 폴더의 작업 스케줄러에 나타납니다 `Library\Microsoft\Windows\PowerShell\ScheduledJobs` .</span><span class="sxs-lookup"><span data-stu-id="a7813-288">Scheduled jobs that you create in Windows PowerShell appear in Task Scheduler in the Task Scheduler `Library\Microsoft\Windows\PowerShell\ScheduledJobs` folder.</span></span> <span data-ttu-id="a7813-289">작업 스케줄러를 사용하여 예약된 작업을 보고 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-289">You can use Task Scheduler to view and edit the scheduled job.</span></span>

<span data-ttu-id="a7813-290">작업 스케줄러, **schtasks.exe** 명령줄 도구 및 작업 스케줄러 cmdlet을 사용 하 여 예약 된 작업 cmdlet으로 만든 예약 된 작업을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-290">You can use Task Scheduler, the **schtasks.exe** command-line tool, and the Task Scheduler cmdlets to manage scheduled jobs that you create with the Scheduled Job cmdlets.</span></span> <span data-ttu-id="a7813-291">그러나 작업 스케줄러에서 만든 작업은 예약 된 작업 cmdlet을 사용 하 여 관리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-291">However, you can't use the Scheduled Job cmdlets to manage tasks that you create in Task Scheduler.</span></span>

<span data-ttu-id="a7813-292">예약된 작업 명령이 실패할 경우 Windows PowerShell에서 오류 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-292">If a scheduled job command fails, Windows PowerShell returns an error message.</span></span> <span data-ttu-id="a7813-293">그러나 작업 스케줄러 실행 하려고 할 때 작업이 실패 하면 Windows PowerShell에서 오류를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-293">However, if the job fails when Task Scheduler tries to run it, the error isn't available to Windows PowerShell.</span></span>

<span data-ttu-id="a7813-294">예약 된 작업이 실행 되지 않으면 다음 방법을 사용 하 여 이유를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-294">If a scheduled job doesn't run, use the following methods to find the reason:</span></span>

- <span data-ttu-id="a7813-295">작업 트리거가 제대로 설정 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-295">Verify that the job trigger is set properly.</span></span>
  - <span data-ttu-id="a7813-296">작업 옵션에 설정 된 조건이 충족 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-296">Verify that the conditions set in the job options are satisfied.</span></span>
- <span data-ttu-id="a7813-297">작업이 실행 되는 사용자 계정에 작업의 명령 또는 스크립트를 실행할 수 있는 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-297">Verify that the user account under which the job runs has permission to run the commands or scripts in the job.</span></span>
- <span data-ttu-id="a7813-298">작업 스케줄러 기록에서 오류를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7813-298">Check the Task Scheduler history for errors.</span></span>
- <span data-ttu-id="a7813-299">작업 스케줄러 이벤트 로그에서 오류를 확인 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a7813-299">Check the Task Scheduler event log for errors.</span></span>

<span data-ttu-id="a7813-300">자세한 내용은 [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7813-300">For more information, see [about_Scheduled_Jobs_Troubleshooting](./about/about_scheduled_jobs_troubleshooting.md).</span></span>

## <span data-ttu-id="a7813-301">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a7813-301">RELATED LINKS</span></span>

[<span data-ttu-id="a7813-302">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a7813-302">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="a7813-303">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a7813-303">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="a7813-304">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a7813-304">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="a7813-305">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a7813-305">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="a7813-306">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a7813-306">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="a7813-307">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a7813-307">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="a7813-308">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a7813-308">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="a7813-309">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a7813-309">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="a7813-310">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a7813-310">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="a7813-311">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a7813-311">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="a7813-312">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a7813-312">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="a7813-313">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a7813-313">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="a7813-314">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="a7813-314">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="a7813-315">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a7813-315">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="a7813-316">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="a7813-316">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="a7813-317">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="a7813-317">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
