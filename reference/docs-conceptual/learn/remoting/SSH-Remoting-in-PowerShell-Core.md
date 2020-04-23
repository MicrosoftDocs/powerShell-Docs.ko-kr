---
title: SSH를 통한 PowerShell 원격
description: SSH를 사용하여 PowerShell Core에서 원격 작업
ms.date: 09/30/2019
ms.openlocfilehash: 0f2fb13010d62dec5b19b373a24a199bff22665d
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "73444368"
---
# <a name="powershell-remoting-over-ssh"></a><span data-ttu-id="c7d76-103">SSH를 통한 PowerShell 원격</span><span class="sxs-lookup"><span data-stu-id="c7d76-103">PowerShell remoting over SSH</span></span>

## <a name="overview"></a><span data-ttu-id="c7d76-104">개요</span><span class="sxs-lookup"><span data-stu-id="c7d76-104">Overview</span></span>

<span data-ttu-id="c7d76-105">PowerShell 원격 기능은 일반적으로 연결 협상 및 데이터 전송에 WinRM을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-105">PowerShell remoting normally uses WinRM for connection negotiation and data transport.</span></span> <span data-ttu-id="c7d76-106">이제 SSH를 Linux 및 Windows 플랫폼에서 사용할 수 있으며 진정한 다중 플랫폼 PowerShell 원격 기능이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-106">SSH is now available for Linux and Windows platforms and allows true multiplatform PowerShell remoting.</span></span>

<span data-ttu-id="c7d76-107">WinRM은 PowerShell 원격 세션을 위한 강력한 호스팅 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-107">WinRM provides a robust hosting model for PowerShell remote sessions.</span></span> <span data-ttu-id="c7d76-108">SSH 기반 원격 기능은 원격 엔드포인트 구성 및 JEA(Just Enough Administration)를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-108">SSH-based remoting doesn't currently support remote endpoint configuration and Just Enough Administration (JEA).</span></span>

<span data-ttu-id="c7d76-109">SSH 원격 기능을 사용하면 Windows 및 Linux 컴퓨터 간에 기본적인 PowerShell 세션 원격 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-109">SSH remoting lets you do basic PowerShell session remoting between Windows and Linux computers.</span></span> <span data-ttu-id="c7d76-110">SSH 원격 기능은 대상 컴퓨터에 SSH 하위 시스템으로 PowerShell 호스트 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-110">SSH remoting creates a PowerShell host process on the target computer as an SSH subsystem.</span></span> <span data-ttu-id="c7d76-111">앞으로는 엔드포인트 구성 및 JEA를 지원하기 위해 WinRM과 유사한 일반 호스팅 모델을 구현할 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-111">Eventually we'll implement a general hosting model, similar to WinRM, to support endpoint configuration and JEA.</span></span>

<span data-ttu-id="c7d76-112">`New-PSSession`, `Enter-PSSession` 및 `Invoke-Command` cmdlet에는 이제 이 새로운 원격 연결을 지원하기 위한 새로운 매개 변수가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-112">The `New-PSSession`, `Enter-PSSession`, and `Invoke-Command` cmdlets now have a new parameter set to support this new remoting connection.</span></span>

