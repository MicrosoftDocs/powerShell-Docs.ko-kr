---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 683329aac35744697d80e22efff5ec53bae74830
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99600659"
---
# <span data-ttu-id="b4544-102">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b4544-102">Install-PackageProvider</span></span>

## <span data-ttu-id="b4544-103">개요</span><span class="sxs-lookup"><span data-stu-id="b4544-103">SYNOPSIS</span></span>
<span data-ttu-id="b4544-104">하나 이상의 패키지 관리 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-104">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="b4544-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b4544-105">SYNTAX</span></span>

### <span data-ttu-id="b4544-106">PackageBySearch (기본값)</span><span class="sxs-lookup"><span data-stu-id="b4544-106">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="b4544-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b4544-107">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="b4544-108">설명</span><span class="sxs-lookup"><span data-stu-id="b4544-108">DESCRIPTION</span></span>

<span data-ttu-id="b4544-109">이 `Install-PackageProvider` cmdlet은 **PowerShellGet** 에 등록 된 패키지 소스에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-109">The `Install-PackageProvider` cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet**.</span></span> <span data-ttu-id="b4544-110">기본적으로이 창에는 **PackageManagement** 태그를 사용 하 여 Windows PowerShell 갤러리에서 사용할 수 있는 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-110">By default, this includes modules available in the Windows PowerShell Gallery with the **PackageManagement** tag.</span></span> <span data-ttu-id="b4544-111">**PowerShellGet** 패키지 관리 공급자는 이러한 리포지토리에서 공급자를 찾는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-111">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="b4544-112">또한이 cmdlet은 패키지 관리 부트스트래핑 응용 프로그램을 통해 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-112">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="b4544-113">또한이 cmdlet은 패키지 관리 Azure Blob 저장소에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-113">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span> <span data-ttu-id="b4544-114">부트스트래퍼 공급자를 사용 하 여 찾아서 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-114">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="b4544-115">처음 실행 하려면 PackageManagement에서 NuGet 패키지 공급자를 다운로드 하려면 인터넷에 연결 되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-115">In order to execute the first time, PackageManagement requires an internet connection to download the NuGet package provider.</span></span> <span data-ttu-id="b4544-116">그러나 컴퓨터에 인터넷 연결이 없고 NuGet 또는 PowerShellGet 공급자를 사용 해야 하는 경우에는 다른 컴퓨터에서 다운로드 하 여 대상 컴퓨터에 복사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-116">However, if your computer does not have an internet connection and you need to use the NuGet or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span> <span data-ttu-id="b4544-117">이렇게 하려면 다음 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-117">Use the following steps to do this:</span></span>

1. <span data-ttu-id="b4544-118">`Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force`을 실행 하 여 인터넷에 연결 된 컴퓨터에서 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-118">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>
1. <span data-ttu-id="b4544-119">설치 후 또는에 설치 된 공급자를 찾을 수 있습니다 `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>` .</span><span class="sxs-lookup"><span data-stu-id="b4544-119">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\<ProviderName>\<ProviderVersion>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\<ProviderName>\<ProviderVersion>`.</span></span>
1. <span data-ttu-id="b4544-120">`<ProviderName>`폴더 (이 경우에는 NuGet 폴더)를 대상 컴퓨터의 해당 위치에 배치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-120">Place the `<ProviderName>` folder, which in this case is the NuGet folder, in the corresponding location on your target computer.</span></span> <span data-ttu-id="b4544-121">대상 컴퓨터가 Nano 서버인 경우 Nano Server에서를 실행 하 여 `Install-PackageProvider` 올바른 NuGet 이진 파일을 다운로드 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-121">If your target computer is a Nano server, you need to run `Install-PackageProvider` from Nano Server to download the correct NuGet binaries.</span></span>
1. <span data-ttu-id="b4544-122">PowerShell을 다시 시작 하 여 패키지 공급자를 자동으로 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-122">Restart PowerShell to auto-load the package provider.</span></span> <span data-ttu-id="b4544-123">또는를 실행 `Get-PackageProvider -ListAvailable` 하 여 컴퓨터에서 사용할 수 있는 패키지 공급자를 모두 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-123">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
   <span data-ttu-id="b4544-124">그런 다음 `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` 를 사용 하 여 현재 Windows PowerShell 세션으로 공급자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-124">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current Windows PowerShell session.</span></span>

## <span data-ttu-id="b4544-125">예제</span><span class="sxs-lookup"><span data-stu-id="b4544-125">EXAMPLES</span></span>

### <span data-ttu-id="b4544-126">예제 1: PowerShell 갤러리에서 패키지 공급자 설치</span><span class="sxs-lookup"><span data-stu-id="b4544-126">Example 1: Install a package provider from the PowerShell Gallery</span></span>

<span data-ttu-id="b4544-127">이 명령은 PowerShell 갤러리에서 GistProvider 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-127">This command installs the GistProvider package provider from the PowerShell Gallery.</span></span>

```powershell
Install-PackageProvider -Name "GistProvider" -Verbose
```

### <span data-ttu-id="b4544-128">예 2: 지정 된 버전의 패키지 공급자 설치</span><span class="sxs-lookup"><span data-stu-id="b4544-128">Example 2: Install a specified version of a package provider</span></span>

<span data-ttu-id="b4544-129">이 예제에서는 지정 된 버전의 NuGet 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-129">This example installs a specified version of the NuGet package provider.</span></span>

<span data-ttu-id="b4544-130">첫 번째 명령은 NuGet 이라는 패키지 공급자의 모든 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-130">The first command finds all versions of the package provider named NuGet.</span></span>
<span data-ttu-id="b4544-131">두 번째 명령은 지정 된 버전의 NuGet 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-131">The second command installs a specified version of the NuGet package provider.</span></span>

```powershell
Find-PackageProvider -Name "NuGet" -AllVersions
Install-PackageProvider -Name "NuGet" -RequiredVersion "2.8.5.216" -Force
```

### <span data-ttu-id="b4544-132">예 3: 공급자 찾기 및 설치</span><span class="sxs-lookup"><span data-stu-id="b4544-132">Example 3: Find a provider and install it</span></span>

<span data-ttu-id="b4544-133">이 예제에서는 및 파이프라인을 사용 하 여 `Find-PackageProvider` 요점 공급자를 검색 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-133">This example uses `Find-PackageProvider` and the pipeline to search for the Gist provider and install it.</span></span>

```powershell
Find-PackageProvider -Name "GistProvider" | Install-PackageProvider -Verbose
```

### <span data-ttu-id="b4544-134">예제 4: 현재 사용자의 모듈 폴더에 공급자 설치</span><span class="sxs-lookup"><span data-stu-id="b4544-134">Example 4: Install a provider to the current user's module folder</span></span>

<span data-ttu-id="b4544-135">이 명령은 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` 현재 사용자만 사용할 수 있도록에 패키지 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-135">This command installs a package provider to `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies` so that only the current user can use it.</span></span>

