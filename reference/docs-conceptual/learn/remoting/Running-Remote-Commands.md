---
ms.date: 08/21/2020
keywords: powershell,cmdlet
title: 원격 명령 실행
ms.openlocfilehash: ab6d464c31144349ee38cd01e82a2cf1470aaa95
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88799624"
---
# <a name="running-remote-commands"></a><span data-ttu-id="045d7-103">원격 명령 실행</span><span class="sxs-lookup"><span data-stu-id="045d7-103">Running Remote Commands</span></span>

<span data-ttu-id="045d7-104">단일 PowerShell 명령으로 한 대 이상의 컴퓨터에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-104">You can run commands on one or hundreds of computers with a single PowerShell command.</span></span> <span data-ttu-id="045d7-105">Windows PowerShell에서는 WMI, RPC, WS-Management 등과 같은 다양한 기술을 사용하여 원격 컴퓨팅을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-105">Windows PowerShell supports remote computing by using various technologies, including WMI, RPC, and WS-Management.</span></span>

<span data-ttu-id="045d7-106">PowerShell Core는 WMI, WS-Management 및 SSH 원격 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-106">PowerShell Core supports WMI, WS-Management, and SSH remoting.</span></span> <span data-ttu-id="045d7-107">PowerShell 6에서 RPC는 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-107">In PowerShell 6, RPC is no longer supported.</span></span> <span data-ttu-id="045d7-108">PowerShell 7 이상에서 RPC는 Windows에서만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-108">In PowerShell 7 and above, RPC is supported only in Windows.</span></span>

<span data-ttu-id="045d7-109">PowerShell Core의 원격 작업에 대한 자세한 내용은 다음 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045d7-109">For more information about remoting in PowerShell Core, see the following articles:</span></span>

