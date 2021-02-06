---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: d08f883b232abadeacb445e5ba542b4b1fae023b
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2020
ms.locfileid: "99600415"
---
# <span data-ttu-id="9048a-102">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="9048a-102">Start-ThreadJob</span></span>

## <span data-ttu-id="9048a-103">개요</span><span class="sxs-lookup"><span data-stu-id="9048a-103">SYNOPSIS</span></span>
<span data-ttu-id="9048a-104">Cmdlet과 비슷한 백그라운드 작업을 만듭니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="9048a-104">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>

## <span data-ttu-id="9048a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9048a-105">SYNTAX</span></span>

### <span data-ttu-id="9048a-106">ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="9048a-106">ScriptBlock</span></span>

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### <span data-ttu-id="9048a-107">FilePath</span><span class="sxs-lookup"><span data-stu-id="9048a-107">FilePath</span></span>

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## <span data-ttu-id="9048a-108">설명</span><span class="sxs-lookup"><span data-stu-id="9048a-108">DESCRIPTION</span></span>

<span data-ttu-id="9048a-109">`Start-ThreadJob` cmdlet과 비슷한 백그라운드 작업을 만듭니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="9048a-109">`Start-ThreadJob` creates background jobs similar to the `Start-Job` cmdlet.</span></span> <span data-ttu-id="9048a-110">주요 차이점은 생성 된 작업은 로컬 프로세스 내에서 별도의 스레드에서 실행 된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-110">The main difference is that the jobs which are created run in separate threads within the local process.</span></span> <span data-ttu-id="9048a-111">기본적으로 작업은 작업을 시작한 호출자의 현재 작업 디렉터리를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-111">By default, the jobs use the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="9048a-112">또한 cmdlet은 **ThrottleLimit** 매개 변수를 지원 하 여 한 번에 실행 되는 작업 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-112">The cmdlet also supports a **ThrottleLimit** parameter to limit the number of jobs running at one time.</span></span> <span data-ttu-id="9048a-113">더 많은 작업이 시작 되 면 큐에 대기 하 고 현재 작업 수가 제한 한도 아래로 떨어질 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-113">As more jobs are started, they are queued and wait until the current number of jobs drops below the throttle limit.</span></span>

## <span data-ttu-id="9048a-114">예제</span><span class="sxs-lookup"><span data-stu-id="9048a-114">EXAMPLES</span></span>

### <span data-ttu-id="9048a-115">예제 1-스레드 한도가 2 인 백그라운드 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="9048a-115">Example 1 - Create background jobs with a thread limit of 2</span></span>

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### <span data-ttu-id="9048a-116">예 2-Start-Job 및 Start-ThreadJob의 성능 비교</span><span class="sxs-lookup"><span data-stu-id="9048a-116">Example 2 - Compare the performance of Start-Job and Start-ThreadJob</span></span>

<span data-ttu-id="9048a-117">이 예에서는와 간의 차이점을 보여 줍니다 `Start-Job` `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="9048a-117">This example shows the difference between `Start-Job` and `Start-ThreadJob`.</span></span> <span data-ttu-id="9048a-118">작업은 cmdlet을 `Start-Sleep` 1 초 동안 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-118">The jobs run the `Start-Sleep` cmdlet for 1 second.</span></span> <span data-ttu-id="9048a-119">작업은 병렬로 실행 되므로 총 실행 시간은 약 1 초 이며 작업을 만드는 데 필요한 시간을 더한 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-119">Since the jobs run in parallel, the total execution time is about 1 second, plus any time required to create the jobs.</span></span>

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

<span data-ttu-id="9048a-120">실행 시간에 대해 1 초를 뺀 후 `Start-Job` 5 개의 작업을 만드는 데 약 4.8 초가 소요 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-120">After subtracting 1 second for execution time, you can see that `Start-Job` takes about 4.8 seconds to create five jobs.</span></span> <span data-ttu-id="9048a-121">`Start-ThreadJob` 는 5 배 더 빠르며 5 개의 작업을 만드는 데 0.6 초 정도 걸립니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-121">`Start-ThreadJob` is 8 times faster, taking about 0.6 seconds to create five jobs.</span></span> <span data-ttu-id="9048a-122">결과는 사용자 환경에서 다를 수 있지만 상대적 향상은 동일 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-122">The results may vary in your environment but the relative improvement should be the same.</span></span>

### <span data-ttu-id="9048a-123">예제 3-InputObject를 사용 하 여 작업 만들기</span><span class="sxs-lookup"><span data-stu-id="9048a-123">Example 3 - Create jobs using InputObject</span></span>

<span data-ttu-id="9048a-124">이 예에서 스크립트 블록은 변수를 사용 하 여 `$input` **InputObject** 매개 변수에서 입력을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-124">In this example, the script block uses the `$input` variable to receive input from the **InputObject** parameter.</span></span> <span data-ttu-id="9048a-125">개체를로 파이프 하 여이 작업을 수행할 수도 있습니다 `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="9048a-125">This can also be done by piping objects to `Start-ThreadJob`.</span></span>

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### <span data-ttu-id="9048a-126">예제 4-부모 호스트에 작업 출력 스트림</span><span class="sxs-lookup"><span data-stu-id="9048a-126">Example 4 - Stream job output to parent host</span></span>

