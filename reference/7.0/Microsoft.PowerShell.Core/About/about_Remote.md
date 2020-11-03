---
description: PowerShell에서 원격 명령을 실행 하는 방법을 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: 1974352f57625689907143340c7439ed3d92b431
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93223802"
---
# <a name="about-remote"></a><span data-ttu-id="ccbbf-104">원격 정보</span><span class="sxs-lookup"><span data-stu-id="ccbbf-104">About Remote</span></span>

## <a name="short-description"></a><span data-ttu-id="ccbbf-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="ccbbf-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="ccbbf-106">PowerShell에서 원격 명령을 실행 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-106">Describes how to run remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="ccbbf-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="ccbbf-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="ccbbf-108">임시 또는 영구 연결을 사용 하 여 단일 컴퓨터 또는 여러 컴퓨터에서 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-108">You can run remote commands on a single computer or on multiple computers by using a temporary or persistent connection.</span></span> <span data-ttu-id="ccbbf-109">단일 원격 컴퓨터를 사용 하 여 대화형 세션을 시작할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-109">You can also start an interactive session with a single remote computer.</span></span>

<span data-ttu-id="ccbbf-110">이 항목에서는 다양 한 유형의 원격 명령을 실행 하는 방법을 보여 주는 일련의 예제를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-110">This topic provides a series of examples to show you how to run different types of remote command.</span></span> <span data-ttu-id="ccbbf-111">이러한 기본 명령을 시도한 후에는 이러한 명령에 사용 되는 각 cmdlet에 대해 설명 하는 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-111">After you try these basic commands, read the Help topics that describe each cmdlet that is used in these commands.</span></span> <span data-ttu-id="ccbbf-112">항목에서는 세부 정보를 제공 하 고 요구 사항에 맞게 명령을 수정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-112">The topics provide the details and explain how you can modify the commands to meet your needs.</span></span>

<span data-ttu-id="ccbbf-113">참고: PowerShell 원격을 사용 하려면 원격 컴퓨터에 대 한 로컬 및 원격 컴퓨터를 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-113">Note: To use PowerShell remoting, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="ccbbf-114">자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-114">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

## <a name="how-to-start-an-interactive-session-enter-pssession"></a><span data-ttu-id="ccbbf-115">대화형 세션을 시작 하는 방법 (입력-PSSESSION)</span><span class="sxs-lookup"><span data-stu-id="ccbbf-115">HOW TO START AN INTERACTIVE SESSION (ENTER-PSSESSION)</span></span>

<span data-ttu-id="ccbbf-116">원격 명령을 실행 하는 가장 쉬운 방법은 원격 컴퓨터와의 대화형 세션을 시작 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-116">The easiest way to run remote commands is to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="ccbbf-117">세션이 시작 되 면 입력 하는 명령은 원격 컴퓨터에서 직접 입력 한 것 처럼 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-117">When the session starts, the commands that you type run on the remote computer, just as though you typed them directly on the remote computer.</span></span> <span data-ttu-id="ccbbf-118">각 대화형 세션에서 한 대의 컴퓨터에만 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-118">You can connect to only one computer in each interactive session.</span></span>

<span data-ttu-id="ccbbf-119">대화형 세션을 시작 하려면 Enter-PSSession cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-119">To start an interactive session, use the Enter-PSSession cmdlet.</span></span> <span data-ttu-id="ccbbf-120">다음 명령은 Server01 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-120">The following command starts an interactive session with the Server01 computer:</span></span>

```powershell
Enter-PSSession Server01
```

<span data-ttu-id="ccbbf-121">명령 프롬프트가 변경 되어 Server01 컴퓨터에 연결 되어 있음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-121">The command prompt changes to indicate that you are connected to the Server01 computer.</span></span>

```
Server01\PS>
```

<span data-ttu-id="ccbbf-122">이제 Server01 컴퓨터에 명령을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-122">Now, you can type commands on the Server01 computer.</span></span>

<span data-ttu-id="ccbbf-123">대화형 세션을 종료하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-123">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="ccbbf-124">자세한 내용은 Enter-PSSession을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-124">For more information, see Enter-PSSession.</span></span>

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a><span data-ttu-id="ccbbf-125">COMPUTERNAME 매개 변수를 사용 하 여 원격 데이터를 가져오는 CMDLET을 사용 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ccbbf-125">HOW TO USE CMDLETS THAT HAVE A COMPUTERNAME PARAMETER TO GET REMOTE DATA</span></span>

