---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/debug-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Debug-Job
ms.openlocfilehash: 12c44f8663017ec13ad135cc37cb076f999e3587
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99600149"
---
# <span data-ttu-id="d028b-102">Debug-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-102">Debug-Job</span></span>

## <span data-ttu-id="d028b-103">개요</span><span class="sxs-lookup"><span data-stu-id="d028b-103">SYNOPSIS</span></span>
<span data-ttu-id="d028b-104">실행 중인 백그라운드, 원격 또는 PowerShell 워크플로 작업을 디버깅 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-104">Debugs a running background, remote, or PowerShell Workflow job.</span></span>

## <span data-ttu-id="d028b-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d028b-105">SYNTAX</span></span>

### <span data-ttu-id="d028b-106">JobParameterSet (기본값)</span><span class="sxs-lookup"><span data-stu-id="d028b-106">JobParameterSet (Default)</span></span>

```
Debug-Job [-Job] <Job> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d028b-107">JobNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="d028b-107">JobNameParameterSet</span></span>

```
Debug-Job [-Name] <String> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d028b-108">JobIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d028b-108">JobIdParameterSet</span></span>

```
Debug-Job [-Id] <Int32> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="d028b-109">JobInstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="d028b-109">JobInstanceIdParameterSet</span></span>

```
Debug-Job [-InstanceId] <Guid> [-BreakAll] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="d028b-110">설명</span><span class="sxs-lookup"><span data-stu-id="d028b-110">DESCRIPTION</span></span>
<span data-ttu-id="d028b-111">**디버그-작업** cmdlet을 사용 하 여 작업 내에서 실행 되는 스크립트를 디버그할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-111">The **Debug-Job** cmdlet lets you debug scripts that are running within jobs.</span></span>
<span data-ttu-id="d028b-112">Cmdlet은 PowerShell 워크플로 작업, 백그라운드 작업 및 원격 세션에서 실행 되는 작업을 디버그 하도록 디자인 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-112">The cmdlet is designed to debug PowerShell Workflow jobs, background jobs, and jobs running in remote sessions.</span></span>
<span data-ttu-id="d028b-113">**디버그-작업** 은 실행 중인 작업 개체, 이름, ID 또는 인스턴스 ID를 입력으로 수락 하 고 실행 중인 스크립트에서 디버깅 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-113">**Debug-Job** accepts a running job object, name, ID, or instance ID as input, and starts a debugging session on the script it is running.</span></span>
<span data-ttu-id="d028b-114">Debugger **quit** 명령은 작업을 중지 하 고 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-114">The debugger **quit** command stops the job and running script.</span></span>
<span data-ttu-id="d028b-115">Windows PowerShell 5.0부터 **끝내기** 명령은 디버거를 분리 하 고 작업을 계속 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-115">Starting in Windows PowerShell 5.0, the **exit** command detaches the debugger, and allows the job to continue to run.</span></span>

## <span data-ttu-id="d028b-116">예제</span><span class="sxs-lookup"><span data-stu-id="d028b-116">EXAMPLES</span></span>

### <span data-ttu-id="d028b-117">예제 1: 작업 ID로 작업 디버그</span><span class="sxs-lookup"><span data-stu-id="d028b-117">Example 1: Debug a job by job ID</span></span>

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

<span data-ttu-id="d028b-118">이 명령은 ID가 3 인 실행 중인 작업을 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-118">This command breaks into a running job with an ID of 3.</span></span>

## <span data-ttu-id="d028b-119">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="d028b-119">PARAMETERS</span></span>

### <span data-ttu-id="d028b-120">-Id</span><span class="sxs-lookup"><span data-stu-id="d028b-120">-Id</span></span>
<span data-ttu-id="d028b-121">실행 중인 작업의 ID 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-121">Specifies the ID number of a running job.</span></span>
<span data-ttu-id="d028b-122">작업의 ID 번호를 가져오려면 Get-Job cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-122">To get the ID number of a job, run the Get-Job cmdlet.</span></span>

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

