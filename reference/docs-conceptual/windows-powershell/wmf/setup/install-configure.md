---
ms.date: 06/10/2020
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: WMF 5.1 설치 및 구성
ms.openlocfilehash: 9e0b4b6ed387b0a0d7fcf62a913677986d70de92
ms.sourcegitcommit: 4a283fe5419f47102e6c1de7060880a934842ee9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84671396"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="b4881-103">WMF 5.1 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="b4881-103">Install and Configure WMF 5.1</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4881-104">WMF 5.0은 WMF 5.1로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-104">WMF 5.0 is superseded by WMF 5.1.</span></span> <span data-ttu-id="b4881-105">WMF 5.0을 사용하는 사용자는 지원을 받기 위해 WMF 5.1로 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-105">Users with WMF 5.0 must upgrade to WMF 5.1 to receive support.</span></span>
> <span data-ttu-id="b4881-106">**WMF 5.1을 사용하려면 .NET Framework 4.5.2 이상이 필요합니다**.</span><span class="sxs-lookup"><span data-stu-id="b4881-106">**WMF 5.1 requires the .NET Framework 4.5.2** (or above).</span></span> <span data-ttu-id="b4881-107">.NET 4.5.2 이상이 설치되어 있지 않은 경우 설치는 되지만, 주요 기능이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-107">Installation will succeed, but key features will fail if .NET 4.5.2 (or above) is not installed.</span></span>

## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="b4881-108">WMF 5.1 패키지 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="b4881-108">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="b4881-109">설치하려는 운영 체제 및 아키텍처에 맞는 WMF 5.1 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-109">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="b4881-110">운영 체제</span><span class="sxs-lookup"><span data-stu-id="b4881-110">Operating System</span></span>       | <span data-ttu-id="b4881-111">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="b4881-111">Prerequisites</span></span>           | <span data-ttu-id="b4881-112">패키지 링크</span><span class="sxs-lookup"><span data-stu-id="b4881-112">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="b4881-113">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b4881-113">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="b4881-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b4881-114">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="b4881-115">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="b4881-115">Windows Server 2012</span></span>    |                         | <span data-ttu-id="b4881-116">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b4881-116">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="b4881-117">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b4881-117">Windows Server 2008 R2</span></span> | <span data-ttu-id="b4881-118">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="b4881-118">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="b4881-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b4881-119">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="b4881-120">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="b4881-120">Windows 8.1</span></span>            |                         | <span data-ttu-id="b4881-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="b4881-121">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="b4881-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="b4881-122">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="b4881-123">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="b4881-123">Windows 7 SP1</span></span>          | <span data-ttu-id="b4881-124">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="b4881-124">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="b4881-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b4881-125">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="b4881-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="b4881-126">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

- <span data-ttu-id="b4881-133">WMF 5.1 RTM을 설치하기 전에 먼저 WMF 5.1 Preview를 제거해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-133">WMF 5.1 Preview must be uninstalled before installing WMF 5.1 RTM.</span></span>
- <span data-ttu-id="b4881-134">WMF 5.1은 WMF 5.0 또는 WMF 4.0 위에 바로 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-134">WMF 5.1 may be installed directly over WMF 5.0 or WMF 4.0.</span></span>
- <span data-ttu-id="b4881-135">Windows 7 및 Windows Server 2008 R2에서는 WMF 5.1을 설치하기 전에 먼저 WMF 4.0을 설치할 **필요가 없습니다**.</span><span class="sxs-lookup"><span data-stu-id="b4881-135">It is **not required** to install WMF 4.0 prior to installing WMF 5.1 on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="b4881-136">Windows Server 2008 R2 및 Windows 7의 경우 WMF 5.1 설치</span><span class="sxs-lookup"><span data-stu-id="b4881-136">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> [!NOTE]
> <span data-ttu-id="b4881-137">Windows Server 2008 R2 및 Windows 7에 대한 설치 지침이 변경되었으며 다른 패키지에 대한 지침과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-137">Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="b4881-138">Windows Server 2012 R2, Windows Server 2012 및 Windows 8.1에 대한 설치 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-138">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