```
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

<span data-ttu-id="c7d76-113">원격 세션을 만들려면 `HostName` 매개 변수를 사용하여 대상 컴퓨터를 지정하고 `UserName`을 사용하여 사용자 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-113">To create a remote session, you specify the target computer with the `HostName` parameter and provide the user name with `UserName`.</span></span> <span data-ttu-id="c7d76-114">cmdlet을 대화형으로 실행하면 암호를 묻는 메시지가 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-114">When running the cmdlets interactively, you're prompted for a password.</span></span> <span data-ttu-id="c7d76-115">`KeyFilePath` 매개 변수와 함께 프라이빗 키 파일을 사용하여 SSH 키 인증을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-115">You can also, use SSH key authentication using a private key file with the `KeyFilePath` parameter.</span></span>

## <a name="general-setup-information"></a><span data-ttu-id="c7d76-116">일반적인 설치 정보</span><span class="sxs-lookup"><span data-stu-id="c7d76-116">General setup information</span></span>

<span data-ttu-id="c7d76-117">PowerShell 6 이상 및 SSH를 모든 컴퓨터에 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-117">PowerShell 6 or higher, and SSH must be installed on all computers.</span></span> <span data-ttu-id="c7d76-118">컴퓨터에서 들어오고 나가는 원격 작업을 수행할 수 있도록 SSH 클라이언트(`ssh.exe`) 및 서버(`sshd.exe`)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-118">Install both the SSH client (`ssh.exe`) and server (`sshd.exe`) so that you can remote to and from the computers.</span></span> <span data-ttu-id="c7d76-119">Windows용 OpenSSH는 이제 Windows 10 빌드 1809 및 Windows Server 2019에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-119">OpenSSH for Windows is now available in Windows 10 build 1809 and Windows Server 2019.</span></span> <span data-ttu-id="c7d76-120">자세한 내용은 [OpenSSH를 사용한 Windows 관리](/windows-server/administration/openssh/openssh_overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-120">For more information, see [Manage Windows with OpenSSH](/windows-server/administration/openssh/openssh_overview).</span></span> <span data-ttu-id="c7d76-121">Linux의 경우 sshd 서버 포함하여 플랫폼에 적합한 SSH를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-121">For Linux, install SSH, including sshd server, that's appropriate for your platform.</span></span> <span data-ttu-id="c7d76-122">또한 SSH 원격 기능을 가져오려면 GitHub에서 PowerShell을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-122">You also need to install PowerShell from GitHub to get the SSH remoting feature.</span></span> <span data-ttu-id="c7d76-123">SSH 서버는 원격 컴퓨터에 PowerShell 프로세스를 호스트하기 위해 SSH 하위 시스템을 만들도록 구성되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-123">The SSH server must be configured to create an SSH subsystem to host a PowerShell process on the remote computer.</span></span> <span data-ttu-id="c7d76-124">또한 **암호** 또는 **키 기반** 인증도 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-124">And, you must enable **password** or **key-based** authentication.</span></span>

## <a name="set-up-on-a-windows-computer"></a><span data-ttu-id="c7d76-125">Windows 컴퓨터에서 설정하기</span><span class="sxs-lookup"><span data-stu-id="c7d76-125">Set up on a Windows computer</span></span>

1. <span data-ttu-id="c7d76-126">최신 버전의 PowerShell을 설치하고 [Windows에서 PowerShell Core 설치하기](../../install/installing-powershell-core-on-windows.md#msi)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-126">Install the latest version of PowerShell, see [Installing PowerShell Core on Windows](../../install/installing-powershell-core-on-windows.md#msi).</span></span>

   <span data-ttu-id="c7d76-127">`New-PSSession` 매개 변수 집합을 나열하여 PowerShell에 SSH 원격 지원이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-127">You can confirm that PowerShell has SSH remoting support by listing the `New-PSSession` parameter sets.</span></span> <span data-ttu-id="c7d76-128">**SSH**로 시작하는 매개 변수 집합 이름이 있는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-128">You'll notice there are parameter set names that begin with **SSH**.</span></span> <span data-ttu-id="c7d76-129">이러한 매개 변수 집합은 **SSH** 매개 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-129">Those parameter sets include **SSH** parameters.</span></span>

   ```powershell
   (Get-Command New-PSSession).ParameterSets.Name
   ```

   ```Output
   Name
   ----
   SSHHost
   SSHHostHashParam
   ```

1. <span data-ttu-id="c7d76-130">최신 Win32 OpenSSH를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-130">Install the latest Win32 OpenSSH.</span></span> <span data-ttu-id="c7d76-131">설치 지침은 [OpenSSH 시작하기](/windows-server/administration/openssh/openssh_install_firstuse)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-131">For installation instructions, see [Getting started with OpenSSH](/windows-server/administration/openssh/openssh_install_firstuse).</span></span>

   > [!NOTE]
   > <span data-ttu-id="c7d76-132">PowerShell을 OpenSSH의 기본 셸로 설정하려면 [OpenSSH용 Windows 구성](/windows-server/administration/openssh/openssh_server_configuration)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-132">If you want to set PowerShell as the default shell for OpenSSH, see [Configuring Windows for OpenSSH](/windows-server/administration/openssh/openssh_server_configuration).</span></span>

1. <span data-ttu-id="c7d76-133">`sshd_config`에 있는 `$env:ProgramData\ssh` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-133">Edit the `sshd_config` file located at `$env:ProgramData\ssh`.</span></span>

   <span data-ttu-id="c7d76-134">암호 인증이 활성화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-134">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c7d76-135">원격 컴퓨터에서 PowerShell 프로세스를 호스트하는 SSH 하위 시스템을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-135">Create the SSH subsystem that hosts a PowerShell process on the remote computer:</span></span>

   ```
   Subsystem powershell c:/progra~1/powershell/6/pwsh.exe -sshs -NoLogo -NoProfile
   ```

   > [!NOTE]
   > <span data-ttu-id="c7d76-136">공백이 포함된 파일 경로에는 짧은 이름(8.3)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-136">You must use the 8.3 short name for any file paths that contain spaces.</span></span> <span data-ttu-id="c7d76-137">하위 시스템 실행 파일 경로의 작업에서 공백을 방지하는 Windows용 OpenSSH에 버그가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-137">There's a bug in OpenSSH for Windows that prevents spaces from working in subsystem executable paths.</span></span> <span data-ttu-id="c7d76-138">자세한 내용은 이 [GitHub 문제](https://github.com/PowerShell/Win32-OpenSSH/issues/784)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-138">For more information, see this [GitHub issue](https://github.com/PowerShell/Win32-OpenSSH/issues/784).</span></span>
   >
   > <span data-ttu-id="c7d76-139">Windows에서 `Program Files` 폴더의 짧은 이름(8.3)은 일반적으로 `Progra~1`입니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-139">The 8.3 short name for the `Program Files` folder in Windows is usually `Progra~1`.</span></span> <span data-ttu-id="c7d76-140">그러나 다음 명령을 사용하여 이를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-140">However, you can use the following command to make sure:</span></span>
   >
   > ```powershell
   > Get-CimInstance Win32_Directory -Filter 'Name="C:\\Program Files"' |
   >   Select-Object EightDotThreeFileName
   > ```
   >
   > ```Output
   > EightDotThreeFileName
   > ---------------------
   > c:\progra~1
   > ```

   <span data-ttu-id="c7d76-141">필요에 따라 키 인증을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-141">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

   <span data-ttu-id="c7d76-142">자세한 내용은 [OpenSSH 키 관리](/windows-server/administration/openssh/openssh_keymanagement)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-142">For more information, see [Managing OpenSSH Keys](/windows-server/administration/openssh/openssh_keymanagement).</span></span>

1. <span data-ttu-id="c7d76-143">**sshd** 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-143">Restart the **sshd** service.</span></span>

   ```powershell
   Restart-Service sshd
   ```

1. <span data-ttu-id="c7d76-144">Path 환경 변수에 OpenSSH가 설치된 경로를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-144">Add the path where OpenSSH is installed to your Path environment variable.</span></span> <span data-ttu-id="c7d76-145">`C:\Program Files\OpenSSH\`)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-145">For example, `C:\Program Files\OpenSSH\`.</span></span> <span data-ttu-id="c7d76-146">이 항목을 입력하면 `ssh.exe`를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-146">This entry allows for the `ssh.exe` to be found.</span></span>

## <a name="set-up-on-an-ubuntu-1604-linux-computer"></a><span data-ttu-id="c7d76-147">Ubuntu 16.04 Linux 컴퓨터에서 설정하기</span><span class="sxs-lookup"><span data-stu-id="c7d76-147">Set up on an Ubuntu 16.04 Linux computer</span></span>

1. <span data-ttu-id="c7d76-148">최신 버전의 PowerShell을 설치하는 방법에 대한 자세한 내용은 [Linux에서 PowerShell Core 설치하기](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-148">Install the latest version of PowerShell, see [Installing PowerShell Core on Linux](../../install/installing-powershell-core-on-linux.md#ubuntu-1604).</span></span>
1. <span data-ttu-id="c7d76-149">[Ubuntu OpenSSH 서버](https://help.ubuntu.com/lts/serverguide/openssh-server.html)를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-149">Install [Ubuntu OpenSSH Server](https://help.ubuntu.com/lts/serverguide/openssh-server.html).</span></span>

   ```bash
   sudo apt install openssh-client
   sudo apt install openssh-server
   ```

1. <span data-ttu-id="c7d76-150">`sshd_config` 위치에서 `/etc/ssh` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-150">Edit the `sshd_config` file at location `/etc/ssh`.</span></span>

   <span data-ttu-id="c7d76-151">암호 인증이 활성화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-151">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c7d76-152">PowerShell 하위 시스템 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-152">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="c7d76-153">필요에 따라 키 인증을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-153">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="c7d76-154">**sshd** 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-154">Restart the **sshd** service.</span></span>

   ```bash
   sudo service sshd restart
   ```

## <a name="set-up-on-a-macos-computer"></a><span data-ttu-id="c7d76-155">MacOS 컴퓨터에서 설정하기</span><span class="sxs-lookup"><span data-stu-id="c7d76-155">Set up on a macOS computer</span></span>

1. <span data-ttu-id="c7d76-156">최신 버전의 PowerShell을 설치하는 방법에 대한 자세한 내용은 [macOS에서 PowerShell Core 설치하기](../../install/installing-powershell-core-on-macos.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-156">Install the latest version of PowerShell, see [Installing PowerShell Core on macOS](../../install/installing-powershell-core-on-macos.md).</span></span>

   <span data-ttu-id="c7d76-157">다음 단계를 수행하여 SSH 원격 기능이 활성화되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-157">Make sure SSH Remoting is enabled by following these steps:</span></span>

   1. <span data-ttu-id="c7d76-158">`System Preferences`를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-158">Open `System Preferences`.</span></span>
   1. <span data-ttu-id="c7d76-159">`Sharing`을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-159">Click on `Sharing`.</span></span>
   1. <span data-ttu-id="c7d76-160">`Remote Login`을 선택하고 `Remote Login: On`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-160">Check `Remote Login` to set `Remote Login: On`.</span></span>
   1. <span data-ttu-id="c7d76-161">적절한 사용자에게 액세스를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-161">Allow access to the appropriate users.</span></span>

1. <span data-ttu-id="c7d76-162">`sshd_config` 위치에서 `/private/etc/ssh/sshd_config` 파일을 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-162">Edit the `sshd_config` file at location `/private/etc/ssh/sshd_config`.</span></span>

   <span data-ttu-id="c7d76-163">**nano**와 같은 텍스트 편집기를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-163">Use a text editor such as **nano**:</span></span>

   ```bash
   sudo nano /private/etc/ssh/sshd_config
   ```

   <span data-ttu-id="c7d76-164">암호 인증이 활성화되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-164">Make sure password authentication is enabled:</span></span>

   ```
   PasswordAuthentication yes
   ```

   <span data-ttu-id="c7d76-165">PowerShell 하위 시스템 항목을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-165">Add a PowerShell subsystem entry:</span></span>

   ```
   Subsystem powershell /usr/local/bin/pwsh -sshs -NoLogo -NoProfile
   ```

   <span data-ttu-id="c7d76-166">필요에 따라 키 인증을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-166">Optionally, enable key authentication:</span></span>

   ```
   PubkeyAuthentication yes
   ```

1. <span data-ttu-id="c7d76-167">**sshd** 서비스를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-167">Restart the **sshd** service.</span></span>

   ```bash
   sudo launchctl stop com.openssh.sshd
   sudo launchctl start com.openssh.sshd
   ```

## <a name="authentication"></a><span data-ttu-id="c7d76-168">인증</span><span class="sxs-lookup"><span data-stu-id="c7d76-168">Authentication</span></span>

<span data-ttu-id="c7d76-169">SSH를 통한 PowerShell 원격 기능은 SSH 클라이언트 및 SSH 서비스 간에 인증 교환을 필요로 하며 어떤 인증 체계도 구현하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-169">PowerShell remoting over SSH relies on the authentication exchange between the SSH client and SSH service and doesn't implement any authentication schemes itself.</span></span> <span data-ttu-id="c7d76-170">그 결과 다단계 인증을 비롯한 모든 구성된 인증 체계는 SSH에서 처리하며 PowerShell과는 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-170">The result is that any configured authentication schemes including multi-factor authentication are handled by SSH and independent of PowerShell.</span></span> <span data-ttu-id="c7d76-171">예를 들어 보안 강화를 위해 일회용 암호 및 공개 키 인증이 필요하도록 SSH 서비스를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-171">For example, you can configure the SSH service to require public key authentication and a one-time password for added security.</span></span> <span data-ttu-id="c7d76-172">다단계 인증의 구성은 이 설명서의 범위를 벗어납니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-172">Configuration of multi-factor authentication is outside the scope of this documentation.</span></span> <span data-ttu-id="c7d76-173">PowerShell 원격 기능에서 다단계 인증을 사용하기 전에 올바르게 다단계 인증을 구성하고 PowerShell 외부에서 작동하는지 유효성 검사를 하는 방법은 SSH에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7d76-173">Refer to documentation for SSH on how to correctly configure multi-factor authentication and validate it works outside of PowerShell before attempting to use it with PowerShell remoting.</span></span>

## <a name="powershell-remoting-example"></a><span data-ttu-id="c7d76-174">PowerShell 원격 기능 예제</span><span class="sxs-lookup"><span data-stu-id="c7d76-174">PowerShell remoting example</span></span>

<span data-ttu-id="c7d76-175">원격 기능을 테스트하는 가장 쉬운 방법은 단일 컴퓨터에서 사용해 보는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-175">The easiest way to test remoting is to try it on a single computer.</span></span> <span data-ttu-id="c7d76-176">이 예제에서는 동일한 Linux 컴퓨터에 원격 세션을 다시 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-176">In this example, we create a remote session back to the same Linux computer.</span></span> <span data-ttu-id="c7d76-177">SSH에서 호스트 컴퓨터를 확인하도록 요구하고 암호를 묻는 메시지를 표시하도록 대화형으로 PowerShell cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-177">We're using PowerShell cmdlets interactively so we see prompts from SSH asking to verify the host computer and prompting for a password.</span></span> <span data-ttu-id="c7d76-178">Windows 컴퓨터에서도 동일한 작업을 수행하여 원격 기능이 작동하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-178">You can do the same thing on a Windows computer to ensure remoting is working.</span></span> <span data-ttu-id="c7d76-179">그런 다음, 호스트 이름을 변경하여 컴퓨터 간을 원격으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-179">Then, remote between computers by changing the host name.</span></span>

```powershell
#
# Linux to Linux
#
$session = New-PSSession -HostName UbuntuVM1 -UserName TestUser
```

```Output
The authenticity of host 'UbuntuVM1 (9.129.17.107)' cannot be established.
ECDSA key fingerprint is SHA256:2kCbnhT2dUE6WCGgVJ8Hyfu1z2wE4lifaJXLO7QJy0Y.
Are you sure you want to continue connecting (yes/no)?
TestUser@UbuntuVM1s password:
```

```powershell
$session
```

```Output
 Id Name   ComputerName    ComputerType    State    ConfigurationName     Availability
 -- ----   ------------    ------------    -----    -----------------     ------------
  1 SSH1   UbuntuVM1       RemoteMachine   Opened   DefaultShell             Available
