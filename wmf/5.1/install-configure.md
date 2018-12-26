---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: keithb
title: WMF 5.1 설치 및 구성
ms.openlocfilehash: e5c7968744a442b4be9f1e43a45e91429a6d6165
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189349"
---
# <a name="install-and-configure-wmf-51"></a><span data-ttu-id="76ae7-103">WMF 5.1 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="76ae7-103">Install and Configure WMF 5.1</span></span> #


## <a name="download-and-install-the-wmf-51-package"></a><span data-ttu-id="76ae7-104">WMF 5.1 패키지 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="76ae7-104">Download and install the WMF 5.1 package</span></span>

<span data-ttu-id="76ae7-105">설치하려는 운영 체제 및 아키텍처에 맞는 WMF 5.1 패키지를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-105">Download the WMF 5.1 package for the operating system and architecture you wish to install it on:</span></span>

| <span data-ttu-id="76ae7-106">운영 체제</span><span class="sxs-lookup"><span data-stu-id="76ae7-106">Operating System</span></span>       | <span data-ttu-id="76ae7-107">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="76ae7-107">Prerequisites</span></span>           | <span data-ttu-id="76ae7-108">패키지 링크</span><span class="sxs-lookup"><span data-stu-id="76ae7-108">Package Links</span></span>                          |
|------------------------|-------------------------|----------------------------------------|
| <span data-ttu-id="76ae7-109">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="76ae7-109">Windows Server 2012 R2</span></span> |                         | <span data-ttu-id="76ae7-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-110">[Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span> |
| <span data-ttu-id="76ae7-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="76ae7-111">Windows Server 2012</span></span>    |                         | <span data-ttu-id="76ae7-112">[W2K12-KB3191565-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-112">[W2K12-KB3191565-x64.msu][]</span></span>            |
| <span data-ttu-id="76ae7-113">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="76ae7-113">Windows Server 2008 R2</span></span> | <span data-ttu-id="76ae7-114">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-114">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="76ae7-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-115">[Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span>    |
| <span data-ttu-id="76ae7-116">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="76ae7-116">Windows 8.1</span></span>            |                         | <span data-ttu-id="76ae7-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-117">**x64:** [Win8.1AndW2K12R2-KB3191564-x64.msu][]</span></span></br><span data-ttu-id="76ae7-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-118">**x86:** [Win8.1-KB3191564-x86.msu][]</span></span> |
| <span data-ttu-id="76ae7-119">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="76ae7-119">Windows 7 SP1</span></span>          | <span data-ttu-id="76ae7-120">[.NET Framework 4.5.2][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-120">[.NET Framework 4.5.2][]</span></span>| <span data-ttu-id="76ae7-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-121">**x64:** [Win7AndW2K8R2-KB3191566-x64.ZIP][]</span></span></br><span data-ttu-id="76ae7-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span><span class="sxs-lookup"><span data-stu-id="76ae7-122">**x86:** [Win7-KB3191566-x86.ZIP][]</span></span> |

[.NET Framework 4.5.2]: https://www.microsoft.com/download/details.aspx?id=42642
[W2K12-KB3191565-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839513
[Win7-KB3191566-x86.ZIP]: https://go.microsoft.com/fwlink/?linkid=839522
[Win7AndW2K8R2-KB3191566-x64.ZIP]: https://go.microsoft.com/fwlink/?linkid=839523
[Win8.1-KB3191564-x86.msu]: https://go.microsoft.com/fwlink/?linkid=839521
[Win8.1AndW2K12R2-KB3191564-x64.msu]: https://go.microsoft.com/fwlink/?linkid=839516

## <a name="install-wmf-51-for-windows-server-2008-r2-and-windows-7"></a><span data-ttu-id="76ae7-129">Windows Server 2008 R2 및 Windows 7의 경우 WMF 5.1 설치</span><span class="sxs-lookup"><span data-stu-id="76ae7-129">Install WMF 5.1 for Windows Server 2008 R2 and Windows 7</span></span>

> <span data-ttu-id="76ae7-130">**참고:** Windows Server 2008 R2 및 Windows 7에 대한 설치 지침이 변경되었으며 다른 패키지에 대한 지침과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-130">**Note:** Installation instructions for Windows Server 2008 R2 and Windows 7 have changed, and differ from the instructions for the other packages.</span></span> <span data-ttu-id="76ae7-131">Windows Server 2012 R2, Windows Server 2012 및 Windows 8.1에 대한 설치 지침은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-131">Installation instructions for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1 are below.</span></span>

<span data-ttu-id="76ae7-132">**Windows Server 2008 R2 및 Windows 7에 WMF 5.1 설치**</span><span class="sxs-lookup"><span data-stu-id="76ae7-132">**Installing WMF 5.1 on Windows Server 2008 R2 and Windows 7**</span></span>

1. <span data-ttu-id="76ae7-133">ZIP 파일을 다운로드한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-133">Navigate to the folder into which you downloaded the ZIP file.</span></span>

2. <span data-ttu-id="76ae7-134">ZIP 파일을 마우스 오른쪽 단추로 클릭하고 "압축 풀기..."를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-134">Right-click on the ZIP file, and select "Extract All...".</span></span> <span data-ttu-id="76ae7-135">Zip에는 2개의 파일 즉, MSU와 Install-WMF5.1.PS1 스크립트 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-135">The Zip contains 2 files: an MSU and the Install-WMF5.1.PS1 script file.</span></span>
<span data-ttu-id="76ae7-136">ZIP 파일의 압축을 푼 후 Windows 7 또는 Windows Server 2008 R2를 실행하는 모든 컴퓨터에 콘텐츠를 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-136">Once you have unpacked the ZIP file, you can copy the contents to any machine running Windows 7 or Windows Server 2008 R2.</span></span>

3. <span data-ttu-id="76ae7-137">ZIP 파일 내용을 추출한 후 관리자 권한으로 PowerShell을 연 다음 ZIP 파일의 내용이 포함된 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-137">After extracting the ZIP file contents, open PowerShell as administrator, then navigate to the folder containing the contents of the ZIP file.</span></span>

4. <span data-ttu-id="76ae7-138">해당 폴더의 Install-Wmf5.1.ps1 스크립트를 실행하고 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-138">Run the Install-Wmf5.1.ps1 script in that folder, and follow the instructions.</span></span> <span data-ttu-id="76ae7-139">이 스크립트는 로컬 컴퓨터에서 필수 조건을 확인하고 필수 조건을 충족한 경우 WMF 5.1을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-139">This script will check the prerequisites on the local machine, and install WMF 5.1 if the prerequisites have been met.</span></span> <span data-ttu-id="76ae7-140">필수 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-140">The prerequisites are listed below.</span></span>

<span data-ttu-id="76ae7-141">Install-WMF5.1.ps1은 다음 매개 변수를 사용하여 Windows Server 2008 R2 및 Windows 7에서 쉽게 설치를 자동화합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-141">Install-WMF5.1.ps1 takes the following parameters to ease automating the installation on Windows Server 2008 R2 and Windows 7:</span></span>

- <span data-ttu-id="76ae7-142">AcceptEula: 이 매개 변수가 포함된 경우 EULA에 자동으로 동의하게 되고 EULA가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-142">AcceptEula: When this parameter is included, the EULA is automatically accepted and will not be displayed.</span></span>
- <span data-ttu-id="76ae7-143">AllowRestart: 이 매개 변수는 AcceptEula가 지정된 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-143">AllowRestart: This parameter can only be used if AcceptEula is specified.</span></span> <span data-ttu-id="76ae7-144">이 매개 변수가 포함된 경우 WMF 5.1을 설치한 후 다시 시작해야 하면 설치가 완료된 직후 메시지가 표시되지 않고 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-144">If this parameter is included, and a restart is required after installing WMF 5.1, the restart will happen without prompting immediately after the installation is completed.</span></span>

<span data-ttu-id="76ae7-145">**Windows Server 2008 R2 SP1 및 Windows 7 SP1에 대한 WMF 5.1 필수 조건**</span><span class="sxs-lookup"><span data-stu-id="76ae7-145">**WMF 5.1 Prerequisites for Windows Server 2008 R2 SP1 and Windows 7 SP1**</span></span>

<span data-ttu-id="76ae7-146">Windows Server 2008 R2 SP1 또는 Windows 7 SP1에서 WMF 5.1을 설치하려면 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-146">Installation of WMF 5.1 on either Windows Server 2008 R2 SP1 or Windows 7 SP1, requires the following:</span></span>
- <span data-ttu-id="76ae7-147">최신 서비스 팩이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-147">Latest service pack must be installed.</span></span>
- <span data-ttu-id="76ae7-148">WMF 3.0이 설치되어 있어서는 **안 됩니다**.</span><span class="sxs-lookup"><span data-stu-id="76ae7-148">WMF 3.0 **must not** be installed.</span></span> <span data-ttu-id="76ae7-149">WMF 3.0 위에 WMF 5.1을 설치하면 PSModulePath가 손실되어 다른 애플리케이션이 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-149">Installing WMF 5.1 over WMF 3.0 will result in the loss of the PSModulePath, which can cause other applications to fail.</span></span> <span data-ttu-id="76ae7-150">WMF 5.1을 설치하기 전에 WMF 3.0을 제거하거나, PSModulePath를 저장한 다음 WMF 5.1 설치가 완료된 후에 수동으로 복원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-150">Before installing WMF 5.1, you must either un-install WMF 3.0, or save the PSModulePath and then restore it manually after WMF 5.1 installation is complete.</span></span>
- <span data-ttu-id="76ae7-151">WMF 5.1을 사용 하려면 적어도 [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642)합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-151">WMF 5.1 requires at least [.NET Framework 4.5.2](https://www.microsoft.com/en-ca/download/details.aspx?id=42642).</span></span>
<span data-ttu-id="76ae7-152">다운로드 위치에 있는 지침에 따라 Microsoft .NET Framework 4.5.2을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-152">You can install Microsoft .NET Framework 4.5.2 by following the instructions at the download location.</span></span>

<span data-ttu-id="76ae7-153">**WinRM 종속성**</span><span class="sxs-lookup"><span data-stu-id="76ae7-153">**WinRM Dependency**</span></span>

<span data-ttu-id="76ae7-154">Windows PowerShell DSC(원하는 상태 구성)는 WinRM에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-154">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span>
<span data-ttu-id="76ae7-155">WinRM은 Windows Server 2008 R2 및 Windows 7에서 기본적으로 사용하도록 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-155">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span>
<span data-ttu-id="76ae7-156">Windows PowerShell 관리자 권한 세션에서 `Set-WSManQuickConfig`를 실행하여 WinRM을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-156">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>


## <a name="install-wmf-51-for-windows-server-2012-r2-windows-server-2012-and-windows-81"></a><span data-ttu-id="76ae7-157">Windows Server 2012 R2, Windows Server 2012 및 Windows 8.1의 경우 WMF 5.1 설치</span><span class="sxs-lookup"><span data-stu-id="76ae7-157">Install WMF 5.1 for Windows Server 2012 R2, Windows Server 2012, and Windows 8.1</span></span>
<span data-ttu-id="76ae7-158">**Windows 탐색기(또는 Windows Server 2012 R2나 Windows 8.1의 파일 탐색기)에서 설치**</span><span class="sxs-lookup"><span data-stu-id="76ae7-158">**Install from Windows Explorer (or File Explorer in Windows Server 2012 R2 or Windows 8.1)**</span></span>

1. <span data-ttu-id="76ae7-159">MSU 파일을 다운로드한 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-159">Navigate to the folder into which you downloaded the MSU file.</span></span>
2. <span data-ttu-id="76ae7-160">MSU를 두 번 클릭하여 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-160">Double-click the MSU to run it.</span></span>

<span data-ttu-id="76ae7-161">**명령 프롬프트에서 설치**</span><span class="sxs-lookup"><span data-stu-id="76ae7-161">**Installing from the Command Prompt**</span></span>

1. <span data-ttu-id="76ae7-162">컴퓨터의 아키텍처에 맞는 올바른 패키지를 다운로드한 후 관리자 권한(관리자 권한으로 실행)으로 명령 프롬프트 창을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-162">After downloading the correct package for your computer's architecture, open a Command Prompt window with elevated user rights (Run as Administrator).</span></span> <span data-ttu-id="76ae7-163">Windows Server 2012 R2, Windows Server 2012 또는 Windows Server 2008 R2 SP1의 Server Core 설치 옵션에서는 명령 프롬프트가 기본적으로 관리자 권한으로 열립니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-163">On the Server Core installation options of Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2 SP1, Command Prompt opens with elevated user rights by default.</span></span>
2. <span data-ttu-id="76ae7-164">WMF 5.1 설치 패키지를 다운로드하거나 복사한 폴더로 디렉터리를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-164">Change directories to the folder into which you have downloaded or copied the WMF 5.1 installation package.</span></span>
3. <span data-ttu-id="76ae7-165">다음 명령 중 하나를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-165">Run one of the following commands:</span></span>
   - <span data-ttu-id="76ae7-166">Windows Server 2012 R2 또는 Windows 8.1 x64를 실행하는 컴퓨터에서 `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-166">On computers that are running Windows Server 2012 R2 or Windows 8.1 x64, run `Win8.1AndW2K12R2-KB3191564-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="76ae7-167">Windows Server 2012를 실행하는 컴퓨터에서 `W2K12-KB3191565-x64.msu /quiet`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-167">On computers that are running Windows Server 2012, run `W2K12-KB3191565-x64.msu /quiet`.</span></span>
   - <span data-ttu-id="76ae7-168">Windows 8.1 X86을 실행하는 컴퓨터에서 `Win8.1-KB3191564-x86.msu /quiet`를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-168">On computers that are running Windows 8.1 x86, run `Win8.1-KB3191564-x86.msu /quiet`.</span></span>

> [!NOTE]
> <span data-ttu-id="76ae7-169">WMF 5.1을 설치하려면 다시 부팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-169">Installing WMF 5.1 requires a reboot.</span></span> <span data-ttu-id="76ae7-170">`/quiet` 옵션을 사용하면 경고 없이 시스템이 다시 부팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-170">Using the `/quiet` option will reboot the system without warning.</span></span>
> <span data-ttu-id="76ae7-171">다시 부팅되지 않도록 하려면 `/norestart` 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="76ae7-171">Use the `/norestart` option to avoid rebooting.</span></span> <span data-ttu-id="76ae7-172">그러나 다시 부팅될 때까지 WMF 5.1이 설치되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="76ae7-172">However, WMF 5.1 will not be installed until you have rebooted.</span></span>