<span data-ttu-id="9048a-127">**Streaminghost** 매개 변수를 사용 하 여 모든 호스트 출력을 특정 호스트로 보내도록 작업에 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-127">Using the **StreamingHost** parameter you can tell a job to direct all host output to a specific host.</span></span> <span data-ttu-id="9048a-128">이 매개 변수를 사용 하지 않으면 출력은 작업 데이터 스트림 컬렉션으로 이동 하 고 작업에서 출력을 받을 때까지 호스트 콘솔에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-128">Without this parameter the output goes to the job data stream collection and doesn't appear in a host console until you receive the output from the job.</span></span>

<span data-ttu-id="9048a-129">이 예에서는 `Start-ThreadJob` 자동 변수를 사용 하 여 현재 호스트를 전달 합니다 `$Host` .</span><span class="sxs-lookup"><span data-stu-id="9048a-129">For this example, the current host is passed to `Start-ThreadJob` using the `$Host` automatic variable.</span></span>

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; �

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

<span data-ttu-id="9048a-130">에서 프롬프트가 `Read-Host` 표시 되 고 입력을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-130">Notice that the prompt from `Read-Host` is displayed and you are able to type input.</span></span> <span data-ttu-id="9048a-131">그런 다음에서 메시지가 `Write-Warning` 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-131">Then, the message from `Write-Warning` is displayed.</span></span> <span data-ttu-id="9048a-132">`Receive-Job`Cmdlet은 작업의 모든 출력을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-132">The `Receive-Job` cmdlet returns all the output from the job.</span></span>

## <span data-ttu-id="9048a-133">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9048a-133">PARAMETERS</span></span>

### <span data-ttu-id="9048a-134">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="9048a-134">-ArgumentList</span></span>

<span data-ttu-id="9048a-135">**FilePath** 또는 **ScriptBlock** 매개 변수로 지정 된 스크립트에 대 한 인수 또는 매개 변수 값의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-135">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** or **ScriptBlock** parameters.</span></span>

<span data-ttu-id="9048a-136">**Argumentlist** 는 명령줄에서 마지막 매개 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-136">**ArgumentList** must be the last parameter on the command line.</span></span> <span data-ttu-id="9048a-137">매개 변수 이름 다음에 오는 모든 값은 인수 목록에서 해석 되는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-137">All the values that follow the parameter name are interpreted values in the argument list.</span></span>

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

### <span data-ttu-id="9048a-138">-FilePath</span><span class="sxs-lookup"><span data-stu-id="9048a-138">-FilePath</span></span>

<span data-ttu-id="9048a-139">백그라운드 작업으로 실행할 스크립트 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-139">Specifies a script file to run as a background job.</span></span> <span data-ttu-id="9048a-140">스크립트의 경로와 파일 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-140">Enter the path and filename of the script.</span></span> <span data-ttu-id="9048a-141">스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에서 액세스할 수 있는 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-141">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="9048a-142">이 매개 변수를 사용 하는 경우 PowerShell은 지정 된 스크립트 파일의 내용을 스크립트 블록으로 변환 하 고 스크립트 블록을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-142">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9048a-143">-또한 initializationscript</span><span class="sxs-lookup"><span data-stu-id="9048a-143">-InitializationScript</span></span>

<span data-ttu-id="9048a-144">작업을 시작하기 전에 실행되는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-144">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="9048a-145">명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-145">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="9048a-146">이 매개 변수를 사용하여 작업이 실행되는 세션을 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-146">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="9048a-147">예를 들어이를 사용 하 여 함수 및 모듈을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-147">For example, you can use it to add functions and modules to the session.</span></span>

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

### <span data-ttu-id="9048a-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9048a-148">-InputObject</span></span>

