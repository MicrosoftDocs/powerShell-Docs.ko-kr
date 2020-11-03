---
Download Help Link: https://aka.ms/powershell71-help
Help Version: 7.1.0.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: 87d4b62b866e0b477668ab4f4a5ec426d9a0df76
ms.sourcegitcommit: 9d95532afe81c235c8094eae28ab84b2f77f8c48
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2020
ms.locfileid: "93220378"
---
# <span data-ttu-id="19c02-103">PowerShellGet 모듈</span><span class="sxs-lookup"><span data-stu-id="19c02-103">PowerShellGet Module</span></span>

## <span data-ttu-id="19c02-104">설명</span><span class="sxs-lookup"><span data-stu-id="19c02-104">Description</span></span>

<span data-ttu-id="19c02-105">PowerShellGet은 모듈, DSC 리소스, 역할 기능 및 스크립트와 같은 PowerShell 아티팩트를 검색, 설치, 업데이트 및 게시 하기 위한 명령이 포함 된 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-105">PowerShellGet is a module with commands for discovering, installing, updating and publishing PowerShell artifacts like Modules, DSC Resources, Role Capabilities, and Scripts.</span></span>

## <span data-ttu-id="19c02-106">PowerShellGet cmdlet</span><span class="sxs-lookup"><span data-stu-id="19c02-106">PowerShellGet Cmdlets</span></span>

### [<span data-ttu-id="19c02-107">Find-Command</span><span class="sxs-lookup"><span data-stu-id="19c02-107">Find-Command</span></span>](Find-Command.md)
<span data-ttu-id="19c02-108">모듈에서 PowerShell 명령을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-108">Finds PowerShell commands in modules.</span></span>

### [<span data-ttu-id="19c02-109">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="19c02-109">Find-DscResource</span></span>](Find-DscResource.md)
<span data-ttu-id="19c02-110">DSC (필요한 상태 구성) 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-110">Finds Desired State Configuration (DSC) resources.</span></span>

### [<span data-ttu-id="19c02-111">Find-Module</span><span class="sxs-lookup"><span data-stu-id="19c02-111">Find-Module</span></span>](Find-Module.md)
<span data-ttu-id="19c02-112">리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-112">Finds modules in a repository that match specified criteria.</span></span>

### [<span data-ttu-id="19c02-113">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="19c02-113">Find-RoleCapability</span></span>](Find-RoleCapability.md)
<span data-ttu-id="19c02-114">모듈에서 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-114">Finds role capabilities in modules.</span></span>

### [<span data-ttu-id="19c02-115">Find-Script</span><span class="sxs-lookup"><span data-stu-id="19c02-115">Find-Script</span></span>](Find-Script.md)
<span data-ttu-id="19c02-116">스크립트를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-116">Finds a script.</span></span>

### [<span data-ttu-id="19c02-117">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="19c02-117">Get-InstalledModule</span></span>](Get-InstalledModule.md)
<span data-ttu-id="19c02-118">PowerShellGet에 의해 설치 된 컴퓨터의 모듈 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-118">Gets a list of modules on the computer that were installed by PowerShellGet.</span></span>

### [<span data-ttu-id="19c02-119">Get-InstalledScript</span><span class="sxs-lookup"><span data-stu-id="19c02-119">Get-InstalledScript</span></span>](Get-InstalledScript.md)
<span data-ttu-id="19c02-120">설치 된 스크립트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-120">Gets an installed script.</span></span>

### [<span data-ttu-id="19c02-121">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="19c02-121">Get-PSRepository</span></span>](Get-PSRepository.md)
<span data-ttu-id="19c02-122">PowerShell 리포지토리를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-122">Gets PowerShell repositories.</span></span>

### [<span data-ttu-id="19c02-123">Install-Module</span><span class="sxs-lookup"><span data-stu-id="19c02-123">Install-Module</span></span>](Install-Module.md)
<span data-ttu-id="19c02-124">리포지토리에서 하나 이상의 모듈을 다운로드 하 고 로컬 컴퓨터에 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-124">Downloads one or more modules from a repository, and installs them on the local computer.</span></span>

### [<span data-ttu-id="19c02-125">Install-Script</span><span class="sxs-lookup"><span data-stu-id="19c02-125">Install-Script</span></span>](Install-Script.md)
<span data-ttu-id="19c02-126">스크립트를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-126">Installs a script.</span></span>

