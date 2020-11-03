---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 058ed7f90e63bd7ca7a29cf6c89864a30255662a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2020
ms.locfileid: "93213290"
---
# <span data-ttu-id="b7bf0-103">Install-Package</span><span class="sxs-lookup"><span data-stu-id="b7bf0-103">Install-Package</span></span>

## <span data-ttu-id="b7bf0-104">개요</span><span class="sxs-lookup"><span data-stu-id="b7bf0-104">SYNOPSIS</span></span>
<span data-ttu-id="b7bf0-105">하나 이상의 소프트웨어 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="b7bf0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7bf0-106">SYNTAX</span></span>

### <span data-ttu-id="b7bf0-107">PackageBySearch (기본값)</span><span class="sxs-lookup"><span data-stu-id="b7bf0-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7bf0-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-109">프로그램: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7bf0-109">Programs:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-110">프로그램: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7bf0-110">Programs:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-111">msi: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7bf0-111">msi:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-112">msi: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7bf0-112">msi:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-113">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7bf0-113">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-114">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7bf0-114">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-115">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="b7bf0-115">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="b7bf0-116">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="b7bf0-116">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="b7bf0-117">설명</span><span class="sxs-lookup"><span data-stu-id="b7bf0-117">DESCRIPTION</span></span>

<span data-ttu-id="b7bf0-118">`Install-Package`Cmdlet은 로컬 컴퓨터에 소프트웨어 패키지를 하나 이상 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-118">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="b7bf0-119">여러 소프트웨어 소스를 사용 하는 경우 `Get-PackageProvider` 및를 사용 `Get-PackageSource` 하 여 공급자에 대 한 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-119">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="b7bf0-120">예제</span><span class="sxs-lookup"><span data-stu-id="b7bf0-120">EXAMPLES</span></span>

### <span data-ttu-id="b7bf0-121">예제 1: 패키지 이름으로 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="b7bf0-121">Example 1: Install a package by package name</span></span>

<span data-ttu-id="b7bf0-122">`Install-Package`Cmdlet은 소프트웨어 패키지와 해당 종속성을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-122">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="b7bf0-123">`Install-Package` 매개 변수를 사용 하 여 패키지 **이름** 및 **원본을** 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-123">`Install-Package` uses parameters to specify the packages **Name** and **Source** .</span></span> <span data-ttu-id="b7bf0-124">**Credential** 매개 변수는 패키지를 설치할 수 있는 권한이 있는 도메인 사용자 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-124">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="b7bf0-125">명령은 사용자 계정 암호를 입력 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-125">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="b7bf0-126">예제 2: Find-Package을 사용 하 여 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="b7bf0-126">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="b7bf0-127">이 예제에서에 의해 반환 된 개체는 `Find-Package` 파이프라인으로 전송 되 고에 의해 설치 됩니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-127">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="b7bf0-128">`Find-Package` 는 **이름** 및 **원본** 매개 변수를 사용 하 여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-128">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="b7bf0-129">개체는 파이프라인으로 전송 되 고 `Install-Package` 로컬 컴퓨터에 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-129">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="b7bf0-130">예제 3: 버전 범위를 지정 하 여 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="b7bf0-130">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="b7bf0-131">`Install-Package` 는 **MinimumVersion** 및 **MaximumVersion** 매개 변수를 사용 하 여 소프트웨어 버전의 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-131">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="b7bf0-132">`Install-Package` 는 **이름** 및 **원본** 매개 변수를 사용 하 여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-132">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="b7bf0-133">**MinimumVersion** 및 **MaximumVersion** 매개 변수는 소프트웨어 버전의 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-133">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="b7bf0-134">범위에서 가장 높은 버전이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-134">The highest version in the range is installed.</span></span>

## <span data-ttu-id="b7bf0-135">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="b7bf0-135">PARAMETERS</span></span>

### <span data-ttu-id="b7bf0-136">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="b7bf0-136">-AcceptLicense</span></span>

 <span data-ttu-id="b7bf0-137">**Acceptlicense** 는 설치 하는 동안 자동으로 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-137">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="b7bf0-138">-AllowClobber</span></span>

<span data-ttu-id="b7bf0-139">기존 명령과의 충돌에 대 한 경고 메시지를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="b7bf0-140">설치 중인 명령과 이름이 같은 기존 명령을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-140">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="b7bf0-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="b7bf0-142">시험판으로 표시 된 패키지를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-142">Allows the installation of packages marked as prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-143">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="b7bf0-143">-AllVersions</span></span>

