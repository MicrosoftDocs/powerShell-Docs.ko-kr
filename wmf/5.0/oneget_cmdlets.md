---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 2f05fe96ec792a31fabf3aff0f9e18b40178316c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680494"
---
# <a name="packagemanagement-cmdlets"></a><span data-ttu-id="5758e-102">PackageManagement Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-102">PackageManagement Cmdlets</span></span>

<span data-ttu-id="5758e-103">SDII(소프트웨어 검색, 설치 및 인벤토리)를 지원하는 PackageManagement의 핵심입니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-103">This is the core of PackageManagement to support software discovery, installation, and inventory (SDII).</span></span> <span data-ttu-id="5758e-104">이러한 작업에 cmdlet을 사용해 보세요.</span><span class="sxs-lookup"><span data-stu-id="5758e-104">Try out the cmdlets for these operations:</span></span>

- `Find-Package`
- `Find-PackageProvider`
- `Get-Package`
- `Get-PackageProvider`
- `Get-PackageSource`
- `Import-PackageProvider`
- `Install-Package`
- `Install-PackageProvider`
- `Register-PackageSource`
- `Save-Package`
- `Set-PackageSource`
- `Uninstall-Package`
- `Unregister-PackageSource`

<span data-ttu-id="5758e-105">PackageManagement는 PowerShell 모듈이므로 다음을 수행하여 PackageManagement 자체를 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-105">As PackageManagement is a PowerShell module, you can do the following to update PackageManagement itself:</span></span>

```powershell
Install-Module PackageManagement –Force
```

<span data-ttu-id="5758e-106">이 경우 새 버전의 PackageManagement로 전환하려면 PowerShell 세션을 다시 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-106">In this case, you will have to re-enter PowerShell session to switch to the new version of PackageManagement.</span></span>

## <a name="find-package-cmdletpowershellmodulepackagemanagementfind-package"></a>[<span data-ttu-id="5758e-107">Find-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-107">Find-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Find-Package)

<span data-ttu-id="5758e-108">이 cmdlet을 사용하면 로드된 패키지 공급자를 사용하여 사용 가능한 패키지 소스에서 소프트웨어 패키지를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-108">This cmdlet allows discovery of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Find all available Windows PowerShell module packages from galleries registered
# with PowerShellGet provider
Find-Package -ProviderName PowerShellGet -Source as source
Find-Package -Name jquery –Provider NuGet -Source http://www.nuget.org/api/v2/

# Find package with name and version
# Here we are assuming that the user already registered nuget.org using
# Register-PackageSource. You can specify either the provider or the source, or
# neither. For the latter, performance may be less optimal as it searches through all
# the providers and registered sources.
Find-Package -Name jquery –Provider NuGet –RequiredVersion 2.1.4 -Source nuget.org
```

## <a name="find-packageprovider-cmdletpowershellmodulepackagemanagementfind-packageprovider"></a>[<span data-ttu-id="5758e-109">Find-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-109">Find-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Find-PackageProvider)

<span data-ttu-id="5758e-110">`Find-PackageProvider` cmdlet은 PowerShellGet을 사용하여 등록된 패키지 소스에서 일치하는 PackageManagement 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-110">The `Find-PackageProvider` cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span> <span data-ttu-id="5758e-111">이러한 패키지 공급자는 `Install-PackageProvider` cmdlet을 사용하여 설치에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-111">These are package providers available for installation with the `Install-PackageProvider` cmdlet.</span></span> <span data-ttu-id="5758e-112">기본적으로 여기에는 PowerShell 갤러리에서 'PackageManagement' 및 'Provider' 태그가 있는 모듈이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-112">By default, this includes modules available in the PowerShell Gallery with the 'PackageManagement' and 'Provider' Tags.</span></span>

<span data-ttu-id="5758e-113">또한 `Find-PackageProvider`는 PackageManagement 공급자를 찾아 설치하는 데 PackageManagement 부트스트래퍼 공급자를 사용하는 PackageManagement Azure Blob 저장소에서 일치하는 PackageManagement 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-113">`Find-PackageProvider` also finds matching PackageManagement providers that are available in the PackageManagement azure blob store where we use the PackageManagement boostrapper provider for finding and installing them.</span></span>

```powershell
#Find all available package providers in PackageManagement azure blob store as well as in PowerShellGallery.com
Find-PackageProvider

#Find all versions of a provider
Find-PackageProvider -Name "Nuget" -AllVersions

#Find a provider from a specified source
Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

