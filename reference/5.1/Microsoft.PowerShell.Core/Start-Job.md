---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/start-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Job
ms.openlocfilehash: 116e007cc28a91e3c97fd980cc27461932390b7c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93212737"
---
# <span data-ttu-id="53de4-103">Start-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-103">Start-Job</span></span>

## <span data-ttu-id="53de4-104">개요</span><span class="sxs-lookup"><span data-stu-id="53de4-104">SYNOPSIS</span></span>
<span data-ttu-id="53de4-105">PowerShell 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-105">Starts a PowerShell background job.</span></span>

## <span data-ttu-id="53de4-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="53de4-106">SYNTAX</span></span>

### <span data-ttu-id="53de4-107">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="53de4-107">ComputerName (Default)</span></span>

```
Start-Job [-Name <String>] [-ScriptBlock] <ScriptBlock> [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="53de4-108">Build.definitionname</span><span class="sxs-lookup"><span data-stu-id="53de4-108">DefinitionName</span></span>

```
Start-Job [-DefinitionName] <String> [[-DefinitionPath] <String>] [[-Type] <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="53de4-109">FilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="53de4-109">FilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] [-FilePath] <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

### <span data-ttu-id="53de4-110">LiteralFilePathComputerName</span><span class="sxs-lookup"><span data-stu-id="53de4-110">LiteralFilePathComputerName</span></span>

```
Start-Job [-Name <String>] [-Credential <PSCredential>] -LiteralPath <String>
 [-Authentication <AuthenticationMechanism>] [[-InitializationScript] <ScriptBlock>] [-RunAs32]
 [-PSVersion <Version>] [-InputObject <PSObject>] [-ArgumentList <Object[]>] [<CommonParameters>]
```

## <span data-ttu-id="53de4-111">설명</span><span class="sxs-lookup"><span data-stu-id="53de4-111">DESCRIPTION</span></span>

<span data-ttu-id="53de4-112">`Start-Job`Cmdlet은 로컬 컴퓨터에서 PowerShell 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-112">The `Start-Job` cmdlet starts a PowerShell background job on the local computer.</span></span>

<span data-ttu-id="53de4-113">PowerShell 백그라운드 작업은 현재 세션과 상호 작용 하지 않고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-113">A PowerShell background job runs a command without interacting with the current session.</span></span> <span data-ttu-id="53de4-114">백그라운드 작업을 시작 하면 작업을 완료 하는 데 오랜 시간이 소요 되는 경우에도 작업 개체가 즉시 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-114">When you start a background job, a job object returns immediately, even if the job takes an extended time to finish.</span></span> <span data-ttu-id="53de4-115">작업이 실행되는 동안 중단 없이 세션에서 작업을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-115">You can continue to work in the session without interruption while the job runs.</span></span>

