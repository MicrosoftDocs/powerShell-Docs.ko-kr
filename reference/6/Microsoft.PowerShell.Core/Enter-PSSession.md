---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 3b087eb53fa575b2af7b18ec17823f9197e719d6
ms.sourcegitcommit: 9dddf1d2e91ebcd347fcfb7bf6ef670d49a12ab7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/24/2020
ms.locfileid: "93218938"
---
# <span data-ttu-id="b8059-103">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-103">Enter-PSSession</span></span>

## <span data-ttu-id="b8059-104">개요</span><span class="sxs-lookup"><span data-stu-id="b8059-104">SYNOPSIS</span></span>
<span data-ttu-id="b8059-105">원격 컴퓨터와 대화형 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-105">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="b8059-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b8059-106">SYNTAX</span></span>

### <span data-ttu-id="b8059-107">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="b8059-107">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="b8059-108">SSHHost</span><span class="sxs-lookup"><span data-stu-id="b8059-108">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### <span data-ttu-id="b8059-109">세션</span><span class="sxs-lookup"><span data-stu-id="b8059-109">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="b8059-110">URI</span><span class="sxs-lookup"><span data-stu-id="b8059-110">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="b8059-111">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b8059-111">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="b8059-112">Id</span><span class="sxs-lookup"><span data-stu-id="b8059-112">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="b8059-113">Name</span><span class="sxs-lookup"><span data-stu-id="b8059-113">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="b8059-114">VMId</span><span class="sxs-lookup"><span data-stu-id="b8059-114">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="b8059-115">VMName</span><span class="sxs-lookup"><span data-stu-id="b8059-115">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="b8059-116">ContainerId</span><span class="sxs-lookup"><span data-stu-id="b8059-116">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="b8059-117">설명</span><span class="sxs-lookup"><span data-stu-id="b8059-117">DESCRIPTION</span></span>

<span data-ttu-id="b8059-118">`Enter-PSSession`Cmdlet은 단일 원격 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-118">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="b8059-119">세션 중에 입력 하는 명령은 원격 컴퓨터에서 직접 입력 하는 것 처럼 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-119">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="b8059-120">한 번에 하나의 대화형 세션만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-120">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="b8059-121">일반적으로 **ComputerName** 매개 변수를 사용하여 원격 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-121">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="b8059-122">그러나 대화형 세션에 cmdlet을 사용 하 여 만든 세션을 사용할 수도 있습니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b8059-122">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="b8059-123">그러나 `Disconnect-PSSession` , `Connect-PSSession` 또는 cmdlet을 사용 하 여 `Receive-PSSession` 대화형 세션에서 연결을 끊거나 다시 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-123">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="b8059-124">PowerShell 6.0부터 ssh (Secure Shell)를 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 하 고, SSH를 로컬 컴퓨터에서 사용할 수 있고, 원격 컴퓨터가 PowerShell SSH 끝점을 사용 하 여 구성 된 경우 원격 컴퓨터에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-124">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="b8059-125">SSH 기반 PowerShell 원격 세션의 혜택은 여러 플랫폼 (Windows, Linux, macOS)에서 작동 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-125">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="b8059-126">SSH 기반 원격의 경우 **HostName** 매개 변수 집합을 사용 하 여 원격 컴퓨터 및 관련 연결 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-126">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="b8059-127">PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-127">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="b8059-128">대화형 세션을 종료 하 고 원격 컴퓨터와의 연결을 끊으려면 `Exit-PSSession` cmdlet을 사용 하거나를 입력 `exit` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-128">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="b8059-129">예제</span><span class="sxs-lookup"><span data-stu-id="b8059-129">EXAMPLES</span></span>

### <span data-ttu-id="b8059-130">예제 1: 대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="b8059-130">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="b8059-131">이 명령은 로컬 컴퓨터에서 대화형 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-131">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="b8059-132">명령 프롬프트가 변경되어 현재 다른 세션에서 명령을 실행하고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-132">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="b8059-133">입력한 명령은 새 세션에서 실행되고 결과가 기본 세션에 텍스트로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-133">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="b8059-134">예제 2: 대화형 세션 작업</span><span class="sxs-lookup"><span data-stu-id="b8059-134">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="b8059-135">첫 번째 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01, 원격 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-135">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="b8059-136">세션이 시작되면 명령 프롬프트가 변경되어 컴퓨터 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-136">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="b8059-137">두 번째 명령은 PowerShell 프로세스를 가져오고 출력을 Process.txt 파일로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-137">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="b8059-138">이 명령은 원격 컴퓨터에 전송되고 Process.txt 파일이 원격 컴퓨터에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-138">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="b8059-139">세 번째 명령은 **Exit** 키워드를 사용 하 여 대화형 세션을 종료 하 고 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-139">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="b8059-140">네 번째 명령은 Process.txt 파일이 원격 컴퓨터에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-140">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="b8059-141">`Get-ChildItem`로컬 컴퓨터의 ("dir") 명령으로 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-141">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