## <a name="get-package-cmdletpowershellmodulepackagemanagementget-package"></a>[<span data-ttu-id="5758e-114">Get-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-114">Get-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Get-Package)

<span data-ttu-id="5758e-115">이 cmdlet은 PackageManagement를 사용하여 설치된 모든 소프트웨어 패키지 목록을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-115">This cmdlet returns a list of all software packages that have been installed using PackageManagement.</span></span>

```powershell
# Get all the packages installed by Programs provider
Get-Package –Provider Programs

# Get all the packages installed by NuGet provider at c:\test using the dynamic
# parameter destination
Get-Package –Provider NuGet -Destination c:\test
```

## <a name="get-packageprovider-cmdletpowershellmodulepackagemanagementget-packageprovider"></a>[<span data-ttu-id="5758e-116">Get-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-116">Get-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageProvider)

<span data-ttu-id="5758e-117">이 cmdlet을 사용하면 로드되어 로컬 컴퓨터에서 사용할 준비가 된 패키지 공급자를 인벤토리에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-117">Package providers that are loaded and ready to be used on the local machine can be inventoried by using the cmdlet.</span></span>

```powershell
# Get all currently loaded package providers
Get-PackageProvider

# The following cmdlet will show all the package providers available on the machine (including those that are not loaded):
Get-PackageProvider -ListAvailable
```

## <a name="get-packagesource-cmdletpowershellmodulepackagemanagementget-packagesource"></a>[<span data-ttu-id="5758e-118">Get-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-118">Get-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Get-PackageSource)

<span data-ttu-id="5758e-119">이 cmdlet은 패키지 공급자에 등록되어 있는 패키지 소스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-119">This cmdlet gets a list of package sources that are registered for a package provider.</span></span>

```powershell
# Get all package sources
Get-PackageSource

# Get all package sources for a specific provider
Get-PackageSource –ProviderName PowerShellGet
```

## <a name="import-packageprovider-cmdletpowershellmodulepackagemanagementimport-packageprovider"></a>[<span data-ttu-id="5758e-120">Import-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-120">Import-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Import-PackageProvider)

<span data-ttu-id="5758e-121">이 cmdlet은 현재 세션에 패키지 관리 패키지 공급자를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-121">This cmdlet adds Package Management package providers to the current session.</span></span>

```powershell
# Import a package provider from the local machine
Import-PackageProvider –Name MyProvider

#The -Name parameter can be either the name of the provider or the full path to the provider. Currently, we support .dll, .exe and.psm1 for the full path case. If the name of the provider is used for the -Name parameter, then additional version parameters such as -RequiredVersion, -MinimumVersion and -MaximumVersion may be specified. Otherwise, the latest version of the provider will be imported.

#If a package provider is not yet loaded to your system, we can discover and install on-demand. You can use explicit discovery and install cmdlets to do so:
 Find-PackageProvider
 Install-PackageProvider –Name MyProvider

#After installed, follow the Import-PackageProvider to load it to your system.

# Import a specific version of a package provider. PackageManagement supports installations of multiple versions of a package provider using PackageProvider cmdlets (not by bootstrapper provider). You can install another version of a package provider given that you already have one up running by:
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force
Get-PackageProvider –ListAvailable
Import-PackageProvider –Name "Nuget" -RequiredVersion "2.8.5.201" -Verbose
Import-PackageProvider –Name MyProvider –RequiredVersion xxxx -force
```

## <a name="-install-package-cmdletpowershellmodulepackagemanagementinstall-package"></a>[<span data-ttu-id="5758e-122"> Install-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-122"> Install-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Install-Package)

<span data-ttu-id="5758e-123">이 cmdlet을 사용하면 로드된 패키지 공급자를 사용하여 사용 가능한 패키지 소스에서 소프트웨어 패키지를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-123">This cmdlet allows installation of software packages in available package sources using loaded package providers.</span></span>

```powershell
# Install a package by name.
# NuGet provider requires us to provide the dynamic parameter destination path
# when we use this provider to install. Not all providers will require you to supply
# dynamic parameters for PackageManagement cmdlets.
Install-Package -Name jquery -Source nuget.org -Destination c:\test

# Install a package by piping.
Find-Package -Name jquery –Provider NuGet | Install-Package -Destination c:\test
```

## <a name="install-packageprovider-cmdletpowershellmodulepackagemanagementinstall-packageprovider"></a>[<span data-ttu-id="5758e-124">Install-PackageProvider Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-124">Install-PackageProvider Cmdlet</span></span>](/powershell/module/PackageManagement/Install-PackageProvider)

