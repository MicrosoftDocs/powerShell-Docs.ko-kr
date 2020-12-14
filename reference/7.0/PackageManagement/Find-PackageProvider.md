---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: ac6acb8017ca992f10f377cf921f59c7b99bea4a
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890613"
---
# <span data-ttu-id="15f23-103">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="15f23-103">Find-PackageProvider</span></span>

## <span data-ttu-id="15f23-104">개요</span><span class="sxs-lookup"><span data-stu-id="15f23-104">SYNOPSIS</span></span>
<span data-ttu-id="15f23-105">설치에 사용할 수 있는 패키지 관리 패키지 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-105">Returns a list of Package Management package providers available for installation.</span></span>

## <span data-ttu-id="15f23-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="15f23-106">SYNTAX</span></span>

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="15f23-107">설명</span><span class="sxs-lookup"><span data-stu-id="15f23-107">DESCRIPTION</span></span>

<span data-ttu-id="15f23-108">**Install-packageprovider** Cmdlet은 PowerShellGet에 등록 된 패키지 소스에서 사용할 수 있는 일치 하는 PackageManagement 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-108">The **Find-PackageProvider** cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span>
<span data-ttu-id="15f23-109">이러한 패키지 공급자는 Install-PackageProvider cmdlet을 사용하여 설치에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-109">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span>
<span data-ttu-id="15f23-110">기본적으로 여기에는 **PackageManagement** 및 **공급자** 태그를 사용 하 여 PowerShell 갤러리에서 사용할 수 있는 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-110">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** and **Provider** tags.</span></span>

<span data-ttu-id="15f23-111">또한 **install-packageprovider** 는 패키지 관리 Azure Blob 저장소에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-111">**Find-PackageProvider** also finds matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="15f23-112">부트스트래퍼 공급자를 사용 하 여 찾아서 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-112">Use the bootstrapper provider to find and install them.</span></span>

## <span data-ttu-id="15f23-113">예제</span><span class="sxs-lookup"><span data-stu-id="15f23-113">EXAMPLES</span></span>

### <span data-ttu-id="15f23-114">예제 1: 사용 가능한 모든 패키지 공급자 찾기</span><span class="sxs-lookup"><span data-stu-id="15f23-114">Example 1: Find all available package providers</span></span>

```
PS C:\> Find-PackageProvider
```

<span data-ttu-id="15f23-115">이 명령은 패키지 관리에서 지 원하는 리포지토리에서 사용할 수 있는 모든 패키지 공급자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-115">This command gets a list of all package providers that are available on the repositories supported by Package Management.</span></span>
<span data-ttu-id="15f23-116">이러한 패키지 공급자는 기본적으로 PowerShell 갤러리 및 패키지 관리 부트스트래핑 응용 프로그램을 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-116">By default, those package providers are available on the PowerShell Gallery and by using the Package Management bootstrapping application.</span></span>

### <span data-ttu-id="15f23-117">예제 2: 공급자의 모든 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="15f23-117">Example 2: Find all versions of a provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

<span data-ttu-id="15f23-118">이 명령은 Nuget 이라는 패키지 공급자의 모든 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-118">This command finds all versions of the package provider named Nuget.</span></span>

### <span data-ttu-id="15f23-119">예제 3: 지정 된 소스에서 공급자 찾기</span><span class="sxs-lookup"><span data-stu-id="15f23-119">Example 3: Find a provider from a specified source</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

<span data-ttu-id="15f23-120">이 명령은 지정 된 패키지 원본을 사용 하 여 사용할 수 있는 패키지 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-120">This command finds a package provider available by using a specified package source.</span></span>

## <span data-ttu-id="15f23-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="15f23-121">PARAMETERS</span></span>

### <span data-ttu-id="15f23-122">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="15f23-122">-AllVersions</span></span>

<span data-ttu-id="15f23-123">이 cmdlet은 패키지 공급자의 사용 가능한 모든 버전을 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-123">Indicates that this cmdlet returns all available versions of the package provider.</span></span>
<span data-ttu-id="15f23-124">기본적으로 **install-packageprovider** 는 사용 가능한 최신 버전만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-124">By default, **Find-PackageProvider** only returns the newest available version.</span></span>

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

### <span data-ttu-id="15f23-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="15f23-125">-Credential</span></span>