```

```powershell
Enter-PSSession $session
```

```Output
[UbuntuVM1]: PS /home/TestUser> uname -a
Linux TestUser-UbuntuVM1 4.2.0-42-generic 49~16.04.1-Ubuntu SMP Wed Jun 29 20:22:11 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

[UbuntuVM1]: PS /home/TestUser> Exit-PSSession
```

```powershell
Invoke-Command $session -ScriptBlock { Get-Process powershell }
```

```Output
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

```Output
PTestName@WinVM1s password:
```

```powershell
[WinVM1]: PS C:\Users\PTestName\Documents> cmd /c ver
```

```Output
Microsoft Windows [Version 10.0.10586]
```

```powershell
#
# Windows to Windows
#
C:\Users\PSUser\Documents>pwsh.exe
```

```Output
PowerShell
Copyright (c) Microsoft Corporation. All rights reserved.
```

```powershell
$session = New-PSSession -HostName WinVM2 -UserName PSRemoteUser
```

```Output
The authenticity of host 'WinVM2 (10.13.37.3)' can't be established.
ECDSA key fingerprint is SHA256:kSU6slAROyQVMEynVIXAdxSiZpwDBigpAF/TXjjWjmw.
Are you sure you want to continue connecting (yes/no)?
Warning: Permanently added 'WinVM2,10.13.37.3' (ECDSA) to the list of known hosts.
PSRemoteUser@WinVM2's password:
```