### <a name="wmf-51-prerequisites-for-windows-server-2008-r2-sp1-and-windows-7-sp1"></a><span data-ttu-id="b4881-139">Windows Server 2008 R2 SP1 및 Windows 7 SP1에 대한 WMF 5.1 필수 조건</span><span class="sxs-lookup"><span data-stu-id="b4881-139">WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1</span></span>

<span data-ttu-id="b4881-140">Windows Server 2008 R2 SP1 또는 Windows 7 SP1에서 WMF 5.1을 설치하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-140">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>

- <span data-ttu-id="b4881-141">최신 서비스 팩이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-141">Latest service pack must be installed.</span></span>
- <span data-ttu-id="b4881-142">WMF 3.0이 설치되어 있어서는 **안 됩니다**.</span><span class="sxs-lookup"><span data-stu-id="b4881-142">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="b4881-143">WMF 3.0 위에 WMF 5.1을 설치하면 **PSModulePath**(`$env:PSModulePath`)가 손실되어 다른 애플리케이션이 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-143">Installing WMF 5.1 over WMF 3.0 will result in the loss of the **PSModulePath** (`$env:PSModulePath`), which can cause other applications to fail.</span></span> <span data-ttu-id="b4881-144">WMF 5.1을 설치하기 전에 WMF 3.0을 제거하거나, **PSModulePath**를 저장한 다음 WMF 5.1 설치가 완료된 후에 수동으로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-144">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the **PSModulePath** and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="b4881-145">WMF 5.1을 사용 하려면 적어도 [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642)합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-145">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/download/details.aspx?id=42642).</span></span> <span data-ttu-id="b4881-146">다운로드 위치에 있는 지침에 따라 Microsoft .NET Framework 4.5.2을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-146">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

### <a name="installing-wmf-51-on-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="b4881-147">Windows Server 2008 R2 및 Windows 7에 WMF 5.1 설치</span><span class="sxs-lookup"><span data-stu-id="b4881-147">Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7</span></span>

1. <span data-ttu-id="b4881-148">ZIP 파일을 다운로드한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-148">Navigate to the folder into which you downloaded the ZIP file.</span></span>

1. <span data-ttu-id="b4881-149">ZIP 파일을 마우스 오른쪽 단추로 클릭하고 **압축 풀기...** 를 선택합니다. ZIP 파일에는 두 파일, 즉 MSU 및 `Install-WMF5.1.ps1` 스크립트 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-149">Right-click on the ZIP file, and select **Extract All...**. The ZIP file contains two files: an MSU and the `Install-WMF5.1.ps1` script file.</span></span> <span data-ttu-id="b4881-150">ZIP 파일의 압축을 푼 후 Windows 7 또는 Windows Server 2008 R2를 실행하는 모든 컴퓨터에 콘텐츠를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-150">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

1. <span data-ttu-id="b4881-151">ZIP 파일 내용을 추출한 후 관리자 권한으로 PowerShell을 연 다음 ZIP 파일의 내용이 포함된 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-151">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

