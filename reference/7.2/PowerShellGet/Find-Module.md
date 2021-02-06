---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: f9cba90ffa69d04df196f4062c8f190d545b9bc3
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99600831"
---
# <span data-ttu-id="280d3-102">Find-Module</span><span class="sxs-lookup"><span data-stu-id="280d3-102">Find-Module</span></span>

## <span data-ttu-id="280d3-103">개요</span><span class="sxs-lookup"><span data-stu-id="280d3-103">SYNOPSIS</span></span>
<span data-ttu-id="280d3-104">리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-104">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="280d3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="280d3-105">SYNTAX</span></span>

### <span data-ttu-id="280d3-106">모두</span><span class="sxs-lookup"><span data-stu-id="280d3-106">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="280d3-107">설명</span><span class="sxs-lookup"><span data-stu-id="280d3-107">DESCRIPTION</span></span>

<span data-ttu-id="280d3-108">`Find-Module`Cmdlet은 리포지토리에서 지정 된 조건과 일치 하는 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-108">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="280d3-109">`Find-Module` 찾은 각 모듈에 대해 **PSRepositoryItemInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-109">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="280d3-110">개체는와 같은 cmdlet에 파이프라인으로 전송 될 수 있습니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="280d3-110">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="280d3-111">처음으로 `Find-Module` 리포지토리를 사용 하려고 시도 하면 업데이트를 설치 하 라는 메시지가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-111">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="280d3-112">리포지토리 원본이 cmdlet에 등록 되지 않은 경우 `Register-PSRepository` 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-112">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="280d3-113">`Find-Module` 버전을 제한 하는 매개 변수를 사용 하지 않는 경우 최신 버전의 모듈을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-113">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="280d3-114">리포지토리의 모듈 버전 목록을 가져오려면 **allversions)** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-114">To get a repository's list of a module's versions, use the parameter **AllVersions**.</span></span>

<span data-ttu-id="280d3-115">**MinimumVersion** 매개 변수를 지정 하는 경우는 `Find-Module` 최소 보다 크거나 같은 모듈 버전을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-115">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="280d3-116">리포지토리에 사용할 수 있는 최신 버전이 있으면 최신 버전이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-116">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="280d3-117">**MaximumVersion** 매개 변수가 지정 된 경우는 `Find-Module` 지정 된 버전을 초과 하지 않는 모듈의 최신 버전을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-117">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="280d3-118">**RequiredVersion** 매개 변수를 지정 하면는 `Find-Module` 지정 된 버전과 정확히 일치 하는 모듈 버전만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-118">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="280d3-119">`Find-Module` 원본 간의 이름 충돌이 발생할 수 있으므로 사용 가능한 모든 모듈을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-119">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="280d3-120">다음 예에서는 [PowerShell 갤러리](https://www.powershellgallery.com/) 를 등록 된 유일한 리포지토리로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-120">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="280d3-121">`Get-PSRepository` 등록 된 리포지토리를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-121">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="280d3-122">등록 된 리포지토리가 여러 개 있는 경우 `-Repository` 매개 변수를 사용 하 여 리포지토리의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-122">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="280d3-123">예제</span><span class="sxs-lookup"><span data-stu-id="280d3-123">EXAMPLES</span></span>

### <span data-ttu-id="280d3-124">예제 1: 이름별로 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-124">Example 1: Find a module by name</span></span>

<span data-ttu-id="280d3-125">이 예에서는 기본 리포지토리에서 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-125">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="280d3-126">`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-126">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="280d3-127">예제 2: 비슷한 이름의 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-127">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="280d3-128">이 예제에서는 별표 ( `*` ) 와일드 카드를 사용 하 여 비슷한 이름의 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-128">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

<span data-ttu-id="280d3-129">`Find-Module`Cmdlet은 **Name** 매개 변수를 별표 () 와일드 카드와 함께 사용 하 여 `*` **PowerShell** 이 포함 된 모든 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-129">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell**.</span></span>

