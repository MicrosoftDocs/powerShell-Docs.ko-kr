---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 2c4f3526e1277c887a350cacda6641a889cae712
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "93210009"
---
# <span data-ttu-id="9acfe-103">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="9acfe-103">Uninstall-Package</span></span>

## <span data-ttu-id="9acfe-104">개요</span><span class="sxs-lookup"><span data-stu-id="9acfe-104">SYNOPSIS</span></span>
<span data-ttu-id="9acfe-105">하나 이상의 소프트웨어 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-105">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="9acfe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9acfe-106">SYNTAX</span></span>

### <span data-ttu-id="9acfe-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="9acfe-107">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9acfe-108">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="9acfe-108">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="9acfe-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="9acfe-109">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="9acfe-110">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="9acfe-110">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="9acfe-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="9acfe-111">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="9acfe-112">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="9acfe-112">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="9acfe-113">설명</span><span class="sxs-lookup"><span data-stu-id="9acfe-113">DESCRIPTION</span></span>

<span data-ttu-id="9acfe-114">`Uninstall-Package`Cmdlet은 로컬 컴퓨터에서 하나 이상의 소프트웨어 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-114">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="9acfe-115">설치 된 패키지를 찾으려면 cmdlet을 사용 `Get-Package` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-115">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="9acfe-116">예제</span><span class="sxs-lookup"><span data-stu-id="9acfe-116">EXAMPLES</span></span>

### <span data-ttu-id="9acfe-117">예제 1: 패키지 제거</span><span class="sxs-lookup"><span data-stu-id="9acfe-117">Example 1: Uninstall a package</span></span>

<span data-ttu-id="9acfe-118">`Uninstall-Package`Cmdlet은 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-118">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="9acfe-119">**Name** 매개 변수는 제거할 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-119">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="9acfe-120">패키지의 여러 버전을 설치 하는 경우 최신 버전이 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-120">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="9acfe-121">예제 2: 파이프라인을 사용 하 여 패키지 제거</span><span class="sxs-lookup"><span data-stu-id="9acfe-121">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="9acfe-122">`Get-Package` 특정 패키지를 찾아서 파이프라인에서 cmdlet에 대 한 개체 **id** 개체를 보냅니다 `Uninsall-Package` .</span><span class="sxs-lookup"><span data-stu-id="9acfe-122">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="9acfe-123">`Get-Package`Cmdlet은 **Name** 및 **RequiredVersion** 매개 변수를 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-123">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="9acfe-124">**\Id** 개체는 파이프라인으로 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-124">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="9acfe-125">`Uninstall-Package`Cmdlet은 개체를 **InputObject** 로 수신 하 고 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-125">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="9acfe-126">또는 `Uninstall-Package` cmdlet에서 **InputObject** 매개 변수에 대 한 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-126">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="9acfe-127">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="9acfe-127">PARAMETERS</span></span>

### <span data-ttu-id="9acfe-128">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="9acfe-128">-AllowClobber</span></span>

<span data-ttu-id="9acfe-129">기존 명령과의 충돌에 대 한 경고 메시지를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-129">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="9acfe-130">설치 중인 명령과 이름이 같은 기존 명령을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-130">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-131">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="9acfe-131">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="9acfe-132">시험판으로 표시 된 패키지를 제거할 수 있도록 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-132">Allows packages marked as prerelease to be uninstalled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-133">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="9acfe-133">-AllVersions</span></span>

<span data-ttu-id="9acfe-134">이 cmdlet은 패키지의 모든 버전을 제거 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-134">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="9acfe-135">-Destination</span><span class="sxs-lookup"><span data-stu-id="9acfe-135">-Destination</span></span>

<span data-ttu-id="9acfe-136">입력 개체의 경로 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-136">Specifies a string of the path to the input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-137">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="9acfe-137">-ExcludeVersion</span></span>

<span data-ttu-id="9acfe-138">스위치를 전환 하 여 폴더 경로에서 버전 번호를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-138">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-139">-Force</span><span class="sxs-lookup"><span data-stu-id="9acfe-139">-Force</span></span>

<span data-ttu-id="9acfe-140">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-140">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9acfe-141">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="9acfe-141">-ForceBootstrap</span></span>

<span data-ttu-id="9acfe-142">**PackageManagement** 가 지정 된 패키지에 대 한 패키지 공급자를 자동으로 설치 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-142">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="9acfe-143">-InputObject</span><span class="sxs-lookup"><span data-stu-id="9acfe-143">-InputObject</span></span>

<span data-ttu-id="9acfe-144">Cmdlet에서 패키지의 **\Id** 개체를 지정 하는 파이프라인 입력을 허용 `Get-Package` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-144">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="9acfe-145">**InputObject** 는 개체를 포함 하는 변수 또는 값으로 **\id** 개체를 수락 합니다 `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="9acfe-145">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="9acfe-146">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="9acfe-146">-InstallUpdate</span></span>

