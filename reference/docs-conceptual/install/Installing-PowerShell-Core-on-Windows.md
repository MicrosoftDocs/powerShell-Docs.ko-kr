---
title: Windows에 PowerShell 설치
description: Windows에서 PowerShell을 설치하는 방법에 대한 정보
ms.date: 08/06/2018
ms.openlocfilehash: a8543a91ad503364c5346a11c9c9d9f910547278
ms.sourcegitcommit: b80ce0396550d0896189d0205d6c4b4372ac2015
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141392"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="b1912-103">Windows에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="b1912-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="b1912-104">Windows에서 여러 가지 방법으로 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1912-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b1912-105">Prerequisites</span></span>

<span data-ttu-id="b1912-106">PowerShell의 최신 릴리스는 Windows 7 SP1, Server 2008 R2 이상 버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="b1912-107">WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="b1912-108">Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="b1912-109">직접 다운로드 또는 Windows 업데이트를 통해 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="b1912-110">완전히 패치된 시스템에는 이 패키지가 이미 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="b1912-111">Windows 7 및 Windows Server 2008 R2에서는 WMF(Windows Management Framework) 4.0 이상을 설치해야만 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="b1912-112">WMF에 대한 자세한 내용은 [WMF 개요](/powershell/scripting/wmf/overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1912-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="b1912-113">설치 프로그램 패키지 다운로드</span><span class="sxs-lookup"><span data-stu-id="b1912-113">Download the installer package</span></span>

<span data-ttu-id="b1912-114">Windows에서 PowerShell을 설치하려면 GitHub [릴리스][releases] 페이지에서 설치 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-114">To install PowerShell on Windows, download the install package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="b1912-115">릴리스 페이지의 **Assets** 섹션이 나올 때까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-115">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="b1912-116">**Assets** 섹션이 축소되어 있으면 클릭하여 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-116">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="b1912-117"><a id="msi" />MSI 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="b1912-117"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="b1912-118">MSI 파일은 `PowerShell-<version>-win-<os-arch>.msi`과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-118">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="b1912-119">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b1912-119">For example:</span></span>

- `PowerShell-7.0.0-win-x64.msi`
- `PowerShell-7.0.0-win-x86.msi`

<span data-ttu-id="b1912-120">다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-120">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="b1912-121">설치 관리자는 Windows 시작 메뉴에 바로 가기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-121">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="b1912-122">기본적으로 패키지는 `$env:ProgramFiles\PowerShell\<version>`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-122">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="b1912-123">시작 메뉴 또는 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-123">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="b1912-124">PowerShell 7은 새 디렉터리에 설치되고 Windows PowerShell 5.1과 함께 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-124">PowerShell 7 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span> <span data-ttu-id="b1912-125">PowerShell Core 6.x의 경우 PowerShell 7은 PowerShell Core 6.x를 제거하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-125">For PowerShell Core 6.x, PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> - <span data-ttu-id="b1912-126">PowerShell 7은 `$env:ProgramFiles\PowerShell\7`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-126">PowerShell 7 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="b1912-127">`$env:ProgramFiles\PowerShell\7` 폴더가 `$env:PATH`에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-127">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="b1912-128">`$env:ProgramFiles\PowerShell\6` 폴더가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-128">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="b1912-129">PowerShell 6과 PowerShell 7을 함께 실행해야 하는 경우 [ZIP 설치](#zip) 방법을 사용하여 PowerShell 6을 다시 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-129">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [ZIP install](#zip) method.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="b1912-130">명령줄에서 관리 설치</span><span class="sxs-lookup"><span data-stu-id="b1912-130">Administrative install from the command line</span></span>

<span data-ttu-id="b1912-131">명령줄에서 MSI 패키지를 설치할 수 있으므로 관리자는 사용자 상호 작용 없이 패키지를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-131">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="b1912-132">MSI 패키지에는 다음과 같은 설치 옵션 제어 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-132">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="b1912-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 이 속성은 Windows 탐색기의 컨택스트 메뉴에 **Open PowerShell** 항목을 추가하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-133">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="b1912-134">**ENABLE_PSREMOTING** - 이 속성은 설치 중 PowerShell 원격 조정을 사용하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-134">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="b1912-135">**REGISTER_MANIFEST** - 이 속성은 Windows 이벤트 로깅 매니페스트를 등록하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-135">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="b1912-136">다음 예제에서는 PowerShell을 자동으로 설치할 때 모든 설치 옵션을 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-136">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.0.0-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="b1912-137">`Msiexec.exe`에 대한 명령줄 옵션의 전체 목록은 [명령줄 옵션](/windows/desktop/Msi/command-line-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1912-137">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

## <a name="installing-the-msix-package"></a><span data-ttu-id="b1912-138"><a id="msix" />MSIX 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="b1912-138"><a id="msix" />Installing the MSIX package</span></span>

<span data-ttu-id="b1912-139">Windows 10 클라이언트에 MSIX 패키지를 수동으로 설치하려면 GitHub [릴리스][releases] 페이지에서 MSIX 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-139">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="b1912-140">설치하려는 릴리스의 **Assets** 섹션까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-140">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="b1912-141">Assets 섹션이 축소되어 있으면 클릭해서 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-141">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="b1912-142">MSIX 파일은 다음과 같습니다. `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="b1912-142">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="b1912-143">패키지를 설치하려면 `Add-AppxPackage` cmdlet을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-143">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

> [!NOTE]
> <span data-ttu-id="b1912-144">MSIX 패키지는 아직 릴리스되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-144">The MSIX package has not been released yet.</span></span> <span data-ttu-id="b1912-145">릴리스되면 Microsoft Store 및 GitHub [릴리스][releases] 페이지에서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-145">When released, the package will be available in the Microsoft Store and from the GitHub [releases][releases] page.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="b1912-146"><a id="zip" />ZIP 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="b1912-146"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="b1912-147">고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-147">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="b1912-148">ZIP 보관 파일 설치는 MSI 패키지처럼 필수 조건을 확인하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-148">Installing the ZIP archive doesn't check the prerequisites like the MSI packages do.</span></span> <span data-ttu-id="b1912-149">[releases][releases] 페이지에서 ZIP 보관 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-149">Download the ZIP archive from the [releases][releases] page.</span></span> <span data-ttu-id="b1912-150">파일을 다운로드하는 방법에 따라 `Unblock-File` cmdlet을 사용하여 파일의 차단을 해제해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-150">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="b1912-151">원하는 위치에 콘텐츠의 압축을 풀고, 여기서 `pwsh.exe`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-151">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="b1912-152">WSMan에서 원격 기능이 제대로 작동하도록 하려면 [필수 조건](#prerequisites)을 충족했는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b1912-152">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="b1912-153">Windows 10 IoT Enterprise에 배포</span><span class="sxs-lookup"><span data-stu-id="b1912-153">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="b1912-154">Windows 10 IoT Enterprise는 PowerShell 7을 배포하는 데 사용할 수 있는 Windows PowerShell과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-154">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="b1912-155">대상 디바이스에 대한 `PSSession` 만들기</span><span class="sxs-lookup"><span data-stu-id="b1912-155">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

2. <span data-ttu-id="b1912-156">디바이스에 ZIP 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="b1912-156">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

3. <span data-ttu-id="b1912-157">디바이스에 연결하고 보관 확장</span><span class="sxs-lookup"><span data-stu-id="b1912-157">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

4. <span data-ttu-id="b1912-158">PowerShell 7에 대한 원격 설정</span><span class="sxs-lookup"><span data-stu-id="b1912-158">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because it has to restart WinRM
   ```

5. <span data-ttu-id="b1912-159">디바이스에서 PowerShell 7 엔드포인트에 연결</span><span class="sxs-lookup"><span data-stu-id="b1912-159">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter.  If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```
## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="b1912-160">Windows 10 IoT Core에 배포</span><span class="sxs-lookup"><span data-stu-id="b1912-160">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="b1912-161">Windows 10 IoT Core는 *IOT_POWERSHELL* 기능을 포함할 때 Windows PowerShell을 추가하여 PowerShell 7을 배포하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-161">Windows 10 IoT Core adds Windows PowerShell when you include *IOT_POWERSHELL* feature, which we can use to deploy PowerShell 7.</span></span>
<span data-ttu-id="b1912-162">IoT Core에 대해서도 위에서 정의한 Windows 10 IoT Enterprise 단계를 따를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-162">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="b1912-163">배송 이미지에 최신 powershell을 추가하려면 [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) 명령을 사용하여 패키지를 워크 영역에 포함하고 *OPENSRC_POWERSHELL* 기능을 이미지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-163">For adding the latest powershell in the shipping image, use [Import-PSCoreRelease](https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease) command to include the package in the workarea and add *OPENSRC_POWERSHELL* feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="b1912-164">ARM64 아키텍처의 경우 *IOT_POWERSHELL*을 포함할 때 Windows Powershell이 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-164">For ARM64 architecture, Windows Powershell is not added when you include *IOT_POWERSHELL*.</span></span> <span data-ttu-id="b1912-165">따라서 zip 기반 설치가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-165">So the zip based install will not work.</span></span>
> <span data-ttu-id="b1912-166">Import-PSCoreRelease 명령을 사용하여 이미지에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-166">You will need to use Import-PSCoreRelease command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="b1912-167">Nano 서버에 배포</span><span class="sxs-lookup"><span data-stu-id="b1912-167">Deploying on Nano Server</span></span>

<span data-ttu-id="b1912-168">이 지침에서는 Nano 서버가 한 가지 버전의 PowerShell이 이미 실행 중인 "헤드리스" OS라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-168">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="b1912-169">자세한 내용은 [Nano 서버 이미지 작성기](/windows-server/get-started/deploy-nano-server) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1912-169">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="b1912-170">두 가지 방법으로 PowerShell 이진 파일을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-170">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="b1912-171">오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-171">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
2. <span data-ttu-id="b1912-172">온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-172">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="b1912-173">두 경우 모두 Windows 10 x64 ZIP 릴리스 패키지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-173">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="b1912-174">PowerShell의 "관리자" 인스턴스 내에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-174">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="b1912-175">PowerShell의 오프라인 배포</span><span class="sxs-lookup"><span data-stu-id="b1912-175">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="b1912-176">자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-176">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
2. <span data-ttu-id="b1912-177">이미지를 탑재 해제하고 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-177">Unmount the image and boot it.</span></span>
3. <span data-ttu-id="b1912-178">Windows PowerShell의 받은 편지함 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-178">Connect to the inbox instance of Windows PowerShell.</span></span>
4. <span data-ttu-id="b1912-179">지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-179">Follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/wsman-remoting-in-powershell-core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="b1912-180">PowerShell의 온라인 배포</span><span class="sxs-lookup"><span data-stu-id="b1912-180">Online Deployment of PowerShell</span></span>

<span data-ttu-id="b1912-181">다음 단계에 따라 PowerShell을 Nano 서버로 배포하세요.</span><span class="sxs-lookup"><span data-stu-id="b1912-181">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="b1912-182">Windows PowerShell의 받은 편지함 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="b1912-182">Connect to the inbox instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="b1912-183">Nano 서버 인스턴스에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="b1912-183">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="b1912-184">세션 입력</span><span class="sxs-lookup"><span data-stu-id="b1912-184">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="b1912-185">ZIP 파일 추출</span><span class="sxs-lookup"><span data-stu-id="b1912-185">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="b1912-186">WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [“다른 인스턴스 기법”](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register)을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-186">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"](../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register).</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="b1912-187">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="b1912-187">Install as a .NET Global tool</span></span>

<span data-ttu-id="b1912-188">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-188">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="b1912-189">dotnet 도구 설치 프로그램은 `$env:PATH` 환경 변수에 `$env:USERPROFILE\dotnet\tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-189">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="b1912-190">그러나 현재 실행 중인 셸에는 업데이트된 `$env:PATH`가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-190">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="b1912-191">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-191">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="b1912-192">원격 엔드포인트를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="b1912-192">How to create a remoting endpoint</span></span>

<span data-ttu-id="b1912-193">PowerShell은 WSMan 및 SSH와 함께 PowerShell Remoting Protocol(PSRP)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b1912-193">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="b1912-194">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b1912-194">For more information, see:</span></span>

- <span data-ttu-id="b1912-195">[PowerShell Core에서의 SSH 원격 작업][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="b1912-195">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="b1912-196">[PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="b1912-196">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

<!-- [download-center]: TODO -->

[releases]: https://github.com/PowerShell/PowerShell/releases
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
