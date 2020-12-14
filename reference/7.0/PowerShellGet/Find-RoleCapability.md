---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: 1cee4ac54bf83d387f61a4842104a80512a8b223
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891527"
---
# <span data-ttu-id="64992-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="64992-103">Find-RoleCapability</span></span>

## <span data-ttu-id="64992-104">개요</span><span class="sxs-lookup"><span data-stu-id="64992-104">SYNOPSIS</span></span>
<span data-ttu-id="64992-105">모듈에서 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-105">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="64992-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="64992-106">SYNTAX</span></span>

### <span data-ttu-id="64992-107">모두</span><span class="sxs-lookup"><span data-stu-id="64992-107">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="64992-108">설명</span><span class="sxs-lookup"><span data-stu-id="64992-108">DESCRIPTION</span></span>

<span data-ttu-id="64992-109">`Find-RoleCapability`Cmdlet은 등록 된 리포지토리를 검색 하 여 PowerShell 역할 기능 및 모듈을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-109">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="64992-110">에서 찾은 각 역할 기능에 대해 `Find-RoleCapability` **PSGetRoleCapabilityInfo** 개체가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64992-110">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="64992-111">**PSGetRoleCapabilityInfo** 개체는 파이프라인에서 또는 cmdlet으로 보낼 수 `Install-Module` 있습니다 `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="64992-111">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="64992-112">PowerShell 역할 기능은 충분 한 관리 (JEA) 끝점에서 사용자가 사용할 수 있는 명령 및 응용 프로그램을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-112">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="64992-113">역할 기능은 확장명이 인 파일에 의해 정의 됩니다 `.psrc` .</span><span class="sxs-lookup"><span data-stu-id="64992-113">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="64992-114">예제</span><span class="sxs-lookup"><span data-stu-id="64992-114">EXAMPLES</span></span>

### <span data-ttu-id="64992-115">예 1: 역할 기능 찾기</span><span class="sxs-lookup"><span data-stu-id="64992-115">Example 1: Find role capabilities</span></span>

<span data-ttu-id="64992-116">`Find-RoleCapability` 등록 된 각 리포지토리에서 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-116">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="64992-117">특정 리포지토리를 검색 하려면 **리포지토리** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-117">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="64992-118">예 2: 이름으로 역할 기능 찾기</span><span class="sxs-lookup"><span data-stu-id="64992-118">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="64992-119">`Find-RoleCapability` 이름으로 역할 기능을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-119">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="64992-120">이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-120">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="64992-121">예 3: 역할 기능의 모듈 찾기 및 저장</span><span class="sxs-lookup"><span data-stu-id="64992-121">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="64992-122">`Find-RoleCapability`Cmdlet은 역할 기능을 찾고 파이프라인에서 개체를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="64992-122">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="64992-123">`Save-Module` 역할 기능의 모듈을 파일 시스템에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-123">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="64992-124">`Get-ChildItem` 모듈 디렉터리의 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-124">`Get-ChildItem` displays the contents of the module's directory.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

<span data-ttu-id="64992-125">`Find-RoleCapability`**Name** 매개 변수를 사용 하 여 **일반-Lev1** 역할 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-125">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="64992-126">개체가 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64992-126">The object is sent down the pipeline.</span></span> <span data-ttu-id="64992-127">`Save-Module` 는 파일 시스템 위치에 **Path** 매개 변수를 사용 하 여 모듈을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-127">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="64992-128">모듈을 저장 한 후에는 `Get-ChildItem` 모듈의 **경로** 를 지정 하 고 **JeaExamples** 모듈의 디렉터리 내용을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-128">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="64992-129">예제 4: 역할 기능의 모듈 찾기 및 설치</span><span class="sxs-lookup"><span data-stu-id="64992-129">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="64992-130">`Find-RoleCapability` 모듈을 찾고 개체를 파이프라인으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="64992-130">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="64992-131">`Install-Module` 모듈을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-131">`Install-Module` installs the module.</span></span> <span data-ttu-id="64992-132">설치 후에는를 사용 `Get-InstalledModule` 하 여 결과를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-132">After the installation, use `Get-InstalledModule` to see the results.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

<span data-ttu-id="64992-133">`Find-RoleCapability`**Name** 매개 변수를 사용 하 여 **일반-Lev1** 역할 기능을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-133">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="64992-134">개체가 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64992-134">The object is sent down the pipeline.</span></span> <span data-ttu-id="64992-135">`Install-Module`**Verbose** 매개 변수를 사용 하 여 설치 중에 상태 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-135">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="64992-136">설치가 완료 되 면 `Get-InstalledModule` 출력은 **JeaExamples** 모듈이 설치 되었음을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-136">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="64992-137">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="64992-137">PARAMETERS</span></span>

### <span data-ttu-id="64992-138">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="64992-138">-AllowPrerelease</span></span>

<span data-ttu-id="64992-139">결과에서 시험판으로 표시 된 리소스를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-139">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="64992-140">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="64992-140">-AllVersions</span></span>

<span data-ttu-id="64992-141">이 cmdlet은 모듈의 모든 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="64992-141">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="64992-142">**Allversions)** 매개 변수는 모듈의 사용 가능한 버전을 각각 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-142">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="64992-143">-Filter</span><span class="sxs-lookup"><span data-stu-id="64992-143">-Filter</span></span>

<span data-ttu-id="64992-144">**PackageManagement** 공급자의 검색 구문에 따라 리소스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-144">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="64992-145">예를 들어 **ModuleName** 및 **Description** 속성 내에서 검색할 단어를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-145">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="64992-146">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="64992-146">-MaximumVersion</span></span>

<span data-ttu-id="64992-147">결과에 포함할 모듈의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-147">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="64992-148">**MaximumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-148">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="64992-149">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="64992-149">-MinimumVersion</span></span>

<span data-ttu-id="64992-150">결과에 포함할 모듈의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-150">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="64992-151">**MinimumVersion** 및 **RequiredVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-151">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="64992-152">-ModuleName</span><span class="sxs-lookup"><span data-stu-id="64992-152">-ModuleName</span></span>

<span data-ttu-id="64992-153">역할 기능을 검색할 모듈의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-153">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="64992-154">기본값은 모든 모듈입니다.</span><span class="sxs-lookup"><span data-stu-id="64992-154">The default is all modules.</span></span>

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

### <span data-ttu-id="64992-155">-Name</span><span class="sxs-lookup"><span data-stu-id="64992-155">-Name</span></span>

<span data-ttu-id="64992-156">역할 기능의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-156">Specifies the name of a role capability.</span></span> <span data-ttu-id="64992-157">기본값은 모든 역할 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="64992-157">The default is all role capabilities.</span></span> <span data-ttu-id="64992-158">리소스 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-158">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="64992-159">-프록시</span><span class="sxs-lookup"><span data-stu-id="64992-159">-Proxy</span></span>

<span data-ttu-id="64992-160">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="64992-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="64992-161">-ProxyCredential</span></span>

<span data-ttu-id="64992-162">**Proxy** 매개 변수에 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-162">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="64992-163">-리포지토리</span><span class="sxs-lookup"><span data-stu-id="64992-163">-Repository</span></span>

<span data-ttu-id="64992-164">역할 기능을 검색할 리포지토리를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-164">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="64992-165">저장소 이름 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-165">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="64992-166">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="64992-166">-RequiredVersion</span></span>

<span data-ttu-id="64992-167">결과에 포함할 모듈의 정확한 버전 번호를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-167">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="64992-168">**RequiredVersion** 및 **MinimumVersion** 매개 변수는 동일한 명령에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-168">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="64992-169">-Tag</span><span class="sxs-lookup"><span data-stu-id="64992-169">-Tag</span></span>

<span data-ttu-id="64992-170">리포지토리의 모듈을 범주화 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="64992-171">태그 배열을 구분 하려면 쉼표를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="64992-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="64992-172">CommonParameters</span></span>

<span data-ttu-id="64992-173">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="64992-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="64992-174">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="64992-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="64992-175">입력</span><span class="sxs-lookup"><span data-stu-id="64992-175">INPUTS</span></span>

### <span data-ttu-id="64992-176">System.Uri</span><span class="sxs-lookup"><span data-stu-id="64992-176">System.Uri</span></span>

### <span data-ttu-id="64992-177">System.object. PSCredential</span><span class="sxs-lookup"><span data-stu-id="64992-177">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="64992-178">출력</span><span class="sxs-lookup"><span data-stu-id="64992-178">OUTPUTS</span></span>

### <span data-ttu-id="64992-179">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="64992-179">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="64992-180">`Find-RoleCapability`Cmdlet은 **PSGetRoleCapabilityInfo** 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-180">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="64992-181">참고</span><span class="sxs-lookup"><span data-stu-id="64992-181">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64992-182">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="64992-182">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="64992-183">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="64992-183">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="64992-184">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="64992-184">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="64992-185">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="64992-185">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="64992-186">관련 링크</span><span class="sxs-lookup"><span data-stu-id="64992-186">RELATED LINKS</span></span>

[<span data-ttu-id="64992-187">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="64992-187">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="64992-188">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="64992-188">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="64992-189">Install-Module</span><span class="sxs-lookup"><span data-stu-id="64992-189">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="64992-190">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="64992-190">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="64992-191">Save-Module</span><span class="sxs-lookup"><span data-stu-id="64992-191">Save-Module</span></span>](Save-Module.md)
