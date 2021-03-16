---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: c26365eb5b4833c4982fa54e742521cf72307e99
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2020
ms.locfileid: "99601257"
---
# <span data-ttu-id="e4f33-102">Get-Package</span><span class="sxs-lookup"><span data-stu-id="e4f33-102">Get-Package</span></span>

## <span data-ttu-id="e4f33-103">개요</span><span class="sxs-lookup"><span data-stu-id="e4f33-103">SYNOPSIS</span></span>
<span data-ttu-id="e4f33-104">**PackageManagement** 를 사용 하 여 설치 된 모든 소프트웨어 패키지 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-104">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="e4f33-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e4f33-105">SYNTAX</span></span>

### <span data-ttu-id="e4f33-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="e4f33-106">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="e4f33-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="e4f33-107">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="e4f33-108">설명</span><span class="sxs-lookup"><span data-stu-id="e4f33-108">DESCRIPTION</span></span>

<span data-ttu-id="e4f33-109">`Get-Package`Cmdlet은 **PackageManagement** 를 사용 하 여 설치 된 로컬 컴퓨터의 모든 소프트웨어 패키지 목록을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-109">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="e4f33-110">`Get-Package`또는 명령이 나 스크립트의 일부로 실행 하 여 원격 컴퓨터에서를 실행할 수 있습니다 `Invoke-Command` `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="e4f33-110">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="e4f33-111">예제</span><span class="sxs-lookup"><span data-stu-id="e4f33-111">EXAMPLES</span></span>

### <span data-ttu-id="e4f33-112">예제 1: 설치 된 모든 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="e4f33-112">Example 1: Get all installed packages</span></span>

<span data-ttu-id="e4f33-113">`Get-Package`Cmdlet은 로컬 컴퓨터에 설치 된 모든 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-113">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="e4f33-114">예 2: 원격 컴퓨터에 설치 된 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="e4f33-114">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="e4f33-115">이 명령은 원격 컴퓨터에서 **PackageManagement** 에 의해 설치 된 패키지 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-115">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="e4f33-116">이 명령은 지정 된 사용자의 암호를 제공 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-116">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="e4f33-117">`Invoke-Command`**ComputerName** 매개 변수를 사용 하 여 원격 컴퓨터 **Server01** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-117">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="e4f33-118">**Credential** 매개 변수는 컴퓨터에서 명령을 실행할 수 있는 권한이 있는 도메인 및 사용자 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-118">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="e4f33-119">**ScriptBlock** 매개 변수는 `Get-Package` 원격 컴퓨터에서 cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-119">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="e4f33-120">예제 3: 지정 된 공급자에 대 한 패키지 가져오기</span><span class="sxs-lookup"><span data-stu-id="e4f33-120">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="e4f33-121">이 명령은 특정 공급자의 로컬 컴퓨터에 설치 된 소프트웨어 패키지를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-121">This command gets software packages installed on the local computer from a specific provider.</span></span>

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="e4f33-122">`Get-Package`**ProviderName** 매개 변수를 사용 하 여 특정 공급자 **PowerShellGet** 을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-122">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="e4f33-123">**모든** 버전 매개 변수는 설치 된 각 버전을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-123">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="e4f33-124">예제 4: 특정 패키지의 정확한 버전 가져오기</span><span class="sxs-lookup"><span data-stu-id="e4f33-124">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="e4f33-125">이 명령은 설치 된 패키지의 특정 버전을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-125">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="e4f33-126">패키지의 여러 버전을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-126">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="e4f33-127">`Get-Package`**name** 매개 변수를 사용 하 여 패키지 이름 **PackageManagement** 를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-127">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="e4f33-128">**ProviderName** 매개 변수는 공급자 ( **PowerShellGet**)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-128">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="e4f33-129">**필수 버전** 매개 변수는 설치 된 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-129">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="e4f33-130">예 5: 패키지 제거</span><span class="sxs-lookup"><span data-stu-id="e4f33-130">Example 5: Uninstall a package</span></span>

