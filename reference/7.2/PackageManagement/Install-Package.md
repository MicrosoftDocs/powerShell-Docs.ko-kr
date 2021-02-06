---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-Package
ms.openlocfilehash: 1518be0d34733e36217b46cbbf496e580ec7b649
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99605502"
---
# <span data-ttu-id="3e783-102">Install-Package</span><span class="sxs-lookup"><span data-stu-id="3e783-102">Install-Package</span></span>

## <span data-ttu-id="3e783-103">개요</span><span class="sxs-lookup"><span data-stu-id="3e783-103">SYNOPSIS</span></span>
<span data-ttu-id="3e783-104">하나 이상의 소프트웨어 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-104">Installs one or more software packages.</span></span>

## <span data-ttu-id="3e783-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e783-105">SYNTAX</span></span>

### <span data-ttu-id="3e783-106">PackageBySearch (기본값)</span><span class="sxs-lookup"><span data-stu-id="3e783-106">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="3e783-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="3e783-107">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="3e783-108">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="3e783-108">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="3e783-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="3e783-109">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="3e783-110">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="3e783-110">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="3e783-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="3e783-111">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="3e783-112">설명</span><span class="sxs-lookup"><span data-stu-id="3e783-112">DESCRIPTION</span></span>

<span data-ttu-id="3e783-113">`Install-Package`Cmdlet은 로컬 컴퓨터에 소프트웨어 패키지를 하나 이상 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-113">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="3e783-114">여러 소프트웨어 소스를 사용 하는 경우 `Get-PackageProvider` 및를 사용 `Get-PackageSource` 하 여 공급자에 대 한 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-114">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="3e783-115">예제</span><span class="sxs-lookup"><span data-stu-id="3e783-115">EXAMPLES</span></span>

### <span data-ttu-id="3e783-116">예제 1: 패키지 이름으로 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="3e783-116">Example 1: Install a package by package name</span></span>

<span data-ttu-id="3e783-117">`Install-Package`Cmdlet은 소프트웨어 패키지와 해당 종속성을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-117">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="3e783-118">`Install-Package` 매개 변수를 사용 하 여 패키지 **이름** 및 **원본을** 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-118">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="3e783-119">**Credential** 매개 변수는 패키지를 설치할 수 있는 권한이 있는 도메인 사용자 계정을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-119">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="3e783-120">명령은 사용자 계정 암호를 입력 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-120">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="3e783-121">예제 2: Find-Package을 사용 하 여 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="3e783-121">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="3e783-122">이 예제에서에 의해 반환 된 개체는 `Find-Package` 파이프라인으로 전송 되 고에 의해 설치 됩니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-122">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="3e783-123">`Find-Package` 는 **이름** 및 **원본** 매개 변수를 사용 하 여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-123">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="3e783-124">개체는 파이프라인으로 전송 되 고 `Install-Package` 로컬 컴퓨터에 패키지를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-124">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="3e783-125">예제 3: 버전 범위를 지정 하 여 패키지 설치</span><span class="sxs-lookup"><span data-stu-id="3e783-125">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="3e783-126">`Install-Package` 는 **MinimumVersion** 및 **MaximumVersion** 매개 변수를 사용 하 여 소프트웨어 버전의 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-126">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="3e783-127">`Install-Package` 는 **이름** 및 **원본** 매개 변수를 사용 하 여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-127">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="3e783-128">**MinimumVersion** 및 **MaximumVersion** 매개 변수는 소프트웨어 버전의 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-128">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="3e783-129">범위에서 가장 높은 버전이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-129">The highest version in the range is installed.</span></span>

## <span data-ttu-id="3e783-130">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="3e783-130">PARAMETERS</span></span>

### <span data-ttu-id="3e783-131">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3e783-131">-AcceptLicense</span></span>

 <span data-ttu-id="3e783-132">**Acceptlicense** 는 설치 하는 동안 자동으로 사용권 계약에 동의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-132">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="3e783-133">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="3e783-133">-AllowClobber</span></span>

<span data-ttu-id="3e783-134">기존 명령과의 충돌에 대 한 경고 메시지를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-134">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="3e783-135">설치 중인 명령과 이름이 같은 기존 명령을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-135">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="3e783-136">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="3e783-136">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="3e783-137">시험판으로 표시 된 패키지를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-137">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="3e783-138">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="3e783-138">-AllVersions</span></span>

<span data-ttu-id="3e783-139">`Install-Package` 패키지의 사용 가능한 모든 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-139">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="3e783-140">기본적으로 최신 버전만 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-140">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="3e783-141">-Command</span><span class="sxs-lookup"><span data-stu-id="3e783-141">-Command</span></span>