### [<span data-ttu-id="19c02-127">New-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="19c02-127">New-ScriptFileInfo</span></span>](New-ScriptFileInfo.md)
<span data-ttu-id="19c02-128">메타데이터를 사용하여 스크립트 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-128">Creates a script file with metadata.</span></span>

### [<span data-ttu-id="19c02-129">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="19c02-129">Publish-Module</span></span>](Publish-Module.md)
<span data-ttu-id="19c02-130">로컬 컴퓨터에서 지정된 모듈을 온라인 갤러리에 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-130">Publishes a specified module from the local computer to an online gallery.</span></span>

### [<span data-ttu-id="19c02-131">Publish-Script</span><span class="sxs-lookup"><span data-stu-id="19c02-131">Publish-Script</span></span>](Publish-Script.md)
<span data-ttu-id="19c02-132">스크립트를 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-132">Publishes a script.</span></span>

### [<span data-ttu-id="19c02-133">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="19c02-133">Register-PSRepository</span></span>](Register-PSRepository.md)
<span data-ttu-id="19c02-134">PowerShell 리포지토리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-134">Registers a PowerShell repository.</span></span>

### [<span data-ttu-id="19c02-135">Save-Module</span><span class="sxs-lookup"><span data-stu-id="19c02-135">Save-Module</span></span>](Save-Module.md)
<span data-ttu-id="19c02-136">모듈 및 해당 종속성을 로컬 컴퓨터에 저장 하지만 모듈을 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-136">Saves a module and its dependencies on the local computer but doesn't install the module.</span></span>

### [<span data-ttu-id="19c02-137">Save-Script</span><span class="sxs-lookup"><span data-stu-id="19c02-137">Save-Script</span></span>](Save-Script.md)
<span data-ttu-id="19c02-138">스크립트를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-138">Saves a script.</span></span>

### [<span data-ttu-id="19c02-139">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="19c02-139">Set-PSRepository</span></span>](Set-PSRepository.md)
<span data-ttu-id="19c02-140">등록 된 리포지토리에 대 한 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-140">Sets values for a registered repository.</span></span>

### [<span data-ttu-id="19c02-141">Test-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="19c02-141">Test-ScriptFileInfo</span></span>](Test-ScriptFileInfo.md)
<span data-ttu-id="19c02-142">스크립트에 대 한 주석 블록의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-142">Validates a comment block for a script.</span></span>

### [<span data-ttu-id="19c02-143">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="19c02-143">Uninstall-Module</span></span>](Uninstall-Module.md)
<span data-ttu-id="19c02-144">모듈을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-144">Uninstalls a module.</span></span>

### [<span data-ttu-id="19c02-145">Uninstall-Script</span><span class="sxs-lookup"><span data-stu-id="19c02-145">Uninstall-Script</span></span>](Uninstall-Script.md)
<span data-ttu-id="19c02-146">스크립트를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-146">Uninstalls a script.</span></span>

### [<span data-ttu-id="19c02-147">Unregister-PSRepository</span><span class="sxs-lookup"><span data-stu-id="19c02-147">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
<span data-ttu-id="19c02-148">리포지토리 등록을 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-148">Unregisters a repository.</span></span>

### [<span data-ttu-id="19c02-149">Update-Module</span><span class="sxs-lookup"><span data-stu-id="19c02-149">Update-Module</span></span>](Update-Module.md)
<span data-ttu-id="19c02-150">온라인 갤러리에서 지정된 모듈의 최신 버전을 로컬 컴퓨터에 다운로드하여 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-150">Downloads and installs the newest version of specified modules from an online gallery to the local computer.</span></span>

### [<span data-ttu-id="19c02-151">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="19c02-151">Update-ModuleManifest</span></span>](Update-ModuleManifest.md)
<span data-ttu-id="19c02-152">모듈 매니페스트 파일을 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-152">Updates a module manifest file.</span></span>

### [<span data-ttu-id="19c02-153">Update-Script</span><span class="sxs-lookup"><span data-stu-id="19c02-153">Update-Script</span></span>](Update-Script.md)
<span data-ttu-id="19c02-154">스크립트를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-154">Updates a script.</span></span>

### [<span data-ttu-id="19c02-155">Update-ScriptFileInfo</span><span class="sxs-lookup"><span data-stu-id="19c02-155">Update-ScriptFileInfo</span></span>](Update-ScriptFileInfo.md)
<span data-ttu-id="19c02-156">스크립트에 대 한 정보를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="19c02-156">Updates information for a script.</span></span>

