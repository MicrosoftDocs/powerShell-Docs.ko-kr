---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 7875419bed68251628b072a35d6c220e75b78c24
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212473"
---
# <span data-ttu-id="dafdb-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="dafdb-103">Start-Job</span></span>

## <span data-ttu-id="dafdb-104">개요</span><span class="sxs-lookup"><span data-stu-id="dafdb-104">SYNOPSIS</span></span>
<span data-ttu-id="dafdb-105">PowerShell 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="dafdb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dafdb-106">SYNTAX</span></span>

### <span data-ttu-id="dafdb-107">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="dafdb-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="dafdb-108">Build.definitionname</span><span class="sxs-lookup"><span data-stu-id="dafdb-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [-WorkingDirectory <String>] [<CommonParameters>]
```

### <span data-ttu-id="dafdb-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="dafdb-109">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="dafdb-110">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="dafdb-110">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>]
 [-WorkingDirectory <String>] [-RunAs32] [-PSVersion <Version>] [-InputObject <PSObject>]
 [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="dafdb-111">설명</span><span class="sxs-lookup"><span data-stu-id="dafdb-111">DESCRIPTION</span></span>

<span data-ttu-id="dafdb-112">`Start-Job`Cmdlet은 로컬 컴퓨터에서 PowerShell 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="dafdb-113">PowerShell 백그라운드 작업은 현재 세션과 상호 작용 하지 않고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="dafdb-114">백그라운드 작업을 시작 하면 작업을 완료 하는 데 오랜 시간이 소요 되는 경우에도 작업 개체가 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="dafdb-115">작업이 실행되는 동안 중단 없이 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="dafdb-116">작업 개체에는 작업에 대 한 유용한 정보가 포함 되어 있지만 작업 결과는 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="dafdb-117">작업이 완료 되 면 cmdlet을 사용 `Receive-Job` 하 여 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="dafdb-118">백그라운드 작업에 대한 자세한 내용은 [about_Jobs](./About/about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="dafdb-119">원격 컴퓨터에서 백그라운드 작업을 실행 하려면 많은 cmdlet에서 사용할 수 있는 **AsJob** 매개 변수를 사용 하거나 cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="dafdb-120">자세한 내용은 [about_Remote_Jobs](./About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="dafdb-121">PowerShell 3.0부터는 `Start-Job` 예약 된 작업과 같은 사용자 지정 작업 유형의 인스턴스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="dafdb-122">를 사용 하 여 사용자 지정 형식으로 작업을 시작 하는 방법에 대 한 자세한 내용은 `Start-Job` 작업 유형 기능에 대 한 도움말 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="dafdb-123">PowerShell 6.0부터 앰퍼샌드 () 백그라운드 연산자를 사용 하 여 작업을 시작할 수 있습니다 `&` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-123">Beginning in PowerShell 6.0, you can start jobs using the ampersand (`&`) background operator.</span></span> <span data-ttu-id="dafdb-124">백그라운드 연산자의 기능은와 비슷합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-124">The functionality of the background operator is similar to `Start-Job`.</span></span> <span data-ttu-id="dafdb-125">작업을 시작 하는 두 가지 방법 모두 **Psremo로 작업** 작업 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-125">Both methods to start a job create a **PSRemotingJob** job object.</span></span> <span data-ttu-id="dafdb-126">앰퍼샌드 ()를 사용 하는 방법에 대 한 자세한 내용은 `&` [about_Operators](./about/about_operators.md#background-operator-)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-126">For more information about using the ampersand (`&`), see [about_Operators](./about/about_operators.md#background-operator-).</span></span>

<span data-ttu-id="dafdb-127">PowerShell 7에는 백그라운드 작업의 초기 작업 디렉터리를 지정 하는 **WorkingDirectory** 매개 변수가 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-127">PowerShell 7 introduced the **WorkingDirectory** parameter that specifies a background job's initial working directory.</span></span> <span data-ttu-id="dafdb-128">매개 변수가 지정 되지 않은 경우는 기본적으로 `Start-Job` 작업을 시작한 호출자의 현재 작업 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-128">If the parameter isn't specified, `Start-Job` defaults to the current working directory of the caller that started the job.</span></span>

> [!NOTE]
> <span data-ttu-id="dafdb-129">Powershell `Start-Job` Azure Functions와 같은 다른 응용 프로그램에서 powershell을 호스팅하는 시나리오에서는를 사용 하 여 out-of-process 백그라운드 작업을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-129">Creating an out-of-process background job with `Start-Job` is not supported in the scenario where PowerShell is being hosted in other applications, such as the PowerShell Azure Functions.</span></span>
>
> <span data-ttu-id="dafdb-130">이것은 `Start-Job` `pwsh` 에서 사용할 수 있는 실행 파일을 사용 하 여 out-of-process 백그라운드 작업을 시작 하기 때문에 의도 된 것 `$PSHOME` 이지만 응용 프로그램이 powershell을 호스트 하는 경우 powershell NuGet SDK 패키지를 직접 사용 하는 것 이며 `pwsh` 함께 제공 되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-130">This is by design because `Start-Job` depends on the `pwsh` executable to be available under `$PSHOME` to start an out-of-process background job, but when an application is hosting PowerShell, it's directly using the PowerShell NuGet SDK packages and won't have `pwsh` shipped along.</span></span>
>
> <span data-ttu-id="dafdb-131">해당 시나리오의 대체는 `Start-ThreadJob` 모듈 **[threadjob](https://www.powershellgallery.com/packages/ThreadJob)** 에서 가져온 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-131">The substitute in that scenario is `Start-ThreadJob` from the module **[ThreadJob](https://www.powershellgallery.com/packages/ThreadJob)** .</span></span>

## <span data-ttu-id="dafdb-132">예제</span><span class="sxs-lookup"><span data-stu-id="dafdb-132">EXAMPLES</span></span>

### <span data-ttu-id="dafdb-133">예제 1: 백그라운드 작업 시작</span><span class="sxs-lookup"><span data-stu-id="dafdb-133">Example 1: Start a background job</span></span>

<span data-ttu-id="dafdb-134">이 예제에서는 로컬 컴퓨터에서 실행 되는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-134">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name pwsh }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name pwsh
```

