---
title: Windows에서 PowerShell Core 설치
description: Windows에서 PowerShell Core를 설치하는 방법에 대한 정보
ms.date: 08/06/2018
ms.openlocfilehash: c06eba06e376c3f795ab9c0fae9270cf6cf8f2ce
ms.sourcegitcommit: 36e4c79afda2ce11febd93951e143687245f0b50
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2019
ms.locfileid: "73444459"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="c8bbd-103">Windows에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="c8bbd-103">Installing PowerShell Core on Windows</span></span>

<span data-ttu-id="c8bbd-104">Windows에서 여러 가지 방법으로 PowerShell Core를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-104">There are multiple ways to install PowerShell Core in Windows.</span></span>

> [!TIP]
> <span data-ttu-id="c8bbd-105">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-105">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="prerequisites"></a><span data-ttu-id="c8bbd-106">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c8bbd-106">Prerequisites</span></span>

<span data-ttu-id="c8bbd-107">WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="c8bbd-108">Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span> <span data-ttu-id="c8bbd-109">직접 다운로드 또는 Windows 업데이트를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-109">It is available via direct download or Windows Update.</span></span> <span data-ttu-id="c8bbd-110">옵션 패키지를 포함하여 완전히 패치된 지원 시스템은 이미 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-110">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="c8bbd-111">Windows 7 및 Windows Server 2008 R2에 WMF(Windows Management Framework) 4.0 이상을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="c8bbd-112">WMF에 대한 자세한 내용은 [WMF 개요](/powershell/wmf/overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-112">For more information about WMF, see [WMF Overview](/powershell/wmf/overview).</span></span>

## <a name="a-idmsi-installing-the-msi-package"></a><span data-ttu-id="c8bbd-113"><a id="msi" />MSI 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="c8bbd-113"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="c8bbd-114">Windows 클라이언트 또는 Windows Server(Windows 7 SP1, Server 2008 R2 이상에서 작동)에 PowerShell을 설치하려면 GitHub [릴리스][releases] 페이지에서 MSI 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-114">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="c8bbd-115">설치하려는 릴리스의 **자산** 섹션으로 스크롤을 내립니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-115">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="c8bbd-116">자산 섹션이 축소되어 있을 수 있으니 확장을 클릭해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-116">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="c8bbd-117">MSI 파일은 다음과 같습니다. - `PowerShell-<version>-win-<os-arch>.msi`</span><span class="sxs-lookup"><span data-stu-id="c8bbd-117">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`</span></span>
<!-- TODO: should be updated to point to the Download Center as well -->

<span data-ttu-id="c8bbd-118">다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-118">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="c8bbd-119">설치 관리자는 Windows 시작 메뉴에 바로 가기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-119">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="c8bbd-120">기본적으로 패키지는 `$env:ProgramFiles\PowerShell\<version>`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-120">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="c8bbd-121">시작 메뉴 또는 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-121">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="c8bbd-122">명령줄에서 관리 설치</span><span class="sxs-lookup"><span data-stu-id="c8bbd-122">Administrative install from the command line</span></span>

<span data-ttu-id="c8bbd-123">MSI 패키지를 명령줄에서 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-123">MSI packages can be installed from the command line.</span></span> <span data-ttu-id="c8bbd-124">이렇게 하면 관리자가 사용자 개입 없이 패키지를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-124">This allows administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="c8bbd-125">PowerShell용 MSI 패키지에는 설치 옵션을 제어하는 다음 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-125">The MSI package for PowerShell includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="c8bbd-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 이 속성은 Windows 탐색기의 상황에 맞는 메뉴에 **Open PowerShell** 항목을 추가하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-126">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="c8bbd-127">**ENABLE_PSREMOTING** - 이 속성은 설치 중 PowerShell 원격을 사용하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-127">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="c8bbd-128">**REGISTER_MANIFEST** - 이 속성은 Windows 이벤트 로깅 매니페스트를 등록하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-128">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="c8bbd-129">다음 예제에서는 모든 설치 옵션을 사용하도록 설정하여 PowerShell Core를 자동으로 설치하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-129">The following examples shows how to silently install PowerShell Core with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-<version>-win-<os-arch>.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="c8bbd-130">Msiexec.exe에 대한 명령줄 옵션의 전체 목록은 [명령줄 옵션](/windows/desktop/Msi/command-line-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-130">For a full list of command line options for Msiexec.exe, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="a-idzip-installing-the-zip-package"></a><span data-ttu-id="c8bbd-131"><a id="zip" />ZIP 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="c8bbd-131"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="c8bbd-132">고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-132">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="c8bbd-133">ZIP 아카이브를 사용하면 MSI 패키지에서와 같이 전제 조건 확인을 받지 못하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-133">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span> <span data-ttu-id="c8bbd-134">WSMan에서 원격 기능이 제대로 작동하려면 [필수 조건](#prerequisites)이 충족되는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-134">For remoting over WSMan to work properly, ensure that you have met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="c8bbd-135">Windows IoT에 배포</span><span class="sxs-lookup"><span data-stu-id="c8bbd-135">Deploying on Windows IoT</span></span>

<span data-ttu-id="c8bbd-136">Windows IoT는 이미 Windows PowerShell과 함께 제공되며, Windows PowerShell을 사용하여 PowerShell Core 6을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-136">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="c8bbd-137">대상 디바이스에 대한 `PSSession` 만들기</span><span class="sxs-lookup"><span data-stu-id="c8bbd-137">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="c8bbd-138">디바이스에 ZIP 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="c8bbd-138">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="c8bbd-139">디바이스에 연결하고 보관 확장</span><span class="sxs-lookup"><span data-stu-id="c8bbd-139">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="c8bbd-140">PowerShell Core 6에 대한 원격 설정</span><span class="sxs-lookup"><span data-stu-id="c8bbd-140">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="c8bbd-141">디바이스에서 PowerShell Core 6 엔드포인트에 연결</span><span class="sxs-lookup"><span data-stu-id="c8bbd-141">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="c8bbd-142">Nano 서버에 배포</span><span class="sxs-lookup"><span data-stu-id="c8bbd-142">Deploying on Nano Server</span></span>

<span data-ttu-id="c8bbd-143">이 지침은 PowerShell 버전이 이미 Nano 서버 이미지에서 실행 중이며 [Nano 서버 이미지 작성기](/windows-server/get-started/deploy-nano-server)에 의해 생성된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-143">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="c8bbd-144">Nano 서버는 “헤드리스” OS입니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-144">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="c8bbd-145">두 가지 방법으로 Core 이진 파일을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-145">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="c8bbd-146">오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-146">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="c8bbd-147">온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-147">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="c8bbd-148">두 경우 모두 Windows 10 x64 ZIP 릴리스 패키지가 필요하며 “관리자” PowerShell 인스턴스 내에서 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-148">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="c8bbd-149">PowerShell Core의 오프라인 배포</span><span class="sxs-lookup"><span data-stu-id="c8bbd-149">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="c8bbd-150">자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-150">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="c8bbd-151">이미지를 탑재 해제하고 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-151">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="c8bbd-152">Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-152">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="c8bbd-153">지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-153">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="c8bbd-154">PowerShell Core의 온라인 배포</span><span class="sxs-lookup"><span data-stu-id="c8bbd-154">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="c8bbd-155">다음 단계는 PowerShell Core를 실행 중인 Nano 서버 인스턴스에 배포하고 원격 엔드포인트를 구성하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-155">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="c8bbd-156">Windows PowerShell의 받은 편지함 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="c8bbd-156">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="c8bbd-157">Nano 서버 인스턴스에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="c8bbd-157">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="c8bbd-158">세션 입력</span><span class="sxs-lookup"><span data-stu-id="c8bbd-158">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="c8bbd-159">ZIP 파일 추출</span><span class="sxs-lookup"><span data-stu-id="c8bbd-159">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="c8bbd-160">WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-160">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="c8bbd-161">원격 엔드포인트를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="c8bbd-161">How to create a remoting endpoint</span></span>

<span data-ttu-id="c8bbd-162">PowerShell Core는 WSMan 및 SSH보다 PowerShell Remoting Protocol(PSRP)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-162">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="c8bbd-163">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c8bbd-163">For more information, see:</span></span>

- <span data-ttu-id="c8bbd-164">[PowerShell Core에서의 SSH 원격 작업][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="c8bbd-164">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="c8bbd-165">[PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="c8bbd-165">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