<span data-ttu-id="b7bf0-144">`Install-Package` 패키지의 사용 가능한 모든 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-144">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="b7bf0-145">기본적으로 최신 버전만 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-145">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="b7bf0-146">-Command</span><span class="sxs-lookup"><span data-stu-id="b7bf0-146">-Command</span></span>

<span data-ttu-id="b7bf0-147">검색 하는 명령을 하나 이상 지정 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-147">Specifies one or more commands that `Install-Package` searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-148">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="b7bf0-148">-ConfigFile</span></span>

<span data-ttu-id="b7bf0-149">구성 파일을 포함 하는 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-149">Specifies a path that contains a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-150">-포함</span><span class="sxs-lookup"><span data-stu-id="b7bf0-150">-Contains</span></span>

<span data-ttu-id="b7bf0-151">`Install-Package`**Contains** 매개 변수가 개체의 속성 값과 일치 하는 값을 지정 하는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-151">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="b7bf0-152">-Credential</span></span>

<span data-ttu-id="b7bf0-153">컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-153">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="b7bf0-154">**User01** , **Domain01\User01** 등의 사용자 이름을 입력 하거나, cmdlet에 의해 생성 되는 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-154">Type a user name, such as **User01** , **Domain01\User01** , or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="b7bf0-155">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-155">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="b7bf0-156">**Credential** 매개 변수를 지정 하지 않으면는 `Install-Package` 현재 사용자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-156">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="b7bf0-157">-Destination</span><span class="sxs-lookup"><span data-stu-id="b7bf0-157">-Destination</span></span>

<span data-ttu-id="b7bf0-158">입력 개체의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-158">Specifies a path to an input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-159">-Get-dscresource</span><span class="sxs-lookup"><span data-stu-id="b7bf0-159">-DscResource</span></span>

<span data-ttu-id="b7bf0-160">에서 검색 한 하나 이상의 DSC (Desired State Configuration) 리소스를 지정 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-160">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="b7bf0-161">Cmdlet을 사용 `Find-DscResource` 하 여 DSC 리소스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-161">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-162">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="b7bf0-162">-ExcludeVersion</span></span>

<span data-ttu-id="b7bf0-163">스위치를 전환 하 여 폴더 경로에서 버전 번호를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-163">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="b7bf0-164">-Filter</span></span>

<span data-ttu-id="b7bf0-165">**이름** 및 **설명** 속성에서 검색할 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-165">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-166">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="b7bf0-166">-FilterOnTag</span></span>

<span data-ttu-id="b7bf0-167">결과를 필터링 하 고 지정 된 태그를 포함 하지 않는 결과를 제외 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-167">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-168">-Force</span><span class="sxs-lookup"><span data-stu-id="b7bf0-168">-Force</span></span>

<span data-ttu-id="b7bf0-169">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-169">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="b7bf0-170">는 보안을 제외 하 고 다음이 발생 하지 않도록 하는 제한을 재정의 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-170">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="b7bf0-171">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="b7bf0-171">-ForceBootstrap</span></span>

<span data-ttu-id="b7bf0-172">**PackageManagement** 가 지정 된 패키지에 대 한 패키지 공급자를 자동으로 설치 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-172">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="b7bf0-173">-헤더</span><span class="sxs-lookup"><span data-stu-id="b7bf0-173">-Headers</span></span>

<span data-ttu-id="b7bf0-174">패키지 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-174">Specifies the package headers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-175">-포함</span><span class="sxs-lookup"><span data-stu-id="b7bf0-175">-Includes</span></span>

<span data-ttu-id="b7bf0-176">에서 모든 패키지 유형을 찾아야 하는지 여부를 지정 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-176">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="b7bf0-177">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-177">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b7bf0-178">cmdlet</span><span class="sxs-lookup"><span data-stu-id="b7bf0-178">Cmdlet</span></span>
- <span data-ttu-id="b7bf0-179">DscResource</span><span class="sxs-lookup"><span data-stu-id="b7bf0-179">DscResource</span></span>
- <span data-ttu-id="b7bf0-180">함수</span><span class="sxs-lookup"><span data-stu-id="b7bf0-180">Function</span></span>
- <span data-ttu-id="b7bf0-181">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="b7bf0-181">RoleCapability</span></span>
- <span data-ttu-id="b7bf0-182">워크플로</span><span class="sxs-lookup"><span data-stu-id="b7bf0-182">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-183">-InputObject</span><span class="sxs-lookup"><span data-stu-id="b7bf0-183">-InputObject</span></span>