<span data-ttu-id="e4f33-131">이 예에서는 패키지 정보를 가져온 다음 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-131">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="e4f33-132">`Get-Package`**name** 매개 변수를 사용 하 여 **posh-git** 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-132">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="e4f33-133">**RequiredVersion** 매개 변수는 패키지의 특정 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-133">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="e4f33-134">개체는 파이프라인에서 cmdlet으로 전송 됩니다 `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="e4f33-134">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="e4f33-135">`Uninstall-Package` 패키지를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-135">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="e4f33-136">PARAMETERS</span><span class="sxs-lookup"><span data-stu-id="e4f33-136">PARAMETERS</span></span>

### <span data-ttu-id="e4f33-137">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="e4f33-137">-AllowClobber</span></span>

<span data-ttu-id="e4f33-138">기존 명령과의 충돌에 대 한 경고 메시지를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-138">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="e4f33-139">모듈에 의해 설치 되는 명령과 이름이 같은 기존 명령을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-139">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

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

### <span data-ttu-id="e4f33-140">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="e4f33-140">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="e4f33-141">결과에서 시험판으로 표시 된 패키지를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-141">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="e4f33-142">-Allversions)</span><span class="sxs-lookup"><span data-stu-id="e4f33-142">-AllVersions</span></span>

<span data-ttu-id="e4f33-143">에서 `Get-Package` 사용 가능한 패키지 버전을 모두 반환 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-143">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="e4f33-144">기본적으로는 `Get-Package` 사용 가능한 최신 버전만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-144">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="e4f33-145">-Destination</span><span class="sxs-lookup"><span data-stu-id="e4f33-145">-Destination</span></span>

<span data-ttu-id="e4f33-146">압축을 푼 패키지 파일을 포함 하는 디렉터리의 경로를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-146">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="e4f33-147">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="e4f33-147">-ExcludeVersion</span></span>

<span data-ttu-id="e4f33-148">스위치를 전환 하 여 폴더 경로에서 버전 번호를 제외 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-148">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="e4f33-149">-Force</span><span class="sxs-lookup"><span data-stu-id="e4f33-149">-Force</span></span>

<span data-ttu-id="e4f33-150">사용자 확인을 요청하지 않고 명령을 강제 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-150">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="e4f33-151">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="e4f33-151">-ForceBootstrap</span></span>

<span data-ttu-id="e4f33-152">PackageManagement에서 `Get-Package` 패키지  공급자를 자동으로 설치 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-152">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="e4f33-153">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="e4f33-153">-InstallUpdate</span></span>

<span data-ttu-id="e4f33-154">이 cmdlet이 업데이트를 설치 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-154">Indicates that this cmdlet installs updates.</span></span>

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

### <span data-ttu-id="e4f33-155">-MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="e4f33-155">-MaximumVersion</span></span>

<span data-ttu-id="e4f33-156">검색 하려는 최대 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-156">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="e4f33-157">-MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="e4f33-157">-MinimumVersion</span></span>

<span data-ttu-id="e4f33-158">찾으려는 최소 패키지 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-158">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="e4f33-159">더 높은 버전을 사용할 수 있는 경우 해당 버전이 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-159">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="e4f33-160">-Name</span><span class="sxs-lookup"><span data-stu-id="e4f33-160">-Name</span></span>

<span data-ttu-id="e4f33-161">하나 이상의 패키지 이름 또는 와일드 카드 문자를 포함 하는 패키지 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-161">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="e4f33-162">여러 패키지 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-162">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="e4f33-163">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="e4f33-163">-NoPathUpdate</span></span>

