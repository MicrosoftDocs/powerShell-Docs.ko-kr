---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
title: WMF 5.1의 새로운 시나리오 및 기능
ms.openlocfilehash: b00069aad7422f86d1462a62a6c4bc8a91e46705
ms.sourcegitcommit: 50b66cada6943784b8d3c103cebc3c1e3e286a16
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37090366"
---
# <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="faea5-103">WMF 5.1의 새로운 시나리오 및 기능</span><span class="sxs-lookup"><span data-stu-id="faea5-103">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="faea5-104">참고: 이 정보는 임시로 제공되며 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-104">Note: This information is preliminary and subject to change.</span></span>

## <a name="powershell-editions"></a><span data-ttu-id="faea5-105">PowerShell 버전</span><span class="sxs-lookup"><span data-stu-id="faea5-105">PowerShell Editions</span></span>

<span data-ttu-id="faea5-106">버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-106">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="faea5-107">**Desktop Edition:** .NET Framework에서 구축되며 Server Core 및 Windows 데스크톱과 같은 전체 설치 공간 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 하는 스크립트 및 모듈과의 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="faea5-108">**Core Edition:** .NET Core에서 구축되며 Nano Server 및 Windows IoT와 같은 축소된 설치 공간 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 하는 스크립트 및 모듈과의 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="faea5-109">**PowerShell 버전 사용 방법에 대한 자세한 정보**</span><span class="sxs-lookup"><span data-stu-id="faea5-109">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="faea5-110">$PSVersionTable을 사용하여 실행 중인 PowerShell 버전 확인</span><span class="sxs-lookup"><span data-stu-id="faea5-110">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="faea5-111">PSEdition 매개 변수를 사용하여 CompatiblePSEditions를 기준으로 Get-Module 결과 필터링</span><span class="sxs-lookup"><span data-stu-id="faea5-111">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="faea5-112">호환되는 PowerShell 버전에서 실행하지 않는 경우 스크립트 실행 방지</span><span class="sxs-lookup"><span data-stu-id="faea5-112">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="faea5-113">특정 PowerShell 버전에 대한 모듈의 호환성 선언</span><span class="sxs-lookup"><span data-stu-id="faea5-113">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/gallery/concepts/module-psedition-support)

## <a name="catalog-cmdlets"></a><span data-ttu-id="faea5-114">카탈로그 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="faea5-114">Catalog Cmdlets</span></span>

<span data-ttu-id="faea5-115">두 개의 새로운 cmdlet을 [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) 모듈에 추가했습니다. 이 cmdlet은 Windows 카탈로그 파일을 생성하고 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-115">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/powershell/module/microsoft.powershell.security) module; these generate and validate Windows catalog files.</span></span>

### <a name="new-filecatalog"></a><span data-ttu-id="faea5-116">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="faea5-116">New-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="faea5-117">New-FileCatalog는 폴더 및 파일 집합에 대한 Windows 카탈로그 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-117">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="faea5-118">이 카탈로그 파일에는 지정된 경로에 있는 모든 파일에 대한 해시가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-118">This catalog file contains hashes for all files in specified paths.</span></span>
<span data-ttu-id="faea5-119">사용자는 폴더 집합을 이러한 폴더를 나타내는 해당 카탈로그 파일과 함께 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-119">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span>
<span data-ttu-id="faea5-120">이 정보는 카탈로그 생성 시간 이후 폴더가 변경되었는지 확인하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-120">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="faea5-121">카탈로그 버전 1과 2가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-121">Catalog versions 1 and 2 are supported.</span></span>
<span data-ttu-id="faea5-122">버전 1은 SHA1 해시 알고리즘을 사용하여 파일 해시를 만들고 버전 2는 SHA256을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-122">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span>
<span data-ttu-id="faea5-123">*Windows Server 2008 R2* 또는 *Windows 7*에서는 카탈로그 버전 2가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-123">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span>
<span data-ttu-id="faea5-124">*Windows 8*, *Windows Server 2012* 및 이후 운영 체제에서는 카탈로그 버전 2를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-124">You should use catalog version 2 on *Windows 8*, *Windows Server 2012*, and later operating systems.</span></span>

![](../images/NewFileCatalog.jpg)

<span data-ttu-id="faea5-125">이 cmdlet은 카탈로그 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-125">This creates the catalog file.</span></span>

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

