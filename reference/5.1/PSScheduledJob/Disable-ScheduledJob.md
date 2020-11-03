---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/disable-scheduledjob?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-ScheduledJob
ms.openlocfilehash: a7ea520d7d0365fd0de8c9d0bb767981b68467c6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213474"
---
# <span data-ttu-id="116b4-103">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="116b4-103">Disable-ScheduledJob</span></span>

## <span data-ttu-id="116b4-104">개요</span><span class="sxs-lookup"><span data-stu-id="116b4-104">SYNOPSIS</span></span>
<span data-ttu-id="116b4-105">예약된 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-105">Disables a scheduled job.</span></span>

## <span data-ttu-id="116b4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="116b4-106">SYNTAX</span></span>

### <span data-ttu-id="116b4-107">정의 (기본값)</span><span class="sxs-lookup"><span data-stu-id="116b4-107">Definition (Default)</span></span>

```
Disable-ScheduledJob [-InputObject] <ScheduledJobDefinition> [-PassThru] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="116b4-108">인</span><span class="sxs-lookup"><span data-stu-id="116b4-108">DefinitionId</span></span>

```
Disable-ScheduledJob [-Id] <Int32> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="116b4-109">Build.definitionname</span><span class="sxs-lookup"><span data-stu-id="116b4-109">DefinitionName</span></span>

```
Disable-ScheduledJob [-Name] <String> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="116b4-110">설명</span><span class="sxs-lookup"><span data-stu-id="116b4-110">DESCRIPTION</span></span>
<span data-ttu-id="116b4-111">**Disable-ScheduledJob** cmdlet은 예약된 작업을 일시적으로 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-111">The **Disable-ScheduledJob** cmdlet temporarily disables scheduled jobs.</span></span>
<span data-ttu-id="116b4-112">사용하지 않도록 설정하면 모든 작업 속성이 유지되며 작업 트리거도 사용할 수 있지만 트리거 시 예약된 작업이 자동으로 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-112">Disabling preserves all job properties and does not disable the job triggers, but it prevents the scheduled jobs from starting automatically when triggered.</span></span>
<span data-ttu-id="116b4-113">Start-Job cmdlet을 사용 하 여 사용 하지 않도록 설정 된 예약 된 작업을 시작 하거나 사용 하지 않도록 설정 된 예약 된 작업을 템플릿으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-113">You can start a disabled scheduled job by using the Start-Job cmdlet or use a disabled scheduled job as a template.</span></span>

<span data-ttu-id="116b4-114">예약된 작업을 사용하지 않도록 설정하기 위해 **Disable-ScheduledJob** cmdlet은 예약된 작업의 **Enabled** 속성을 False($false)로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-114">To disable a scheduled job, the **Disable-ScheduledJob** cmdlet sets the **Enabled** property of the scheduled job to False ($false).</span></span>
<span data-ttu-id="116b4-115">예약 된 작업을 다시 사용 하도록 설정 하려면 Enable-ScheduledJob cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-115">To re-enable the scheduled job, use the Enable-ScheduledJob cmdlet.</span></span>

<span data-ttu-id="116b4-116">**Set-scheduledjob** 는 Windows PowerShell에 포함 된 **PSScheduledJob** 모듈의 작업 예약 cmdlet 컬렉션 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-116">**Disable-ScheduledJob** is one of a collection of job scheduling cmdlets in the **PSScheduledJob** module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="116b4-117">예약된 작업에 대한 자세한 내용은 PSScheduledJob 모듈의 정보 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="116b4-117">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="116b4-118">PSScheduledJob 모듈을 가져온 다음를 입력 `Get-Help about_Scheduled*` 하거나 about_Scheduled_Jobs를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="116b4-118">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="116b4-119">이 cmdlet은 Windows PowerShell 3.0에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-119">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="116b4-120">예제</span><span class="sxs-lookup"><span data-stu-id="116b4-120">EXAMPLES</span></span>

### <span data-ttu-id="116b4-121">예제 1: 예약 된 작업을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="116b4-121">Example 1: Disable a scheduled job</span></span>

```
PS C:\> Disable-ScheduledJob -ID 2 -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
```

<span data-ttu-id="116b4-122">이 명령은 로컬 컴퓨터에서 ID가 2인 예약된 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-122">This command disables the scheduled job with ID 2 on the local computer.</span></span>
<span data-ttu-id="116b4-123">출력은 명령의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-123">The output shows the effect of the command.</span></span>

### <span data-ttu-id="116b4-124">예 2: 모든 예약 된 작업을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="116b4-124">Example 2: Disable all scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Disable-ScheduledJob -Passthru
Id         Name            Triggers        Command                                  Enabled
--         ----            --------        -------                                  -------
1          ArchiveProje... {}              C:\Scripts\Archive-DxProjects.ps1        False
2          Inventory       {1, 2}          \\Srv01\Scripts\Get-FullInventory.ps1    False
4          Test-HelpFiles  {1}             .\Test-HelpFiles.ps1                     False
5          TestJob         {1, 2}          .\Run-AllTests.ps1                       False
```