<span data-ttu-id="e4f33-164">**Nopathupdate** 는 cmdlet에만 적용 됩니다 `Install-Script` .</span><span class="sxs-lookup"><span data-stu-id="e4f33-164">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="e4f33-165">**Nopathupdate** 는 공급자가 추가 하는 동적 매개 변수 이며에서 지원 되지 않습니다 `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="e4f33-165">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

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

### <span data-ttu-id="e4f33-166">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="e4f33-166">-PackageManagementProvider</span></span>

<span data-ttu-id="e4f33-167">패키지 관리 공급자의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-167">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="e4f33-168">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="e4f33-168">-ProviderName</span></span>

<span data-ttu-id="e4f33-169">패키지 공급자 이름을 하나 이상 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-169">Specifies one or more package provider names.</span></span> <span data-ttu-id="e4f33-170">여러 패키지 공급자 이름을 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-170">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="e4f33-171">사용 `Get-PackageProvider` 가능한 패키지 공급자 목록을 가져오는 데 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-171">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="e4f33-172">-RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="e4f33-172">-RequiredVersion</span></span>

<span data-ttu-id="e4f33-173">찾을 패키지의 정확한 버전을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-173">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="e4f33-174">-범위</span><span class="sxs-lookup"><span data-stu-id="e4f33-174">-Scope</span></span>

<span data-ttu-id="e4f33-175">패키지에 대 한 검색 범위를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-175">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e4f33-176">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="e4f33-176">-SkipDependencies</span></span>

<span data-ttu-id="e4f33-177">에서 패키지 종속성 찾기를 건너뛰도록 지정 하는 스위치입니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-177">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="e4f33-178">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="e4f33-178">-SkipPublisherCheck</span></span>

<span data-ttu-id="e4f33-179">설치 된 버전 보다 최신 버전의 패키지 버전을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-179">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="e4f33-180">예를 들어 신뢰할 수 있는 게시자가 디지털 서명 하지만 새 버전은 디지털 서명 되지 않은 설치 된 패키지입니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-180">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="e4f33-181">-Type</span><span class="sxs-lookup"><span data-stu-id="e4f33-181">-Type</span></span>

<span data-ttu-id="e4f33-182">모듈, 스크립트 또는 중 하나를 사용 하 여 패키지를 검색할지 여부를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-182">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="e4f33-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e4f33-183">CommonParameters</span></span>

<span data-ttu-id="e4f33-184">이 cmdlet 일반 매개 변수를 지원합니다. -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction 및 -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e4f33-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e4f33-185">자세한 내용은 [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4f33-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e4f33-186">입력</span><span class="sxs-lookup"><span data-stu-id="e4f33-186">INPUTS</span></span>

## <span data-ttu-id="e4f33-187">출력</span><span class="sxs-lookup"><span data-stu-id="e4f33-187">OUTPUTS</span></span>

### <span data-ttu-id="e4f33-188">\Id []</span><span class="sxs-lookup"><span data-stu-id="e4f33-188">SoftwareIdentity[]</span></span>

## <span data-ttu-id="e4f33-189">참고</span><span class="sxs-lookup"><span data-stu-id="e4f33-189">NOTES</span></span>

<span data-ttu-id="e4f33-190">명령에 패키지 공급자를 포함 하면 cmdlet에서 동적 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-190">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="e4f33-191">동적 매개 변수는 패키지 공급자에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-191">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="e4f33-192">`Get-Help`Cmdlet은 cmdlet의 매개 변수 집합을 나열 하 고 공급자의 매개 변수 집합을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-192">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="e4f33-193">예를 들어,에는, `Get-Package` 및를 포함 하는 **PowerShellGet** 매개 변수 집합이 있습니다 `-NoPathUpdate` `AllowClobber` `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="e4f33-193">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e4f33-194">2020년 4월부터 PowerShell 갤러리는 더 이상 TLS(전송 계층 보안) 버전 1.0 및 1.1을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-194">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="e4f33-195">TLS 1.2 이상을 사용하지 않을 경우 PowerShell 갤러리에 액세스하려고 하면 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-195">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="e4f33-196">다음 명령을 사용하여 TLS 1.2를 사용하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e4f33-196">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="e4f33-197">자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e4f33-197">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="e4f33-198">관련 링크</span><span class="sxs-lookup"><span data-stu-id="e4f33-198">RELATED LINKS</span></span>

[<span data-ttu-id="e4f33-199">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="e4f33-199">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="e4f33-200">Enter-PSSession</span><span class="sxs-lookup"><span data-stu-id="e4f33-200">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="e4f33-201">Find-Package</span><span class="sxs-lookup"><span data-stu-id="e4f33-201">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="e4f33-202">Get-Help</span><span class="sxs-lookup"><span data-stu-id="e4f33-202">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="e4f33-203">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="e4f33-203">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="e4f33-204">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="e4f33-204">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="e4f33-205">Install-Package</span><span class="sxs-lookup"><span data-stu-id="e4f33-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="e4f33-206">Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="e4f33-206">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="e4f33-207">Save-Package</span><span class="sxs-lookup"><span data-stu-id="e4f33-207">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="e4f33-208">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="e4f33-208">Uninstall-Package</span></span>](Uninstall-Package.md)