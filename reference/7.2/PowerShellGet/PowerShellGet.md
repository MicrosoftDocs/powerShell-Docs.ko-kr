---
Download Help Link: https://aka.ms/powershell72-help
Help Version: 7.2.0.0
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 0d4e5e26184558055a17f99bd5321aaf3f3789f7
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99602686"
---
# <span data-ttu-id="d4b88-102">PowerShellGet 모듈</span><span class="sxs-lookup"><span data-stu-id="d4b88-102">PowerShellGet Module</span></span>

## <span data-ttu-id="d4b88-103">설명</span><span class="sxs-lookup"><span data-stu-id="d4b88-103">Description</span></span>

<span data-ttu-id="d4b88-104">PowerShellGet은 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 PowerShell 아티팩트를 검색, 설치, 업데이트 및 게시 하기 위한 명령이 포함 된 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-104">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d4b88-105">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-105">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d4b88-106">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-106">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d4b88-107">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-107">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d4b88-108">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d4b88-108">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d4b88-109">PowerShellGet cmdlet</span><span class="sxs-lookup"><span data-stu-id="d4b88-109">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="d4b88-110">Find-Command</span><span class="sxs-lookup"><span data-stu-id="d4b88-110">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="d4b88-111">모듈에서 PowerShell 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-111">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="d4b88-112">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="d4b88-112">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="d4b88-113">DSC (필요한 상태 구성) 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-113">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="d4b88-114">Find-Module</span><span class="sxs-lookup"><span data-stu-id="d4b88-114">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="d4b88-115">리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-115">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="d4b88-116">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="d4b88-116">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="d4b88-117">모듈에서 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-117">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="d4b88-118">Find-Script</span><span class="sxs-lookup"><span data-stu-id="d4b88-118">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="d4b88-119">스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-119">Finds a script.</span></span>

### [<span data-ttu-id="d4b88-120">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="d4b88-120">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="d4b88-121">PowerShellGet에 의해 설치 된 컴퓨터의 모듈 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-121">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="d4b88-122">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="d4b88-122">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="d4b88-123">설치 된 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-123">Gets an installed script.</span></span>

### [<span data-ttu-id="d4b88-124">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d4b88-124">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="d4b88-125">PowerShell 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-125">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="d4b88-126">Install-Module</span><span class="sxs-lookup"><span data-stu-id="d4b88-126">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="d4b88-127">리포지토리에서 하나 이상의 모듈을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-127">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="d4b88-128">Install-Script</span><span class="sxs-lookup"><span data-stu-id="d4b88-128">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="d4b88-129">스크립트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-129">Installs a script.</span></span>

### [<span data-ttu-id="d4b88-130">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d4b88-130">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="d4b88-131">메타데이터를 사용하여 스크립트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-131">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="d4b88-132">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="d4b88-132">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="d4b88-133">로컬 컴퓨터에서 지정된 모듈을 온라인 갤러리에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-133">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="d4b88-134">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="d4b88-134">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="d4b88-135">스크립트를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-135">Publishes a script.</span></span>

### [<span data-ttu-id="d4b88-136">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d4b88-136">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="d4b88-137">PowerShell 리포지토리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-137">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="d4b88-138">Save-Module</span><span class="sxs-lookup"><span data-stu-id="d4b88-138">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="d4b88-139">모듈 및 해당 종속성을 로컬 컴퓨터에 저장 하지만 모듈을 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-139">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="d4b88-140">Save-Script</span><span class="sxs-lookup"><span data-stu-id="d4b88-140">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="d4b88-141">스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-141">Saves a script.</span></span>

### [<span data-ttu-id="d4b88-142">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d4b88-142">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="d4b88-143">등록 된 리포지토리에 대 한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-143">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="d4b88-144">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d4b88-144">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="d4b88-145">스크립트에 대 한 주석 블록의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-145">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="d4b88-146">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="d4b88-146">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="d4b88-147">모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-147">Uninstalls a module.</span></span>

### [<span data-ttu-id="d4b88-148">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="d4b88-148">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="d4b88-149">스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-149">Uninstalls a script.</span></span>

### [<span data-ttu-id="d4b88-150">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="d4b88-150">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="d4b88-151">리포지토리 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-151">Unregisters a repository.</span></span>

### [<span data-ttu-id="d4b88-152">Update-Module</span><span class="sxs-lookup"><span data-stu-id="d4b88-152">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="d4b88-153">온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-153">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="d4b88-154">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="d4b88-154">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="d4b88-155">모듈 매니페스트 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-155">Updates a module manifest file.</span></span>

### [<span data-ttu-id="d4b88-156">Update-Script</span><span class="sxs-lookup"><span data-stu-id="d4b88-156">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="d4b88-157">스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-157">Updates a script.</span></span>

### [<span data-ttu-id="d4b88-158">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="d4b88-158">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="d4b88-159">스크립트에 대 한 정보를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4b88-159">Updates information for a script.</span></span>
