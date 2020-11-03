---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 9bb2bf79aa17b139bd89281ac0967f7241414d89
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210433"
---
# <span data-ttu-id="52c7c-103">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="52c7c-103">Install-PackageProvider</span></span>

## <span data-ttu-id="52c7c-104">개요</span><span class="sxs-lookup"><span data-stu-id="52c7c-104">SYNOPSIS</span></span>
<span data-ttu-id="52c7c-105">하나 이상의 패키지 관리 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-105">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="52c7c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52c7c-106">SYNTAX</span></span>

### <span data-ttu-id="52c7c-107">PackageBySearch (기본값)</span><span class="sxs-lookup"><span data-stu-id="52c7c-107">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="52c7c-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="52c7c-108">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="52c7c-109">설명</span><span class="sxs-lookup"><span data-stu-id="52c7c-109">DESCRIPTION</span></span>

<span data-ttu-id="52c7c-110">**Install-packageprovider** Cmdlet은 **PowerShellGet** 에 등록 된 패키지 소스에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-110">The **Install-PackageProvider** cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet** .</span></span>
<span data-ttu-id="52c7c-111">기본적으로 여기에는 **PackageManagement** 태그를 사용 하 여 PowerShell 갤러리에서 사용할 수 있는 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-111">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** tag.</span></span>
<span data-ttu-id="52c7c-112">**PowerShellGet** 패키지 관리 공급자는 이러한 리포지토리에서 공급자를 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-112">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="52c7c-113">또한이 cmdlet은 패키지 관리 부트스트래핑 응용 프로그램을 통해 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-113">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="52c7c-114">또한이 cmdlet은 패키지 관리 Azure Blob 저장소에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-114">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="52c7c-115">부트스트래퍼 공급자를 사용 하 여 찾아서 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-115">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="52c7c-116">처음 실행 하려면 PackageManagement에서 Nuget 패키지 공급자를 다운로드 하려면 인터넷에 연결 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-116">In order to execute the first time, PackageManagement requires an internet connection to download the Nuget package provider.</span></span>
<span data-ttu-id="52c7c-117">그러나 컴퓨터에 인터넷 연결이 없고 Nuget 또는 PowerShellGet 공급자를 사용 해야 하는 경우에는 다른 컴퓨터에서 다운로드 하 여 대상 컴퓨터에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-117">However, if your computer does not have an internet connection and you need to use the Nuget or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span>
<span data-ttu-id="52c7c-118">이렇게 하려면 다음 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-118">Use the following steps to do this:</span></span>

1.
<span data-ttu-id="52c7c-119">`Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force`을 실행 하 여 인터넷에 연결 된 컴퓨터에서 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-119">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>

2.
<span data-ttu-id="52c7c-120">설치 후 또는에 설치 된 공급자를 찾을 수 있습니다 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` .</span><span class="sxs-lookup"><span data-stu-id="52c7c-120">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>`.</span></span>

3.
<span data-ttu-id="52c7c-121">\<ProviderName\>폴더 (이 경우에는 Nuget 폴더)를 대상 컴퓨터의 해당 위치에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-121">Place the \<ProviderName\> folder, which in this case is the Nuget folder, in the corresponding location on your target computer.</span></span>
<span data-ttu-id="52c7c-122">대상 컴퓨터가 Nano 서버인 경우 Nano Server에서 **install-packageprovider** 를 실행 하 여 올바른 Nuget 이진 파일을 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-122">If your target computer is a Nano server, you need to run **Install-PackageProvider** from Nano Server to download the correct Nuget binaries.</span></span>

4.
<span data-ttu-id="52c7c-123">PowerShell을 다시 시작 하 여 패키지 공급자를 자동으로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-123">Restart PowerShell to auto-load the package provider.</span></span>
<span data-ttu-id="52c7c-124">또는를 실행 `Get-PackageProvider -ListAvailable` 하 여 컴퓨터에서 사용할 수 있는 패키지 공급자를 모두 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-124">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
<span data-ttu-id="52c7c-125">그런 다음 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 를 사용 하 여 공급자를 현재 PowerShell 세션으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-125">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current PowerShell session.</span></span>

## <span data-ttu-id="52c7c-126">예제</span><span class="sxs-lookup"><span data-stu-id="52c7c-126">EXAMPLES</span></span>

