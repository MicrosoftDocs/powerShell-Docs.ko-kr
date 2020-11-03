---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: 9bbcda92b98410835a2380296a06fd053c01b52c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210914"
---
# <span data-ttu-id="2f81e-103">Find-Package</span><span class="sxs-lookup"><span data-stu-id="2f81e-103">Find-Package</span></span>

## <span data-ttu-id="2f81e-104">개요</span><span class="sxs-lookup"><span data-stu-id="2f81e-104">SYNOPSIS</span></span>
<span data-ttu-id="2f81e-105">사용 가능한 패키지 소스에서 소프트웨어 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-105">Finds software packages in available package sources.</span></span>

## <span data-ttu-id="2f81e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f81e-106">SYNTAX</span></span>

### <span data-ttu-id="2f81e-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="2f81e-107">NuGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="2f81e-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="2f81e-108">PowerShellGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-AllowPrereleaseVersions] [-PackageManagementProvider <String>]
 [-PublishLocation <String>] [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>]
 [-Type <String>] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>]
 [-DscResource <String[]>] [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense]
 [<CommonParameters>]
```

## <span data-ttu-id="2f81e-109">설명</span><span class="sxs-lookup"><span data-stu-id="2f81e-109">DESCRIPTION</span></span>

<span data-ttu-id="2f81e-110">`Find-Package` 패키지 원본에서 사용할 수 있는 소프트웨어 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-110">`Find-Package` finds software packages that are available in package sources.</span></span> <span data-ttu-id="2f81e-111">`Get-PackageProvider` 및 `Get-PackageSource` 공급자에 대 한 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-111">`Get-PackageProvider` and `Get-PackageSource` display details about your providers.</span></span>

## <span data-ttu-id="2f81e-112">예제</span><span class="sxs-lookup"><span data-stu-id="2f81e-112">EXAMPLES</span></span>

### <span data-ttu-id="2f81e-113">예제 1: 패키지 공급자에서 사용 가능한 모든 패키지 찾기</span><span class="sxs-lookup"><span data-stu-id="2f81e-113">Example 1: Find all available packages from a package provider</span></span>

<span data-ttu-id="2f81e-114">이 명령은 등록 된 갤러리에서 사용 가능한 모든 PowerShell 모듈 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-114">This command finds all available PowerShell module packages in a registered gallery.</span></span> <span data-ttu-id="2f81e-115">`Get-PackageProvider`를 사용 하 여 공급자 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-115">Use `Get-PackageProvider` to get the provider name.</span></span>

```
Find-Package -ProviderName NuGet
```

```Output
Name               Version   Source     Summary
----               -------   ------     -------
NUnit              3.11.0    MyNuGet    NUnit is a unit-testing framework for all .NET langua...
Newtonsoft.Json    12.0.1    MyNuGet    Json.NET is a popular high-performance JSON framework...
EntityFramework    6.2.0     MyNuGet    Entity Framework is Microsoft's recommended data acce...
MySql.Data         8.0.15    MyNuGet    MySql.Data.MySqlClient .Net Core Class Library
bootstrap          4.3.1     MyNuGet    Bootstrap framework in CSS. Includes fonts and JavaSc...
NuGet.Core         2.14.0    MyNuGet    NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="2f81e-116">`Find-Package`**provider 매개 변수** 를 사용 하 여 공급자 **NuGet** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-116">`Find-Package` uses the **Provider** parameter to specify the provider **NuGet** .</span></span>

### <span data-ttu-id="2f81e-117">예제 2: 패키지 원본에서 패키지 찾기</span><span class="sxs-lookup"><span data-stu-id="2f81e-117">Example 2: Find a package from a package source</span></span>

<span data-ttu-id="2f81e-118">이 명령은 지정 된 패키지 원본에서 최신 버전의 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-118">This command finds the newest version of a package from a specified package source.</span></span> <span data-ttu-id="2f81e-119">패키지 원본을 제공 하지 않으면에서 `Find-Package` 설치 된 각 패키지 공급자와 해당 패키지 원본을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-119">If a package source isn't provided, `Find-Package` searches each installed package provider and its package sources.</span></span> <span data-ttu-id="2f81e-120">`Get-PackageSource`를 사용 하 여 원본 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-120">Use `Get-PackageSource` to get the source name.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="2f81e-121">`Find-Package`**name** 매개 변수를 사용 하 여 **NuGet. Core** 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-121">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core** .</span></span> <span data-ttu-id="2f81e-122">**Source** 매개 변수는 **MyNuGet** 에서 패키지를 검색 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-122">The **Source** parameter specifies to search for the package in **MyNuGet** .</span></span>

### <span data-ttu-id="2f81e-123">예제 3: 패키지의 모든 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="2f81e-123">Example 3: Find all versions of a package</span></span>

