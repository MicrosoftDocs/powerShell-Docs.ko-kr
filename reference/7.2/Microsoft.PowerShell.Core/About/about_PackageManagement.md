---
description: PackageManagement는 소프트웨어 패키지 관리자를 위한 집계입니다.
Locale: en-US
ms.date: 03/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_packagemanagement?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PackageManagement
ms.openlocfilehash: 22f47d01063778fca4f51a534b15d485b3beee28
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/17/2020
ms.locfileid: "99601831"
---
# <a name="about-packagemanagement"></a><span data-ttu-id="a81ad-103">PackageManagement 정보</span><span class="sxs-lookup"><span data-stu-id="a81ad-103">About PackageManagement</span></span>

## <a name="short-description"></a><span data-ttu-id="a81ad-104">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="a81ad-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="a81ad-105">PackageManagement는 소프트웨어 패키지 관리자를 위한 집계입니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-105">PackageManagement is an aggregator for software package managers.</span></span>

## <a name="long-description"></a><span data-ttu-id="a81ad-106">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="a81ad-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="a81ad-107">PackageManagement 기능은 Windows PowerShell 5.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-107">PackageManagement functionality was introduced in Windows PowerShell 5.0.</span></span>

<span data-ttu-id="a81ad-108">PackageManagement는 소프트웨어 패키지 관리 시스템에 대 한 통합 인터페이스입니다. PackageManagement cmdlet을 실행 하 여 SDII (소프트웨어 검색, 설치 및 인벤토리) 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-108">PackageManagement is a unified interface for software package management systems; you can run PackageManagement cmdlets to perform software discovery, installation, and inventory (SDII) tasks.</span></span> <span data-ttu-id="a81ad-109">기본 설치 기술에 관계 없이 PackageManagement 모듈에서 일반 cmdlet을 실행 하 여 패키지를 검색, 설치 또는 제거할 수 있습니다. 패키지 리포지토리 추가, 제거 및 쿼리 그리고 컴퓨터에서 쿼리를 실행 하 여 설치 된 소프트웨어 패키지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-109">Regardless of the underlying installation technology, you can run the common cmdlets in the PackageManagement module to search for, install, or uninstall packages; add, remove, and query package repositories; and run queries on a computer to determine which software packages are installed.</span></span>

<span data-ttu-id="a81ad-110">PackageManagement는 다른 소프트웨어 패키지 관리 시스템을 지원할 수 있도록 하는 유연한 플러그 인 모델을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-110">PackageManagement supports a flexible plug-in model that enables support for other software package management systems.</span></span>

<span data-ttu-id="a81ad-111">PackageManagement 모듈은 PowerShell의 Windows PowerShell 5.0 이상 릴리스에 포함 되어 있으며 패키지 공급자, 패키지 원본 및 패키지 자체의 세 가지 패키지 관리 구조 수준에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-111">The PackageManagement module is included with Windows PowerShell 5.0 and later releases of PowerShell, and works on three levels of package management structure: package providers, package sources, and the packages themselves.</span></span> <span data-ttu-id="a81ad-112">몇 가지 용어를 정의 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-112">Let us define some terms:</span></span>

- <span data-ttu-id="a81ad-113">패키지 관리자: 소프트웨어 패키지 관리 시스템.</span><span class="sxs-lookup"><span data-stu-id="a81ad-113">Package manager: Software package management system.</span></span> <span data-ttu-id="a81ad-114">PackageManagement 용어로는 패키지 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-114">In PackageManagement terms, this is a package provider.</span></span>
- <span data-ttu-id="a81ad-115">패키지 공급자: 패키지 관리자에 대 한 PackageManagement 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-115">Package provider: PackageManagement term for a package manager.</span></span> <span data-ttu-id="a81ad-116">예를 들면 Windows Installer, Chocolatey 등이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-116">Examples can include Windows Installer, Chocolatey, and others.</span></span>
- <span data-ttu-id="a81ad-117">패키지 원본: 리포지토리로 사용할 패키지 공급자를 구성 하는 URL, 로컬 폴더 또는 네트워크 공유 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-117">Package source: A URL, local folder, or network shared folder that you configure package providers to use as a repository.</span></span>
- <span data-ttu-id="a81ad-118">패키지: 패키지 공급자가 관리 하며 특정 패키지 원본에 저장 되는 소프트웨어의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-118">Package: A piece of software that a package provider manages, and that is stored in a specific package source.</span></span>

