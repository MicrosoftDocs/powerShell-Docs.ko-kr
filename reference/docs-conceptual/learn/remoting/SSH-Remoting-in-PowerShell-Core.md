---
title: SSH를 통한 PowerShell 원격
description: SSH를 사용하여 PowerShell Core에서 원격 작업
ms.date: 08/14/2018
ms.openlocfilehash: d994a3888b9a372b803a65666634775a8905d63a
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68372144"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="38a88-103">SSH를 통한 PowerShell 원격</span><span class="sxs-lookup"><span data-stu-id="38a88-103">PowerShell Remoting Over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="38a88-104">개요</span><span class="sxs-lookup"><span data-stu-id="38a88-104">Overview</span></span>

<span data-ttu-id="38a88-105">PowerShell 원격 기능은 일반적으로 연결 협상 및 데이터 전송에 WinRM을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="38a88-106">이제 SSH를 Linux 및 Windows 플랫폼에서 사용할 수 있으며 진정한 다중 플랫폼 PowerShell 원격 기능이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="38a88-107">WinRM은 PowerShell 원격 세션을 위한 강력한 호스팅 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="38a88-108">SSH 기반 원격 기능은 원격 엔드포인트 구성 및 JEA(Just Enough Administration)를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-108">SSH-based remoting doesn't currently support remote endpoint configuration and JEA (Just Enough Administration).</span></span>

<span data-ttu-id="38a88-109">SSH 원격 기능을 사용하면 Windows 및 Linux 컴퓨터 간에 기본적인 PowerShell 세션 원격 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux machines.</span></span> <span data-ttu-id="38a88-110">SSH 원격 기능은 대상 컴퓨터에 SSH 하위 시스템으로 PowerShell 호스트 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-110">SSH Remoting creates a PowerShell host process on the target machine as an SSH subsystem.</span></span> <span data-ttu-id="38a88-111">앞으로는 엔드포인트 구성 및 JEA를 지원하기 위해 WinRM과 유사한 일반 호스팅 모델을 구현할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="38a88-112">`New-PSSession`, `Enter-PSSession` 및 `Invoke-Command` cmdlet에는 이제 이 새로운 원격 연결을 지원하기 위한 새로운 매개 변수가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="38a88-113">원격 세션을 만들려면 `HostName` 매개 변수를 사용하여 대상 컴퓨터를 지정하고 `UserName`을 사용하여 사용자 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-113">To create a remote session, you specify the target machine with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="38a88-114">cmdlet을 대화형으로 실행하면 암호를 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="38a88-115">`KeyFilePath` 매개 변수와 함께 프라이빗 키 파일을 사용하여 SSH 키 인증을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="38a88-116">일반적인 설치 정보</span><span class="sxs-lookup"><span data-stu-id="38a88-116">General setup information</span></span>