```powershell
PS C:\> Enter-PSSession -ComputerName Server01
[Server01]: PS>
[Server01]: PS C:\> Get-Process PowerShell > C:\ps-test\Process.txt
[Server01]: PS C:\> exit
PS C:\>
PS C:\> dir C:\ps-test\process.txt
Get-ChildItem : Cannot find path 'C:\ps-test\process.txt' because it does not exist.
At line:1 char:4
+ dir <<<<  c:\ps-test\process.txt
```

<span data-ttu-id="b8059-142">이 명령은 원격 컴퓨터와의 대화형 세션에서 작업하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-142">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="b8059-143">예 3: Session 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="b8059-143">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="b8059-144">이러한 명령은의 **Session** 매개 변수를 사용 `Enter-PSSession` 하 여 기존 PowerShell 세션 ( **PSSession** )에서 대화형 세션을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-144">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session ( **PSSession** ).</span></span>

### <span data-ttu-id="b8059-145">예 4: 대화형 세션을 시작 하 고 포트 및 자격 증명 매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="b8059-145">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="b8059-146">이 명령은 Server01 컴퓨터와 대화형 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-146">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="b8059-147">**Port** 매개 변수를 사용 하 여 포트를 지정 하 고 **Credential** 매개 변수를 사용 하 여 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자의 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-147">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="b8059-148">예 5: 대화형 세션 중지</span><span class="sxs-lookup"><span data-stu-id="b8059-148">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="b8059-149">이 예제에서는 대화형 세션을 시작하고 중지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-149">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="b8059-150">첫 번째 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-150">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="b8059-151">두 번째 명령은 cmdlet을 사용 하 여 `Exit-PSSession` 세션을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-151">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="b8059-152">**Exit** 키워드를 사용 하 여 대화형 세션을 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-152">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="b8059-153">`Exit-PSSession` 및 **종료** 는 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-153">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="b8059-154">예제 6: SSH를 사용 하 여 대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="b8059-154">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="b8059-155">이 예제에서는 Secure Shell (SSH)를 사용 하 여 대화형 세션을 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-155">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="b8059-156">SSH가 원격 컴퓨터에서 암호를 묻는 메시지를 표시 하도록 구성 된 경우 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-156">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="b8059-157">그렇지 않은 경우에는 SSH 키 기반 사용자 인증을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-157">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="b8059-158">예 7: SSH를 사용 하 여 대화형 세션을 시작 하 고 포트 및 사용자 인증 키 지정</span><span class="sxs-lookup"><span data-stu-id="b8059-158">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="b8059-159">이 예제에서는 SSH를 사용 하 여 대화형 세션을 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-159">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="b8059-160">**Port** 매개 변수를 사용 하 여 사용할 포트를 지정 하 고 **keyfilepath** 매개 변수를 사용 하 여 원격 컴퓨터에서 사용자를 인증 하는 데 사용 되는 RSA 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-160">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="b8059-161">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b8059-161">PARAMETERS</span></span>

### <span data-ttu-id="b8059-162">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="b8059-162">-AllowRedirection</span></span>

<span data-ttu-id="b8059-163">이 연결을 대체 URI(Uniform Resource Identifier)로 리디렉션할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-163">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="b8059-164">기본적으로 리디렉션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-164">By default, redirection is not allowed.</span></span>

<span data-ttu-id="b8059-165">**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-165">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="b8059-166">기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-166">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="b8059-167">또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-167">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="b8059-168">Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 `$PSSessionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-168">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="b8059-169">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-169">The default value is 5.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-170">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="b8059-170">-ApplicationName</span></span>