<span data-ttu-id="3e783-142">검색 하는 명령을 하나 이상 지정 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-142">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="3e783-143">-Smi-s</span><span class="sxs-lookup"><span data-stu-id="3e783-143">-ConfigFile</span></span>

<span data-ttu-id="3e783-144">구성 파일을 포함 하는 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-144">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="3e783-145">-포함</span><span class="sxs-lookup"><span data-stu-id="3e783-145">-Contains</span></span>

<span data-ttu-id="3e783-146">`Install-Package`**Contains** 매개 변수가 개체의 속성 값과 일치 하는 값을 지정 하는 경우 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-146">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="3e783-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="3e783-147">-Credential</span></span>

<span data-ttu-id="3e783-148">컴퓨터에 액세스할 수 있는 권한이 있는 사용자 계정을 지정 하 고 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-148">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="3e783-149">**User01**, **Domain01\User01** 등의 사용자 이름을 입력 하거나, cmdlet에 의해 생성 되는 **PSCredential** 개체를 입력 합니다 `Get-Credential` .</span><span class="sxs-lookup"><span data-stu-id="3e783-149">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="3e783-150">사용자 이름을 입력 하면 암호를 입력 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-150">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="3e783-151">**Credential** 매개 변수를 지정 하지 않으면는 `Install-Package` 현재 사용자를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-151">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="3e783-152">-Destination</span><span class="sxs-lookup"><span data-stu-id="3e783-152">-Destination</span></span>

<span data-ttu-id="3e783-153">입력 개체의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-153">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="3e783-154">-Get-dscresource</span><span class="sxs-lookup"><span data-stu-id="3e783-154">-DscResource</span></span>

<span data-ttu-id="3e783-155">에서 검색 한 하나 이상의 DSC (Desired State Configuration) 리소스를 지정 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-155">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="3e783-156">Cmdlet을 사용 `Find-DscResource` 하 여 DSC 리소스를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-156">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="3e783-157">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="3e783-157">-ExcludeVersion</span></span>

<span data-ttu-id="3e783-158">스위치를 전환 하 여 폴더 경로에서 버전 번호를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-158">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="3e783-159">-Filter</span><span class="sxs-lookup"><span data-stu-id="3e783-159">-Filter</span></span>

<span data-ttu-id="3e783-160">**이름** 및 **설명** 속성에서 검색할 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-160">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="3e783-161">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="3e783-161">-FilterOnTag</span></span>

<span data-ttu-id="3e783-162">결과를 필터링 하 고 지정 된 태그를 포함 하지 않는 결과를 제외 하는 태그를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-162">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="3e783-163">-Force</span><span class="sxs-lookup"><span data-stu-id="3e783-163">-Force</span></span>

<span data-ttu-id="3e783-164">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-164">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="3e783-165">는 보안을 제외 하 고 다음이 발생 하지 않도록 하는 제한을 재정의 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-165">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="3e783-166">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="3e783-166">-ForceBootstrap</span></span>

<span data-ttu-id="3e783-167">**PackageManagement** 가 지정 된 패키지에 대 한 패키지 공급자를 자동으로 설치 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-167">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="3e783-168">-헤더</span><span class="sxs-lookup"><span data-stu-id="3e783-168">-Headers</span></span>

<span data-ttu-id="3e783-169">패키지 헤더를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-169">Specifies the package headers.</span></span>

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

### <span data-ttu-id="3e783-170">-포함</span><span class="sxs-lookup"><span data-stu-id="3e783-170">-Includes</span></span>

<span data-ttu-id="3e783-171">에서 모든 패키지 유형을 찾아야 하는지 여부를 지정 합니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-171">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="3e783-172">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-172">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3e783-173">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e783-173">Cmdlet</span></span>
- <span data-ttu-id="3e783-174">DscResource</span><span class="sxs-lookup"><span data-stu-id="3e783-174">DscResource</span></span>
- <span data-ttu-id="3e783-175">함수</span><span class="sxs-lookup"><span data-stu-id="3e783-175">Function</span></span>
- <span data-ttu-id="3e783-176">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="3e783-176">RoleCapability</span></span>
- <span data-ttu-id="3e783-177">워크플로</span><span class="sxs-lookup"><span data-stu-id="3e783-177">Workflow</span></span>

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

### <span data-ttu-id="3e783-178">-InputObject</span><span class="sxs-lookup"><span data-stu-id="3e783-178">-InputObject</span></span>