<span data-ttu-id="ccbbf-126">여러 cmdlet에는 원격 컴퓨터에서 개체를 가져올 수 있도록 하는 ComputerName 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-126">Several cmdlets have a ComputerName parameter that lets you get objects from remote computers.</span></span>

<span data-ttu-id="ccbbf-127">이러한 cmdlet은 WS-MANAGEMENT 기반 PowerShell 원격을 사용 하지 않으므로 PowerShell을 실행 하는 모든 컴퓨터에서 이러한 cmdlet의 ComputerName 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-127">Because these cmdlets do not use WS-Management-based PowerShell remoting, you can use the ComputerName parameter of these cmdlets on any computer that is running PowerShell.</span></span> <span data-ttu-id="ccbbf-128">컴퓨터를 PowerShell 원격으로 구성할 필요가 없으며, 컴퓨터는 원격 서비스에 대 한 시스템 요구 사항을 충족할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-128">The computers do not have to be configured for PowerShell remoting, and the computers do not have to meet the system requirements for remoting.</span></span>

<span data-ttu-id="ccbbf-129">다음 cmdlet에는 ComputerName 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-129">The following cmdlets have a ComputerName parameter:</span></span>

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

<span data-ttu-id="ccbbf-130">예를 들어 다음 명령은 Server01 원격 컴퓨터의 서비스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-130">For example, the following command gets the services on the Server01 remote computer:</span></span>

```powershell
Get-Service -ComputerName Server01
```

<span data-ttu-id="ccbbf-131">일반적으로 특별 한 구성 없이 원격 작업을 지 원하는 cmdlet에는 **ComputerName** 매개 변수가 있으며 **Session** 매개 변수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-131">Typically, cmdlets that support remoting without special configuration have a **ComputerName** parameter and do not have a **Session** parameter.</span></span> <span data-ttu-id="ccbbf-132">세션에서 이러한 cmdlet을 찾으려면 다음과 같이 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-132">To find these cmdlets in your session, type:</span></span>

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a><span data-ttu-id="ccbbf-133">원격 명령을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ccbbf-133">HOW TO RUN A REMOTE COMMAND</span></span>

<span data-ttu-id="ccbbf-134">원격 컴퓨터에서 다른 명령을 실행 하려면 Invoke-Command cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-134">To run other commands on remote computers, use the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="ccbbf-135">단일 명령이 나 몇 가지 관련 되지 않은 명령을 실행 하려면 Invoke-Command의 ComputerName 매개 변수를 사용 하 여 원격 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-135">To run a single command or a few unrelated commands, use the ComputerName parameter of Invoke-Command to specify the remote computers.</span></span> <span data-ttu-id="ccbbf-136">ScriptBlock 매개 변수를 사용 하 여 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-136">Use the ScriptBlock parameter to specify the command.</span></span>

<span data-ttu-id="ccbbf-137">예를 들어 다음 명령은 Server01 컴퓨터에서 Get-Culture 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-137">For example, the following command runs a Get-Culture command on the Server01 computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="ccbbf-138">ComputerName 매개 변수는 하나 이상의 컴퓨터에서 단일 명령 또는 관련 되지 않은 여러 명령을 실행 하는 상황을 위해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-138">The ComputerName parameter is designed for situation in which you run a single command or several unrelated commands on one or many computers.</span></span> <span data-ttu-id="ccbbf-139">원격 컴퓨터에 대 한 영구 연결을 설정 하려면 Session 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-139">To establish a persistent connection to a remote computer, use the Session parameter.</span></span>

## <a name="how-to-create-a-persistent-connection-pssession"></a><span data-ttu-id="ccbbf-140">영구 연결 (PSSESSION)을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="ccbbf-140">HOW TO CREATE A PERSISTENT CONNECTION (PSSESSION)</span></span>

<span data-ttu-id="ccbbf-141">Invoke-Command cmdlet의 ComputerName 매개 변수를 사용 하는 경우 Windows PowerShell은 명령에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-141">When you use the ComputerName parameter of the Invoke-Command cmdlet, Windows PowerShell establishes a connection just for the command.</span></span> <span data-ttu-id="ccbbf-142">명령이 완료될 때 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-142">Then, it closes the connection when the command is complete.</span></span> <span data-ttu-id="ccbbf-143">명령에 정의 된 변수나 함수는 모두 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-143">Any variables or functions that are defined in the command are lost.</span></span>

