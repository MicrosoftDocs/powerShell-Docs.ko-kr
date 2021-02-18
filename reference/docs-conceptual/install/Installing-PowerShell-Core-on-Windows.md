---
title: Windows에 PowerShell 설치
description: Windows에서 PowerShell을 설치하는 방법에 대한 정보
ms.date: 02/02/2021
ms.openlocfilehash: 12dedfed8349d243d3f2988fd7cb69c4cfc276bb
ms.sourcegitcommit: 4f1c2fe700b8a0544c59e371eb7cfbc6d852b185
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100563264"
---
# <a name="installing-powershell-on-windows"></a><span data-ttu-id="45799-103">Windows에 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="45799-103">Installing PowerShell on Windows</span></span>

<span data-ttu-id="45799-104">Windows에서 여러 가지 방법으로 PowerShell을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-104">There are multiple ways to install PowerShell in Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="45799-105">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="45799-105">Prerequisites</span></span>

<span data-ttu-id="45799-106">PowerShell의 최신 릴리스는 Windows 7 SP1, Server 2008 R2 이상 버전에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-106">The latest release of PowerShell is supported on Windows 7 SP1, Server 2008 R2, and later versions.</span></span>

<span data-ttu-id="45799-107">WSMan을 통한 PowerShell 원격 기능을 사용하려면 다음 전제 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-107">To enable PowerShell remoting over WSMan, the following prerequisites need to be met:</span></span>

- <span data-ttu-id="45799-108">Windows 10 이전의 Windows 버전에서는 [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410)을 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-108">Install the [Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=50410) on Windows versions predating Windows 10.</span></span> <span data-ttu-id="45799-109">직접 다운로드 또는 Windows 업데이트를 통해 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-109">It's available via direct download or Windows Update.</span></span> <span data-ttu-id="45799-110">완전히 패치된 시스템에는 이 패키지가 이미 설치되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-110">Fully patched systems already have this package installed.</span></span>
- <span data-ttu-id="45799-111">Windows 7 및 Windows Server 2008 R2에서는 WMF(Windows Management Framework) 4.0 이상을 설치해야만 합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-111">Install the Windows Management Framework (WMF) 4.0 or newer on Windows 7 and Windows Server 2008 R2.</span></span> <span data-ttu-id="45799-112">WMF에 대한 자세한 내용은 [WMF 개요](/powershell/scripting/wmf/overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-112">For more information about WMF, see [WMF Overview](/powershell/scripting/wmf/overview).</span></span>

## <a name="download-the-installer-package"></a><span data-ttu-id="45799-113">설치 프로그램 패키지 다운로드</span><span class="sxs-lookup"><span data-stu-id="45799-113">Download the installer package</span></span>

<span data-ttu-id="45799-114">Windows에서 PowerShell을 설치하려면 GitHub에서 [최신][] 패키지 설치를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-114">To install PowerShell on Windows, download the [latest][] install package from GitHub.</span></span> <span data-ttu-id="45799-115">최신 [미리 보기][] 버전을 찾을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-115">You can also find the latest [preview][] version.</span></span> <span data-ttu-id="45799-116">릴리스 페이지의 **Assets** 섹션이 나올 때까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-116">Scroll down to the **Assets** section of the Release page.</span></span> <span data-ttu-id="45799-117">**Assets** 섹션이 축소되어 있으면 클릭하여 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-117">The **Assets** section may be collapsed, so you may need to click to expand it.</span></span>

## <a name="installing-the-msi-package"></a><span data-ttu-id="45799-118"><a id="msi" />MSI 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="45799-118"><a id="msi" />Installing the MSI package</span></span>

<span data-ttu-id="45799-119">MSI 파일은 `PowerShell-<version>-win-<os-arch>.msi`과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-119">The MSI file looks like `PowerShell-<version>-win-<os-arch>.msi`.</span></span> <span data-ttu-id="45799-120">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="45799-120">For example:</span></span>

- `PowerShell-7.1.2-win-x64.msi`
- `PowerShell-7.1.2-win-x86.msi`

<span data-ttu-id="45799-121">다운로드가 완료되면 설치 프로그램을 두 번 클릭하고 지시를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="45799-121">Once downloaded, double-click the installer and follow the prompts.</span></span>

<span data-ttu-id="45799-122">설치 관리자는 Windows 시작 메뉴에 바로 가기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45799-122">The installer creates a shortcut in the Windows Start Menu.</span></span>

- <span data-ttu-id="45799-123">기본적으로 패키지는 `$env:ProgramFiles\PowerShell\<version>`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-123">By default the package is installed to `$env:ProgramFiles\PowerShell\<version>`</span></span>
- <span data-ttu-id="45799-124">시작 메뉴 또는 `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`를 통해 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-124">You can launch PowerShell via the Start Menu or `$env:ProgramFiles\PowerShell\<version>\pwsh.exe`</span></span>