<span data-ttu-id="b7bf0-184">파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-184">Accepts pipeline input.</span></span> <span data-ttu-id="b7bf0-185">패키지의 **\Id** 유형을 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-185">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="b7bf0-186">`Find-Package`**\Id** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-186">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="b7bf0-187">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="b7bf0-187">-InstallUpdate</span></span>

<span data-ttu-id="b7bf0-188">에서 업데이트를 설치 함을 나타냅니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-188">Indicates that `Install-Package` installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-189">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b7bf0-189">-MaximumVersion</span></span>

<span data-ttu-id="b7bf0-190">설치 하려는 최대 허용 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-190">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="b7bf0-191">이 매개 변수를 지정 하지 않으면에서 `Install-Package` 패키지의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-191">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="b7bf0-192">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b7bf0-192">-MinimumVersion</span></span>

<span data-ttu-id="b7bf0-193">설치 하려는 최소 허용 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-193">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="b7bf0-194">이 매개 변수를 추가 하지 않으면 `Install-Package` 은 **MaximumVersion** 매개 변수로 지정 된 모든 버전을 충족 하는 패키지의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-194">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="b7bf0-195">-Name</span><span class="sxs-lookup"><span data-stu-id="b7bf0-195">-Name</span></span>

<span data-ttu-id="b7bf0-196">하나 이상의 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-196">Specifies one or more package names.</span></span> <span data-ttu-id="b7bf0-197">여러 패키지 이름을 쉼표로 구분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-197">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="b7bf0-198">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="b7bf0-198">-NoPathUpdate</span></span>

<span data-ttu-id="b7bf0-199">**Nopathupdate** 는 cmdlet에만 적용 됩니다 `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-199">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="b7bf0-200">**Nopathupdate** 는 공급자가 추가 하는 동적 매개 변수 이며에서 지원 되지 않습니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-200">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-201">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="b7bf0-201">-PackageManagementProvider</span></span>

<span data-ttu-id="b7bf0-202">**PackageManagement** 공급자의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-202">Specifies the name of the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-203">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="b7bf0-203">-ProviderName</span></span>

<span data-ttu-id="b7bf0-204">패키지 검색의 범위를 지정할 패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-204">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="b7bf0-205">`Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-205">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="b7bf0-206">-프록시</span><span class="sxs-lookup"><span data-stu-id="b7bf0-206">-Proxy</span></span>

<span data-ttu-id="b7bf0-207">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-207">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="b7bf0-208">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b7bf0-208">-ProxyCredential</span></span>

<span data-ttu-id="b7bf0-209">**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-209">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="b7bf0-210">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="b7bf0-210">-PublishLocation</span></span>

<span data-ttu-id="b7bf0-211">패키지의 게시 된 위치에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-211">Specifies the path to a package's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-212">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b7bf0-212">-RequiredVersion</span></span>

<span data-ttu-id="b7bf0-213">설치 하려는 패키지의 정확한 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-213">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="b7bf0-214">이 매개 변수를 추가 하지 않으면 `Install-Package` 은 **MaximumVersion** 매개 변수로 지정 된 모든 버전을 충족 하는 패키지의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-214">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="b7bf0-215">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="b7bf0-215">-RoleCapability</span></span>

<span data-ttu-id="b7bf0-216">역할 기능의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-216">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-217">-범위</span><span class="sxs-lookup"><span data-stu-id="b7bf0-217">-Scope</span></span>

<span data-ttu-id="b7bf0-218">패키지를 설치할 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-218">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="b7bf0-219">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-219">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b7bf0-220">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="b7bf0-220">CurrentUser</span></span>
- <span data-ttu-id="b7bf0-221">AllUsers</span><span class="sxs-lookup"><span data-stu-id="b7bf0-221">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-222">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="b7bf0-222">-ScriptPublishLocation</span></span>

<span data-ttu-id="b7bf0-223">스크립트의 게시 된 위치에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-223">Specifies the path to a script's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-224">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="b7bf0-224">-ScriptSourceLocation</span></span>

<span data-ttu-id="b7bf0-225">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-225">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-226">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="b7bf0-226">-SkipDependencies</span></span>

<span data-ttu-id="b7bf0-227">소프트웨어 종속성의 설치를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-227">Skips the installation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-228">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="b7bf0-228">-SkipPublisherCheck</span></span>

<span data-ttu-id="b7bf0-229">설치 된 버전 보다 최신 버전의 패키지 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-229">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="b7bf0-230">예를 들어 신뢰할 수 있는 게시자가 디지털 서명 하지만 새 버전은 디지털 서명 되지 않은 설치 된 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-230">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-231">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="b7bf0-231">-SkipValidate</span></span>

