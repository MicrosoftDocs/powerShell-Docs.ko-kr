---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 93ec8264bad588e38554daddcdf5dc9befce053e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99605501"
---
# <span data-ttu-id="5e041-102">Save-Package</span><span class="sxs-lookup"><span data-stu-id="5e041-102">Save-Package</span></span>

## <span data-ttu-id="5e041-103">개요</span><span class="sxs-lookup"><span data-stu-id="5e041-103">SYNOPSIS</span></span>
<span data-ttu-id="5e041-104">패키지를 설치 하지 않고 로컬 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-104">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="5e041-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5e041-105">SYNTAX</span></span>

### <span data-ttu-id="5e041-106">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="5e041-106">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="5e041-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="5e041-107">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="5e041-108">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="5e041-108">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="5e041-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="5e041-109">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="5e041-110">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="5e041-110">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="5e041-111">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5e041-111">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="5e041-112">설명</span><span class="sxs-lookup"><span data-stu-id="5e041-112">DESCRIPTION</span></span>

<span data-ttu-id="5e041-113">`Save-Package`Cmdlet은 패키지를 로컬 컴퓨터에 저장 하지만 패키지를 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-113">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="5e041-114">이 cmdlet은 **RequiredVerion** 를 지정 하지 않는 한 최신 버전의 패키지를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-114">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="5e041-115">**Path** 및 **LiteralPath** 매개 변수는 함께 사용할 수 없으며 동일한 명령에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-115">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="5e041-116">예제</span><span class="sxs-lookup"><span data-stu-id="5e041-116">EXAMPLES</span></span>

### <span data-ttu-id="5e041-117">예 1: 로컬 컴퓨터에 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="5e041-117">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="5e041-118">이 예제에서는 최신 버전의 패키지를 로컬 컴퓨터의 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-118">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="5e041-119">패키지의 종속성이 패키지와 함께 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-119">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="5e041-120">`Save-Package`**Name** 매개 변수를 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-120">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="5e041-121">패키지는 **ProviderName** 매개 변수로 지정 된 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-121">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="5e041-122">**Path** 매개 변수는 패키지가 저장 되는 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-122">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="5e041-123">예 2: 특정 패키지 버전 저장</span><span class="sxs-lookup"><span data-stu-id="5e041-123">Example 2: Save a specific package version</span></span>

<span data-ttu-id="5e041-124">이 예에서는 패키지 버전을 지정 하 고 로컬 컴퓨터의 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-124">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="5e041-125">`Save-Package`**Name** 매개 변수를 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-125">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="5e041-126">**RequiredVersion** 은 특정 패키지 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-126">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="5e041-127">패키지는 **ProviderName** 매개 변수로 지정 된 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-127">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="5e041-128">**Path** 매개 변수는 패키지가 저장 되는 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-128">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="5e041-129">예 3: Find-Package을 사용 하 여 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="5e041-129">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="5e041-130">이 명령은를 사용 하 여 `Find-Package` 최신 버전의 패키지를 찾고 개체를로 보냅니다 `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="5e041-130">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="5e041-131">`Find-Package`**Name** 매개 변수를 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-131">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="5e041-132">패키지는 **ProviderName** 매개 변수로 지정 된 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-132">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="5e041-133">개체는 파이프라인에서로 전송 됩니다 `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="5e041-133">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="5e041-134">**Path** 매개 변수는 패키지가 저장 되는 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-134">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="5e041-135">예 4: 패키지를 저장 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-135">Example 4: Save and install the package</span></span>

<span data-ttu-id="5e041-136">최신 버전의 패키지와 해당 종속성이 로컬 컴퓨터에 다운로드 되 고 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-136">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="5e041-137">`Save-Package` 패키지 파일 및 해당 종속성을 로컬 컴퓨터에 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-137">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="5e041-138">`Install-Package` 지정 된 디렉터리에서 패키지와 종속성을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-138">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="5e041-139">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="5e041-139">PARAMETERS</span></span>

