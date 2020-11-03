---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/enable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-ScheduledJob
ms.openlocfilehash: 757402a348a6b694d2f2aee53053a1b7615dbb53
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213449"
---
# <span data-ttu-id="69197-103">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="69197-103">Enable-ScheduledJob</span></span>

## <span data-ttu-id="69197-104">개요</span><span class="sxs-lookup"><span data-stu-id="69197-104">SYNOPSIS</span></span>
<span data-ttu-id="69197-105">예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-105">Enables a scheduled job.</span></span>

## <span data-ttu-id="69197-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="69197-106">SYNTAX</span></span>

### <span data-ttu-id="69197-107">정의 (기본값)</span><span class="sxs-lookup"><span data-stu-id="69197-107">Definition (Default)</span></span>

```
Enable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="69197-108">인</span><span class="sxs-lookup"><span data-stu-id="69197-108">DefinitionId</span></span>

```
Enable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="69197-109">Build.definitionname</span><span class="sxs-lookup"><span data-stu-id="69197-109">DefinitionName</span></span>

```
Enable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="69197-110">설명</span><span class="sxs-lookup"><span data-stu-id="69197-110">DESCRIPTION</span></span>
<span data-ttu-id="69197-111">**Set-scheduledjob** cmdlet은 Disable-ScheduledJob cmdlet을 사용 하 여 비활성화 된 작업 등 사용 하지 않도록 설정 된 예약 된 작업을 다시 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-111">The **Enable-ScheduledJob** cmdlet re-enables scheduled jobs that are disabled, such as those that are disabled by using the Disable-ScheduledJob cmdlet.</span></span>
<span data-ttu-id="69197-112">사용되는 작업은 트리거 시 자동으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="69197-112">Enabled jobs run automatically when triggered.</span></span>

<span data-ttu-id="69197-113">예약 된 작업을 사용 하도록 설정 하기 위해 **set-scheduledjob** cmdlet은 예약 된 작업의 Enabled 속성을 $True 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-113">To enable a scheduled job, the **Enable-ScheduledJob** cmdlet sets the Enabled property of the scheduled job to $True.</span></span>

<span data-ttu-id="69197-114">**Enabled-set-scheduledjob** 은 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="69197-114">**Enabled-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="69197-115">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69197-115">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="69197-116">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="69197-116">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="69197-117">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-117">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="69197-118">예제</span><span class="sxs-lookup"><span data-stu-id="69197-118">EXAMPLES</span></span>

### <span data-ttu-id="69197-119">예제 1: 예약 된 작업을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="69197-119">Example 1: Enable a scheduled job</span></span>

```
PS C:\> Enable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
```

<span data-ttu-id="69197-120">이 명령은 로컬 컴퓨터에서 ID가 2인 예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-120">This command enables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="69197-121">출력은 명령의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="69197-121">The output shows the effect of the command.</span></span>

### <span data-ttu-id="69197-122">예 2: 모든 예약 된 작업을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="69197-122">Example 2: Enable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Enable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        True
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    True
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     True
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       True
```

<span data-ttu-id="69197-123">이 명령은 로컬 컴퓨터에서 모든 예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-123">This command enables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="69197-124">Get-ScheduledJob cmdlet을 사용 하 여 모든 예약 된 작업을 가져오고 **set-scheduledjob** cmdlet을 사용 하 여 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-124">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Enable-ScheduledJob** cmdlet to enable them.</span></span>

<span data-ttu-id="69197-125">이미 사용 하도록 설정 된 예약 된 작업을 사용 하도록 설정 하는 경우 **set-scheduledjob** 는 경고 또는 오류를 생성 하지 않으므로 조건 없이 모든 예약 된 작업을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-125">**Enable-ScheduledJob** does not generate warnings or errors if you enable a scheduled job that is already enabled, so you can enable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="69197-126">예 3: 선택한 예약 된 작업 사용</span><span class="sxs-lookup"><span data-stu-id="69197-126">Example 3: Enable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Get-ScheduledJobOption | Where-Object {$_.RunWithoutNetwork} | ForEach-Object {Enable-ScheduledJob -InputObject $_.JobDefinition}
```

<span data-ttu-id="69197-127">이 명령은 네트워크 연결이 필요 없는 예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-127">This command enables scheduled jobs that do not require a network connection.</span></span>

<span data-ttu-id="69197-128">이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 컴퓨터에 있는 모든 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69197-128">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="69197-129">파이프라인 연산자는 예약 된 작업을 Get-ScheduledJobOption cmdlet으로 보냅니다 .이 cmdlet은 예약 된 각 작업의 작업 옵션을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69197-129">A pipeline operator sends the scheduled jobs to the Get-ScheduledJobOption cmdlet, which gets the job options of each scheduled job.</span></span>
<span data-ttu-id="69197-130">각 작업 옵션 개체에는 관련 예약된 작업을 포함하는 JobDefinition 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-130">Each job options object has a JobDefinition property that contains the associated scheduled job.</span></span>
<span data-ttu-id="69197-131">JobDefinition 속성은 명령을 완료하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="69197-131">The JobDefinition property is used to complete the command.</span></span>

<span data-ttu-id="69197-132">이 명령은 파이프라인 연산자 (|)를 사용 하 여 작업 옵션을 Where-Object cmdlet으로 보냅니다 .이 cmdlet은 **RunWithoutNetwork** 속성 값이 True ($true) 인 예약 된 작업 옵션 개체를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-132">The command uses a pipeline operator (|) to send the job options to the Where-Object cmdlet, which selects scheduled job option objects in which the **RunWithoutNetwork** property has a value of True ($true).</span></span>
<span data-ttu-id="69197-133">다른 파이프라인 연산자는 선택한 예약 된 작업 옵션 개체를 ForEach-Object cmdlet으로 보냅니다 .이 cmdlet은 예약 된 작업에서 각 작업 옵션 개체의 JobDefinition 속성 값에 있는 **set-scheduledjob** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-133">Another pipeline operator sends the selected scheduled job options objects to the ForEach-Object cmdlet which runs an **Enable-ScheduledJob** command on the scheduled job in the value of the JobDefinition property of each job options object.</span></span>

### <span data-ttu-id="69197-134">예 4: 원격 컴퓨터에서 예약 된 작업을 사용 하도록 설정</span><span class="sxs-lookup"><span data-stu-id="69197-134">Example 4: Enable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName "Srv01,Srv10" -ScriptBlock {Enable-ScheduledJob -Name "Inventory"}
```