### <span data-ttu-id="280d3-130">예 3: 최소 버전 별로 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-130">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="280d3-131">이 예제에서는 모듈의 최소 버전을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-131">This example searches for a module's minimum version.</span></span> <span data-ttu-id="280d3-132">리포지토리에 최신 버전의 모듈이 포함 되어 있으면 최신 버전이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-132">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="280d3-133">`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-133">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="280d3-134">**MinimumVersion** 은 **1.6.5** 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-134">The **MinimumVersion** specifies version **1.6.5**.</span></span> <span data-ttu-id="280d3-135">`Find-Module` PowerShellGet 버전 **2.1.0** 가 최소 버전을 초과 하 고 최신 버전 이므로 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-135">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="280d3-136">예제 4: 특정 버전 별로 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-136">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="280d3-137">이 예제에서는 모듈의 특정 버전을 나타내는 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-137">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="280d3-138">지정 된 버전을 찾을 수 없는 경우 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-138">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="280d3-139">`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-139">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="280d3-140">**RequiredVersion** 매개 변수는 **1.6.5** 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-140">The **RequiredVersion** parameter specifies version **1.6.5**.</span></span>

### <span data-ttu-id="280d3-141">예 5: 특정 리포지토리에서 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-141">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="280d3-142">이 예에서는 **리포지토리** 매개 변수를 사용 하 여 특정 리포지토리의 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-142">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="280d3-143">`Find-Module`Cmdlet은 **Name** 매개 변수를 사용 하 여 **PowerShellGet** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-143">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="280d3-144">**리포지토리** 매개 변수는 **PSGallery** 리포지토리를 검색 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-144">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="280d3-145">예 6: 여러 리포지토리에서 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-145">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="280d3-146">이 예제에서는를 사용 하 여 `Register-PSRepository` 리포지토리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-146">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="280d3-147">`Find-Module` 리포지토리를 사용 하 여 모듈을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-147">`Find-Module` uses the repository to search for a module.</span></span>

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

<span data-ttu-id="280d3-148">`Register-PSRepository`Cmdlet은 새 리포지토리를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-148">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="280d3-149">**Name** 매개 변수는 **MySource** 이름을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-149">The **Name** parameter assigns the name **MySource**.</span></span> <span data-ttu-id="280d3-150">위치 **매개 변수** 는 리포지토리의 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-150">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="280d3-151">`Find-Module`Cmdlet은 **Name** 매개 변수와 별표 ( `*` ) 와일드 카드를 사용 하 여 **Contoso** 모듈을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-151">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="280d3-152">**리포지토리** 매개 변수는 **PSGallery** 및 **MySource** 라는 두 리포지토리를 검색 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-152">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource**.</span></span>

### <span data-ttu-id="280d3-153">예 7: DSC 리소스를 포함 하는 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-153">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="280d3-154">이 명령은 DSC 리소스를 포함 하는 모듈을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-154">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="280d3-155">**Include** 매개 변수에는 리포지토리를 검색 하는 데 사용 되는 4 가지 미리 정의 된 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-155">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="280d3-156">탭-전체를 사용 하 여 **include** 매개 변수에서 지 원하는 네 가지 기능을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-156">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

<span data-ttu-id="280d3-157">`Find-Module`이 cmdlet은 **리포지토리** 매개 변수를 사용 하 여 리포지토리 ( **PSGallery**)를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-157">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery**.</span></span>
<span data-ttu-id="280d3-158">**Include** 매개 변수는 매개 변수가 리포지토리에서 검색할 수 있는 기능인 **get-dscresource** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-158">The **Includes** parameter specifies **DscResource**, which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="280d3-159">예 8: 필터를 사용 하 여 모듈 찾기</span><span class="sxs-lookup"><span data-stu-id="280d3-159">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="280d3-160">이 예에서는 모듈을 찾기 위해 필터를 사용 하 여 리포지토리를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-160">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="280d3-161">NuGet 기반 리포지토리의 경우 **필터** 매개 변수는 인수에 대 한 이름, 설명 및 태그를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-161">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="280d3-162">`Find-Module`Cmdlet은 **필터** 매개 변수를 사용 하 여 저장소에서 **AppDomain** 을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-162">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain**.</span></span>