### <span data-ttu-id="d028b-123">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="d028b-123">-InstanceId</span></span>
<span data-ttu-id="d028b-124">실행 중인 작업의 인스턴스 ID GUID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-124">Specifies the instance ID GUID of a running job.</span></span>
<span data-ttu-id="d028b-125">작업의 *InstanceId* 를 가져오려면 다음 예제와 같이 **get job** cmdlet을 실행 하 고 결과를 **Format-** _ cmdlet으로 파이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-125">To get the *InstanceId* of a job, run the **Get-Job** cmdlet, piping the results into a **Format-** _ cmdlet, as shown in the following example:</span></span>

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

### <span data-ttu-id="d028b-126">-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-126">-Job</span></span>
<span data-ttu-id="d028b-127">실행 중인 작업 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-127">Specifies a running job object.</span></span>
<span data-ttu-id="d028b-128">이 매개 변수를 사용 하는 가장 간단한 방법은 변수로 디버그할 실행 중인 작업을 반환 하는 _ *Get job*\* 명령의 결과를 저장 한 다음이 매개 변수의 값으로 변수를 지정 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-128">The simplest way to use this parameter is to save the results of a _ *Get-Job*\* command that returns the running job that you want to debug in a variable, and then specify the variable as the value of this parameter.</span></span>

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

### <span data-ttu-id="d028b-129">-Name</span><span class="sxs-lookup"><span data-stu-id="d028b-129">-Name</span></span>
<span data-ttu-id="d028b-130">작업 이름을 지정 하 여 작업을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-130">Specifies a job by the friendly name of the job.</span></span>
<span data-ttu-id="d028b-131">작업을 시작할 때 Invoke-Command 및 JobName와 같은 cmdlet에  매개 변수를 추가 하 여 작업 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-131">When you start a job, you can specify a job name by adding the *JobName* parameter, in cmdlets such as Invoke-Command and Start-Job.</span></span>

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

### <span data-ttu-id="d028b-132">-Confirm</span><span class="sxs-lookup"><span data-stu-id="d028b-132">-Confirm</span></span>
<span data-ttu-id="d028b-133">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-133">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="d028b-134">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="d028b-134">-WhatIf</span></span>
<span data-ttu-id="d028b-135">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-135">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="d028b-136">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d028b-136">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="d028b-137">-간</span><span class="sxs-lookup"><span data-stu-id="d028b-137">-BreakAll</span></span>

<span data-ttu-id="d028b-138">{{모든 설명 채우기 설명}}</span><span class="sxs-lookup"><span data-stu-id="d028b-138">{{ Fill BreakAll Description }}</span></span>

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

### <span data-ttu-id="d028b-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d028b-139">CommonParameters</span></span>
<span data-ttu-id="d028b-140">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d028b-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d028b-141">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d028b-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d028b-142">입력</span><span class="sxs-lookup"><span data-stu-id="d028b-142">INPUTS</span></span>

### <span data-ttu-id="d028b-143">System.web. Remorererea 작업</span><span class="sxs-lookup"><span data-stu-id="d028b-143">System.Management.Automation.RemotingJob</span></span>

## <span data-ttu-id="d028b-144">출력</span><span class="sxs-lookup"><span data-stu-id="d028b-144">OUTPUTS</span></span>

## <span data-ttu-id="d028b-145">참고</span><span class="sxs-lookup"><span data-stu-id="d028b-145">NOTES</span></span>

## <span data-ttu-id="d028b-146">관련 링크</span><span class="sxs-lookup"><span data-stu-id="d028b-146">RELATED LINKS</span></span>

[<span data-ttu-id="d028b-147">Get-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-147">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="d028b-148">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-148">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="d028b-149">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-149">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="d028b-150">Start-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-150">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="d028b-151">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-151">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="d028b-152">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="d028b-152">Wait-Job</span></span>](Wait-Job.md)

