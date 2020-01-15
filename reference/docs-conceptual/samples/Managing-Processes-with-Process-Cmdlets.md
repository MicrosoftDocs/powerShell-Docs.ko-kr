---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Process Cmdlet으로 프로세스 관리
ms.openlocfilehash: 8de0cbae508958bf7970ce69e03257ea0a8dca6f
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870747"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="69ec0-103">Process Cmdlet으로 프로세스 관리</span><span class="sxs-lookup"><span data-stu-id="69ec0-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="69ec0-104">Windows PowerShell에서 Process cmdlet을 사용하여 Windows PowerShell의 로컬 및 원격 프로세스를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="69ec0-105">프로세스 가져오기(Get-Process)</span><span class="sxs-lookup"><span data-stu-id="69ec0-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="69ec0-106">로컬 컴퓨터에서 실행 중인 프로세스를 가져오려면 **Get-Process**를 매개 변수 없이 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="69ec0-107">프로세스 이름 또는 프로세스 ID를 지정하여 특정 프로세스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="69ec0-108">다음 명령은 Idle 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="69ec0-109">일반적으로 cmdlet이 데이터를 반환하지 않아도 오류 메시지가 나타나지 않지만 ProcessId를 사용하여 프로세스를 지정한 경우 **Get-Process**가 일치하는 항목을 찾지 못하면 오류 메시지가 나타납니다. 이 cmdlet의 기본 목적이 실행 중인 프로세스를 검색하는 것이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="69ec0-110">해당 Id를 가진 프로세스가 없으면 Id가 잘못되었거나 해당 프로세스가 이미 종료된 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="69ec0-111">Get-Process cmdlet의 Name 매개 변수를 사용하면 프로세스 이름을 기반으로 프로세서의 하위 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="69ec0-112">Name 매개 변수는 여러 개의 이름을 쉼표로 구분된 목록으로 받아들일 수 있으며 와일드카드 사용을 지원하기 때문에 사용자는 이름 패턴을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="69ec0-113">예를 들어 다음 명령은 이름이 "ex"로 시작되는 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="69ec0-114">.NET System.Diagnostics.Process 클래스는 Windows PowerShell 프로세스의 기초이므로 System.Diagnostics.Process가 사용하는 일부 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="69ec0-115">이러한 규칙 중 하나는 실행 파일의 프로세스 이름에 ".exe" 확장명을 포함하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="69ec0-116">또한 **Get-Process**는 Name 매개 변수에 대해 여러 값을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="69ec0-117">Get-Process의 ComputerName 매개 변수를 사용하여 원격 컴퓨터의 프로세스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="69ec0-118">예를 들어 다음 명령은 로컬 컴퓨터("localhost"로 표현됨)에 있는 PowerShell 프로세스와 두 개의 원격 컴퓨터에 있는 PowerShell 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="69ec0-119">이 표시에서는 컴퓨터 이름이 분명히 나타나지 않지만 Get-Process가 반환하는 프로세스 개체의 MachineName 속성에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="69ec0-120">다음 명령은 Format-Table cmdlet을 사용하여 프로세스 개체의 프로세스 ID, ProcessName 및 MachineName(ComputerName) 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 |
  Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="69ec0-121">더욱 복잡한 이 명령은 MachineName 속성을 표준 Get-Process 표시에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="69ec0-122">프로세스 중지(Stop-Process)</span><span class="sxs-lookup"><span data-stu-id="69ec0-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="69ec0-123">Windows PowerShell에서는 다양한 방법으로 프로세스를 표시할 수 있지만 프로세스 중지의 경우는 어떨까요?</span><span class="sxs-lookup"><span data-stu-id="69ec0-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="69ec0-124">**Stop-Process** cmdlet은 Name 또는 Id를 사용하여 중지할 프로세스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="69ec0-125">프로세스를 중지할 수 있는지 여부는 사용 권한에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="69ec0-126">일부 프로세스는 중지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="69ec0-127">예를 들어 유휴 프로세스를 중지하려고 하면 다음과 같은 오류 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="69ec0-128">**Confirm** 매개 변수를 사용하여 강제로 확인하도록 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="69ec0-129">이 매개 변수는 프로세스 이름을 지정할 때 와일드카드를 사용할 경우 원하지 않는 프로세스가 중지될 수 있으므로 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="69ec0-130">일부 개체 필터링 cmdlet을 사용하면 복잡한 프로세스 조작이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="69ec0-131">프로세스 개체에는 더 이상 응답이 없을 때 true인 응답 속성이 있으므로 다음 명령을 사용하여 응답이 없는 모든 애플리케이션을 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="69ec0-132">위와 동일한 방법을 다른 경우에 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="69ec0-133">예를 들어 다른 애플리케이션을 시작하면 보조 알림 영역 애플리케이션이 자동으로 실행된다고 가정할 경우</span><span class="sxs-lookup"><span data-stu-id="69ec0-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="69ec0-134">이 보조 알림 영역 응용 프로그램이 터미널 서비스 세션에서 올바로 작동하지 않는 것을 알았지만 실제 컴퓨터 콘솔에서 실행되는 세션에서 이 응용 프로그램을 계속 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="69ec0-135">실제 컴퓨터의 데스크톱에 연결된 세션에는 항상 세션 ID로 0이 지정되므로 다음과 같이 **Where-Object**와 **SessionId** 프로세스를 사용하여 다른 세션에 있는 프로세스의 인스턴스를 모두 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="69ec0-136">Stop-Process cmdlet에는 ComputerName 매개 변수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="69ec0-137">따라서 원격 컴퓨터에서 프로세스 중지 명령을 실행하려면 Invoke-Command cmdlet을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="69ec0-138">예를 들어 Server01 원격 컴퓨터에서 PowerShell 프로세스를 중지하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="69ec0-139">다른 모든 Windows PowerShell 세션 중지</span><span class="sxs-lookup"><span data-stu-id="69ec0-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="69ec0-140">경우에 따라 현재 세션을 제외하고 실행 중인 다른 모든 Windows PowerShell 세션을 중지할 수 있는 기능이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="69ec0-141">세션에서 너무 많은 리소스를 사용하고 있거나 세션에 액세스할 수 없으면(원격에서 실행 중이거나 다른 데스크톱 세션에서 실행 중인 경우) 세션을 직접 중지하지 못할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="69ec0-142">그러나 실행 중인 세션을 모두 중지하려고 하면 현재 세션이 대신 종료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="69ec0-143">각 Windows PowerShell 세션에는 Windows PowerShell 프로세스의 Id가 들어 있는 환경 변수 PID가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="69ec0-144">각 세션의 Id에 대해 $PID를 확인하고 다른 Id를 가진 Windows PowerShell 세션만 종료할 수 있습니다. 다음 파이프라인 명령은 이 작업을 수행하고 종료된 세션의 목록을 반환합니다. 이 명령이 종료된 세션의 목록을 반환하는 것은 **PassThru** 매개 변수를 사용하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="69ec0-145">프로세스 시작, 디버그 및 대기</span><span class="sxs-lookup"><span data-stu-id="69ec0-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="69ec0-146">Windows PowerShell에는 프로세스를 시작(또는 다시 시작)하고, 프로세스를 디버그하고, 명령을 실행하기 전에 프로세스의 완료를 기다리는 cmdlet도 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="69ec0-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="69ec0-147">이러한 cmdlet에 대한 자세한 내용은 각 cmdlet의 cmdlet 도움말 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="69ec0-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="69ec0-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69ec0-148">See Also</span></span>

- [<span data-ttu-id="69ec0-149">Get-Process</span><span class="sxs-lookup"><span data-stu-id="69ec0-149">Get-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Get-Process)
- [<span data-ttu-id="69ec0-150">Stop-Process</span><span class="sxs-lookup"><span data-stu-id="69ec0-150">Stop-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Stop-Process)
- [<span data-ttu-id="69ec0-151">Start-Process</span><span class="sxs-lookup"><span data-stu-id="69ec0-151">Start-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Start-Process)
- [<span data-ttu-id="69ec0-152">Wait-Process</span><span class="sxs-lookup"><span data-stu-id="69ec0-152">Wait-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Wait-Process)
- [<span data-ttu-id="69ec0-153">Debug-Process</span><span class="sxs-lookup"><span data-stu-id="69ec0-153">Debug-Process</span></span>](/powershell/module/Microsoft.PowerShell.Management/Debug-Process)
- [<span data-ttu-id="69ec0-154">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="69ec0-154">Invoke-Command</span></span>](/powershell/module/Microsoft.PowerShell.Core/Invoke-Command)