<span data-ttu-id="3e783-179">파이프라인 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-179">Accepts pipeline input.</span></span> <span data-ttu-id="3e783-180">패키지의 **\Id** 유형을 사용 하 여 패키지를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-180">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="3e783-181">`Find-Package`**\Id** 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-181">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="3e783-182">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="3e783-182">-InstallUpdate</span></span>

<span data-ttu-id="3e783-183">에서 업데이트를 설치 함을 나타냅니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-183">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="3e783-184">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3e783-184">-MaximumVersion</span></span>

<span data-ttu-id="3e783-185">설치 하려는 최대 허용 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-185">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="3e783-186">이 매개 변수를 지정 하지 않으면에서 `Install-Package` 패키지의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-186">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="3e783-187">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3e783-187">-MinimumVersion</span></span>

<span data-ttu-id="3e783-188">설치 하려는 최소 허용 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-188">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="3e783-189">이 매개 변수를 추가 하지 않으면 `Install-Package` 은 **MaximumVersion** 매개 변수로 지정 된 모든 버전을 충족 하는 패키지의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-189">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="3e783-190">-Name</span><span class="sxs-lookup"><span data-stu-id="3e783-190">-Name</span></span>

<span data-ttu-id="3e783-191">하나 이상의 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-191">Specifies one or more package names.</span></span> <span data-ttu-id="3e783-192">여러 패키지 이름을 쉼표로 구분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-192">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="3e783-193">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="3e783-193">-NoPathUpdate</span></span>

<span data-ttu-id="3e783-194">**Nopathupdate** 는 cmdlet에만 적용 됩니다 `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="3e783-194">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="3e783-195">**Nopathupdate** 는 공급자가 추가 하는 동적 매개 변수 이며에서 지원 되지 않습니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-195">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="3e783-196">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="3e783-196">-PackageManagementProvider</span></span>

<span data-ttu-id="3e783-197">**PackageManagement** 공급자의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-197">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="3e783-198">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="3e783-198">-ProviderName</span></span>

<span data-ttu-id="3e783-199">패키지 검색의 범위를 지정할 패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-199">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="3e783-200">`Get-PackageProvider` cmdlet을 실행하여 패키지 공급자 이름을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-200">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="3e783-201">-프록시</span><span class="sxs-lookup"><span data-stu-id="3e783-201">-Proxy</span></span>

<span data-ttu-id="3e783-202">인터넷 리소스에 직접 연결 하는 대신 요청에 대 한 프록시 서버를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-202">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="3e783-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="3e783-203">-ProxyCredential</span></span>

<span data-ttu-id="3e783-204">**프록시** 매개 변수로 지정 된 프록시 서버를 사용할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-204">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="3e783-205">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="3e783-205">-PublishLocation</span></span>

<span data-ttu-id="3e783-206">패키지의 게시 된 위치에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-206">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="3e783-207">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3e783-207">-RequiredVersion</span></span>

<span data-ttu-id="3e783-208">설치 하려는 패키지의 정확한 허용 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-208">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="3e783-209">이 매개 변수를 추가 하지 않으면 `Install-Package` 은 **MaximumVersion** 매개 변수로 지정 된 모든 버전을 충족 하는 패키지의 최신 버전을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-209">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="3e783-210">-Find-rolecapability</span><span class="sxs-lookup"><span data-stu-id="3e783-210">-RoleCapability</span></span>

<span data-ttu-id="3e783-211">역할 기능의 배열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-211">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="3e783-212">-범위</span><span class="sxs-lookup"><span data-stu-id="3e783-212">-Scope</span></span>

<span data-ttu-id="3e783-213">패키지를 설치할 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-213">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="3e783-214">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3e783-215">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="3e783-215">CurrentUser</span></span>
- <span data-ttu-id="3e783-216">AllUsers</span><span class="sxs-lookup"><span data-stu-id="3e783-216">AllUsers</span></span>

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

### <span data-ttu-id="3e783-217">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="3e783-217">-ScriptPublishLocation</span></span>

<span data-ttu-id="3e783-218">스크립트의 게시 된 위치에 대 한 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-218">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="3e783-219">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="3e783-219">-ScriptSourceLocation</span></span>

<span data-ttu-id="3e783-220">스크립트 원본 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-220">Specifies the script source location.</span></span>

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

### <span data-ttu-id="3e783-221">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="3e783-221">-SkipDependencies</span></span>

<span data-ttu-id="3e783-222">소프트웨어 종속성의 설치를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-222">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="3e783-223">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="3e783-223">-SkipPublisherCheck</span></span>

<span data-ttu-id="3e783-224">설치 된 버전 보다 최신 버전의 패키지 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-224">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="3e783-225">예를 들어 신뢰할 수 있는 게시자가 디지털 서명 하지만 새 버전은 디지털 서명 되지 않은 설치 된 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-225">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="3e783-226">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="3e783-226">-SkipValidate</span></span>

<span data-ttu-id="3e783-227">패키지의 자격 증명에 대 한 유효성 검사를 건너뛰는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-227">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="3e783-228">-Source</span><span class="sxs-lookup"><span data-stu-id="3e783-228">-Source</span></span>

<span data-ttu-id="3e783-229">패키지 소스를 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-229">Specifies one or more package sources.</span></span> <span data-ttu-id="3e783-230">여러 패키지 원본 이름을 쉼표로 구분 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-230">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="3e783-231">Cmdlet을 실행 하 여 패키지 원본 이름을 가져올 수 있습니다 `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="3e783-231">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="3e783-232">-Tag</span><span class="sxs-lookup"><span data-stu-id="3e783-232">-Tag</span></span>

