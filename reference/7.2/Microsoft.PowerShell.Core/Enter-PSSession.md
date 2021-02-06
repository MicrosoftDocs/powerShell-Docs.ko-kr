---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enter-PSSession
ms.openlocfilehash: 9c08e78d840815a396b55eb26bf8e21d73cb81aa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601847"
---
# <span data-ttu-id="1926f-102">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-102">Enter-PSSession</span></span>

## <span data-ttu-id="1926f-103">개요</span><span class="sxs-lookup"><span data-stu-id="1926f-103">SYNOPSIS</span></span>
<span data-ttu-id="1926f-104">원격 컴퓨터와 대화형 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-104">Starts an interactive session with a remote computer.</span></span>

## <span data-ttu-id="1926f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1926f-105">SYNTAX</span></span>

### <span data-ttu-id="1926f-106">ComputerName (기본값)</span><span class="sxs-lookup"><span data-stu-id="1926f-106">ComputerName (Default)</span></span>

```
Enter-PSSession [-ComputerName] <String> [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-Port <Int32>] [-UseSSL] [-ApplicationName <String>]
 [-SessionOption <PSSessionOption>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="1926f-107">SSHHost</span><span class="sxs-lookup"><span data-stu-id="1926f-107">SSHHost</span></span>

```
Enter-PSSession [-HostName] <String> [-Port <Int32>] [-UserName <String>] [-KeyFilePath <String>]
 [-SSHTransport] [<CommonParameters>]
