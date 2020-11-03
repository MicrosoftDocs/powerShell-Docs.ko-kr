---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 9d62706d5788f1ae2c97da4bf1f6143eed2ad8f9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213217"
---
# <span data-ttu-id="36238-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="36238-103">Find-DscResource</span></span>

## <span data-ttu-id="36238-104">개요</span><span class="sxs-lookup"><span data-stu-id="36238-104">SYNOPSIS</span></span>
<span data-ttu-id="36238-105">DSC (필요한 상태 구성) 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-105">Finds Desired State Configuration (DSC) resources.</span></span>

## <span data-ttu-id="36238-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="36238-106">SYNTAX</span></span>

### <span data-ttu-id="36238-107">모두</span><span class="sxs-lookup"><span data-stu-id="36238-107">All</span></span>

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="36238-108">설명</span><span class="sxs-lookup"><span data-stu-id="36238-108">DESCRIPTION</span></span>

<span data-ttu-id="36238-109">`Find-DscResource`Cmdlet은 모듈에 포함 된 DSC 리소스를 찾기 위해 등록 된 리포지토리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-109">The `Find-DscResource` cmdlet searches registered repositories to find DSC resources contained in modules.</span></span> <span data-ttu-id="36238-110">기본적으로는 `Find-DscResource` 등록 된 모든 리포지토리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-110">By default `Find-DscResource` searches all registered repositories.</span></span>

<span data-ttu-id="36238-111">에서 찾은 각 모듈에 대해 `Find-DscResource` **Psgetdscresourceinfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36238-111">For each module found by `Find-DscResource`, a **PSGetDscResourceInfo** object is returned.</span></span>
<span data-ttu-id="36238-112">**Psgetdscresourceinfo** 개체를 파이프라인에서 cmdlet으로 보낼 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="36238-112">**PSGetDscResourceInfo** objects can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="36238-113">`Install-Module` 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-113">`Install-Module` installs the module.</span></span>

## <span data-ttu-id="36238-114">예제</span><span class="sxs-lookup"><span data-stu-id="36238-114">EXAMPLES</span></span>

### <span data-ttu-id="36238-115">예 1: 모든 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="36238-115">Example 1: Find all DSC resources</span></span>

<span data-ttu-id="36238-116">`Find-DscResource` 등록 된 리포지토리에서 DSC 리소스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-116">`Find-DscResource` returns DSC resources from registered repositories.</span></span> <span data-ttu-id="36238-117">특정 리포지토리를 검색 하려면 **리포지토리** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-117">To search a specific repository, use the **Repository** parameter.</span></span>

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

### <span data-ttu-id="36238-118">예제 2: 이름별로 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="36238-118">Example 2: Find a DSC resource by name</span></span>

<span data-ttu-id="36238-119">`Find-DscResource` 이름별로 DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-119">`Find-DscResource` locates DSC resources by name.</span></span> <span data-ttu-id="36238-120">리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-120">Use commas to separate an array of resource names.</span></span>

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

<span data-ttu-id="36238-121">`Find-DscResource`**Name** 매개 변수를 사용 하 여 DSC 리소스의 지정 된 배열을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-121">`Find-DscResource` uses the **Name** parameter to find the specified array of DSC resources.</span></span>

### <span data-ttu-id="36238-122">예 3: DSC 리소스 찾기 및 설치</span><span class="sxs-lookup"><span data-stu-id="36238-122">Example 3: Find a DSC resource and install it</span></span>

<span data-ttu-id="36238-123">`Find-DscResource` DSC 리소스를 찾아서 설치할 파이프라인에서 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="36238-123">`Find-DscResource` locates a DSC resource and sends the object down the pipeline to be installed.</span></span>
<span data-ttu-id="36238-124">설치 후 `Get-InstalledModule` 에는를 사용 하 여 결과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-124">After the installation, use `Get-InstalledModule` to view the results.</span></span>

<span data-ttu-id="36238-125">동일한 모듈의 여러 리소스를 파이프라인에서로 보낼 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="36238-125">Multiple resources from the same module can be sent down the pipeline to the `Install-Module`.</span></span>
<span data-ttu-id="36238-126">`Install-Module` 모듈을 한 번만 설치 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-126">`Install-Module` attempts to only install the module once.</span></span>

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

