---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: PowerShell 갤러리 시작
ms.openlocfilehash: c8beba3009e462ce52cdecd34fc0313d9234f289
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682998"
---
# <a name="getting-started-with-the-powershell-gallery"></a><span data-ttu-id="b27fc-103">PowerShell 갤러리 시작</span><span class="sxs-lookup"><span data-stu-id="b27fc-103">Getting Started with the PowerShell Gallery</span></span>

<span data-ttu-id="b27fc-104">PowerShell 갤러리는 스크립트, 모듈 및 DSC 리소스 다운로드를 활용 하 여 포함 된 패키지 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-104">The PowerShell Gallery is a package repository containing scripts, modules, and DSC resources you can download and leverage.</span></span> <span data-ttu-id="b27fc-105">Cmdlet을 사용 합니다 [PowerShellGet](/powershell/module/powershellget) 모듈을 PowerShell 갤러리에서 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-105">You use the cmdlets in the [PowerShellGet](/powershell/module/powershellget) module to install packages from the PowerShell Gallery.</span></span> <span data-ttu-id="b27fc-106">PowerShell 갤러리에서 항목을 다운로드하기 위해 로그인할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-106">You do not need to sign in to download items from the PowerShell Gallery.</span></span>

> [!NOTE]
> <span data-ttu-id="b27fc-107">패키지는 PowerShell 갤러리에서 직접 다운로드할 수 있지만 권장되는 방법이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-107">It is possible to download a package from the PowerShell Gallery directly, but this is not a recommended approach.</span></span>
> <span data-ttu-id="b27fc-108">자세한 내용은 [수동 패키지 다운로드](/powershell/gallery/how-to/working-with-packages/manual-download)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b27fc-108">For more details, see [Manual Package Download](/powershell/gallery/how-to/working-with-packages/manual-download).</span></span>

## <a name="discovering-packages-from-the-powershell-gallery"></a><span data-ttu-id="b27fc-109">PowerShell 갤러리에서 패키지 검색</span><span class="sxs-lookup"><span data-stu-id="b27fc-109">Discovering packages from the PowerShell Gallery</span></span>