### <span data-ttu-id="5e041-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5e041-140">-AcceptLicense</span></span>

<span data-ttu-id="5e041-141">패키지에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-142">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="5e041-142">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="5e041-143">시험판으로 표시 된 패키지를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-143">Allows packages marked as Prerelease to be saved.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-144">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="5e041-144">-AllVersions</span></span>

<span data-ttu-id="5e041-145">이 cmdlet이 사용 가능한 모든 버전의 패키지를 저장 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-145">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="5e041-146">-Command</span><span class="sxs-lookup"><span data-stu-id="5e041-146">-Command</span></span>

<span data-ttu-id="5e041-147">패키지에 포함 된 명령을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-147">Specifies one or more commands included in the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-148">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="5e041-148">-ConfigFile</span></span>

<span data-ttu-id="5e041-149">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-149">Specifies a configuration File.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-150">-포함</span><span class="sxs-lookup"><span data-stu-id="5e041-150">-Contains</span></span>

<span data-ttu-id="5e041-151">`Save-Package` 개체의 속성 값에 있는 항목이 지정 된 값과 정확히 일치 하는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-151">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="5e041-152">-Credential</span></span>

<span data-ttu-id="5e041-153">지정 된 패키지 공급자나 원본에서 패키지를 저장할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-153">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="5e041-154">-Get-dscresource</span><span class="sxs-lookup"><span data-stu-id="5e041-154">-DscResource</span></span>

<span data-ttu-id="5e041-155">패키지에 대 한 하나 이상의 DSC (필요한 상태 구성) 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-155">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-156">-Filter</span><span class="sxs-lookup"><span data-stu-id="5e041-156">-Filter</span></span>

<span data-ttu-id="5e041-157">패키지에 대 한 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-157">Specifies a filter for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-158">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="5e041-158">-FilterOnTag</span></span>

<span data-ttu-id="5e041-159">결과를 필터링 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-159">Specifies the tag that filters the results.</span></span> <span data-ttu-id="5e041-160">지정 된 태그를 포함 하지 않는 결과는 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-160">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-161">-Force</span><span class="sxs-lookup"><span data-stu-id="5e041-161">-Force</span></span>

<span data-ttu-id="5e041-162">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-162">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5e041-163">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="5e041-163">-ForceBootstrap</span></span>

<span data-ttu-id="5e041-164">PackageManagement가 `Save-Package` 지정  된 패키지에 대 한 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-164">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="5e041-165">-헤더</span><span class="sxs-lookup"><span data-stu-id="5e041-165">-Headers</span></span>

<span data-ttu-id="5e041-166">패키지에 대 한 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-166">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-167">-포함</span><span class="sxs-lookup"><span data-stu-id="5e041-167">-Includes</span></span>

<span data-ttu-id="5e041-168">패키지에 포함 된 리소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-168">Indicates the resources that the package includes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-169">-InputObject</span><span class="sxs-lookup"><span data-stu-id="5e041-169">-InputObject</span></span>

<span data-ttu-id="5e041-170">저장 하려는 패키지를 나타내는 소프트웨어 ID 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-170">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="5e041-171">소프트웨어 Id는 cmdlet의 결과에 포함 됩니다 `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="5e041-171">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5e041-172">-LiteralPath</span></span>

<span data-ttu-id="5e041-173">패키지를 저장 하려는 리터럴 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-173">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="5e041-174">동일한 명령에이 매개 변수와 **Path** 매개 변수를 모두 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-174">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="5e041-175">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5e041-175">-MaximumVersion</span></span>

<span data-ttu-id="5e041-176">저장 하려는 패키지의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-176">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="5e041-177">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5e041-177">-MinimumVersion</span></span>

<span data-ttu-id="5e041-178">찾으려는 패키지의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-178">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="5e041-179">-Name</span><span class="sxs-lookup"><span data-stu-id="5e041-179">-Name</span></span>

