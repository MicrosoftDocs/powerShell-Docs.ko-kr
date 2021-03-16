---
description: PowerShell에서 원격 명령을 실행 하는 방법에 대 한 질문과 대답이 포함 되어 있습니다.
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_faq?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_FAQ
ms.openlocfilehash: da3516697c58e3273538ed2ed93a7a54fcd9bb49
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601045"
---
# <a name="about-remote-faq"></a><span data-ttu-id="3872b-103">원격 FAQ 정보</span><span class="sxs-lookup"><span data-stu-id="3872b-103">About Remote FAQ</span></span>

## <a name="short-description"></a><span data-ttu-id="3872b-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="3872b-104">Short description</span></span>
<span data-ttu-id="3872b-105">PowerShell에서 원격 명령을 실행 하는 방법에 대 한 질문과 대답이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-105">Contains questions and answers about running remote commands in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="3872b-106">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-106">Long description</span></span>

<span data-ttu-id="3872b-107">원격으로 작업 하는 경우 한 컴퓨터 ("로컬 컴퓨터" 라고도 함)의 PowerShell에 명령을 입력 하지만 명령이 다른 컴퓨터에서 실행 됩니다 ("원격 컴퓨터" 라고도 함).</span><span class="sxs-lookup"><span data-stu-id="3872b-107">When you work remotely, you type commands in PowerShell on one computer (known as the "local computer"), but the commands run on another computer (known as the "remote computer").</span></span> <span data-ttu-id="3872b-108">원격으로 작업 하는 환경은 가능 하면 원격 컴퓨터에서 직접 작업 하는 것과 매우 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-108">The experience of working remotely should be as much like working directly at the remote computer as possible.</span></span>

<span data-ttu-id="3872b-109">참고: PowerShell 원격을 사용 하려면 원격 컴퓨터를 원격으로 구성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-109">Note: To use PowerShell remoting, the remote computer must be configured for remoting.</span></span> <span data-ttu-id="3872b-110">자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-110">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="must-both-computers-have-powershell-installed"></a><span data-ttu-id="3872b-111">두 컴퓨터 모두에 PowerShell이 설치 되어 있어야 하나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-111">Must both computers have PowerShell installed?</span></span>

<span data-ttu-id="3872b-112">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-112">Yes.</span></span> <span data-ttu-id="3872b-113">원격으로 작업 하려면 로컬 및 원격 컴퓨터에 PowerShell, Microsoft .NET 프레임 워크 및 WS-MANAGEMENT (Web Services for Management) 프로토콜이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-113">To work remotely, the local and remote computers must have PowerShell, the Microsoft .NET Framework, and the Web Services for Management (WS-Management) protocol.</span></span> <span data-ttu-id="3872b-114">특정 명령을 실행 하는 데 필요한 모든 파일 및 기타 리소스는 원격 컴퓨터에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-114">Any files and other resources that are needed to execute a particular command must be on the remote computer.</span></span>

<span data-ttu-id="3872b-115">Windows PowerShell 3.0 및 Windows PowerShell 2.0을 실행 하는 컴퓨터를 실행 하는 컴퓨터는 원격으로 연결 하 고 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-115">Computers running Windows PowerShell 3.0 and computers running Windows PowerShell 2.0 can connect to each other remotely and run remote commands.</span></span>
<span data-ttu-id="3872b-116">그러나 세션에서 연결을 끊고 다시 연결 하는 기능과 같은 일부 기능은 두 컴퓨터에서 모두 Windows PowerShell 3.0를 실행 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-116">However, some features, such as the ability to disconnect from a session and reconnect to it, work only when both computers are running Windows PowerShell 3.0.</span></span>

<span data-ttu-id="3872b-117">원격 컴퓨터에 연결할 수 있는 권한, PowerShell을 실행할 수 있는 권한 및 원격 컴퓨터의 데이터 저장소 (예: 파일 및 폴더)에 대 한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-117">You must have permission to connect to the remote computer, permission to run PowerShell, and permission to access data stores (such as files and folders), and the registry on the remote computer.</span></span>