```powershell
Install-PackageProvider -Name GistProvider -Verbose -Scope CurrentUser
```

## <span data-ttu-id="b4544-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b4544-136">PARAMETERS</span></span>

### <span data-ttu-id="b4544-137">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="b4544-137">-AllVersions</span></span>

<span data-ttu-id="b4544-138">이 cmdlet은 패키지 공급자의 사용 가능한 모든 버전을 설치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-138">Indicates that this cmdlet installs all available versions of the package provider.</span></span> <span data-ttu-id="b4544-139">기본적으로는 `Install-PackageProvider` 사용 가능한 가장 높은 버전만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-139">By default, `Install-PackageProvider` only returns the highest available version.</span></span>

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

### <span data-ttu-id="b4544-140">-Credential</span><span class="sxs-lookup"><span data-stu-id="b4544-140">-Credential</span></span>

<span data-ttu-id="b4544-141">패키지 공급자를 설치할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-141">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="b4544-142">-Force</span><span class="sxs-lookup"><span data-stu-id="b4544-142">-Force</span></span>

<span data-ttu-id="b4544-143">이 cmdlet이 강제로 적용할 수 있는이 cmdlet을 사용 하 여 모든 작업을 수행 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-143">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span> <span data-ttu-id="b4544-144">현재는 **Force** 매개 변수가 **forcebootstrap** 매개 변수와 동일 하 게 작동 한다는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-144">Currently, this means the **Force** parameter acts the same as the **ForceBootstrap** parameter.</span></span>

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

### <span data-ttu-id="b4544-145">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="b4544-145">-ForceBootstrap</span></span>

<span data-ttu-id="b4544-146">이 cmdlet이 패키지 공급자를 자동으로 설치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-146">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="b4544-147">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b4544-147">-InputObject</span></span>

<span data-ttu-id="b4544-148">**\Identity** 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-148">Specifies a **SoftwareIdentity** object.</span></span> <span data-ttu-id="b4544-149">Cmdlet을 사용 하 여를 `Find-PackageProvider` 파이프 하는 개체 **를** 가져옵니다 `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="b4544-149">Use the `Find-PackageProvider` cmdlet to obtain a **SoftwareIdentity** object to pipe into `Install-PackageProvider`.</span></span>

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

### <span data-ttu-id="b4544-150">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b4544-150">-MaximumVersion</span></span>

<span data-ttu-id="b4544-151">설치 하려는 패키지 공급자의 최대 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-151">Specifies the maximum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="b4544-152">이 매개 변수를 추가 하지 않으면에서 `Install-PackageProvider` 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-152">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider.</span></span>

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

### <span data-ttu-id="b4544-153">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b4544-153">-MinimumVersion</span></span>