<span data-ttu-id="2f81e-124">이 명령은 지정 된 공급자에서 사용 가능한 모든 패키지 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-124">This command finds all available package versions from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.14.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.14.0-rtm-832   MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.13.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
...
NuGet.Core    1.1.229.159      MyNuGet      NuGet.Core is the core framework assembly for NuGet...
Nuget.Core    1.0.1120.104     MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="2f81e-125">`Find-Package`**Name** 매개 변수를 사용 하 여 **NuGet. Core** 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-125">`Find-Package` uses the **Name** parameter to specify the package **NuGet.Core** .</span></span> <span data-ttu-id="2f81e-126">**ProviderName** 매개 변수는 **MyNuGet** 에서 패키지를 검색 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-126">The **ProviderName** parameter specifies to search for the package in **MyNuGet** .</span></span> <span data-ttu-id="2f81e-127">**Allversions)** 는 사용 가능한 모든 버전을 반환 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-127">**AllVersions** specifies that all available versions are returned.</span></span>

### <span data-ttu-id="2f81e-128">예제 4: 특정 이름 및 버전의 패키지 찾기</span><span class="sxs-lookup"><span data-stu-id="2f81e-128">Example 4: Find a package with a specific name and version</span></span>

<span data-ttu-id="2f81e-129">이 명령은 지정 된 공급자에서 특정 패키지 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-129">This command finds a specific package version from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="2f81e-130">`Find-Package`**name** 매개 변수를 사용 하 여 **NuGet. Core** 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-130">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core** .</span></span> <span data-ttu-id="2f81e-131">**ProviderName** 매개 변수는 **NuGet** 에서 패키지를 검색 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-131">The **ProviderName** parameter specifies to search for the package in **NuGet** .</span></span> <span data-ttu-id="2f81e-132">**RequiredVersion** 은 버전 **2.9.0** 반환 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-132">**RequiredVersion** specifies that only version **2.9.0** is returned.</span></span>

### <span data-ttu-id="2f81e-133">예 5: 버전 범위 내에서 패키지 찾기</span><span class="sxs-lookup"><span data-stu-id="2f81e-133">Example 5: Find packages within a range of versions</span></span>

<span data-ttu-id="2f81e-134">이 명령은 지정 된 패키지에 대 한 버전 범위를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-134">This command finds a range of versions for a specified package.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -MinimumVersion 2.7.0 -MaximumVersion 2.9.0 -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.6            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.7.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="2f81e-135">`Find-Package`**name** 매개 변수를 사용 하 여 **NuGet. Core** 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-135">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core** .</span></span> <span data-ttu-id="2f81e-136">**ProviderName** 매개 변수는 **NuGet** 에서 패키지를 검색 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-136">The **ProviderName** parameter specifies to search for the package in **NuGet** .</span></span> <span data-ttu-id="2f81e-137">**MinimumVersion** 은 가장 낮은 버전의 **합니다** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-137">**MinimumVersion** specifies the lowest version **2.7.0** .</span></span> <span data-ttu-id="2f81e-138">**MaximumVersion** 은 가장 높은 버전의 **2.9.0** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-138">**MaximumVersion** specifies the highest version **2.9.0** .</span></span>
<span data-ttu-id="2f81e-139">**Allversions)** 는 최소값과 최대값으로 지정 된 범위를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-139">**AllVersions** determines the range is returned as specified by the minimum and maximum.</span></span>

### <span data-ttu-id="2f81e-140">예제 6: 파일 시스템에서 패키지 찾기</span><span class="sxs-lookup"><span data-stu-id="2f81e-140">Example 6: Find a package from a file system</span></span>

<span data-ttu-id="2f81e-141">이 명령은 `.nupkg` 로컬 컴퓨터에 저장 된 파일 확장명을 사용 하 여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-141">This command finds packages with the file extension `.nupkg` that are stored on the local computer.</span></span>
<span data-ttu-id="2f81e-142">파일은 **NuGet** 과 같은 갤러리에서 다운로드 된 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-142">The files are packages downloaded from a gallery such as the **NuGet** .</span></span>

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## <span data-ttu-id="2f81e-143">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="2f81e-143">PARAMETERS</span></span>

### <span data-ttu-id="2f81e-144">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="2f81e-144">-AcceptLicense</span></span>

<span data-ttu-id="2f81e-145">패키지에 필요한 경우 자동으로 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-145">Automatically accepts a license agreement if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-146">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="2f81e-146">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="2f81e-147">결과에서 시험판으로 표시 된 패키지를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-147">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="2f81e-148">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="2f81e-148">-AllVersions</span></span>