<span data-ttu-id="dafdb-135">`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Process` 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-135">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="dafdb-136">**Name** 매개 변수는 PowerShell 프로세스를 찾도록 지정 합니다 `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-136">The **Name** parameter specifies to find PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="dafdb-137">작업 정보가 표시 되 고 백그라운드에서 작업이 실행 되는 동안 PowerShell에서 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-137">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="dafdb-138">작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-138">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="dafdb-139">예들 들어 `Receive-Job -Id 1`입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-139">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="dafdb-140">예 2: background 연산자를 사용 하 여 백그라운드 작업 시작</span><span class="sxs-lookup"><span data-stu-id="dafdb-140">Example 2: Use the background operator to start a background job</span></span>

<span data-ttu-id="dafdb-141">이 예에서는 앰퍼샌드 ( `&` ) 백그라운드 연산자를 사용 하 여 로컬 컴퓨터에서 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-141">This example uses the ampersand (`&`) background operator to start a background job on the local computer.</span></span> <span data-ttu-id="dafdb-142">작업은 예제 1과 동일한 결과를 가져옵니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-142">The job gets the same result as `Start-Job` in Example 1.</span></span>

```powershell
Get-Process -Name pwsh &
```

```Output
Id    Name   PSJobTypeName   State       HasMoreData     Location      Command
--    ----   -------------   -----       -----------     --------      -------
5     Job5   BackgroundJob   Running     True            localhost     Microsoft.PowerShell.Man...
```

<span data-ttu-id="dafdb-143">`Get-Process`**Name** 매개 변수를 사용 하 여 PowerShell 프로세스를 지정 `pwsh` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-143">`Get-Process` uses the **Name** parameter to specify PowerShell processes, `pwsh`.</span></span> <span data-ttu-id="dafdb-144">앰퍼샌드 ( `&` )는 명령을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-144">The ampersand (`&`) runs the command as a background job.</span></span> <span data-ttu-id="dafdb-145">작업 정보가 표시 되 고 백그라운드에서 작업이 실행 되는 동안 PowerShell에서 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-145">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="dafdb-146">작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-146">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="dafdb-147">예들 들어 `Receive-Job -Id 5`입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-147">For example, `Receive-Job -Id 5`.</span></span>