<span data-ttu-id="36238-127">`Find-DscResource`**Name** 매개 변수를 사용 하 여 **xwebsite** 라는 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-127">`Find-DscResource` uses the **Name** parameter to find the resource named **xWebsite** .</span></span> <span data-ttu-id="36238-128">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="36238-128">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="36238-129">`Install-Module` 리소스에 대 한 **Xwebadministration** 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-129">`Install-Module` installs the **xWebAdministration** module for the resource.</span></span>

### <span data-ttu-id="36238-130">예제 4: 모듈의 모든 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="36238-130">Example 4: Find all DSC resources in a module</span></span>

<span data-ttu-id="36238-131">`Find-DscResource` 지정 된 모듈에 포함 된 모든 DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-131">`Find-DscResource` finds all the DSC resources contained in a specified module.</span></span> <span data-ttu-id="36238-132">기본적으로 현재 버전이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36238-132">By default, the current version is displayed.</span></span> <span data-ttu-id="36238-133">다른 버전을 표시 하려면 **allversions)** 또는 **requiredversions** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-133">To display other versions, use the **AllVersions** or **RequiredVersions** parameters.</span></span>

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

<span data-ttu-id="36238-134">`Find-DscResource`**ModuleName** 매개 변수를 사용 하 여 **xwebadministration** 를 지정 하 고 모듈에 포함 된 DSC 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-134">`Find-DscResource` uses the **ModuleName** parameter to specify the **xWebAdministration** and find the DSC resources contained in the module.</span></span> <span data-ttu-id="36238-135">각 리소스의 현재 버전이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="36238-135">The current version of each resource is displayed.</span></span>

### <span data-ttu-id="36238-136">예 5: 태그 및 필요한 버전으로 DSC 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="36238-136">Example 5: Find a DSC resource by tag and required version</span></span>

<span data-ttu-id="36238-137">DSC 리소스는 parameters **태그** 및 **RequiredVersion** 을 사용 하 여 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-137">DSC resources can be located using the parameters **Tag** and **RequiredVersion** .</span></span> <span data-ttu-id="36238-138">**태그** 리포지토리에 지정 된 태그를 포함 하는 모든 리소스의 현재 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-138">**Tag** displays the current version of every resource that contains the specified tag in the repository.</span></span>
<span data-ttu-id="36238-139">**RequiredVersion** 은 **ModuleName** 매개 변수를 요구 하 고 **Name** 매개 변수는 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="36238-139">**RequiredVersion** needs the **ModuleName** parameter and the **Name** parameter is optional.</span></span> <span data-ttu-id="36238-140">**Name** 및 **ModuleName** 매개 변수는 출력을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-140">The **Name** and **ModuleName** parameters limit the output.</span></span> <span data-ttu-id="36238-141">**Allversions)** 매개 변수를 사용 하 여 DSC 리소스의 사용 가능한 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-141">Use the **AllVersions** parameter to display a DSC resource's available versions.</span></span>

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

### <span data-ttu-id="36238-142">예제 6: 필터를 사용 하 여 리소스 찾기</span><span class="sxs-lookup"><span data-stu-id="36238-142">Example 6: Find a resource by using a filter</span></span>

<span data-ttu-id="36238-143">`Find-DscResource` 모든 리소스를 찾은 다음 **필터** 매개 변수를 사용 하 여 **도메인별** 결과를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-143">`Find-DscResource` finds all resources and uses the **Filter** parameter to specify the results by **Domain** .</span></span> <span data-ttu-id="36238-144">**Filter** 매개 변수는 개체의 설명 또는 모듈 이름에서 필터 값을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-144">The **Filter** parameter finds the filter value in the object's description or module name.</span></span> <span data-ttu-id="36238-145">Cmdlet을 사용 `Select-Object` 하 여 개체의 속성을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-145">Use the `Select-Object` cmdlet to view an object's properties.</span></span>

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

## <span data-ttu-id="36238-146">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="36238-146">PARAMETERS</span></span>

### <span data-ttu-id="36238-147">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="36238-147">-AllowPrerelease</span></span>

<span data-ttu-id="36238-148">결과에서 시험판으로 표시 된 리소스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-148">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="36238-149">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="36238-149">-AllVersions</span></span>