<span data-ttu-id="ccbbf-144">원격 컴퓨터에 대 한 영구 연결을 만들려면 New-PSSession cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-144">To create a persistent connection to a remote computer, use the New-PSSession cmdlet.</span></span> <span data-ttu-id="ccbbf-145">예를 들어 다음 명령은 Server01 및 Server02 컴퓨터에 pssession을 만든 다음 $s 변수에 pssession을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-145">For example, the following command creates PSSessions on the Server01 and Server02 computers and then saves the PSSessions in the $s variable.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a><span data-ttu-id="ccbbf-146">PSSESSION에서 명령을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ccbbf-146">HOW TO RUN COMMANDS IN A PSSESSION</span></span>

<span data-ttu-id="ccbbf-147">PSSession을 사용 하 여 함수, 별칭 및 변수 값과 같은 데이터를 공유 하는 일련의 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-147">With a PSSession, you can run a series of remote commands that share data, like functions, aliases, and the values of variables.</span></span> <span data-ttu-id="ccbbf-148">PSSession에서 명령을 실행 하려면 Invoke-Command cmdlet의 Session 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-148">To run commands in a PSSession, use the Session parameter of the Invoke-Command cmdlet.</span></span>

<span data-ttu-id="ccbbf-149">예를 들어 다음 명령은 Invoke-Command cmdlet을 사용 하 여 Server01 및 Server02 컴퓨터의 PSSessions에서 Get-Process 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-149">For example, the following command uses the Invoke-Command cmdlet to run a Get-Process command in the PSSessions on the Server01 and Server02 computers.</span></span>
<span data-ttu-id="ccbbf-150">이 명령은 각 PSSession의 $p 변수에 프로세스를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-150">The command saves the processes in a $p variable in each PSSession.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

<span data-ttu-id="ccbbf-151">PSSession에서 영구 연결을 사용 하기 때문에 $p 변수를 사용 하는 동일한 PSSession에서 다른 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-151">Because the PSSession uses a persistent connection, you can run another command in the same PSSession that uses the $p variable.</span></span> <span data-ttu-id="ccbbf-152">다음 명령은 $p에 저장 된 프로세스의 수를 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-152">The following command counts the number of processes saved in $p.</span></span>

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a><span data-ttu-id="ccbbf-153">여러 컴퓨터에서 원격 명령을 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ccbbf-153">HOW TO RUN A REMOTE COMMAND ON MULTIPLE COMPUTERS</span></span>

<span data-ttu-id="ccbbf-154">여러 컴퓨터에서 원격 명령을 실행 하려면 ComputerName 매개 변수 값에 모든 컴퓨터 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-154">To run a remote command on multiple computers, type all of the computer names in the value of the ComputerName parameter of Invoke-Command.</span></span> <span data-ttu-id="ccbbf-155">이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-155">Separate the names with commas.</span></span>

<span data-ttu-id="ccbbf-156">예를 들어 다음 명령은 3 대의 컴퓨터에서 Get-Culture 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-156">For example, the following command runs a Get-Culture command on three computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

<span data-ttu-id="ccbbf-157">여러 PSSessions에서 명령을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-157">You can also run a command in multiple PSSessions.</span></span> <span data-ttu-id="ccbbf-158">다음 명령은 Server01, Server02 및 Server03 컴퓨터에서 pssession을 만든 다음 각 PSSessions에서 Get-Culture 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-158">The following commands create PSSessions on the Server01, Server02, and Server03 computers and then run a Get-Culture command in each of the PSSessions.</span></span>

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

<span data-ttu-id="ccbbf-159">컴퓨터의 로컬 컴퓨터 목록을 포함 하려면 로컬 컴퓨터의 이름을 입력 하 고 점 (.)을 입력 하거나 "localhost"를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-159">To include the local computer list of computers, type the name of the local computer, type a dot (.), or type  "localhost".</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a><span data-ttu-id="ccbbf-160">원격 컴퓨터에서 스크립트를 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ccbbf-160">HOW TO RUN A SCRIPT ON REMOTE COMPUTERS</span></span>

<span data-ttu-id="ccbbf-161">원격 컴퓨터에서 로컬 스크립트를 실행 하려면 Invoke 명령의 FilePath 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-161">To run a local script on remote computers, use the FilePath parameter of Invoke-Command.</span></span>

<span data-ttu-id="ccbbf-162">예를 들어 다음 명령은 S1 및 S2 컴퓨터에서 Sample.ps1 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-162">For example, the following command runs the Sample.ps1 script on the S1 and S2 computers:</span></span>

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