<span data-ttu-id="5e041-180">하나 이상의 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-180">Specifies one or more package names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-181">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="5e041-181">-PackageManagementProvider</span></span>

<span data-ttu-id="5e041-182">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-182">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-183">-Path</span><span class="sxs-lookup"><span data-stu-id="5e041-183">-Path</span></span>

<span data-ttu-id="5e041-184">패키지를 저장할 로컬 컴퓨터의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-184">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="5e041-185">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="5e041-185">-ProviderName</span></span>

<span data-ttu-id="5e041-186">공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-186">Specifies one or more provider names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-187">-프록시</span><span class="sxs-lookup"><span data-stu-id="5e041-187">-Proxy</span></span>

<span data-ttu-id="5e041-188">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-188">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="5e041-189">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="5e041-189">-ProxyCredential</span></span>

<span data-ttu-id="5e041-190">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-190">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="5e041-191">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="5e041-191">-PublishLocation</span></span>

<span data-ttu-id="5e041-192">게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-192">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-193">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5e041-193">-RequiredVersion</span></span>

<span data-ttu-id="5e041-194">저장할 패키지의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-194">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="5e041-195">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="5e041-195">-RoleCapability</span></span>

<span data-ttu-id="5e041-196">역할 기능의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-196">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-197">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="5e041-197">-ScriptPublishLocation</span></span>

<span data-ttu-id="5e041-198">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-198">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-199">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="5e041-199">-ScriptSourceLocation</span></span>

<span data-ttu-id="5e041-200">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-200">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-201">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="5e041-201">-SkipValidate</span></span>

<span data-ttu-id="5e041-202">패키지의 자격 증명에 대 한 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-202">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-203">-Source</span><span class="sxs-lookup"><span data-stu-id="5e041-203">-Source</span></span>

<span data-ttu-id="5e041-204">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-204">Specifies one or more package sources.</span></span>

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

### <span data-ttu-id="5e041-205">-Tag</span><span class="sxs-lookup"><span data-stu-id="5e041-205">-Tag</span></span>

<span data-ttu-id="5e041-206">패키지 메타 데이터 내에서 검색할 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-206">Specifies a tag to search for within the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-207">-Type</span><span class="sxs-lookup"><span data-stu-id="5e041-207">-Type</span></span>

<span data-ttu-id="5e041-208">모듈, 스크립트 또는 중 하나를 사용 하 여 패키지를 검색할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-208">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5e041-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5e041-209">-Confirm</span></span>

<span data-ttu-id="5e041-210">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-210">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5e041-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5e041-211">-WhatIf</span></span>

<span data-ttu-id="5e041-212">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="5e041-213">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5e041-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e041-214">CommonParameters</span></span>

<span data-ttu-id="5e041-215">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e041-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e041-216">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e041-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e041-217">입력</span><span class="sxs-lookup"><span data-stu-id="5e041-217">INPUTS</span></span>

### <span data-ttu-id="5e041-218">`Save-Package` 파이프라인의 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-218">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="5e041-219">출력</span><span class="sxs-lookup"><span data-stu-id="5e041-219">OUTPUTS</span></span>

### <span data-ttu-id="5e041-220">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-220">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5e041-221">참고</span><span class="sxs-lookup"><span data-stu-id="5e041-221">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e041-222">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-222">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="5e041-223">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-223">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="5e041-224">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5e041-224">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="5e041-225">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5e041-225">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="5e041-226">관련 링크</span><span class="sxs-lookup"><span data-stu-id="5e041-226">RELATED LINKS</span></span>

[<span data-ttu-id="5e041-227">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="5e041-227">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="5e041-228">Get-Package</span><span class="sxs-lookup"><span data-stu-id="5e041-228">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="5e041-229">Install-Package</span><span class="sxs-lookup"><span data-stu-id="5e041-229">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="5e041-230">Save-Package</span><span class="sxs-lookup"><span data-stu-id="5e041-230">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="5e041-231">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="5e041-231">Uninstall-Package</span></span>](Uninstall-Package.md)