## <span data-ttu-id="280d3-163">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="280d3-163">PARAMETERS</span></span>

### <span data-ttu-id="280d3-164">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="280d3-164">-AllowPrerelease</span></span>

<span data-ttu-id="280d3-165">시험판으로 표시 된 결과 모듈에를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-165">Includes in the results modules marked as a pre-release.</span></span>

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

### <span data-ttu-id="280d3-166">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="280d3-166">-AllVersions</span></span>

<span data-ttu-id="280d3-167">모든 버전의 모듈을 결과에 포함 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-167">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="280d3-168">**Allversions)** 매개 변수는 **MinimumVersion**, **MaximumVersion** 또는 **RequiredVersion** 매개 변수와 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-168">You cannot use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="280d3-169">-Command</span><span class="sxs-lookup"><span data-stu-id="280d3-169">-Command</span></span>

<span data-ttu-id="280d3-170">모듈에서 찾을 명령의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-170">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="280d3-171">명령은 함수 또는 워크플로가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-171">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="280d3-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="280d3-172">-Credential</span></span>

<span data-ttu-id="280d3-173">지정 된 패키지 공급자 또는 원본에 대해 모듈을 설치할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-173">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="280d3-174">-Get-dscresource</span><span class="sxs-lookup"><span data-stu-id="280d3-174">-DscResource</span></span>

<span data-ttu-id="280d3-175">DSC 리소스를 포함 하는 모듈의 이름 또는 이름의 일부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-175">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="280d3-176">PowerShell 규칙에 따라는 여러 인수를 제공 하는 경우 **또는** 검색을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-176">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

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

### <span data-ttu-id="280d3-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="280d3-177">-Filter</span></span>

<span data-ttu-id="280d3-178">**PackageManagement** 공급자별 검색 구문을 기반으로 하는 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-178">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="280d3-179">NuGet 모듈의 경우이 매개 변수는 [PowerShell 갤러리](https://www.powershellgallery.com/) 웹 사이트의 검색 표시줄을 사용 하 여 검색 하는 것과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-179">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="280d3-180">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="280d3-180">-IncludeDependencies</span></span>

<span data-ttu-id="280d3-181">이 작업에 **Name** 매개 변수에 지정 된 모듈에 종속 된 모든 모듈이 포함 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-181">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="280d3-182">-포함</span><span class="sxs-lookup"><span data-stu-id="280d3-182">-Includes</span></span>

<span data-ttu-id="280d3-183">는 특정 종류의 PowerShell 기능을 포함 하는 모듈만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-183">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="280d3-184">예를 들어 **get-dscresource** 를 포함 하는 모듈만 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-184">For example, you might only want to find modules that include **DSCResource**.</span></span> <span data-ttu-id="280d3-185">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-185">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="280d3-186">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="280d3-186">Cmdlet</span></span>
- <span data-ttu-id="280d3-187">DscResource</span><span class="sxs-lookup"><span data-stu-id="280d3-187">DscResource</span></span>
- <span data-ttu-id="280d3-188">함수</span><span class="sxs-lookup"><span data-stu-id="280d3-188">Function</span></span>
- <span data-ttu-id="280d3-189">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="280d3-189">RoleCapability</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="280d3-190">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="280d3-190">-MaximumVersion</span></span>

<span data-ttu-id="280d3-191">검색 결과에 포함할 모듈의 최대 또는 최신 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-191">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="280d3-192">**MaximumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-192">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="280d3-193">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="280d3-193">-MinimumVersion</span></span>

<span data-ttu-id="280d3-194">결과에 포함할 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-194">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="280d3-195">**MinimumVersion** 및 **RequiredVersion** 은 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-195">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="280d3-196">-Name</span><span class="sxs-lookup"><span data-stu-id="280d3-196">-Name</span></span>

<span data-ttu-id="280d3-197">리포지토리에서 검색할 모듈의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-197">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="280d3-198">쉼표로 구분 된 모듈 이름 목록이 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-198">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="280d3-199">와일드 카드가 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-199">Wildcards are accepted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="280d3-200">-프록시</span><span class="sxs-lookup"><span data-stu-id="280d3-200">-Proxy</span></span>