<span data-ttu-id="b4544-154">설치 하려는 패키지 공급자의 최소 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-154">Specifies the minimum allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="b4544-155">이 매개 변수를 추가 하지 않으면에서 `Install-PackageProvider` *MaximumVersion* 매개 변수로 지정 된 요구 사항에 부합 하는 사용 가능한 가장 높은 버전의 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-155">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="b4544-156">-Name</span><span class="sxs-lookup"><span data-stu-id="b4544-156">-Name</span></span>

<span data-ttu-id="b4544-157">패키지 공급자 모듈 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-157">Specifies one or more package provider module names.</span></span> <span data-ttu-id="b4544-158">여러 패키지 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-158">Separate multiple package names with commas.</span></span>
<span data-ttu-id="b4544-159">와일드카드 문자는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-159">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="b4544-160">-프록시</span><span class="sxs-lookup"><span data-stu-id="b4544-160">-Proxy</span></span>

<span data-ttu-id="b4544-161">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-161">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="b4544-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b4544-162">-ProxyCredential</span></span>

<span data-ttu-id="b4544-163">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="b4544-164">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b4544-164">-RequiredVersion</span></span>

<span data-ttu-id="b4544-165">설치 하려는 패키지 공급자의 정확한 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-165">Specifies the exact allowed version of the package provider that you want to install.</span></span> <span data-ttu-id="b4544-166">이 매개 변수를 추가 하지 않으면에서 `Install-PackageProvider` **MaximumVersion** 매개 변수로 지정 된 최대 버전을 만족 하는 사용 가능한 가장 높은 버전의 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-166">If you do not add this parameter, `Install-PackageProvider` installs the highest available version of the provider that also satisfies any maximum version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="b4544-167">-범위</span><span class="sxs-lookup"><span data-stu-id="b4544-167">-Scope</span></span>

<span data-ttu-id="b4544-168">공급자의 설치 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-168">Specifies the installation scope of the provider.</span></span> <span data-ttu-id="b4544-169">이 매개 변수에 허용되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-169">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="b4544-170">**AllUsers** -컴퓨터의 모든 사용자가 액세스할 수 있는 위치에 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-170">**AllUsers** - installs providers in a location that is accessible to all users of the computer.</span></span>
  <span data-ttu-id="b4544-171">기본적으로 **$env:P rogramfiles\packagemanagement\providerassemblies.** 입니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-171">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

- <span data-ttu-id="b4544-172">**CurrentUser** -현재 사용자만 액세스할 수 있는 위치에 공급자를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-172">**CurrentUser** - installs providers in a location where they are only accessible to the current user.</span></span> <span data-ttu-id="b4544-173">기본적으로 **$env입니다. LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="b4544-173">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

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

### <span data-ttu-id="b4544-174">-Source</span><span class="sxs-lookup"><span data-stu-id="b4544-174">-Source</span></span>

<span data-ttu-id="b4544-175">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-175">Specifies one or more package sources.</span></span> <span data-ttu-id="b4544-176">Cmdlet을 사용 `Get-PackageSource` 하 여 사용 가능한 패키지 원본 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-176">Use the `Get-PackageSource` cmdlet to get a list of available package sources.</span></span>

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

### <span data-ttu-id="b4544-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b4544-177">-Confirm</span></span>

<span data-ttu-id="b4544-178">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-178">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b4544-179">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b4544-179">-WhatIf</span></span>

<span data-ttu-id="b4544-180">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-180">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="b4544-181">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-181">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b4544-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b4544-182">CommonParameters</span></span>

<span data-ttu-id="b4544-183">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b4544-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b4544-184">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4544-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b4544-185">입력</span><span class="sxs-lookup"><span data-stu-id="b4544-185">INPUTS</span></span>

### <span data-ttu-id="b4544-186">Microsoft PackageManagement. 패키지 Id</span><span class="sxs-lookup"><span data-stu-id="b4544-186">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="b4544-187">이 cmdlet에는 개체 **id** 개체를 파이프 하 여 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-187">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span> <span data-ttu-id="b4544-188">를 사용 `Find-PackageProvider` 하 여로 파이프 될 수 있는 고 지 **id** 개체를 가져옵니다 `Install-PackageProvider` .</span><span class="sxs-lookup"><span data-stu-id="b4544-188">Use `Find-PackageProvider` to get a **SoftwareIdentity** object that can be piped into `Install-PackageProvider`.</span></span>

## <span data-ttu-id="b4544-189">출력</span><span class="sxs-lookup"><span data-stu-id="b4544-189">OUTPUTS</span></span>

## <span data-ttu-id="b4544-190">참고</span><span class="sxs-lookup"><span data-stu-id="b4544-190">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4544-191">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-191">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="b4544-192">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-192">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="b4544-193">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4544-193">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="b4544-194">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4544-194">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="b4544-195">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b4544-195">RELATED LINKS</span></span>

[<span data-ttu-id="b4544-196">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b4544-196">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="b4544-197">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b4544-197">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="b4544-198">Import-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b4544-198">Import-PackageProvider</span></span>](Import-PackageProvider.md)