<span data-ttu-id="b7bf0-232">패키지의 자격 증명에 대 한 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-232">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-233">-Source</span><span class="sxs-lookup"><span data-stu-id="b7bf0-233">-Source</span></span>

<span data-ttu-id="b7bf0-234">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-234">Specifies one or more package sources.</span></span> <span data-ttu-id="b7bf0-235">여러 패키지 원본 이름을 쉼표로 구분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-235">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="b7bf0-236">Cmdlet을 실행 하 여 패키지 원본 이름을 가져올 수 있습니다 `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-236">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="b7bf0-237">-Tag</span><span class="sxs-lookup"><span data-stu-id="b7bf0-237">-Tag</span></span>

<span data-ttu-id="b7bf0-238">패키지 메타 데이터에서 검색할 문자열을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-238">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-239">-Type</span><span class="sxs-lookup"><span data-stu-id="b7bf0-239">-Type</span></span>

<span data-ttu-id="b7bf0-240">모듈, 스크립트 또는 둘 다를 포함 하는 패키지를 검색할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-240">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="b7bf0-241">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-241">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="b7bf0-242">모듈</span><span class="sxs-lookup"><span data-stu-id="b7bf0-242">Module</span></span>
- <span data-ttu-id="b7bf0-243">스크립트</span><span class="sxs-lookup"><span data-stu-id="b7bf0-243">Script</span></span>
- <span data-ttu-id="b7bf0-244">모두</span><span class="sxs-lookup"><span data-stu-id="b7bf0-244">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-245">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b7bf0-245">-Confirm</span></span>

<span data-ttu-id="b7bf0-246">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-246">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b7bf0-247">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b7bf0-247">-WhatIf</span></span>

<span data-ttu-id="b7bf0-248">Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-248">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="b7bf0-249">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-249">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b7bf0-250">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="b7bf0-250">-AdditionalArguments</span></span>

<span data-ttu-id="b7bf0-251">설치할 추가 인수를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-251">Specifies one or more additional arguments for installation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi:PackageBySearch, msi:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-252">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="b7bf0-252">-IncludeSystemComponent</span></span>

<span data-ttu-id="b7bf0-253">이 cmdlet이 결과의 시스템 구성 요소를 포함 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-253">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-254">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="b7bf0-254">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="b7bf0-255">이 cmdlet의 결과에 Windows installer가 포함 되어 있음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-255">Indicates that this cmdlet includes the Windows installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b7bf0-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7bf0-256">CommonParameters</span></span>

<span data-ttu-id="b7bf0-257">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7bf0-258">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b7bf0-259">입력</span><span class="sxs-lookup"><span data-stu-id="b7bf0-259">INPUTS</span></span>

### <span data-ttu-id="b7bf0-260">`Install-Package` 파이프라인의 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-260">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="b7bf0-261">출력</span><span class="sxs-lookup"><span data-stu-id="b7bf0-261">OUTPUTS</span></span>

### <span data-ttu-id="b7bf0-262">\Id []</span><span class="sxs-lookup"><span data-stu-id="b7bf0-262">SoftwareIdentity[]</span></span>

## <span data-ttu-id="b7bf0-263">참고</span><span class="sxs-lookup"><span data-stu-id="b7bf0-263">NOTES</span></span>

<span data-ttu-id="b7bf0-264">명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-264">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="b7bf0-265">동적 매개 변수는 패키지 공급자에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-265">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="b7bf0-266">`Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7bf0-266">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="b7bf0-267">예를 들어,에는, `Install-Package` 및를 포함 하는 **PowerShellGet** 매개 변수 집합이 있습니다 `-NoPathUpdate` `AllowClobber` `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="b7bf0-267">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="b7bf0-268">관련 링크</span><span class="sxs-lookup"><span data-stu-id="b7bf0-268">RELATED LINKS</span></span>

[<span data-ttu-id="b7bf0-269">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="b7bf0-269">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="b7bf0-270">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="b7bf0-270">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="b7bf0-271">Get-Help</span><span class="sxs-lookup"><span data-stu-id="b7bf0-271">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="b7bf0-272">Get-Package</span><span class="sxs-lookup"><span data-stu-id="b7bf0-272">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="b7bf0-273">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b7bf0-273">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="b7bf0-274">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b7bf0-274">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="b7bf0-275">Find-Package</span><span class="sxs-lookup"><span data-stu-id="b7bf0-275">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="b7bf0-276">Save-Package</span><span class="sxs-lookup"><span data-stu-id="b7bf0-276">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="b7bf0-277">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="b7bf0-277">Uninstall-Package</span></span>](Uninstall-Package.md)