<span data-ttu-id="116b4-125">이 명령은 로컬 컴퓨터에서 모든 예약된 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-125">This command disables all scheduled jobs on the local computer.</span></span>
<span data-ttu-id="116b4-126">Get-ScheduledJob cmdlet을 사용 하 여 모든 예약 된 작업을 가져오고 **set-scheduledjob** cmdlet을 사용 하 여 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-126">It uses the Get-ScheduledJob cmdlet to get all scheduled job and the **Disable-ScheduledJob** cmdlet to disable them.</span></span>

<span data-ttu-id="116b4-127">Enable-ScheduledJob cmdlet을 사용 하 여 예약 된 작업을 다시 사용 하도록 설정 하 고 Start-Job cmdlet을 사용 하 여 사용 하지 않도록 설정 된 예약 된 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-127">You can re-enable scheduled job by using the Enable-ScheduledJob cmdlet and run a disabled scheduled job by using the Start-Job cmdlet.</span></span>

<span data-ttu-id="116b4-128">**Set-scheduledjob** 는 이미 사용 하지 않도록 설정 된 예약 된 작업을 사용 하지 않도록 설정 하는 경우 경고 또는 오류를 생성 하지 않으므로 조건 없이 모든 예약 된 작업을 사용 하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-128">**Disable-ScheduledJob** does not generate warnings or errors if you disable a scheduled job that is already disabled, so you can disable all scheduled jobs without conditions.</span></span>

### <span data-ttu-id="116b4-129">예 3: 선택한 예약 된 작업 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="116b4-129">Example 3: Disable selected scheduled jobs</span></span>

```
PS C:\> Get-ScheduledJob | Where-Object {!$_.Credential} | Disable-ScheduledJob
```

<span data-ttu-id="116b4-130">이 명령은 자격 증명이 포함되지 않은 예약된 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-130">This command disables scheduled job do not include a credential.</span></span>
<span data-ttu-id="116b4-131">자격 증명이 없는 작업은 작업을 만든 사용자의 사용 권한으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-131">Jobs without credentials run with the permission of the user who created them.</span></span>

<span data-ttu-id="116b4-132">이 명령은 Get-ScheduledJob cmdlet을 사용 하 여 컴퓨터에 있는 모든 예약 된 작업을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-132">The command uses the Get-ScheduledJob cmdlet to get all scheduled jobs on the computer.</span></span>
<span data-ttu-id="116b4-133">파이프라인 연산자는 예약 된 작업을 Where-Object cmdlet으로 보냅니다 .이 cmdlet은 자격 증명이 없는 예약 된 작업을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-133">A pipeline operator sends the scheduled jobs to the Where-Object cmdlet, which selects scheduled jobs that do not have credentials.</span></span>
<span data-ttu-id="116b4-134">이 명령은 NOT(!) 연산자를 사용하며 예약된 작업의 Credential 속성을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-134">The command uses the not (!) operator and references the Credential property of the scheduled job.</span></span>
<span data-ttu-id="116b4-135">다른 파이프라인 연산자가 선택한 예약된 작업을 **Disable-ScheduledJob** cmdlet으로 보내면 이 cmdlet이 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-135">Another pipeline operator sends the selected scheduled jobs to the **Disable-ScheduledJob** cmdlet, which disables them.</span></span>

### <span data-ttu-id="116b4-136">예 4: 원격 컴퓨터에서 예약 된 작업을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="116b4-136">Example 4: Disable scheduled jobs on a remote computer</span></span>

```
PS C:\> Invoke-Command -ComputerName Srv01, Srv10 -ScriptBlock {Disable-ScheduledJob -Name TestJob}
```

