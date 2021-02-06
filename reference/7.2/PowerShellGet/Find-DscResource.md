---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: e1cb814d349d6b77885ebaaf176a7c3153d93eb5
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99603070"
---
# <span data-ttu-id="a9655-102">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="a9655-102">Find-DscResource</span></span>

## <span data-ttu-id="a9655-103">개요</span><span class="sxs-lookup"><span data-stu-id="a9655-103">SYNOPSIS</span></span>
<span data-ttu-id="a9655-104">DSC (필요한 상태 구성) 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-104">Finds Desired State Configuration (DSC) resources.</span></span>

## <span data-ttu-id="a9655-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9655-105">SYNTAX</span></span>

### <span data-ttu-id="a9655-106">모두</span><span class="sxs-lookup"><span data-stu-id="a9655-106">All</span></span>

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="a9655-107">설명</span><span class="sxs-lookup"><span data-stu-id="a9655-107">DESCRIPTION</span></span>

<span data-ttu-id="a9655-108">`Find-DscResource`Cmdlet은 모듈에 포함 된 DSC 리소스를 찾기 위해 등록 된 리포지토리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-108">The `Find-DscResource` cmdlet searches registered repositories to find DSC resources contained in modules.</span></span> <span data-ttu-id="a9655-109">기본적으로는 `Find-DscResource` 등록 된 모든 리포지토리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-109">By default `Find-DscResource` searches all registered repositories.</span></span>

<span data-ttu-id="a9655-110">에서 찾은 각 모듈에 대해 `Find-DscResource` **Psgetdscresourceinfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-110">For each module found by `Find-DscResource`, a **PSGetDscResourceInfo** object is returned.</span></span>
<span data-ttu-id="a9655-111">**Psgetdscresourceinfo** 개체를 파이프라인에서 cmdlet으로 보낼 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="a9655-111">**PSGetDscResourceInfo** objects can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="a9655-112">`Install-Module` 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-112">`Install-Module` installs the module.</span></span>

## <span data-ttu-id="a9655-113">예제</span><span class="sxs-lookup"><span data-stu-id="a9655-113">EXAMPLES</span></span>

### <span data-ttu-id="a9655-114">예 1: 모든 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="a9655-114">Example 1: Find all DSC resources</span></span>

<span data-ttu-id="a9655-115">`Find-DscResource` 등록 된 리포지토리에서 DSC 리소스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-115">`Find-DscResource` returns DSC resources from registered repositories.</span></span> <span data-ttu-id="a9655-116">특정 리포지토리를 검색 하려면 **리포지토리** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-116">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### <span data-ttu-id="a9655-117">예제 2: 이름별로 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="a9655-117">Example 2: Find a DSC resource by name</span></span>

<span data-ttu-id="a9655-118">`Find-DscResource` 이름별로 DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-118">`Find-DscResource` locates DSC resources by name.</span></span> <span data-ttu-id="a9655-119">리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-119">Use commas to separate an array of resource names.</span></span>

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

<span data-ttu-id="a9655-120">`Find-DscResource`**Name** 매개 변수를 사용 하 여 DSC 리소스의 지정 된 배열을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-120">`Find-DscResource` uses the **Name** parameter to find the specified array of DSC resources.</span></span>

### <span data-ttu-id="a9655-121">예 3: DSC 리소스 찾기 및 설치</span><span class="sxs-lookup"><span data-stu-id="a9655-121">Example 3: Find a DSC resource and install it</span></span>

<span data-ttu-id="a9655-122">`Find-DscResource` DSC 리소스를 찾아서 설치할 파이프라인에서 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-122">`Find-DscResource` locates a DSC resource and sends the object down the pipeline to be installed.</span></span>
<span data-ttu-id="a9655-123">설치 후 `Get-InstalledModule` 에는를 사용 하 여 결과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-123">After the installation, use `Get-InstalledModule` to view the results.</span></span>

<span data-ttu-id="a9655-124">동일한 모듈의 여러 리소스를 파이프라인에서로 보낼 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="a9655-124">Multiple resources from the same module can be sent down the pipeline to the `Install-Module`.</span></span>
<span data-ttu-id="a9655-125">`Install-Module` 모듈을 한 번만 설치 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-125">`Install-Module` attempts to only install the module once.</span></span>

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