1. <span data-ttu-id="b4881-152">해당 폴더의 `Install-WMF5.1.ps1` 스크립트를 실행하고 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-152">Run the `Install-WMF5.1.ps1` script in that folder, and follow the instructions.</span></span> <span data-ttu-id="b4881-153">이 스크립트는 로컬 컴퓨터에서 필수 조건을 확인하고 필수 조건을 충족한 경우 WMF 5.1을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-153">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="b4881-154">필수 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-154">The prerequisites are listed below.</span></span>

   <span data-ttu-id="b4881-155">`Install-WMF5.1.ps1`은 다음 매개 변수를 사용하여 Windows Server 2008 R2 및 Windows 7에서 쉽게 설치를 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-155">`Install-WMF5.1.ps1` takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

   - <span data-ttu-id="b4881-156">**AcceptEula**: 이 매개 변수가 포함된 경우 EULA에 자동으로 동의하게 되고 EULA가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-156">**AcceptEula**: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
   - <span data-ttu-id="b4881-157">**AllowRestart**: 이 매개 변수는 AcceptEula가 지정된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-157">**AllowRestart**: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="b4881-158">이 매개 변수가 포함된 경우 WMF 5.1을 설치한 후 다시 시작해야 하면 설치가 완료된 직후 메시지가 표시되지 않고 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-158">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="b4881-159">WinRM 종속성</span><span class="sxs-lookup"><span data-stu-id="b4881-159">WinRM Dependency</span></span>

<span data-ttu-id="b4881-160">Windows PowerShell DSC(원하는 상태 구성)는 WinRM에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-160">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="b4881-161">WinRM은 Windows Server 2008 R2 및 Windows 7에서 기본적으로 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-161">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="b4881-162">Windows PowerShell 관리자 권한 세션에서 `Set-WSManQuickConfig`를 실행하여 WinRM을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-162">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="b4881-163">Windows Server 2012 R2, Windows Server 2012 및 Windows 8.1의 경우 WMF 5.1 설치</span><span class="sxs-lookup"><span data-stu-id="b4881-163">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>

### <a name="install-from-windows-file-explorer"></a><span data-ttu-id="b4881-164">Windows 파일 탐색기에서 설치</span><span class="sxs-lookup"><span data-stu-id="b4881-164">Install from Windows File Explorer</span></span>

1. <span data-ttu-id="b4881-165">MSU 파일을 다운로드한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-165">Navigate to the folder into which you downloaded the MSU file.</span></span>
1. <span data-ttu-id="b4881-166">MSU를 두 번 클릭하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-166">Double-click the MSU to run it.</span></span>

### <a name="installing-from-the-command-prompt"></a><span data-ttu-id="b4881-167">명령 프롬프트에서 설치</span><span class="sxs-lookup"><span data-stu-id="b4881-167">Installing from the Command Prompt</span></span>

1. <span data-ttu-id="b4881-168">컴퓨터의 아키텍처에 맞는 올바른 패키지를 다운로드한 후 관리자 권한(관리자 권한으로 실행)으로 명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-168">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="b4881-169">Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1의 Server Core 설치 옵션에서는 명령 프롬프트가 기본적으로 관리자 권한으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-169">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
1. <span data-ttu-id="b4881-170">WMF 5.1 설치 패키지를 다운로드하거나 복사한 폴더로 디렉터리를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-170">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
1. <span data-ttu-id="b4881-171">다음 명령 중 하나를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-171">Run one of the following commands:</span></span>
   - <span data-ttu-id="b4881-172">Windows Server 2012 R2 또는 Windows 8.1 x64를 실행하는 컴퓨터에서 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-172">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet /norestart`.</span></span>
   - <span data-ttu-id="b4881-173">Windows Server 2012를 실행하는 컴퓨터에서 `W2K12-KB3191565-x64.msu /quiet /norestart`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-173">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet /norestart`.</span></span>
   - <span data-ttu-id="b4881-174">Windows 8.1 X86을 실행하는 컴퓨터에서 `Win8.1-KB3191564-x86.msu /quiet /norestart`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-174">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet /norestart`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b4881-175">WMF 5.1을 설치하려면 다시 부팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-175">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="b4881-176">`/quiet` 옵션만 사용하면 경고 없이 시스템이 다시 부팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-176">Using the `/quiet` option alone will reboot the system without warning.</span></span> <span data-ttu-id="b4881-177">다시 부팅되지 않도록 하려면 `/norestart` 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="b4881-177">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="b4881-178">그러나 다시 부팅될 때까지 WMF 5.1이 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4881-178">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
