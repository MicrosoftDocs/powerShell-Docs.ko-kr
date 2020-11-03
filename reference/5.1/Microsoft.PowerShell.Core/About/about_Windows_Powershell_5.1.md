---
description: Windows PowerShell 5.1에 포함 된 새로운 기능에 대해 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/17/2018
online version: https://docs.microsoft.com/powershell/module/?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Windows_PowerShell_5.1
ms.openlocfilehash: 567af048dd137c0287c6eba4ccc42a77055c0c92
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2020
ms.locfileid: "93224906"
---
# <a name="about_windows_powershell_51"></a><span data-ttu-id="7fbb1-104">about_Windows_PowerShell_5.1</span><span class="sxs-lookup"><span data-stu-id="7fbb1-104">about_Windows_PowerShell_5.1</span></span>

## <a name="short-description"></a><span data-ttu-id="7fbb1-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="7fbb1-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="7fbb1-106">Windows PowerShell 5.1에 포함 된 새로운 기능에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-106">Describes new features that are included in Windows PowerShell 5.1.</span></span>

## <a name="long-description"></a><span data-ttu-id="7fbb1-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="7fbb1-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="7fbb1-108">Windows PowerShell 5.1에는 사용을 확장 하 고, 유용성을 개선 하 고, Windows 기반 환경을 보다 쉽게 포괄적으로 제어 하 고 관리할 수 있는 중요 한 새로운 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-108">Windows PowerShell 5.1 includes significant new features that extend its use, improve its usability, and allow you to control and manage Windows-based environments more easily and comprehensively.</span></span>

<span data-ttu-id="7fbb1-109">Windows PowerShell 5.1은 이전 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-109">Windows PowerShell 5.1 is backward-compatible.</span></span> <span data-ttu-id="7fbb1-110">Windows PowerShell 4.0, Windows PowerShell 3.0 및 Windows PowerShell 2.0 용으로 설계 된 cmdlet, 공급자, 모듈, 스냅인, 함수 및 프로필은 일반적으로 Windows PowerShell 5.1에서 변경 없이 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-110">Cmdlets, providers, modules, snap-ins, scripts, functions, and profiles that were designed for Windows PowerShell 4.0, Windows PowerShell 3.0, and Windows PowerShell 2.0 generally work in Windows PowerShell 5.1 without changes.</span></span>

- <span data-ttu-id="7fbb1-111">새 cmdlet: 로컬 사용자 및 그룹; Get-ComputerInfo</span><span class="sxs-lookup"><span data-stu-id="7fbb1-111">New cmdlets: local users and groups; Get-ComputerInfo</span></span>
- <span data-ttu-id="7fbb1-112">서명된 모듈, JEA 모듈 설치 등의 PowerShellGet 개선 사항</span><span class="sxs-lookup"><span data-stu-id="7fbb1-112">PowerShellGet improvements include enforcing signed modules, and installing JEA modules</span></span>
- <span data-ttu-id="7fbb1-113">PackageManagement에서 컨테이너, CBS 설치, EXE 기반 설치, CAB 패키지에 대한 지원 추가</span><span class="sxs-lookup"><span data-stu-id="7fbb1-113">PackageManagement added support for Containers, CBS Setup, EXE-based setup, CAB packages</span></span>
- <span data-ttu-id="7fbb1-114">DSC 및 PowerShell 클래스에 대한 디버깅 개선 사항</span><span class="sxs-lookup"><span data-stu-id="7fbb1-114">Debugging improvements for DSC and PowerShell classes</span></span>
- <span data-ttu-id="7fbb1-115">끌어오기 서버에서 나오는 카탈로그 서명 모듈 적용 및 PowerShellGet cmdlet을 사용할 경우를 비롯한 보안 향상</span><span class="sxs-lookup"><span data-stu-id="7fbb1-115">Security enhancements including enforcement of catalog-signed modules coming from the Pull Server and when using PowerShellGet cmdlets</span></span>
- <span data-ttu-id="7fbb1-116">다양한 사용자 요청 및 문제에 대한 응답</span><span class="sxs-lookup"><span data-stu-id="7fbb1-116">Responses to a number of user requests and issues</span></span>

