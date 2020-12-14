---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 1b780ad8c28c6c7095012fd75ed4dfa31d761b08
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889997"
---
# <span data-ttu-id="85ef0-103">Save-Package</span><span class="sxs-lookup"><span data-stu-id="85ef0-103">Save-Package</span></span>

## <span data-ttu-id="85ef0-104">개요</span><span class="sxs-lookup"><span data-stu-id="85ef0-104">SYNOPSIS</span></span>
<span data-ttu-id="85ef0-105">패키지를 설치 하지 않고 로컬 컴퓨터에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-105">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="85ef0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="85ef0-106">SYNTAX</span></span>

### <span data-ttu-id="85ef0-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="85ef0-107">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="85ef0-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="85ef0-108">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="85ef0-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="85ef0-109">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="85ef0-110">NuGet</span><span class="sxs-lookup"><span data-stu-id="85ef0-110">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="85ef0-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="85ef0-111">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="85ef0-112">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="85ef0-112">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="85ef0-113">설명</span><span class="sxs-lookup"><span data-stu-id="85ef0-113">DESCRIPTION</span></span>

<span data-ttu-id="85ef0-114">`Save-Package`Cmdlet은 패키지를 로컬 컴퓨터에 저장 하지만 패키지를 설치 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-114">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="85ef0-115">이 cmdlet은 **RequiredVerion** 를 지정 하지 않는 한 최신 버전의 패키지를 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-115">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="85ef0-116">**Path** 및 **LiteralPath** 매개 변수는 함께 사용할 수 없으며 동일한 명령에 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-116">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="85ef0-117">예제</span><span class="sxs-lookup"><span data-stu-id="85ef0-117">EXAMPLES</span></span>

### <span data-ttu-id="85ef0-118">예 1: 로컬 컴퓨터에 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="85ef0-118">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="85ef0-119">이 예제에서는 최신 버전의 패키지를 로컬 컴퓨터의 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-119">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="85ef0-120">패키지의 종속성이 패키지와 함께 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-120">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="85ef0-121">`Save-Package`**Name** 매개 변수를 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-121">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="85ef0-122">패키지는 **ProviderName** 매개 변수로 지정 된 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-122">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="85ef0-123">**Path** 매개 변수는 패키지가 저장 되는 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-123">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="85ef0-124">예 2: 특정 패키지 버전 저장</span><span class="sxs-lookup"><span data-stu-id="85ef0-124">Example 2: Save a specific package version</span></span>

<span data-ttu-id="85ef0-125">이 예에서는 패키지 버전을 지정 하 고 로컬 컴퓨터의 디렉터리에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-125">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="85ef0-126">`Save-Package`**Name** 매개 변수를 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-126">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="85ef0-127">**RequiredVersion** 은 특정 패키지 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-127">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="85ef0-128">패키지는 **ProviderName** 매개 변수로 지정 된 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-128">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="85ef0-129">**Path** 매개 변수는 패키지가 저장 되는 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-129">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="85ef0-130">예 3: Find-Package을 사용 하 여 패키지 저장</span><span class="sxs-lookup"><span data-stu-id="85ef0-130">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="85ef0-131">이 명령은를 사용 하 여 `Find-Package` 최신 버전의 패키지를 찾고 개체를로 보냅니다 `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="85ef0-131">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="85ef0-132">`Find-Package`**Name** 매개 변수를 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-132">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="85ef0-133">패키지는 **ProviderName** 매개 변수로 지정 된 리포지토리에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-133">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="85ef0-134">개체는 파이프라인에서로 전송 됩니다 `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="85ef0-134">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="85ef0-135">**Path** 매개 변수는 패키지가 저장 되는 위치를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-135">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="85ef0-136">예 4: 패키지를 저장 하 고 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-136">Example 4: Save and install the package</span></span>

<span data-ttu-id="85ef0-137">최신 버전의 패키지와 해당 종속성이 로컬 컴퓨터에 다운로드 되 고 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-137">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="85ef0-138">`Save-Package` 패키지 파일 및 해당 종속성을 로컬 컴퓨터에 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-138">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="85ef0-139">`Install-Package` 지정 된 디렉터리에서 패키지와 종속성을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-139">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="85ef0-140">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="85ef0-140">PARAMETERS</span></span>

### <span data-ttu-id="85ef0-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="85ef0-141">-AcceptLicense</span></span>

<span data-ttu-id="85ef0-142">패키지에 필요한 경우 설치 하는 동안 사용권 계약에 자동으로 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-142">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="85ef0-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="85ef0-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="85ef0-144">시험판으로 표시 된 패키지를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-144">Allows packages marked as Prerelease to be saved.</span></span>

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