<span data-ttu-id="a9655-126">`Find-DscResource`**Name** 매개 변수를 사용 하 여 **xwebsite** 라는 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-126">`Find-DscResource` uses the **Name** parameter to find the resource named **xWebsite**.</span></span> <span data-ttu-id="a9655-127">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="a9655-127">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="a9655-128">`Install-Module` 리소스에 대 한 **Xwebadministration** 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-128">`Install-Module` installs the **xWebAdministration** module for the resource.</span></span>

### <span data-ttu-id="a9655-129">예제 4: 모듈의 모든 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="a9655-129">Example 4: Find all DSC resources in a module</span></span>

<span data-ttu-id="a9655-130">`Find-DscResource` 지정 된 모듈에 포함 된 모든 DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-130">`Find-DscResource` finds all the DSC resources contained in a specified module.</span></span> <span data-ttu-id="a9655-131">기본적으로 현재 버전이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-131">By default, the current version is displayed.</span></span> <span data-ttu-id="a9655-132">다른 버전을 표시 하려면 **allversions)** 또는 **requiredversions** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-132">To display other versions, use the **AllVersions** or **RequiredVersions** parameters.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

<span data-ttu-id="a9655-133">`Find-DscResource`**ModuleName** 매개 변수를 사용 하 여 **xwebadministration** 를 지정 하 고 모듈에 포함 된 DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-133">`Find-DscResource` uses the **ModuleName** parameter to specify the **xWebAdministration** and find the DSC resources contained in the module.</span></span> <span data-ttu-id="a9655-134">각 리소스의 현재 버전이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-134">The current version of each resource is displayed.</span></span>

### <span data-ttu-id="a9655-135">예 5: 태그 및 필요한 버전으로 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="a9655-135">Example 5: Find a DSC resource by tag and required version</span></span>

<span data-ttu-id="a9655-136">DSC 리소스는 parameters **태그** 및 **RequiredVersion** 을 사용 하 여 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-136">DSC resources can be located using the parameters **Tag** and **RequiredVersion**.</span></span> <span data-ttu-id="a9655-137">**태그** 리포지토리에 지정 된 태그를 포함 하는 모든 리소스의 현재 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-137">**Tag** displays the current version of every resource that contains the specified tag in the repository.</span></span>
<span data-ttu-id="a9655-138">**RequiredVersion** 은 **ModuleName** 매개 변수를 요구 하 고 **Name** 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-138">**RequiredVersion** needs the **ModuleName** parameter and the **Name** parameter is optional.</span></span> <span data-ttu-id="a9655-139">**Name** 및 **ModuleName** 매개 변수는 출력을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-139">The **Name** and **ModuleName** parameters limit the output.</span></span> <span data-ttu-id="a9655-140">**Allversions)** 매개 변수를 사용 하 여 DSC 리소스의 사용 가능한 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-140">Use the **AllVersions** parameter to display a DSC resource's available versions.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### <span data-ttu-id="a9655-141">예제 6: 필터를 사용 하 여 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="a9655-141">Example 6: Find a resource by using a filter</span></span>

<span data-ttu-id="a9655-142">`Find-DscResource` 모든 리소스를 찾은 다음 **필터** 매개 변수를 사용 하 여 **도메인별** 결과를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-142">`Find-DscResource` finds all resources and uses the **Filter** parameter to specify the results by **Domain**.</span></span> <span data-ttu-id="a9655-143">**Filter** 매개 변수는 개체의 설명 또는 모듈 이름에서 필터 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-143">The **Filter** parameter finds the filter value in the object's description or module name.</span></span> <span data-ttu-id="a9655-144">Cmdlet을 사용 `Select-Object` 하 여 개체의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-144">Use the `Select-Object` cmdlet to view an object's properties.</span></span>

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## <span data-ttu-id="a9655-145">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="a9655-145">PARAMETERS</span></span>

### <span data-ttu-id="a9655-146">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="a9655-146">-AllowPrerelease</span></span>

<span data-ttu-id="a9655-147">결과에서 시험판으로 표시 된 리소스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-147">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="a9655-148">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="a9655-148">-AllVersions</span></span>

<span data-ttu-id="a9655-149">**Allversions)** 매개 변수는 각 DSC 리소스의 사용 가능한 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-149">The **AllVersions** parameter displays each of a DSC resource's available versions.</span></span> <span data-ttu-id="a9655-150">**Allversions)** 매개 변수는 **MinimumVersion**, **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-150">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="a9655-151">-Filter</span><span class="sxs-lookup"><span data-stu-id="a9655-151">-Filter</span></span>