<span data-ttu-id="116b4-137">이 명령은 두 원격 컴퓨터 Srv01 및 Srv10에서 TestJob scheduled 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-137">This command disables the TestJob scheduled job on two remote computers, Srv01 and Srv10.</span></span>

<span data-ttu-id="116b4-138">이 명령은 Invoke-Command cmdlet을 사용 하 여 Srv01 및 Srv10 컴퓨터에서 **set-scheduledjob** 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-138">The command uses the Invoke-Command cmdlet to run a **Disable-ScheduledJob** command on the Srv01 and Srv10 computers.</span></span>
<span data-ttu-id="116b4-139">*Disable-ScheduledJob* 의 **Name** 매개 변수를 사용하여 각 컴퓨터에서 TestJob 예약된 작업을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-139">The command uses the *Name* parameter of **Disable-ScheduledJob** to select the TestJob scheduled job on each computer.</span></span>

### <span data-ttu-id="116b4-140">예 5: 전역 ID로 예약 된 작업을 사용 하지 않도록 설정</span><span class="sxs-lookup"><span data-stu-id="116b4-140">Example 5: Disable a scheduled job by its global ID</span></span>

```
The first command demonstrates one way of finding the GlobalID of a scheduled job. The command uses the Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Format-Table cmdlet, which displays the Name, GlobalID, and Command properties of each job in a table.
PS C:\> Get-ScheduledJob | Format-Table -Property Name, GlobalID, Command -Autosize
Name             GlobalId                             Command
----             --------                             -------
ArchiveProjects1 a26a0b3d-b4e6-44d3-8b95-8706ef621f7c C:\Scripts\Archive-DxProjects.ps1
Inventory        3ac37e5d-84c0-4a8f-9661-7e88ebb8f914 \\Srv01\Scripts\Get-FullInventory.ps1
Backup-Scripts   4d0cc6be-c082-48d1-baec-1bd8278f3c81  Copy-Item C:\CurrentScripts\*.ps1 -Destination C:\BackupScripts
Test-HelpFiles   d77020ca-f20d-42be-86c8-fc64df97db90 .\Test-HelpFiles.ps1
Test-HelpFiles   2f1606d2-c6cf-4bef-8b1c-ae36a9cc9934 .\Test-DomainHelpFiles.ps1

The second command uses the  Get-ScheduledJob cmdlet to get the scheduled jobs on the computer. A pipeline operator (|) sends the scheduled jobs to the Where-Object cmdlet, which selects the scheduled job with the specified global ID. Another pipeline operator sends the job to the **Disable-ScheduledJob** cmdlet, which disables it.
PS C:\> Get-ScheduledJob | Where-Object {$_.GlobalID = d77020ca-f20d-42be-86c8-fc64df97db90} | Disable-ScheduledJob
```

<span data-ttu-id="116b4-141">이 예제에서는 전역 ID를 사용하여 예약된 작업을 사용하지 않도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-141">This examples shows how to disable a scheduled job by using its global identifier.</span></span>
<span data-ttu-id="116b4-142">예약된 작업의 GlobalID 속성 값은 고유 식별자(GUID)입니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-142">The value of the GlobalID property of a scheduled job is a unique identifier (GUID).</span></span>
<span data-ttu-id="116b4-143">여러 컴퓨터에서 예약된 작업을 사용하지 않도록 설정하는 경우와 같이 정밀도가 필요할 때 GlobalID 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-143">Use the GlobalID value when precision is required, such as when you are disabling scheduled jobs on multiple computers.</span></span>

## <span data-ttu-id="116b4-144">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="116b4-144">PARAMETERS</span></span>

### <span data-ttu-id="116b4-145">-Id</span><span class="sxs-lookup"><span data-stu-id="116b4-145">-Id</span></span>
<span data-ttu-id="116b4-146">지정한 ID를 가진 예약된 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-146">Disables the scheduled job with the specified identification number (ID).</span></span>
<span data-ttu-id="116b4-147">예약된 작업의 ID를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-147">Enter the ID of a scheduled job.</span></span>

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