### <span data-ttu-id="85ef0-145">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="85ef0-145">-AllVersions</span></span>

<span data-ttu-id="85ef0-146">이 cmdlet이 사용 가능한 모든 버전의 패키지를 저장 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-146">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="85ef0-147">-Command</span><span class="sxs-lookup"><span data-stu-id="85ef0-147">-Command</span></span>

<span data-ttu-id="85ef0-148">패키지에 포함 된 명령을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-148">Specifies one or more commands included in the package.</span></span>

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

### <span data-ttu-id="85ef0-149">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="85ef0-149">-ConfigFile</span></span>

<span data-ttu-id="85ef0-150">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-150">Specifies a configuration File.</span></span>

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

### <span data-ttu-id="85ef0-151">-포함</span><span class="sxs-lookup"><span data-stu-id="85ef0-151">-Contains</span></span>

<span data-ttu-id="85ef0-152">`Save-Package` 개체의 속성 값에 있는 항목이 지정 된 값과 정확히 일치 하는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-152">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="85ef0-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="85ef0-153">-Credential</span></span>

<span data-ttu-id="85ef0-154">지정 된 패키지 공급자나 원본에서 패키지를 저장할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-154">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="85ef0-155">-Get-dscresource</span><span class="sxs-lookup"><span data-stu-id="85ef0-155">-DscResource</span></span>

<span data-ttu-id="85ef0-156">패키지에 대 한 하나 이상의 DSC (필요한 상태 구성) 리소스를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-156">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

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

### <span data-ttu-id="85ef0-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="85ef0-157">-Filter</span></span>

<span data-ttu-id="85ef0-158">패키지에 대 한 필터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-158">Specifies a filter for the package.</span></span>

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

### <span data-ttu-id="85ef0-159">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="85ef0-159">-FilterOnTag</span></span>

<span data-ttu-id="85ef0-160">결과를 필터링 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-160">Specifies the tag that filters the results.</span></span> <span data-ttu-id="85ef0-161">지정 된 태그를 포함 하지 않는 결과는 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-161">Results that don't contain the specified tag are excluded.</span></span>

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

### <span data-ttu-id="85ef0-162">-Force</span><span class="sxs-lookup"><span data-stu-id="85ef0-162">-Force</span></span>

<span data-ttu-id="85ef0-163">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-163">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="85ef0-164">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="85ef0-164">-ForceBootstrap</span></span>

<span data-ttu-id="85ef0-165">PackageManagement가 `Save-Package` 지정  된 패키지에 대 한 패키지 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-165">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="85ef0-166">-헤더</span><span class="sxs-lookup"><span data-stu-id="85ef0-166">-Headers</span></span>

<span data-ttu-id="85ef0-167">패키지에 대 한 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-167">Specifies the headers for the package.</span></span>

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

### <span data-ttu-id="85ef0-168">-포함</span><span class="sxs-lookup"><span data-stu-id="85ef0-168">-Includes</span></span>

<span data-ttu-id="85ef0-169">패키지에 포함 된 리소스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-169">Indicates the resources that the package includes.</span></span>

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

### <span data-ttu-id="85ef0-170">-InputObject</span><span class="sxs-lookup"><span data-stu-id="85ef0-170">-InputObject</span></span>

<span data-ttu-id="85ef0-171">저장 하려는 패키지를 나타내는 소프트웨어 ID 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-171">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="85ef0-172">소프트웨어 Id는 cmdlet의 결과에 포함 됩니다 `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="85ef0-172">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

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

### <span data-ttu-id="85ef0-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="85ef0-173">-LiteralPath</span></span>

<span data-ttu-id="85ef0-174">패키지를 저장 하려는 리터럴 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-174">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="85ef0-175">동일한 명령에이 매개 변수와 **Path** 매개 변수를 모두 추가할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-175">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="85ef0-176">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="85ef0-176">-MaximumVersion</span></span>

<span data-ttu-id="85ef0-177">저장 하려는 패키지의 최대 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-177">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="85ef0-178">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="85ef0-178">-MinimumVersion</span></span>

<span data-ttu-id="85ef0-179">찾으려는 패키지의 최소 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-179">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="85ef0-180">-Name</span><span class="sxs-lookup"><span data-stu-id="85ef0-180">-Name</span></span>

<span data-ttu-id="85ef0-181">하나 이상의 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-181">Specifies one or more package names.</span></span>

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

### <span data-ttu-id="85ef0-182">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="85ef0-182">-PackageManagementProvider</span></span>

<span data-ttu-id="85ef0-183">패키지 관리 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-183">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="85ef0-184">-Path</span><span class="sxs-lookup"><span data-stu-id="85ef0-184">-Path</span></span>