<span data-ttu-id="b8059-171">연결 URI의 애플리케이션 이름 세그먼트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-171">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="b8059-172">명령에서 **ConnectionURI**  매개 변수를 사용하지 않는 경우 이 매개 변수를 사용하여 응용 프로그램 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-172">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="b8059-173">기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-173">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="b8059-174">이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-174">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="b8059-175">이 값은 대부분의 사용에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-175">This value is appropriate for most uses.</span></span> <span data-ttu-id="b8059-176">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-176">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="b8059-177">**WinRM** 서비스는 응용 프로그램 이름을 사용 하 여 연결 요청을 처리 하는 수신기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-177">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="b8059-178">이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-178">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-179">-인증</span><span class="sxs-lookup"><span data-stu-id="b8059-179">-Authentication</span></span>

<span data-ttu-id="b8059-180">사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-180">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="b8059-181">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-181">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b8059-182">기본값</span><span class="sxs-lookup"><span data-stu-id="b8059-182">Default</span></span>
- <span data-ttu-id="b8059-183">Basic</span><span class="sxs-lookup"><span data-stu-id="b8059-183">Basic</span></span>
- <span data-ttu-id="b8059-184">Credssp</span><span class="sxs-lookup"><span data-stu-id="b8059-184">Credssp</span></span>
- <span data-ttu-id="b8059-185">다이제스트</span><span class="sxs-lookup"><span data-stu-id="b8059-185">Digest</span></span>
- <span data-ttu-id="b8059-186">Kerberos</span><span class="sxs-lookup"><span data-stu-id="b8059-186">Kerberos</span></span>
- <span data-ttu-id="b8059-187">Negotiate</span><span class="sxs-lookup"><span data-stu-id="b8059-187">Negotiate</span></span>
- <span data-ttu-id="b8059-188">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="b8059-188">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="b8059-189">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-189">The default value is Default.</span></span>

<span data-ttu-id="b8059-190">CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-190">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="b8059-191">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거형](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-191">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="b8059-192">주의: 사용자의 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-192">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="b8059-193">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-193">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="b8059-194">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-194">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.AuthenticationMechanism
Parameter Sets: ComputerName, Uri
Aliases:
Accepted values: Default, Basic, Negotiate, NegotiateWithImplicitCredential, Credssp, Digest, Kerberos

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-195">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="b8059-195">-CertificateThumbprint</span></span>

<span data-ttu-id="b8059-196">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-196">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="b8059-197">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-197">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="b8059-198">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-198">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="b8059-199">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-199">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="b8059-200">인증서를 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-200">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-201">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="b8059-201">-ComputerName</span></span>

<span data-ttu-id="b8059-202">컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-202">Specifies a computer name.</span></span> <span data-ttu-id="b8059-203">이 cmdlet은 지정 된 원격 컴퓨터와의 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-203">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="b8059-204">컴퓨터 이름을 하나만 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-204">Enter only one computer name.</span></span> <span data-ttu-id="b8059-205">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-205">The default is the local computer.</span></span>

<span data-ttu-id="b8059-206">컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-206">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="b8059-207">컴퓨터 이름을로 파이프 할 수도 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b8059-207">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="b8059-208">**ComputerName** 매개 변수 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-208">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="b8059-209">또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-209">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="b8059-210">TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b8059-210">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="b8059-211">참고: Windows Vista 이상 버전의 Windows 운영 체제에서 **ComputerName** 매개 변수 값에 로컬 컴퓨터를 포함 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-211">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: Cn

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-212">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="b8059-212">-ConfigurationName</span></span>

<span data-ttu-id="b8059-213">대화형 세션에 사용할 세션 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-213">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="b8059-214">세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-214">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="b8059-215">구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/powershell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-215">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="b8059-216">SSH와 함께 사용 하는 경우 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-216">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="b8059-217">SSH의 기본값은 `powershell` 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-217">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="b8059-218">세션의 세션 구성은 원격 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-218">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="b8059-219">지정된 세션 구성이 원격 컴퓨터에 없으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-219">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="b8059-220">기본값은 `$PSSessionConfigurationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-220">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="b8059-221">이 기본 설정 변수를 설정하지 않으면 Microsoft.PowerShell이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-221">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="b8059-222">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-222">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ComputerName, Uri, VMId, VMName, ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-223">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="b8059-223">-ConnectionUri</span></span>