<span data-ttu-id="3872b-118">자세한 내용은 [about_Remote_Requirements](about_Remote_Requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-118">For more information, see [about_Remote_Requirements](about_Remote_Requirements.md).</span></span>

### <a name="how-does-remoting-work"></a><span data-ttu-id="3872b-119">Remoting은 어떻게 작동 하나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-119">How does remoting work?</span></span>

<span data-ttu-id="3872b-120">원격 명령을 제출 하면 명령이 네트워크를 통해 원격 컴퓨터의 PowerShell 엔진에 전송 되 고 원격 컴퓨터의 PowerShell 클라이언트에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-120">When you submit a remote command, the command is transmitted across the network to the PowerShell engine on the remote computer, and it runs in the PowerShell client on the remote computer.</span></span> <span data-ttu-id="3872b-121">명령 결과는 로컬 컴퓨터에 다시 전송 되 고 로컬 컴퓨터의 PowerShell 세션에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-121">The command results are sent back to the local computer and appear in the PowerShell session on the local computer.</span></span>

<span data-ttu-id="3872b-122">명령을 전송 하 고 출력을 수신 하기 위해 PowerShell은 WS-Management 프로토콜을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-122">To transmit the commands and receive the output, PowerShell uses the WS-Management protocol.</span></span> <span data-ttu-id="3872b-123">WS-Management 프로토콜에 대 한 자세한 내용은 Windows 설명서의 [WS-Management 프로토콜](/windows/win32/winrm/ws-management-protocol) 를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3872b-123">For information about the WS-Management protocol, see [WS-Management Protocol](/windows/win32/winrm/ws-management-protocol) in the Windows documentation.</span></span>

<span data-ttu-id="3872b-124">Windows PowerShell 3.0부터 원격 세션은 원격 컴퓨터에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-124">Beginning in Windows PowerShell 3.0, remote sessions are stored on the remote computer.</span></span> <span data-ttu-id="3872b-125">이렇게 하면 세션에서 연결을 끊고 다른 세션이 나 다른 컴퓨터에서 다시 연결 하 여 명령을 중단 하거나 상태를 손실할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-125">This enables you to disconnect from the session and reconnect from a different session or a different computer without interrupting the commands or losing state.</span></span>

### <a name="is-powershell-remoting-secure"></a><span data-ttu-id="3872b-126">PowerShell remoting은 안전 한가요?</span><span class="sxs-lookup"><span data-stu-id="3872b-126">Is PowerShell remoting secure?</span></span>

<span data-ttu-id="3872b-127">원격 컴퓨터에 연결 하는 경우 시스템은 로컬 컴퓨터의 사용자 이름 및 암호 자격 증명을 사용 하거나 명령에서 제공 하는 자격 증명을 사용 하 여 원격 컴퓨터에 로그인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-127">When you connect to a remote computer, the system uses the username and password credentials on the local computer or the credentials that you supply in the command to log you in to the remote computer.</span></span> <span data-ttu-id="3872b-128">자격 증명과 전송의 나머지는 암호화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-128">The credentials and the rest of the transmission are encrypted.</span></span>

<span data-ttu-id="3872b-129">보호를 추가 하려면 WinRM (Windows 원격 관리) 요청을 수신 대기 하도록 원격 컴퓨터에서 HTTP 대신 SSL(Secure Sockets Layer) (SSL)를 사용 하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-129">To add additional protection, you can configure the remote computer to use Secure Sockets Layer (SSL) instead of HTTP to listen for Windows Remote Management (WinRM) requests.</span></span> <span data-ttu-id="3872b-130">그런 다음 사용자는 연결을  `Invoke-Command` `New-PSSession` 설정할 때, 및 cmdlet의 UseSSL 매개 변수를 사용할 수 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="3872b-130">Then, users can use the **UseSSL** parameter of the `Invoke-Command`, `New-PSSession`, and `Enter-PSSession` cmdlets when establishing a connection.</span></span> <span data-ttu-id="3872b-131">이 옵션은 HTTP 대신 보다 안전한 HTTPS 채널을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-131">This option uses the more secure HTTPS channel instead of HTTP.</span></span>

### <a name="do-all-remote-commands-require-powershell-remoting"></a><span data-ttu-id="3872b-132">모든 원격 명령에 PowerShell 원격이 필요 한가요?</span><span class="sxs-lookup"><span data-stu-id="3872b-132">Do all remote commands require PowerShell remoting?</span></span>

<span data-ttu-id="3872b-133">아니요.</span><span class="sxs-lookup"><span data-stu-id="3872b-133">No.</span></span> <span data-ttu-id="3872b-134">여러 cmdlet에는 원격 컴퓨터에서 개체를 가져올 수 있도록 하는 **ComputerName** 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-134">Several cmdlets have a **ComputerName** parameter that lets you get objects from the remote computer.</span></span>

<span data-ttu-id="3872b-135">이러한 cmdlet은 PowerShell 원격을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-135">These cmdlets do not use PowerShell remoting.</span></span> <span data-ttu-id="3872b-136">따라서 powershell 원격에 대해 컴퓨터를 구성 하지 않은 경우 또는 컴퓨터가 PowerShell 원격을 위한 요구 사항을 충족 하지 않는 경우에도 PowerShell을 실행 하는 모든 컴퓨터에서이 파일을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-136">So, you can use them on any computer that is running PowerShell, even if the computer is not configured for PowerShell remoting or if the computer does not meet the requirements for PowerShell remoting.</span></span>

<span data-ttu-id="3872b-137">이러한 cmdlet에는 다음이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-137">These cmdlets include the following:</span></span>

- `Get-Process`
- `Get-Service`
- `Get-WinEvent`
- `Get-EventLog`
- `Test-Connection`

<span data-ttu-id="3872b-138">**ComputerName** 매개 변수를 사용 하 여 모든 cmdlet을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-138">To find all the cmdlets with a **ComputerName** parameter, type:</span></span>

```powershell
Get-Help * -Parameter ComputerName
# or
Get-Command -ParameterName ComputerName
```

<span data-ttu-id="3872b-139">특정 cmdlet의 **ComputerName** 매개 변수가 PowerShell 원격을 사용 해야 하는지 여부를 확인 하려면 매개 변수 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-139">To determine whether the **ComputerName** parameter of a particular cmdlet requires PowerShell remoting, see the parameter description.</span></span> <span data-ttu-id="3872b-140">매개 변수 설명을 표시 하려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-140">To display the parameter description, type:</span></span>

```powershell
Get-Help <cmdlet-name> -Parameter ComputerName
```

<span data-ttu-id="3872b-141">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="3872b-141">For example:</span></span>

```powershell
Get-Help Get-Process -Parameter ComputerName
```

<span data-ttu-id="3872b-142">다른 모든 명령의 경우 cmdlet을 사용 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-142">For all other commands, use the `Invoke-Command` cmdlet.</span></span>

### <a name="how-do-i-run-a-command-on-a-remote-computer"></a><span data-ttu-id="3872b-143">원격 컴퓨터에서 명령을 실행 어떻게 할까요??</span><span class="sxs-lookup"><span data-stu-id="3872b-143">How do I run a command on a remote computer?</span></span>

<span data-ttu-id="3872b-144">원격 컴퓨터에서 명령을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-144">To run a command on a remote computer, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="3872b-145">명령을 중괄호 ()로 묶어 `{}` 스크립트 블록으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-145">Enclose your command in braces (`{}`) to make it a script block.</span></span> <span data-ttu-id="3872b-146">의 **ScriptBlock** 매개 변수를 사용 `Invoke-Command` 하 여 명령을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-146">Use the **ScriptBlock** parameter of `Invoke-Command` to specify the command.</span></span>

<span data-ttu-id="3872b-147">의 **ComputerName** 매개 변수를 사용 `Invoke-Command` 하 여 원격 컴퓨터를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-147">You can use the **ComputerName** parameter of `Invoke-Command` to specify a remote computer.</span></span> <span data-ttu-id="3872b-148">또는 원격 컴퓨터에 대 한 영구 연결 (세션)을 만든 다음의 **session** 매개 변수를 사용 `Invoke-Command` 하 여 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-148">Or, you can create a persistent connection to a remote computer (a session) and then use the **Session** parameter of `Invoke-Command` to run the command in the session.</span></span>

<span data-ttu-id="3872b-149">예를 들어 다음 명령은 `Get-Process` 명령을 원격으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-149">For example, the following commands run a `Get-Process` command remotely.</span></span>

```powershell
Invoke-Command -ComputerName Server01, Server02 -ScriptBlock {Get-Process}

#  - OR -

Invoke-Command -Session $s -ScriptBlock {Get-Process}
```

<span data-ttu-id="3872b-150">원격 명령을 중단 하려면 <kbd>CTRL</kbd> + <kbd>C</kbd>를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-150">To interrupt a remote command, type <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span> <span data-ttu-id="3872b-151">중단 요청은 원격 컴퓨터에 전달 되 고 원격 컴퓨터는 원격 명령을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-151">The interruption request is passed to the remote computer, where it terminates the remote command.</span></span>

<span data-ttu-id="3872b-152">원격 명령에 대 한 자세한 내용은 about_Remote 및 원격 기능을 지 원하는 cmdlet에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-152">For more information about remote commands, see about_Remote and the Help topics for the cmdlets that support remoting.</span></span>

### <a name="can-i-just-telnet-into-a-remote-computer"></a><span data-ttu-id="3872b-153">원격 컴퓨터에 텔넷으로 텔넷으로 사용할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-153">Can I just telnet into a remote computer?</span></span>

<span data-ttu-id="3872b-154">Cmdlet을 사용 `Enter-PSSession` 하 여 원격 컴퓨터와의 대화형 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-154">You can use the `Enter-PSSession` cmdlet to start an interactive session with a remote computer.</span></span>

<span data-ttu-id="3872b-155">PowerShell 프롬프트에서 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-155">At the PowerShell prompt, type:</span></span>

```powershell
Enter-PSSession <ComputerName>
```

<span data-ttu-id="3872b-156">명령 프롬프트가 변경 되어 원격 컴퓨터에 연결 되어 있음을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-156">The command prompt changes to show that you are connected to the remote computer.</span></span>

```
<ComputerName>\C:>
```

<span data-ttu-id="3872b-157">이제 입력 하는 명령은 원격 컴퓨터에서 직접 입력 한 것 처럼 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-157">Now, the commands that you type run on the remote computer just as though you typed them directly on the remote computer.</span></span>

<span data-ttu-id="3872b-158">대화형 세션을 종료하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-158">To end the interactive session, type:</span></span>

```powershell
Exit-PSSession
```

<span data-ttu-id="3872b-159">대화형 세션은 WS-Management 프로토콜을 사용 하는 영구 세션입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-159">An interactive session is a persistent session that uses the WS-Management protocol.</span></span> <span data-ttu-id="3872b-160">이는 Telnet을 사용 하는 것과는 동일 하지만 유사한 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-160">It is not the same as using Telnet, but it provides a similar experience.</span></span>

<span data-ttu-id="3872b-161">자세한 내용은 `Enter-PSSession`를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-161">For more information, see `Enter-PSSession`.</span></span>

### <a name="can-i-create-a-persistent-connection"></a><span data-ttu-id="3872b-162">영구 연결을 만들 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-162">Can I create a persistent connection?</span></span>

<span data-ttu-id="3872b-163">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-163">Yes.</span></span> <span data-ttu-id="3872b-164">원격 컴퓨터의 이름, NetBIOS 이름 또는 IP 주소를 지정 하 여 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-164">You can run remote commands by specifying the name of the remote computer, its NetBIOS name, or its IP address.</span></span> <span data-ttu-id="3872b-165">또는 원격 컴퓨터에 연결 된 PowerShell 세션 (PSSession)을 지정 하 여 원격 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-165">Or, you can run remote commands by specifying a PowerShell session (PSSession) that is connected to the remote computer.</span></span>

<span data-ttu-id="3872b-166">또는의 **ComputerName** 매개 변수를 사용 하는 경우 `Invoke-Command` `Enter-PSSession` PowerShell에서 임시 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-166">When you use the **ComputerName** parameter of `Invoke-Command` or `Enter-PSSession`, PowerShell establishes a temporary connection.</span></span> <span data-ttu-id="3872b-167">PowerShell은 연결을 사용 하 여 현재 명령만 실행 한 다음 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-167">PowerShell uses the connection to run only the current command, and then it closes the connection.</span></span> <span data-ttu-id="3872b-168">이 방법은 여러 원격 컴퓨터 에서도 단일 명령 또는 관련 되지 않은 여러 명령을 실행 하는 매우 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-168">This is a very efficient method for running a single command or several unrelated commands, even on many remote computers.</span></span>

<span data-ttu-id="3872b-169">Cmdlet을 사용 하 여 `New-PSSession` pssession을 만드는 경우 PowerShell은 pssession에 대 한 영구 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-169">When you use the `New-PSSession` cmdlet to create a PSSession, PowerShell establishes a persistent connection for the PSSession.</span></span> <span data-ttu-id="3872b-170">그런 다음 데이터를 공유 하는 명령을 포함 하 여 PSSession에서 여러 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-170">Then, you can run multiple commands in the PSSession, including commands that share data.</span></span>

<span data-ttu-id="3872b-171">일반적으로 데이터를 공유 하는 일련의 관련 명령을 실행 하려면 PSSession을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-171">Typically, you create a PSSession to run a series of related commands that share data.</span></span> <span data-ttu-id="3872b-172">그렇지 않으면 **ComputerName** 매개 변수로 만든 임시 연결 만으로도 대부분의 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-172">Otherwise, the temporary connection created by the **ComputerName** parameter is sufficient for most commands.</span></span>

<span data-ttu-id="3872b-173">세션에 대 한 자세한 내용은 about_PSSessions를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-173">For more information about sessions, see about_PSSessions.</span></span>

### <a name="can-i-run-commands-on-more-than-one-computer-at-a-time"></a><span data-ttu-id="3872b-174">한 번에 두 대 이상의 컴퓨터에서 명령을 실행할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-174">Can I run commands on more than one computer at a time?</span></span>

<span data-ttu-id="3872b-175">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-175">Yes.</span></span> <span data-ttu-id="3872b-176">Cmdlet의 **ComputerName** 매개 변수는 `Invoke-Command` 여러 컴퓨터 이름을 허용 하 고 **Session** 매개 변수는 여러 개의 pssession을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-176">The **ComputerName** parameter of the `Invoke-Command` cmdlet accepts multiple computer names, and the **Session** parameter accepts multiple PSSessions.</span></span>

<span data-ttu-id="3872b-177">명령을 실행 하면 `Invoke-Command` PowerShell에서 지정 된 모든 컴퓨터 또는 지정 된 모든 pssession에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-177">When you run an `Invoke-Command` command, PowerShell runs the commands on all of the specified computers or in all of the specified PSSessions.</span></span>

<span data-ttu-id="3872b-178">PowerShell은 수백 개의 동시 원격 연결을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-178">PowerShell can manage hundreds of concurrent remote connections.</span></span> <span data-ttu-id="3872b-179">그러나 전송할 수 있는 원격 명령의 수는 컴퓨터의 리소스 및 여러 네트워크 연결을 설정 하 고 유지 관리 하는 용량에 의해 제한 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-179">However, the number of remote commands that you can send might be limited by the resources of your computer and its capacity to establish and maintain multiple network connections.</span></span>

<span data-ttu-id="3872b-180">자세한 내용은 도움말 항목의 예제를 참조 `Invoke-Command` 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-180">For more information, see the example in the `Invoke-Command` Help topic.</span></span>

### <a name="where-are-my-profiles"></a><span data-ttu-id="3872b-181">내 프로필은 어디에 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-181">Where are my profiles?</span></span>

<span data-ttu-id="3872b-182">PowerShell 프로필은 원격 세션에서 자동으로 실행 되지 않으므로 프로필이 추가 하는 명령은 세션에 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-182">PowerShell profiles are not run automatically in remote sessions, so the commands that the profile adds are not present in the session.</span></span> <span data-ttu-id="3872b-183">또한 `$profile` 자동 변수는 원격 세션에서 채워지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-183">In addition, the `$profile` automatic variable is not populated in remote sessions.</span></span>

<span data-ttu-id="3872b-184">세션에서 프로필을 실행 하려면 cmdlet을 사용 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-184">To run a profile in a session, use the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="3872b-185">예를 들어 다음 명령은의 세션에서 로컬 컴퓨터의 (예: 프로필을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="3872b-185">For example, the following command runs the CurrentUserCurrentHost profile from the local computer in the session in `$s`.</span></span>

```
Invoke-Command -Session $s -FilePath $profile
```

<span data-ttu-id="3872b-186">다음 명령은의 세션에 있는 원격 컴퓨터에서 (예: 프로필을 실행 합니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="3872b-186">The following command runs the CurrentUserCurrentHost profile from the remote computer in the session in `$s`.</span></span> <span data-ttu-id="3872b-187">`$profile`변수가 채워지지 않으므로 명령은 프로필에 대 한 명시적 경로를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-187">Because the `$profile` variable is not populated, the command uses the explicit path to the profile.</span></span>

```powershell
Invoke-Command -Session $s {
  . "$home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1"
}
```

<span data-ttu-id="3872b-188">이 명령을 실행 한 후 프로필을 세션에 추가 하는 명령은에서 사용할 수 있습니다 `$s` .</span><span class="sxs-lookup"><span data-stu-id="3872b-188">After running this command, the commands that the profile adds to the session are available in `$s`.</span></span>

<span data-ttu-id="3872b-189">세션 구성에서 시작 스크립트를 사용 하 여 세션 구성을 사용 하는 모든 원격 세션에서 프로필을 실행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-189">You can also use a startup script in a session configuration to run a profile in every remote session that uses the session configuration.</span></span>

<span data-ttu-id="3872b-190">PowerShell 프로필에 대 한 자세한 내용은 about_Profiles를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-190">For more information about PowerShell profiles, see about_Profiles.</span></span>
<span data-ttu-id="3872b-191">세션 구성에 대 한 자세한 내용은을 참조 하십시오 `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="3872b-191">For more information about session configurations, see `Register-PSSessionConfiguration`.</span></span>

### <a name="how-does-throttling-work-on-remote-commands"></a><span data-ttu-id="3872b-192">원격 명령에 대 한 제한은 어떻게 작동 하나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-192">How does throttling work on remote commands?</span></span>

<span data-ttu-id="3872b-193">PowerShell에는 로컬 컴퓨터의 리소스를 관리 하는 데 도움이 되도록 각 명령에 대해 설정 되는 동시 원격 연결 수를 제한할 수 있는 명령 당 제한 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-193">To help you manage the resources on your local computer, PowerShell includes a per-command throttling feature that lets you limit the number of concurrent remote connections that are established for each command.</span></span>

<span data-ttu-id="3872b-194">기본값은 32 동시 연결 이지만 cmdlet의 **ThrottleLimit** 매개 변수를 사용 하 여 특정 명령에 대 한 사용자 지정 스로틀 제한을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-194">The default is 32 concurrent connections, but you can use the **ThrottleLimit** parameter of the cmdlets to set a custom throttle limit for particular commands.</span></span>

<span data-ttu-id="3872b-195">제한 기능을 사용 하는 경우 전체 세션이 아닌 컴퓨터에 적용 되는 것이 아니라 각 명령에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-195">When you use the throttling feature, remember that it is applied to each command, not to the entire session or to the computer.</span></span> <span data-ttu-id="3872b-196">여러 세션이 나 pssession에서 동시에 명령을 실행 하는 경우 동시 연결 수는 모든 세션에서 동시 연결의 합계입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-196">If you are running commands concurrently in several sessions or PSSessions, the number of concurrent connections is the sum of the concurrent connections in all the sessions.</span></span>

<span data-ttu-id="3872b-197">**ThrottleLimit** 매개 변수를 사용 하 여 cmdlet을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-197">To find cmdlets with a **ThrottleLimit** parameter, type:</span></span>

```
Get-Help * -Parameter ThrottleLimit
-or-
Get-Command -ParameterName ThrottleLimit
```

### <a name="is-the-output-of-remote-commands-different-from-local-output"></a><span data-ttu-id="3872b-198">원격 명령의 출력이 로컬 출력과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-198">Is the output of remote commands different from local output?</span></span>

<span data-ttu-id="3872b-199">PowerShell을 로컬로 사용 하는 경우 "live" .NET Framework 개체를 보내고 받습니다. "라이브" 개체는 실제 프로그램 또는 시스템 구성 요소와 연결 된 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-199">When you use PowerShell locally, you send and receive "live" .NET Framework objects; "live" objects are objects that are associated with actual programs or system components.</span></span> <span data-ttu-id="3872b-200">메서드를 호출 하거나 라이브 개체의 속성을 변경 하면 변경 내용이 실제 프로그램이 나 구성 요소에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-200">When you invoke the methods or change the properties of live objects, the changes affect the actual program or component.</span></span> <span data-ttu-id="3872b-201">또한 프로그램 또는 구성 요소의 속성을 변경 하면 해당 속성을 나타내는 개체의 속성도 변경 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-201">And, when the properties of a program or component change, the properties of the object that represent them also change.</span></span>

<span data-ttu-id="3872b-202">그러나 대부분의 라이브 개체는 네트워크를 통해 전송할 수 없으므로 PowerShell에서 원격 명령에 전송 된 대부분의 개체를 "serialize" 합니다. 즉, 각 개체를 전송에 대 한 일련의 XML (XML [Export-clixml]) 데이터 요소로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-202">However, because most live objects cannot be transmitted over the network, PowerShell "serializes" most of the objects sent in remote commands, that is, it converts each object into a series of XML (Constraint Language in XML [CLiXML]) data elements for transmission.</span></span>

<span data-ttu-id="3872b-203">PowerShell은 직렬화 된 개체를 받을 때 XML을 deserialize 된 개체 형식으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-203">When PowerShell receives a serialized object, it converts the XML into a deserialized object type.</span></span> <span data-ttu-id="3872b-204">Deserialize 된 개체는 이전에 프로그램 또는 구성 요소의 속성에 대 한 정확한 레코드 이지만 더 이상 "라이브"가 아닙니다. 즉, 더 이상 구성 요소에 직접 연결 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-204">The deserialized object is an accurate record of the properties of the program or component at a previous time, but it is no longer "live", that is, it is no longer directly associated with the component.</span></span> <span data-ttu-id="3872b-205">그리고 메서드는 더 이상 유효 하지 않기 때문에 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-205">And, the methods are removed because they are no longer effective.</span></span>

<span data-ttu-id="3872b-206">일반적으로 라이브 개체를 사용 하는 것 처럼 deserialize 된 개체를 사용할 수 있지만 제한 사항을 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-206">Typically, you can use deserialized objects just as you would use live objects, but you must be aware of their limitations.</span></span> <span data-ttu-id="3872b-207">또한 cmdlet에서 반환 되는 개체에는 `Invoke-Command` 명령의 원본을 결정 하는 데 도움이 되는 추가 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-207">Also, the objects that are returned by the `Invoke-Command` cmdlet have additional properties that help you to determine the origin of the command.</span></span>

<span data-ttu-id="3872b-208">System.io.directoryinfo 개체 및 Guid와 같은 일부 개체 유형은 수신 될 때 라이브 개체로 다시 변환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-208">Some object types, such as DirectoryInfo objects and GUIDs, are converted back into live objects when they are received.</span></span> <span data-ttu-id="3872b-209">이러한 개체는 특별 한 처리 나 서식 지정이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-209">These objects do not need any special handling or formatting.</span></span>

<span data-ttu-id="3872b-210">원격 출력을 해석 하 고 형식을 지정 하는 방법에 대 한 자세한 내용은 [about_Remote_Output](about_Remote_Output.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-210">For information about interpreting and formatting remote output, see [about_Remote_Output](about_Remote_Output.md).</span></span>

### <a name="can-i-run-background-jobs-remotely"></a><span data-ttu-id="3872b-211">백그라운드 작업을 원격으로 실행할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-211">Can I run background jobs remotely?</span></span>

<span data-ttu-id="3872b-212">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-212">Yes.</span></span> <span data-ttu-id="3872b-213">PowerShell 백그라운드 작업은 세션과 상호 작용 하지 않고 비동기적으로 실행 되는 PowerShell 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-213">A PowerShell background job is a PowerShell command that runs asynchronously without interacting with the session.</span></span> <span data-ttu-id="3872b-214">백그라운드 작업을 시작 하는 경우 명령 프롬프트가 즉시 반환 되며, 오랜 시간 동안 실행 되는 경우에도 작업이 실행 되는 동안 세션에서 계속 작업할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-214">When you start a background job, the command prompt returns immediately, and you can continue to work in the session while the job runs even if it runs for an extended period of time.</span></span>

<span data-ttu-id="3872b-215">백그라운드 작업은 항상 임시 세션에서 비동기적으로 실행 되므로 다른 명령이 실행 되는 동안에도 백그라운드 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-215">You can start a background job even while other commands are running because background jobs always run asynchronously in a temporary session.</span></span>

<span data-ttu-id="3872b-216">로컬 또는 원격 컴퓨터에서 백그라운드 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-216">You can run background jobs on a local or remote computer.</span></span> <span data-ttu-id="3872b-217">기본적으로 백그라운드 작업은 로컬 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-217">By default, a background job runs on the local computer.</span></span> <span data-ttu-id="3872b-218">그러나 cmdlet의 **AsJob** 매개 변수를 사용 하 여 `Invoke-Command` 모든 원격 명령을 백그라운드 작업으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-218">However, you can use the **AsJob** parameter of the `Invoke-Command` cmdlet to run any remote command as a background job.</span></span> <span data-ttu-id="3872b-219">를 사용 `Invoke-Command` 하 여 `Start-Job` 명령을 원격으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-219">And, you can use `Invoke-Command` to run a `Start-Job` command remotely.</span></span>

<span data-ttu-id="3872b-220">PowerShell의 백그라운드 작업에 대 한 자세한 내용은 [about_Jobs (about_Jobs)] 및 [about_Remote_Jobs (about_Remote_Jobs)]를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-220">For more information about background jobs in PowerShell , see [about_Jobs(about_Jobs.md)] and [about_Remote_Jobs(about_Remote_Jobs.md)].</span></span>

### <a name="can-i-run-windows-programs-on-a-remote-computer"></a><span data-ttu-id="3872b-221">원격 컴퓨터에서 windows 프로그램을 실행할 수 있습니까?</span><span class="sxs-lookup"><span data-stu-id="3872b-221">Can I run windows programs on a remote computer?</span></span>

<span data-ttu-id="3872b-222">PowerShell 원격 명령을 사용 하 여 원격 컴퓨터에서 Windows 기반 프로그램을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-222">You can use PowerShell remote commands to run Windows-based programs on remote computers.</span></span> <span data-ttu-id="3872b-223">예를 들어 `Shutdown.exe` 원격 컴퓨터에서 또는를 실행할 수 있습니다 `Ipconfig.exe` .</span><span class="sxs-lookup"><span data-stu-id="3872b-223">For example, you can run `Shutdown.exe` or `Ipconfig.exe` on a remote computer.</span></span>

<span data-ttu-id="3872b-224">그러나 PowerShell 명령을 사용 하 여 원격 컴퓨터의 프로그램에 대 한 사용자 인터페이스를 열 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-224">However, you cannot use PowerShell commands to open the user interface for any program on a remote computer.</span></span>

<span data-ttu-id="3872b-225">원격 컴퓨터에서 Windows 프로그램을 시작 하면 명령이 완료 되지 않으며, 프로그램이 완료 되거나 <kbd>CTRL</kbd> + <kbd>C</kbd> 를 눌러 명령을 중단할 때까지 PowerShell 명령 프롬프트가 반환 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-225">When you start a Windows program on a remote computer, the command is not completed, and the PowerShell command prompt does not return, until the program is finished or until you press <kbd>CTRL</kbd>+<kbd>C</kbd> to interrupt the command.</span></span> <span data-ttu-id="3872b-226">예를 들어 원격 컴퓨터에서 프로그램을 실행 하는 경우 `Ipconfig.exe` 이 완료 될 때까지 명령 프롬프트가 반환 되지 않습니다 `Ipconfig.exe` .</span><span class="sxs-lookup"><span data-stu-id="3872b-226">For example, if you run the `Ipconfig.exe` program on a remote computer, the command prompt does not return until `Ipconfig.exe` is completed.</span></span>

<span data-ttu-id="3872b-227">원격 명령을 사용 하 여 사용자 인터페이스를 포함 하는 프로그램을 시작 하면 프로그램 프로세스가 시작 되지만 사용자 인터페이스가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-227">If you use remote commands to start a program that has a user interface, the program process starts, but the user interface does not appear.</span></span> <span data-ttu-id="3872b-228">PowerShell 명령이 완료 되지 않고 프로그램 프로세스를 중지 하거나 <kbd>ctrl</kbd>C를 누를 때까지 명령 프롬프트가 반환 되지 않습니다 .이 경우 + <kbd></kbd>명령이 중단 되 고 프로세스가 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-228">The PowerShell command is not completed, and the command prompt does not return until you stop the program process or until you press <kbd>CTRL</kbd>+<kbd>C</kbd>, which interrupts the command and stops the process.</span></span>

<span data-ttu-id="3872b-229">예를 들어 PowerShell 명령을 사용 하 여 원격 컴퓨터에서 실행 하는 경우 `Notepad` 메모장 프로세스가 원격 컴퓨터에서 시작 되지만 메모장 사용자 인터페이스가 나타나지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-229">For example, if you use a PowerShell command to run `Notepad` on a remote computer, the Notepad process starts on the remote computer, but the Notepad user interface does not appear.</span></span> <span data-ttu-id="3872b-230">명령을 중단 하 고 명령 프롬프트를 복원 하려면 <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-230">To interrupt the command and restore the command prompt, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

### <a name="can-i-limit-the-commands-that-users-can-run-remotely-on-my-computer"></a><span data-ttu-id="3872b-231">사용자가 컴퓨터에서 원격으로 실행할 수 있는 명령을 제한할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-231">Can I limit the commands that users can run remotely on my computer?</span></span>

<span data-ttu-id="3872b-232">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-232">Yes.</span></span> <span data-ttu-id="3872b-233">모든 원격 세션은 원격 컴퓨터의 세션 구성 중 하나를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-233">Every remote session must use one of the session configurations on the remote computer.</span></span> <span data-ttu-id="3872b-234">컴퓨터의 세션 구성 및 해당 세션 구성에 대 한 권한을 관리 하 여 컴퓨터에서 원격으로 명령을 실행할 수 있는 사용자와 실행할 수 있는 명령을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-234">You can manage the session configurations on your computer (and the permissions to those session configurations) to determine who can run commands remotely on your computer and which commands they can run.</span></span>

<span data-ttu-id="3872b-235">세션 구성은 세션에 대 한 환경을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-235">A session configuration configures the environment for the session.</span></span> <span data-ttu-id="3872b-236">새 구성 클래스를 구현 하는 어셈블리를 사용 하거나 세션에서 실행 되는 스크립트를 사용 하 여 구성을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-236">You can define the configuration by using an assembly that implements a new configuration class or by using a script that runs in the session.</span></span> <span data-ttu-id="3872b-237">구성에 따라 세션에서 사용할 수 있는 명령이 결정 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-237">The configuration can determine the commands that are available in the session.</span></span>
<span data-ttu-id="3872b-238">그리고 구성에는 세션이 단일 개체나 명령에서 원격으로 받을 수 있는 데이터 양을 제한 하는 설정과 같이 컴퓨터를 보호 하는 설정이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-238">And, the configuration can include settings that protect the computer, such as settings that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="3872b-239">구성을 사용 하는 데 필요한 사용 권한을 결정 하는 보안 설명자를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-239">You can also specify a security descriptor that determines the permissions that are required to use the configuration.</span></span>

<span data-ttu-id="3872b-240">`Enable-PSRemoting`이 cmdlet은 컴퓨터에 microsoft.powershell32 (64 비트 운영 체제에만 해당)의 기본 세션 구성을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-240">The `Enable-PSRemoting` cmdlet creates the default session configurations on your computer: Microsoft.PowerShell, Microsoft.PowerShell.Workflow, and Microsoft.PowerShell32 (64-bit operating systems only).</span></span> <span data-ttu-id="3872b-241">`Enable-PSRemoting` 컴퓨터에서 Administrators 그룹의 구성원만 사용할 수 있도록 구성의 보안 설명자를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-241">`Enable-PSRemoting` sets the security descriptor for the configuration to allow only members of the Administrators group on your computer to use them.</span></span>

<span data-ttu-id="3872b-242">세션 구성 cmdlet을 사용 하 여 기본 세션 구성을 편집 하 고, 새 세션 구성을 만들고, 모든 세션 구성의 보안 설명자를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-242">You can use the session configuration cmdlets to edit the default session configurations, to create new session configurations, and to change the security descriptors of all the session configurations.</span></span>

<span data-ttu-id="3872b-243">Windows PowerShell 3.0부터 `New-PSSessionConfigurationFile` cmdlet을 사용 하면 텍스트 파일을 사용 하 여 사용자 지정 세션 구성을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-243">Beginning in Windows PowerShell 3.0, the `New-PSSessionConfigurationFile` cmdlet lets you create custom session configurations by using a text file.</span></span> <span data-ttu-id="3872b-244">이 파일에는 언어 모드를 설정 하 고 세션 구성을 사용 하는 세션에서 사용 가능한 cmdlet 및 모듈을 지정 하는 옵션이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-244">The file includes options for setting the language mode and for specifying the cmdlets and modules that are available in sessions that use the session configuration.</span></span>

<span data-ttu-id="3872b-245">사용자가, 또는 cmdlet을 사용 하는 경우 `Invoke-Command` `New-PSSession` `Enter-PSSession` **ConfigurationName** 매개 변수를 사용 하 여 세션에 사용 되는 세션 구성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-245">When users use the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets, they can use the **ConfigurationName** parameter to indicate the session configuration that is used for the session.</span></span> <span data-ttu-id="3872b-246">또한 세션의 기본 설정 변수 값을 변경 하 여 해당 세션에서 사용 하는 기본 구성을 변경할 수 있습니다 `$PSSessionConfigurationName` .</span><span class="sxs-lookup"><span data-stu-id="3872b-246">And, they can change the default configuration that their sessions use by changing the value of the `$PSSessionConfigurationName` preference variable in the session.</span></span>

<span data-ttu-id="3872b-247">세션 구성에 대 한 자세한 내용은 세션 구성 cmdlet에 대 한 도움말을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-247">For more information about session configurations, see the Help for the session configuration cmdlets.</span></span> <span data-ttu-id="3872b-248">세션 구성 cmdlet을 찾으려면 다음을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-248">To find the session configuration cmdlets, type:</span></span>

```powershell
Get-Command *PSSessionConfiguration
```

### <a name="what-are-fan-in-and-fan-out-configurations"></a><span data-ttu-id="3872b-249">팬 및 팬 구성 이란?</span><span class="sxs-lookup"><span data-stu-id="3872b-249">What are fan in and fan out configurations?</span></span>

<span data-ttu-id="3872b-250">여러 컴퓨터를 포함 하는 가장 일반적인 PowerShell 원격 시나리오는 일 대 다 구성으로, 하나의 로컬 컴퓨터 (관리자 컴퓨터)가 여러 원격 컴퓨터에서 PowerShell 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-250">The most common PowerShell remoting scenario involving multiple computers is the one-to-many configuration, in which one local computer (the administrator's computer) runs PowerShell commands on numerous remote computers.</span></span> <span data-ttu-id="3872b-251">이를 "팬 아웃" 시나리오 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-251">This is known as the "fan-out" scenario.</span></span>

<span data-ttu-id="3872b-252">그러나 일부 기업에서는 많은 클라이언트 컴퓨터가 PowerShell을 실행 하는 단일 원격 컴퓨터 (예: 파일 서버 또는 키오스크)에 연결 하는 다 대 일 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-252">However, in some enterprises, the configuration is many-to-one, where many client computers connect to a single remote computer that is running PowerShell, such as a file server or a kiosk.</span></span> <span data-ttu-id="3872b-253">이를 "팬" 구성 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-253">This is known as the "fan-in" configuration.</span></span>

<span data-ttu-id="3872b-254">PowerShell remoting은 팬 아웃 및 팬 인 구성을 모두 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-254">PowerShell remoting supports both fan-out and fan-in configurations.</span></span>

<span data-ttu-id="3872b-255">팬 아웃 구성의 경우 PowerShell은 ws-management (Web Services for Management) 프로토콜 및 WS-MANAGEMENT의 Microsoft 구현을 지 원하는 WinRM 서비스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-255">For the fan-out configuration, PowerShell uses the Web Services for Management (WS-Management) protocol and the WinRM service that supports the Microsoft implementation of WS-Management.</span></span> <span data-ttu-id="3872b-256">로컬 컴퓨터가 원격 컴퓨터에 연결 하는 경우 WS-Management 연결을 설정 하 고 PowerShell 용 플러그 인을 사용 하 여 원격 컴퓨터에서 PowerShell 호스트 프로세스 (Wsmprovhost.exe)를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-256">When a local computer connects to a remote computer, WS-Management establishes a connection and uses a plug-in for PowerShell to start the PowerShell host process (Wsmprovhost.exe) on the remote computer.</span></span> <span data-ttu-id="3872b-257">사용자는 대체 포트, 대체 세션 구성 및 기타 기능을 지정 하 여 원격 연결을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-257">The user can specify an alternate port, an alternate session configuration, and other features to customize the remote connection.</span></span>

<span data-ttu-id="3872b-258">"팬 인" 구성을 지원 하기 위해 PowerShell은 IIS (인터넷 정보 서비스)를 사용 하 여 WS 관리를 호스팅하고 PowerShell 플러그 인을 로드 하 고 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-258">To support the "fan-in" configuration, PowerShell uses internet Information Services (IIS) to host WS-Management, to load the PowerShell plug-in, and to start PowerShell.</span></span> <span data-ttu-id="3872b-259">이 시나리오에서는 별도의 프로세스에서 각 PowerShell 세션을 시작 하는 대신 모든 PowerShell 세션이 동일한 호스트 프로세스에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-259">In this scenario, instead of starting each PowerShell session in a separate process, all PowerShell sessions run in the same host process.</span></span>

<span data-ttu-id="3872b-260">Windows XP 또는 Windows Server 2003에서는 IIS 호스팅 및 팬 인 원격 관리가 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-260">IIS hosting and fan-in remote management is not supported in Windows XP or in Windows Server 2003.</span></span>

<span data-ttu-id="3872b-261">사용자는 팬 인 구성에서 전송, 컴퓨터 이름, 포트 및 응용 프로그램 이름을 포함 하 여 연결 URI 및 HTTP 끝점을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-261">In a fan-in configuration, the user can specify a connection URI and an HTTP endpoint, including the transport, computer name, port, and application name.</span></span>
<span data-ttu-id="3872b-262">IIS는 지정 된 응용 프로그램 이름을 가진 모든 요청을 응용 프로그램에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-262">IIS forwards all the requests with a specified application name to the application.</span></span> <span data-ttu-id="3872b-263">기본값은 PowerShell을 호스트할 수 있는 WS-MANAGEMENT입니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-263">The default is WS-Management, which can host PowerShell.</span></span>

<span data-ttu-id="3872b-264">인증 메커니즘을 지정 하 고 HTTP 및 HTTPS 끝점에서 리디렉션을 허용 하거나 허용 하지 않도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-264">You can also specify an authentication mechanism and prohibit or allow redirection from HTTP and HTTPS endpoints.</span></span>

### <a name="can-i-test-remoting-on-a-single-computer-not-in-a-domain"></a><span data-ttu-id="3872b-265">도메인에 없는 단일 컴퓨터에서 원격을 테스트할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-265">Can I test remoting on a single computer not in a domain?</span></span>

<span data-ttu-id="3872b-266">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-266">Yes.</span></span> <span data-ttu-id="3872b-267">로컬 컴퓨터가 도메인에 있지 않은 경우에도 PowerShell 원격 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-267">PowerShell remoting is available even when the local computer is not in a domain.</span></span> <span data-ttu-id="3872b-268">원격 기능을 사용 하 여 세션에 연결 하 고 동일한 컴퓨터에 세션을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-268">You can use the remoting features to connect to sessions and to create sessions on the same computer.</span></span> <span data-ttu-id="3872b-269">기능은 원격 컴퓨터에 연결할 때와 동일 하 게 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-269">The features work the same as they do when you connect to a remote computer.</span></span>

<span data-ttu-id="3872b-270">작업 그룹의 컴퓨터에서 원격 명령을 실행 하려면 컴퓨터에서 다음 Windows 설정을 변경 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-270">To run remote commands on a computer in a workgroup, change the following Windows settings on the computer.</span></span>

<span data-ttu-id="3872b-271">주의: 이러한 설정은 시스템의 모든 사용자에 게 영향을 주며 시스템이 악의적인 공격에 더 취약 해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-271">Caution: These settings affect all users on the system and they can make the system more vulnerable to a malicious attack.</span></span> <span data-ttu-id="3872b-272">이러한 변경을 수행 하는 경우 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-272">Use caution when making these changes.</span></span>

- <span data-ttu-id="3872b-273">Windows Vista, Windows 7, Windows 8:</span><span class="sxs-lookup"><span data-stu-id="3872b-273">Windows Vista, Windows 7, Windows 8:</span></span>

  <span data-ttu-id="3872b-274">다음 레지스트리 항목을 만들고 해당 값을 1: LocalAccountTokenFilterPolicy in으로 설정 합니다. ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span><span class="sxs-lookup"><span data-stu-id="3872b-274">Create the following registry entry, and then set its value to 1: LocalAccountTokenFilterPolicy in ` HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System`</span></span>

  <span data-ttu-id="3872b-275">다음 PowerShell 명령을 사용 하 여이 항목을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-275">You can use the following PowerShell command to add this entry:</span></span>

    ```powershell
    $parameters = @{
      Path='HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System'
      Name='LocalAccountTokenFilterPolicy'
      propertyType='DWord'
      Value=1
    }
    New-ItemProperty @parameters
    ```

- <span data-ttu-id="3872b-276">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span><span class="sxs-lookup"><span data-stu-id="3872b-276">Windows Server 2003, Windows Server 2008, Windows Server 2012, Windows Server 2012 R2:</span></span>

  <span data-ttu-id="3872b-277">"네트워크 액세스: 로컬 계정에 대 한 공유 및 보안 모델" 정책의 기본 설정이 "클래식" 이므로 변경이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-277">No changes are needed because the default setting of the "Network Access: Sharing and security model for local accounts" policy is "Classic".</span></span> <span data-ttu-id="3872b-278">변경 된 경우 설정을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-278">Verify the setting in case it has changed.</span></span>

### <a name="can-i-run-remote-commands-on-a-computer-in-another-domain"></a><span data-ttu-id="3872b-279">다른 도메인의 컴퓨터에서 원격 명령을 실행할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-279">Can I run remote commands on a computer in another domain?</span></span>

<span data-ttu-id="3872b-280">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-280">Yes.</span></span> <span data-ttu-id="3872b-281">일반적으로 명령은 오류 없이 실행 되지만, 또는 cmdlet의 **Credential** 매개 변수를 사용 하 여 `Invoke-Command` `New-PSSession` `Enter-PSSession` 원격 컴퓨터의 Administrators 그룹 구성원에 대 한 자격 증명을 제공 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-281">Typically, the commands run without error, although you might need to use the **Credential** parameter of the `Invoke-Command`, `New-PSSession`, or `Enter-PSSession` cmdlets to provide the credentials of a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="3872b-282">현재 사용자가 로컬 및 원격 컴퓨터에서 Administrators 그룹의 구성원 인 경우에도이 과정이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-282">This is sometimes required even when the current user is a member of the Administrators group on the local and remote computers.</span></span>

<span data-ttu-id="3872b-283">그러나 원격 컴퓨터가 로컬 컴퓨터가 신뢰 하는 도메인에 있지 않은 경우에는 원격 컴퓨터가 사용자의 자격 증명을 인증 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-283">However, if the remote computer is not in a domain that the local computer trusts, the remote computer might not be able to authenticate the user's credentials.</span></span>

<span data-ttu-id="3872b-284">인증을 사용 하도록 설정 하려면 다음 명령을 사용 하 여 WinRM의 로컬 컴퓨터에 대 한 신뢰할 수 있는 호스트 목록에 원격 컴퓨터를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-284">To enable authentication, use the following command to add the remote computer to the list of trusted hosts for the local computer in WinRM.</span></span> <span data-ttu-id="3872b-285">PowerShell 프롬프트에서 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-285">Type the command at the PowerShell prompt.</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value <Remote-computer-name>
```

<span data-ttu-id="3872b-286">예를 들어 로컬 컴퓨터의 신뢰할 수 있는 호스트 목록에 Server01 컴퓨터를 추가 하려면 PowerShell 프롬프트에서 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3872b-286">For example, to add the Server01 computer to the list of trusted hosts on the local computer, type the following command at the PowerShell prompt:</span></span>

```powershell
Set-Item WSMan:\localhost\Client\TrustedHosts -Value Server01
```

### <a name="does-powershell-support-remoting-over-ssh"></a><span data-ttu-id="3872b-287">PowerShell에서 SSH를 통한 원격 지원을 지원 하나요?</span><span class="sxs-lookup"><span data-stu-id="3872b-287">Does PowerShell support remoting over SSH?</span></span>

<span data-ttu-id="3872b-288">예.</span><span class="sxs-lookup"><span data-stu-id="3872b-288">Yes.</span></span> <span data-ttu-id="3872b-289">자세한 내용은 [SSH를 통한 PowerShell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3872b-289">For more information, see [PowerShell remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="see-also"></a><span data-ttu-id="3872b-290">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3872b-290">See also</span></span>

[<span data-ttu-id="3872b-291">about_Remote</span><span class="sxs-lookup"><span data-stu-id="3872b-291">about_Remote</span></span>](about_Remote.md)

[<span data-ttu-id="3872b-292">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="3872b-292">about_Profiles</span></span>](about_Profiles.md)

[<span data-ttu-id="3872b-293">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="3872b-293">about_PSSessions</span></span>](about_PSSessions.md)

[<span data-ttu-id="3872b-294">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="3872b-294">about_Remote_Jobs</span></span>](about_Remote_Jobs.md)

[<span data-ttu-id="3872b-295">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="3872b-295">about_Remote_Variables</span></span>](about_Remote_Variables.md)

[<span data-ttu-id="3872b-296">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="3872b-296">Invoke-Command</span></span>](xref:Microsoft.PowerShell.Core.Invoke-Command)

[<span data-ttu-id="3872b-297">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="3872b-297">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)