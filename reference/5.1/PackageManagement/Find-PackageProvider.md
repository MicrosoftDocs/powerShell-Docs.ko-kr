---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: dc4450e1c9f8b9506ee57948e4cec2d0541c181d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213346"
---
# <span data-ttu-id="05d35-103">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="05d35-103">Find-PackageProvider</span></span>

## <span data-ttu-id="05d35-104">개요</span><span class="sxs-lookup"><span data-stu-id="05d35-104">SYNOPSIS</span></span>
<span data-ttu-id="05d35-105">설치에 사용할 수 있는 패키지 관리 패키지 공급자 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-105">Returns a list of Package Management package providers available for installation.</span></span>

## <span data-ttu-id="05d35-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05d35-106">SYNTAX</span></span>

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="05d35-107">설명</span><span class="sxs-lookup"><span data-stu-id="05d35-107">DESCRIPTION</span></span>

<span data-ttu-id="05d35-108">**Install-packageprovider** Cmdlet은 PowerShellGet에 등록 된 패키지 소스에서 사용할 수 있는 일치 하는 PackageManagement 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-108">The **Find-PackageProvider** cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span>
<span data-ttu-id="05d35-109">이러한 패키지 공급자는 Install-PackageProvider cmdlet을 사용하여 설치에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-109">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span>
<span data-ttu-id="05d35-110">기본적으로 여기에는 **PackageManagement** 및 **공급자** 태그를 사용 하 여 PowerShell 갤러리에서 사용할 수 있는 모듈이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-110">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** and **Provider** tags.</span></span>

<span data-ttu-id="05d35-111">또한 **install-packageprovider** 는 패키지 관리 Azure Blob 저장소에서 사용할 수 있는 일치 하는 패키지 관리 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-111">**Find-PackageProvider** also finds matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="05d35-112">부트스트래퍼 공급자를 사용 하 여 찾아서 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-112">Use the bootstrapper provider to find and install them.</span></span>

## <span data-ttu-id="05d35-113">예제</span><span class="sxs-lookup"><span data-stu-id="05d35-113">EXAMPLES</span></span>

### <span data-ttu-id="05d35-114">예제 1: 사용 가능한 모든 패키지 공급자 찾기</span><span class="sxs-lookup"><span data-stu-id="05d35-114">Example 1: Find all available package providers</span></span>

```
PS C:\> Find-PackageProvider
```

<span data-ttu-id="05d35-115">이 명령은 패키지 관리에서 지 원하는 리포지토리에서 사용할 수 있는 모든 패키지 공급자 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-115">This command gets a list of all package providers that are available on the repositories supported by Package Management.</span></span>
<span data-ttu-id="05d35-116">이러한 패키지 공급자는 기본적으로 PowerShell 갤러리 및 패키지 관리 부트스트래핑 응용 프로그램을 사용 하 여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-116">By default, those package providers are available on the PowerShell Gallery and by using the Package Management bootstrapping application.</span></span>

### <span data-ttu-id="05d35-117">예제 2: 공급자의 모든 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="05d35-117">Example 2: Find all versions of a provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

<span data-ttu-id="05d35-118">이 명령은 Nuget 이라는 패키지 공급자의 모든 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-118">This command finds all versions of the package provider named Nuget.</span></span>

### <span data-ttu-id="05d35-119">예제 3: 지정 된 소스에서 공급자 찾기</span><span class="sxs-lookup"><span data-stu-id="05d35-119">Example 3: Find a provider from a specified source</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

<span data-ttu-id="05d35-120">이 명령은 지정 된 패키지 원본을 사용 하 여 사용할 수 있는 패키지 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-120">This command finds a package provider available by using a specified package source.</span></span>

## <span data-ttu-id="05d35-121">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="05d35-121">PARAMETERS</span></span>

### <span data-ttu-id="05d35-122">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="05d35-122">-AllVersions</span></span>

<span data-ttu-id="05d35-123">이 cmdlet은 패키지 공급자의 사용 가능한 모든 버전을 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-123">Indicates that this cmdlet returns all available versions of the package provider.</span></span>
<span data-ttu-id="05d35-124">기본적으로 **install-packageprovider** 는 사용 가능한 최신 버전만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-124">By default, **Find-PackageProvider** only returns the newest available version.</span></span>

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

### <span data-ttu-id="05d35-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="05d35-125">-Credential</span></span>

<span data-ttu-id="05d35-126">패키지 공급자를 검색할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-126">Specifies a user account that has permission to search for package providers.</span></span>

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