### <span data-ttu-id="dafdb-148">예 3: Invoke-Command을 사용 하 여 작업 시작</span><span class="sxs-lookup"><span data-stu-id="dafdb-148">Example 3: Start a job using Invoke-Command</span></span>

<span data-ttu-id="dafdb-149">이 예제에서는 여러 컴퓨터에서 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-149">This example runs a job on multiple computers.</span></span> <span data-ttu-id="dafdb-150">작업은 변수에 저장 되며 PowerShell 명령줄에서 변수 이름을 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-150">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="dafdb-151">를 사용 하는 작업 `Invoke-Command` 은 변수에 생성 되어 저장 됩니다 `$jobWRM` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-151">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="dafdb-152">`Invoke-Command`**ComputerName** 매개 변수를 사용 하 여 작업이 실행 되는 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-152">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="dafdb-153">`Get-Content` 파일에서 서버 이름을 가져옵니다 `C:\Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-153">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="dafdb-154">**ScriptBlock** 매개 변수는 `Get-Service` **WinRM** 서비스를 가져오는 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-154">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="dafdb-155">**JobName** 매개 변수는 작업의 친숙 한 이름 ( **WinRM** )을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-155">The **JobName** parameter specifies a friendly name for the job, **WinRM** .</span></span> <span data-ttu-id="dafdb-156">**ThrottleLimit** 매개 변수는 동시 명령 수를 16으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-156">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="dafdb-157">**AsJob** 매개 변수는 서버에서 명령을 실행 하는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-157">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="dafdb-158">예제 4: 작업 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="dafdb-158">Example 4: Get job information</span></span>

<span data-ttu-id="dafdb-159">이 예에서는 작업에 대 한 정보를 가져오고 로컬 컴퓨터에서 실행 된 완료 된 작업의 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-159">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

```powershell
$j = Start-Job -ScriptBlock { Get-WinEvent -Log System } -Credential Domain01\User01
$j | Select-Object -Property *
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-WinEvent -Log System
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : 27ce3fd9-40ed-488a-99e5-679cd91b9dd3
Id            : 18
Name          : Job18
ChildJobs     : {Job19}
PSBeginTime   : 8/8/2019 14:41:57
PSEndTime     : 8/8/2019 14:42:07
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="dafdb-160">`Start-Job` 는 **ScriptBlock** 매개 변수를 사용 하 여 `Get-WinEvent` **시스템** 로그를 가져오도록를 지정 하는 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-160">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="dafdb-161">**Credential** 매개 변수는 컴퓨터에서 작업을 실행할 수 있는 권한이 있는 도메인 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-161">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="dafdb-162">작업 개체는 변수에 저장 됩니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-162">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="dafdb-163">변수의 개체는 `$j` 파이프라인에서로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-163">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="dafdb-164">**Property** 매개 변수는 `*` 모든 작업 개체의 속성을 표시 하는 별표 ()를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-164">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="dafdb-165">예 5: 백그라운드 작업으로 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="dafdb-165">Example 5: Run a script as a background job</span></span>

<span data-ttu-id="dafdb-166">이 예에서는 로컬 컴퓨터의 스크립트가 백그라운드 작업으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-166">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="dafdb-167">`Start-Job`**FilePath** 매개 변수를 사용 하 여 로컬 컴퓨터에 저장 된 스크립트 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-167">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="dafdb-168">예제 6: 백그라운드 작업을 사용 하 여 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="dafdb-168">Example 6: Get a process using a background job</span></span>

<span data-ttu-id="dafdb-169">이 예제에서는 백그라운드 작업을 사용 하 여 지정 된 프로세스를 이름으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-169">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="dafdb-170">`Start-Job`**name** 매개 변수를 사용 하 여 친숙 한 작업 이름 **pshelljob** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-170">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob** .</span></span> <span data-ttu-id="dafdb-171">**ScriptBlock** 매개 변수는 `Get-Process` 이름이 **PowerShell** 인 프로세스를 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-171">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell** .</span></span>