### <span data-ttu-id="116b4-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="116b4-148">-InputObject</span></span>
<span data-ttu-id="116b4-149">사용하지 않도록 설정할 예약된 작업을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-149">Specifies the scheduled job to be disabled.</span></span>
<span data-ttu-id="116b4-150">**ScheduledJobDefinition** 개체가 포함 된 변수를 입력 하거나 **ScheduledJobDefinition** 개체를 가져오는 명령 또는 식 (예: Get-ScheduledJob 명령)을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-150">Enter a variable that contains  **ScheduledJobDefinition** objects or type a command or expression that gets **ScheduledJobDefinition** objects, such as a Get-ScheduledJob command.</span></span>
<span data-ttu-id="116b4-151">**ScheduledJobDefinition** 개체를 set-scheduledjob로 파이프 하 여 **사용 하지 않도록 설정할** 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-151">You can also pipe a **ScheduledJobDefinition** object to **Disable-ScheduledJob**.</span></span>

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

### <span data-ttu-id="116b4-152">-Name</span><span class="sxs-lookup"><span data-stu-id="116b4-152">-Name</span></span>
<span data-ttu-id="116b4-153">지정한 이름을 가진 예약된 작업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-153">Disables the scheduled jobs with the specified names.</span></span>
<span data-ttu-id="116b4-154">예약된 작업의 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-154">Enter the name of a scheduled job.</span></span>
<span data-ttu-id="116b4-155">와일드카드가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-155">Wildcards are supported.</span></span>

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

### <span data-ttu-id="116b4-156">-PassThru</span><span class="sxs-lookup"><span data-stu-id="116b4-156">-PassThru</span></span>
<span data-ttu-id="116b4-157">작업 중인 항목을 나타내는 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-157">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="116b4-158">기본적으로 이 cmdlet은 출력을 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-158">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="116b4-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="116b4-159">-Confirm</span></span>
<span data-ttu-id="116b4-160">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-160">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="116b4-161">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="116b4-161">-WhatIf</span></span>
<span data-ttu-id="116b4-162">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-162">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="116b4-163">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-163">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="116b4-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="116b4-164">CommonParameters</span></span>
<span data-ttu-id="116b4-165">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="116b4-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="116b4-166">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="116b4-166">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="116b4-167">입력</span><span class="sxs-lookup"><span data-stu-id="116b4-167">INPUTS</span></span>

### <span data-ttu-id="116b4-168">Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="116b4-168">Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="116b4-169">예약된 작업을 **Disable-ScheduledJob** 으로 파이프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-169">You can pipe a scheduled job to **Disable-ScheduledJob**.</span></span>

## <span data-ttu-id="116b4-170">출력</span><span class="sxs-lookup"><span data-stu-id="116b4-170">OUTPUTS</span></span>

### <span data-ttu-id="116b4-171">None 또는 Set-scheduledjob. ScheduledJobDefinition</span><span class="sxs-lookup"><span data-stu-id="116b4-171">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition</span></span>
<span data-ttu-id="116b4-172">**Passthru** 매개 변수를 사용할 경우 **Disable-ScheduledJob** 은 사용하지 않도록 설정된 예약된 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-172">If you use the **Passthru** parameter, **Disable-ScheduledJob** returns the scheduled job that was disabled.</span></span>
<span data-ttu-id="116b4-173">그러지 않으면 이 cmdlet에서 출력이 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-173">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="116b4-174">참고</span><span class="sxs-lookup"><span data-stu-id="116b4-174">NOTES</span></span>

* <span data-ttu-id="116b4-175">**Set-scheduledjob** 는 이미 사용 하지 않도록 설정 된 예약 된 작업을 사용 하지 않도록 설정 하는 데 사용 하는 경우 경고 또는 오류를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="116b4-175">**Disable-ScheduledJob** does not generate warnings or errors if you use it to disable a scheduled job that is already disabled.</span></span>

## <span data-ttu-id="116b4-176">관련 링크</span><span class="sxs-lookup"><span data-stu-id="116b4-176">RELATED LINKS</span></span>

[<span data-ttu-id="116b4-177">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="116b4-177">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="116b4-178">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="116b4-178">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="116b4-179">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="116b4-179">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="116b4-180">Enable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="116b4-180">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="116b4-181">Enable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="116b4-181">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="116b4-182">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="116b4-182">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="116b4-183">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="116b4-183">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="116b4-184">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="116b4-184">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="116b4-185">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="116b4-185">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="116b4-186">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="116b4-186">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="116b4-187">Register-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="116b4-187">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="116b4-188">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="116b4-188">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="116b4-189">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="116b4-189">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="116b4-190">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="116b4-190">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="116b4-191">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="116b4-191">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="116b4-192">Unregister-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="116b4-192">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