<span data-ttu-id="b27fc-110">사용 하 여 PowerShell 갤러리에서 패키지를 찾을 수 있습니다 합니다 **검색** PowerShell 갤러리의 컨트롤 [홈페이지](https://www.powershellgallery.com), 또는 모듈 및 스크립트를 통해 이동 하 여에서 [패키지 페이지 ](https://www.powershellgallery.com/packages).</span><span class="sxs-lookup"><span data-stu-id="b27fc-110">You can find packages in the PowerShell Gallery by using the **Search** control on the PowerShell Gallery's [home page](https://www.powershellgallery.com), or by browsing through the Modules and Scripts from the [Packages page](https://www.powershellgallery.com/packages).</span></span> <span data-ttu-id="b27fc-111">PowerShell 갤러리에서 패키지를 실행 하 여 찾을 수도 있습니다는 [Find-module][]를 [Find-dscresource], 및 [Find-script][] 패키지 형식에 따라 cmdlet 사용 하 여 `-Repository PSGallery`입니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-111">You can also find packages from the PowerShell Gallery by running the [Find-Module][], [Find-DscResource], and [Find-Script][] cmdlets, depending on the package type, with `-Repository PSGallery`.</span></span>

<span data-ttu-id="b27fc-112">다음 매개 변수를 사용 하 여 갤러리의 결과 필터링 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-112">You can filter results from the Gallery by using the following parameters:</span></span>

- <span data-ttu-id="b27fc-113">이름</span><span class="sxs-lookup"><span data-stu-id="b27fc-113">Name</span></span>
- <span data-ttu-id="b27fc-114">AllVersions</span><span class="sxs-lookup"><span data-stu-id="b27fc-114">AllVersions</span></span>
- <span data-ttu-id="b27fc-115">MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b27fc-115">MinimumVersion</span></span>
- <span data-ttu-id="b27fc-116">RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b27fc-116">RequiredVersion</span></span>
- <span data-ttu-id="b27fc-117">태그</span><span class="sxs-lookup"><span data-stu-id="b27fc-117">Tag</span></span>
- <span data-ttu-id="b27fc-118">Includes</span><span class="sxs-lookup"><span data-stu-id="b27fc-118">Includes</span></span>
- <span data-ttu-id="b27fc-119">DscResource</span><span class="sxs-lookup"><span data-stu-id="b27fc-119">DscResource</span></span>
- <span data-ttu-id="b27fc-120">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="b27fc-120">RoleCapability</span></span>
- <span data-ttu-id="b27fc-121">명령</span><span class="sxs-lookup"><span data-stu-id="b27fc-121">Command</span></span>
- <span data-ttu-id="b27fc-122">필터</span><span class="sxs-lookup"><span data-stu-id="b27fc-122">Filter</span></span>

<span data-ttu-id="b27fc-123">갤러리에서 특정 DSC 리소스를 검색하는 데만 관심이 있는 경우 [Find-DscResource] cmdlet을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-123">If you're only interested in discovering specific DSC resources in the Gallery, you can run the [Find-DscResource] cmdlet.</span></span> <span data-ttu-id="b27fc-124">Find-DscResource는 갤러리에 포함된 DSC 리소스에 대한 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-124">Find-DscResource returns data on DSC resources contained in the Gallery.</span></span>
<span data-ttu-id="b27fc-125">DSC 리소스는 항상 모듈의 일부로 제공되기 때문에 여전히 [Install-Module][]을 실행하여 이러한 DSC 리소스를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-125">Because DSC resources are always delivered as part of a module, you still need to run [Install-Module][] to install those DSC resources.</span></span>

## <a name="learning-about-packages-in-the-powershell-gallery"></a><span data-ttu-id="b27fc-126">PowerShell 갤러리에 있는 패키지에 대해 알아보기</span><span class="sxs-lookup"><span data-stu-id="b27fc-126">Learning about packages in the PowerShell Gallery</span></span>

<span data-ttu-id="b27fc-127">관심 있는 패키지를 찾았으면 자세히 알아보는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-127">Once you've identified a package that you're interested in, you may want to learn more about it.</span></span> <span data-ttu-id="b27fc-128">이렇게 하려면 갤러리에서 해당 패키지의 페이지를 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-128">You can do this by examining that package's specific page on the Gallery.</span></span> <span data-ttu-id="b27fc-129">이 페이지에서 패키지와 함께 업로드된 메타데이터를 모두 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-129">On that page, you'll be able to see all of the metadata uploaded with the package.</span></span> <span data-ttu-id="b27fc-130">이 메타데이터는 패키지의 작성자가 제공하며 Microsoft에서 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-130">This metadata is provided by the package's author, and is not verified by Microsoft.</span></span> <span data-ttu-id="b27fc-131">패키지의 소유자는 패키지를 게시하는 데 사용되는 갤러리 계정에 강하게 연결되어 있으며 작성자 필드보다 더 신뢰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-131">The Owner of the package is strongly tied to the Gallery account used to publish the package, and is more trustworthy than the Author field.</span></span>

<span data-ttu-id="b27fc-132">좋은 의도로 게시되지 않은 것 같은 패키지를 발견할 경우 해당 패키지의 페이지에서 **신고하기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-132">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

<span data-ttu-id="b27fc-133">[Find-Module][] 또는 [Find-Script][]를 실행하는 경우 반환된 PSGetModuleInfo 개체에서 이 데이터를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-133">If you're running [Find-Module][] or [Find-Script][], you can view this data in the returned PSGetModuleInfo object.</span></span> <span data-ttu-id="b27fc-134">예를 들어 `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`를 실행하면</span><span class="sxs-lookup"><span data-stu-id="b27fc-134">For example, running `Find-Module -Name PSReadLine -Repository PSGallery |Get-Member`</span></span>
<span data-ttu-id="b27fc-135">갤러리에서 PSReadLine 모듈의 데이터가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-135">returns data on the PSReadLine module in the Gallery.</span></span>

## <a name="downloading-packages-from-the-powershell-gallery"></a><span data-ttu-id="b27fc-136">PowerShell 갤러리에서 패키지 다운로드</span><span class="sxs-lookup"><span data-stu-id="b27fc-136">Downloading packages from the PowerShell Gallery</span></span>

<span data-ttu-id="b27fc-137">PowerShell 갤러리에서 패키지를 다운로드하려면 다음 프로세스를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-137">We encourage the following process when downloading packages from the PowerShell Gallery:</span></span>

### <a name="inspect"></a><span data-ttu-id="b27fc-138">검사</span><span class="sxs-lookup"><span data-stu-id="b27fc-138">Inspect</span></span>

<span data-ttu-id="b27fc-139">검사를 위해 갤러리에서 패키지를 다운로드하려면 패키지 유형에 따라 [Save-Module][] 또는 [Save-Script][] cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-139">To download a package from the Gallery for inspection, run either the [Save-Module][] or [Save-Script][] cmdlet, depending on the package type.</span></span> <span data-ttu-id="b27fc-140">이렇게 하면 설치하지 않고 로컬에 패키지를 저장한 다음 패키지 내용을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-140">This lets you save the package locally without installing it, and inspect the package contents.</span></span> <span data-ttu-id="b27fc-141">저장된 패키지는 수동으로 삭제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-141">Remember to delete the saved package manually.</span></span>

<span data-ttu-id="b27fc-142">이러한 패키지 중 일부는 Microsoft에서 작성되었으며 다른 항목은 PowerShell 커뮤니티에서 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-142">Some of these packages are authored by Microsoft, and others are authored by the PowerShell community.</span></span>
<span data-ttu-id="b27fc-143">설치 전에 이 갤러리에 있는 패키지의 내용과 코드를 검토하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-143">Microsoft recommends that you review the contents and code of packages on this gallery prior to installation.</span></span>

<span data-ttu-id="b27fc-144">좋은 의도로 게시되지 않은 것 같은 패키지를 발견할 경우 해당 패키지의 페이지에서 **신고하기**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-144">If you discover a package that you feel is not published in good faith, click **Report Abuse** on that package's page.</span></span>

### <a name="install"></a><span data-ttu-id="b27fc-145">설치</span><span class="sxs-lookup"><span data-stu-id="b27fc-145">Install</span></span>

<span data-ttu-id="b27fc-146">사용을 위해 갤러리에서 패키지를 설치하려면 패키지 유형에 따라 [Install-Module][] 또는 [Install-Script][] cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-146">To install a package from the Gallery for use, run either the [Install-Module][] or [Install-Script][] cmdlet, depending on the package type.</span></span>

<span data-ttu-id="b27fc-147">[Install-Module][]은 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Modules`에 모듈을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-147">[Install-Module][] installs the module to `$env:ProgramFiles\WindowsPowerShell\Modules` by default.</span></span>
<span data-ttu-id="b27fc-148">이 경우 관리자 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-148">This requires an administrator account.</span></span> <span data-ttu-id="b27fc-149">`-Scope CurrentUser` 매개 변수를 추가하는 경우 모듈은 `$env:USERPROFILE\Documents\WindowsPowerShell\Modules`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-149">If you add the `-Scope CurrentUser` parameter, the module is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Modules` .</span></span>

<span data-ttu-id="b27fc-150">[Install-Script][]는 기본적으로 `$env:ProgramFiles\WindowsPowerShell\Scripts`에 스크립트를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-150">[Install-Script][] installs the script to `$env:ProgramFiles\WindowsPowerShell\Scripts` by default.</span></span>
<span data-ttu-id="b27fc-151">이 경우 관리자 계정이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-151">This requires an administrator account.</span></span> <span data-ttu-id="b27fc-152">`-Scope CurrentUser` 매개 변수를 추가하는 경우 스크립트는 `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts`에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-152">If you add the `-Scope CurrentUser` parameter, the script is installed to `$env:USERPROFILE\Documents\WindowsPowerShell\Scripts` .</span></span>

<span data-ttu-id="b27fc-153">기본적으로 [Install-Module][] 및 [Install-Script][]는 최신 버전의 패키지를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-153">By default, [Install-Module][] and [Install-Script][] installs the most current version of a package.</span></span>
<span data-ttu-id="b27fc-154">이전 버전의 패키지를 설치하려면 `-RequiredVersion` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-154">To install an older version of the package, add the `-RequiredVersion` parameter.</span></span>

### <a name="deploy"></a><span data-ttu-id="b27fc-155">배포 게스트 클러스터에</span><span class="sxs-lookup"><span data-stu-id="b27fc-155">Deploy</span></span>

<span data-ttu-id="b27fc-156">Azure Automation에 PowerShell 갤러리에서 패키지를 배포 하려면 **Azure Automation**, 클릭 **Azure Automation에 배포** 패키지 세부 정보 페이지입니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-156">To deploy a package from the PowerShell Gallery to Azure Automation, click **Azure Automation**, then click **Deploy to Azure Automation** on the package details page.</span></span> <span data-ttu-id="b27fc-157">Azure 계정 자격 증명을 사용 하 여 로그인 하는 Azure 관리 포털로 리디렉션됩니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-157">You are redirected to the Azure Management Portal where you sign in by using your Azure account credentials.</span></span> <span data-ttu-id="b27fc-158">참고는 종속성을 사용 하 여 패키지 배포 Azure Automation에 모든 종속성을 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-158">Note that deploying packages with dependencies deploys all the dependencies to Azure Automation.</span></span> <span data-ttu-id="b27fc-159">패키지 메타데이터에 **AzureAutomationNotSupported** 태그를 추가하면 Azure Automation에 배포 단추를 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-159">The 'Deploy to Azure Automation' button can be disabled by adding the **AzureAutomationNotSupported** tag to your package metadata.</span></span>

<span data-ttu-id="b27fc-160">Azure Automation에 대한 자세한 내용은 [Azure Automation](/azure/automation) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b27fc-160">To learn more about Azure Automation, see the [Azure Automation](/azure/automation) documentation.</span></span>

## <a name="updating-packages-from-the-powershell-gallery"></a><span data-ttu-id="b27fc-161">PowerShell 갤러리에서 패키지 업데이트</span><span class="sxs-lookup"><span data-stu-id="b27fc-161">Updating packages from the PowerShell Gallery</span></span>

<span data-ttu-id="b27fc-162">PowerShell 갤러리에서 설치된 패키지를 업데이트하려면 [Update-Module][] 또는 [Update-Script][] cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-162">To update packages installed from the PowerShell Gallery, run either the [Update-Module][] or [Update-Script][] cmdlet.</span></span> <span data-ttu-id="b27fc-163">[Update-module] 실행 하 여 설치 된 모든 모듈을 업데이트 하려고 추가 매개 변수 없이 실행 될 때 [Install-module][]합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-163">When run without any additional parameters, [Update-Module][] attempts to update all modules installed by running [Install-Module][].</span></span> <span data-ttu-id="b27fc-164">모듈을 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-164">To selectively update modules, add the `-Name` parameter.</span></span> 

<span data-ttu-id="b27fc-165">마찬가지로, 추가 매개 변수 없이 실행 될 때 [Update-script] 업데이트 하려고 모든 스크립트를 실행 하 여 설치 [Install-script][]합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-165">Similarly, when run without any additional parameters, [Update-Script][] also attempts to update all scripts installed by running [Install-Script][].</span></span> <span data-ttu-id="b27fc-166">스크립트를 선택적으로 업데이트하려면 `-Name` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-166">To selectively update scripts, add the `-Name` parameter.</span></span>

## <a name="list-packages-that-you-have-installed-from-the-powershell-gallery"></a><span data-ttu-id="b27fc-167">PowerShell 갤러리에서 설치한 패키지 나열</span><span class="sxs-lookup"><span data-stu-id="b27fc-167">List packages that you have installed from the PowerShell Gallery</span></span>

<span data-ttu-id="b27fc-168">PowerShell 갤러리에서 설치한 모듈을 찾으려면 [Get-InstalledModule][] cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-168">To find out which modules you have installed from the PowerShell Gallery, run the [Get-InstalledModule][] cmdlet.</span></span> <span data-ttu-id="b27fc-169">이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 모듈을 모두 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-169">This command lists all of the modules you have on your system that were installed directly from the PowerShell Gallery.</span></span>

<span data-ttu-id="b27fc-170">마찬가지로, PowerShell 갤러리에서 설치한 스크립트를 찾으려면 [Get-InstalledScript][] cmdlet을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-170">Similarly, to find out which scripts you have installed from the PowerShell Gallery, run the [Get-InstalledScript][] cmdlet.</span></span> <span data-ttu-id="b27fc-171">이 명령은 PowerShell 갤러리에서 직접 설치된 시스템의 스크립트를 모두 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="b27fc-171">This command lists all of the scripts you have on your system that were installed directly from the PowerShell Gallery.</span></span>

[Find-DscResource]: /powershell/module/powershellget/Find-DscResource
[Find-Module]: /powershell/module/powershellget/Find-Module
[Find-Script]: /powershell/module/powershellget/Find-Script
[Get-InstalledModule]: /powershell/module/powershellget/Get-InstalledModule
[Get-InstalledScript]: /powershell/module/powershellget/Get-InstalledScript
[Install-Module]: /powershell/module/powershellget/Install-Module
[Install-Script]: /powershell/module/powershellget/Install-Script
[Publish-Module]: /powershell/module/powershellget/Publish-Module
[Publish-Script]: /powershell/module/powershellget/Publish-Script
[Register-PSRepository]: /powershell/module/powershellget/Register-Repository
[Save-Module]: /powershell/module/powershellget/Save-Module
[Save-Script]: /powershell/module/powershellget/Save-Script