<span data-ttu-id="a81ad-119">PackageManagement 모듈에는 다음 cmdlet이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-119">The PackageManagement module includes the following cmdlets.</span></span> <span data-ttu-id="a81ad-120">자세한 내용은 [PackageManagement](/powershell/module/packagemanagement) 도움말을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a81ad-120">For more information, see the [PackageManagement](/powershell/module/packagemanagement) help.</span></span>

- <span data-ttu-id="a81ad-121">`Get-PackageProvider`: PackageManagement에 연결 된 패키지 공급자의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-121">`Get-PackageProvider`: Returns a list of package providers that are  connected to PackageManagement.</span></span>
- <span data-ttu-id="a81ad-122">`Get-PackageSource`: 패키지 공급자에 대해 등록 된 패키지 소스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-122">`Get-PackageSource`: Gets a list of package sources that are registered for a package provider.</span></span>
- <span data-ttu-id="a81ad-123">`Register-PackageSource`: 지정 된 패키지 공급자에 대 한 패키지 소스를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-123">`Register-PackageSource`: Adds a package source for a specified package provider.</span></span>
- <span data-ttu-id="a81ad-124">`Set-PackageSource`: 기존 패키지 소스에 대 한 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-124">`Set-PackageSource`: Sets properties on an existing package source.</span></span>
- <span data-ttu-id="a81ad-125">`Unregister-PackageSource`: 등록 된 패키지 원본을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-125">`Unregister-PackageSource`: Removes a registered package source.</span></span>
- <span data-ttu-id="a81ad-126">`Get-Package`: 설치 된 소프트웨어 패키지의 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-126">`Get-Package`: Returns a list of installed software packages.</span></span>
- <span data-ttu-id="a81ad-127">`Find-Package`: 사용 가능한 패키지 소스에서 소프트웨어 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-127">`Find-Package`: Finds software packages in available package sources.</span></span>
- <span data-ttu-id="a81ad-128">`Install-Package`: 하나 이상의 소프트웨어 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-128">`Install-Package`: Installs one or more software packages.</span></span>
- <span data-ttu-id="a81ad-129">`Save-Package`: 패키지를 설치 하지 않고 로컬 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-129">`Save-Package`: Saves packages to the local computer without installing them.</span></span>
- <span data-ttu-id="a81ad-130">`Uninstall-Package`: 하나 이상의 소프트웨어 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-130">`Uninstall-Package`: Uninstalls one or more software packages.</span></span>

### <a name="package-provider-bootstrapping-and-dynamic-cmdlet-parameters"></a><span data-ttu-id="a81ad-131">패키지 공급자 부트스트래핑 및 동적 Cmdlet 매개 변수</span><span class="sxs-lookup"><span data-stu-id="a81ad-131">Package Provider Bootstrapping and Dynamic Cmdlet Parameters</span></span>

<span data-ttu-id="a81ad-132">기본적으로 PackageManagement는 핵심 부트스트랩 공급자와 함께 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-132">By default, PackageManagement ships with a core bootstrap provider.</span></span> <span data-ttu-id="a81ad-133">공급자를 부트스트래핑 하 여 필요에 따라 추가 패키지 공급자를 설치할 수 있습니다. 즉, 웹 서비스에서 공급자를 자동으로 설치 하 라는 메시지에 응답 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-133">You can install additional package providers as you need them by bootstrapping the providers; that is, responding to a prompt to install the provider automatically, from a web service.</span></span> <span data-ttu-id="a81ad-134">모든 PackageManagement cmdlet을 사용 하 여 패키지 공급자를 지정할 수 있습니다. 지정 된 공급자를 사용할 수 없는 경우 PackageManagement는 공급자를 부트스트랩 하거나 자동으로 설치 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-134">You can specify a package provider with any PackageManagement cmdlet; if the specified provider is not available, PackageManagement prompts you to bootstrap (or automatically install) the provider.</span></span> <span data-ttu-id="a81ad-135">다음 예에서는 Chocolatey 공급자가 아직 설치 되지 않은 경우 PackageManagement 부트스트래핑에서 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-135">In the following examples, if the Chocolatey provider is not already installed, PackageManagement bootstrapping installs the provider.</span></span>

```powershell
Find-Package -Provider Chocolatey <PackageName>
```

<span data-ttu-id="a81ad-136">Chocolatey 공급자가 아직 설치 되지 않은 경우 앞의 명령을 실행할 때 설치 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-136">If the Chocolatey provider is not already installed, when you run the preceding command, you are prompted to install it.</span></span>