<span data-ttu-id="b8059-224">세션에 대 한 연결 끝점을 정의 하는 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-224">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="b8059-225">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-225">The URI must be fully qualified.</span></span> <span data-ttu-id="b8059-226">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-226">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="b8059-227">기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-227">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="b8059-228">**ConnectionURI** 를 지정하지 않은 경우 **UseSSL** , **ComputerName** , **Port** 및 **ApplicationName** 매개 변수를 사용하여 **ConnectionURI** 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-228">If you do not specify a **ConnectionURI** , you can use the **UseSSL** , **ComputerName** , **Port** , and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="b8059-229">URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-229">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="b8059-230">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-230">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="b8059-231">PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-231">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="b8059-232">대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-232">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

```yaml
Type: System.Uri
Parameter Sets: Uri
Aliases: URI, CU

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-233">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="b8059-233">-ContainerId</span></span>

<span data-ttu-id="b8059-234">컨테이너의 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-234">Specifies the ID of a container.</span></span>

```yaml
Type: System.String
Parameter Sets: ContainerId
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-235">-Credential</span><span class="sxs-lookup"><span data-stu-id="b8059-235">-Credential</span></span>

<span data-ttu-id="b8059-236">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-236">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="b8059-237">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-237">The default is the current user.</span></span>

<span data-ttu-id="b8059-238">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="b8059-238">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b8059-239">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-239">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="b8059-240">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-240">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="b8059-241">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="b8059-241">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerName, Uri, VMId, VMName
Aliases:

Required: True (VMId, VMName), False (ComputerName, Uri)
Position: 1
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-242">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="b8059-242">-EnableNetworkAccess</span></span>

<span data-ttu-id="b8059-243">이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-243">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="b8059-244">대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-244">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="b8059-245">예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-245">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="b8059-246">루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-246">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="b8059-247">루프백 세션을 만들려면 **ComputerName** 매개 변수를 생략 하거나 값을로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-247">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="b8059-248">(점), localhost 또는 로컬 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-248">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="b8059-249">기본적으로 루프백 세션은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 사용 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-249">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="b8059-250">**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-250">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="b8059-251">원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 를 사용 하는 경우 명령은 성공 하지만 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-251">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="b8059-252">또한 세션 자격 증명을 다른 컴퓨터에 위임하는 **CredSSP** 매개 변수의 **Authentication** 값을 사용하여 루프백 세션에서 원격 액세스를 허용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-252">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="b8059-253">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-253">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-254">-HostName</span><span class="sxs-lookup"><span data-stu-id="b8059-254">-HostName</span></span>

<span data-ttu-id="b8059-255">SSH (Secure Shell) 기반 연결에 대 한 컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-255">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="b8059-256">이는 원격 컴퓨터에 대 한 연결이 Windows WinRM이 아닌 SSH를 사용 하는 경우를 제외 하 고 **ComputerName** 매개 변수와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-256">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="b8059-257">이 매개 변수는 형식을 사용 하 여 호스트 이름 매개 변수 값의 일부로 사용자 이름 및/또는 포트를 지정 하도록 지원 합니다 `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="b8059-257">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="b8059-258">호스트 이름의 일부로 지정 된 사용자 이름 및/또는 포트가 `-UserName` 지정 된 경우 및 매개 변수 보다 우선적으로 적용 `-Port` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-258">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="b8059-259">이를 통해 특정 사용자 이름 및/또는 포트를 포함 하는 여러 컴퓨터 이름을이 매개 변수에 전달할 수 있으며, 다른 사용자 이름 및/또는 포트는 `-UserName` 및 매개 변수에서 사용할 수 있습니다 `-Port` .</span><span class="sxs-lookup"><span data-stu-id="b8059-259">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="b8059-260">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-260">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-261">-Id</span><span class="sxs-lookup"><span data-stu-id="b8059-261">-Id</span></span>

<span data-ttu-id="b8059-262">기존 세션의 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-262">Specifies the ID of an existing session.</span></span> <span data-ttu-id="b8059-263">`Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-263">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="b8059-264">세션의 ID를 찾으려면 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b8059-264">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Id
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-265">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="b8059-265">-InstanceId</span></span>

<span data-ttu-id="b8059-266">기존 세션의 인스턴스 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-266">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="b8059-267">`Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-267">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="b8059-268">인스턴스 ID는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-268">The instance ID is a GUID.</span></span> <span data-ttu-id="b8059-269">세션의 인스턴스 ID를 확인 하려면 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b8059-269">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="b8059-270">**Session** , **Name** 또는 **ID** 매개 변수를 사용 하 여 기존 세션을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-270">You can also use the **Session** , **Name** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="b8059-271">또는 **ComputerName** 매개 변수를 사용 하 여 임시 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-271">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