```

### <span data-ttu-id="1926f-108">세션</span><span class="sxs-lookup"><span data-stu-id="1926f-108">Session</span></span>

```
Enter-PSSession [[-Session] <PSSession>] [<CommonParameters>]
```

### <span data-ttu-id="1926f-109">URI</span><span class="sxs-lookup"><span data-stu-id="1926f-109">Uri</span></span>

```
Enter-PSSession [[-ConnectionUri] <Uri>] [-EnableNetworkAccess] [[-Credential] <PSCredential>]
 [-ConfigurationName <String>] [-AllowRedirection] [-SessionOption <PSSessionOption>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### <span data-ttu-id="1926f-110">InstanceId</span><span class="sxs-lookup"><span data-stu-id="1926f-110">InstanceId</span></span>

```
Enter-PSSession [-InstanceId <Guid>] [<CommonParameters>]
```

### <span data-ttu-id="1926f-111">Id</span><span class="sxs-lookup"><span data-stu-id="1926f-111">Id</span></span>

```
Enter-PSSession [[-Id] <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="1926f-112">Name</span><span class="sxs-lookup"><span data-stu-id="1926f-112">Name</span></span>

```
Enter-PSSession [-Name <String>] [<CommonParameters>]
```

### <span data-ttu-id="1926f-113">VMId</span><span class="sxs-lookup"><span data-stu-id="1926f-113">VMId</span></span>

```
Enter-PSSession [-VMId] <Guid> [-Credential] <PSCredential> [-ConfigurationName <String>] [<CommonParameters>]
```

### <span data-ttu-id="1926f-114">VMName</span><span class="sxs-lookup"><span data-stu-id="1926f-114">VMName</span></span>

```
Enter-PSSession [-VMName] <String> [-Credential] <PSCredential> [-ConfigurationName <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="1926f-115">ContainerId</span><span class="sxs-lookup"><span data-stu-id="1926f-115">ContainerId</span></span>

```
Enter-PSSession [-ContainerId] <String> [-ConfigurationName <String>] [-RunAsAdministrator]
 [<CommonParameters>]
```

## <span data-ttu-id="1926f-116">설명</span><span class="sxs-lookup"><span data-stu-id="1926f-116">DESCRIPTION</span></span>

<span data-ttu-id="1926f-117">`Enter-PSSession`Cmdlet은 단일 원격 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-117">The `Enter-PSSession` cmdlet starts an interactive session with a single remote computer.</span></span>
<span data-ttu-id="1926f-118">세션 중에 입력 하는 명령은 원격 컴퓨터에서 직접 입력 하는 것 처럼 원격 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-118">During the session, the commands that you type run on the remote computer, just as if you were typing directly on the remote computer.</span></span> <span data-ttu-id="1926f-119">한 번에 하나의 대화형 세션만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-119">You can have only one interactive session at a time.</span></span>

<span data-ttu-id="1926f-120">일반적으로 **ComputerName** 매개 변수를 사용하여 원격 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-120">Typically, you use the **ComputerName** parameter to specify the name of the remote computer.</span></span>
<span data-ttu-id="1926f-121">그러나 대화형 세션에 cmdlet을 사용 하 여 만든 세션을 사용할 수도 있습니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1926f-121">However, you can also use a session that you create by using the `New-PSSession` cmdlet for the interactive session.</span></span> <span data-ttu-id="1926f-122">그러나 `Disconnect-PSSession` , `Connect-PSSession` 또는 cmdlet을 사용 하 여 `Receive-PSSession` 대화형 세션에서 연결을 끊거나 다시 연결할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-122">However, you cannot use the `Disconnect-PSSession`, `Connect-PSSession`, or `Receive-PSSession` cmdlets to disconnect from or re-connect to an interactive session.</span></span>

<span data-ttu-id="1926f-123">PowerShell 6.0부터 ssh (Secure Shell)를 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 하 고, SSH를 로컬 컴퓨터에서 사용할 수 있고, 원격 컴퓨터가 PowerShell SSH 끝점을 사용 하 여 구성 된 경우 원격 컴퓨터에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-123">Starting with PowerShell 6.0 you can use Secure Shell (SSH) to establish a connection to a remote computer, if SSH is available on the local computer and the remote computer is configured with a PowerShell SSH endpoint.</span></span> <span data-ttu-id="1926f-124">SSH 기반 PowerShell 원격 세션의 혜택은 여러 플랫폼 (Windows, Linux, macOS)에서 작동 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-124">The benefit an SSH based PowerShell remote session is that it works across multiple platforms (Windows, Linux, macOS).</span></span> <span data-ttu-id="1926f-125">SSH 기반 원격의 경우 **HostName** 매개 변수 집합을 사용 하 여 원격 컴퓨터 및 관련 연결 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-125">For SSH based remoting you use the **HostName** parameter set to specify the remote computer and relevant connection information.</span></span> <span data-ttu-id="1926f-126">PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-126">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="1926f-127">대화형 세션을 종료 하 고 원격 컴퓨터와의 연결을 끊으려면 `Exit-PSSession` cmdlet을 사용 하거나를 입력 `exit` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-127">To end the interactive session and disconnect from the remote computer, use the `Exit-PSSession` cmdlet, or type `exit`.</span></span>

## <span data-ttu-id="1926f-128">예제</span><span class="sxs-lookup"><span data-stu-id="1926f-128">EXAMPLES</span></span>

### <span data-ttu-id="1926f-129">예제 1: 대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="1926f-129">Example 1: Start an interactive session</span></span>

```
PS> Enter-PSSession
[localhost]: PS>
```

<span data-ttu-id="1926f-130">이 명령은 로컬 컴퓨터에서 대화형 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-130">This command starts an interactive session on the local computer.</span></span> <span data-ttu-id="1926f-131">명령 프롬프트가 변경되어 현재 다른 세션에서 명령을 실행하고 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-131">The command prompt changes to indicate that you are now running commands in a different session.</span></span>

<span data-ttu-id="1926f-132">입력한 명령은 새 세션에서 실행되고 결과가 기본 세션에 텍스트로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-132">The commands that you enter run in the new session, and the results are returned to the default session as text.</span></span>

### <span data-ttu-id="1926f-133">예제 2: 대화형 세션 작업</span><span class="sxs-lookup"><span data-stu-id="1926f-133">Example 2: Work with an interactive session</span></span>

<span data-ttu-id="1926f-134">첫 번째 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01, 원격 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-134">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with Server01, a remote computer.</span></span> <span data-ttu-id="1926f-135">세션이 시작되면 명령 프롬프트가 변경되어 컴퓨터 이름을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-135">When the session starts, the command prompt changes to include the computer name.</span></span>

<span data-ttu-id="1926f-136">두 번째 명령은 PowerShell 프로세스를 가져오고 출력을 Process.txt 파일로 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-136">The second command gets the PowerShell process and redirects the output to the Process.txt file.</span></span> <span data-ttu-id="1926f-137">이 명령은 원격 컴퓨터에 전송되고 Process.txt 파일이 원격 컴퓨터에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-137">The command is submitted to the remote computer, and the file is saved on the remote computer.</span></span>

<span data-ttu-id="1926f-138">세 번째 명령은 **Exit** 키워드를 사용 하 여 대화형 세션을 종료 하 고 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-138">The third command uses the **Exit** keyword to end the interactive session and close the connection.</span></span>
<span data-ttu-id="1926f-139">네 번째 명령은 Process.txt 파일이 원격 컴퓨터에 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-139">The fourth command confirms that the Process.txt file is on the remote computer.</span></span> <span data-ttu-id="1926f-140">`Get-ChildItem`로컬 컴퓨터의 ("dir") 명령으로 파일을 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-140">A `Get-ChildItem` ("dir") command on the local computer cannot find the file.</span></span>

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

<span data-ttu-id="1926f-141">이 명령은 원격 컴퓨터와의 대화형 세션에서 작업하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-141">This command shows how to work in an interactive session with a remote computer.</span></span>

### <span data-ttu-id="1926f-142">예 3: Session 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="1926f-142">Example 3: Use the Session parameter</span></span>

```powershell
PS> $s = New-PSSession -ComputerName Server01
PS> Enter-PSSession -Session $s
[Server01]: PS>
```

<span data-ttu-id="1926f-143">이러한 명령은의 **Session** 매개 변수를 사용 `Enter-PSSession` 하 여 기존 PowerShell 세션 (**PSSession**)에서 대화형 세션을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-143">These commands use the **Session** parameter of `Enter-PSSession` to run the interactive session in an existing PowerShell session (**PSSession**).</span></span>

### <span data-ttu-id="1926f-144">예 4: 대화형 세션을 시작 하 고 포트 및 자격 증명 매개 변수 지정</span><span class="sxs-lookup"><span data-stu-id="1926f-144">Example 4: Start an interactive session and specify the Port and Credential parameters</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01 -Port 90 -Credential Domain01\User01
[Server01]: PS>
```

<span data-ttu-id="1926f-145">이 명령은 Server01 컴퓨터와 대화형 세션을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-145">This command starts an interactive session with the Server01 computer.</span></span> <span data-ttu-id="1926f-146">**Port** 매개 변수를 사용 하 여 포트를 지정 하 고 **Credential** 매개 변수를 사용 하 여 원격 컴퓨터에 연결할 수 있는 권한을 가진 사용자의 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-146">It uses the **Port** parameter to specify the port and the **Credential** parameter to specify the account of a user who has permission to connect to the remote computer.</span></span>

### <span data-ttu-id="1926f-147">예 5: 대화형 세션 중지</span><span class="sxs-lookup"><span data-stu-id="1926f-147">Example 5: Stop an interactive session</span></span>

```powershell
PS> Enter-PSSession -ComputerName Server01
[Server01]: PS> Exit-PSSession
PS>
```

<span data-ttu-id="1926f-148">이 예제에서는 대화형 세션을 시작하고 중지하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-148">This example shows how to start and stop an interactive session.</span></span> <span data-ttu-id="1926f-149">첫 번째 명령은 cmdlet을 사용 하 여 `Enter-PSSession` Server01 컴퓨터와 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-149">The first command uses the `Enter-PSSession` cmdlet to start an interactive session with the Server01 computer.</span></span>

<span data-ttu-id="1926f-150">두 번째 명령은 cmdlet을 사용 하 여 `Exit-PSSession` 세션을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-150">The second command uses the `Exit-PSSession` cmdlet to end the session.</span></span> <span data-ttu-id="1926f-151">**Exit** 키워드를 사용 하 여 대화형 세션을 종료할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-151">You can also use the **Exit** keyword to end the interactive session.</span></span> <span data-ttu-id="1926f-152">`Exit-PSSession` 및 **종료** 는 동일한 효과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-152">`Exit-PSSession` and **Exit** have the same effect.</span></span>

### <span data-ttu-id="1926f-153">예제 6: SSH를 사용 하 여 대화형 세션 시작</span><span class="sxs-lookup"><span data-stu-id="1926f-153">Example 6: Start an interactive session using SSH</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer01
```

<span data-ttu-id="1926f-154">이 예제에서는 Secure Shell (SSH)를 사용 하 여 대화형 세션을 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-154">This example shows how to start an interactive session using Secure Shell (SSH).</span></span> <span data-ttu-id="1926f-155">SSH가 원격 컴퓨터에서 암호를 묻는 메시지를 표시 하도록 구성 된 경우 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-155">If SSH is configured on the remote computer to prompt for passwords then you will get a password prompt.</span></span>
<span data-ttu-id="1926f-156">그렇지 않은 경우에는 SSH 키 기반 사용자 인증을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-156">Otherwise you will have to use SSH key based user authentication.</span></span>

### <span data-ttu-id="1926f-157">예 7: SSH를 사용 하 여 대화형 세션을 시작 하 고 포트 및 사용자 인증 키 지정</span><span class="sxs-lookup"><span data-stu-id="1926f-157">Example 7: Start an interactive session using SSH and specify the Port and user authentication key</span></span>

```powershell
PS> Enter-PSSession -HostName UserA@LinuxServer02:22 -KeyFilePath c:\<path>\userAKey_rsa
```

<span data-ttu-id="1926f-158">이 예제에서는 SSH를 사용 하 여 대화형 세션을 시작 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-158">This example shows how to start an interactive session using SSH.</span></span> <span data-ttu-id="1926f-159">**Port** 매개 변수를 사용 하 여 사용할 포트를 지정 하 고 **keyfilepath** 매개 변수를 사용 하 여 원격 컴퓨터에서 사용자를 인증 하는 데 사용 되는 RSA 키를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-159">It uses the **Port** parameter to specify the port to use and the **KeyFilePath** parameter to specify an RSA key used to authenticate the user on the remote computer.</span></span>

## <span data-ttu-id="1926f-160">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="1926f-160">PARAMETERS</span></span>

### <span data-ttu-id="1926f-161">-AllowRedirection</span><span class="sxs-lookup"><span data-stu-id="1926f-161">-AllowRedirection</span></span>

<span data-ttu-id="1926f-162">이 연결을 대체 URI(Uniform Resource Identifier)로 리디렉션할 수 있도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-162">Allows redirection of this connection to an alternate Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="1926f-163">기본적으로 리디렉션은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-163">By default, redirection is not allowed.</span></span>

<span data-ttu-id="1926f-164">**ConnectionURI** 매개 변수를 사용하면 원격 대상에서 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-164">When you use the **ConnectionURI** parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="1926f-165">기본적으로 PowerShell은 연결을 리디렉션하지 않지만이 매개 변수를 사용 하 여 연결을 리디렉션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-165">By default, PowerShell does not redirect connections, but you can use this parameter to allow it to redirect the connection.</span></span>

<span data-ttu-id="1926f-166">또한 **MaximumConnectionRedirectionCount** 세션 옵션 값을 변경하여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-166">You can also limit the number of times the connection is redirected by changing the **MaximumConnectionRedirectionCount** session option value.</span></span> <span data-ttu-id="1926f-167">Cmdlet의 **Maximumredirection** 매개 변수를 사용 `New-PSSessionOption` 하거나 기본 설정 변수의 **MaximumConnectionRedirectionCount** 속성을 설정 `$PSSessionOption` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-167">Use the **MaximumRedirection** parameter of the `New-PSSessionOption` cmdlet or set the **MaximumConnectionRedirectionCount** property of the `$PSSessionOption` preference variable.</span></span> <span data-ttu-id="1926f-168">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-168">The default value is 5.</span></span>

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

### <span data-ttu-id="1926f-169">-ApplicationName</span><span class="sxs-lookup"><span data-stu-id="1926f-169">-ApplicationName</span></span>

<span data-ttu-id="1926f-170">연결 URI의 애플리케이션 이름 세그먼트를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-170">Specifies the application name segment of the connection URI.</span></span> <span data-ttu-id="1926f-171">명령에서 **ConnectionURI**  매개 변수를 사용하지 않는 경우 이 매개 변수를 사용하여 응용 프로그램 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-171">Use this parameter to specify the application name when you are not using the **ConnectionURI** parameter in the command.</span></span>

<span data-ttu-id="1926f-172">기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-172">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="1926f-173">이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-173">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="1926f-174">이 값은 대부분의 사용에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-174">This value is appropriate for most uses.</span></span> <span data-ttu-id="1926f-175">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-175">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="1926f-176">**WinRM** 서비스는 응용 프로그램 이름을 사용 하 여 연결 요청을 처리 하는 수신기를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-176">The **WinRM** service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="1926f-177">이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 **URLPrefix** 속성 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-177">The value of this parameter should match the value of the **URLPrefix** property of a listener on the remote computer.</span></span>

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

### <span data-ttu-id="1926f-178">-인증</span><span class="sxs-lookup"><span data-stu-id="1926f-178">-Authentication</span></span>

<span data-ttu-id="1926f-179">사용자 자격 증명을 인증하는 데 사용되는 메커니즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-179">Specifies the mechanism that is used to authenticate the user's credentials.</span></span> <span data-ttu-id="1926f-180">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-180">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="1926f-181">기본값</span><span class="sxs-lookup"><span data-stu-id="1926f-181">Default</span></span>
- <span data-ttu-id="1926f-182">Basic</span><span class="sxs-lookup"><span data-stu-id="1926f-182">Basic</span></span>
- <span data-ttu-id="1926f-183">Credssp</span><span class="sxs-lookup"><span data-stu-id="1926f-183">Credssp</span></span>
- <span data-ttu-id="1926f-184">다이제스트</span><span class="sxs-lookup"><span data-stu-id="1926f-184">Digest</span></span>
- <span data-ttu-id="1926f-185">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1926f-185">Kerberos</span></span>
- <span data-ttu-id="1926f-186">Negotiate</span><span class="sxs-lookup"><span data-stu-id="1926f-186">Negotiate</span></span>
- <span data-ttu-id="1926f-187">NegotiateWithImplicitCredential</span><span class="sxs-lookup"><span data-stu-id="1926f-187">NegotiateWithImplicitCredential</span></span>

<span data-ttu-id="1926f-188">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-188">The default value is Default.</span></span>

<span data-ttu-id="1926f-189">CredSSP 인증은 windows Vista, Windows Server 2008 이상 버전의 Windows 운영 체제 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-189">CredSSP authentication is available only in Windows Vista, Windows Server 2008, and later versions of the Windows operating system.</span></span>

<span data-ttu-id="1926f-190">이 매개 변수 값에 대 한 자세한 내용은 [Authenticationmechanism 열거형](/dotnet/api/system.management.automation.runspaces.authenticationmechanism)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-190">For more information about the values of this parameter, see [AuthenticationMechanism Enum](/dotnet/api/system.management.automation.runspaces.authenticationmechanism).</span></span>

<span data-ttu-id="1926f-191">주의: 사용자의 자격 증명이 인증을 위해 원격 컴퓨터에 전달 되는 CredSSP (자격 증명 보안 지원 공급자) 인증은 원격 네트워크 공유에 액세스 하는 것과 같이 둘 이상의 리소스에서 인증이 필요한 명령에 대해 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-191">Caution: Credential Security Support Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="1926f-192">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-192">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="1926f-193">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-193">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

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

### <span data-ttu-id="1926f-194">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="1926f-194">-CertificateThumbprint</span></span>

<span data-ttu-id="1926f-195">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-195">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="1926f-196">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-196">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="1926f-197">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-197">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="1926f-198">인증서는 로컬 사용자 계정에만 매핑할 수 있으며 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-198">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="1926f-199">인증서를 가져오려면 `Get-Item` `Get-ChildItem` PowerShell Cert: 드라이브에서 또는 명령을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-199">To get a certificate, use the `Get-Item` or `Get-ChildItem` command in the PowerShell Cert: drive.</span></span>

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

### <span data-ttu-id="1926f-200">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="1926f-200">-ComputerName</span></span>

<span data-ttu-id="1926f-201">컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-201">Specifies a computer name.</span></span> <span data-ttu-id="1926f-202">이 cmdlet은 지정 된 원격 컴퓨터와의 대화형 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-202">This cmdlet starts an interactive session with the specified remote computer.</span></span> <span data-ttu-id="1926f-203">컴퓨터 이름을 하나만 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-203">Enter only one computer name.</span></span> <span data-ttu-id="1926f-204">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-204">The default is the local computer.</span></span>

<span data-ttu-id="1926f-205">컴퓨터의 NetBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-205">Type the NetBIOS name, the IP address, or the fully qualified domain name of the computer.</span></span> <span data-ttu-id="1926f-206">컴퓨터 이름을로 파이프 할 수도 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1926f-206">You can also pipe a computer name to `Enter-PSSession`.</span></span>

<span data-ttu-id="1926f-207">**ComputerName** 매개 변수 값에 IP 주소를 사용 하려면 명령에 **Credential** 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-207">To use an IP address in the value of the **ComputerName** parameter, the command must include the **Credential** parameter.</span></span> <span data-ttu-id="1926f-208">또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-208">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="1926f-209">TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="1926f-209">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](About/about_Remote_Troubleshooting.md).</span></span>

<span data-ttu-id="1926f-210">참고: Windows Vista 이상 버전의 Windows 운영 체제에서 **ComputerName** 매개 변수 값에 로컬 컴퓨터를 포함 하려면 관리자 권한으로 실행 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-210">Note: In Windows Vista and later versions of the Windows operating system, to include the local computer in the value of the **ComputerName** parameter, you must start PowerShell with the Run as administrator option.</span></span>

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

### <span data-ttu-id="1926f-211">-ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="1926f-211">-ConfigurationName</span></span>

<span data-ttu-id="1926f-212">대화형 세션에 사용할 세션 구성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-212">Specifies the session configuration that is used for the interactive session.</span></span>

<span data-ttu-id="1926f-213">세션 구성의 구성 이름 또는 정규화된 리소스 URI를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-213">Enter a configuration name or the fully qualified resource URI for a session configuration.</span></span> <span data-ttu-id="1926f-214">구성 이름만 지정 하는 경우에는 다음 스키마 URI가 앞에와 야 `http://schemas.microsoft.com/powershell` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-214">If you specify only the configuration name, the following schema URI is prepended: `http://schemas.microsoft.com/powershell`.</span></span>

<span data-ttu-id="1926f-215">SSH와 함께 사용 하는 경우 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-215">When used with SSH, this specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="1926f-216">SSH의 기본값은 `powershell` 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-216">The default value for SSH is the `powershell` subsystem.</span></span>

<span data-ttu-id="1926f-217">세션의 세션 구성은 원격 컴퓨터에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-217">The session configuration for a session is located on the remote computer.</span></span> <span data-ttu-id="1926f-218">지정된 세션 구성이 원격 컴퓨터에 없으면 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-218">If the specified session configuration does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="1926f-219">기본값은 `$PSSessionConfigurationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-219">The default value is the value of the `$PSSessionConfigurationName` preference variable on the local computer.</span></span> <span data-ttu-id="1926f-220">이 기본 설정 변수를 설정하지 않으면 Microsoft.PowerShell이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-220">If this preference variable is not set, the default is Microsoft.PowerShell.</span></span> <span data-ttu-id="1926f-221">자세한 내용은 [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-221">For more information, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

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

### <span data-ttu-id="1926f-222">-ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="1926f-222">-ConnectionUri</span></span>

<span data-ttu-id="1926f-223">세션에 대 한 연결 끝점을 정의 하는 URI를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-223">Specifies a URI that defines the connection endpoint for the session.</span></span> <span data-ttu-id="1926f-224">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-224">The URI must be fully qualified.</span></span> <span data-ttu-id="1926f-225">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-225">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="1926f-226">기본값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-226">The default value is as follows:</span></span>

`http://localhost:5985/WSMAN`

<span data-ttu-id="1926f-227">**ConnectionURI** 를 지정하지 않은 경우 **UseSSL**, **ComputerName**, **Port** 및 **ApplicationName** 매개 변수를 사용하여 **ConnectionURI** 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-227">If you do not specify a **ConnectionURI**, you can use the **UseSSL**, **ComputerName**, **Port**, and **ApplicationName** parameters to specify the **ConnectionURI** values.</span></span>

<span data-ttu-id="1926f-228">URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-228">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="1926f-229">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-229">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created by using standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="1926f-230">PowerShell 원격을 위한 기본 포트를 사용 하려면 HTTP의 경우 포트 5985을, HTTPS의 경우 5986을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-230">To use the default ports for PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

<span data-ttu-id="1926f-231">대상 컴퓨터에서 연결을 다른 URI로 리디렉션하는 경우 명령에서 **allowredirection** 매개 변수를 사용 하지 않으면 PowerShell에서 리디렉션을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-231">If the destination computer redirects the connection to a different URI, PowerShell prevents the redirection unless you use the **AllowRedirection** parameter in the command.</span></span>

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

### <span data-ttu-id="1926f-232">-ContainerId</span><span class="sxs-lookup"><span data-stu-id="1926f-232">-ContainerId</span></span>

<span data-ttu-id="1926f-233">컨테이너의 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-233">Specifies the ID of a container.</span></span>

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

### <span data-ttu-id="1926f-234">-Credential</span><span class="sxs-lookup"><span data-stu-id="1926f-234">-Credential</span></span>

<span data-ttu-id="1926f-235">이 작업을 수행할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-235">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="1926f-236">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-236">The default is the current user.</span></span>

<span data-ttu-id="1926f-237">**User01** 또는 **Domain01\User01** 과 같은 사용자 이름을 입력 하거나 cmdlet에 의해 생성 된 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="1926f-237">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1926f-238">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-238">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="1926f-239">자격 증명은 [PSCredential](/dotnet/api/system.management.automation.pscredential) 개체에 저장 되 고 암호는 [SecureString](/dotnet/api/system.security.securestring)으로 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-239">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="1926f-240">**Securestring** 데이터 보호에 대 한 자세한 [내용은 참조 하십시오](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="1926f-240">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="1926f-241">-EnableNetworkAccess</span><span class="sxs-lookup"><span data-stu-id="1926f-241">-EnableNetworkAccess</span></span>

<span data-ttu-id="1926f-242">이 cmdlet이 루프백 세션에 대화형 보안 토큰을 추가 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-242">Indicates that this cmdlet adds an interactive security token to loopback sessions.</span></span> <span data-ttu-id="1926f-243">대화형 토큰을 사용하면 다른 컴퓨터에서 데이터를 가져오는 명령을 루프백 세션에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-243">The interactive token lets you run commands in the loopback session that get data from other computers.</span></span> <span data-ttu-id="1926f-244">예를 들어 원격 컴퓨터에서 로컬 컴퓨터로 XML 파일을 복사하는 세션에서 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-244">For example, you can run a command in the session that copies XML files from a remote computer to the local computer.</span></span>

<span data-ttu-id="1926f-245">루프백 세션은 동일한 컴퓨터에서 시작 하 여 종료 되는 **PSSession** 입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-245">A loopback session is a **PSSession** that originates and ends on the same computer.</span></span> <span data-ttu-id="1926f-246">루프백 세션을 만들려면 **ComputerName** 매개 변수를 생략 하거나 값을로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-246">To create a loopback session, omit the **ComputerName** parameter or set its value to .</span></span> <span data-ttu-id="1926f-247">(점), localhost 또는 로컬 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-247">(dot), localhost, or the name of the local computer.</span></span>

<span data-ttu-id="1926f-248">기본적으로 루프백 세션은 원격 컴퓨터를 인증 하는 데 충분 한 권한을 제공 하지 않을 수 있는 네트워크 토큰을 사용 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-248">By default, loopback sessions are created by using a network token, which might not provide sufficient permission to authenticate to remote computers.</span></span>

<span data-ttu-id="1926f-249">**EnableNetworkAccess** 매개 변수는 루프백 세션에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-249">The **EnableNetworkAccess** parameter is effective only in loopback sessions.</span></span> <span data-ttu-id="1926f-250">원격 컴퓨터에서 세션을 만들 때 **EnableNetworkAccess** 를 사용 하는 경우 명령은 성공 하지만 매개 변수는 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-250">If you use **EnableNetworkAccess** when you create a session on a remote computer, the command succeeds, but the parameter is ignored.</span></span>

<span data-ttu-id="1926f-251">또한 세션 자격 증명을 다른 컴퓨터에 위임하는 **CredSSP** 매개 변수의 **Authentication** 값을 사용하여 루프백 세션에서 원격 액세스를 허용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-251">You can also allow remote access in a loopback session by using the **CredSSP** value of the **Authentication** parameter, which delegates the session credentials to other computers.</span></span>

<span data-ttu-id="1926f-252">이 매개 변수는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-252">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="1926f-253">-HostName</span><span class="sxs-lookup"><span data-stu-id="1926f-253">-HostName</span></span>

<span data-ttu-id="1926f-254">SSH (Secure Shell) 기반 연결에 대 한 컴퓨터 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-254">Specifies a computer name for a Secure Shell (SSH) based connection.</span></span> <span data-ttu-id="1926f-255">이는 원격 컴퓨터에 대 한 연결이 Windows WinRM이 아닌 SSH를 사용 하는 경우를 제외 하 고 **ComputerName** 매개 변수와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-255">This is similar to the **ComputerName** parameter except that the connection to the remote computer is made using SSH rather than Windows WinRM.</span></span> <span data-ttu-id="1926f-256">이 매개 변수는 형식을 사용 하 여 호스트 이름 매개 변수 값의 일부로 사용자 이름 및/또는 포트를 지정 하도록 지원 합니다 `user@hostname:port` .</span><span class="sxs-lookup"><span data-stu-id="1926f-256">This parameter supports specifying the user name and/or port as part of the host name parameter value using the form `user@hostname:port`.</span></span> <span data-ttu-id="1926f-257">호스트 이름의 일부로 지정 된 사용자 이름 및/또는 포트가 `-UserName` 지정 된 경우 및 매개 변수 보다 우선적으로 적용 `-Port` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-257">The user name and/or port specified as part of the host name takes precedence over the `-UserName` and `-Port` parameters, if specified.</span></span> <span data-ttu-id="1926f-258">이를 통해 특정 사용자 이름 및/또는 포트를 포함 하는 여러 컴퓨터 이름을이 매개 변수에 전달할 수 있으며, 다른 사용자 이름 및/또는 포트는 `-UserName` 및 매개 변수에서 사용할 수 있습니다 `-Port` .</span><span class="sxs-lookup"><span data-stu-id="1926f-258">This allows passing multiple computer names to this parameter where some have specific user names and/or ports, while others use the user name and/or port from the `-UserName` and `-Port` parameters.</span></span>

<span data-ttu-id="1926f-259">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-259">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="1926f-260">-Id</span><span class="sxs-lookup"><span data-stu-id="1926f-260">-Id</span></span>

<span data-ttu-id="1926f-261">기존 세션의 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-261">Specifies the ID of an existing session.</span></span> <span data-ttu-id="1926f-262">`Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-262">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="1926f-263">세션의 ID를 찾으려면 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1926f-263">To find the ID of a session, use the `Get-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="1926f-264">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="1926f-264">-InstanceId</span></span>

<span data-ttu-id="1926f-265">기존 세션의 인스턴스 ID를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-265">Specifies the instance ID of an existing session.</span></span> <span data-ttu-id="1926f-266">`Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-266">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="1926f-267">인스턴스 ID는 GUID입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-267">The instance ID is a GUID.</span></span> <span data-ttu-id="1926f-268">세션의 인스턴스 ID를 확인 하려면 cmdlet을 사용 합니다 `Get-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1926f-268">To find the instance ID of a session, use the `Get-PSSession` cmdlet.</span></span> <span data-ttu-id="1926f-269">**Session**, **Name** 또는 **ID** 매개 변수를 사용 하 여 기존 세션을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-269">You can also use the **Session**, **Name**, or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="1926f-270">또는 **ComputerName** 매개 변수를 사용 하 여 임시 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-270">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

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

### <span data-ttu-id="1926f-271">-KeyFilePath</span><span class="sxs-lookup"><span data-stu-id="1926f-271">-KeyFilePath</span></span>

<span data-ttu-id="1926f-272">SSH (Secure Shell)에서 원격 컴퓨터의 사용자를 인증 하는 데 사용 하는 키 파일 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-272">Specifies a key file path used by Secure Shell (SSH) to authenticate a user on a remote computer.</span></span>

<span data-ttu-id="1926f-273">SSH를 사용 하면 기본 암호 인증 대신 개인/공개 키를 통해 사용자 인증을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-273">SSH allows user authentication to be performed via private/public keys as an alternative to basic password authentication.</span></span> <span data-ttu-id="1926f-274">키 인증을 사용 하도록 원격 컴퓨터를 구성 하는 경우이 매개 변수를 사용 하 여 사용자를 식별 하는 키를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-274">If the remote computer is configured for key authentication then this parameter can be used to provide the key that identifies the user.</span></span>

<span data-ttu-id="1926f-275">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-275">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="1926f-276">-Name</span><span class="sxs-lookup"><span data-stu-id="1926f-276">-Name</span></span>

<span data-ttu-id="1926f-277">기존 세션의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-277">Specifies the friendly name of an existing session.</span></span> <span data-ttu-id="1926f-278">`Enter-PSSession` 대화형 세션에 대해 지정 된 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-278">`Enter-PSSession` uses the specified session for the interactive session.</span></span>

<span data-ttu-id="1926f-279">지정한 이름이 둘 이상의 세션과 일치하는 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-279">If the name that you specify matches more than one session, the command fails.</span></span> <span data-ttu-id="1926f-280">**Session**, **InstanceID** 또는 **ID** 매개 변수를 사용 하 여 기존 세션을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-280">You can also use the **Session**, **InstanceID**, or **ID** parameters to specify an existing session.</span></span> <span data-ttu-id="1926f-281">또는 **ComputerName** 매개 변수를 사용 하 여 임시 세션을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-281">Or, you can use the **ComputerName** parameter to start a temporary session.</span></span>

<span data-ttu-id="1926f-282">세션의 이름을 설정 하려면 cmdlet의 **name** 매개 변수를 사용 합니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1926f-282">To establish a friendly name for a session, use the **Name** parameter of the `New-PSSession` cmdlet.</span></span>

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

### <span data-ttu-id="1926f-283">-Port</span><span class="sxs-lookup"><span data-stu-id="1926f-283">-Port</span></span>

<span data-ttu-id="1926f-284">이 명령에 사용 되는 원격 컴퓨터의 네트워크 포트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-284">Specifies the network port on the remote computer that is used for this command.</span></span>

<span data-ttu-id="1926f-285">PowerShell 6.0에서이 매개 변수는 SSH (Secure Shell) 연결을 지 원하는 **HostName** 매개 변수 집합에서 가져왔습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-285">In PowerShell 6.0 this parameter was inlcuded in the **HostName** parameter set which supports Secure Shell (SSH) connections.</span></span>

<span data-ttu-id="1926f-286">**WinRM (ComputerName 매개 변수 설정)**</span><span class="sxs-lookup"><span data-stu-id="1926f-286">**WinRM (ComputerName parameter set)**</span></span>

<span data-ttu-id="1926f-287">원격 컴퓨터에 연결하려면 원격 컴퓨터가 연결에서 사용하는 포트에서 수신 대기하고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-287">To connect to a remote computer, the remote computer must be listening on the port that the connection uses.</span></span> <span data-ttu-id="1926f-288">기본 포트는 HTTP의 WinRM 포트인 5985이 고, HTTPS의 경우 WinRM 포트인 5986입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-288">The default ports are 5985, which is the WinRM port for HTTP, and 5986, which is the WinRM port for HTTPS.</span></span>

<span data-ttu-id="1926f-289">대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-289">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span> <span data-ttu-id="1926f-290">다음 명령을 사용하여 수신기를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-290">Use the following commands to configure the listener:</span></span>

1. `winrm delete winrm/config/listener?Address=*+Transport=HTTP`
2. `winrm create winrm/config/listener?Address=*+Transport=HTTP @{Port="\<port-number\>"}`

<span data-ttu-id="1926f-291">필요한 경우가 아니면 **Port** 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-291">Do not use the **Port** parameter unless you must.</span></span> <span data-ttu-id="1926f-292">명령의 포트 설정은 이 명령이 실행되는 모든 컴퓨터나 세션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-292">The port setting in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="1926f-293">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-293">An alternate port setting might prevent the command from running on all computers.</span></span>

<span data-ttu-id="1926f-294">**SSH (호스트 이름 매개 변수 집합)**</span><span class="sxs-lookup"><span data-stu-id="1926f-294">**SSH (HostName parameter set)**</span></span>

<span data-ttu-id="1926f-295">원격 컴퓨터에 연결 하려면 SSH 서비스 (SSHD)를 사용 하 여 원격 컴퓨터를 구성 하 고 연결에서 사용 하는 포트에서 수신 대기 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-295">To connect to a remote computer, the remote computer must be configured with the SSH service (SSHD) and must be listening on the port that the connection uses.</span></span> <span data-ttu-id="1926f-296">SSH에 대 한 기본 포트는 22입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-296">The default port for SSH is 22.</span></span>

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

### <span data-ttu-id="1926f-297">-RunAsAdministrator</span><span class="sxs-lookup"><span data-stu-id="1926f-297">-RunAsAdministrator</span></span>

<span data-ttu-id="1926f-298">**PSSession** 이 관리자 권한으로 실행 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-298">Indicates that the **PSSession** runs as administrator.</span></span>

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

### <span data-ttu-id="1926f-299">-Session</span><span class="sxs-lookup"><span data-stu-id="1926f-299">-Session</span></span>

<span data-ttu-id="1926f-300">대화형 세션에 사용할 PowerShell 세션 (**PSSession**)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-300">Specifies a PowerShell session (**PSSession**) to use for the interactive session.</span></span> <span data-ttu-id="1926f-301">이 매개 변수는 세션 개체를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-301">This parameter takes a session object.</span></span> <span data-ttu-id="1926f-302">**Name**, **InstanceID** 또는 **ID** 매개 변수를 사용 하 여 **PSSession** 을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-302">You can also use the **Name**, **InstanceID**, or **ID** parameters to specify a **PSSession**.</span></span>

<span data-ttu-id="1926f-303">세션 개체를 포함 하는 변수를 입력 하거나 세션 개체를 만들거나 가져오는 명령 (예: 또는 명령)을 입력 `New-PSSession` `Get-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-303">Enter a variable that contains a session object or a command that creates or gets a session object, such as a `New-PSSession` or `Get-PSSession` command.</span></span> <span data-ttu-id="1926f-304">세션 개체를로 파이프 할 수도 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1926f-304">You can also pipe a session object to `Enter-PSSession`.</span></span> <span data-ttu-id="1926f-305">이 매개 변수를 사용 하 여 하나의 **PSSession** 만 제출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-305">You can submit only one **PSSession** by using this parameter.</span></span> <span data-ttu-id="1926f-306">둘 이상의 **PSSession** 이 포함 된 변수를 입력 하는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-306">If you enter a variable that contains more than one **PSSession**, the command fails.</span></span>

<span data-ttu-id="1926f-307">`Exit-PSSession`또는 **EXIT** 키워드를 사용 하는 경우 대화형 세션이 종료 되지만 사용자가 만든 **PSSession** 은 계속 열려 있고 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-307">When you use `Exit-PSSession` or the **EXIT** keyword, the interactive session ends, but the **PSSession** that you created remains open and available for use.</span></span>

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

### <span data-ttu-id="1926f-308">-SessionOption</span><span class="sxs-lookup"><span data-stu-id="1926f-308">-SessionOption</span></span>

<span data-ttu-id="1926f-309">세션의 고급 옵션을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-309">Sets advanced options for the session.</span></span> <span data-ttu-id="1926f-310">Cmdlet을 사용 하 여 만든 것과 같은 **sessionoption** 개체를 입력 `New-PSSessionOption` 하거나 키가 세션 옵션 이름이 고 값이 session 옵션 값인 해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-310">Enter a **SessionOption** object, such as one that you create by using the `New-PSSessionOption` cmdlet, or a hash table in which the keys are session option names and the values are session option values.</span></span>

<span data-ttu-id="1926f-311">옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-311">The default values for the options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="1926f-312">그러지 않으면 기본값은 세션 구성에 설정된 옵션에 따라 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-312">Otherwise, the default values are established by options set in the session configuration.</span></span>

<span data-ttu-id="1926f-313">세션 옵션 값은 기본 설정 변수 및 세션 구성에 설정 된 세션의 기본값 보다 우선 적용 `$PSSessionOption` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-313">The session option values take precedence over default values for sessions set in the `$PSSessionOption` preference variable and in the session configuration.</span></span> <span data-ttu-id="1926f-314">그러나 이러한 값은 세션 구성에 설정된 최대값, 할당량 또는 제한보다 우선하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-314">However, they do not take precedence over maximum values, quotas or limits set in the session configuration.</span></span>

<span data-ttu-id="1926f-315">기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은을 참조 하십시오 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="1926f-315">For a description of the session options, including the default values, see `New-PSSessionOption`.</span></span>
<span data-ttu-id="1926f-316">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-316">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span> <span data-ttu-id="1926f-317">세션 구성에 대 한 자세한 내용은 [about_Session_Configurations](About/about_Session_Configurations.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-317">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

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

### <span data-ttu-id="1926f-318">-SSHTransport</span><span class="sxs-lookup"><span data-stu-id="1926f-318">-SSHTransport</span></span>

<span data-ttu-id="1926f-319">SSH (Secure Shell)를 사용 하 여 원격 연결을 설정 했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-319">Indicates that the remote connection is established using Secure Shell (SSH).</span></span>

<span data-ttu-id="1926f-320">기본적으로 PowerShell은 Windows WinRM을 사용 하 여 원격 컴퓨터에 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-320">By default PowerShell uses Windows WinRM to connect to a remote computer.</span></span> <span data-ttu-id="1926f-321">이 스위치를 사용 하면 PowerShell에서 호스트 이름 매개 변수 집합을 사용 하 여 SSH 기반 원격 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-321">This switch forces PowerShell to use the HostName parameter set for establishing an SSH based remote connection.</span></span>

<span data-ttu-id="1926f-322">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-322">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="1926f-323">-하위 시스템</span><span class="sxs-lookup"><span data-stu-id="1926f-323">-Subsystem</span></span>

<span data-ttu-id="1926f-324">새 **PSSession** 에 사용 되는 SSH 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-324">Specifies the SSH subsystem used for the new **PSSession**.</span></span>

<span data-ttu-id="1926f-325">이는 sshd_config에 정의 된 대로 대상에서 사용할 하위 시스템을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-325">This specifies the subsystem to use on the target as defined in sshd_config.</span></span> <span data-ttu-id="1926f-326">하위 시스템은 미리 정의 된 매개 변수를 사용 하 여 특정 버전의 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-326">The subsystem starts a specific version of PowerShell with predefined parameters.</span></span> <span data-ttu-id="1926f-327">지정 된 하위 시스템이 원격 컴퓨터에 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-327">If the specified subsystem does not exist on the remote computer, the command fails.</span></span>

<span data-ttu-id="1926f-328">이 매개 변수를 사용 하지 않는 경우 기본값은 ' powershell ' 하위 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-328">If this parameter is not used, the default is the 'powershell' subsystem.</span></span>

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

### <span data-ttu-id="1926f-329">-UserName</span><span class="sxs-lookup"><span data-stu-id="1926f-329">-UserName</span></span>

<span data-ttu-id="1926f-330">원격 컴퓨터에서 세션을 만드는 데 사용 되는 계정의 사용자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-330">Specifies the user name for the account used to create a session on the remote computer.</span></span> <span data-ttu-id="1926f-331">사용자 인증 방법은 원격 컴퓨터에서 SSH (Secure Shell)가 구성 된 방식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-331">User authentication method will depend on how Secure Shell (SSH) is configured on the remote computer.</span></span>

<span data-ttu-id="1926f-332">SSH가 기본 암호 인증으로 구성 된 경우 사용자 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-332">If SSH is configured for basic password authentication then you will be prompted for the user password.</span></span>

<span data-ttu-id="1926f-333">키 기반 사용자 인증에 대해 SSH를 구성 하는 경우 키 파일 경로를 **Keyfilepath** 매개 변수를 통해 제공할 수 있으며 암호 프롬프트가 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-333">If SSH is configured for key based user authentication then a key file path can be provided via the **KeyFilePath** parameter and no password prompt will occur.</span></span> <span data-ttu-id="1926f-334">클라이언트 사용자 키 파일이 SSH 알려진 위치에 있는 경우 키 기반 인증에는 **Keyfilepath** 매개 변수가 필요 하지 않으며 사용자 인증은 사용자 이름에 따라 자동으로 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-334">Note that if the client user key file is located in an SSH known location then the **KeyFilePath** parameter is not needed for key based authentication, and user authentication will occur automatically based on the user name.</span></span> <span data-ttu-id="1926f-335">자세한 내용은 키 기반 사용자 인증에 대 한 SSH 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-335">See SSH documentation about key based user authentication for more information.</span></span>

<span data-ttu-id="1926f-336">필수 매개 변수가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-336">This is not a required parameter.</span></span> <span data-ttu-id="1926f-337">**UserName** 매개 변수를 지정 하지 않으면 현재 로그온 사용자 이름이 연결에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-337">If no **UserName** parameter is specified then the current log on user name is used for the connection.</span></span>

<span data-ttu-id="1926f-338">이 매개 변수는 PowerShell 6.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-338">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="1926f-339">-UseSSL</span><span class="sxs-lookup"><span data-stu-id="1926f-339">-UseSSL</span></span>

<span data-ttu-id="1926f-340">이 cmdlet이 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 원격 컴퓨터에 대 한 연결을 설정 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-340">Indicates that this cmdlet uses the Secure Sockets Layer (SSL) protocol to establish a connection to the remote computer.</span></span> <span data-ttu-id="1926f-341">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-341">By default, SSL is not used.</span></span>

<span data-ttu-id="1926f-342">WS-Management는 네트워크를 통해 전송 되는 모든 PowerShell 콘텐츠를 암호화 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-342">WS-Management encrypts all PowerShell content transmitted over the network.</span></span> <span data-ttu-id="1926f-343">**UseSSL** 매개 변수는 HTTP 연결 대신 HTTPS 연결을 통해 데이터를 전송 하는 추가 보호 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-343">The **UseSSL** parameter is an additional protection that sends the data across an HTTPS connection instead of an HTTP connection.</span></span>

<span data-ttu-id="1926f-344">이 매개 변수를 사용 하지만 명령에 사용 되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-344">If you use this parameter, but SSL is not available on the port that is used for the command, the command fails.</span></span>

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

### <span data-ttu-id="1926f-345">-VMId</span><span class="sxs-lookup"><span data-stu-id="1926f-345">-VMId</span></span>

<span data-ttu-id="1926f-346">가상 컴퓨터의 ID를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-346">Specifies the ID of a virtual machine.</span></span>

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

### <span data-ttu-id="1926f-347">-VMName</span><span class="sxs-lookup"><span data-stu-id="1926f-347">-VMName</span></span>

<span data-ttu-id="1926f-348">가상 컴퓨터의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-348">Specifies the name of a virtual machine.</span></span>

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

### <span data-ttu-id="1926f-349">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1926f-349">CommonParameters</span></span>

<span data-ttu-id="1926f-350">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1926f-350">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1926f-351">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-351">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1926f-352">입력</span><span class="sxs-lookup"><span data-stu-id="1926f-352">INPUTS</span></span>

### <span data-ttu-id="1926f-353">System.string (Runspace, 시스템.</span><span class="sxs-lookup"><span data-stu-id="1926f-353">System.String, System.Management.Automation.Runspaces.PSSession</span></span>

<span data-ttu-id="1926f-354">컴퓨터 이름, 문자열 또는 세션 개체를이 cmdlet으로 파이프 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-354">You can pipe a computer name, as a string, or a session object to this cmdlet.</span></span>

## <span data-ttu-id="1926f-355">출력</span><span class="sxs-lookup"><span data-stu-id="1926f-355">OUTPUTS</span></span>

### <span data-ttu-id="1926f-356">없음</span><span class="sxs-lookup"><span data-stu-id="1926f-356">None</span></span>

<span data-ttu-id="1926f-357">이 cmdlet은 어떠한 출력도 반환되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-357">The cmdlet does not return any output.</span></span>

## <span data-ttu-id="1926f-358">참고</span><span class="sxs-lookup"><span data-stu-id="1926f-358">NOTES</span></span>

<span data-ttu-id="1926f-359">원격 컴퓨터에 연결하려면 원격 컴퓨터의 Administrators 그룹 구성원이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-359">To connect to a remote computer, you must be a member of the Administrators group on the remote computer.</span></span> <span data-ttu-id="1926f-360">로컬 컴퓨터에서 대화형 세션을 시작 하려면 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-360">To start an interactive session on the local computer, you must start PowerShell with the **Run as administrator** option.</span></span>

<span data-ttu-id="1926f-361">를 사용 하는 경우 `Enter-PSSession` 원격 컴퓨터의 사용자 프로필이 대화형 세션에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-361">When you use `Enter-PSSession`, your user profile on the remote computer is used for the interactive session.</span></span> <span data-ttu-id="1926f-362">PowerShell 모듈을 추가 하 고 명령 프롬프트를 변경 하는 명령을 비롯 한 원격 사용자 프로필의 명령은 원격 프롬프트가 표시 되기 전에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-362">The commands in the remote user profile, including commands to add PowerShell modules and to change the command prompt, run before the remote prompt is displayed.</span></span>

<span data-ttu-id="1926f-363">`Enter-PSSession` 는 대화형 세션을 위해 로컬 컴퓨터에서 UI 문화권 설정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-363">`Enter-PSSession` uses the UI culture setting on the local computer for the interactive session.</span></span> <span data-ttu-id="1926f-364">로컬 UI 문화권을 찾으려면 자동 변수를 사용 `$UICulture` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-364">To find the local UI culture, use the `$UICulture` automatic variable.</span></span>

<span data-ttu-id="1926f-365">`Enter-PSSession``Get-Command`, `Out-Default` 및 cmdlet이 필요 `Exit-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-365">`Enter-PSSession` requires the `Get-Command`, `Out-Default`, and `Exit-PSSession` cmdlets.</span></span> <span data-ttu-id="1926f-366">이러한 cmdlet이 원격 컴퓨터의 세션 구성에 포함 되지 않은 경우 `Enter-PSSession` 명령이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-366">If these cmdlets are not included in the session configuration on the remote computer, the `Enter-PSSession` commands fails.</span></span>

<span data-ttu-id="1926f-367">가 `Invoke-Command` 원격 컴퓨터에 보내기 전에 명령을 구문 분석 하 고 해석 하는와 달리는 `Enter-PSSession` 명령을 해석 하지 않고 원격 컴퓨터에 직접 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-367">Unlike `Invoke-Command`, which parses and interprets the commands before it sends them to the remote computer, `Enter-PSSession` sends the commands directly to the remote computer without interpretation.</span></span>

<span data-ttu-id="1926f-368">입력 하려는 세션이 명령을 처리 하는 중이면 PowerShell이 명령에 응답 하기 전에 지연이 있을 수 있습니다 `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="1926f-368">If the session you want to enter is busy processing a command, there might be a delay before PowerShell responds to the `Enter-PSSession` command.</span></span> <span data-ttu-id="1926f-369">세션을 사용할 수 있게 되 면 즉시 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-369">You are connected as soon as the session is available.</span></span> <span data-ttu-id="1926f-370">명령을 취소 하려면 `Enter-PSSession` <kbd>ctrl</kbd> + <kbd>C</kbd>를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-370">To cancel the `Enter-PSSession` command, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="1926f-371">**HostName** 매개 변수 집합은 PowerShell 6.0부터 포함 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-371">The **HostName** parameter set was included starting with PowerShell 6.0.</span></span> <span data-ttu-id="1926f-372">Secure Shell (SSH)를 기반으로 PowerShell 원격 기능을 제공 하기 위해 추가 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-372">It was added to provide PowerShell remoting based on Secure Shell (SSH).</span></span> <span data-ttu-id="1926f-373">SSH와 PowerShell은 여러 플랫폼 (Windows, Linux, macOS)에서 지원 되며 powershell 원격은 PowerShell 및 SSH가 설치 되 고 구성 되는 이러한 플랫폼에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-373">Both SSH and PowerShell are supported on multiple platforms (Windows, Linux, macOS) and PowerShell remoting will work over these platforms where PowerShell and SSH are installed and configured.</span></span> <span data-ttu-id="1926f-374">이는 WinRM을 기반으로 하는 이전 Windows 전용 원격 시스템과 별개 이며, 대부분의 WinRM 특정 기능 및 제한 사항이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-374">This is separate from the previous Windows only remoting that is based on WinRM and much of the WinRM specific features and limitations do not apply.</span></span> <span data-ttu-id="1926f-375">예를 들어 WinRM 기반 할당량, 세션 옵션, 사용자 지정 끝점 구성 및 연결 끊기/다시 연결 기능은 현재 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-375">For example, WinRM based quotas, session options, custom endpoint configuration, and disconnect/reconnect features are currently not supported.</span></span> <span data-ttu-id="1926f-376">PowerShell SSH 원격을 설정 하는 방법에 대 한 자세한 내용은 [ssh를 통한 Powershell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1926f-376">For more information about how to set up PowerShell SSH remoting, see [PowerShell Remoting Over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

<span data-ttu-id="1926f-377">PowerShell 7.1 이전에는 SSH를 통한 원격 기능이 두 번째 홉 원격 세션을 지원하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-377">Prior to PowerShell 7.1, remoting over SSH did not support second-hop remote sessions.</span></span> <span data-ttu-id="1926f-378">해당 기능은 WinRM을 사용하는 세션으로 제한되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-378">This capability was limited to sessions using WinRM.</span></span> <span data-ttu-id="1926f-379">PowerShell 7.1을 사용하면 `Enter-PSSession` 및 `Enter-PSHostProcess`가 대화형 원격 세션 내에서 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1926f-379">PowerShell 7.1 allows `Enter-PSSession` and `Enter-PSHostProcess` to work from within any interactive remote session.</span></span>

## <span data-ttu-id="1926f-380">관련 링크</span><span class="sxs-lookup"><span data-stu-id="1926f-380">RELATED LINKS</span></span>

[<span data-ttu-id="1926f-381">Exit-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-381">Exit-PSSession</span></span>](Exit-PSSession.md)

[<span data-ttu-id="1926f-382">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-382">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="1926f-383">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="1926f-383">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="1926f-384">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-384">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="1926f-385">Remove-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-385">Remove-PSSession</span></span>](Remove-PSSession.md)

[<span data-ttu-id="1926f-386">Connect-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-386">Connect-PSSession</span></span>](Connect-PSSession.md)

[<span data-ttu-id="1926f-387">Disconnect-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-387">Disconnect-PSSession</span></span>](Disconnect-PSSession.md)

[<span data-ttu-id="1926f-388">Receive-PSSession</span><span class="sxs-lookup"><span data-stu-id="1926f-388">Receive-PSSession</span></span>](Receive-PSSession.md)

[<span data-ttu-id="1926f-389">about_PSSessions</span><span class="sxs-lookup"><span data-stu-id="1926f-389">about_PSSessions</span></span>](About/about_PSSessions.md)

[<span data-ttu-id="1926f-390">about_Remote</span><span class="sxs-lookup"><span data-stu-id="1926f-390">about_Remote</span></span>](About/about_Remote.md)