<span data-ttu-id="53de4-116">작업 개체에는 작업에 대 한 유용한 정보가 포함 되어 있지만 작업 결과는 포함 되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-116">The job object contains useful information about the job, but it doesn't contain the job results.</span></span>
<span data-ttu-id="53de4-117">작업이 완료 되 면 cmdlet을 사용 `Receive-Job` 하 여 작업의 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-117">When the job finishes, use the `Receive-Job` cmdlet to get the results of the job.</span></span> <span data-ttu-id="53de4-118">백그라운드 작업에 대한 자세한 내용은 [about_Jobs](./About/about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-118">For more information about background jobs, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="53de4-119">원격 컴퓨터에서 백그라운드 작업을 실행 하려면 많은 cmdlet에서 사용할 수 있는 **AsJob** 매개 변수를 사용 하거나 cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-119">To run a background job on a remote computer, use the **AsJob** parameter that is available on many cmdlets, or use the `Invoke-Command` cmdlet to run a `Start-Job` command on the remote computer.</span></span> <span data-ttu-id="53de4-120">자세한 내용은 [about_Remote_Jobs](./About/about_Remote_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-120">For more information, see [about_Remote_Jobs](./About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="53de4-121">PowerShell 3.0부터는 `Start-Job` 예약 된 작업과 같은 사용자 지정 작업 유형의 인스턴스를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-121">Starting in PowerShell 3.0, `Start-Job` can start instances of custom job types, such as scheduled jobs.</span></span> <span data-ttu-id="53de4-122">를 사용 하 여 사용자 지정 형식으로 작업을 시작 하는 방법에 대 한 자세한 내용은 `Start-Job` 작업 유형 기능에 대 한 도움말 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-122">For information about how to use `Start-Job` to start jobs with custom types, see the help documents for the job type feature.</span></span>

<span data-ttu-id="53de4-123">작업의 기본 작업 디렉터리는 하드 코딩 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-123">The default working directory for jobs is hardcoded.</span></span> <span data-ttu-id="53de4-124">Windows 기본값은 `$HOME\Documents` 및 Linux 또는 macOS에서입니다. 기본값은 `$HOME` 입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-124">The Windows default is `$HOME\Documents` and on Linux or macOS the default is `$HOME`.</span></span> <span data-ttu-id="53de4-125">백그라운드 작업에서 실행 되는 스크립트 코드는 필요에 따라 작업 디렉터리를 관리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-125">The script code running in the background job needs to manage the working directory as needed.</span></span>

## <span data-ttu-id="53de4-126">예제</span><span class="sxs-lookup"><span data-stu-id="53de4-126">EXAMPLES</span></span>

### <span data-ttu-id="53de4-127">예제 1: 백그라운드 작업 시작</span><span class="sxs-lookup"><span data-stu-id="53de4-127">Example 1: Start a background job</span></span>

<span data-ttu-id="53de4-128">이 예제에서는 로컬 컴퓨터에서 실행 되는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-128">This example starts a background job that runs on the local computer.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name powershell }
```

```Output
Id  Name   PSJobTypeName   State     HasMoreData   Location    Command
--  ----   -------------   -----     -----------   --------    -------
1   Job1   BackgroundJob   Running   True          localhost   Get-Process -Name powershell
```

<span data-ttu-id="53de4-129">`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Process` 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-129">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Process` as a background job.</span></span> <span data-ttu-id="53de4-130">**Name** 매개 변수는 PowerShell 프로세스를 찾도록 지정 합니다 `powershell` .</span><span class="sxs-lookup"><span data-stu-id="53de4-130">The **Name** parameter specifies to find PowerShell processes, `powershell`.</span></span> <span data-ttu-id="53de4-131">작업 정보가 표시 되 고 백그라운드에서 작업이 실행 되는 동안 PowerShell에서 프롬프트로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-131">The job information is displayed and PowerShell returns to a prompt while the job runs in the background.</span></span>

<span data-ttu-id="53de4-132">작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-132">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="53de4-133">예들 들어 `Receive-Job -Id 1`입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-133">For example, `Receive-Job -Id 1`.</span></span>

### <span data-ttu-id="53de4-134">예 2: Invoke-Command을 사용 하 여 작업 시작</span><span class="sxs-lookup"><span data-stu-id="53de4-134">Example 2: Start a job using Invoke-Command</span></span>

<span data-ttu-id="53de4-135">이 예제에서는 여러 컴퓨터에서 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-135">This example runs a job on multiple computers.</span></span> <span data-ttu-id="53de4-136">작업은 변수에 저장 되며 PowerShell 명령줄에서 변수 이름을 사용 하 여 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-136">The job is stored in a variable and is executed by using the variable name on the PowerShell command line.</span></span>

```powershell
$jobWRM = Invoke-Command -ComputerName (Get-Content -Path C:\Servers.txt) -ScriptBlock {
   Get-Service -Name WinRM } -JobName WinRM -ThrottleLimit 16 -AsJob
```

<span data-ttu-id="53de4-137">를 사용 하는 작업 `Invoke-Command` 은 변수에 생성 되어 저장 됩니다 `$jobWRM` .</span><span class="sxs-lookup"><span data-stu-id="53de4-137">A job that uses `Invoke-Command` is created and stored in the `$jobWRM` variable.</span></span> <span data-ttu-id="53de4-138">`Invoke-Command`**ComputerName** 매개 변수를 사용 하 여 작업이 실행 되는 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-138">`Invoke-Command` uses the **ComputerName** parameter to specify the computers where the job runs.</span></span> <span data-ttu-id="53de4-139">`Get-Content` 파일에서 서버 이름을 가져옵니다 `C:\Servers.txt` .</span><span class="sxs-lookup"><span data-stu-id="53de4-139">`Get-Content` gets the server names from the `C:\Servers.txt` file.</span></span>

<span data-ttu-id="53de4-140">**ScriptBlock** 매개 변수는 `Get-Service` **WinRM** 서비스를 가져오는 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-140">The **ScriptBlock** parameter specifies a command that `Get-Service` gets the **WinRM** service.</span></span> <span data-ttu-id="53de4-141">**JobName** 매개 변수는 작업의 친숙 한 이름 ( **WinRM** )을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-141">The **JobName** parameter specifies a friendly name for the job, **WinRM** .</span></span> <span data-ttu-id="53de4-142">**ThrottleLimit** 매개 변수는 동시 명령 수를 16으로 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-142">The **ThrottleLimit** parameter limits the number of concurrent commands to 16.</span></span> <span data-ttu-id="53de4-143">**AsJob** 매개 변수는 서버에서 명령을 실행 하는 백그라운드 작업을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-143">The **AsJob** parameter starts a background job that runs the command on the servers.</span></span>

### <span data-ttu-id="53de4-144">예제 3: 작업 정보 가져오기</span><span class="sxs-lookup"><span data-stu-id="53de4-144">Example 3: Get job information</span></span>

<span data-ttu-id="53de4-145">이 예에서는 작업에 대 한 정보를 가져오고 로컬 컴퓨터에서 실행 된 완료 된 작업의 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-145">This example gets information about a job and displays the results of a completed job that was run on the local computer.</span></span>

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

<span data-ttu-id="53de4-146">`Start-Job` 는 **ScriptBlock** 매개 변수를 사용 하 여 `Get-WinEvent` **시스템** 로그를 가져오도록를 지정 하는 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-146">`Start-Job` uses the **ScriptBlock** parameter to run a command that specifies `Get-WinEvent` to get the **System** log.</span></span> <span data-ttu-id="53de4-147">**Credential** 매개 변수는 컴퓨터에서 작업을 실행할 수 있는 권한이 있는 도메인 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-147">The **Credential** parameter specifies a domain user account with permission to run the job on the computer.</span></span> <span data-ttu-id="53de4-148">작업 개체는 변수에 저장 됩니다 `$j` .</span><span class="sxs-lookup"><span data-stu-id="53de4-148">The job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="53de4-149">변수의 개체는 `$j` 파이프라인에서로 전송 됩니다 `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="53de4-149">The object in the `$j` variable is sent down the pipeline to `Select-Object`.</span></span> <span data-ttu-id="53de4-150">**Property** 매개 변수는 `*` 모든 작업 개체의 속성을 표시 하는 별표 ()를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-150">The **Property** parameter specifies an asterisk (`*`) to display all the job object's properties.</span></span>

### <span data-ttu-id="53de4-151">예제 4: 백그라운드 작업으로 스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="53de4-151">Example 4: Run a script as a background job</span></span>

<span data-ttu-id="53de4-152">이 예에서는 로컬 컴퓨터의 스크립트가 백그라운드 작업으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-152">In this example, a script on the local computer is run as a background job.</span></span>

```powershell
Start-Job -FilePath C:\Scripts\Sample.ps1
```

<span data-ttu-id="53de4-153">`Start-Job`**FilePath** 매개 변수를 사용 하 여 로컬 컴퓨터에 저장 된 스크립트 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-153">`Start-Job` uses the **FilePath** parameter to specify a script file that's stored on the local computer.</span></span>

### <span data-ttu-id="53de4-154">예 5: 백그라운드 작업을 사용 하 여 프로세스 가져오기</span><span class="sxs-lookup"><span data-stu-id="53de4-154">Example 5: Get a process using a background job</span></span>

<span data-ttu-id="53de4-155">이 예제에서는 백그라운드 작업을 사용 하 여 지정 된 프로세스를 이름으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-155">This example uses a background job to get a specified process by name.</span></span>

```powershell
Start-Job -Name PShellJob -ScriptBlock { Get-Process -Name PowerShell }
```

<span data-ttu-id="53de4-156">`Start-Job`**name** 매개 변수를 사용 하 여 친숙 한 작업 이름 **pshelljob** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-156">`Start-Job` uses the **Name** parameter to specify a friendly job name, **PShellJob** .</span></span> <span data-ttu-id="53de4-157">**ScriptBlock** 매개 변수는 `Get-Process` 이름이 **PowerShell** 인 프로세스를 가져오도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-157">The **ScriptBlock** parameter specifies `Get-Process` to get processes with the name **PowerShell** .</span></span>

### <span data-ttu-id="53de4-158">예제 6: 백그라운드 작업을 사용 하 여 데이터 수집 및 저장</span><span class="sxs-lookup"><span data-stu-id="53de4-158">Example 6: Collect and save data by using a background job</span></span>

<span data-ttu-id="53de4-159">이 예에서는 많은 양의 지도 데이터를 수집 하 여 파일에 저장 하는 작업을 시작 `.tif` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-159">This example starts a job that collects a large amount of map data and then saves it in a `.tif` file.</span></span>

```powershell
Start-Job -Name GetMappingFiles -InitializationScript {Import-Module MapFunctions} -ScriptBlock {
   Get-Map -Name * | Set-Content -Path D:\Maps.tif } -RunAs32
```

<span data-ttu-id="53de4-160">`Start-Job`**name** 매개 변수를 사용 하 여 친숙 한 작업 이름인 **GetMappingFiles** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-160">`Start-Job` uses the **Name** parameter to specify a friendly job name, **GetMappingFiles** .</span></span> <span data-ttu-id="53de4-161">**또한 initializationscript** 매개 변수는 **mapfunctions** 모듈을 가져오는 스크립트 블록을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-161">The **InitializationScript** parameter runs a script block that imports the **MapFunctions** module.</span></span> <span data-ttu-id="53de4-162">**ScriptBlock** 매개 변수는 `Get-Map` `Set-Content` **Path** 매개 변수에서 지정한 위치에 데이터를 실행 하 고 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-162">The **ScriptBlock** parameter runs `Get-Map` and `Set-Content` saves the data in the location specified by the **Path** parameter.</span></span> <span data-ttu-id="53de4-163">**체제가 있어도 runas32** 매개 변수는 64 비트 운영 체제 에서도 프로세스를 32 비트로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-163">The **RunAs32** parameter runs the process as 32-bit, even on a 64-bit operating system.</span></span>

### <span data-ttu-id="53de4-164">예 7: 백그라운드 작업에 입력 전달</span><span class="sxs-lookup"><span data-stu-id="53de4-164">Example 7: Pass input to a background job</span></span>

<span data-ttu-id="53de4-165">이 예에서는 자동 변수를 사용 하 여 `$input` 입력 개체를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-165">This example uses the `$input` automatic variable to process an input object.</span></span> <span data-ttu-id="53de4-166">`Receive-Job`를 사용 하 여 작업의 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-166">Use `Receive-Job` to view the job's output.</span></span>

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

<span data-ttu-id="53de4-167">`Start-Job`**ScriptBlock** 매개 변수를 사용 하 여 `Get-Content` `$input` 자동 변수와 함께 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-167">`Start-Job` uses the **ScriptBlock** parameter to run `Get-Content` with the `$input` automatic variable.</span></span> <span data-ttu-id="53de4-168">`$input`변수는 **InputObject** 매개 변수에서 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-168">The `$input` variable gets objects from the **InputObject** parameter.</span></span> <span data-ttu-id="53de4-169">`Receive-Job`**Name** 매개 변수를 사용 하 여 작업을 지정 하 고 결과를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-169">`Receive-Job` uses the **Name** parameter to specify the job and outputs the results.</span></span> <span data-ttu-id="53de4-170">**Keep** 매개 변수는 PowerShell 세션 중에 다시 볼 수 있도록 작업 출력을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-170">The **Keep** parameter saves the job output so it can be viewed again during the PowerShell session.</span></span>

### <span data-ttu-id="53de4-171">예 8: ArgumentList 매개 변수를 사용 하 여 배열 지정</span><span class="sxs-lookup"><span data-stu-id="53de4-171">Example 8: Use the ArgumentList parameter to specify an array</span></span>

<span data-ttu-id="53de4-172">이 예제에서는 **Argumentlist** 매개 변수를 사용 하 여 인수의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-172">This example uses the **ArgumentList** parameter to specify an array of arguments.</span></span> <span data-ttu-id="53de4-173">배열은 쉼표로 구분 된 프로세스 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-173">The array is a comma-separated list of process names.</span></span>

```powershell
Start-Job -ScriptBlock { Get-Process -Name $args } -ArgumentList powershell, pwsh, notepad
```

```Output
Id     Name      PSJobTypeName   State       HasMoreData     Location     Command
--     ----      -------------   -----       -----------     --------     -------
1      Job1      BackgroundJob   Running     True            localhost    Get-Process -Name $args
```

<span data-ttu-id="53de4-174">`Start-Job`Cmdlet은 **ScriptBlock** 매개 변수를 사용 하 여 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-174">The `Start-Job` cmdlet uses the **ScriptBlock** parameter to run a command.</span></span> <span data-ttu-id="53de4-175">`Get-Process`**Name** 매개 변수를 사용 하 여 자동 변수를 지정 합니다 `$args` .</span><span class="sxs-lookup"><span data-stu-id="53de4-175">`Get-Process` uses the **Name** parameter to specify the automatic variable `$args`.</span></span> <span data-ttu-id="53de4-176">**Argumentlist** 매개 변수는 프로세스 이름 배열을에 전달 `$args` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-176">The **ArgumentList** parameter passes the array of process names to `$args`.</span></span> <span data-ttu-id="53de4-177">Powershell, pwsh 및 notepad 프로세스 이름은 로컬 컴퓨터에서 실행 되는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-177">The process names powershell, pwsh, and notepad are processes running on the local computer.</span></span>

<span data-ttu-id="53de4-178">작업의 출력을 보려면 cmdlet을 사용 `Receive-Job` 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-178">To view the job's output, use the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="53de4-179">예들 들어 `Receive-Job -Id 1`입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-179">For example, `Receive-Job -Id 1`.</span></span>

## <span data-ttu-id="53de4-180">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="53de4-180">PARAMETERS</span></span>

### <span data-ttu-id="53de4-181">-ArgumentList</span><span class="sxs-lookup"><span data-stu-id="53de4-181">-ArgumentList</span></span>

<span data-ttu-id="53de4-182">**FilePath** 매개 변수로 지정 된 스크립트 또는 **ScriptBlock** 매개 변수를 사용 하 여 지정 된 명령에 대 한 인수 또는 매개 변수 값의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-182">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** parameter or a command specified with the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="53de4-183">인수는 **Argumentlist** 에 단일 차원 배열 인수로 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-183">Arguments must be passed to **ArgumentList** as single-dimension array argument.</span></span> <span data-ttu-id="53de4-184">예를 들어 쉼표로 구분 된 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-184">For example, a comma-separated list.</span></span> <span data-ttu-id="53de4-185">**Argumentlist** 의 동작에 대 한 자세한 내용은 [about_Splatting](about/about_Splatting.md#splatting-with-arrays)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-185">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-186">-인증</span><span class="sxs-lookup"><span data-stu-id="53de4-186">-Authentication</span></span>

<span data-ttu-id="53de4-187">사용자 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-187">Specifies the mechanism that is used to authenticate user credentials.</span></span>

<span data-ttu-id="53de4-188">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-188">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="53de4-189">기본값</span><span class="sxs-lookup"><span data-stu-id="53de4-189">Default</span></span>
- <span data-ttu-id="53de4-190">Basic</span><span class="sxs-lookup"><span data-stu-id="53de4-190">Basic</span></span>
- <span data-ttu-id="53de4-191">Credssp</span><span class="sxs-lookup"><span data-stu-id="53de4-191">Credssp</span></span>
- <span data-ttu-id="53de4-192">다이제스트</span><span class="sxs-lookup"><span data-stu-id="53de4-192">Digest</span></span>
- <span data-ttu-id="53de4-193">Kerberos</span><span class="sxs-lookup"><span data-stu-id="53de4-193">Kerberos</span></span>
- <span data-ttu-id="53de4-194">Negotiate</span><span class="sxs-lookup"><span data-stu-id="53de4-194">Negotiate</span></span>
- <span data-ttu-id="53de4-195">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="53de4-195">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="53de4-196">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-196">The default value is Default.</span></span>

<span data-ttu-id="53de4-197">CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-197">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="53de4-198">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="53de4-198">For more information about the values of this parameter, see [AuthenticationMechanism](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

> [!CAUTION]
> <span data-ttu-id="53de4-199">사용자의 자격 증명이 인증을 위해 원격 컴퓨터로 전달되는 CredSSP(자격 증명 보안 지원 공급자) 인증은 둘 이상의 리소스에서 인증이 필요한 명령(예: 원격 네트워크 공유 액세스)에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-199">Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="53de4-200">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-200">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="53de4-201">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-201">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-202">-Credential</span><span class="sxs-lookup"><span data-stu-id="53de4-202">-Credential</span></span>

<span data-ttu-id="53de4-203">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-203">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="53de4-204">**Credential** 매개 변수를 지정 하지 않으면 명령은 현재 사용자의 자격 증명을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-204">If the **Credential** parameter isn't specified, the command uses the current user's credentials.</span></span>

<span data-ttu-id="53de4-205">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="53de4-205">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="53de4-206">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-206">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="53de4-207">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-207">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="53de4-208">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="53de4-208">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-209">-DefinitionName</span><span class="sxs-lookup"><span data-stu-id="53de4-209">-DefinitionName</span></span>

<span data-ttu-id="53de4-210">이 cmdlet이 시작 하는 작업의 정의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-210">Specifies the definition name of the job that this cmdlet starts.</span></span> <span data-ttu-id="53de4-211">이 매개 변수를 사용하여 예약된 작업과 같이 정의 이름이 있는 사용자 지정 작업 유형을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-211">Use this parameter to start custom job types that have a definition name, such as scheduled jobs.</span></span>

<span data-ttu-id="53de4-212">`Start-Job`를 사용 하 여 예약 된 작업의 인스턴스를 시작 하면 작업 트리거 또는 작업 옵션에 관계 없이 작업이 즉시 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-212">When you use `Start-Job` to start an instance of a scheduled job, the job starts immediately, regardless of job triggers or job options.</span></span> <span data-ttu-id="53de4-213">결과 작업 인스턴스는 예약 된 작업 이지만 트리거된 예약 된 작업 처럼 디스크에 저장 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-213">The resulting job instance is a scheduled job, but it isn't saved to disk like triggered scheduled jobs.</span></span> <span data-ttu-id="53de4-214">의 **Argumentlist** 매개 변수를 사용 `Start-Job` 하 여 예약 된 작업에서 실행 되는 스크립트의 매개 변수에 대 한 값을 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-214">You can't use the **ArgumentList** parameter of `Start-Job` to provide values for parameters of scripts that run in a scheduled job.</span></span> <span data-ttu-id="53de4-215">자세한 내용은 [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-215">For more information, see [about_Scheduled_Jobs](../PSScheduledJob/About/about_Scheduled_Jobs.md).</span></span>

<span data-ttu-id="53de4-216">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53de4-217">-DefinitionPath</span><span class="sxs-lookup"><span data-stu-id="53de4-217">-DefinitionPath</span></span>

<span data-ttu-id="53de4-218">이 cmdlet이 시작 되는 작업 정의의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-218">Specifies path of the definition for the job that this cmdlet starts.</span></span> <span data-ttu-id="53de4-219">정의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-219">Enter the definition path.</span></span> <span data-ttu-id="53de4-220">**Definitionpath** 및 **definitionpath** 매개 변수의 값 연결은 작업 정의의 정규화 된 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-220">The concatenation of the values of the **DefinitionPath** and **DefinitionName** parameters is the fully qualified path of the job definition.</span></span> <span data-ttu-id="53de4-221">이 매개 변수를 사용하여 예약된 작업과 같이 정의 경로가 있는 사용자 지정 작업 유형을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-221">Use this parameter to start custom job types that have a definition path, such as scheduled jobs.</span></span>

<span data-ttu-id="53de4-222">예약 된 작업의 경우 **Definitionpath** 매개 변수의 값은 `$home\AppData\Local\Windows\PowerShell\ScheduledJob` 입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-222">For scheduled jobs, the value of the **DefinitionPath** parameter is `$home\AppData\Local\Windows\PowerShell\ScheduledJob`.</span></span>

<span data-ttu-id="53de4-223">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-223">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53de4-224">-FilePath</span><span class="sxs-lookup"><span data-stu-id="53de4-224">-FilePath</span></span>

<span data-ttu-id="53de4-225">백그라운드 작업으로 실행 되는 로컬 스크립트를 지정 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="53de4-225">Specifies a local script that `Start-Job` runs as a background job.</span></span> <span data-ttu-id="53de4-226">스크립트의 경로와 파일 이름을 입력 하거나 파이프라인을 사용 하 여 스크립트 경로를로 보냅니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="53de4-226">Enter the path and file name of the script or use the pipeline to send a script path to `Start-Job`.</span></span> <span data-ttu-id="53de4-227">스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에서 액세스할 수 있는 폴더에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-227">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="53de4-228">이 매개 변수를 사용 하는 경우 PowerShell은 지정 된 스크립트 파일의 내용을 스크립트 블록으로 변환 하 고 스크립트 블록을 백그라운드 작업으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-228">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

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

### <span data-ttu-id="53de4-229">-또한 initializationscript</span><span class="sxs-lookup"><span data-stu-id="53de4-229">-InitializationScript</span></span>

<span data-ttu-id="53de4-230">작업을 시작하기 전에 실행되는 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-230">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="53de4-231">스크립트 블록을 만들려면 명령을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="53de4-231">To create a script block, enclose the commands in curly braces (`{}`).</span></span>

<span data-ttu-id="53de4-232">이 매개 변수를 사용하여 작업이 실행되는 세션을 준비할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-232">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="53de4-233">예를 들어 이 매개 변수를 사용하여 함수, 스냅인 및 모듈을 세션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-233">For example, you can use it to add functions, snap-ins, and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-234">-InputObject</span><span class="sxs-lookup"><span data-stu-id="53de4-234">-InputObject</span></span>

<span data-ttu-id="53de4-235">명령에 대한 입력을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-235">Specifies input to the command.</span></span> <span data-ttu-id="53de4-236">개체가 포함된 변수를 입력하거나 개체를 생성하는 명령 또는 식을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-236">Enter a variable that contains the objects, or type a command or expression that generates the objects.</span></span>

<span data-ttu-id="53de4-237">**ScriptBlock** 매개 변수 값에서 `$input` 자동 변수를 사용 하 여 입력 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-237">In the value of the **ScriptBlock** parameter, use the `$input` automatic variable to represent the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-238">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="53de4-238">-LiteralPath</span></span>

<span data-ttu-id="53de4-239">이 cmdlet이 백그라운드 작업으로 실행 되는 로컬 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-239">Specifies a local script that this cmdlet runs as a background job.</span></span> <span data-ttu-id="53de4-240">로컬 컴퓨터에서 스크립트의 경로를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-240">Enter the path of a script on the local computer.</span></span>

<span data-ttu-id="53de4-241">`Start-Job`**LiteralPath** 매개 변수의 값을 입력 된 대로 정확 하 게 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-241">`Start-Job` uses the value of the **LiteralPath** parameter exactly as it's typed.</span></span> <span data-ttu-id="53de4-242">어떠한 문자도 와일드카드 문자로 해석되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-242">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="53de4-243">이스케이프 문자가 포함된 경로는 작은따옴표로 묶으세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-243">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="53de4-244">작은따옴표는 모든 문자를 이스케이프 시퀀스로 해석 하지 않도록 PowerShell에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-244">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralFilePathComputerName
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-245">-Name</span><span class="sxs-lookup"><span data-stu-id="53de4-245">-Name</span></span>

<span data-ttu-id="53de4-246">새 작업의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-246">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="53de4-247">이 이름을 사용 하 여 cmdlet과 같은 다른 작업 cmdlet에 대 한 작업을 식별할 수 있습니다 `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="53de4-247">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="53de4-248">기본 이름은 이며 `Job#` , 여기서 `#` 은 각 작업에 대해 증가 하는 서 수입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-248">The default friendly name is `Job#`, where `#` is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-249">-PSVersion</span><span class="sxs-lookup"><span data-stu-id="53de4-249">-PSVersion</span></span>

<span data-ttu-id="53de4-250">버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-250">Specifies a version.</span></span> <span data-ttu-id="53de4-251">`Start-Job` PowerShell의 버전을 사용 하 여 작업을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-251">`Start-Job` runs the job with the version of PowerShell.</span></span> <span data-ttu-id="53de4-252">이 매개 변수에 허용 되는 값은 `2.0` 및 `3.0` 입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-252">The acceptable values for this parameter are: `2.0` and `3.0`.</span></span>

<span data-ttu-id="53de4-253">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-253">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-254">-체제가 있어도 runas32</span><span class="sxs-lookup"><span data-stu-id="53de4-254">-RunAs32</span></span>

<span data-ttu-id="53de4-255">`Start-Job`에서 작업을 32 비트 프로세스로 실행 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-255">Indicates that `Start-Job` runs the job in a 32-bit process.</span></span> <span data-ttu-id="53de4-256">**체제가 있어도 runas32** 는 64 비트 운영 체제에도 불구 하 고 32 비트 프로세스에서 작업을 실행 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-256">**RunAs32** forces the job to run in a 32-bit process, even on a 64-bit operating system.</span></span>

<span data-ttu-id="53de4-257">64 비트 버전의 Windows 7 및 Windows Server 2008 r 2에서 `Start-Job` 명령에 **체제가 있어도 runas32** 매개 변수가 포함 된 경우 **Credential** 매개 변수를 사용 하 여 다른 사용자의 자격 증명을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-257">On 64-bit versions of Windows 7 and Windows Server 2008 R2, when the `Start-Job` command includes the **RunAs32** parameter, you can't use the **Credential** parameter to specify the credentials of another user.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, LiteralFilePathComputerName, FilePathComputerName
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="53de4-258">-ScriptBlock</span><span class="sxs-lookup"><span data-stu-id="53de4-258">-ScriptBlock</span></span>

<span data-ttu-id="53de4-259">백그라운드 작업에서 실행할 명령을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-259">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="53de4-260">스크립트 블록을 만들려면 명령을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="53de4-260">To create a script block, enclose the commands in curly braces (`{}`).</span></span> <span data-ttu-id="53de4-261">`$input`자동 변수를 사용 하 여 **InputObject** 매개 변수의 값에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-261">Use the `$input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="53de4-262">이 매개 변수는 필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-262">This parameter is required.</span></span>

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

### <span data-ttu-id="53de4-263">-Type</span><span class="sxs-lookup"><span data-stu-id="53de4-263">-Type</span></span>

<span data-ttu-id="53de4-264">에서 시작한 작업의 사용자 지정 형식을 지정 합니다 `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="53de4-264">Specifies the custom type for jobs started by `Start-Job`.</span></span> <span data-ttu-id="53de4-265">사용자 지정 작업 유형 이름(예: 예약된 작업의 경우 PSScheduledJob 또는 워크플로 작업의 경우 PSWorkflowJob)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-265">Enter a custom job type name, such as PSScheduledJob for scheduled jobs or PSWorkflowJob for workflows jobs.</span></span> <span data-ttu-id="53de4-266">이 매개 변수는 표준 백그라운드 작업에 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-266">This parameter isn't valid for standard background jobs.</span></span>

<span data-ttu-id="53de4-267">이 매개 변수는 PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-267">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="53de4-268">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="53de4-268">CommonParameters</span></span>

<span data-ttu-id="53de4-269">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="53de4-269">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="53de4-270">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="53de4-270">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="53de4-271">입력</span><span class="sxs-lookup"><span data-stu-id="53de4-271">INPUTS</span></span>

### <span data-ttu-id="53de4-272">System.String</span><span class="sxs-lookup"><span data-stu-id="53de4-272">System.String</span></span>

<span data-ttu-id="53de4-273">파이프라인을 사용 하 여 **name** 속성이 있는 개체를 **name** 매개 변수로 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-273">You can use the pipeline to send an object with the **Name** property to the **Name** parameter.</span></span> <span data-ttu-id="53de4-274">예를 들어, **FileInfo** 개체를에서로 파이프라인 할 수 있습니다 `Get-ChildItem` `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="53de4-274">For example, you can pipeline a **FileInfo** object from `Get-ChildItem` to `Start-Job`.</span></span>

## <span data-ttu-id="53de4-275">출력</span><span class="sxs-lookup"><span data-stu-id="53de4-275">OUTPUTS</span></span>

### <span data-ttu-id="53de4-276">System.web. a p.</span><span class="sxs-lookup"><span data-stu-id="53de4-276">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="53de4-277">`Start-Job` 시작 된 작업을 나타내는 **Psremotingjob** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-277">`Start-Job` returns a **PSRemotingJob** object that represents the job that it started.</span></span>

## <span data-ttu-id="53de4-278">참고</span><span class="sxs-lookup"><span data-stu-id="53de4-278">NOTES</span></span>

<span data-ttu-id="53de4-279">백그라운드에서 실행 하려면는 `Start-Job` 현재 세션에서 자체 세션으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-279">To run in the background, `Start-Job` runs in its own session in the current session.</span></span> <span data-ttu-id="53de4-280">Cmdlet을 사용 `Invoke-Command` 하 여 `Start-Job` 원격 컴퓨터의 세션에서 명령을 실행할 경우는 `Start-Job` 원격 세션의 세션에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="53de4-280">When you use the `Invoke-Command` cmdlet to run a `Start-Job` command in a session on a remote computer, `Start-Job` runs in a session in the remote session.</span></span>

## <span data-ttu-id="53de4-281">관련 링크</span><span class="sxs-lookup"><span data-stu-id="53de4-281">RELATED LINKS</span></span>

[<span data-ttu-id="53de4-282">about_Arrays</span><span class="sxs-lookup"><span data-stu-id="53de4-282">about_Arrays</span></span>](./about/about_arrays.md)

[<span data-ttu-id="53de4-283">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="53de4-283">about_Automatic_Variables</span></span>](./about/about_automatic_variables.md)

[<span data-ttu-id="53de4-284">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="53de4-284">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="53de4-285">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="53de4-285">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="53de4-286">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="53de4-286">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="53de4-287">Get-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-287">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="53de4-288">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="53de4-288">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="53de4-289">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-289">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="53de4-290">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-290">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="53de4-291">Resume-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-291">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="53de4-292">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-292">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="53de4-293">Suspend-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-293">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="53de4-294">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="53de4-294">Wait-Job</span></span>](Wait-Job.md)