```yaml
Type: System.Guid
Parameter Sets: InstanceId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-272">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="b8059-272">-KeyFilePath</span></span>

<span data-ttu-id="b8059-273">SSH (Secure Shell)에서 원격 컴퓨터의 사용자를 인증 하는 데 사용 하는 키 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-273">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="b8059-274">SSH를 사용 하면 기본 암호 인증 대신 개인/공개 키를 통해 사용자 인증을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-274">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="b8059-275">키 인증을 사용 하도록 원격 컴퓨터를 구성 하는 경우이 매개 변수를 사용 하 여 사용자를 식별 하는 키를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-275">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="b8059-276">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-276">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases: IdentityFilePath

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-277">-Name</span><span class="sxs-lookup"><span data-stu-id="b8059-277">-Name</span></span>

<span data-ttu-id="b8059-278">기존 세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-278">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="b8059-279">`Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-279">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="b8059-280">지정한 이름이 둘 이상의 세션과 일치하는 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-280">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="b8059-281">**Session** , **InstanceID** 또는 **ID** 매개 변수를 사용 하 여 기존 세션을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-281">You can also use the **Session** , **InstanceID** , or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="b8059-282">또는 **ComputerName** 매개 변수를 사용 하 여 임시 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-282">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="b8059-283">세션의 이름을 설정 하려면 cmdlet의 **name** 매개 변수를 사용 합니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b8059-283">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: Name
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-284">-Port</span><span class="sxs-lookup"><span data-stu-id="b8059-284">-Port</span></span>

<span data-ttu-id="b8059-285">이 명령에 사용 되는 원격 컴퓨터의 네트워크 포트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-285">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="b8059-286">PowerShell 6.0에서이 매개 변수는 SSH (Secure Shell) 연결을 지 원하는 **HostName** 매개 변수 집합에서 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-286">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="b8059-287">**WinRM (ComputerName 매개 변수 설정)**</span><span class="sxs-lookup"><span data-stu-id="b8059-287">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="b8059-288">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-288">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="b8059-289">기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-289">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="b8059-290">대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-290">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="b8059-291">다음 명령을 사용하여 수신기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-291">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="b8059-292">필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-292">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="b8059-293">명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-293">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="b8059-294">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-294">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="b8059-295">**SSH (호스트 이름 매개 변수 집합)**</span><span class="sxs-lookup"><span data-stu-id="b8059-295">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="b8059-296">원격 컴퓨터에 연결 하려면 SSH 서비스 (SSHD)를 사용 하 여 원격 컴퓨터를 구성 하 고 연결에서 사용 하는 포트에서 수신 대기 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-296">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="b8059-297">SSH에 대 한 기본 포트는 22입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-297">The default port for SSH is 22.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ComputerName, SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-298">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="b8059-298">-RunAsAdministrator</span></span>

<span data-ttu-id="b8059-299">**PSSession** 이 관리자 권한으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-299">Indicates that the **PSSession** runs as administrator.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ContainerId
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-300">-Session</span><span class="sxs-lookup"><span data-stu-id="b8059-300">-Session</span></span>

<span data-ttu-id="b8059-301">대화형 세션에 사용할 PowerShell 세션 ( **PSSession** )을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-301">Specifies a PowerShell session ( **PSSession** ) to use for the interactive session.</span></span> <span data-ttu-id="b8059-302">이 매개 변수는 세션 개체를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-302">This parameter takes a session object.</span></span> <span data-ttu-id="b8059-303">**Name** , **InstanceID** 또는 **ID** 매개 변수를 사용 하 여 **PSSession** 을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-303">You can also use the **Name** , **InstanceID** , or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="b8059-304">세션 개체를 포함 하는 변수를 입력 하거나 세션 개체를 만들거나 가져오는 명령 (예: 또는 명령)을 입력 `New-PSSession` `Get-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-304">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="b8059-305">세션 개체를로 파이프 할 수도 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b8059-305">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="b8059-306">이 매개 변수를 사용 하 여 하나의 **PSSession** 만 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-306">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="b8059-307">둘 이상의 **PSSession** 이 포함 된 변수를 입력 하는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-307">If you enter a variable that contains more than one **PSSession** , the command fails.</span></span>

<span data-ttu-id="b8059-308">`Exit-PSSession`또는 **EXIT** 키워드를 사용 하는 경우 대화형 세션이 종료 되지만 사용자가 만든 **PSSession** 은 계속 열려 있고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-308">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: Session
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-309">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="b8059-309">-SessionOption</span></span>