<span data-ttu-id="9acfe-147">에서 업데이트를 제거 함을 나타냅니다 `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="9acfe-147">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-148">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9acfe-148">-MaximumVersion</span></span>

<span data-ttu-id="9acfe-149">제거 하려는 최대 허용 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-149">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="9acfe-150">이 매개 변수를 지정 하지 않으면에서 `Uninstall-Package` 패키지의 최신 버전을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-150">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="9acfe-151">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9acfe-151">-MinimumVersion</span></span>

<span data-ttu-id="9acfe-152">제거 하려는 최소 허용 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-152">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="9acfe-153">이 매개 변수를 추가 하지 않으면 `Uninstall-Package` 은 **MaximumVersion** 매개 변수로 지정 된 버전을 충족 하는 최신 버전의 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-153">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="9acfe-154">-Name</span><span class="sxs-lookup"><span data-stu-id="9acfe-154">-Name</span></span>

<span data-ttu-id="9acfe-155">하나 이상의 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-155">Specifies one or more package names.</span></span> <span data-ttu-id="9acfe-156">여러 패키지 이름을 쉼표로 구분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-156">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="9acfe-157">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="9acfe-157">-NoPathUpdate</span></span>

<span data-ttu-id="9acfe-158">**Nopathupdate** 는 cmdlet에만 적용 됩니다 `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="9acfe-158">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="9acfe-159">**Nopathupdate** 는 공급자가 추가 하는 동적 매개 변수 이며에서 지원 되지 않습니다 `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="9acfe-159">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-160">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="9acfe-160">-PackageManagementProvider</span></span>

<span data-ttu-id="9acfe-161">**PackageManagement** 공급자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-161">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-162">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="9acfe-162">-ProviderName</span></span>

<span data-ttu-id="9acfe-163">패키지를 검색할 패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-163">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="9acfe-164">`Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-164">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="9acfe-165">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9acfe-165">-RequiredVersion</span></span>

<span data-ttu-id="9acfe-166">제거 하려는 패키지의 정확한 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-166">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="9acfe-167">이 매개 변수를 추가 하지 않으면 `Uninstall-Package` 은 **MaximumVersion** 매개 변수로 지정 된 버전을 충족 하는 최신 버전의 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-167">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="9acfe-168">-범위</span><span class="sxs-lookup"><span data-stu-id="9acfe-168">-Scope</span></span>

<span data-ttu-id="9acfe-169">패키지를 제거할 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-169">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="9acfe-170">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9acfe-171">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="9acfe-171">CurrentUser</span></span>
- <span data-ttu-id="9acfe-172">AllUsers</span><span class="sxs-lookup"><span data-stu-id="9acfe-172">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-173">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="9acfe-173">-SkipDependencies</span></span>

<span data-ttu-id="9acfe-174">소프트웨어 종속성 제거를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-174">Skips the uninstallation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-175">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="9acfe-175">-SkipPublisherCheck</span></span>

<span data-ttu-id="9acfe-176">설치 된 버전 보다 최신 버전의 패키지 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-176">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="9acfe-177">예를 들어 신뢰할 수 있는 게시자가 디지털 서명 하지만 새 버전은 디지털 서명 되지 않은 설치 된 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-177">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-178">-Type</span><span class="sxs-lookup"><span data-stu-id="9acfe-178">-Type</span></span>

<span data-ttu-id="9acfe-179">모듈, 스크립트 또는 둘 다를 포함 하는 패키지를 검색할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-179">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="9acfe-180">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-180">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9acfe-181">모듈</span><span class="sxs-lookup"><span data-stu-id="9acfe-181">Module</span></span>
- <span data-ttu-id="9acfe-182">스크립트</span><span class="sxs-lookup"><span data-stu-id="9acfe-182">Script</span></span>
- <span data-ttu-id="9acfe-183">모두</span><span class="sxs-lookup"><span data-stu-id="9acfe-183">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9acfe-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9acfe-184">-Confirm</span></span>

<span data-ttu-id="9acfe-185">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9acfe-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9acfe-186">-WhatIf</span></span>

<span data-ttu-id="9acfe-187">Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="9acfe-187">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="9acfe-188">Cmdlet이 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-188">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="9acfe-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9acfe-189">CommonParameters</span></span>

<span data-ttu-id="9acfe-190">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9acfe-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9acfe-191">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9acfe-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9acfe-192">입력</span><span class="sxs-lookup"><span data-stu-id="9acfe-192">INPUTS</span></span>

### <span data-ttu-id="9acfe-193">`Uninstall-Package` 파이프라인의 **\Id** 개체를 입력으로 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-193">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="9acfe-194">출력</span><span class="sxs-lookup"><span data-stu-id="9acfe-194">OUTPUTS</span></span>

### <span data-ttu-id="9acfe-195">`Uninstall-Package` 는 출력을 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-195">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="9acfe-196">참고</span><span class="sxs-lookup"><span data-stu-id="9acfe-196">NOTES</span></span>

<span data-ttu-id="9acfe-197">명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-197">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="9acfe-198">동적 매개 변수는 패키지 공급자에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-198">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="9acfe-199">`Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="9acfe-199">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="9acfe-200">예를 들어,에는, `Uninstall-Package` 및를 포함 하는 **PowerShellGet** 매개 변수 집합이 있습니다 `-NoPathUpdate` `AllowClobber` `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="9acfe-200">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="9acfe-201">관련 링크</span><span class="sxs-lookup"><span data-stu-id="9acfe-201">RELATED LINKS</span></span>

[<span data-ttu-id="9acfe-202">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="9acfe-202">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="9acfe-203">Find-Package</span><span class="sxs-lookup"><span data-stu-id="9acfe-203">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="9acfe-204">Get-Package</span><span class="sxs-lookup"><span data-stu-id="9acfe-204">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="9acfe-205">Install-Package</span><span class="sxs-lookup"><span data-stu-id="9acfe-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="9acfe-206">Save-Package</span><span class="sxs-lookup"><span data-stu-id="9acfe-206">Save-Package</span></span>](Save-Package.md)