<span data-ttu-id="69197-135">이 명령은 두 원격 컴퓨터 Srv01 및 Srv10에서 이름에 "test"가 포함된 예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-135">This command enables scheduled jobs that have "test" in their names on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="69197-136">이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 및 Srv10 컴퓨터에서 **set-scheduledjob** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-136">The command uses the Invoke-Command cmdlet to run an **Enable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="69197-137">*Enable-ScheduledJob* 의 **Name** 매개 변수를 사용하여 각 컴퓨터에서 Inventory 예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-137">The command uses the *Name* parameter of **Enable-ScheduledJob** to enable the Inventory scheduled job on each computer.</span></span>

## <span data-ttu-id="69197-138">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="69197-138">PARAMETERS</span></span>

### <span data-ttu-id="69197-139">-Id</span><span class="sxs-lookup"><span data-stu-id="69197-139">-Id</span></span>
<span data-ttu-id="69197-140">지정한 ID를 가진 예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-140">Enables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="69197-141">예약된 작업의 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-141">Enter the ID of a scheduled job.</span></span>

```yaml
Type: System.Int32
Parameter Sets: DefinitionId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="69197-142">-InputObject</span><span class="sxs-lookup"><span data-stu-id="69197-142">-InputObject</span></span>
<span data-ttu-id="69197-143">사용할 예약 된 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-143">Specifies the scheduled job to enable.</span></span>
<span data-ttu-id="69197-144">**ScheduledJobDefinition** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobDefinition** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-144">Enter a variable that contains **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="69197-145">**ScheduledJobDefinition** 개체를 **Enable-ScheduledJob** 으로 파이프할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-145">You can also pipe a **ScheduledJobDefinition** object to **Enable-ScheduledJob** .</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
Parameter Sets: Definition
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="69197-146">-Name</span><span class="sxs-lookup"><span data-stu-id="69197-146">-Name</span></span>
<span data-ttu-id="69197-147">지정한 이름을 가진 예약된 작업을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-147">Enables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="69197-148">예약된 작업의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-148">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="69197-149">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="69197-149">Wildcards are supported.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="69197-150">-PassThru</span><span class="sxs-lookup"><span data-stu-id="69197-150">-PassThru</span></span>
<span data-ttu-id="69197-151">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-151">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="69197-152">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-152">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="69197-153">-Confirm</span><span class="sxs-lookup"><span data-stu-id="69197-153">-Confirm</span></span>
<span data-ttu-id="69197-154">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-154">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="69197-155">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="69197-155">-WhatIf</span></span>
<span data-ttu-id="69197-156">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-156">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="69197-157">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-157">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="69197-158">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="69197-158">CommonParameters</span></span>
<span data-ttu-id="69197-159">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="69197-159">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="69197-160">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69197-160">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="69197-161">입력</span><span class="sxs-lookup"><span data-stu-id="69197-161">INPUTS</span></span>

### <span data-ttu-id="69197-162">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="69197-162">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="69197-163">예약 된 작업을 Set-scheduledjob로 파이프 하 여 **설정할** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-163">You can pipe a scheduled job to **Enable-ScheduledJob** .</span></span>

## <span data-ttu-id="69197-164">출력</span><span class="sxs-lookup"><span data-stu-id="69197-164">OUTPUTS</span></span>

### <span data-ttu-id="69197-165">None 또는 Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="69197-165">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="69197-166">**Passthru** 매개 변수를 사용할 경우 **Enable-ScheduledJob** 은 사용하도록 설정된 예약된 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="69197-166">If you use the **Passthru** parameter, **Enable-ScheduledJob** returns the scheduled job that was enabled.</span></span>
<span data-ttu-id="69197-167">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-167">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="69197-168">참고</span><span class="sxs-lookup"><span data-stu-id="69197-168">NOTES</span></span>

* <span data-ttu-id="69197-169">사용 하도록 설정 된 예약 된 작업을 사용 하도록 설정 하는 데 사용 하는 경우 **set-scheduledjob** 는 경고 또는 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="69197-169">**Enable-ScheduledJob** does not generate warnings or errors if you use it to enable a scheduled job that is already enabled.</span></span>

## <span data-ttu-id="69197-170">관련 링크</span><span class="sxs-lookup"><span data-stu-id="69197-170">RELATED LINKS</span></span>

[<span data-ttu-id="69197-171">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="69197-171">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="69197-172">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="69197-172">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="69197-173">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="69197-173">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="69197-174">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="69197-174">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="69197-175">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="69197-175">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="69197-176">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="69197-176">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="69197-177">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="69197-177">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="69197-178">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="69197-178">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="69197-179">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="69197-179">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="69197-180">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="69197-180">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="69197-181">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="69197-181">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="69197-182">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="69197-182">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="69197-183">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="69197-183">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="69197-184">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="69197-184">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="69197-185">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="69197-185">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="69197-186">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="69197-186">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