<span data-ttu-id="b8059-310">세션의 고급 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-310">Sets advanced options for the session.</span></span> <span data-ttu-id="b8059-311">Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-311">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="b8059-312">옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-312">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="b8059-313">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-313">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="b8059-314">세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-314">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="b8059-315">그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-315">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="b8059-316">기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="b8059-316">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="b8059-317">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-317">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="b8059-318">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-318">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

```yaml
Type: System.Management.Automation.Remoting.PSSessionOption
Parameter Sets: ComputerName, Uri
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-319">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="b8059-319">-SSHTransport</span></span>

<span data-ttu-id="b8059-320">SSH (Secure Shell)를 사용 하 여 원격 연결을 설정 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-320">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="b8059-321">기본적으로 PowerShell은 Windows WinRM을 사용 하 여 원격 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-321">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="b8059-322">이 스위치를 사용 하면 PowerShell에서 호스트 이름 매개 변수 집합을 사용 하 여 SSH 기반 원격 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-322">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="b8059-323">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-323">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SSHHost
Aliases:
Accepted values: true

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-324">-하위 시스템</span><span class="sxs-lookup"><span data-stu-id="b8059-324">-Subsystem</span></span>

<span data-ttu-id="b8059-325">새 **PSSession** 에 사용 되는 SSH 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-325">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="b8059-326">이는 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-326">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="b8059-327">하위 시스템은 미리 정의 된 매개 변수를 사용 하 여 특정 버전의 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-327">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="b8059-328">지정 된 하위 시스템이 원격 컴퓨터에 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-328">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="b8059-329">이 매개 변수를 사용 하지 않는 경우 기본값은 ' powershell ' 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-329">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: powershell
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-330">-UserName</span><span class="sxs-lookup"><span data-stu-id="b8059-330">-UserName</span></span>

<span data-ttu-id="b8059-331">원격 컴퓨터에서 세션을 만드는 데 사용 되는 계정의 사용자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-331">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="b8059-332">사용자 인증 방법은 원격 컴퓨터에서 SSH (Secure Shell)가 구성 된 방식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-332">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="b8059-333">SSH가 기본 암호 인증으로 구성 된 경우 사용자 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-333">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="b8059-334">키 기반 사용자 인증에 대해 SSH를 구성 하는 경우 키 파일 경로를 **Keyfilepath** 매개 변수를 통해 제공할 수 있으며 암호 프롬프트가 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-334">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="b8059-335">클라이언트 사용자 키 파일이 SSH 알려진 위치에 있는 경우 키 기반 인증에는 **Keyfilepath** 매개 변수가 필요 하지 않으며 사용자 인증은 사용자 이름에 따라 자동으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-335">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="b8059-336">자세한 내용은 키 기반 사용자 인증에 대 한 SSH 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-336">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="b8059-337">필수 매개 변수가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-337">This is not a required parameter.</span></span> <span data-ttu-id="b8059-338">**UserName** 매개 변수를 지정 하지 않으면 현재 로그온 사용자 이름이 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-338">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="b8059-339">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-339">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SSHHost
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-340">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="b8059-340">-UseSSL</span></span>

<span data-ttu-id="b8059-341">이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-341">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="b8059-342">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-342">By default, SSL is not used.</span></span>

<span data-ttu-id="b8059-343">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-343">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="b8059-344">**UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-344">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="b8059-345">이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-345">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-346">-VMId</span><span class="sxs-lookup"><span data-stu-id="b8059-346">-VMId</span></span>

<span data-ttu-id="b8059-347">가상 컴퓨터의 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-347">Specifies the ID of a virtual machine.</span></span>

```yaml
Type: System.Guid
Parameter Sets: VMId
Aliases: VMGuid

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-348">-VMName</span><span class="sxs-lookup"><span data-stu-id="b8059-348">-VMName</span></span>

<span data-ttu-id="b8059-349">가상 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-349">Specifies the name of a virtual machine.</span></span>