### <span data-ttu-id="52c7c-127">예제 1: PowerShell 갤러리에서 패키지 공급자 설치</span><span class="sxs-lookup"><span data-stu-id="52c7c-127">Example 1: Install a package provider from the PowerShell Gallery</span></span>

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

<span data-ttu-id="52c7c-128">이 명령은 PowerShell 갤러리에서 Gistprovider를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-128">This command installs the Gistprovider from the PowerShell Gallery.</span></span>

### <span data-ttu-id="52c7c-129">예 2: 지정 된 버전의 패키지 공급자 설치</span><span class="sxs-lookup"><span data-stu-id="52c7c-129">Example 2: Install a specified version of a package provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

<span data-ttu-id="52c7c-130">이 예제에서는 지정 된 버전의 Nuget 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-130">This example installs a specified version of the Nuget package provider.</span></span>

<span data-ttu-id="52c7c-131">첫 번째 명령은 Nuget 이라는 패키지 공급자의 모든 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-131">The first command finds all versions of the package provider named Nuget.</span></span>
<span data-ttu-id="52c7c-132">두 번째 명령은 지정 된 버전의 Nuget 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-132">The second command installs a specified version of the Nuget package provider.</span></span>

### <span data-ttu-id="52c7c-133">예 3: 공급자 찾기 및 설치</span><span class="sxs-lookup"><span data-stu-id="52c7c-133">Example 3: Find a provider and install it</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

<span data-ttu-id="52c7c-134">이 명령은 **install-packageprovider** 및 파이프라인을 사용 하 여 요점 공급자를 검색 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-134">This command uses **Find-PackageProvider** and the pipeline to search for the Gist provider and install it.</span></span>

### <span data-ttu-id="52c7c-135">예제 4: 현재 사용자의 모듈 폴더에 공급자 설치</span><span class="sxs-lookup"><span data-stu-id="52c7c-135">Example 4: Install a provider to the current user's module folder</span></span>

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

<span data-ttu-id="52c7c-136">이 명령은 $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies에 패키지 공급자를 설치 하 여 현재 사용자만 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-136">This command installs a package provider to $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies so that only the current user can use it.</span></span>

## <span data-ttu-id="52c7c-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="52c7c-137">PARAMETERS</span></span>

### <span data-ttu-id="52c7c-138">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="52c7c-138">-AllVersions</span></span>

<span data-ttu-id="52c7c-139">이 cmdlet은 패키지 공급자의 사용 가능한 모든 버전을 설치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-139">Indicates that this cmdlet installs all available versions of the package provider.</span></span>
<span data-ttu-id="52c7c-140">기본적으로 **install-packageprovider** 는 사용 가능한 가장 높은 버전만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-140">By default, **Install-PackageProvider** only returns the highest available version.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="52c7c-141">-Credential</span></span>

<span data-ttu-id="52c7c-142">패키지 공급자를 설치할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-142">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-143">-Force</span><span class="sxs-lookup"><span data-stu-id="52c7c-143">-Force</span></span>

<span data-ttu-id="52c7c-144">이 cmdlet이 강제로 적용할 수 있는이 cmdlet을 사용 하 여 모든 작업을 수행 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-144">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="52c7c-145">현재는 *Force* 매개 변수가 *forcebootstrap* 매개 변수와 동일 하 게 작동 한다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-145">Currently, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-146">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="52c7c-146">-ForceBootstrap</span></span>

<span data-ttu-id="52c7c-147">이 cmdlet이 패키지 공급자를 자동으로 설치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-147">Indicates that this cmdlet automatically installs the package provider.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-148">-InputObject</span><span class="sxs-lookup"><span data-stu-id="52c7c-148">-InputObject</span></span>

<span data-ttu-id="52c7c-149">**\Identity** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-149">Specifies a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="52c7c-150">**Install-packageprovider** cmdlet을 사용 하 여 **install-packageprovider** 에 파이프 하기 위한 **\id** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-150">Use the **Find-PackageProvider** cmdlet to obtain a **SoftwareIdentity** object to pipe into **Install-PackageProvider** .</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-151">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="52c7c-151">-MaximumVersion</span></span>

<span data-ttu-id="52c7c-152">설치 하려는 패키지 공급자의 최대 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-152">Specifies the maximum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="52c7c-153">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-153">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-154">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="52c7c-154">-MinimumVersion</span></span>