### <span data-ttu-id="dafdb-172">예 7: 백그라운드 작업을 사용 하 여 데이터 수집 및 저장</span><span class="sxs-lookup"><span data-stu-id="dafdb-172">Example 7: Collect and save data by using a background job</span></span>

<span data-ttu-id="dafdb-173">이 예에서는 많은 양의 지도 데이터를 수집 하 여 파일에 저장 하는 작업을 시작 `.tif` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-173">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif }
```

<span data-ttu-id="dafdb-174">`Start-Job`**name** 매개 변수를 사용 하 여 친숙 한 작업 이름인 **GetMappingFiles** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-174">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles** .</span></span> <span data-ttu-id="dafdb-175">**또한 initializationscript** 매개 변수는 **mapfunctions** 모듈을 가져오는 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-175">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="dafdb-176">**ScriptBlock** 매개 변수는 `Get-Map` `Set-Content` **Path** 매개 변수에서 지정한 위치에 데이터를 실행 하 고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-176">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span>

### <span data-ttu-id="dafdb-177">예 8: 백그라운드 작업에 입력 전달</span><span class="sxs-lookup"><span data-stu-id="dafdb-177">Example 8: Pass input to a background job</span></span>

<span data-ttu-id="dafdb-178">이 예에서는 자동 변수를 사용 하 여 `$input` 입력 개체를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-178">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="dafdb-179">`Receive-Job`를 사용 하 여 작업의 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-179">Use `Receive-Job` to view the job's output.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Content $input } -InputObject "C:\Servers.txt"
Receive-Job -Name Job45 -Keep
```

```Output
Server01
Server02
Server03
Server04
```

<span data-ttu-id="dafdb-180">`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Content` `$input` 자동 변수와 함께 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-180">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="dafdb-181">`$input`변수는 **InputObject** 매개 변수에서 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-181">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="dafdb-182">`Receive-Job`**Name** 매개 변수를 사용 하 여 작업을 지정 하 고 결과를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-182">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="dafdb-183">**Keep** 매개 변수는 PowerShell 세션 중에 다시 볼 수 있도록 작업 출력을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-183">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="dafdb-184">예 9: 백그라운드 작업에 대 한 작업 디렉터리 설정</span><span class="sxs-lookup"><span data-stu-id="dafdb-184">Example 9: Set the working directory for a background job</span></span>

<span data-ttu-id="dafdb-185">**WorkingDirectory** 를 사용 하면 스크립트를 실행 하거나 파일을 열 수 있는 작업에 대 한 대체 디렉터리를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-185">The **WorkingDirectory** allows you to specify an alternate directory for a job from which you can run scripts or open files.</span></span> <span data-ttu-id="dafdb-186">이 예제에서 백그라운드 작업은 현재 디렉터리 위치와 다른 작업 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-186">In this example, the background job specifies a working directory that's different than the current directory location.</span></span>

```
PS C:\Test> Start-Job -WorkingDirectory C:\Test\Scripts { $PWD } | Receive-Job -AutoRemoveJob -Wait

Path
----
C:\Test\Scripts
```

<span data-ttu-id="dafdb-187">이 예제의 현재 작업 디렉터리는 `C:\Test` 입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-187">This example's current working directory is `C:\Test`.</span></span> <span data-ttu-id="dafdb-188">`Start-Job`**WorkingDirectory** 매개 변수를 사용 하 여 작업의 작업 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-188">`Start-Job` uses the **WorkingDirectory** parameter to specify the job's working directory.</span></span> <span data-ttu-id="dafdb-189">**ScriptBlock** 매개 변수는 `$PWD` 를 사용 하 여 작업의 작업 디렉터리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-189">The **ScriptBlock** parameter uses `$PWD` to display the job's working directory.</span></span> <span data-ttu-id="dafdb-190">`Receive-Job` 백그라운드 작업의 출력을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-190">`Receive-Job` displays the background job's output.</span></span>
<span data-ttu-id="dafdb-191">**AutoRemoveJob** 는 작업을 삭제 하 고 **Wait** 는 모든 결과가 수신 될 때까지 명령 프롬프트를 표시 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-191">**AutoRemoveJob** deletes the job and **Wait** suppresses the command prompt until all results are received.</span></span>