### <span data-ttu-id="05d35-127">-Force</span><span class="sxs-lookup"><span data-stu-id="05d35-127">-Force</span></span>

<span data-ttu-id="05d35-128">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-128">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="05d35-129">현재는 *Forcebootstrap* 매개 변수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-129">Currently, this is equivalent to the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="05d35-130">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="05d35-130">-ForceBootstrap</span></span>

<span data-ttu-id="05d35-131">이 cmdlet이 패키지 관리 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-131">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="05d35-132">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="05d35-132">-IncludeDependencies</span></span>

<span data-ttu-id="05d35-133">이 cmdlet에 종속성이 포함 되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-133">Indicates that this cmdlet includes dependencies.</span></span>

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

### <span data-ttu-id="05d35-134">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="05d35-134">-MaximumVersion</span></span>

<span data-ttu-id="05d35-135">검색 하려는 패키지 공급자의 최대 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-135">Specifies the maximum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="05d35-136">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 에서 사용 가능한 가장 높은 버전의 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-136">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider.</span></span>

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

### <span data-ttu-id="05d35-137">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="05d35-137">-MinimumVersion</span></span>

<span data-ttu-id="05d35-138">검색 하려는 패키지 공급자의 최소 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-138">Specifies the minimum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="05d35-139">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 지정 버전을 만족 하는 패키지의 사용 가능한 가장 높은 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-139">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="05d35-140">-Name</span><span class="sxs-lookup"><span data-stu-id="05d35-140">-Name</span></span>

<span data-ttu-id="05d35-141">하나 이상의 패키지 공급자 모듈 이름 또는 와일드 카드 문자를 포함 하는 공급자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-141">Specifies one or more package provider module names, or provider names with wildcard characters.</span></span>
<span data-ttu-id="05d35-142">여러 패키지 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-142">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="05d35-143">-프록시</span><span class="sxs-lookup"><span data-stu-id="05d35-143">-Proxy</span></span>

<span data-ttu-id="05d35-144">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-144">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="05d35-145">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="05d35-145">-ProxyCredential</span></span>

<span data-ttu-id="05d35-146">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-146">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="05d35-147">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="05d35-147">-RequiredVersion</span></span>

<span data-ttu-id="05d35-148">찾으려는 패키지 공급자의 정확한 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-148">Specifies the exact allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="05d35-149">이 매개 변수를 추가 하지 않으면 **install-packageprovider** 는 *MaximumVersion* 매개 변수로 지정 된 최대 버전을 충족 하는 사용 가능한 가장 높은 버전의 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-149">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="05d35-150">-Source</span><span class="sxs-lookup"><span data-stu-id="05d35-150">-Source</span></span>

<span data-ttu-id="05d35-151">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-151">Specifies one or more package sources.</span></span>
<span data-ttu-id="05d35-152">Get-PackageSource cmdlet을 사용 하 여 사용 가능한 패키지 원본 목록을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-152">You can get a list of available package sources by using the Get-PackageSource cmdlet.</span></span>

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

### <span data-ttu-id="05d35-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05d35-153">CommonParameters</span></span>

<span data-ttu-id="05d35-154">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="05d35-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05d35-155">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05d35-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="05d35-156">입력</span><span class="sxs-lookup"><span data-stu-id="05d35-156">INPUTS</span></span>

## <span data-ttu-id="05d35-157">출력</span><span class="sxs-lookup"><span data-stu-id="05d35-157">OUTPUTS</span></span>

### <span data-ttu-id="05d35-158">Microsoft PackageManagement. 패키지 Id</span><span class="sxs-lookup"><span data-stu-id="05d35-158">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="05d35-159">이 cmdlet은 **\Id** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-159">This cmdlet returns a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="05d35-160">**Install-packageprovider** 의 결과를 설치 하기 위해 **\Id** 개체를 **install-packageprovider** 에 파이프 하 여 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05d35-160">A **SoftwareIdentity** object can be piped into **Install-PackageProvider** to install the results of **Find-PackageProvider** .</span></span>

## <span data-ttu-id="05d35-161">참고</span><span class="sxs-lookup"><span data-stu-id="05d35-161">NOTES</span></span>

## <span data-ttu-id="05d35-162">관련 링크</span><span class="sxs-lookup"><span data-stu-id="05d35-162">RELATED LINKS</span></span>

[<span data-ttu-id="05d35-163">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="05d35-163">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="05d35-164">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="05d35-164">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="05d35-165">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="05d35-165">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="05d35-166">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="05d35-166">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="05d35-167">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="05d35-167">Install-PackageProvider</span></span>](Install-PackageProvider.md)