<span data-ttu-id="7fbb1-117">Windows PowerShell 5.1은 windows Server 2016 및 Windows 10에 기본적으로 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-117">Windows PowerShell 5.1 is installed by default on Windows Server 2016 and Windows 10.</span></span> <span data-ttu-id="7fbb1-118">Windows Server 2012 R2, Windows 8.1 Enterprise 또는 Windows 8.1 Pro에서 Windows PowerShell 5.1을 설치 하려면 [WMF 5.1 설치 및 구성](/powershell/scripting/wmf/setup/install-configure)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-118">To install Windows PowerShell 5.1 on Windows Server 2012 R2, Windows 8.1 Enterprise, or Windows 8.1 Pro, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>
<span data-ttu-id="7fbb1-119">Windows Management Framework 5.1을 설치 하기 전에 다운로드 정보를 읽고 모든 시스템 요구 사항을 충족 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-119">Be sure to read the download details, and meet all system requirements, before you install Windows Management Framework 5.1.</span></span>

<span data-ttu-id="7fbb1-120">Windows [powershell의 새로운 기능](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50)에서 windows powershell 5.1에 대 한 변경 내용을 읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-120">You can also read about changes to Windows PowerShell 5.1 in [What's New in Windows PowerShell](/powershell/scripting/windows-powershell/whats-new/what-s-new-in-windows-powershell-50).</span></span>

## <a name="new-scenarios-and-features-in-wmf-51"></a><span data-ttu-id="7fbb1-121">WMF 5.1의 새로운 시나리오 및 기능</span><span class="sxs-lookup"><span data-stu-id="7fbb1-121">New Scenarios and Features in WMF 5.1</span></span>

> <span data-ttu-id="7fbb1-122">참고: 이 정보는 임시로 제공되며 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-122">Note: This information is preliminary and subject to change.</span></span>

### <a name="powershell-editions"></a><span data-ttu-id="7fbb1-123">PowerShell Edition</span><span class="sxs-lookup"><span data-stu-id="7fbb1-123">PowerShell Editions</span></span>
<span data-ttu-id="7fbb1-124">버전 5.1부터 PowerShell은 다양한 기능 집합 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-124">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="7fbb1-125">**Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-125">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="7fbb1-126">**Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상 지정하는 스크립트 및 모듈과 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-126">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="7fbb1-127">**PowerShell 버전 사용 방법에 대한 자세한 정보**</span><span class="sxs-lookup"><span data-stu-id="7fbb1-127">**Learn more about using PowerShell Editions**</span></span>