<span data-ttu-id="38a88-117">SSH는 모든 컴퓨터에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-117">SSH must be installed on all machines.</span></span> <span data-ttu-id="38a88-118">컴퓨터에서 들어오고 나가는 원격 작업을 수행할 수 있도록 SSH 클라이언트(`ssh.exe`) 및 서버(`sshd.exe`)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the machines.</span></span> <span data-ttu-id="38a88-119">Windows용 OpenSSH는 이제 Windows 10 빌드 1809 및 Windows Server 2019에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="38a88-120">자세한 내용은 [Windows용 OpenSSH](/windows-server/administration/openssh/openssh_overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38a88-120">For more information, see [OpenSSH for Windows](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="38a88-121">Linux의 경우 플랫폼에 적합한 SSH(sshd 서버 포함)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-121">For Linux, install SSH (including sshd server) appropriate to your platform.</span></span> <span data-ttu-id="38a88-122">또한 SSH 원격 기능을 가져오려면 GitHub에서 PowerShell Core를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-122">You also need to install PowerShell Core from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="38a88-123">SSH 서버는 원격 컴퓨터에 PowerShell 프로세스를 호스트하기 위해 SSH 하위 시스템을 만들도록 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote machine.</span></span> <span data-ttu-id="38a88-124">또한 암호 또는 키 기반 인증도 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-124">You also must configure enable password or key-based authentication.</span></span>

## <a name="set-up-on-windows-machine"></a><span data-ttu-id="38a88-125">Windows 컴퓨터에 설치</span><span class="sxs-lookup"><span data-stu-id="38a88-125">Set up on Windows Machine</span></span>

1. <span data-ttu-id="38a88-126">최신 버전의 [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi) 설치</span><span class="sxs-lookup"><span data-stu-id="38a88-126">Install the latest version of [PowerShell Core for Windows](../../install/installing-powershell-core-on-windows.md#msi)</span></span>

   - <span data-ttu-id="38a88-127">`New-PSSession`의 매개 변수 집합을 확인하면 SSH 원격 기능이 지원되는지 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-127">You can tell if it has the SSH remoting support by looking at the parameter sets for `New-PSSession`</span></span>

   ```powershell
   Get-Command New-PSSession -syntax
   ```

   ```output
   New-PSSession [-HostName] <string[]> [-Name <string[]>] [-UserName <string>] [-KeyFilePath <string>] [-SSHTransport] [<CommonParameters>]
   ```

2. <span data-ttu-id="38a88-128">최신 Win32 OpenSSH를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-128">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="38a88-129">설치 지침은 [OpenSSH 설치](/windows-server/administration/openssh/openssh_install_firstuse)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38a88-129">For installation instructions, see [Installation of OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>
3. <span data-ttu-id="38a88-130">`$env:ProgramData\ssh`에 있는 `sshd_config` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-130">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   - <span data-ttu-id="38a88-131">암호 인증이 활성화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-131">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

     ```
     Subsystem    powershell c:/program files/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
     ```

     > [!NOTE]
     > <span data-ttu-id="38a88-132">하위 시스템 실행 파일 경로의 작업에서 공백을 방지하는 Windows용 OpenSSH에 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-132">There is a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="38a88-133">자세한 내용은 [이 GitHub 문제](https://github.com/PowerShell/Win32-OpenSSH/issues/784)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38a88-133">For more information, see [this GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>

     <span data-ttu-id="38a88-134">한 가지 해결 방법은 공백이 없는 PowerShell 설치 디렉터리에 symlink를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-134">One solution is to create a symlink to the PowerShell installation directory that doesn't have spaces:</span></span>

     ```powershell
     mklink /D c:\pwsh "C:\Program Files\PowerShell\6"
     ```

     <span data-ttu-id="38a88-135">그런 다음, 하위 시스템에 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-135">and then enter it in the subsystem:</span></span>

     ```
     Subsystem    powershell c:\pwsh\pwsh.exe -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="38a88-136">필요에 따라 키 인증을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-136">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

4. <span data-ttu-id="38a88-137">sshd 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-137">Restart the sshd service</span></span>

   ```powershell
   Restart-Service sshd
   ```

5. <span data-ttu-id="38a88-138">Path 환경 변수에 OpenSSH가 설치된 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-138">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="38a88-139">정의합니다(예: `C:\Program Files\OpenSSH\`).</span><span class="sxs-lookup"><span data-stu-id="38a88-139">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="38a88-140">이 항목을 입력하면 ssh.exe를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-140">This entry allows for the ssh.exe to be found.</span></span>

## <a name="set-up-on-linux-ubuntu-1604-machine"></a><span data-ttu-id="38a88-141">Linux(Ubuntu 16.04) 머신에 설치</span><span class="sxs-lookup"><span data-stu-id="38a88-141">Set up on Linux (Ubuntu 16.04) Machine</span></span>

1. <span data-ttu-id="38a88-142">GitHub에서 최신 [Linux용 PowerShell Core](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) 빌드를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-142">Install the latest [PowerShell Core for Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604) build from GitHub</span></span>
2. <span data-ttu-id="38a88-143">필요에 따라 [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-143">Install [Ubuntu SSH](https://help.ubuntu.com/lts/serverguide/openssh-server.html) as needed</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

3. <span data-ttu-id="38a88-144">/etc/ssh 위치에서 sshd_config 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-144">Edit the sshd_config file at location /etc/ssh</span></span>

   - <span data-ttu-id="38a88-145">암호 인증이 활성화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-145">Make sure password authentication is enabled</span></span>

   ```
   PasswordAuthentication yes
   ```

   - <span data-ttu-id="38a88-146">PowerShell 하위 시스템 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-146">Add a PowerShell subsystem entry</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   - <span data-ttu-id="38a88-147">필요에 따라 키 인증을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-147">Optionally enable key authentication</span></span>

   ```
   PubkeyAuthentication yes
   ```

4. <span data-ttu-id="38a88-148">sshd 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-148">Restart the sshd service</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-macos-machine"></a><span data-ttu-id="38a88-149">MacOS 컴퓨터에 설치</span><span class="sxs-lookup"><span data-stu-id="38a88-149">Set up on MacOS Machine</span></span>

1. <span data-ttu-id="38a88-150">최신 [MacOS용 PowerShell Core](../../install/installing-powershell-core-on-macos.md) 빌드를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-150">Install the latest [PowerShell Core for MacOS](../../install/installing-powershell-core-on-macos.md) build</span></span>

   - <span data-ttu-id="38a88-151">다음 단계를 수행하여 SSH 원격 기능이 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-151">Make sure SSH Remoting is enabled by following these steps:</span></span>
     - <span data-ttu-id="38a88-152">`System Preferences`를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-152">Open `System Preferences`</span></span>
     - <span data-ttu-id="38a88-153">`Sharing`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-153">Click on `Sharing`</span></span>
     - <span data-ttu-id="38a88-154">`Remote Login`을 확인합니다(`Remote Login: On`이어야 함).</span><span class="sxs-lookup"><span data-stu-id="38a88-154">Check `Remote Login` - Should say `Remote Login: On`</span></span>
     - <span data-ttu-id="38a88-155">적절한 사용자에게 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-155">Allow access to appropriate users</span></span>

2. <span data-ttu-id="38a88-156">`/private/etc/ssh/sshd_config` 위치에서 `sshd_config` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-156">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`</span></span>

   - <span data-ttu-id="38a88-157">선호하는 편집기를 사용합니다. 또는</span><span class="sxs-lookup"><span data-stu-id="38a88-157">Use your favorite editor or</span></span>

     ```bash
     sudo nano /private/etc/ssh/sshd_config
     ```

   - <span data-ttu-id="38a88-158">암호 인증이 활성화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-158">Make sure password authentication is enabled</span></span>

     ```
     PasswordAuthentication yes
     ```

   - <span data-ttu-id="38a88-159">PowerShell 하위 시스템 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-159">Add a PowerShell subsystem entry</span></span>

     ```
     Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
     ```

   - <span data-ttu-id="38a88-160">필요에 따라 키 인증을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-160">Optionally enable key authentication</span></span>

     ```
     PubkeyAuthentication yes
     ```

3. <span data-ttu-id="38a88-161">sshd 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-161">Restart the sshd service</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="38a88-162">인증</span><span class="sxs-lookup"><span data-stu-id="38a88-162">Authentication</span></span>

<span data-ttu-id="38a88-163">SSH를 통한 PowerShell 원격 기능은 SSH 클라이언트 및 SSH 서비스 간에 인증 교환을 필요로 하며 어떤 인증 체계도 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-163">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and does not implement any authentication schemes itself.</span></span> <span data-ttu-id="38a88-164">즉, 다단계 인증을 비롯한 모든 구성된 인증 체계는 SSH에서 처리하며 PowerShell과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-164">This means that any configured authentication schemes including multi-factor authentication is handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="38a88-165">예를 들어 보안 강화를 위해 일회용 암호뿐만 아니라 공개 키 인증이 필요하도록 SSH 서비스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-165">For example, you can configure the SSH service to require public key authentication as well as a one-time password for added security.</span></span> <span data-ttu-id="38a88-166">다단계 인증의 구성은 이 설명서의 범위를 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-166">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="38a88-167">PowerShell 원격 기능에서 다단계 인증을 사용하기 전에 올바르게 다단계 인증을 구성하고 PowerShell 외부에서 작동하는지 유효성 검사를 하는 방법은 SSH에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38a88-167">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="38a88-168">PowerShell 원격 기능 예제</span><span class="sxs-lookup"><span data-stu-id="38a88-168">PowerShell Remoting Example</span></span>

<span data-ttu-id="38a88-169">원격 기능을 테스트하는 가장 쉬운 방법은 단일 컴퓨터에서 사용해 보는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-169">The easiest way to test remoting is to try it on a single machine.</span></span> <span data-ttu-id="38a88-170">이 예제에서는 동일한 Linux 컴퓨터에 원격 세션을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-170">In this example, we create a remote session back to the same Linux machine.</span></span> <span data-ttu-id="38a88-171">SSH에서 호스트 컴퓨터를 확인하도록 요구하고 암호를 묻는 메시지를 표시하도록 대화형으로 PowerShell cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-171">We are using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="38a88-172">Windows 컴퓨터에서도 동일한 작업을 수행하여 원격 기능이 작동하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-172">You can do the same thing on a Windows machine to ensure remoting is working.</span></span> <span data-ttu-id="38a88-173">그런 다음, 호스트 이름을 변경하여 시스템 간을 원격으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-173">Then remote between machines by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```output
Handles  NPM(K)    PM(K)      WS(K)     CPU(s)     Id  SI ProcessName                    PSComputerName
-------  ------    -----      -----     ------     --  -- -----------                    --------------
      0       0        0         19       3.23  10635 635 powershell                     UbuntuVM1
      0       0        0         21       4.92  11033 017 powershell                     UbuntuVM1
      0       0        0         20       3.07  11076 076 powershell                     UbuntuVM1
```

```powershell
#
# Linux to Windows
#
Enter-PSSession -HostName WinVM1 -UserName PTestName
```

```output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```output
[WinVM2]: PS C:\Users\PSRemoteUser\Documents> $PSVersionTable

Name                           Value
----                           -----
PSEdition                      Core
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
SerializationVersion           1.1.0.1
BuildVersion                   3.0.0.0
CLRVersion
PSVersion                      6.0.0-alpha
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
GitCommitId                    v6.0.0-alpha.17


[WinVM2]: PS C:\Users\PSRemoteUser\Documents>
```

### <a name="known-issues"></a><span data-ttu-id="38a88-174">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="38a88-174">Known Issues</span></span>

<span data-ttu-id="38a88-175">sudo 명령은 Linux 컴퓨터에 대한 원격 세션에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="38a88-175">The sudo command doesn't work in remote session to Linux machine.</span></span>

## <a name="see-also"></a><span data-ttu-id="38a88-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="38a88-176">See Also</span></span>

[<span data-ttu-id="38a88-177">Windows용 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="38a88-177">PowerShell Core for Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="38a88-178">Linux용 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="38a88-178">PowerShell Core for Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="38a88-179">MacOS용 PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="38a88-179">PowerShell Core for MacOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="38a88-180">Windows용 OpenSSH</span><span class="sxs-lookup"><span data-stu-id="38a88-180">OpenSSH for Windows</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="38a88-181">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="38a88-181">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