<span data-ttu-id="a9655-152">**PackageManagement** 공급자의 검색 구문에 따라 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-152">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="a9655-153">예를 들어 **ModuleName** 및 **Description** 속성 내에서 검색할 단어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-153">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="a9655-154">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="a9655-154">-MaximumVersion</span></span>

<span data-ttu-id="a9655-155">결과에 포함할 리소스의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-155">Specifies the maximum version of the resource to include in results.</span></span> <span data-ttu-id="a9655-156">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-156">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a9655-157">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="a9655-157">-MinimumVersion</span></span>

<span data-ttu-id="a9655-158">결과에 포함할 리소스의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-158">Specifies the minimum version of the resource to include in results.</span></span> <span data-ttu-id="a9655-159">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-159">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a9655-160">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="a9655-160">-ModuleName</span></span>

<span data-ttu-id="a9655-161">DSC 리소스를 포함 하는 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-161">Specifies a module that contains the DSC resource.</span></span>

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

### <span data-ttu-id="a9655-162">-Name</span><span class="sxs-lookup"><span data-stu-id="a9655-162">-Name</span></span>

<span data-ttu-id="a9655-163">리소스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-163">Specifies the name of a resource.</span></span> <span data-ttu-id="a9655-164">기본값은 모든 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-164">The default is all resources.</span></span> <span data-ttu-id="a9655-165">리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-165">Use commas to separate an array of resource names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9655-166">-프록시</span><span class="sxs-lookup"><span data-stu-id="a9655-166">-Proxy</span></span>

<span data-ttu-id="a9655-167">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-167">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9655-168">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a9655-168">-ProxyCredential</span></span>

<span data-ttu-id="a9655-169">**Proxy** 매개 변수에 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-169">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9655-170">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="a9655-170">-Repository</span></span>

<span data-ttu-id="a9655-171">리소스를 검색할 리포지토리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-171">Specifies a repository to search for resources.</span></span> <span data-ttu-id="a9655-172">저장소 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-172">Use commas to separate an array of repository names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9655-173">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="a9655-173">-RequiredVersion</span></span>

<span data-ttu-id="a9655-174">결과에 포함할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-174">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="a9655-175">**RequiredVersion** 및 **MinimumVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-175">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="a9655-176">-Tag</span><span class="sxs-lookup"><span data-stu-id="a9655-176">-Tag</span></span>

<span data-ttu-id="a9655-177">리포지토리의 모듈을 범주화 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-177">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="a9655-178">태그 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-178">Use commas to separate an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9655-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9655-179">CommonParameters</span></span>

<span data-ttu-id="a9655-180">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a9655-180">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9655-181">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9655-181">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9655-182">입력</span><span class="sxs-lookup"><span data-stu-id="a9655-182">INPUTS</span></span>

## <span data-ttu-id="a9655-183">출력</span><span class="sxs-lookup"><span data-stu-id="a9655-183">OUTPUTS</span></span>

### <span data-ttu-id="a9655-184">PSGetDscResourceInfo</span><span class="sxs-lookup"><span data-stu-id="a9655-184">PSGetDscResourceInfo</span></span>

<span data-ttu-id="a9655-185">`Find-DscResource`**Psgetdscresourceinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-185">`Find-DscResource` returns a **PSGetDscResourceInfo** object.</span></span>

## <span data-ttu-id="a9655-186">참고</span><span class="sxs-lookup"><span data-stu-id="a9655-186">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9655-187">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-187">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="a9655-188">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-188">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="a9655-189">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a9655-189">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="a9655-190">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a9655-190">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="a9655-191">관련 링크</span><span class="sxs-lookup"><span data-stu-id="a9655-191">RELATED LINKS</span></span>

[<span data-ttu-id="a9655-192">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="a9655-192">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="a9655-193">Install-Module</span><span class="sxs-lookup"><span data-stu-id="a9655-193">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="a9655-194">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="a9655-194">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="a9655-195">Select-Object</span><span class="sxs-lookup"><span data-stu-id="a9655-195">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="a9655-196">제거 모듈</span><span class="sxs-lookup"><span data-stu-id="a9655-196">Uninstall-Module</span></span>](Uninstall-Module.md)