<span data-ttu-id="9048a-149">스크립트 블록의 입력으로 사용 되는 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-149">Specifies the objects used as input to the script block.</span></span> <span data-ttu-id="9048a-150">파이프라인 입력도 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-150">It also allows for pipeline input.</span></span> <span data-ttu-id="9048a-151">`$input`스크립트 블록의 자동 변수를 사용 하 여 입력 개체에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-151">Use the `$input` automatic variable in the script block to access the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9048a-152">-Name</span><span class="sxs-lookup"><span data-stu-id="9048a-152">-Name</span></span>

<span data-ttu-id="9048a-153">새 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-153">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="9048a-154">이 이름을 사용 하 여 cmdlet과 같은 다른 작업 cmdlet에 대 한 작업을 식별할 수 있습니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="9048a-154">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="9048a-155">기본 이름은 "Job #" 이며, 여기서 "#"은 각 작업에 대해 증가 하는 서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-155">The default friendly name is "Job#", where "#" is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9048a-156">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="9048a-156">-ScriptBlock</span></span>

<span data-ttu-id="9048a-157">백그라운드 작업에서 실행할 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-157">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="9048a-158">명령을 중괄호 ()로 묶어 `{}` 스크립트 블록을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-158">Enclose the commands in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="9048a-159">`$Input`자동 변수를 사용 하 여 **InputObject** 매개 변수의 값에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-159">Use the `$Input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="9048a-160">이 매개 변수는 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-160">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9048a-161">-StreamingHost</span><span class="sxs-lookup"><span data-stu-id="9048a-161">-StreamingHost</span></span>

<span data-ttu-id="9048a-162">이 매개 변수는 `Write-Host` 출력을 전달 된 **PSHost** 개체로 바로 이동할 수 있는 스레드로부터 안전한 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-162">This parameter provides a thread safe way to allow `Write-Host` output to go directly to the passed in **PSHost** object.</span></span> <span data-ttu-id="9048a-163">이를 사용 하지 않으면 `Write-Host` 출력은 작업 정보 데이터 스트림 컬렉션으로 이동 하 고 작업 실행이 완료 될 때까지 호스트 콘솔에 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-163">Without it, `Write-Host` output goes to the job information data stream collection and doesn't appear in a host console until after the jobs finish running.</span></span>

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9048a-164">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="9048a-164">-ThrottleLimit</span></span>

<span data-ttu-id="9048a-165">이 매개 변수는 한 번에 실행 되는 작업 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-165">This parameter limits the number of jobs running at one time.</span></span> <span data-ttu-id="9048a-166">작업이 시작 되 면 큐에 대기 하 고 스레드 풀에서 스레드를 사용 하 여 작업을 실행할 때까지 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-166">As jobs are started, they are queued and wait until a thread is available in the thread pool to run the job.</span></span> <span data-ttu-id="9048a-167">기본 제한은 5 개의 스레드입니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-167">The default limit is 5 threads.</span></span>

<span data-ttu-id="9048a-168">스레드 풀 크기는 PowerShell 세션의 전역입니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-168">The thread pool size is global to the PowerShell session.</span></span> <span data-ttu-id="9048a-169">한 호출에 **ThrottleLimit** 를 지정 하면 동일한 세션에서 후속 호출에 대 한 제한이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9048a-169">Specifying a **ThrottleLimit** in one call sets the limit for subsequent calls in the same session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9048a-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9048a-170">CommonParameters</span></span>

<span data-ttu-id="9048a-171">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9048a-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9048a-172">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9048a-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9048a-173">입력</span><span class="sxs-lookup"><span data-stu-id="9048a-173">INPUTS</span></span>

### <span data-ttu-id="9048a-174">System.web. PSObject</span><span class="sxs-lookup"><span data-stu-id="9048a-174">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="9048a-175">출력</span><span class="sxs-lookup"><span data-stu-id="9048a-175">OUTPUTS</span></span>

### <span data-ttu-id="9048a-176">ThreadJob. ThreadJob</span><span class="sxs-lookup"><span data-stu-id="9048a-176">ThreadJob.ThreadJob</span></span>

## <span data-ttu-id="9048a-177">참고</span><span class="sxs-lookup"><span data-stu-id="9048a-177">NOTES</span></span>

## <span data-ttu-id="9048a-178">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9048a-178">RELATED LINKS</span></span>

[<span data-ttu-id="9048a-179">Start-Job</span><span class="sxs-lookup"><span data-stu-id="9048a-179">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="9048a-180">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="9048a-180">Stop-Job</span></span>](../Microsoft.PowerShell.Core/Stop-Job.md)

[<span data-ttu-id="9048a-181">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="9048a-181">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)
