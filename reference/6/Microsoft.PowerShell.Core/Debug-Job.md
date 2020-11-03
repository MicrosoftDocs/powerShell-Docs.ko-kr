---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: 312e3b9900a67e294ec5052cb05b4ee989d4c3ad
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93215073"
---
# <span data-ttu-id="a27aa-103">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-103">Debug-Job</span></span>

## <span data-ttu-id="a27aa-104">개요</span><span class="sxs-lookup"><span data-stu-id="a27aa-104">SYNOPSIS</span></span>
<span data-ttu-id="a27aa-105">실행 중인 백그라운드, 원격 또는 PowerShell 워크플로 작업을 디버깅 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-105">Debugs a running background, remote, or PowerShell Workflow job.</span></span>

## <span data-ttu-id="a27aa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a27aa-106">SYNTAX</span></span>

### <span data-ttu-id="a27aa-107">JobParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="a27aa-107">JobParameterSet (Default)</span></span>

```
Debug-Job [-Job] <Job> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a27aa-108">JobNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="a27aa-108">JobNameParameterSet</span></span>

```
Debug-Job [-Name] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a27aa-109">JobIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="a27aa-109">JobIdParameterSet</span></span>

```
Debug-Job [-Id] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a27aa-110">JobInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="a27aa-110">JobInstanceIdParameterSet</span></span>

```
Debug-Job [-InstanceId] <Guid> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a27aa-111">설명</span><span class="sxs-lookup"><span data-stu-id="a27aa-111">DESCRIPTION</span></span>
<span data-ttu-id="a27aa-112">**디버그-작업** cmdlet을 사용 하 여 작업 내에서 실행 되는 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-112">The **Debug-Job** cmdlet lets you debug scripts that are running within jobs.</span></span>
<span data-ttu-id="a27aa-113">Cmdlet은 PowerShell 워크플로 작업, 백그라운드 작업 및 원격 세션에서 실행 되는 작업을 디버그 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-113">The cmdlet is designed to debug PowerShell Workflow jobs, background jobs, and jobs running in remote sessions.</span></span>
<span data-ttu-id="a27aa-114">**디버그-작업** 은 실행 중인 작업 개체, 이름, ID 또는 인스턴스 ID를 입력으로 수락 하 고 실행 중인 스크립트에서 디버깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-114">**Debug-Job** accepts a running job object, name, ID, or instance ID as input, and starts a debugging session on the script it is running.</span></span>
<span data-ttu-id="a27aa-115">Debugger **quit** 명령은 작업을 중지 하 고 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-115">The debugger **quit** command stops the job and running script.</span></span>
<span data-ttu-id="a27aa-116">Windows PowerShell 5.0부터 **끝내기** 명령은 디버거를 분리 하 고 작업을 계속 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-116">Starting in Windows PowerShell 5.0, the **exit** command detaches the debugger, and allows the job to continue to run.</span></span>

## <span data-ttu-id="a27aa-117">예제</span><span class="sxs-lookup"><span data-stu-id="a27aa-117">EXAMPLES</span></span>

### <span data-ttu-id="a27aa-118">예제 1: 작업 ID로 작업 디버그</span><span class="sxs-lookup"><span data-stu-id="a27aa-118">Example 1: Debug a job by job ID</span></span>

```
PS C:\> Debug-Job -ID 3
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
3      Job3            RemoteJob       Running       True            PowerShellIx         TestWFDemo1.ps1
          Entering debug mode. Use h or ? for help.

          Hit Line breakpoint on 'C:\TestWFDemo1.ps1:8'

          At C:\TestWFDemo1.ps1:8 char:5
          +     Write-Output -InputObject "Now writing output:"
          +     ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
          [DBG:PowerShellIx]: PS C:\> > list

              3:
              4:  workflow SampleWorkflowTest
              5:  {
              6:      param ($MyOutput)
              7:
              8:*     Write-Output -InputObject "Now writing output:"
              9:      Write-Output -Input $MyOutput
             10:
             11:      Write-Output -InputObject "Get PowerShell process:"
             12:      Get-Process -Name powershell
             13:
             14:      Write-Output -InputObject "Workflow function complete."
             15:  }
             16:
             17:  # Call workflow function
             18:  SampleWorkflowTest -MyOutput "Hello"
```