```yaml
Type: System.String
Parameter Sets: VMName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b8059-350">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b8059-350">CommonParameters</span></span>

<span data-ttu-id="b8059-351">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b8059-351">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b8059-352">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-352">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b8059-353">입력</span><span class="sxs-lookup"><span data-stu-id="b8059-353">INPUTS</span></span>

### <span data-ttu-id="b8059-354">System.string (Runspace, 시스템.</span><span class="sxs-lookup"><span data-stu-id="b8059-354">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="b8059-355">컴퓨터 이름, 문자열 또는 세션 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-355">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="b8059-356">출력</span><span class="sxs-lookup"><span data-stu-id="b8059-356">OUTPUTS</span></span>

### <span data-ttu-id="b8059-357">없음</span><span class="sxs-lookup"><span data-stu-id="b8059-357">None</span></span>

<span data-ttu-id="b8059-358">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-358">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="b8059-359">참고</span><span class="sxs-lookup"><span data-stu-id="b8059-359">NOTES</span></span>

<span data-ttu-id="b8059-360">원격 컴퓨터에 연결하려면 원격 컴퓨터의 Administrators 그룹 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-360">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="b8059-361">로컬 컴퓨터에서 대화형 세션을 시작 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-361">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="b8059-362">를 사용 하는 경우 `Enter-PSSession` 원격 컴퓨터의 사용자 프로필이 대화형 세션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-362">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="b8059-363">PowerShell 모듈을 추가 하 고 명령 프롬프트를 변경 하는 명령을 비롯 한 원격 사용자 프로필의 명령은 원격 프롬프트가 표시 되기 전에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-363">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="b8059-364">`Enter-PSSession` 는 대화형 세션을 위해 로컬 컴퓨터에서 UI 문화권 설정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-364">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="b8059-365">로컬 UI 문화권을 찾으려면 자동 변수를 사용 `$UICulture` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-365">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="b8059-366">`Enter-PSSession``Get-Command`, `Out-Default` 및 cmdlet이 필요 `Exit-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-366">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="b8059-367">이러한 cmdlet이 원격 컴퓨터의 세션 구성에 포함 되지 않은 경우 `Enter-PSSession` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-367">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="b8059-368">가 `Invoke-Command` 원격 컴퓨터에 보내기 전에 명령을 구문 분석 하 고 해석 하는와 달리는 `Enter-PSSession` 명령을 해석 하지 않고 원격 컴퓨터에 직접 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-368">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="b8059-369">입력 하려는 세션이 명령을 처리 하는 중이면 PowerShell이 명령에 응답 하기 전에 지연이 있을 수 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="b8059-369">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="b8059-370">세션을 사용할 수 있게 되 면 즉시 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-370">You are connected as soon as the session is available.</span></span> <span data-ttu-id="b8059-371">명령을 취소 하려면 `Enter-PSSession` <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-371">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="b8059-372">**HostName** 매개 변수 집합은 PowerShell 6.0부터 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-372">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="b8059-373">Secure Shell (SSH)를 기반으로 PowerShell 원격 기능을 제공 하기 위해 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-373">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="b8059-374">SSH와 PowerShell은 여러 플랫폼 (Windows, Linux, macOS)에서 지원 되며 powershell 원격은 PowerShell 및 SSH가 설치 되 고 구성 되는 이러한 플랫폼에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-374">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="b8059-375">이는 WinRM을 기반으로 하는 이전 Windows 전용 원격 시스템과 별개 이며, 대부분의 WinRM 특정 기능 및 제한 사항이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-375">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="b8059-376">예를 들어 WinRM 기반 할당량, 세션 옵션, 사용자 지정 끝점 구성 및 연결 끊기/다시 연결 기능은 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-376">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="b8059-377">PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8059-377">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="b8059-378">PowerShell 7.1 이전에는 SSH를 통한 원격 기능이 두 번째 홉 원격 세션을 지원하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-378">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="b8059-379">해당 기능은 WinRM을 사용하는 세션으로 제한되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-379">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="b8059-380">PowerShell 7.1을 사용하면 `Enter-PSSession` 및 `Enter-PSHostProcess`가 대화형 원격 세션 내에서 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8059-380">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="b8059-381">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b8059-381">RELATED LINKS</span></span>

[<span data-ttu-id="b8059-382">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-382">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="b8059-383">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-383">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="b8059-384">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="b8059-384">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="b8059-385">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-385">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="b8059-386">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-386">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="b8059-387">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-387">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="b8059-388">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-388">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="b8059-389">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="b8059-389">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="b8059-390">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="b8059-390">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="b8059-391">about_Remote</span><span class="sxs-lookup"><span data-stu-id="b8059-391">about_Remote</span></span>](About/about_Remote.md)