### <span data-ttu-id="dafdb-192">예 10: ArgumentList 매개 변수를 사용 하 여 배열 지정</span><span class="sxs-lookup"><span data-stu-id="dafdb-192">Example 10: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="dafdb-193">이 예제에서는 **Argumentlist** 매개 변수를 사용 하 여 인수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-193">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="dafdb-194">배열은 쉼표로 구분 된 프로세스 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-194">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="dafdb-195">`Start-Job`Cmdlet은 **ScriptBlock** 매개 변수를 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-195">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="dafdb-196">`Get-Process`**Name** 매개 변수를 사용 하 여 자동 변수를 지정 합니다 `$args` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-196">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="dafdb-197">**Argumentlist** 매개 변수는 프로세스 이름 배열을에 전달 `$args` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-197">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="dafdb-198">Powershell, pwsh 및 notepad 프로세스 이름은 로컬 컴퓨터에서 실행 되는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-198">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="dafdb-199">작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-199">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="dafdb-200">예들 들어 `Receive-Job -Id 1`입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-200">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="dafdb-201">예 11: Windows PowerShell 5.1에서 작업 실행</span><span class="sxs-lookup"><span data-stu-id="dafdb-201">Example 11: Run job in a Windows PowerShell 5.1</span></span>

<span data-ttu-id="dafdb-202">이 예제에서는 값이 **5.1** 인 **PSVersion** 매개 변수를 사용 하 여 Windows PowerShell 5.1 세션에서 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-202">This example uses the **PSVersion** parameter with value **5.1** to run job in a Windows PowerShell 5.1 session.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Patch  PreReleaseLabel BuildLabel
-----  -----  -----  --------------- ----------
7      0      0      rc.1
```

```powershell
$job = Start-Job { $PSVersionTable.PSVersion } -PSVersion 5.1
Receive-Job $job
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  3383
```

## <span data-ttu-id="dafdb-203">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="dafdb-203">PARAMETERS</span></span>

### <span data-ttu-id="dafdb-204">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="dafdb-204">-ArgumentList</span></span>

<span data-ttu-id="dafdb-205">**FilePath** 매개 변수로 지정 된 스크립트 또는 **ScriptBlock** 매개 변수를 사용 하 여 지정 된 명령에 대 한 인수 또는 매개 변수 값의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-205">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="dafdb-206">인수는 **Argumentlist** 에 단일 차원 배열 인수로 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-206">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="dafdb-207">예를 들어 쉼표로 구분 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-207">For example, a comma-separated list.</span></span> <span data-ttu-id="dafdb-208">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-208">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-209">-인증</span><span class="sxs-lookup"><span data-stu-id="dafdb-209">-Authentication</span></span>

<span data-ttu-id="dafdb-210">사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-210">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="dafdb-211">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-211">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="dafdb-212">기본값</span><span class="sxs-lookup"><span data-stu-id="dafdb-212">Default</span></span>
- <span data-ttu-id="dafdb-213">Basic</span><span class="sxs-lookup"><span data-stu-id="dafdb-213">Basic</span></span>
- <span data-ttu-id="dafdb-214">Credssp</span><span class="sxs-lookup"><span data-stu-id="dafdb-214">Credssp</span></span>
- <span data-ttu-id="dafdb-215">다이제스트</span><span class="sxs-lookup"><span data-stu-id="dafdb-215">Digest</span></span>
- <span data-ttu-id="dafdb-216">Kerberos</span><span class="sxs-lookup"><span data-stu-id="dafdb-216">Kerberos</span></span>
- <span data-ttu-id="dafdb-217">Negotiate</span><span class="sxs-lookup"><span data-stu-id="dafdb-217">Negotiate</span></span>
- <span data-ttu-id="dafdb-218">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="dafdb-218">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="dafdb-219">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-219">The default value is Default.</span></span>

<span data-ttu-id="dafdb-220">CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-220">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="dafdb-221">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="dafdb-221">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="dafdb-222">사용자의 자격 증명이 인증을 위해 원격 컴퓨터로 전달되는 CredSSP(자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스에서 인증이 필요한 명령(예: 원격 네트워크 공유 액세스)에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-222">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="dafdb-223">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-223">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="dafdb-224">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-224">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-225">-Credential</span><span class="sxs-lookup"><span data-stu-id="dafdb-225">-Credential</span></span>

<span data-ttu-id="dafdb-226">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-226">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="dafdb-227">**Credential** 매개 변수를 지정 하지 않으면 명령은 현재 사용자의 자격 증명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-227">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="dafdb-228">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-228">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="dafdb-229">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-229">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="dafdb-230">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-230">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="dafdb-231">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="dafdb-231">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-232">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="dafdb-232">-DefinitionName</span></span>

<span data-ttu-id="dafdb-233">이 cmdlet이 시작 하는 작업의 정의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-233">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="dafdb-234">이 매개 변수를 사용하여 예약된 작업과 같이 정의 이름이 있는 사용자 지정 작업 유형을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-234">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="dafdb-235">`Start-Job`를 사용 하 여 예약 된 작업의 인스턴스를 시작 하면 작업 트리거 또는 작업 옵션에 관계 없이 작업이 즉시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-235">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="dafdb-236">결과 작업 인스턴스는 예약 된 작업 이지만 트리거된 예약 된 작업 처럼 디스크에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-236">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="dafdb-237">의 **Argumentlist** 매개 변수를 사용 `Start-Job` 하 여 예약 된 작업에서 실행 되는 스크립트의 매개 변수에 대 한 값을 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-237">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span>

<span data-ttu-id="dafdb-238">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-238">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="dafdb-239">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="dafdb-239">-DefinitionPath</span></span>

<span data-ttu-id="dafdb-240">이 cmdlet이 시작 되는 작업 정의의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-240">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="dafdb-241">정의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-241">Enter the definition path.</span></span> <span data-ttu-id="dafdb-242">**Definitionpath** 및 **definitionpath** 매개 변수의 값 연결은 작업 정의의 정규화 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-242">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="dafdb-243">이 매개 변수를 사용하여 예약된 작업과 같이 정의 경로가 있는 사용자 지정 작업 유형을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-243">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="dafdb-244">예약 된 작업의 경우 **Definitionpath** 매개 변수의 값은 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-244">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="dafdb-245">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-245">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-246">-FilePath</span><span class="sxs-lookup"><span data-stu-id="dafdb-246">-FilePath</span></span>

<span data-ttu-id="dafdb-247">백그라운드 작업으로 실행 되는 로컬 스크립트를 지정 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-247">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="dafdb-248">스크립트의 경로와 파일 이름을 입력 하거나 파이프라인을 사용 하 여 스크립트 경로를로 보냅니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-248">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="dafdb-249">스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에서 액세스할 수 있는 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-249">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="dafdb-250">이 매개 변수를 사용 하는 경우 PowerShell은 지정 된 스크립트 파일의 내용을 스크립트 블록으로 변환 하 고 스크립트 블록을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-250">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePathComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-251">-또한 initializationscript</span><span class="sxs-lookup"><span data-stu-id="dafdb-251">-InitializationScript</span></span>

<span data-ttu-id="dafdb-252">작업을 시작하기 전에 실행되는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-252">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="dafdb-253">스크립트 블록을 만들려면 명령을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-253">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="dafdb-254">이 매개 변수를 사용하여 작업이 실행되는 세션을 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-254">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="dafdb-255">예를 들어 이 매개 변수를 사용하여 함수, 스냅인 및 모듈을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-255">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-256">-InputObject</span><span class="sxs-lookup"><span data-stu-id="dafdb-256">-InputObject</span></span>

<span data-ttu-id="dafdb-257">명령에 대한 입력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-257">Specifies input to the command.</span></span> <span data-ttu-id="dafdb-258">개체가 포함된 변수를 입력하거나 개체를 생성하는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-258">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="dafdb-259">**ScriptBlock** 매개 변수 값에서 `$input` 자동 변수를 사용 하 여 입력 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-259">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-260">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="dafdb-260">-LiteralPath</span></span>

<span data-ttu-id="dafdb-261">이 cmdlet이 백그라운드 작업으로 실행 되는 로컬 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-261">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="dafdb-262">로컬 컴퓨터에서 스크립트의 경로를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-262">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="dafdb-263">`Start-Job`**LiteralPath** 매개 변수의 값을 입력 된 대로 정확 하 게 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-263">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="dafdb-264">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-264">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="dafdb-265">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-265">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="dafdb-266">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-266">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-267">-Name</span><span class="sxs-lookup"><span data-stu-id="dafdb-267">-Name</span></span>

<span data-ttu-id="dafdb-268">새 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-268">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="dafdb-269">이 이름을 사용 하 여 cmdlet과 같은 다른 작업 cmdlet에 대 한 작업을 식별할 수 있습니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-269">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="dafdb-270">기본 이름은 이며 `Job#` , 여기서 `#` 은 각 작업에 대해 증가 하는 서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-270">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-271">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="dafdb-271">-PSVersion</span></span>

