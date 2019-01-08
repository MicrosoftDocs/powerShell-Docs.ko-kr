---
title: Windows에서 PowerShell Core 설치
description: Windows에서 PowerShell Core를 설치하는 방법에 대한 정보
ms.date: 08/06/2018
ms.openlocfilehash: 7c109c7e1848af2349092c1e70fe4a7a25be54b8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53402887"
---
# <a name="installing-powershell-core-on-windows"></a><span data-ttu-id="d63ac-103">Windows에서 PowerShell Core 설치</span><span class="sxs-lookup"><span data-stu-id="d63ac-103">Installing PowerShell Core on Windows</span></span>

## <a name="msi"></a><span data-ttu-id="d63ac-104">MSI</span><span class="sxs-lookup"><span data-stu-id="d63ac-104">MSI</span></span>

<span data-ttu-id="d63ac-105">Windows 클라이언트 또는 Windows Server(Windows 7 SP1, Server 2008 R2 이상에서 작동)에 PowerShell을 설치하려면 GitHub [릴리스][] 페이지에서 MSI 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-105">To install PowerShell on a Windows client or Windows Server (works on Windows 7 SP1, Server 2008 R2, and later), download the MSI package from our GitHub [releases][] page.</span></span>

<span data-ttu-id="d63ac-106">MSI 파일은 다음과 같습니다. - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span><span class="sxs-lookup"><span data-stu-id="d63ac-106">The MSI file looks like this - `PowerShell-<version>-win-<os-arch>.msi`
<!-- TODO: should be updated to point to the Download Center as well --></span></span>

<span data-ttu-id="d63ac-107">다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-107">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="d63ac-108">설치하고 나면 시작 메뉴에 바로 가기가 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-108">There is a shortcut placed in the Start Menu upon installation.</span></span>

- <span data-ttu-id="d63ac-109">기본적으로 패키지는 `$env:ProgramFiles\PowerShell\<version>`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-109">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="d63ac-110">시작 메뉴 또는 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-110">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

### <a name="prerequisites"></a><span data-ttu-id="d63ac-111">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d63ac-111">Prerequisites</span></span>

<span data-ttu-id="d63ac-112">WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-112">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="d63ac-113">Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-113">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions prior to Windows 10.</span></span>
  <span data-ttu-id="d63ac-114">직접 다운로드 또는 Windows 업데이트를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-114">It is available via direct download or Windows Update.</span></span>
  <span data-ttu-id="d63ac-115">옵션 패키지를 포함하여 완전히 패치된 지원 시스템은 이미 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-115">Fully patched (including optional packages), supported systems will already have this installed.</span></span>
- <span data-ttu-id="d63ac-116">Windows 7 및 Windows Server 2008 R2에 WMF(Windows Management Framework) 4.0 이상을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-116">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="zip"></a><span data-ttu-id="d63ac-117">ZIP</span><span class="sxs-lookup"><span data-stu-id="d63ac-117">ZIP</span></span>