<span data-ttu-id="52c7c-155">설치 하려는 패키지 공급자의 최소 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-155">Specifies the minimum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="52c7c-156">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 요구 사항을 충족 하는 사용 가능한 가장 높은 버전의 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-156">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-157">-Name</span><span class="sxs-lookup"><span data-stu-id="52c7c-157">-Name</span></span>

<span data-ttu-id="52c7c-158">패키지 공급자 모듈 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-158">Specifies one or more package provider module names.</span></span>
<span data-ttu-id="52c7c-159">여러 패키지 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-159">Separate multiple package names with commas.</span></span>
<span data-ttu-id="52c7c-160">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-160">Wildcard characters are not supported.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-161">-프록시</span><span class="sxs-lookup"><span data-stu-id="52c7c-161">-Proxy</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="52c7c-162">-ProxyCredential</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-163">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="52c7c-163">-RequiredVersion</span></span>

<span data-ttu-id="52c7c-164">설치 하려는 패키지 공급자의 정확한 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-164">Specifies the exact allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="52c7c-165">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-165">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-166">-범위</span><span class="sxs-lookup"><span data-stu-id="52c7c-166">-Scope</span></span>

<span data-ttu-id="52c7c-167">공급자의 설치 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-167">Specifies the installation scope of the provider.</span></span>
<span data-ttu-id="52c7c-168">이 매개 변수에 허용 되는 값은 **AllUsers** 및 **CurrentUser** 입니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-168">The acceptable values for this parameter are: **AllUsers** and **CurrentUser** .</span></span>

<span data-ttu-id="52c7c-169">**AllUsers** 범위는 컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-169">The **AllUsers** scope installs providers in a location that is accessible to all users of the computer.</span></span>
<span data-ttu-id="52c7c-170">기본적으로 **$env:P rogramfiles\packagemanagement\providerassemblies.** 입니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-170">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

<span data-ttu-id="52c7c-171">**CurrentUser** 범위는 현재 사용자만 액세스할 수 있는 위치에 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-171">The **CurrentUser** scope installs providers in a location where they are only accessible to the current user.</span></span>
<span data-ttu-id="52c7c-172">기본적으로 **$env입니다. LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="52c7c-172">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-173">-Source</span><span class="sxs-lookup"><span data-stu-id="52c7c-173">-Source</span></span>

<span data-ttu-id="52c7c-174">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-174">Specifies one or more package sources.</span></span>
<span data-ttu-id="52c7c-175">Get-PackageSource cmdlet을 사용 하 여 사용 가능한 패키지 원본 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-175">Use the Get-PackageSource cmdlet to get a list of available package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-176">-Confirm</span><span class="sxs-lookup"><span data-stu-id="52c7c-176">-Confirm</span></span>

<span data-ttu-id="52c7c-177">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-177">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-178">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="52c7c-178">-WhatIf</span></span>

<span data-ttu-id="52c7c-179">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-179">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="52c7c-180">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-180">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="52c7c-181">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52c7c-181">CommonParameters</span></span>

<span data-ttu-id="52c7c-182">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52c7c-182">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52c7c-183">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52c7c-183">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52c7c-184">입력</span><span class="sxs-lookup"><span data-stu-id="52c7c-184">INPUTS</span></span>

### <span data-ttu-id="52c7c-185">Microsoft PackageManagement. 패키지 Id</span><span class="sxs-lookup"><span data-stu-id="52c7c-185">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="52c7c-186">이 cmdlet에는 개체 **id** 개체를 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-186">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span>
<span data-ttu-id="52c7c-187">Find-PackageProvider를 사용 하 여 **install-packageprovider** 로 파이프 될 수 있는 **\id** 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52c7c-187">Use Find-PackageProvider to get a **SoftwareIdentity** object that can be piped into **Install-PackageProvider** .</span></span>

## <span data-ttu-id="52c7c-188">출력</span><span class="sxs-lookup"><span data-stu-id="52c7c-188">OUTPUTS</span></span>

## <span data-ttu-id="52c7c-189">참고</span><span class="sxs-lookup"><span data-stu-id="52c7c-189">NOTES</span></span>

## <span data-ttu-id="52c7c-190">관련 링크</span><span class="sxs-lookup"><span data-stu-id="52c7c-190">RELATED LINKS</span></span>

[<span data-ttu-id="52c7c-191">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="52c7c-191">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="52c7c-192">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="52c7c-192">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="52c7c-193">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="52c7c-193">Import-PackageProvider</span></span>](Import-PackageProvider.md)