<span data-ttu-id="dafdb-272">작업을 실행 하는 데 사용할 PowerShell 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-272">Specifies a version of PowerShell to use for running the job.</span></span>
<span data-ttu-id="dafdb-273">**PSVersion** 의 값이 **5.1** 인 경우 작업이 Windows PowerShell 5.1 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-273">When the value of **PSVersion** is **5.1** The job is run in a Windows PowerShell 5.1 session.</span></span>
<span data-ttu-id="dafdb-274">다른 값의 경우에는 현재 버전의 PowerShell을 사용 하 여 작업이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-274">For any other value, the job is run using the current version of PowerShell.</span></span>

<span data-ttu-id="dafdb-275">이 매개 변수는 PowerShell 7에서 추가 되었으며 Windows 에서만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-275">This parameter was added in PowerShell 7 and only works on Windows.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-276">-체제가 있어도 runas32</span><span class="sxs-lookup"><span data-stu-id="dafdb-276">-RunAs32</span></span>

<span data-ttu-id="dafdb-277">PowerShell 7부터 **체제가 있어도 runas32** 매개 변수는 64 비트 PowerShell ()에서 작동 하지 않습니다 `pwsh` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-277">Beginning with PowerShell 7, the **RunAs32** parameter doesn't work on 64-bit PowerShell (`pwsh`).</span></span>
<span data-ttu-id="dafdb-278">**체제가 있어도 runas32** 이 64 비트 PowerShell에 지정 된 경우에서 `Start-Job` 종료 예외 오류를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-278">If **RunAs32** is specified in 64-bit PowerShell, `Start-Job` throws a terminating exception error.</span></span>
<span data-ttu-id="dafdb-279">체제가 있어도 runas32를 사용 하 여 32 비트 PowerShell ( `pwsh` ) 프로세스 **RunAs32** 를 시작 하려면 32 비트 powershell이 설치 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-279">To start a 32-bit PowerShell (`pwsh`) process with **RunAs32** , you need to have the 32-bit PowerShell installed.</span></span>