<span data-ttu-id="a27aa-119">이 명령은 ID가 3 인 실행 중인 작업을 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-119">This command breaks into a running job with an ID of 3.</span></span>

## <span data-ttu-id="a27aa-120">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a27aa-120">PARAMETERS</span></span>

### <span data-ttu-id="a27aa-121">-Id</span><span class="sxs-lookup"><span data-stu-id="a27aa-121">-Id</span></span>
<span data-ttu-id="a27aa-122">실행 중인 작업의 ID 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-122">Specifies the ID number of a running job.</span></span>
<span data-ttu-id="a27aa-123">작업의 ID 번호를 가져오려면 Get-Job cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-123">To get the ID number of a job, run the Get-Job cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: JobIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a27aa-124">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="a27aa-124">-InstanceId</span></span>
<span data-ttu-id="a27aa-125">실행 중인 작업의 인스턴스 ID GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-125">Specifies the instance ID GUID of a running job.</span></span>
<span data-ttu-id="a27aa-126">작업의 *InstanceId* 를 가져오려면 다음 예제와 같이 **get job** cmdlet을 실행 하 고 결과를 **형식-** \* cmdlet으로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-126">To get the *InstanceId* of a job, run the **Get-Job** cmdlet, piping the results into a **Format-** \* cmdlet, as shown in the following example:</span></span>

`Get-Job | Format-List -Property Id,Name,InstanceId,State`

```yaml
Type: System.Guid
Parameter Sets: JobInstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a27aa-127">-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-127">-Job</span></span>
<span data-ttu-id="a27aa-128">실행 중인 작업 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-128">Specifies a running job object.</span></span>
<span data-ttu-id="a27aa-129">이 매개 변수를 사용 하는 가장 간단한 방법은 디버깅할 실행 중인 작업을 반환 하는 **Get job** 명령의 결과를 저장 한 다음 변수를이 매개 변수 값으로 지정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-129">The simplest way to use this parameter is to save the results of a **Get-Job** command that returns the running job that you want to debug in a variable, and then specify the variable as the value of this parameter.</span></span>

```yaml
Type: System.Management.Automation.Job
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a27aa-130">-Name</span><span class="sxs-lookup"><span data-stu-id="a27aa-130">-Name</span></span>
<span data-ttu-id="a27aa-131">작업 이름을 지정 하 여 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-131">Specifies a job by the friendly name of the job.</span></span>
<span data-ttu-id="a27aa-132">작업을 시작할 때 Invoke-Command 및 JobName와 같은 cmdlet에 *JobName* 매개 변수를 추가 하 여 작업 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-132">When you start a job, you can specify a job name by adding the *JobName* parameter, in cmdlets such as Invoke-Command and Start-Job.</span></span>

```yaml
Type: System.String
Parameter Sets: JobNameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a27aa-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a27aa-133">-Confirm</span></span>
<span data-ttu-id="a27aa-134">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a27aa-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a27aa-135">-WhatIf</span></span>
<span data-ttu-id="a27aa-136">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-136">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a27aa-137">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a27aa-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a27aa-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a27aa-138">CommonParameters</span></span>
<span data-ttu-id="a27aa-139">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a27aa-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a27aa-140">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a27aa-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a27aa-141">입력</span><span class="sxs-lookup"><span data-stu-id="a27aa-141">INPUTS</span></span>

### <span data-ttu-id="a27aa-142">System.web. Remorererea 작업</span><span class="sxs-lookup"><span data-stu-id="a27aa-142">System.Management.Automation.RemotingJob</span></span>

## <span data-ttu-id="a27aa-143">출력</span><span class="sxs-lookup"><span data-stu-id="a27aa-143">OUTPUTS</span></span>

## <span data-ttu-id="a27aa-144">참고</span><span class="sxs-lookup"><span data-stu-id="a27aa-144">NOTES</span></span>

## <span data-ttu-id="a27aa-145">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a27aa-145">RELATED LINKS</span></span>

[<span data-ttu-id="a27aa-146">Get-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-146">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="a27aa-147">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-147">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="a27aa-148">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-148">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="a27aa-149">Start-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-149">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="a27aa-150">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-150">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="a27aa-151">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="a27aa-151">Wait-Job</span></span>](Wait-Job.md)