> [!NOTE]
> <span data-ttu-id="45799-125">PowerShell 7.1은 새 디렉터리에 설치되고 Windows PowerShell 5.1과 함께 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-125">PowerShell 7.1 installs to a new directory and runs side-by-side with Windows PowerShell 5.1.</span></span>
> <span data-ttu-id="45799-126">PowerShell 7.1은 PowerShell 6.x</span><span class="sxs-lookup"><span data-stu-id="45799-126">PowerShell 7.1 is an in-place upgrade that replaces PowerShell 6.x.</span></span> <span data-ttu-id="45799-127">또는 PowerShell 7.0을 대체하는 현재 위치 업그레이드입니다.</span><span class="sxs-lookup"><span data-stu-id="45799-127">or PowerShell 7.0.</span></span>
>
> - <span data-ttu-id="45799-128">PowerShell 7.1은 `$env:ProgramFiles\PowerShell\7`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-128">PowerShell 7.1 is installed to `$env:ProgramFiles\PowerShell\7`</span></span>
> - <span data-ttu-id="45799-129">`$env:ProgramFiles\PowerShell\7` 폴더가 `$env:PATH`에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-129">The `$env:ProgramFiles\PowerShell\7` folder is added to `$env:PATH`</span></span>
> - <span data-ttu-id="45799-130">`$env:ProgramFiles\PowerShell\6` 폴더가 삭제됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-130">The `$env:ProgramFiles\PowerShell\6` folder is deleted</span></span>
>
> <span data-ttu-id="45799-131">PowerShell 7.1을 다른 버전과 나란히 실행해야 하는 경우 [ZIP install](#zip) 메서드를 사용하여 다른 버전을 다른 폴더에 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-131">If you need to run PowerShell 7.1 side-by-side with other versions, use the [ZIP install](#zip) method to install the other version to a different folder.</span></span>

### <a name="administrative-install-from-the-command-line"></a><span data-ttu-id="45799-132">명령줄에서 관리 설치</span><span class="sxs-lookup"><span data-stu-id="45799-132">Administrative install from the command line</span></span>

<span data-ttu-id="45799-133">명령줄에서 MSI 패키지를 설치할 수 있으므로 관리자는 사용자 상호 작용 없이 패키지를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-133">MSI packages can be installed from the command line allowing administrators to deploy packages without user interaction.</span></span> <span data-ttu-id="45799-134">MSI 패키지에는 다음과 같은 설치 옵션 제어 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-134">The MSI package includes the following properties to control the installation options:</span></span>

- <span data-ttu-id="45799-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - 이 속성은 Windows 탐색기의 컨택스트 메뉴에 **Open PowerShell** 항목을 추가하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-135">**ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL** - This property controls the option for adding the **Open PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="45799-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** - 이 속성은 Windows 탐색기의 상황에 맞는 메뉴에 **PowerShell에서 실행** 항목을 추가하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-136">**ADD_FILE_CONTEXT_MENU_RUNPOWERSHELL** - This property controls the option for adding the **Run with PowerShell** item to the context menu in Windows Explorer.</span></span>
- <span data-ttu-id="45799-137">**ENABLE_PSREMOTING** - 이 속성은 설치 중 PowerShell 원격 조정을 사용하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-137">**ENABLE_PSREMOTING** - This property controls the option for enabling PowerShell remoting during installation.</span></span>
- <span data-ttu-id="45799-138">**REGISTER_MANIFEST** - 이 속성은 Windows 이벤트 로깅 매니페스트를 등록하는 옵션을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-138">**REGISTER_MANIFEST** - This property controls the option for registering the Windows Event Logging manifest.</span></span>

<span data-ttu-id="45799-139">다음 예제에서는 PowerShell을 자동으로 설치할 때 모든 설치 옵션을 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45799-139">The following example shows how to silently install PowerShell with all the install options enabled.</span></span>

```powershell
msiexec.exe /package PowerShell-7.1.2-win-x64.msi /quiet ADD_EXPLORER_CONTEXT_MENU_OPENPOWERSHELL=1 ENABLE_PSREMOTING=1 REGISTER_MANIFEST=1
```

<span data-ttu-id="45799-140">`Msiexec.exe`에 대한 명령줄 옵션의 전체 목록은 [명령줄 옵션](/windows/desktop/Msi/command-line-options)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-140">For a full list of command-line options for `Msiexec.exe`, see [Command line options](/windows/desktop/Msi/command-line-options).</span></span>

### <a name="registry-keys-created-during-installation"></a><span data-ttu-id="45799-141">설치 중 생성되는 레지스트리 키</span><span class="sxs-lookup"><span data-stu-id="45799-141">Registry keys created during installation</span></span>

<span data-ttu-id="45799-142">PowerShell 7.1부터 MSI 패키지는 PowerShell의 설치 위치 및 버전을 저장하는 레지스트리 키를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45799-142">Beginning in PowerShell 7.1, the MSI package creates registry keys that store the installation location and version of PowerShell.</span></span> <span data-ttu-id="45799-143">이러한 값은 `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-143">These values are located in `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\<GUID>`.</span></span> <span data-ttu-id="45799-144">`<GUID>`의 값은 각 빌드 형식(릴리스 또는 미리 보기), 주 버전 및 아키텍처에 대해 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-144">The value of `<GUID>` is unique for each build type (release or preview), major version, and architecture.</span></span>

|    <span data-ttu-id="45799-145">해제</span><span class="sxs-lookup"><span data-stu-id="45799-145">Release</span></span>    | <span data-ttu-id="45799-146">Architecture</span><span class="sxs-lookup"><span data-stu-id="45799-146">Architecture</span></span> |                                          <span data-ttu-id="45799-147">레지스트리 키</span><span class="sxs-lookup"><span data-stu-id="45799-147">Registry Key</span></span>                                           |
| ------------- | :----------: | ----------------------------------------------------------------------------------------------- |
| <span data-ttu-id="45799-148">7.1.x 릴리스</span><span class="sxs-lookup"><span data-stu-id="45799-148">7.1.x Release</span></span> |     <span data-ttu-id="45799-149">x86</span><span class="sxs-lookup"><span data-stu-id="45799-149">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\1d00683b-0f84-4db8-a64f-2f98ad42fe06` |
| <span data-ttu-id="45799-150">7.1.x 릴리스</span><span class="sxs-lookup"><span data-stu-id="45799-150">7.1.x Release</span></span> |     <span data-ttu-id="45799-151">X64</span><span class="sxs-lookup"><span data-stu-id="45799-151">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\31ab5147-9a97-4452-8443-d9709f0516e1` |
| <span data-ttu-id="45799-152">7.1.x 미리 보기</span><span class="sxs-lookup"><span data-stu-id="45799-152">7.1.x Preview</span></span> |     <span data-ttu-id="45799-153">x86</span><span class="sxs-lookup"><span data-stu-id="45799-153">x86</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\86abcfbd-1ccc-4a88-b8b2-0facfde29094` |
| <span data-ttu-id="45799-154">7.1.x 미리 보기</span><span class="sxs-lookup"><span data-stu-id="45799-154">7.1.x Preview</span></span> |     <span data-ttu-id="45799-155">X64</span><span class="sxs-lookup"><span data-stu-id="45799-155">x64</span></span>      | `HKLM\Software\Microsoft\PowerShellCore\InstalledVersions\39243d76-adaf-42b1-94fb-16ecf83237c8` |

<span data-ttu-id="45799-156">관리자 및 개발자가 PowerShell 경로를 찾는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-156">This can be used by administrators and developers to find the path to PowerShell.</span></span> <span data-ttu-id="45799-157">`<GUID>` 값은 모든 미리 보기 및 부 버전 릴리스에서 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-157">The `<GUID>` values will be the same for all preview and minor version releases.</span></span> <span data-ttu-id="45799-158">`<GUID>` 값은 주 릴리스마다 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-158">The `<GUID>` values are changed for each major release.</span></span>

## <a name="installing-the-zip-package"></a><span data-ttu-id="45799-159"><a id="zip" />ZIP 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="45799-159"><a id="zip" />Installing the ZIP package</span></span>

<span data-ttu-id="45799-160">고급 배포 시나리오를 지원하기 위해 PowerShell 이진 ZIP 아카이브가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-160">PowerShell binary ZIP archives are provided to enable advanced deployment scenarios.</span></span> <span data-ttu-id="45799-161">[릴리스][릴리스] 페이지에서 다음 ZIP 보관 파일 중 하나를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-161">Download one of the following ZIP archives from the [releases][releases] page.</span></span>

- <span data-ttu-id="45799-162">PowerShell-7.1.2-win-x64.zip</span><span class="sxs-lookup"><span data-stu-id="45799-162">PowerShell-7.1.2-win-x64.zip</span></span>
- <span data-ttu-id="45799-163">PowerShell-7.1.2-win-x86.zip</span><span class="sxs-lookup"><span data-stu-id="45799-163">PowerShell-7.1.2-win-x86.zip</span></span>
- <span data-ttu-id="45799-164">PowerShell-7.1.2-win-arm64.zip</span><span class="sxs-lookup"><span data-stu-id="45799-164">PowerShell-7.1.2-win-arm64.zip</span></span>
- <span data-ttu-id="45799-165">PowerShell-7.1.2-win-arm32.zip</span><span class="sxs-lookup"><span data-stu-id="45799-165">PowerShell-7.1.2-win-arm32.zip</span></span>

<span data-ttu-id="45799-166">파일을 다운로드하는 방법에 따라 `Unblock-File` cmdlet을 사용하여 파일의 차단을 해제해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-166">Depending on how you download the file you may need to unblock the file using the `Unblock-File` cmdlet.</span></span> <span data-ttu-id="45799-167">원하는 위치에 콘텐츠의 압축을 풀고, 여기서 `pwsh.exe`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-167">Unzip the contents to the location of your choice and run `pwsh.exe` from there.</span></span> <span data-ttu-id="45799-168">MSI 패키지 설치와 달리 ZIP 보관 파일 설치는 필수 조건을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-168">Unlike installing the MSI packages, installing the ZIP archive doesn't check for prerequisites.</span></span> <span data-ttu-id="45799-169">WSMan에서 원격 기능이 제대로 작동하도록 하려면 [필수 조건](#prerequisites)을 충족했는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-169">For remoting over WSMan to work properly, ensure that you've met the [prerequisites](#prerequisites).</span></span>

<span data-ttu-id="45799-170">이 방법을 사용하여 Microsoft Surface Pro X와 같은 컴퓨터에 ARM 기반 버전의 PowerShell을 설치합니다. 최상의 결과를 위해서는 `$env:ProgramFiles\PowerShell\7` 폴더에 PowerShell을 설치하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-170">Use this method to install the ARM-based version of PowerShell on computers like the Microsoft Surface Pro X. For best results, install PowerShell to the to `$env:ProgramFiles\PowerShell\7` folder.</span></span>

## <a name="deploying-on-windows-10-iot-enterprise"></a><span data-ttu-id="45799-171">Windows 10 IoT Enterprise에 배포</span><span class="sxs-lookup"><span data-stu-id="45799-171">Deploying on Windows 10 IoT Enterprise</span></span>

<span data-ttu-id="45799-172">Windows 10 IoT Enterprise는 PowerShell 7을 배포하는 데 사용할 수 있는 Windows PowerShell과 함께 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-172">Windows 10 IoT Enterprise comes with Windows PowerShell, which we can use to deploy PowerShell 7.</span></span>

1. <span data-ttu-id="45799-173">대상 디바이스에 대한 `PSSession` 만들기</span><span class="sxs-lookup"><span data-stu-id="45799-173">Create `PSSession` to target device</span></span>

   ```powershell
   Set-Item -Path WSMan:\localhost\Client\TrustedHosts <deviceip>
   $S = New-PSSession -ComputerName <deviceIp> -Credential Administrator
   ```

1. <span data-ttu-id="45799-174">디바이스에 ZIP 패키지 복사</span><span class="sxs-lookup"><span data-stu-id="45799-174">Copy the ZIP package to the device</span></span>

   ```powershell
   # change the destination to however you had partitioned it with sufficient
   # space for the zip and the unzipped contents
   # the path should be local to the device
   Copy-Item .\PowerShell-<version>-win-<os-arch>.zip -Destination u:\users\administrator\Downloads -ToSession $s
   ```

1. <span data-ttu-id="45799-175">디바이스에 연결하고 보관 확장</span><span class="sxs-lookup"><span data-stu-id="45799-175">Connect to the device and expand the archive</span></span>

   ```powershell
   Enter-PSSession $s
   Set-Location u:\users\administrator\downloads
   Expand-Archive .\PowerShell-<version>-win-<os-arch>.zip
   ```

1. <span data-ttu-id="45799-176">PowerShell 7에 대한 원격 설정</span><span class="sxs-lookup"><span data-stu-id="45799-176">Set up remoting to PowerShell 7</span></span>

   ```powershell
   Set-Location .\PowerShell-<version>-win-<os-arch>
   # Be sure to use the -PowerShellHome parameter otherwise it'll try to create a new
   # endpoint with Windows PowerShell 5.1
   .\Install-PowerShellRemoting.ps1 -PowerShellHome .
   # You'll get an error message and will be disconnected from the device because
   # it has to restart WinRM
   ```

1. <span data-ttu-id="45799-177">디바이스에서 PowerShell 7 엔드포인트에 연결</span><span class="sxs-lookup"><span data-stu-id="45799-177">Connect to PowerShell 7 endpoint on device</span></span>

   ```powershell
   # Be sure to use the -Configuration parameter. If you omit it, you will connect to Windows PowerShell 5.1
   Enter-PSSession -ComputerName <deviceIp> -Credential Administrator -Configuration powershell.<version>
   ```

## <a name="deploying-on-windows-10-iot-core"></a><span data-ttu-id="45799-178">Windows 10 IoT Core에 배포</span><span class="sxs-lookup"><span data-stu-id="45799-178">Deploying on Windows 10 IoT Core</span></span>

<span data-ttu-id="45799-179">Windows 10 IoT Core는 _IOT_POWERSHELL_ 기능을 포함할 때 Windows PowerShell을 추가하여 PowerShell 7을 배포하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-179">Windows 10 IoT Core adds Windows PowerShell when you include _IOT_POWERSHELL_ feature, which we can use to deploy PowerShell 7.</span></span> <span data-ttu-id="45799-180">IoT Core에 대해서도 위에서 정의한 Windows 10 IoT Enterprise 단계를 따를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-180">The steps defined above for Windows 10 IoT Enterprise can be followed for IoT Core as well.</span></span>

<span data-ttu-id="45799-181">배송 이미지에 최신 PowerShell을 추가하려면 [Import-PSCoreRelease][] 명령을 사용하여 패키지를 작업 영역에 포함하고 _OPENSRC_POWERSHELL_ 기능을 이미지에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-181">For adding the latest PowerShell in the shipping image, use [Import-PSCoreRelease][] command to include the package in the workarea and add _OPENSRC_POWERSHELL_ feature to your image.</span></span>

> [!NOTE]
> <span data-ttu-id="45799-182">ARM64 아키텍처의 경우 _IOT_POWERSHELL_ 을 포함할 때 Windows PowerShell이 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-182">For ARM64 architecture, Windows PowerShell is not added when you include _IOT_POWERSHELL_.</span></span> <span data-ttu-id="45799-183">따라서 zip 기반 설치가 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-183">So the zip based install will not work.</span></span> <span data-ttu-id="45799-184">`Import-PSCoreRelease` 명령을 사용하여 이미지에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-184">You will need to use `Import-PSCoreRelease` command to add it in the image.</span></span>

## <a name="deploying-on-nano-server"></a><span data-ttu-id="45799-185">Nano 서버에 배포</span><span class="sxs-lookup"><span data-stu-id="45799-185">Deploying on Nano Server</span></span>

<span data-ttu-id="45799-186">이 지침에서는 Nano 서버가 한 가지 버전의 PowerShell이 이미 실행 중인 "헤드리스" OS라고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-186">These instructions assume that the Nano Server is a "headless" OS that has a version of PowerShell is already running on it.</span></span> <span data-ttu-id="45799-187">자세한 내용은 [Nano 서버 이미지 작성기](/windows-server/get-started/deploy-nano-server) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-187">For more information, see the [Nano Server Image Builder](/windows-server/get-started/deploy-nano-server) documentation.</span></span>

<span data-ttu-id="45799-188">두 가지 방법으로 PowerShell 이진 파일을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-188">PowerShell binaries can be deployed using two different methods.</span></span>

1. <span data-ttu-id="45799-189">오프라인 - Nano 서버 VHD를 탑재하고 zip 파일의 내용을 탑재된 이미지 내의 선택한 위치에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="45799-189">Offline - Mount the Nano Server VHD and unzip the contents of the zip file to your chosen location within the mounted image.</span></span>
1. <span data-ttu-id="45799-190">온라인 - PowerShell 세션을 통해 zip 파일을 전송하고 선택한 위치에서 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="45799-190">Online - Transfer the zip file over a PowerShell Session and unzip it in your chosen location.</span></span>

<span data-ttu-id="45799-191">두 경우 모두 Windows 10 x64 ZIP 릴리스 패키지가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-191">In both cases, you need the Windows 10 x64 ZIP release package.</span></span> <span data-ttu-id="45799-192">PowerShell의 "관리자" 인스턴스 내에서 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-192">Run the commands within an "Administrator" instance of PowerShell.</span></span>

### <a name="offline-deployment-of-powershell"></a><span data-ttu-id="45799-193">PowerShell의 오프라인 배포</span><span class="sxs-lookup"><span data-stu-id="45799-193">Offline Deployment of PowerShell</span></span>

1. <span data-ttu-id="45799-194">자주 사용하는 zip 유틸리티로 패키지를 탑재된 Nano 서버 이미지 내의 디렉터리에 압축을 풉니다.</span><span class="sxs-lookup"><span data-stu-id="45799-194">Use your favorite zip utility to unzip the package to a directory within the mounted Nano Server image.</span></span>
1. <span data-ttu-id="45799-195">이미지를 탑재 해제하고 부팅합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-195">Unmount the image and boot it.</span></span>
1. <span data-ttu-id="45799-196">Windows PowerShell의 기본 제공 인스턴스에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-196">Connect to the built-in instance of Windows PowerShell.</span></span>
1. <span data-ttu-id="45799-197">지침에 따라 [“다른 인스턴스 기법”][]을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45799-197">Follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

### <a name="online-deployment-of-powershell"></a><span data-ttu-id="45799-198">PowerShell의 온라인 배포</span><span class="sxs-lookup"><span data-stu-id="45799-198">Online Deployment of PowerShell</span></span>

<span data-ttu-id="45799-199">다음 단계에 따라 PowerShell을 Nano 서버로 배포하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-199">Deploy PowerShell to Nano Server using the following steps.</span></span>

- <span data-ttu-id="45799-200">Windows PowerShell의 기본 제공 인스턴스에 연결</span><span class="sxs-lookup"><span data-stu-id="45799-200">Connect to the built-in instance of Windows PowerShell</span></span>

  ```powershell
  $session = New-PSSession -ComputerName <Nano Server IP address> -Credential <An Administrator account on the system>
  ```

- <span data-ttu-id="45799-201">Nano 서버 인스턴스에 파일 복사</span><span class="sxs-lookup"><span data-stu-id="45799-201">Copy the file to the Nano Server instance</span></span>

  ```powershell
  Copy-Item <local PS Core download location>\powershell-<version>-win-x64.zip c:\ -ToSession $session
  ```

- <span data-ttu-id="45799-202">세션 입력</span><span class="sxs-lookup"><span data-stu-id="45799-202">Enter the session</span></span>

  ```powershell
  Enter-PSSession $session
  ```

- <span data-ttu-id="45799-203">ZIP 파일 추출</span><span class="sxs-lookup"><span data-stu-id="45799-203">Extract the ZIP file</span></span>

  ```powershell
  # Insert the appropriate version.
  Expand-Archive -Path C:\powershell-<version>-win-x64.zip -DestinationPath "C:\PowerShell_<version>"
  ```

- <span data-ttu-id="45799-204">WSMan 기반 원격 작업이 필요한 경우 지침에 따라 [“다른 인스턴스 기법”][]을 사용하여 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="45799-204">If you want WSMan-based remoting, follow the instructions to create a remoting endpoint using the ["another instance technique"][].</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="45799-205">.NET 전역 도구로 설치</span><span class="sxs-lookup"><span data-stu-id="45799-205">Install as a .NET Global tool</span></span>

<span data-ttu-id="45799-206">[.NET Core SDK](/dotnet/core/sdk)가 이미 설치되어 있는 경우 PowerShell을 [.NET 전역 도구](/dotnet/core/tools/global-tools)로 쉽게 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-206">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="45799-207">dotnet 도구 설치 프로그램은 `$env:PATH` 환경 변수에 `$env:USERPROFILE\dotnet\tools`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-207">The dotnet tool installer adds `$env:USERPROFILE\dotnet\tools` to your `$env:PATH` environment variable.</span></span> <span data-ttu-id="45799-208">그러나 현재 실행 중인 셸에는 업데이트된 `$env:PATH`가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-208">However, the currently running shell doesn't have the updated `$env:PATH`.</span></span> <span data-ttu-id="45799-209">새 셸에서 `pwsh`를 입력하여 PowerShell을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-209">You can start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="install-powershell-via-winget"></a><span data-ttu-id="45799-210">Winget을 통해 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="45799-210">Install PowerShell via Winget</span></span>

<span data-ttu-id="45799-211">개발자는 `winget` 명령줄 도구를 사용하여 Windows 10 컴퓨터에서 애플리케이션을 검색, 설치, 업그레이드, 제거 및 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-211">The `winget` command-line tool enables developers to discover, install, upgrade, remove, and configure applications on Windows 10 computers.</span></span> <span data-ttu-id="45799-212">이 도구는 Windows 패키지 관리자 서비스에 대한 클라이언트 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="45799-212">This tool is the client interface to the Windows Package Manager service.</span></span>

> [!NOTE]
> <span data-ttu-id="45799-213">`winget` 도구는 현재 미리 보기입니다.</span><span class="sxs-lookup"><span data-stu-id="45799-213">The `winget` tool is currently a preview.</span></span> <span data-ttu-id="45799-214">계획된 기능을 모두 지금 사용할 수 있는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="45799-214">Not all planned functionality is available at this time.</span></span>
> <span data-ttu-id="45799-215">프로덕션 배포 시나리오에서는 이 방법을 사용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-215">You should not use this method in a production deployment scenario.</span></span> <span data-ttu-id="45799-216">시스템 요구 사항 및 설치 지침 목록은 [winget] 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-216">See the [winget] documentation for a list of system requirements and install instructions.</span></span>

<span data-ttu-id="45799-217">게시된 `winget` 패키지로 PowerShell을 설치하는 데 다음 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-217">The following commands can be used to install PowerShell using the published `winget` packages:</span></span>

1. <span data-ttu-id="45799-218">PowerShell 최신 버전 검색</span><span class="sxs-lookup"><span data-stu-id="45799-218">Search for the latest version of PowerShell</span></span>

   ```powershell
   winget search Microsoft.PowerShell
   ```

   ```Output
   Name               Id                           Version
   ---------------------------------------------------------------
   PowerShell         Microsoft.PowerShell         7.1.2
   PowerShell-Preview Microsoft.PowerShell-Preview 7.1.2-preview.5
   ```

1. <span data-ttu-id="45799-219">`--exact` 매개 변수를 사용하여 특정 버전의 PowerShell 설치</span><span class="sxs-lookup"><span data-stu-id="45799-219">Install a version of PowerShell using the `--exact` parameter</span></span>

   ```powershell
   winget install --name PowerShell --exact
   winget install --name PowerShell-Preview --exact
   ```

## <a name="installing-from-the-microsoft-store"></a><span data-ttu-id="45799-220"><a id="msix" />Microsoft Store에서 설치</span><span class="sxs-lookup"><span data-stu-id="45799-220"><a id="msix" />Installing from the Microsoft Store</span></span>

<span data-ttu-id="45799-221">PowerShell 7.1이 Microsoft Store에 게시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-221">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="45799-222">이 PowerShell 릴리스는 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 웹 사이트 또는 Windows의 Microsoft Store 애플리케이션에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-222">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="45799-223">Microsoft Store 패키지의 이점:</span><span class="sxs-lookup"><span data-stu-id="45799-223">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="45799-224">Windows 10에 바로 기본 제공되는 자동 업데이트</span><span class="sxs-lookup"><span data-stu-id="45799-224">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="45799-225">Intune 및 SCCM과 같은 기타 소프트웨어 배포 메커니즘과 통합</span><span class="sxs-lookup"><span data-stu-id="45799-225">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

<span data-ttu-id="45799-226">제한 사항:</span><span class="sxs-lookup"><span data-stu-id="45799-226">Limitations:</span></span>

<span data-ttu-id="45799-227">MSIX 패키지는 일부 파일 시스템 및 레지스트리 위치에 대한 액세스를 가상화하는 애플리케이션 샌드박스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-227">MSIX packages run in an application sandbox that virtualizes access to some filesystem and registry locations.</span></span>

- <span data-ttu-id="45799-228">HKEY_CURRENT_USER 아래의 모든 레지스트리 변경 내용은 개인, 사용자별, 앱별 위치에 쓸 때 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-228">All registry changes under HKEY_CURRENT_USER are copied on write to a private, per-user, per-app location.</span></span> <span data-ttu-id="45799-229">따라서 이러한 값은 다른 애플리케이션에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-229">Therefore, those values are not available to other applications.</span></span>
- <span data-ttu-id="45799-230">`$PSHOME`에 저장된 시스템 수준 구성 설정은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-230">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="45799-231">여기에는 WSMAN 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-231">This includes the WSMAN configuration.</span></span> <span data-ttu-id="45799-232">그러므로 원격 세션에서 PowerShell의 저장소 기반 설치에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-232">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="45799-233">사용자 수준 구성 및 SSH 원격 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-233">User-level configurations and SSH remoting are supported.</span></span>

<span data-ttu-id="45799-234">자세한 내용은 [Windows에서 패키지된 데스크톱 앱을 실행하는 방법 이해](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-234">For more information, see [Understanding how packaged desktop apps run on Windows](/windows/msix/desktop/desktop-to-uwp-behind-the-scenes).</span></span>

### <a name="using-the-msix-package"></a><span data-ttu-id="45799-235">MSIX 패키지 사용</span><span class="sxs-lookup"><span data-stu-id="45799-235">Using the MSIX package</span></span>

> [!NOTE]
> <span data-ttu-id="45799-236">PowerShell의 미리 보기 빌드에는 MSIX 패키지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-236">The preview builds of PowerShell include an MSIX package.</span></span> <span data-ttu-id="45799-237">MSIX 패키지는 공식적으로 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-237">The MSIX package is not officially supported.</span></span> <span data-ttu-id="45799-238">이 패키지는 미리 보기 기간 동안 테스트 목적으로 빌드된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="45799-238">The package is built for testing purposes during the preview period.</span></span>

<span data-ttu-id="45799-239">Windows 10 클라이언트에 MSIX 패키지를 수동으로 설치하려면 GitHub [릴리스][릴리스] 페이지에서 MSIX 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-239">To manually install the MSIX package on a Windows 10 client, download the MSIX package from our GitHub [releases][releases] page.</span></span> <span data-ttu-id="45799-240">설치하려는 릴리스의 **Assets** 섹션까지 아래로 스크롤합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-240">Scroll down to the **Assets** section of the Release you want to install.</span></span> <span data-ttu-id="45799-241">Assets 섹션이 축소되어 있으면 클릭해서 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-241">The Assets section may be collapsed, so you may need to click to expand it.</span></span>

<span data-ttu-id="45799-242">MSIX 파일은 다음과 같습니다. `PowerShell-<version>-win-<os-arch>.msix`</span><span class="sxs-lookup"><span data-stu-id="45799-242">The MSIX file looks like this - `PowerShell-<version>-win-<os-arch>.msix`</span></span>

<span data-ttu-id="45799-243">패키지를 설치하려면 `Add-AppxPackage` cmdlet을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-243">To install the package, you must use the `Add-AppxPackage` cmdlet.</span></span>

```powershell
Add-AppxPackage PowerShell-<version>-win-<os-arch>.msix
```

## <a name="how-to-create-a-remoting-endpoint"></a><span data-ttu-id="45799-244">원격 엔드포인트를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="45799-244">How to create a remoting endpoint</span></span>

<span data-ttu-id="45799-245">PowerShell은 WSMan 및 SSH와 함께 PowerShell Remoting Protocol(PSRP)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-245">PowerShell supports the PowerShell Remoting Protocol (PSRP) over both WSMan and SSH.</span></span> <span data-ttu-id="45799-246">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45799-246">For more information, see:</span></span>

- <span data-ttu-id="45799-247">[PowerShell Core에서의 SSH 원격 작업][ssh-remoting]</span><span class="sxs-lookup"><span data-stu-id="45799-247">[SSH Remoting in PowerShell Core][ssh-remoting]</span></span>
- <span data-ttu-id="45799-248">[PowerShell Core에서의 WSMan 원격 작업][wsman-remoting]</span><span class="sxs-lookup"><span data-stu-id="45799-248">[WSMan Remoting in PowerShell Core][wsman-remoting]</span></span>

## <a name="upgrading-an-existing-installation"></a><span data-ttu-id="45799-249">기존 설치 업그레이드</span><span class="sxs-lookup"><span data-stu-id="45799-249">Upgrading an existing installation</span></span>

<span data-ttu-id="45799-250">업그레이드할 때 최상의 결과를 위해서는 PowerShell을 처음 설치할 때 사용한 것과 동일한 설치 방법을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-250">For best results when upgrading, you should use the same install method you used when you first installed PowerShell.</span></span> <span data-ttu-id="45799-251">설치 방법마다 PowerShell이 설치되는 위치가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="45799-251">Each installation method installs PowerShell in a different location.</span></span> <span data-ttu-id="45799-252">PowerShell이 설치되었는지 확실하지 않은 경우 설치된 위치를 이 문서의 패키지 정보와 비교하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-252">If you are not sure how PowerShell was installed, you can compare the installed location with the package information in this article.</span></span> <span data-ttu-id="45799-253">MSI 패키지를 통해 설치한 경우 **프로그램 및 기능** 제어판에 해당 정보가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="45799-253">If you installed via the MSI package, that information appears in the **Programs and Features** Control Panel.</span></span>

## <a name="installation-support"></a><span data-ttu-id="45799-254">설치 지원</span><span class="sxs-lookup"><span data-stu-id="45799-254">Installation support</span></span>

<span data-ttu-id="45799-255">Microsoft는 이 문서의 설치 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="45799-255">Microsoft supports the installation methods in this document.</span></span> <span data-ttu-id="45799-256">다른 원본에서 사용 가능한 다른 설치 방법이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-256">There may be other methods of installation available from other sources.</span></span> <span data-ttu-id="45799-257">관련 도구 및 방법이 유효하더라도 Microsoft에서는 해당 방법을 지원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="45799-257">While those tools and methods may work, Microsoft cannot support those methods.</span></span>

<!-- link references -->

[미리 보기]: https://aka.ms/powershell-release?tag=preview
[preview]: https://aka.ms/powershell-release?tag=preview
[최신]: https://aka.ms/powershell-release?tag=stable
[latest]: https://aka.ms/powershell-release?tag=stable
[ssh-remoting]: ../learn/remoting/SSH-Remoting-in-PowerShell-Core.md
[wsman-remoting]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md
[AppVeyor]: https://ci.appveyor.com/project/PowerShell/powershell
[winget]: /windows/package-manager/winget
["다른 인스턴스 방법"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
["another instance technique"]: ../learn/remoting/WSMan-Remoting-in-PowerShell-Core.md#executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register
[Import-PSCoreRelease]: https://github.com/ms-iot/iot-adk-addonkit/blob/master/Tools/IoTCoreImaging/Docs/Import-PSCoreRelease.md#Import-PSCoreRelease