<span data-ttu-id="dafdb-280">32 비트 PowerShell에서 **체제가 있어도 runas32** 은 64 비트 운영 체제 에서도 강제로 32 비트 프로세스에서 작업을 실행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-280">In 32-bit PowerShell, **RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="dafdb-281">64 비트 버전의 Windows 7 및 Windows Server 2008 r 2에서 `Start-Job` 명령에 **체제가 있어도 runas32** 매개 변수가 포함 된 경우 **Credential** 매개 변수를 사용 하 여 다른 사용자의 자격 증명을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-281">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, FilePathComputerName, LiteralFilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-282">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="dafdb-282">-ScriptBlock</span></span>

<span data-ttu-id="dafdb-283">백그라운드 작업에서 실행할 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-283">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="dafdb-284">스크립트 블록을 만들려면 명령을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-284">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="dafdb-285">`$input`자동 변수를 사용 하 여 **InputObject** 매개 변수의 값에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-285">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="dafdb-286">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-286">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName
Aliases: Command

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-287">-Type</span><span class="sxs-lookup"><span data-stu-id="dafdb-287">-Type</span></span>

<span data-ttu-id="dafdb-288">에서 시작한 작업의 사용자 지정 형식을 지정 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-288">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="dafdb-289">사용자 지정 작업 유형 이름(예: 예약된 작업의 경우 PSScheduledJob 또는 워크플로 작업의 경우 PSWorkflowJob)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-289">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="dafdb-290">이 매개 변수는 표준 백그라운드 작업에 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-290">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="dafdb-291">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-291">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: DefinitionName
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-292">-WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="dafdb-292">-WorkingDirectory</span></span>