<span data-ttu-id="2f81e-149">에서 `Find-Package` 사용 가능한 패키지 버전을 모두 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-149">Indicates that `Find-Package` returns all available versions of the package.</span></span> <span data-ttu-id="2f81e-150">기본적으로는 `Find-Package` 사용 가능한 최신 버전만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-150">By default, `Find-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="2f81e-151">-Command</span><span class="sxs-lookup"><span data-stu-id="2f81e-151">-Command</span></span>

<span data-ttu-id="2f81e-152">에서 검색 하는 명령 배열을 지정 합니다 `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="2f81e-152">Specifies an array of commands searched by `Find-Package`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-153">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="2f81e-153">-ConfigFile</span></span>

<span data-ttu-id="2f81e-154">구성 파일을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-154">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-155">-포함</span><span class="sxs-lookup"><span data-stu-id="2f81e-155">-Contains</span></span>

<span data-ttu-id="2f81e-156">`Find-Package` 개체의 속성 값에 있는 항목이 지정 된 값과 정확히 일치 하는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-156">`Find-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="2f81e-157">-Credential</span></span>

<span data-ttu-id="2f81e-158">패키지를 검색할 수 있는 권한이 있는 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-158">Specifies a user account that has permission to search for packages.</span></span>

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

### <span data-ttu-id="2f81e-159">-Get-dscresource</span><span class="sxs-lookup"><span data-stu-id="2f81e-159">-DscResource</span></span>

<span data-ttu-id="2f81e-160">이 cmdlet이 검색 하는 DSC (필요한 상태 구성) 리소스의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-160">Specifies an array of Desired State Configuration (DSC) resources that this cmdlet searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-161">-Filter</span><span class="sxs-lookup"><span data-stu-id="2f81e-161">-Filter</span></span>

<span data-ttu-id="2f81e-162">**이름** 및 **설명** 속성에서 검색할 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-162">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-163">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="2f81e-163">-FilterOnTag</span></span>

<span data-ttu-id="2f81e-164">결과를 필터링 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-164">Specifies the tag that filters the results.</span></span> <span data-ttu-id="2f81e-165">지정 된 태그를 포함 하지 않는 결과는 제외 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-165">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-166">-Force</span><span class="sxs-lookup"><span data-stu-id="2f81e-166">-Force</span></span>

<span data-ttu-id="2f81e-167">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-167">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="2f81e-168">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="2f81e-168">-ForceBootstrap</span></span>

<span data-ttu-id="2f81e-169">PackageManagement에서 `Find-Package` 패키지 **PackageManagement** 공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-169">Indicates that `Find-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="2f81e-170">-헤더</span><span class="sxs-lookup"><span data-stu-id="2f81e-170">-Headers</span></span>

<span data-ttu-id="2f81e-171">패키지에 대 한 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-171">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-172">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="2f81e-172">-IncludeDependencies</span></span>

<span data-ttu-id="2f81e-173">이 cmdlet이 결과의 패키지 종속성을 포함 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-173">Indicates that this cmdlet includes package dependencies in the results.</span></span>

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

### <span data-ttu-id="2f81e-174">-포함</span><span class="sxs-lookup"><span data-stu-id="2f81e-174">-Includes</span></span>

<span data-ttu-id="2f81e-175">`Find-Package`에서 범주 내의 모든 패키지를 찾아야 하는지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-175">Specifies whether `Find-Package` should find all packages within a category.</span></span>

<span data-ttu-id="2f81e-176">허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-176">The accepted values are as follows:</span></span>

- <span data-ttu-id="2f81e-177">cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f81e-177">Cmdlet</span></span>
- <span data-ttu-id="2f81e-178">DscResource</span><span class="sxs-lookup"><span data-stu-id="2f81e-178">DscResource</span></span>
- <span data-ttu-id="2f81e-179">함수</span><span class="sxs-lookup"><span data-stu-id="2f81e-179">Function</span></span>
- <span data-ttu-id="2f81e-180">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="2f81e-180">RoleCapability</span></span>
- <span data-ttu-id="2f81e-181">워크플로</span><span class="sxs-lookup"><span data-stu-id="2f81e-181">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-182">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2f81e-182">-MaximumVersion</span></span>

<span data-ttu-id="2f81e-183">검색 하려는 최대 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-183">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="2f81e-184">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2f81e-184">-MinimumVersion</span></span>

<span data-ttu-id="2f81e-185">찾으려는 최소 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-185">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="2f81e-186">더 높은 버전을 사용할 수 있는 경우 해당 버전이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-186">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="2f81e-187">-Name</span><span class="sxs-lookup"><span data-stu-id="2f81e-187">-Name</span></span>

<span data-ttu-id="2f81e-188">하나 이상의 패키지 이름 또는 와일드 카드 문자를 포함 하는 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-188">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="2f81e-189">여러 패키지 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-189">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="2f81e-190">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="2f81e-190">-PackageManagementProvider</span></span>

<span data-ttu-id="2f81e-191">패키지 관리 공급자의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-191">Specifies the name of a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-192">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="2f81e-192">-ProviderName</span></span>