<span data-ttu-id="5758e-125">이 cmdlet은 하나 이상의 패키지 관리 패키지 공급자를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-125">This cmdlet installs one or more Package Management package providers.</span></span>

```powershell
# Install a package provider from the PowerShell Gallery
Install-PackageProvider –Name "Gistprovider" -Verbose

# Install a specified version of a package provider
Find-PackageProvider –Name "Nuget" -AllVersions
Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.201" -Force

# Find a provider and install it
Find-PackageProvider –Name "Gistprovider" | Install-PackageProvider -Verbose

# Install a provider to the current user’s module folder
Install-PackageProvider –Name Gistprovider –Verbose –Scope CurrentUser
```

## <a name="register-packagesource-cmdletpowershellmodulepackagemanagementregister-packagesource"></a>[<span data-ttu-id="5758e-126">Register-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-126">Register-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Register-PackageSource)

<span data-ttu-id="5758e-127">이 cmdlet은 지정된 패키지 공급자에 대한 패키지 소스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-127">This cmdlet adds a package source for a specified package provider.</span></span>
<span data-ttu-id="5758e-128">각 PackageManagement 공급자에는 하나 또는 여러 개의 소프트웨어 소스 또는 리포지토리가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-128">Each PackageManagement provider may have one or multiple software sources, or repositories.</span></span> <span data-ttu-id="5758e-129">PackageManagement는 소스를 추가/제거/쿼리하는 PowerShell cmdlet을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-129">PackageManagement provides PowerShell cmdlets to add/remove/query the source.</span></span> <span data-ttu-id="5758e-130">예를 들어 NuGet 공급자에 대해 패키지 소스를 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-130">For example, you can register a package source for the NuGet provider:</span></span>

```powershell
Register-PackageSource -Name "NugetSource" -Location "http://www.nuget.org/api/v2" –ProviderName nuget
```

## <a name="save-package-cmdletpowershellmodulepackagemanagementsave-package"></a>[<span data-ttu-id="5758e-131">Save-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-131">Save-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Save-Package)

<span data-ttu-id="5758e-132">이 cmdlet은 패키지를 설치하지 않고 로컬 컴퓨터에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-132">This cmdlet saves packages to the local computer without installing them.</span></span>

```powershell
# Saves jquery package to c:\test using NuGetProvider
# Notes that the -Path parameter must point to an existing location
Save-Package -Name jquery –Provider NuGet -Path c:\test

# Save a package by piping.
Find-Package -Name jquery -Source http://www.nuget.org/api/v2/ | Save-Package -Path c:\test
Find-Package -Source c:\test
```

## <a name="set-packagesource-cmdletpowershellmodulepackagemanagementset-packagesource"></a>[<span data-ttu-id="5758e-133">Set-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-133">Set-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Set-PackageSource)

<span data-ttu-id="5758e-134">이 cmdlet은 기존 패키지 소스에 대한 정보를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-134">This cmdlet changes information about an existing package source.</span></span>

```powershell
#Set-PackageSource changes the values for a source that has already been registered by running the Register-PackageSource cmdlet. By #running Set-PackageSource, you can change the source name and location.
Set-PackageSource  -Name nuget.org -Location  http://www.nuget.org/api/v2 -NewName nuget2 -NewLocation https://www.nuget.org/api/v2
```

## <a name="uninstall-package-cmdletpowershellmodulepackagemanagementuninstall-package"></a>[<span data-ttu-id="5758e-135">Uninstall-Package Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-135">Uninstall-Package Cmdlet</span></span>](/powershell/module/PackageManagement/Uninstall-Package)

<span data-ttu-id="5758e-136">이 cmdlet은 로컬 컴퓨터에 설치된 패키지를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5758e-136">This cmdlet uninstalls packages installed on the local computer.</span></span>

```powershell
# Uninstall jquery using nuget
Uninstall-Package -Name jquery –Provider NuGet -Destination c:\test

# Uninstall a package with by piping with Get-Package
Get-Package -Name jquery –Provider NuGet -Destination c:\test | Uninstall-Package
```

## <a name="unregister-packagesource-cmdletpowershellmodulepackagemanagementunregister-packagesource"></a>[<span data-ttu-id="5758e-137">Unregister-PackageSource Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5758e-137">Unregister-PackageSource Cmdlet</span></span>](/powershell/module/PackageManagement/Unregister-PackageSource)

```powershell
# Unregister a package source for the NuGet provider. You can use command Unregister-PackageSource, to disconnect with a repository, and Get-PackageSource, to discover what the repositories are associated with that provider.
Unregister-PackageSource  -Name "NugetSource"
```