<span data-ttu-id="280d3-201">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-201">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="280d3-202">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="280d3-202">-ProxyCredential</span></span>

<span data-ttu-id="280d3-203">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-203">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="280d3-204">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="280d3-204">-Repository</span></span>

<span data-ttu-id="280d3-205">**리포지토리** 매개 변수를 사용 하 여 모듈을 검색할 리포지토리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-205">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="280d3-206">여러 리포지토리를 등록할 때 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-206">Used when multiple repositories are registered.</span></span> <span data-ttu-id="280d3-207">쉼표로 구분 된 저장소 목록을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-207">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="280d3-208">리포지토리를 등록 하려면를 사용 `Register-PSRepository` 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-208">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="280d3-209">등록 된 리포지토리를 표시 하려면를 사용 `Get-PSRepository` 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-209">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="280d3-210">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="280d3-210">-RequiredVersion</span></span>

<span data-ttu-id="280d3-211">결과에 포함할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-211">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="280d3-212">**RequiredVersion** 은 **MinimumVersion** 또는 **MaximumVersion** 과 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-212">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="280d3-213">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="280d3-213">-RoleCapability</span></span>

<span data-ttu-id="280d3-214">역할 기능의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-214">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="280d3-215">-Tag</span><span class="sxs-lookup"><span data-stu-id="280d3-215">-Tag</span></span>

<span data-ttu-id="280d3-216">태그의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-216">Specifies an array of tags.</span></span> <span data-ttu-id="280d3-217">예제 태그에는 **DesiredStateConfiguration**, **DSC**, **Dscresourcekit** 또는 **psmodule** 이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-217">Example tags include **DesiredStateConfiguration**, **DSC**, **DSCResourceKit**, or **PSModule**.</span></span>

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

### <span data-ttu-id="280d3-218">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="280d3-218">CommonParameters</span></span>

<span data-ttu-id="280d3-219">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="280d3-219">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="280d3-220">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="280d3-220">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="280d3-221">입력</span><span class="sxs-lookup"><span data-stu-id="280d3-221">INPUTS</span></span>

### <span data-ttu-id="280d3-222">System.String[]</span><span class="sxs-lookup"><span data-stu-id="280d3-222">System.String[]</span></span>

### <span data-ttu-id="280d3-223">System.String</span><span class="sxs-lookup"><span data-stu-id="280d3-223">System.String</span></span>

### <span data-ttu-id="280d3-224">System.Uri</span><span class="sxs-lookup"><span data-stu-id="280d3-224">System.Uri</span></span>

### <span data-ttu-id="280d3-225">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="280d3-225">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="280d3-226">출력</span><span class="sxs-lookup"><span data-stu-id="280d3-226">OUTPUTS</span></span>

### <span data-ttu-id="280d3-227">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="280d3-227">PSRepositoryItemInfo</span></span>

<span data-ttu-id="280d3-228">`Find-Module` 와 같은 cmdlet에 파이프라인으로 전송할 수 있는 **PSRepositoryItemInfo** 개체를 만듭니다 `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="280d3-228">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="280d3-229">참고</span><span class="sxs-lookup"><span data-stu-id="280d3-229">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="280d3-230">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-230">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="280d3-231">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-231">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="280d3-232">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="280d3-232">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="280d3-233">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="280d3-233">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="280d3-234">관련 링크</span><span class="sxs-lookup"><span data-stu-id="280d3-234">RELATED LINKS</span></span>

[<span data-ttu-id="280d3-235">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="280d3-235">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="280d3-236">Install-Module</span><span class="sxs-lookup"><span data-stu-id="280d3-236">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="280d3-237">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="280d3-237">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="280d3-238">Save-Module</span><span class="sxs-lookup"><span data-stu-id="280d3-238">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="280d3-239">Uninstall-Module</span><span class="sxs-lookup"><span data-stu-id="280d3-239">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="280d3-240">Update-Module</span><span class="sxs-lookup"><span data-stu-id="280d3-240">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="280d3-241">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="280d3-241">Register-PSRepository</span></span>](Register-PSRepository.md)