<span data-ttu-id="d63ac-118">고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-118">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span>
<span data-ttu-id="d63ac-119">ZIP 아카이브를 사용하면 MSI 패키지에서와 같이 전제 조건 확인을 받지 못하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-119">Be noted that when using the ZIP archive, you won't get the prerequisites check as in the MSI package.</span></span>
<span data-ttu-id="d63ac-120">따라서 Windows 10 이전의 Windows 버전에서 WSMan을 원격으로 실행하려면 [전제 조건](#prerequisites)이 충족되는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-120">So in order for remoting over WSMan to work properly on Windows versions prior to Windows 10, you need to make sure the [prerequisites](#prerequisites) are met.</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="d63ac-121">Windows IoT에 배포</span><span class="sxs-lookup"><span data-stu-id="d63ac-121">Deploying on Windows IoT</span></span>

<span data-ttu-id="d63ac-122">Windows IoT는 이미 Windows PowerShell과 함께 제공되며, Windows PowerShell을 사용하여 PowerShell Core 6을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-122">Windows IoT already comes with Windows PowerShell which we will use to deploy PowerShell Core 6.</span></span>

1. <span data-ttu-id="d63ac-123">대상 디바이스에 대한 `PSSession` 만들기</span><span class="sxs-lookup"><span data-stu-id="d63ac-123">Create `PSSession` to target device</span></span>

   ```powershell
   $s = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="d63ac-124">디바이스에 ZIP 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="d63ac-124">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-6.1.0-win-arm32.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="d63ac-125">디바이스에 연결하고 보관 확장</span><span class="sxs-lookup"><span data-stu-id="d63ac-125">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-6.1.0-win-arm32.zip
   ```

4. <span data-ttu-id="d63ac-126">PowerShell Core 6에 대한 원격 설정</span><span class="sxs-lookup"><span data-stu-id="d63ac-126">Setup remoting to PowerShell Core 6</span></span>

   ```powershell
   Set-Location .\PowerShell-6.1.0-win-arm32
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="d63ac-127">디바이스에서 PowerShell Core 6 엔드포인트에 연결</span><span class="sxs-lookup"><span data-stu-id="d63ac-127">Connect to PowerShell Core 6 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.6.1.0
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="d63ac-128">Nano 서버에 배포</span><span class="sxs-lookup"><span data-stu-id="d63ac-128">Deploying on Nano Server</span></span>

<span data-ttu-id="d63ac-129">이 지침은 PowerShell 버전이 이미 Nano 서버 이미지에서 실행 중이며 [Nano 서버 이미지 작성기](/windows-server/get-started/deploy-nano-server)에 의해 생성된 것으로 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-129">These instructions assume that a version of PowerShell is already running on the Nano Server image and that it has been generated by the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server).</span></span>
<span data-ttu-id="d63ac-130">Nano 서버는 “헤드리스” OS입니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-130">Nano Server is a "headless" OS.</span></span> <span data-ttu-id="d63ac-131">두 가지 방법으로 Core 이진 파일을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-131">Core binaries can be deploy using two different methods.</span></span>

1. <span data-ttu-id="d63ac-132">오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-132">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="d63ac-133">온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-133">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="d63ac-134">두 경우 모두 Windows 10 x64 ZIP 릴리스 패키지가 필요하며 “관리자” PowerShell 인스턴스 내에서 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-134">In both cases, you will need the Windows 10 x64 ZIP release package and will need to run the commands within an "Administrator" PowerShell instance.</span></span>

### <a name="offline-deployment-of-powershell-core"></a><span data-ttu-id="d63ac-135">PowerShell Core의 오프라인 배포</span><span class="sxs-lookup"><span data-stu-id="d63ac-135">Offline Deployment of PowerShell Core</span></span>

1. <span data-ttu-id="d63ac-136">자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-136">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="d63ac-137">이미지를 탑재 해제하고 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-137">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="d63ac-138">Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-138">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="d63ac-139">지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-139">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell-core"></a><span data-ttu-id="d63ac-140">PowerShell Core의 온라인 배포</span><span class="sxs-lookup"><span data-stu-id="d63ac-140">Online Deployment of PowerShell Core</span></span>

<span data-ttu-id="d63ac-141">다음 단계는 PowerShell Core를 실행 중인 Nano 서버 인스턴스에 배포하고 원격 엔드포인트를 구성하는 과정을 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-141">The following steps guide you through the deployment of PowerShell Core to a running instance of Nano Server and the configuration of its remote endpoint.</span></span>

- <span data-ttu-id="d63ac-142">Windows PowerShell의 받은 편지함 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="d63ac-142">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="d63ac-143">Nano 서버 인스턴스에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="d63ac-143">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="d63ac-144">세션 입력</span><span class="sxs-lookup"><span data-stu-id="d63ac-144">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="d63ac-145">ZIP 파일 추출</span><span class="sxs-lookup"><span data-stu-id="d63ac-145">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShellCore_<version>"
  ```

- <span data-ttu-id="d63ac-146">WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-146">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="d63ac-147">원격 엔드포인트 만들기 지침</span><span class="sxs-lookup"><span data-stu-id="d63ac-147">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="d63ac-148">PowerShell Core는 WSMan 및 SSH보다 PowerShell Remoting Protocol(PSRP)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-148">PowerShell Core supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span>
<span data-ttu-id="d63ac-149">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d63ac-149">For more information, see:</span></span>

- <span data-ttu-id="d63ac-150">[PowerShell Core에서의 SSH 원격 작업][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="d63ac-150">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="d63ac-151">[PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="d63ac-151">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="artifact-installation-instructions"></a><span data-ttu-id="d63ac-152">아티팩트 설치 지침</span><span class="sxs-lookup"><span data-stu-id="d63ac-152">Artifact Installation Instructions</span></span>

<span data-ttu-id="d63ac-153">[AppVeyor][]를 사용하여 모든 CI 빌드에 CoreCLR 비트가 있는 아카이브를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-153">We publish an archive with CoreCLR bits on every CI build with [AppVeyor][].</span></span>

<span data-ttu-id="d63ac-154">CoreCLR 아티팩트에서 PowerShell Core를 설치하려면</span><span class="sxs-lookup"><span data-stu-id="d63ac-154">To install PowerShell Core from the CoreCLR Artifact:</span></span>

1. <span data-ttu-id="d63ac-155">특정 빌드의 **아티팩트** 탭에서 ZIP 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="d63ac-155">Download ZIP package from **artifacts** tab of the particular build.</span></span>
2. <span data-ttu-id="d63ac-156">ZIP 파일 차단 해제: 파일 탐색기에서 마우스 오른쪽 단추 클릭 -> 속성 -> ‘차단 해제’ 상자 선택 -> 적용</span><span class="sxs-lookup"><span data-stu-id="d63ac-156">Unblock ZIP file: right-click in File Explorer -> Properties -> check 'Unblock' box -> apply</span></span>
3. <span data-ttu-id="d63ac-157">zip 파일을 `bin` 디렉터리로 추출</span><span class="sxs-lookup"><span data-stu-id="d63ac-157">Extract zip file to `bin` directory</span></span>
4. `./bin/pwsh.exe`

<!-- [download-center]: TODO -->

[릴리스]: https://github.com/PowerShell/PowerShell/releases
[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../core-powershell/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../core-powershell/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