- <span data-ttu-id="045d7-110">[PowerShell Core에서의 SSH 원격 작업][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="045d7-110">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="045d7-111">[PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="045d7-111">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="windows-powershell-remoting-without-configuration"></a><span data-ttu-id="045d7-112">구성 없이 Windows PowerShell 원격 작업</span><span class="sxs-lookup"><span data-stu-id="045d7-112">Windows PowerShell Remoting Without Configuration</span></span>

<span data-ttu-id="045d7-113">많은 Windows PowerShell cmdlet에서는 데이터를 수집하고 하나 이상의 원격 컴퓨터에서 설정을 변경할 수 있는 ComputerName 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-113">Many Windows PowerShell cmdlets have the ComputerName parameter that enables you to collect data and change settings on one or more remote computers.</span></span> <span data-ttu-id="045d7-114">이러한 cmdlet은 다양한 통신 프로토콜을 사용하고, 특별한 구성 없이도 모든 Windows 운영 체제에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-114">These cmdlets use varying communication protocols and work on all Windows operating systems without any special configuration.</span></span>

<span data-ttu-id="045d7-115">이러한 cmdlet은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-115">These cmdlets include:</span></span>

- [<span data-ttu-id="045d7-116">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="045d7-116">Restart-Computer</span></span>](/powershell/module/microsoft.powershell.management/restart-computer)
- [<span data-ttu-id="045d7-117">Test-Connection</span><span class="sxs-lookup"><span data-stu-id="045d7-117">Test-Connection</span></span>](/powershell/module/microsoft.powershell.management/test-connection)
- [<span data-ttu-id="045d7-118">Clear-EventLog</span><span class="sxs-lookup"><span data-stu-id="045d7-118">Clear-EventLog</span></span>](/powershell/module/microsoft.powershell.management/clear-eventlog)
- [<span data-ttu-id="045d7-119">Get-EventLog</span><span class="sxs-lookup"><span data-stu-id="045d7-119">Get-EventLog</span></span>](/powershell/module/microsoft.powershell.management/get-eventlog)
- [<span data-ttu-id="045d7-120">Get-HotFix</span><span class="sxs-lookup"><span data-stu-id="045d7-120">Get-HotFix</span></span>](/powershell/module/microsoft.powershell.management/get-hotfix)
- [<span data-ttu-id="045d7-121">Get-Process</span><span class="sxs-lookup"><span data-stu-id="045d7-121">Get-Process</span></span>](/powershell/module/microsoft.powershell.management/get-process)
- [<span data-ttu-id="045d7-122">Get-Service</span><span class="sxs-lookup"><span data-stu-id="045d7-122">Get-Service</span></span>](/powershell/module/microsoft.powershell.management/get-service)
- [<span data-ttu-id="045d7-123">Set-Service</span><span class="sxs-lookup"><span data-stu-id="045d7-123">Set-Service</span></span>](/powershell/module/microsoft.powershell.management/set-service)
- [<span data-ttu-id="045d7-124">Get-WinEvent</span><span class="sxs-lookup"><span data-stu-id="045d7-124">Get-WinEvent</span></span>](/powershell/module/microsoft.powershell.diagnostics/get-winevent)
- [<span data-ttu-id="045d7-125">Get-WmiObject</span><span class="sxs-lookup"><span data-stu-id="045d7-125">Get-WmiObject</span></span>](/powershell/module/microsoft.powershell.management/get-wmiobject)

<span data-ttu-id="045d7-126">일반적으로 특별한 구성 없이 원격 작업을 지원하는 cmdlet에는 ComputerName 매개 변수는 있지만 Session 매개 변수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-126">Typically, cmdlets that support remoting without special configuration have the ComputerName parameter and don't have the Session parameter.</span></span> <span data-ttu-id="045d7-127">세션에서 이러한 cmdlet을 찾으려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-127">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | where { $_.parameters.keys -contains "ComputerName" -and $_.parameters.keys -notcontains "Session"}
```

## <a name="windows-powershell-remoting"></a><span data-ttu-id="045d7-128">Windows PowerShell 원격 작업</span><span class="sxs-lookup"><span data-stu-id="045d7-128">Windows PowerShell Remoting</span></span>

<span data-ttu-id="045d7-129">WS-Management 프로토콜에서 Windows PowerShell 원격 작업을 사용하면 한 대 이상의 원격 컴퓨터에서 Windows PowerShell 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-129">Using the WS-Management protocol, Windows PowerShell remoting lets you run any Windows PowerShell command on one or more remote computers.</span></span> <span data-ttu-id="045d7-130">원격 컴퓨터에서 영구 연결을 설정하고, 대화형 세션을 시작하고, 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-130">You can establish persistent connections, start interactive sessions, and run scripts on remote computers.</span></span>

<span data-ttu-id="045d7-131">Windows PowerShell 원격 작업을 사용하려면 원격 관리를 위해 원격 컴퓨터를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-131">To use Windows PowerShell remoting, the remote computer must be configured for remote management.</span></span>
<span data-ttu-id="045d7-132">자세한 내용과 지침은 [원격 요구 사항 정보](/powershell/module/microsoft.powershell.core/about/about_remote_requirements)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045d7-132">For more information, including instructions, see [About Remote Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).</span></span>

<span data-ttu-id="045d7-133">Windows PowerShell 원격 작업을 구성한 후 다양한 원격 전략을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-133">Once you have configured Windows PowerShell remoting, many remoting strategies are available to you.</span></span>
<span data-ttu-id="045d7-134">이 문서에는 이러한 전략 중 일부만 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-134">This article lists just a few of them.</span></span> <span data-ttu-id="045d7-135">자세한 내용은 [원격 기능 정보](/powershell/module/microsoft.powershell.core/about/about_remote)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045d7-135">For more information, see [About Remote](/powershell/module/microsoft.powershell.core/about/about_remote).</span></span>

### <a name="start-an-interactive-session"></a><span data-ttu-id="045d7-136">대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="045d7-136">Start an Interactive Session</span></span>

<span data-ttu-id="045d7-137">단일 원격 컴퓨터와 대화형 세션을 시작하려면 [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-137">To start an interactive session with a single remote computer, use the [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession) cmdlet.</span></span> <span data-ttu-id="045d7-138">예를 들어 Server01 원격 컴퓨터와 대화형 세션을 시작하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-138">For example, to start an interactive session with the Server01 remote computer, type:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="045d7-139">명령 프롬프트가 변경되어 원격 컴퓨터의 이름이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-139">The command prompt changes to display the name of the remote computer.</span></span> <span data-ttu-id="045d7-140">프롬프트에 입력하는 명령이 원격 컴퓨터에서 실행되고 그 결과가 로컬 컴퓨터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-140">Any commands that you type at the prompt run on the remote computer and the results are displayed on the local computer.</span></span>

<span data-ttu-id="045d7-141">대화형 세션을 종료하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-141">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="045d7-142">Enter\-PSSession 및 Exit\-PSSession cmdlet에 대한 자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045d7-142">For more information about the Enter-PSSession and Exit-PSSession cmdlets, see:</span></span>

- [<span data-ttu-id="045d7-143">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="045d7-143">Enter-PSSession</span></span>](/powershell/module/microsoft.powershell.core/enter-pssession)
- [<span data-ttu-id="045d7-144">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="045d7-144">Exit-PSSession</span></span>](/powershell/module/microsoft.powershell.core/exit-pssession)

### <a name="run-a-remote-command"></a><span data-ttu-id="045d7-145">원격 명령 실행</span><span class="sxs-lookup"><span data-stu-id="045d7-145">Run a Remote Command</span></span>

<span data-ttu-id="045d7-146">한 대 이상의 컴퓨터에서 명령을 실행하려면 [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-146">To run a command on one or more computers, use the [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet.</span></span> <span data-ttu-id="045d7-147">예를 들어 Server01 및 Server02 원격 컴퓨터에서 [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) 명령을 실행하려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-147">For example, to run a [Get-UICulture](/powershell/module/microsoft.powershell.utility/get-uiculture) command on the Server01 and Server02 remote computers, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-UICulture}
```

<span data-ttu-id="045d7-148">출력은 사용자의 컴퓨터에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-148">The output is returned to your computer.</span></span>

```output
LCID    Name     DisplayName               PSComputerName
----    ----     -----------               --------------
1033    en-US    English (United States)   server01.corp.fabrikam.com
1033    en-US    English (United States)   server02.corp.fabrikam.com
```

### <a name="run-a-script"></a><span data-ttu-id="045d7-149">스크립트 실행</span><span class="sxs-lookup"><span data-stu-id="045d7-149">Run a Script</span></span>

<span data-ttu-id="045d7-150">한 대 이상의 원격 컴퓨터에서 스크립트를 실행하려면 `Invoke-Command` cmdlet의 FilePath 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-150">To run a script on one or many remote computers, use the FilePath parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="045d7-151">스크립트는 로컬 컴퓨터에 있거나 로컬 컴퓨터에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-151">The script must be on or accessible to your local computer.</span></span> <span data-ttu-id="045d7-152">결과는 로컬 컴퓨터에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-152">The results are returned to your local computer.</span></span>

<span data-ttu-id="045d7-153">예를 들어 다음 명령은 Server01 및 Server02 원격 컴퓨터에서 DiskCollect.ps1 스크립트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-153">For example, the following command runs the DiskCollect.ps1 script on the remote computers, Server01 and Server02.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -FilePath c:\Scripts\DiskCollect.ps1
```

### <a name="establish-a-persistent-connection"></a><span data-ttu-id="045d7-154">영구 연결 설정</span><span class="sxs-lookup"><span data-stu-id="045d7-154">Establish a Persistent Connection</span></span>

<span data-ttu-id="045d7-155">`New-PSSession` cmdlet을 사용하여 원격 컴퓨터에서 영구 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-155">Use the `New-PSSession` cmdlet to create a persistent session on a remote computer.</span></span> <span data-ttu-id="045d7-156">다음 예제에서는 Server01 및 Server02에 원격 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-156">The following example creates remote sessions on Server01 and Server02.</span></span> <span data-ttu-id="045d7-157">세션 개체는 `$s` 변수에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-157">The session objects are stored in the `$s` variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

<span data-ttu-id="045d7-158">세션을 설정했으므로 이제 해당 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-158">Now that the sessions are established, you can run any command in them.</span></span> <span data-ttu-id="045d7-159">세션이 영구 세션이므로 명령을 실행하여 데이터를 수집하고 다른 명령에서 해당 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-159">And because the sessions are persistent, you can collect data from one command and use it in another command.</span></span>

<span data-ttu-id="045d7-160">예를 들어 다음 명령은 $s 변수의 세션에서 Get-Hotfix 명령을 실행하고 결과를 $h 변수에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-160">For example, the following command runs a Get-HotFix command in the sessions in the $s variable and it saves the results in the $h variable.</span></span> <span data-ttu-id="045d7-161">$h 변수는 $s의 각 세션에서 생성되지만 로컬 세션에는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-161">The $h variable is created in each of the sessions in $s, but it doesn't exist in the local session.</span></span>

```powershell
Invoke-Command -Session $s {$h = Get-HotFix}
```

<span data-ttu-id="045d7-162">이제 동일한 세션에서 다른 명령에 `$h` 변수의 데이터를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-162">Now you can use the data in the `$h` variable with other commands in the same session.</span></span> <span data-ttu-id="045d7-163">결과는 로컬 컴퓨터에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-163">The results are displayed on the local computer.</span></span> <span data-ttu-id="045d7-164">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-164">For example:</span></span>

```powershell
Invoke-Command -Session $s {$h | where {$_.InstalledBy -ne "NTAUTHORITY\SYSTEM"}}
```

### <a name="advanced-remoting"></a><span data-ttu-id="045d7-165">고급 원격 작업</span><span class="sxs-lookup"><span data-stu-id="045d7-165">Advanced Remoting</span></span>

<span data-ttu-id="045d7-166">Windows PowerShell 원격 관리가 여기에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-166">Windows PowerShell remote management just begins here.</span></span> <span data-ttu-id="045d7-167">Windows PowerShell과 함께 설치되는 cmdlet을 사용하여 로컬 끝점과 원격 끝점 모두에서 원격 세션을 설정하여 구성하고, 사용자 지정되고 제한된 세션을 만들고, 사용자가 원격 세션에서 암시적으로 실행되는 명령을 원격 세션에서 가져오도록 허용하고, 원격 세션의 보안을 구성하는 등과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-167">By using the cmdlets installed with Windows PowerShell, you can establish and configure remote sessions both from the local and remote ends, create customized and restricted sessions, allow users to import commands from a remote session that actually run implicitly on the remote session, configure the security of a remote session, and much more.</span></span>

<span data-ttu-id="045d7-168">Windows PowerShell에는 WSMan 공급자가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-168">Windows PowerShell includes a WSMan provider.</span></span> <span data-ttu-id="045d7-169">공급자는 로컬 컴퓨터와 원격 컴퓨터에서 구성 설정 계층을 탐색할 수 있는 `WSMAN:` 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="045d7-169">The provider creates a `WSMAN:` drive that lets you navigate through a hierarchy of configuration settings on the local computer and remote computers.</span></span>

<span data-ttu-id="045d7-170">WSMan 공급자에 대한 자세한 내용을 보려면 [WSMan 공급자](https://technet.microsoft.com/library/dd819476.aspx) 및 [WS-Management Cmdlet 정보](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets)를 참조하거나 Windows PowerShell 콘솔에서 "`Get-Help wsman`"을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="045d7-170">For more information about the WSMan provider, see [WSMan Provider](https://technet.microsoft.com/library/dd819476.aspx) and [About WS-Management Cmdlets](/powershell/module/microsoft.powershell.core/about/about_ws-management_cmdlets), or in the Windows PowerShell console, type `Get-Help wsman`.</span></span>

<span data-ttu-id="045d7-171">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045d7-171">For more information, see:</span></span>

- [<span data-ttu-id="045d7-172">원격 FAQ 정보</span><span class="sxs-lookup"><span data-stu-id="045d7-172">About Remote FAQ</span></span>](https://technet.microsoft.com/library/dd315359.aspx)
- [<span data-ttu-id="045d7-173">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="045d7-173">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="045d7-174">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="045d7-174">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)

<span data-ttu-id="045d7-175">원격 오류에 대한 도움이 필요한 경우 [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="045d7-175">For help with remoting errors, see [about_Remote_Troubleshooting](https://technet.microsoft.com/library/dd347642.aspx).</span></span>

## <a name="see-also"></a><span data-ttu-id="045d7-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="045d7-176">See Also</span></span>

- [<span data-ttu-id="045d7-177">about_Remote</span><span class="sxs-lookup"><span data-stu-id="045d7-177">about_Remote</span></span>](https://technet.microsoft.com/library/9b4a5c87-9162-4adf-bdfe-fbc80b9b8970)
- [<span data-ttu-id="045d7-178">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="045d7-178">about_Remote_FAQ</span></span>](https://technet.microsoft.com/library/e23702fd-9415-4a98-9975-390a4d3adc42)
- [<span data-ttu-id="045d7-179">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="045d7-179">about_Remote_Requirements</span></span>](https://technet.microsoft.com/library/da213949-134c-4741-b307-81f4492ba1bd)
- [<span data-ttu-id="045d7-180">about_Remote_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="045d7-180">about_Remote_Troubleshooting</span></span>](https://technet.microsoft.com/library/2f890148-8578-49ed-85ea-79a489dd6317)
- [<span data-ttu-id="045d7-181">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="045d7-181">about_PSSessions</span></span>](https://technet.microsoft.com/library/7a9b4e0e-fa1b-47b0-92f6-6e2995d70acb)
- [<span data-ttu-id="045d7-182">about_WS-Management_Cmdlets</span><span class="sxs-lookup"><span data-stu-id="045d7-182">about_WS-Management_Cmdlets</span></span>](https://technet.microsoft.com/library/6ed3370a-ea10-45a5-9493-696aeace27ed)
- [<span data-ttu-id="045d7-183">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="045d7-183">Invoke-Command</span></span>](/powershell/module/microsoft.powershell.core/invoke-command)
- [<span data-ttu-id="045d7-184">Import-PSSession</span><span class="sxs-lookup"><span data-stu-id="045d7-184">Import-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821821)
- [<span data-ttu-id="045d7-185">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="045d7-185">New-PSSession</span></span>](https://go.microsoft.com/fwlink/?LinkId=821498)
- [<span data-ttu-id="045d7-186">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="045d7-186">Register-PSSessionConfiguration</span></span>](https://go.microsoft.com/fwlink/?LinkId=821508)
- [<span data-ttu-id="045d7-187">WSMan 공급자</span><span class="sxs-lookup"><span data-stu-id="045d7-187">WSMan Provider</span></span>](https://technet.microsoft.com/library/66fe1241-e08f-49ca-832f-a84c33ca8735)

[wsman-remoting]: WSMan-Remoting-in-PowerShell-Core.md
[ssh-remoting]: SSH-Remoting-in-PowerShell-Core.md