<span data-ttu-id="36238-150">**Allversions)** 매개 변수는 각 DSC 리소스의 사용 가능한 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-150">The **AllVersions** parameter displays each of a DSC resource's available versions.</span></span> <span data-ttu-id="36238-151">**Allversions)** 매개 변수는 **MinimumVersion** , **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-151">You can't use the **AllVersions** parameter with the **MinimumVersion** , **MaximumVersion** , or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="36238-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="36238-152">-Filter</span></span>

<span data-ttu-id="36238-153">**PackageManagement** 공급자의 검색 구문에 따라 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-153">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="36238-154">예를 들어 **ModuleName** 및 **Description** 속성 내에서 검색할 단어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-154">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="36238-155">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="36238-155">-MaximumVersion</span></span>

<span data-ttu-id="36238-156">결과에 포함할 리소스의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-156">Specifies the maximum version of the resource to include in results.</span></span> <span data-ttu-id="36238-157">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-157">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="36238-158">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="36238-158">-MinimumVersion</span></span>

<span data-ttu-id="36238-159">결과에 포함할 리소스의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-159">Specifies the minimum version of the resource to include in results.</span></span> <span data-ttu-id="36238-160">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-160">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="36238-161">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="36238-161">-ModuleName</span></span>

<span data-ttu-id="36238-162">DSC 리소스를 포함 하는 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-162">Specifies a module that contains the DSC resource.</span></span>

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

### <span data-ttu-id="36238-163">-Name</span><span class="sxs-lookup"><span data-stu-id="36238-163">-Name</span></span>

<span data-ttu-id="36238-164">리소스의 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-164">Specifies the name of a resource.</span></span> <span data-ttu-id="36238-165">기본값은 모든 리소스입니다.</span><span class="sxs-lookup"><span data-stu-id="36238-165">The default is all resources.</span></span> <span data-ttu-id="36238-166">리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-166">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="36238-167">-프록시</span><span class="sxs-lookup"><span data-stu-id="36238-167">-Proxy</span></span>

<span data-ttu-id="36238-168">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-168">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="36238-169">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="36238-169">-ProxyCredential</span></span>

<span data-ttu-id="36238-170">**Proxy** 매개 변수에 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-170">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="36238-171">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="36238-171">-Repository</span></span>

<span data-ttu-id="36238-172">리소스를 검색할 리포지토리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-172">Specifies a repository to search for resources.</span></span> <span data-ttu-id="36238-173">저장소 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-173">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="36238-174">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="36238-174">-RequiredVersion</span></span>

<span data-ttu-id="36238-175">결과에 포함할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-175">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="36238-176">**RequiredVersion** 및 **MinimumVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="36238-176">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="36238-177">-Tag</span><span class="sxs-lookup"><span data-stu-id="36238-177">-Tag</span></span>

<span data-ttu-id="36238-178">리포지토리의 모듈을 범주화 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-178">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="36238-179">태그 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-179">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="36238-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="36238-180">CommonParameters</span></span>

<span data-ttu-id="36238-181">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="36238-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="36238-182">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="36238-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="36238-183">입력</span><span class="sxs-lookup"><span data-stu-id="36238-183">INPUTS</span></span>

## <span data-ttu-id="36238-184">출력</span><span class="sxs-lookup"><span data-stu-id="36238-184">OUTPUTS</span></span>

### <span data-ttu-id="36238-185">PSGetDscResourceInfo</span><span class="sxs-lookup"><span data-stu-id="36238-185">PSGetDscResourceInfo</span></span>

<span data-ttu-id="36238-186">`Find-DscResource`**Psgetdscresourceinfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="36238-186">`Find-DscResource` returns a **PSGetDscResourceInfo** object.</span></span>

## <span data-ttu-id="36238-187">참고</span><span class="sxs-lookup"><span data-stu-id="36238-187">NOTES</span></span>

## <span data-ttu-id="36238-188">관련 링크</span><span class="sxs-lookup"><span data-stu-id="36238-188">RELATED LINKS</span></span>

[<span data-ttu-id="36238-189">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="36238-189">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="36238-190">Install-Module</span><span class="sxs-lookup"><span data-stu-id="36238-190">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="36238-191">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="36238-191">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="36238-192">Select-Object</span><span class="sxs-lookup"><span data-stu-id="36238-192">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="36238-193">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="36238-193">Uninstall-Module</span></span>](Uninstall-Module.md)