<span data-ttu-id="dafdb-293">백그라운드 작업의 초기 작업 디렉터리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-293">Specifies the initial working directory of the background job.</span></span> <span data-ttu-id="dafdb-294">매개 변수가 지정 되지 않은 경우 작업은 기본 위치에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-294">If the parameter isn't specified, the job runs from the default location.</span></span> <span data-ttu-id="dafdb-295">기본 위치는 작업을 시작한 호출자의 현재 작업 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-295">The default location is the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="dafdb-296">이 매개 변수는 PowerShell 7에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-296">This parameter was introduced in PowerShell 7.</span></span>

```yaml
Type: System.String
Parameter Sets: All
Aliases:

Required: False
Position: Named
Default value: $HOME on Unix (macOS, Linux) and $HOME\Documents on Windows
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dafdb-297">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dafdb-297">CommonParameters</span></span>

<span data-ttu-id="dafdb-298">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dafdb-298">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dafdb-299">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dafdb-299">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dafdb-300">입력</span><span class="sxs-lookup"><span data-stu-id="dafdb-300">INPUTS</span></span>

### <span data-ttu-id="dafdb-301">System.String</span><span class="sxs-lookup"><span data-stu-id="dafdb-301">System.String</span></span>

<span data-ttu-id="dafdb-302">파이프라인을 사용 하 여 **name** 속성이 있는 개체를 **name** 매개 변수로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-302">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="dafdb-303">예를 들어, **FileInfo** 개체를에서로 파이프라인 할 수 있습니다 `Get-ChildItem` `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="dafdb-303">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="dafdb-304">출력</span><span class="sxs-lookup"><span data-stu-id="dafdb-304">OUTPUTS</span></span>

### <span data-ttu-id="dafdb-305">System.web. a p.</span><span class="sxs-lookup"><span data-stu-id="dafdb-305">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="dafdb-306">`Start-Job` 시작 된 작업을 나타내는 **Psremotingjob** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-306">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="dafdb-307">참고</span><span class="sxs-lookup"><span data-stu-id="dafdb-307">NOTES</span></span>

<span data-ttu-id="dafdb-308">백그라운드에서 실행 하려면는 `Start-Job` 현재 세션에서 자체 세션으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-308">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="dafdb-309">Cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터의 세션에서 명령을 실행할 경우는 `Start-Job` 원격 세션의 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dafdb-309">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="dafdb-310">관련 링크</span><span class="sxs-lookup"><span data-stu-id="dafdb-310">RELATED LINKS</span></span>

[<span data-ttu-id="dafdb-311">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="dafdb-311">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="dafdb-312">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="dafdb-312">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="dafdb-313">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="dafdb-313">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="dafdb-314">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="dafdb-314">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="dafdb-315">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="dafdb-315">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="dafdb-316">Get-Job</span><span class="sxs-lookup"><span data-stu-id="dafdb-316">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="dafdb-317">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="dafdb-317">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="dafdb-318">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="dafdb-318">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="dafdb-319">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="dafdb-319">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="dafdb-320">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="dafdb-320">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="dafdb-321">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="dafdb-321">Wait-Job</span></span>](Wait-Job.md)