<span data-ttu-id="2f81e-193">패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-193">Specifies one or more package provider names.</span></span> <span data-ttu-id="2f81e-194">여러 패키지 공급자 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-194">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="2f81e-195">사용 `Get-PackageProvider` 가능한 패키지 공급자 목록을 가져오는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-195">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-196">-프록시</span><span class="sxs-lookup"><span data-stu-id="2f81e-196">-Proxy</span></span>

<span data-ttu-id="2f81e-197">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-197">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="2f81e-198">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="2f81e-198">-ProxyCredential</span></span>

<span data-ttu-id="2f81e-199">**Proxy** 매개 변수에 지정된 프록시 서버를 사용할 권한이 있는 사용자 계정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-199">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="2f81e-200">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="2f81e-200">-PublishLocation</span></span>

<span data-ttu-id="2f81e-201">패키지를 게시할 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-201">Specifies a location for publishing the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-202">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2f81e-202">-RequiredVersion</span></span>

<span data-ttu-id="2f81e-203">찾으려는 정확한 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-203">Specifies an exact package version that you want to find.</span></span>

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

### <span data-ttu-id="2f81e-204">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="2f81e-204">-RoleCapability</span></span>

<span data-ttu-id="2f81e-205">역할 기능의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-205">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-206">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="2f81e-206">-ScriptPublishLocation</span></span>

<span data-ttu-id="2f81e-207">패키지에 대 한 스크립트 게시 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-207">Specifies a script publishing location for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-208">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="2f81e-208">-ScriptSourceLocation</span></span>

<span data-ttu-id="2f81e-209">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-209">Specifies a script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-210">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="2f81e-210">-SkipValidate</span></span>

<span data-ttu-id="2f81e-211">패키지 자격 증명 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-211">Switch that skips package credential validation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-212">-Source</span><span class="sxs-lookup"><span data-stu-id="2f81e-212">-Source</span></span>

<span data-ttu-id="2f81e-213">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-213">Specifies one or more package sources.</span></span> <span data-ttu-id="2f81e-214">사용 `Get-PackageSource` 가능한 패키지 원본 목록을 가져오는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-214">Use `Get-PackageSource` to get a list of available package sources.</span></span> <span data-ttu-id="2f81e-215">파일 시스템 디렉터리를 다운로드 패키지의 원본으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-215">A file system directory can be used as a source for download packages.</span></span>

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

### <span data-ttu-id="2f81e-216">-Tag</span><span class="sxs-lookup"><span data-stu-id="2f81e-216">-Tag</span></span>

<span data-ttu-id="2f81e-217">패키지 메타 데이터에서 검색할 문자열을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-217">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-218">-Type</span><span class="sxs-lookup"><span data-stu-id="2f81e-218">-Type</span></span>

<span data-ttu-id="2f81e-219">모듈, 스크립트 또는 중 하나를 사용 하 여 패키지를 검색할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-219">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f81e-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f81e-220">CommonParameters</span></span>

<span data-ttu-id="2f81e-221">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f81e-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f81e-222">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f81e-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f81e-223">입력</span><span class="sxs-lookup"><span data-stu-id="2f81e-223">INPUTS</span></span>

### <span data-ttu-id="2f81e-224">없음</span><span class="sxs-lookup"><span data-stu-id="2f81e-224">None</span></span>

<span data-ttu-id="2f81e-225">`Find-Package` 파이프라인의 입력을 허용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-225">`Find-Package` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="2f81e-226">출력</span><span class="sxs-lookup"><span data-stu-id="2f81e-226">OUTPUTS</span></span>

### <span data-ttu-id="2f81e-227">\Id []</span><span class="sxs-lookup"><span data-stu-id="2f81e-227">SoftwareIdentify[]</span></span>

<span data-ttu-id="2f81e-228">`Find-Package`**\Id** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f81e-228">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

## <span data-ttu-id="2f81e-229">참고</span><span class="sxs-lookup"><span data-stu-id="2f81e-229">NOTES</span></span>

## <span data-ttu-id="2f81e-230">관련 링크</span><span class="sxs-lookup"><span data-stu-id="2f81e-230">RELATED LINKS</span></span>

[<span data-ttu-id="2f81e-231">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="2f81e-231">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="2f81e-232">Get-Package</span><span class="sxs-lookup"><span data-stu-id="2f81e-232">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="2f81e-233">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="2f81e-233">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="2f81e-234">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="2f81e-234">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="2f81e-235">Install-Package</span><span class="sxs-lookup"><span data-stu-id="2f81e-235">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="2f81e-236">Save-Package</span><span class="sxs-lookup"><span data-stu-id="2f81e-236">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="2f81e-237">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="2f81e-237">Uninstall-Package</span></span>](Uninstall-Package.md)
