---
title: Windows에 PowerShell 설치
description: Windows에서 PowerShell을 설치하는 방법에 대한 정보
ms.date: 08/06/2018
ms.openlocfilehash: ea5432725f4baea8c688fb8e67482910e2c3981e
ms.sourcegitcommit: b6cf10224eb9f32919a505cdffbe5968241c18a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2020
ms.locfileid: "80374889"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="25609-103">Windows에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="25609-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="25609-104">Windows에서 여러 가지 방법으로 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="25609-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="25609-105">Prerequisites</span></span>

<span data-ttu-id="25609-106">PowerShell의 최신 릴리스는 Windows 7 SP1, Server 2008 R2 이상 버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="25609-107">WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="25609-108">Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="25609-109">직접 다운로드 또는 Windows 업데이트를 통해 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="25609-110">완전히 패치된 시스템에는 이 패키지가 이미 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="25609-111">Windows 7 및 Windows Server 2008 R2에서는 WMF(Windows Management Framework) 4.0 이상을 설치해야만 합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="25609-112">WMF에 대한 자세한 내용은 [WMF 개요](/powershell/scripting/wmf/overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25609-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="25609-113">설치 프로그램 패키지 다운로드</span><span class="sxs-lookup"><span data-stu-id="25609-113">Download the installer package</span></span>

<span data-ttu-id="25609-114">Windows에서 PowerShell을 설치하려면 GitHub [릴리스][releases] 페이지에서 설치 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="25609-115">릴리스 페이지의 **Assets** 섹션이 나올 때까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="25609-116">**Assets** 섹션이 축소되어 있으면 클릭하여 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="25609-117"><a id="msi" />MSI 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="25609-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="25609-118">MSI 파일은 `PowerShell-<version>-win-<os-arch>.msi`과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="25609-119">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="25609-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="25609-120">다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="25609-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="25609-121">설치 관리자는 Windows 시작 메뉴에 바로 가기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25609-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="25609-122">기본적으로 패키지는 `$env:ProgramFiles\PowerShell\<version>`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="25609-123">시작 메뉴 또는 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="25609-124">PowerShell 7은 새 디렉터리에 설치되고 Windows PowerShell 5.1과 함께 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="25609-125">PowerShell Core 6.x의 경우 PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="25609-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="25609-126">PowerShell 7은 `$env:ProgramFiles\PowerShell\7`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="25609-127">`$env:ProgramFiles\PowerShell\7` 폴더가 `$env:PATH`에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="25609-128">`$env:ProgramFiles\PowerShell\6` 폴더가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="25609-129">PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [ZIP 설치](#zip) 방법을 사용하여 PowerShell 6을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="25609-130">명령줄에서 관리 설치</span><span class="sxs-lookup"><span data-stu-id="25609-130">Administrative install from the command line</span></span>

<span data-ttu-id="25609-131">명령줄에서 MSI 패키지를 설치할 수 있으므로 관리자는 사용자 상호 작용 없이 패키지를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="25609-132">MSI 패키지에는 다음과 같은 설치 옵션 제어 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="25609-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 이 속성은 Windows 탐색기의 컨택스트 메뉴에 **Open PowerShell** 항목을 추가하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="25609-134">**ENABLE_PSREMOTING** - 이 속성은 설치 중 PowerShell 원격 조정을 사용하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="25609-135">**REGISTER_MANIFEST** - 이 속성은 Windows 이벤트 로깅 매니페스트를 등록하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="25609-136">다음 예제에서는 PowerShell을 자동으로 설치할 때 모든 설치 옵션을 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25609-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="25609-137">`Msiexec.exe`에 대한 명령줄 옵션의 전체 목록은 [명령줄 옵션](/windows/desktop/Msi/command-line-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25609-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="25609-138"><a id="msix" />MSIX 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="25609-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="25609-139">Windows 10 클라이언트에 MSIX 패키지를 수동으로 설치하려면 GitHub [릴리스][releases] 페이지에서 MSIX 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="25609-140">설치하려는 릴리스의 **Assets** 섹션까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="25609-141">Assets 섹션이 축소되어 있으면 클릭해서 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="25609-142">MSIX 파일은 다음과 같습니다. `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="25609-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="25609-143">패키지를 설치하려면 `Add-AppxPackage` cmdlet을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="25609-144">MSIX 패키지는 아직 릴리스되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="25609-145">릴리스되면 Microsoft Store 및 GitHub [릴리스][releases] 페이지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="25609-146"><a id="zip" />ZIP 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="25609-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="25609-147">고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="25609-148">ZIP 보관 파일 설치는 MSI 패키지처럼 필수 조건을 확인하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="25609-149">WSMan에서 원격 기능이 제대로 작동하도록 하려면 [필수 조건](#prerequisites)을 충족했는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="25609-149">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-iot"></a><span data-ttu-id="25609-150">Windows IoT에 배포</span><span class="sxs-lookup"><span data-stu-id="25609-150">Deploying on Windows IoT</span></span>

<span data-ttu-id="25609-151">Windows IoT는 PowerShell 7을 배포하는 데 사용할 수 있는 Windows PowerShell과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="25609-151">Windows IoT comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="25609-152">대상 디바이스에 대한 `PSSession` 만들기</span><span class="sxs-lookup"><span data-stu-id="25609-152">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="25609-153">디바이스에 ZIP 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="25609-153">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="25609-154">디바이스에 연결하고 보관 확장</span><span class="sxs-lookup"><span data-stu-id="25609-154">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="25609-155">PowerShell 7에 대한 원격 설정</span><span class="sxs-lookup"><span data-stu-id="25609-155">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="25609-156">디바이스에서 PowerShell 7 엔드포인트에 연결</span><span class="sxs-lookup"><span data-stu-id="25609-156">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-nano-server"></a><span data-ttu-id="25609-157">Nano 서버에 배포</span><span class="sxs-lookup"><span data-stu-id="25609-157">Deploying on Nano Server</span></span>

<span data-ttu-id="25609-158">이 지침에서는 Nano 서버가 한 가지 버전의 PowerShell이 이미 실행 중인 "헤드리스" OS라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-158">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="25609-159">자세한 내용은 [Nano 서버 이미지 작성기](/windows-server/get-started/deploy-nano-server) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25609-159">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="25609-160">두 가지 방법으로 PowerShell 이진 파일을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-160">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="25609-161">오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="25609-161">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="25609-162">온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="25609-162">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="25609-163">두 경우 모두 Windows 10 x64 ZIP 릴리스 패키지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-163">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="25609-164">PowerShell의 "관리자" 인스턴스 내에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-164">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="25609-165">PowerShell의 오프라인 배포</span><span class="sxs-lookup"><span data-stu-id="25609-165">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="25609-166">자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="25609-166">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="25609-167">이미지를 탑재 해제하고 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-167">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="25609-168">Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-168">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="25609-169">지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25609-169">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="25609-170">PowerShell의 온라인 배포</span><span class="sxs-lookup"><span data-stu-id="25609-170">Online Deployment of PowerShell</span></span>

<span data-ttu-id="25609-171">다음 단계에 따라 PowerShell을 Nano 서버로 배포하세요.</span><span class="sxs-lookup"><span data-stu-id="25609-171">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="25609-172">Windows PowerShell의 받은 편지함 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="25609-172">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="25609-173">Nano 서버 인스턴스에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="25609-173">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="25609-174">세션 입력</span><span class="sxs-lookup"><span data-stu-id="25609-174">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="25609-175">ZIP 파일 추출</span><span class="sxs-lookup"><span data-stu-id="25609-175">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="25609-176">WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="25609-176">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="25609-177">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="25609-177">Install as a .NET Global tool</span></span>

<span data-ttu-id="25609-178">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-178">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="25609-179">dotnet 도구 설치 프로그램은 `$env:PATH` 환경 변수에 `$env:USERPROFILE\dotnet\tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-179">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="25609-180">그러나 현재 실행 중인 셸에는 업데이트된 `$env:PATH`가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-180">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="25609-181">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25609-181">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="25609-182">원격 엔드포인트를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="25609-182">How to create a remoting endpoint</span></span>

<span data-ttu-id="25609-183">PowerShell은 WSMan 및 SSH와 함께 PowerShell Remoting Protocol(PSRP)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="25609-183">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="25609-184">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25609-184">For more information, see:</span></span>

- <span data-ttu-id="25609-185">[PowerShell Core에서의 SSH 원격 작업][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="25609-185">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="25609-186">[PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="25609-186">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