<span data-ttu-id="15f23-126">패키지 공급자를 검색할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-126">Specifies a user account that has permission to search for package providers.</span></span>

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

### <span data-ttu-id="15f23-127">-Force</span><span class="sxs-lookup"><span data-stu-id="15f23-127">-Force</span></span>

<span data-ttu-id="15f23-128">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-128">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="15f23-129">현재는 *Forcebootstrap* 매개 변수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-129">Currently, this is equivalent to the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="15f23-130">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="15f23-130">-ForceBootstrap</span></span>

<span data-ttu-id="15f23-131">이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-131">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="15f23-132">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="15f23-132">-IncludeDependencies</span></span>

<span data-ttu-id="15f23-133">이 cmdlet에 종속성이 포함 되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-133">Indicates that this cmdlet includes dependencies.</span></span>

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

### <span data-ttu-id="15f23-134">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="15f23-134">-MaximumVersion</span></span>

<span data-ttu-id="15f23-135">검색 하려는 패키지 공급자의 최대 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-135">Specifies the maximum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="15f23-136">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 에서 사용 가능한 가장 높은 버전의 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-136">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f23-137">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="15f23-137">-MinimumVersion</span></span>

<span data-ttu-id="15f23-138">검색 하려는 패키지 공급자의 최소 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-138">Specifies the minimum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="15f23-139">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 지정 버전을 만족 하는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-139">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f23-140">-Name</span><span class="sxs-lookup"><span data-stu-id="15f23-140">-Name</span></span>

<span data-ttu-id="15f23-141">하나 이상의 패키지 공급자 모듈 이름 또는 와일드 카드 문자를 포함 하는 공급자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-141">Specifies one or more package provider module names, or provider names with wildcard characters.</span></span>
<span data-ttu-id="15f23-142">여러 패키지 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-142">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="15f23-143">-프록시</span><span class="sxs-lookup"><span data-stu-id="15f23-143">-Proxy</span></span>

<span data-ttu-id="15f23-144">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-144">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="15f23-145">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="15f23-145">-ProxyCredential</span></span>

<span data-ttu-id="15f23-146">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-146">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="15f23-147">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="15f23-147">-RequiredVersion</span></span>

<span data-ttu-id="15f23-148">찾으려는 패키지 공급자의 정확한 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-148">Specifies the exact allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="15f23-149">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-149">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="15f23-150">-Source</span><span class="sxs-lookup"><span data-stu-id="15f23-150">-Source</span></span>

<span data-ttu-id="15f23-151">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-151">Specifies one or more package sources.</span></span>
<span data-ttu-id="15f23-152">Get-PackageSource cmdlet을 사용 하 여 사용 가능한 패키지 원본 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-152">You can get a list of available package sources by using the Get-PackageSource cmdlet.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="15f23-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="15f23-153">CommonParameters</span></span>

<span data-ttu-id="15f23-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="15f23-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="15f23-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15f23-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="15f23-156">입력</span><span class="sxs-lookup"><span data-stu-id="15f23-156">INPUTS</span></span>

## <span data-ttu-id="15f23-157">출력</span><span class="sxs-lookup"><span data-stu-id="15f23-157">OUTPUTS</span></span>

### <span data-ttu-id="15f23-158">Microsoft PackageManagement. 패키지 Id</span><span class="sxs-lookup"><span data-stu-id="15f23-158">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="15f23-159">이 cmdlet은 **\Id** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-159">This cmdlet returns a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="15f23-160">**Install-packageprovider** 의 결과를 설치 하기 위해 **\Id** 개체를 **install-packageprovider** 에 파이프 하 여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-160">A **SoftwareIdentity** object can be piped into **Install-PackageProvider** to install the results of **Find-PackageProvider**.</span></span>

## <span data-ttu-id="15f23-161">참고</span><span class="sxs-lookup"><span data-stu-id="15f23-161">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="15f23-162">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-162">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="15f23-163">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-163">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="15f23-164">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="15f23-164">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="15f23-165">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="15f23-165">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="15f23-166">관련 링크</span><span class="sxs-lookup"><span data-stu-id="15f23-166">RELATED LINKS</span></span>

[<span data-ttu-id="15f23-167">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="15f23-167">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="15f23-168">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="15f23-168">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="15f23-169">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="15f23-169">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="15f23-170">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="15f23-170">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="15f23-171">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="15f23-171">Install-PackageProvider</span></span>](Install-PackageProvider.md)