```powershell
$session
```

```Output
 Id Name            ComputerName    ComputerType    State         ConfigurationName     Availability
 -- ----            ------------    ------------    -----         -----------------     ------------
  1 SSH1            WinVM2          RemoteMachine   Opened        DefaultShell             Available
```

```powershell
Enter-PSSession -Session $session
```

```Output
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

### <a name="known-issues"></a><span data-ttu-id="c7d76-180">알려진 문제</span><span class="sxs-lookup"><span data-stu-id="c7d76-180">Known issues</span></span>

<span data-ttu-id="c7d76-181">**sudo** 명령은 Linux 컴퓨터에 대한 원격 세션에서 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d76-181">The **sudo** command doesn't work in a remote session to a Linux computer.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7d76-182">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7d76-182">See also</span></span>

[<span data-ttu-id="c7d76-183">Linux에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="c7d76-183">Installing PowerShell Core on Linux</span></span>](../../install/installing-powershell-core-on-linux.md#ubuntu-1604)

[<span data-ttu-id="c7d76-184">macOS에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="c7d76-184">Installing PowerShell Core on macOS</span></span>](../../install/installing-powershell-core-on-macos.md)

[<span data-ttu-id="c7d76-185">Windows에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="c7d76-185">Installing PowerShell Core on Windows</span></span>](../../install/installing-powershell-core-on-windows.md#msi)

[<span data-ttu-id="c7d76-186">OpenSSH를 사용한 Windows 관리</span><span class="sxs-lookup"><span data-stu-id="c7d76-186">Manage Windows with OpenSSH</span></span>](/windows-server/administration/openssh/openssh_overview)

[<span data-ttu-id="c7d76-187">OpenSSH 키 관리</span><span class="sxs-lookup"><span data-stu-id="c7d76-187">Managing OpenSSH Keys</span></span>](/windows-server/administration/openssh/openssh_keymanagement)

[<span data-ttu-id="c7d76-188">Ubuntu SSH</span><span class="sxs-lookup"><span data-stu-id="c7d76-188">Ubuntu SSH</span></span>](https://help.ubuntu.com/lts/serverguide/openssh-server.html)