<span data-ttu-id="3e783-233">패키지 메타 데이터에서 검색할 문자열을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-233">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="3e783-234">-Type</span><span class="sxs-lookup"><span data-stu-id="3e783-234">-Type</span></span>

<span data-ttu-id="3e783-235">모듈, 스크립트 또는 둘 다를 포함 하는 패키지를 검색할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-235">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="3e783-236">이 매개 변수에 허용 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-236">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3e783-237">모듈</span><span class="sxs-lookup"><span data-stu-id="3e783-237">Module</span></span>
- <span data-ttu-id="3e783-238">스크립트</span><span class="sxs-lookup"><span data-stu-id="3e783-238">Script</span></span>
- <span data-ttu-id="3e783-239">모두</span><span class="sxs-lookup"><span data-stu-id="3e783-239">All</span></span>

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

### <span data-ttu-id="3e783-240">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3e783-240">-Confirm</span></span>

<span data-ttu-id="3e783-241">cmdlet을 실행하기 전에 확인을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-241">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3e783-242">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3e783-242">-WhatIf</span></span>

<span data-ttu-id="3e783-243">Cmdlet이 실행 될 경우 발생 하는 상황을 보여 줍니다 `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e783-243">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="3e783-244">cmdlet은 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-244">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3e783-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e783-245">CommonParameters</span></span>

<span data-ttu-id="3e783-246">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e783-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e783-247">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e783-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e783-248">입력</span><span class="sxs-lookup"><span data-stu-id="3e783-248">INPUTS</span></span>

### <span data-ttu-id="3e783-249">`Install-Package` 파이프라인의 입력을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-249">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="3e783-250">출력</span><span class="sxs-lookup"><span data-stu-id="3e783-250">OUTPUTS</span></span>

### <span data-ttu-id="3e783-251">\Id []</span><span class="sxs-lookup"><span data-stu-id="3e783-251">SoftwareIdentity[]</span></span>

## <span data-ttu-id="3e783-252">참고</span><span class="sxs-lookup"><span data-stu-id="3e783-252">NOTES</span></span>

<span data-ttu-id="3e783-253">명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-253">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="3e783-254">동적 매개 변수는 패키지 공급자에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-254">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="3e783-255">`Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-255">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="3e783-256">예를 들어,에는, `Install-Package` 및를 포함 하는 **PowerShellGet** 매개 변수 집합이 있습니다 `-NoPathUpdate` `AllowClobber` `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="3e783-256">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3e783-257">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-257">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="3e783-258">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-258">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="3e783-259">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="3e783-259">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="3e783-260">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e783-260">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="3e783-261">관련 링크</span><span class="sxs-lookup"><span data-stu-id="3e783-261">RELATED LINKS</span></span>

[<span data-ttu-id="3e783-262">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="3e783-262">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="3e783-263">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="3e783-263">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="3e783-264">Get-Help</span><span class="sxs-lookup"><span data-stu-id="3e783-264">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="3e783-265">Get-Package</span><span class="sxs-lookup"><span data-stu-id="3e783-265">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="3e783-266">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3e783-266">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="3e783-267">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3e783-267">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="3e783-268">Find-Package</span><span class="sxs-lookup"><span data-stu-id="3e783-268">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="3e783-269">Save-Package</span><span class="sxs-lookup"><span data-stu-id="3e783-269">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="3e783-270">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="3e783-270">Uninstall-Package</span></span>](Uninstall-Package.md)