- [<span data-ttu-id="7fbb1-128">$PSVersionTable을 사용하여 실행 중인 PowerShell 버전 확인</span><span class="sxs-lookup"><span data-stu-id="7fbb1-128">Determine running edition of PowerShell using $PSVersionTable</span></span>](/powershell/module/microsoft.powershell.core/about/about_automatic_variables)
- [<span data-ttu-id="7fbb1-129">PSEdition 매개 변수를 사용하여 CompatiblePSEditions를 기준으로 Get-Module 결과 필터링</span><span class="sxs-lookup"><span data-stu-id="7fbb1-129">Filter Get-Module results by CompatiblePSEditions using PSEdition parameter</span></span>](/powershell/module/microsoft.powershell.core/get-module)
- [<span data-ttu-id="7fbb1-130">호환되는 PowerShell 버전에서 실행하지 않는 경우 스크립트 실행 방지</span><span class="sxs-lookup"><span data-stu-id="7fbb1-130">Prevent script execution unless run on a compatible edition of PowerShell</span></span>](/powershell/scripting/gallery/concepts/script-psedition-support)
- [<span data-ttu-id="7fbb1-131">특정 PowerShell 버전에 대한 모듈의 호환성 선언</span><span class="sxs-lookup"><span data-stu-id="7fbb1-131">Declare a module's compatibility to specific PowerShell versions</span></span>](/powershell/scripting/gallery/concepts/module-psedition-support)

### <a name="catalog-cmdlets"></a><span data-ttu-id="7fbb1-132">카탈로그 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="7fbb1-132">Catalog Cmdlets</span></span>

<span data-ttu-id="7fbb1-133">두 개의 새로운 cmdlet을 [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) 모듈에 추가했습니다. 이 cmdlet은 Windows 카탈로그 파일을 생성하고 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-133">Two new cmdlets have been added in the [Microsoft.PowerShell.Security](/previous-versions/windows/powershell-scripting/hh847877(v=wps.640)) module; these generate and validate Windows catalog files.</span></span>

#### <a name="new-filecatalog"></a><span data-ttu-id="7fbb1-134">New-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="7fbb1-134">New-FileCatalog</span></span>

<span data-ttu-id="7fbb1-135">New-FileCatalog는 폴더 및 파일 집합에 대한 Windows 카탈로그 파일을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-135">New-FileCatalog creates a Windows catalog file for set of folders and files.</span></span>
<span data-ttu-id="7fbb1-136">이 카탈로그 파일에는 지정된 경로에 있는 모든 파일에 대한 해시가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-136">This catalog file contains hashes for all files in specified paths.</span></span> <span data-ttu-id="7fbb1-137">사용자는 폴더 집합을 이러한 폴더를 나타내는 해당 카탈로그 파일과 함께 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-137">Users can distribute the set of folders along with corresponding catalog file representing those folders.</span></span> <span data-ttu-id="7fbb1-138">이 정보는 카탈로그 생성 시간 이후 폴더가 변경되었는지 확인하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-138">This information is useful to validate whether any changes have been made to the folders since catalog creation time.</span></span>

```
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>]
 [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="7fbb1-139">카탈로그 버전 1과 2가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-139">Catalog versions 1 and 2 are supported.</span></span> <span data-ttu-id="7fbb1-140">버전 1은 SHA1 해시 알고리즘을 사용하여 파일 해시를 만들고 버전 2는 SHA256을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-140">Version 1 uses the SHA1 hashing algorithm to create file hashes; version 2 uses SHA256.</span></span> <span data-ttu-id="7fbb1-141">*Windows Server 2008 R2* 또는 *Windows 7* 에서는 카탈로그 버전 2가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-141">Catalog version 2 is not supported on *Windows Server 2008 R2* or *Windows 7*.</span></span> <span data-ttu-id="7fbb1-142">*Windows 8* , *Windows Server 2012* 및 이후 운영 체제에서는 카탈로그 버전 2를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-142">You should use catalog version 2 on *Windows 8* , *Windows Server 2012* , and later operating systems.</span></span>

<span data-ttu-id="7fbb1-143">카탈로그 파일(위 예에서는 Pester.cat)의 무결성을 확인하려면 [Set-authenticodesignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) cmdlet을 사용하여 카탈로그 파일에 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-143">To verify the integrity of catalog file (Pester.cat in above example), sign it using [Set-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/set-authenticodesignature) cmdlet.</span></span>

#### <a name="test-filecatalog"></a><span data-ttu-id="7fbb1-144">Test-FileCatalog</span><span class="sxs-lookup"><span data-stu-id="7fbb1-144">Test-FileCatalog</span></span>

<span data-ttu-id="7fbb1-145">Test-FileCatalog는 폴더 집합을 나타내는 카탈로그의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-145">Test-FileCatalog validates the catalog representing a set of folders.</span></span>

```
Test-FileCatalog [-Detailed] [-FilesToSkip <String[]>]
 [-CatalogFilePath] <String> [[-Path] <String[]>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

<span data-ttu-id="7fbb1-146">이 cmdlet은 *카탈로그* 에서 찾은 모든 파일 해시 및 해당 상대 경로를 *디스크* 의 파일 해시 및 상대 경로와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-146">This cmdlet compares all the files hashes and their relative paths found in *catalog* with ones on *disk*.</span></span> <span data-ttu-id="7fbb1-147">파일 해시 및 경로 간의 불일치를 발견하면 *ValidationFailed* 와 같은 상태를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-147">If it detects any mismatch between file hashes and paths it returns the status as *ValidationFailed*.</span></span> <span data-ttu-id="7fbb1-148">사용자는 *-Detailed* 매개 변수를 사용하여 이 모든 정보를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-148">Users can retrieve all this information by using the *-Detailed* parameter.</span></span> <span data-ttu-id="7fbb1-149">또한 이 cmdlet은 카탈로그 파일에서 [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) cmdlet을 호출할 때와 동일한 *Signature* 속성에 카탈로그의 서명 상태를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-149">It also displays signing status of catalog in *Signature* property which is equivalent to calling [Get-AuthenticodeSignature](/powershell/module/microsoft.powershell.security/get-authenticodesignature) cmdlet on the catalog file.</span></span> <span data-ttu-id="7fbb1-150">사용자는 *-FilesToSkip* 매개 변수를 사용하여 유효성 검사 시 파일을 건너뛸 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-150">Users can also skip any file during validation by using the *-FilesToSkip* parameter.</span></span>

### <a name="module-analysis-cache"></a><span data-ttu-id="7fbb1-151">모듈 분석 캐시</span><span class="sxs-lookup"><span data-stu-id="7fbb1-151">Module Analysis Cache</span></span>

<span data-ttu-id="7fbb1-152">WMF 5.1부터 PowerShell에서는 내보내는 명령과 같은 모듈에 대한 데이터를 캐시하는 데 사용되는 파일을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-152">Starting with WMF 5.1, PowerShell provides control over the file that is used to cache data about a module, such as the commands it exports.</span></span>

<span data-ttu-id="7fbb1-153">기본적으로 이 캐시 파일은 `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache` 파일에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-153">By default, this cache is stored in the file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span> <span data-ttu-id="7fbb1-154">일반적으로 이 캐시는 시작 시 명령을 검색할 때 읽으며 모듈을 가져오고 잠시 후에 백그라운드 스레드에서 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-154">The cache is typically read at startup while searching for a command and is written on a background thread sometime after a module is imported.</span></span>

<span data-ttu-id="7fbb1-155">캐시의 기본 위치를 변경하려면 PowerShell을 시작하기 전에 `$env:PSModuleAnalysisCachePath` 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-155">To change the default location of the cache, set the `$env:PSModuleAnalysisCachePath` environment variable before starting PowerShell.</span></span> <span data-ttu-id="7fbb1-156">이 환경 변수의 변경 내용은 자식 프로세스에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-156">Changes to this environment variable will only affect children processes.</span></span> <span data-ttu-id="7fbb1-157">PowerShell이 파일을 만들고 쓸 수 있는 전체 경로(파일 이름 포함)를 값으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-157">The value should name a full path (including filename) that PowerShell has permission to create and write files.</span></span> <span data-ttu-id="7fbb1-158">파일 캐시를 사용하지 않도록 설정하려면 이 값을 다음과 같은 잘못된 위치로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-158">To disable the file cache, set this value to an invalid location, for example:</span></span>

```powershell
$env:PSModuleAnalysisCachePath = 'nul'
```

<span data-ttu-id="7fbb1-159">이렇게 하면 잘못된 디바이스에 대한 경로가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-159">This sets the path to an invalid device.</span></span> <span data-ttu-id="7fbb1-160">PowerShell에서 경로에 쓸 수 없는 경우 오류가 반환되지 않지만 추적 프로그램을 사용하여 오류 보고를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-160">If PowerShell can't write to the path, no error is returned, but you can see error reporting by using a tracer:</span></span>

```powershell
Trace-Command -PSHost -Name Modules -Expression {
  Import-Module Microsoft.PowerShell.Management -Force
}
```

<span data-ttu-id="7fbb1-161">캐시를 쓸 때 PowerShell에서는 캐시가 불필요하게 커지지 않도록 더 이상 없는 모듈을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-161">When writing out the cache, PowerShell will check for modules that no longer exist to avoid an unnecessarily large cache.</span></span> <span data-ttu-id="7fbb1-162">때로는 이러한 확인이 필요하지 않을 수도 있으며, 이 경우 다음을 설정하여 확인을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-162">Sometimes these checks are not desirable, in which case you can turn them off by setting:</span></span>

```powershell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

<span data-ttu-id="7fbb1-163">이 환경 변수를 설정하면 현재 프로세스에 즉시 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-163">Setting this environment variable will take effect immediately in the current process.</span></span>

### <a name="specifying-module-version"></a><span data-ttu-id="7fbb1-164">모듈 버전 지정</span><span class="sxs-lookup"><span data-stu-id="7fbb1-164">Specifying module version</span></span>

<span data-ttu-id="7fbb1-165">WMF 5.1에서 `using module`은 PowerShell에서 다른 모듈 관련 생성과 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-165">In WMF 5.1, `using module` behaves the same way as other module-related constructions in PowerShell.</span></span> <span data-ttu-id="7fbb1-166">이전에는 특정 모듈 버전을 지정할 수 없었습니다. 따라서 여러 버전이 있는 경우 오류가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-166">Previously, you had no way to specify a particular module version; if there were multiple versions present, this resulted in an error.</span></span>

<span data-ttu-id="7fbb1-167">WMF 5.1에서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-167">In WMF 5.1:</span></span>

* <span data-ttu-id="7fbb1-168">[ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor)(ModuleSpecification 생성자(해시 테이블))를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-168">You can use [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor).</span></span>
  <span data-ttu-id="7fbb1-169">이 해시 테이블은 `Get-Module -FullyQualifiedName`과 형식이 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-169">This hash table has the same format as `Get-Module -FullyQualifiedName`.</span></span>

  <span data-ttu-id="7fbb1-170">**예제:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span><span class="sxs-lookup"><span data-stu-id="7fbb1-170">**Example:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`</span></span>

* <span data-ttu-id="7fbb1-171">모듈의 여러 버전이 있는 경우 PowerShell에서는 `Import-Module`과 **동일한 해결 논리** 를 사용하고 오류가 발생하지 않습니다. 동작은 `Import-Module` 및 `Import-DscResource`와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-171">If there are multiple versions of the module, PowerShell uses the **same resolution logic** as `Import-Module` and doesn't return an error--the same behavior as `Import-Module` and `Import-DscResource`.</span></span>

### <a name="improvements-to-pester"></a><span data-ttu-id="7fbb1-172">Pester의 향상된 기능</span><span class="sxs-lookup"><span data-stu-id="7fbb1-172">Improvements to Pester</span></span>

<span data-ttu-id="7fbb1-173">WMF 5.1에서는 PowerShell과 함께 제공 되는 Pester 버전이 3.3.5에서 3.4.0로 업데이트 되었으며, GitHub [PR # 484](https://github.com/pester/Pester/pull/484)을 추가 하 여 Nano Server에서 Pester의 더 나은 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-173">In WMF 5.1, the version of Pester that ships with PowerShell has been updated from 3.3.5 to 3.4.0, with the addition of GitHub [PR# 484](https://github.com/pester/Pester/pull/484), which enables better behavior for Pester on Nano Server.</span></span>

<span data-ttu-id="7fbb1-174">[https://github.com/pester/Pester/blob/master/CHANGELOG.md](https://github.com/pester/Pester/blob/master/CHANGELOG.md)에서 ChangeLog.md 파일을 검사하여 버전 3.3.5~3.4.0의 변경 내용을 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7fbb1-174">You can review the changes in versions 3.3.5 to 3.4.0 by inspecting the ChangeLog.md file at: https://github.com/pester/Pester/blob/master/CHANGELOG.md</span></span>

## <a name="keywords"></a><span data-ttu-id="7fbb1-175">어</span><span class="sxs-lookup"><span data-stu-id="7fbb1-175">KEYWORDS</span></span>

<span data-ttu-id="7fbb1-176">Windows PowerShell 5.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="7fbb1-176">What's New in Windows PowerShell 5.1</span></span>