<span data-ttu-id="ccbbf-163">스크립트의 결과는 로컬 컴퓨터에 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-163">The results of the script are returned to the local computer.</span></span> <span data-ttu-id="ccbbf-164">모든 파일을 복사할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-164">You do not need to copy any files.</span></span>

## <a name="how-to-stop-a-remote-command"></a><span data-ttu-id="ccbbf-165">원격 명령을 중지 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ccbbf-165">HOW TO STOP A REMOTE COMMAND</span></span>

<span data-ttu-id="ccbbf-166">명령을 중단 하려면 CTRL + C를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-166">To interrupt a command, press CTRL+C.</span></span> <span data-ttu-id="ccbbf-167">원격 명령을 종료 하는 원격 컴퓨터에 인터럽트 요청이 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-167">The interrupt request is passed to the remote computer where it terminates the remote command.</span></span>

## <a name="for-more-information"></a><span data-ttu-id="ccbbf-168">상세 설명</span><span class="sxs-lookup"><span data-stu-id="ccbbf-168">FOR MORE INFORMATION</span></span>

- <span data-ttu-id="ccbbf-169">원격 기능에 대 한 시스템 요구 사항에 대 한 자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-169">For information about the system requirements for remoting, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

- <span data-ttu-id="ccbbf-170">원격 출력 서식 지정에 대 한 도움말은 [about_Remote_Output](about_Remote_Output.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-170">For help in formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

- <span data-ttu-id="ccbbf-171">원격 작업 방식, 원격 데이터 관리 방법, 특수 구성, 보안 문제 및 기타 질문과 대답에 대 한 자세한 내용은 [about_Remote_FAQ](about_Remote_FAQ.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-171">For information about how remoting works, how to manage remote data, special configurations, security issues, and other frequently asked questions, see [about_Remote_FAQ](about_Remote_FAQ.md).</span></span>

- <span data-ttu-id="ccbbf-172">원격 오류 해결에 대 한 도움말은 about_Remote_Troubleshooting를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-172">For help in resolving remoting errors, see about_Remote_Troubleshooting.</span></span>

- <span data-ttu-id="ccbbf-173">PSSessions 및 영구 연결에 대 한 자세한 내용은 [about_PSSessions](about_PSSessions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-173">For information about PSSessions and persistent connections, see [about_PSSessions](about_PSSessions.md).</span></span>

- <span data-ttu-id="ccbbf-174">PowerShell 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs](about_Jobs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-174">For information about PowerShell background jobs, see [about_Jobs](about_Jobs.md).</span></span>

## <a name="keywords"></a><span data-ttu-id="ccbbf-175">어</span><span class="sxs-lookup"><span data-stu-id="ccbbf-175">KEYWORDS</span></span>

<span data-ttu-id="ccbbf-176">about_Remoting</span><span class="sxs-lookup"><span data-stu-id="ccbbf-176">about_Remoting</span></span>

## <a name="see-also"></a><span data-ttu-id="ccbbf-177">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ccbbf-177">SEE ALSO</span></span>

[<span data-ttu-id="ccbbf-178">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="ccbbf-178">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="ccbbf-179">about_Remote_Disconnected_Sessions</span><span class="sxs-lookup"><span data-stu-id="ccbbf-179">about_Remote_Disconnected_Sessions</span></span>](about_Remote_Disconnected_Sessions.md)

[<span data-ttu-id="ccbbf-180">about_Remote_Requirements</span><span class="sxs-lookup"><span data-stu-id="ccbbf-180">about_Remote_Requirements</span></span>](about_Remote_Requirements.md)

[<span data-ttu-id="ccbbf-181">about_Remote_FAQ</span><span class="sxs-lookup"><span data-stu-id="ccbbf-181">about_Remote_FAQ</span></span>](about_Remote_FAQ.md)

[<span data-ttu-id="ccbbf-182">about_Remote_TroubleShooting</span><span class="sxs-lookup"><span data-stu-id="ccbbf-182">about_Remote_TroubleShooting</span></span>](about_Remote_TroubleShooting.md)

[<span data-ttu-id="ccbbf-183">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="ccbbf-183">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="ccbbf-184">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="ccbbf-184">Enter-PSSession</span></span>](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[<span data-ttu-id="ccbbf-185">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="ccbbf-185">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="ccbbf-186">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="ccbbf-186">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)
