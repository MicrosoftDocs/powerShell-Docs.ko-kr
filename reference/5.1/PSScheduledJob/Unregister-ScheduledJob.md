---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/unregister-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-ScheduledJob
ms.openlocfilehash: 0c0b55513bcfdcebdcd5d8a6f17968a4a45e2839
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213370"
---
# <span data-ttu-id="6fbc0-103">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6fbc0-103">Unregister-ScheduledJob</span></span>

## <span data-ttu-id="6fbc0-104">개요</span><span class="sxs-lookup"><span data-stu-id="6fbc0-104">SYNOPSIS</span></span>
<span data-ttu-id="6fbc0-105">로컬 컴퓨터에서 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-105">Deletes scheduled jobs on the local computer.</span></span>

## <span data-ttu-id="6fbc0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6fbc0-106">SYNTAX</span></span>

### <span data-ttu-id="6fbc0-107">정의 (기본값)</span><span class="sxs-lookup"><span data-stu-id="6fbc0-107">Definition (Default)</span></span>

```
Unregister-ScheduledJob [-InputObject] <ScheduledJobDefinition[]> [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="6fbc0-108">인</span><span class="sxs-lookup"><span data-stu-id="6fbc0-108">DefinitionId</span></span>

```
Unregister-ScheduledJob [-Id] <Int32[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6fbc0-109">Build.definitionname</span><span class="sxs-lookup"><span data-stu-id="6fbc0-109">DefinitionName</span></span>

```
Unregister-ScheduledJob [-Name] <String[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="6fbc0-110">설명</span><span class="sxs-lookup"><span data-stu-id="6fbc0-110">DESCRIPTION</span></span>
<span data-ttu-id="6fbc0-111">**Unregister-ScheduledJob** cmdlet은 로컬 컴퓨터에서 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-111">The **Unregister-ScheduledJob** cmdlet deletes scheduled jobs from the local computer.</span></span>

<span data-ttu-id="6fbc0-112">예약 된 작업을 삭제 하거나 등록 취소 하면 **set-scheduledjob** 는 예약 된 작업 ($home \appdata\local\microsoft\windows\powershell\scheduledjobs 디렉터리)에 대 한 디렉터리를 삭제 합니다. 여기에는 예약 된 작업, 작업 실행 기록 및 모든 작업 결과를 정의 하는 XML 파일이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-112">When it deletes or unregisters a scheduled job, **Unregister-ScheduledJob** deletes the directory for the scheduled job (in the $home\AppData\Local\Microsoft\Windows\PowerShell\ScheduledJobs directory), which contains the XML file that defines the scheduled job, the job execution history, and all job results.</span></span>
<span data-ttu-id="6fbc0-113">이 작업은 작업 스케줄러에서 작업도 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-113">This action also deletes the job from Task Scheduler.</span></span>

<span data-ttu-id="6fbc0-114">**Set-scheduledjob** 는 Register-ScheduledJob cmdlet을 사용 하 여 만든 예약 작업만 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-114">**Unregister-ScheduledJob** deletes only the scheduled jobs that are created by using the Register-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="6fbc0-115">작업 스케줄러에서 만들어진 예약된 작업은 삭제하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-115">It does not delete scheduled jobs that are created in Task Scheduler.</span></span>

<span data-ttu-id="6fbc0-116">**Set-scheduledjob** 의 매개 변수를 사용 하 여 ID 또는 이름으로 예약 된 작업을 삭제 하거나 Get-ScheduledJob에서 **set-scheduledjob** 로의 파이프 예약 된 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-116">You can use the parameters of **Unregister-ScheduledJob** to delete scheduled jobs by ID or name, or pipe scheduled jobs from Get-ScheduledJob to **Unregister-ScheduledJob** .</span></span>

<span data-ttu-id="6fbc0-117">**Set-scheduledjob** 는 Windows PowerShell에 포함 된 PSScheduledJob 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-117">**Unregister-ScheduledJob** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="6fbc0-118">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-118">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="6fbc0-119">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-119">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="6fbc0-120">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-120">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="6fbc0-121">예제</span><span class="sxs-lookup"><span data-stu-id="6fbc0-121">EXAMPLES</span></span>

### <span data-ttu-id="6fbc0-122">예제 1: 예약 된 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="6fbc0-122">Example 1: Delete a scheduled job</span></span>

```
PS C:\> Unregister-ScheduledJob TestJob
```

<span data-ttu-id="6fbc0-123">이 명령은 로컬 컴퓨터에 있는 TestJob 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-123">This command deletes the TestJob scheduled job on the local computer.</span></span>

### <span data-ttu-id="6fbc0-124">예 2: 모든 예약 된 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="6fbc0-124">Example 2: Delete all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Unregister-ScheduledJob -Force
PS C:\> Unregister-ScheduledJob -Name "*" -Force
```

<span data-ttu-id="6fbc0-125">이 예제에서는 로컬 컴퓨터에서 모든 예약 된 작업을 삭제 하는 두 가지 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-125">This example shows two different commands that delete all scheduled jobs on the local computer.</span></span>

<span data-ttu-id="6fbc0-126">첫 번째 명령은 Get-ScheduledJob cmdlet을 사용 하 여 로컬 컴퓨터에서 모든 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-126">The first command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="6fbc0-127">파이프라인 연산자(|)가 예약된 작업을 **Unregister-ScheduleJob** 으로 보내면 이 cmdlet이 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-127">A pipeline operator (|) sends the scheduled jobs to **Unregister-ScheduleJob** , which deletes them.</span></span>

<span data-ttu-id="6fbc0-128">두 번째 명령은 *Unregister-ScheduledJob* 의 **Name** 매개 변수를 모두(\*) 값으로 사용하여 모든 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-128">The second command uses the *Name* parameter of **Unregister-ScheduledJob** with a value of all (\*) to delete all scheduled jobs.</span></span>

<span data-ttu-id="6fbc0-129">두 명령은 작업 인스턴스가 실행 중인 경우에도 예약된 작업을 삭제하는 *Force* 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-129">Both commands use the *Force* parameter, which deletes a scheduled job even if an instance of the job is running.</span></span>

### <span data-ttu-id="6fbc0-130">예 3: 원격 컴퓨터에서 예약 된 작업 삭제</span><span class="sxs-lookup"><span data-stu-id="6fbc0-130">Example 3: Delete a scheduled job on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" { Unregister-ScheduledJob -Name "Test*"}
```

<span data-ttu-id="6fbc0-131">이 명령은 이름이 Server01 원격 컴퓨터의 테스트로 시작 하는 예약 된 작업을 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-131">This command deletes scheduled jobs with names that begin with Test on the Server01 remote computer.</span></span>
<span data-ttu-id="6fbc0-132">이 명령은 Invoke-Command cmdlet을 사용 하 여 Server02 컴퓨터에서 **set-scheduledjob** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-132">The command uses the Invoke-Command cmdlet to run the **Unregister-ScheduledJob** command on the Server02 computer.</span></span>

## <span data-ttu-id="6fbc0-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="6fbc0-133">PARAMETERS</span></span>

### <span data-ttu-id="6fbc0-134">-Force</span><span class="sxs-lookup"><span data-stu-id="6fbc0-134">-Force</span></span>
<span data-ttu-id="6fbc0-135">작업 인스턴스가 실행 중인 경우에도 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-135">Deletes the scheduled job even if an instance of the job is running.</span></span>
<span data-ttu-id="6fbc0-136">기본적으로 **Unregister-ScheduledJob** 은 실행 중인 작업을 중단하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-136">By default, **Unregister-ScheduledJob** does not interrupt running jobs.</span></span>

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

### <span data-ttu-id="6fbc0-137">-Id</span><span class="sxs-lookup"><span data-stu-id="6fbc0-137">-Id</span></span>
<span data-ttu-id="6fbc0-138">지정한 ID 번호(ID)를 가진 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-138">Deletes the scheduled jobs with the specified identification numbers (ID).</span></span>
<span data-ttu-id="6fbc0-139">컴퓨터에 있는 예약된 작업의 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-139">Enter the IDs of scheduled jobs on the computer.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fbc0-140">-InputObject</span><span class="sxs-lookup"><span data-stu-id="6fbc0-140">-InputObject</span></span>
<span data-ttu-id="6fbc0-141">예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-141">Specifies a scheduled job.</span></span>
<span data-ttu-id="6fbc0-142">**Set-scheduledjob** 개체가 포함 된 변수를 입력 하거나 **set-scheduledjob** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-142">Enter a variable that contains **ScheduledJob** objects or type a command or expression that gets **ScheduledJob** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="6fbc0-143">**Set-scheduledjob** 개체를 파이프 되지 않은 **jobtrigger** 로 파이프 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-143">You can also pipe **ScheduledJob** objects to **Unregister-JobTrigger** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition[]
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="6fbc0-144">-Name</span><span class="sxs-lookup"><span data-stu-id="6fbc0-144">-Name</span></span>
<span data-ttu-id="6fbc0-145">지정한 이름을 가진 예약된 작업을 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-145">Deletes the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="6fbc0-146">컴퓨터에 있는 하나 이상 예약된 작업의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-146">Enter the names of one or more scheduled jobs on the computer.</span></span>
<span data-ttu-id="6fbc0-147">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-147">Wildcards are supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6fbc0-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6fbc0-148">-Confirm</span></span>
<span data-ttu-id="6fbc0-149">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="6fbc0-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6fbc0-150">-WhatIf</span></span>
<span data-ttu-id="6fbc0-151">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6fbc0-152">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="6fbc0-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6fbc0-153">CommonParameters</span></span>
<span data-ttu-id="6fbc0-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6fbc0-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6fbc0-156">입력</span><span class="sxs-lookup"><span data-stu-id="6fbc0-156">INPUTS</span></span>

### <span data-ttu-id="6fbc0-157">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="6fbc0-157">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="6fbc0-158">예약된 작업을 Unregister-ScheduledJob으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-158">You can pipe scheduled jobs to Unregister-ScheduledJob</span></span>

## <span data-ttu-id="6fbc0-159">출력</span><span class="sxs-lookup"><span data-stu-id="6fbc0-159">OUTPUTS</span></span>

### <span data-ttu-id="6fbc0-160">없음</span><span class="sxs-lookup"><span data-stu-id="6fbc0-160">None</span></span>
<span data-ttu-id="6fbc0-161">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6fbc0-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="6fbc0-162">참고</span><span class="sxs-lookup"><span data-stu-id="6fbc0-162">NOTES</span></span>

## <span data-ttu-id="6fbc0-163">관련 링크</span><span class="sxs-lookup"><span data-stu-id="6fbc0-163">RELATED LINKS</span></span>

[<span data-ttu-id="6fbc0-164">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6fbc0-164">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="6fbc0-165">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6fbc0-165">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="6fbc0-166">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6fbc0-166">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="6fbc0-167">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6fbc0-167">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="6fbc0-168">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6fbc0-168">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="6fbc0-169">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6fbc0-169">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="6fbc0-170">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6fbc0-170">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="6fbc0-171">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6fbc0-171">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="6fbc0-172">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6fbc0-172">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="6fbc0-173">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6fbc0-173">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="6fbc0-174">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6fbc0-174">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="6fbc0-175">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6fbc0-175">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="6fbc0-176">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="6fbc0-176">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="6fbc0-177">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6fbc0-177">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="6fbc0-178">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="6fbc0-178">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="6fbc0-179">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="6fbc0-179">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
