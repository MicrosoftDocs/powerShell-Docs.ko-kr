---
Download Help Link: https://go.microsoft.com/fwlink/?LinkId=393271
Help Version: 5.2.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 130582b1b9f18a8f6ada7c009c6d25a7dab75e46
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890715"
---
# <span data-ttu-id="60ba4-103">PowerShellGet 모듈</span><span class="sxs-lookup"><span data-stu-id="60ba4-103">PowerShellGet Module</span></span>

## <span data-ttu-id="60ba4-104">설명</span><span class="sxs-lookup"><span data-stu-id="60ba4-104">Description</span></span>

<span data-ttu-id="60ba4-105">PowerShellGet은 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 PowerShell 아티팩트를 검색, 설치, 업데이트 및 게시 하기 위한 명령이 포함 된 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-105">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="60ba4-106">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-106">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="60ba4-107">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-107">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="60ba4-108">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-108">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="60ba4-109">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60ba4-109">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="60ba4-110">PowerShellGet cmdlet</span><span class="sxs-lookup"><span data-stu-id="60ba4-110">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="60ba4-111">Find-Command</span><span class="sxs-lookup"><span data-stu-id="60ba4-111">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="60ba4-112">모듈에서 PowerShell 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-112">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="60ba4-113">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="60ba4-113">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="60ba4-114">DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-114">Finds a DSC resource.</span></span>

### [<span data-ttu-id="60ba4-115">Find-Module</span><span class="sxs-lookup"><span data-stu-id="60ba4-115">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="60ba4-116">리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-116">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="60ba4-117">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="60ba4-117">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="60ba4-118">모듈에서 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-118">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="60ba4-119">Find-Script</span><span class="sxs-lookup"><span data-stu-id="60ba4-119">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="60ba4-120">스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-120">Finds a script.</span></span>

### [<span data-ttu-id="60ba4-121">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="60ba4-121">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="60ba4-122">PowerShellGet에 의해 설치 된 컴퓨터의 모듈 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-122">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="60ba4-123">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="60ba4-123">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="60ba4-124">설치 된 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-124">Gets an installed script.</span></span>

### [<span data-ttu-id="60ba4-125">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="60ba4-125">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="60ba4-126">PowerShell 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-126">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="60ba4-127">Install-Module</span><span class="sxs-lookup"><span data-stu-id="60ba4-127">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="60ba4-128">리포지토리에서 하나 이상의 모듈을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-128">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="60ba4-129">Install-Script</span><span class="sxs-lookup"><span data-stu-id="60ba4-129">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="60ba4-130">스크립트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-130">Installs a script.</span></span>

### [<span data-ttu-id="60ba4-131">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="60ba4-131">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="60ba4-132">메타데이터를 사용하여 스크립트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-132">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="60ba4-133">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="60ba4-133">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="60ba4-134">로컬 컴퓨터에서 지정된 모듈을 온라인 갤러리에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-134">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="60ba4-135">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="60ba4-135">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="60ba4-136">스크립트를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-136">Publishes a script.</span></span>

### [<span data-ttu-id="60ba4-137">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="60ba4-137">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="60ba4-138">PowerShell 리포지토리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-138">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="60ba4-139">Save-Module</span><span class="sxs-lookup"><span data-stu-id="60ba4-139">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="60ba4-140">모듈 및 해당 종속성을 로컬 컴퓨터에 저장 하지만 모듈을 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-140">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="60ba4-141">Save-Script</span><span class="sxs-lookup"><span data-stu-id="60ba4-141">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="60ba4-142">스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-142">Saves a script.</span></span>

### [<span data-ttu-id="60ba4-143">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="60ba4-143">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="60ba4-144">등록 된 리포지토리에 대 한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-144">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="60ba4-145">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="60ba4-145">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="60ba4-146">스크립트에 대 한 주석 블록의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-146">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="60ba4-147">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="60ba4-147">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="60ba4-148">모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-148">Uninstalls a module.</span></span>

### [<span data-ttu-id="60ba4-149">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="60ba4-149">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="60ba4-150">스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-150">Uninstalls a script.</span></span>

### [<span data-ttu-id="60ba4-151">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="60ba4-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="60ba4-152">리포지토리 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-152">Unregisters a repository.</span></span>

### [<span data-ttu-id="60ba4-153">Update-Module</span><span class="sxs-lookup"><span data-stu-id="60ba4-153">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="60ba4-154">온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-154">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="60ba4-155">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="60ba4-155">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="60ba4-156">모듈 매니페스트 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-156">Updates a module manifest file.</span></span>

### [<span data-ttu-id="60ba4-157">Update-Script</span><span class="sxs-lookup"><span data-stu-id="60ba4-157">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="60ba4-158">스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-158">Updates a script.</span></span>

### [<span data-ttu-id="60ba4-159">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="60ba4-159">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="60ba4-160">스크립트에 대 한 정보를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="60ba4-160">Updates information for a script.</span></span>