<span data-ttu-id="faea5-126">카탈로그 파일(위 예에서는 Pester.cat)의 무결성을 확인하려면 [Set-authenticodesignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet을 사용하여 카탈로그 파일에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-126">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Set-AuthenticodeSignature) cmdlet.</span></span>

### <a name="test-filecatalog"></a><span data-ttu-id="faea5-127">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="faea5-127">Test-FileCatalog</span></span>
--------------------------------

<span data-ttu-id="faea5-128">Test-FileCatalog는 폴더 집합을 나타내는 카탈로그의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-128">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

<span data-ttu-id="faea5-129">이 cmdlet은 *카탈로그*에서 찾은 모든 파일 해시 및 해당 상대 경로를 *디스크*의 파일 해시 및 상대 경로와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-129">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span>
<span data-ttu-id="faea5-130">파일 해시 및 경로 간의 불일치를 발견하면 *ValidationFailed*와 같은 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-130">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span>
<span data-ttu-id="faea5-131">사용자는 *-Detailed* 매개 변수를 사용하여 이 모든 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-131">Users can retrieve all this information by using the *-Detailed* parameter.</span></span>
<span data-ttu-id="faea5-132">또한 이 cmdlet은 카탈로그 파일에서 [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet을 호출할 때와 동일한 *Signature* 속성에 카탈로그의 서명 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-132">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/Microsoft.PowerShell.Security/Get-AuthenticodeSignature) cmdlet on the catalog file.</span></span>
<span data-ttu-id="faea5-133">사용자는 *-FilesToSkip* 매개 변수를 사용하여 유효성 검사 시 파일을 건너뛸 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-133">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

## <a name="module-analysis-cache"></a><span data-ttu-id="faea5-134">모듈 분석 캐시</span><span class="sxs-lookup"><span data-stu-id="faea5-134">Module Analysis Cache</span></span>

<span data-ttu-id="faea5-135">WMF 5.1부터 PowerShell에서는 내보내는 명령과 같은 모듈에 대한 데이터를 캐시하는 데 사용되는 파일을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-135">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="faea5-136">기본적으로 이 캐시 파일은 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-136">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="faea5-137">일반적으로 이 캐시는 시작 시 명령을 검색할 때 읽으며 모듈을 가져오고 잠시 후에 백그라운드 스레드에서 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-137">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="faea5-138">캐시의 기본 위치를 변경하려면 PowerShell을 시작하기 전에 `$env:PSModuleAnalysisCachePath` 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-138">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span>
<span data-ttu-id="faea5-139">이 환경 변수의 변경 내용은 자식 프로세스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-139">Changes to this environment variable will only affect children processes.</span></span>
<span data-ttu-id="faea5-140">PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-140">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span>
<span data-ttu-id="faea5-141">파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-141">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="faea5-142">이렇게 하면 잘못된 디바이스에 대한 경로가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-142">This sets the path to an invalid device.</span></span>
<span data-ttu-id="faea5-143">PowerShell에서 경로에 쓸 수 없는 경우 오류가 반환되지 않지만 추적 프로그램을 사용하여 오류 보고를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-143">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

<span data-ttu-id="faea5-144">캐시를 쓸 때 PowerShell에서는 캐시가 불필요하게 커지지 않도록 더 이상 없는 모듈을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-144">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span>
<span data-ttu-id="faea5-145">때로는 이러한 확인이 필요하지 않을 수도 있으며, 이 경우 다음을 설정하여 확인을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-145">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="faea5-146">이 환경 변수를 설정하면 현재 프로세스에 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-146">Setting this environment variable will take effect immediately in the current process.</span></span>

## <a name="specifying-module-version"></a><span data-ttu-id="faea5-147">모듈 버전 지정</span><span class="sxs-lookup"><span data-stu-id="faea5-147">Specifying module version</span></span>

<span data-ttu-id="faea5-148">WMF 5.1에서 `using module`은 PowerShell에서 다른 모듈 관련 생성과 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-148">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span>
<span data-ttu-id="faea5-149">이전에는 특정 모듈 버전을 지정할 수 없었습니다. 따라서 여러 버전이 있는 경우 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-149">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="faea5-150">WMF 5.1에서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-150">In WMF 5.1:</span></span>

- <span data-ttu-id="faea5-151">[ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_)(ModuleSpecification 생성자(해시 테이블))를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-151">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>
<span data-ttu-id="faea5-152">이 해시 테이블은 `Get-Module -FullyQualifiedName`과 형식이 같습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-152">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

<span data-ttu-id="faea5-153">**예:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="faea5-153">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

- <span data-ttu-id="faea5-154">모듈의 여러 버전이 있는 경우 PowerShell에서는 `Import-Module`과 **동일한 해결 논리**를 사용하고 오류가 발생하지 않습니다. 동작은 `Import-Module` 및 `Import-DscResource`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-154">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

## <a name="improvements-to-pester"></a><span data-ttu-id="faea5-155">Pester의 향상된 기능</span><span class="sxs-lookup"><span data-stu-id="faea5-155">Improvements to Pester</span></span>

<span data-ttu-id="faea5-156">WMF 5.1에서는 PowerShell과 함께 제공되는 Pester 버전이 3.3.5에서 3.4.0으로 업데이트되었고, Nano Server에서 Pester가 더 잘 동작할 수 있도록 커밋 https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-156">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="faea5-157">https://github.com/pester/Pester/blob/master/CHANGELOG.md에서 ChangeLog.md 파일을 검사하여 버전 3.3.5~3.4.0의 변경 내용을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="faea5-157">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>