```powershell
Install-Package <Chocolatey package Name> -ForceBootstrap
```

<span data-ttu-id="a81ad-137">Chocolatey 공급자가 아직 설치 되지 않은 경우 위의 명령을 실행 하면 공급자가 설치 됩니다. 그러나 ForceBootstrap 매개 변수가 명령에 추가 되었기 때문에 설치 하 라는 메시지가 표시 되지 않습니다. 공급자와 패키지는 모두 자동으로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-137">If the Chocolatey provider is not already installed, when you run the preceding command, the provider is installed; but because the ForceBootstrap parameter has been added to the command, you are not prompted to install it; both the provider and the package are installed automatically.</span></span>

<span data-ttu-id="a81ad-138">패키지를 설치 하려고 할 때 지원 공급자를 아직 설치 하지 않은 경우 명령에 ForceBootstrap 매개 변수를 추가 하지 않은 경우 PackageManagement에서 공급자를 설치할지 묻는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-138">When you try to install a package, if you do not already have the supporting provider installed, and you do not add the ForceBootstrap parameter to your command, PackageManagement prompts you to install the provider.</span></span>

<span data-ttu-id="a81ad-139">PackageManagement 명령에 패키지 공급자를 지정 하면 해당 패키지 공급자와 관련 된 동적 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-139">Specifying a package provider in your PackageManagement command can make dynamic parameters available that are specific to that package provider.</span></span> <span data-ttu-id="a81ad-140">특정 PackageManagement cmdlet에 대 한 Get-Help를 실행 하면 매개 변수 집합 목록이 반환 되 고, 사용 가능한 패키지 공급자에 대 한 동적 매개 변수를 별도의 매개 변수 집합에서 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="a81ad-140">When you run Get-Help for a specific PackageManagement cmdlet, a list of parameter sets are returned, grouping dynamic parameters for available package providers in separate parameter sets.</span></span>

<span data-ttu-id="a81ad-141">PackageManagement 프로젝트에 대 한 자세한 정보</span><span class="sxs-lookup"><span data-stu-id="a81ad-141">More Information About the PackageManagement Project</span></span>

<span data-ttu-id="a81ad-142">Packagemanagement 패키지 공급자를 만드는 방법을 비롯 한 PackageManagement open development 프로젝트에 대 한 자세한 내용은 GitHub의 PackageManagement 프로젝트를 참조 https://oneget.org 하세요.</span><span class="sxs-lookup"><span data-stu-id="a81ad-142">For more information about the PackageManagement open development project, including how to create a PackageManagement package provider, see the PackageManagement project on GitHub at https://oneget.org.</span></span>

## <a name="see-also"></a><span data-ttu-id="a81ad-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a81ad-143">SEE ALSO</span></span>

[<span data-ttu-id="a81ad-144">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="a81ad-144">Get-PackageProvider</span></span>](xref:PackageManagement.Get-PackageProvider)

[<span data-ttu-id="a81ad-145">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a81ad-145">Get-PackageSource</span></span>](xref:PackageManagement.Get-PackageSource)

[<span data-ttu-id="a81ad-146">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a81ad-146">Register-PackageSource</span></span>](xref:PackageManagement.Register-PackageSource)

[<span data-ttu-id="a81ad-147">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a81ad-147">Set-PackageSource</span></span>](xref:PackageManagement.Set-PackageSource)

[<span data-ttu-id="a81ad-148">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a81ad-148">Unregister-PackageSource</span></span>](xref:PackageManagement.Unregister-PackageSource)

[<span data-ttu-id="a81ad-149">Get-Package</span><span class="sxs-lookup"><span data-stu-id="a81ad-149">Get-Package</span></span>](xref:PackageManagement.Get-Package)

[<span data-ttu-id="a81ad-150">Find-Package</span><span class="sxs-lookup"><span data-stu-id="a81ad-150">Find-Package</span></span>](xref:PackageManagement.Find-Package)

[<span data-ttu-id="a81ad-151">Install-Package</span><span class="sxs-lookup"><span data-stu-id="a81ad-151">Install-Package</span></span>](xref:PackageManagement.Install-Package)

[<span data-ttu-id="a81ad-152">Save-Package</span><span class="sxs-lookup"><span data-stu-id="a81ad-152">Save-Package</span></span>](xref:PackageManagement.Save-Package)

[<span data-ttu-id="a81ad-153">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="a81ad-153">Uninstall-Package</span></span>](xref:PackageManagement.Uninstall-Package)