<span data-ttu-id="85ef0-185">패키지를 저장할 로컬 컴퓨터의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-185">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="85ef0-186">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="85ef0-186">-ProviderName</span></span>

<span data-ttu-id="85ef0-187">공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-187">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="85ef0-188">-프록시</span><span class="sxs-lookup"><span data-stu-id="85ef0-188">-Proxy</span></span>

<span data-ttu-id="85ef0-189">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-189">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="85ef0-190">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="85ef0-190">-ProxyCredential</span></span>

<span data-ttu-id="85ef0-191">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-191">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="85ef0-192">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="85ef0-192">-PublishLocation</span></span>

<span data-ttu-id="85ef0-193">게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-193">Specifies the publish location.</span></span>

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

### <span data-ttu-id="85ef0-194">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="85ef0-194">-RequiredVersion</span></span>

<span data-ttu-id="85ef0-195">저장할 패키지의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-195">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="85ef0-196">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="85ef0-196">-RoleCapability</span></span>

<span data-ttu-id="85ef0-197">역할 기능의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-197">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="85ef0-198">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="85ef0-198">-ScriptPublishLocation</span></span>

<span data-ttu-id="85ef0-199">스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-199">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="85ef0-200">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="85ef0-200">-ScriptSourceLocation</span></span>

<span data-ttu-id="85ef0-201">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-201">Specifies the script source location.</span></span>

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

### <span data-ttu-id="85ef0-202">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="85ef0-202">-SkipValidate</span></span>

<span data-ttu-id="85ef0-203">패키지의 자격 증명에 대 한 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-203">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="85ef0-204">-Source</span><span class="sxs-lookup"><span data-stu-id="85ef0-204">-Source</span></span>

<span data-ttu-id="85ef0-205">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-205">Specifies one or more package sources.</span></span>

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

### <span data-ttu-id="85ef0-206">-Tag</span><span class="sxs-lookup"><span data-stu-id="85ef0-206">-Tag</span></span>

<span data-ttu-id="85ef0-207">패키지 메타 데이터 내에서 검색할 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-207">Specifies a tag to search for within the package metadata.</span></span>

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

### <span data-ttu-id="85ef0-208">-Type</span><span class="sxs-lookup"><span data-stu-id="85ef0-208">-Type</span></span>

<span data-ttu-id="85ef0-209">모듈, 스크립트 또는 중 하나를 사용 하 여 패키지를 검색할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-209">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="85ef0-210">-Confirm</span><span class="sxs-lookup"><span data-stu-id="85ef0-210">-Confirm</span></span>

<span data-ttu-id="85ef0-211">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-211">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="85ef0-212">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="85ef0-212">-WhatIf</span></span>

<span data-ttu-id="85ef0-213">cmdlet을 실행할 경우 발생하는 일을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-213">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="85ef0-214">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-214">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="85ef0-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="85ef0-215">CommonParameters</span></span>

<span data-ttu-id="85ef0-216">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="85ef0-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="85ef0-217">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85ef0-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="85ef0-218">입력</span><span class="sxs-lookup"><span data-stu-id="85ef0-218">INPUTS</span></span>

### <span data-ttu-id="85ef0-219">`Save-Package` 파이프라인의 개체를 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-219">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="85ef0-220">출력</span><span class="sxs-lookup"><span data-stu-id="85ef0-220">OUTPUTS</span></span>

### <span data-ttu-id="85ef0-221">이 cmdlet은 어떠한 출력도 생성하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-221">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="85ef0-222">참고</span><span class="sxs-lookup"><span data-stu-id="85ef0-222">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85ef0-223">2020 4 월부터 PowerShell 갤러리는 더 이상 TLS (Transport Layer Security) 버전 1.0 및 1.1을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-223">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="85ef0-224">TLS 1.2 이상을 사용 하지 않는 경우 PowerShell 갤러리에 액세스 하려고 하면 오류가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-224">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="85ef0-225">다음 명령을 사용 하 여 TLS 1.2을 사용 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="85ef0-225">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="85ef0-226">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="85ef0-226">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="85ef0-227">관련 링크</span><span class="sxs-lookup"><span data-stu-id="85ef0-227">RELATED LINKS</span></span>

[<span data-ttu-id="85ef0-228">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="85ef0-228">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="85ef0-229">Get-Package</span><span class="sxs-lookup"><span data-stu-id="85ef0-229">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="85ef0-230">Install-Package</span><span class="sxs-lookup"><span data-stu-id="85ef0-230">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="85ef0-231">Save-Package</span><span class="sxs-lookup"><span data-stu-id="85ef0-231">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="85ef0-232">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="85ef0-232">Uninstall-Package</span></span>](Uninstall-Package.md)
