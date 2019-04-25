---
ms.date: 09/26/2017
contributor: keithb
keywords: gallery,powershell,cmdlet,psget
title: 시험판 모듈 버전
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084864"
---
# <a name="prerelease-module-versions"></a><span data-ttu-id="dbe47-103">시험판 모듈 버전</span><span class="sxs-lookup"><span data-stu-id="dbe47-103">Prerelease Module Versions</span></span>

<span data-ttu-id="dbe47-104">버전 1.6.0부터 PowerShellGet 및 PowerShell 갤러리에서 시험판으로 1.0.0보다 큰 버전에 대한 태그 지정을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-104">Starting with version 1.6.0, PowerShellGet and the PowerShell Gallery provide support for tagging versions greater than 1.0.0 as a prerelease.</span></span> <span data-ttu-id="dbe47-105">이 기능이 출시되기 전에는 시험판 패키지가 0으로 시작하는 버전으로 제한되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-105">Prior to this feature, prerelease packages were limited to having a version beginning with 0.</span></span> <span data-ttu-id="dbe47-106">이러한 기능의 목표는 PowerShell 버전 3 이상 또는 기존 PowerShellGet 버전 및 이전 버전과의 호환성을 손상하지 않으면서 [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) 버전 관리 규칙을 더 효율적으로 지원하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-106">The goal of these features is to provide greater support for [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) versioning convention without breaking backwards compatibility with PowerShell versions 3 and above, or existing versions of PowerShellGet.</span></span> <span data-ttu-id="dbe47-107">이 항목에서는 모듈의 특정 기능에 중점을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-107">This topic focuses on the module-specific features.</span></span> <span data-ttu-id="dbe47-108">스크립트에 해당하는 기능은 [시험판 스크립트 버전](script-prerelease-support.md) 항목에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-108">The equivalent features for scripts are in the [Prerelease Versions of Scripts](script-prerelease-support.md) topic.</span></span> <span data-ttu-id="dbe47-109">게시자는 먼저 이러한 기능을 사용하여 모듈 또는 스크립트를 2.5.0-alpha 버전으로 식별하고, 나중에 해당 시험판 버전을 대체하는 2.5.0 프로덕션 준비 버전을 출시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-109">Using these features, publishers can identify a module or script as version 2.5.0-alpha, and later release a production-ready version 2.5.0 that supersedes the prerelease version.</span></span>

<span data-ttu-id="dbe47-110">상위 수준의 시험판 모듈 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-110">At a high level, the prerelease module features include:</span></span>

- <span data-ttu-id="dbe47-111">모듈 매니페스트의 PSData 섹션에 Prerelease 문자열을 추가하면 해당 모듈이 시험판 버전으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-111">Adding a Prerelease string to the PSData section of the module manifest identifies the module as a prerelease version.</span></span> <span data-ttu-id="dbe47-112">모듈이 PowerShell 갤러리에 게시되면 매니페스트에서 이 데이터를 추출하여 시험판 패키지를 식별하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-112">When the module is published to the PowerShell Gallery, this data is extracted from the manifest, and used to identify prerelease packages.</span></span>
- <span data-ttu-id="dbe47-113">시험판 패키지를 가져오려면 PowerShellGet 명령 `Find-Module`, `Install-Module`, `Update-Module` 및 `Save-Module`에 `-AllowPrerelease` 플래그를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-113">Acquiring prerelease packages requires adding `-AllowPrerelease` flag to the PowerShellGet commands `Find-Module`, `Install-Module`, `Update-Module`, and `Save-Module`.</span></span> <span data-ttu-id="dbe47-114">플래그를 지정하지 않으면 시험판 패키지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-114">If the flag is not specified, prerelease packages will not be shown.</span></span>
- <span data-ttu-id="dbe47-115">`Find-Module`, `Get-InstalledModule` 및 PowerShell 갤러리에 표시되는 모듈 버전은 2.5.0-alpha와 같이 Prerelease 문자열이 추가된 단일 문자열로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-115">Module versions displayed by `Find-Module`, `Get-InstalledModule`, and in the PowerShell Gallery will be displayed as a single string with the Prerelease string appended, as in 2.5.0-alpha.</span></span>

<span data-ttu-id="dbe47-116">기능에 대한 자세한 내용은 아래에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-116">Details for the features are included below.</span></span>

<span data-ttu-id="dbe47-117">이러한 변경 내용은 PowerShell에 기본 제공되는 모듈 버전 지원에 영향을 주지 않으며 PowerShell 3.0, 4.0 및 5와 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-117">These changes do not affect the module version support that is built into PowerShell, and are compatible with PowerShell 3.0, 4.0, and 5.</span></span>

## <a name="identifying-a-module-version-as-a-prerelease"></a><span data-ttu-id="dbe47-118">모듈 버전을 시험판 버전으로 식별</span><span class="sxs-lookup"><span data-stu-id="dbe47-118">Identifying a module version as a prerelease</span></span>

<span data-ttu-id="dbe47-119">PowerShellGet으로 시험판 버전을 지원하려면 모듈 매니페스트 내에서 다음 두 필드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-119">PowerShellGet support for prerelease versions requires the use of two fields within the Module Manifest:</span></span>

- <span data-ttu-id="dbe47-120">시험판 버전이 사용되는 경우 모듈 매니페스트에 포함된 ModuleVersion이 세 부분으로 구성된 버전이어야 하며 기존 PowerShell 버전 관리를 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-120">The ModuleVersion included in the module manifest must be a 3-part version if a prerelease version is used, and must comply with existing PowerShell versioning.</span></span> <span data-ttu-id="dbe47-121">버전 형식은 A.B.C이며, 여기서 A, B 및 C는 모두 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-121">The version format would be A.B.C, where A, B, and C are all integers.</span></span>
- <span data-ttu-id="dbe47-122">Prerelease 문자열은 모듈 매니페스트에 있는PrivateData의 PSData 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-122">The Prerelease string is specified in the module manifest, in the PSData section of PrivateData.</span></span>

<span data-ttu-id="dbe47-123">Prerelease 문자열에 대한 자세한 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-123">Detailed requirements on the Prerelease string are below.</span></span>

<span data-ttu-id="dbe47-124">모듈을 시험판으로 정의하는 모듈 매니페스트의 예제 섹션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-124">An example section of a module manifest that defines a module as a prerelease would look like the following:</span></span>

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

<span data-ttu-id="dbe47-125">Prerelease 문자열의 세부 요구 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-125">The detailed requirements for Prerelease string are:</span></span>

- <span data-ttu-id="dbe47-126">ModuleVersion이 Major.Minor.Build에 해당하는 3개 세그먼트로 구성된 경우에만 Prerelease 문자열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-126">Prerelease string may only be specified when the ModuleVersion is 3 segments for Major.Minor.Build.</span></span> <span data-ttu-id="dbe47-127">이는 SemVer v1.0.0과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-127">This aligns with SemVer v1.0.0.</span></span>
- <span data-ttu-id="dbe47-128">하이픈은 Build 숫자와 Prerelease 문자열 사이의 구분 기호입니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-128">A hyphen is the delimiter between the Build number and the Prerelease string.</span></span> <span data-ttu-id="dbe47-129">Prerelease 문자열에서 하이픈은 첫 번째 문자로만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-129">A hyphen may be included in the Prerelease string as the first character, only.</span></span>
- <span data-ttu-id="dbe47-130">Prerelease 문자열에는 ASCII 영숫자[0-9, A-Z, a-z, -]만 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-130">The Prerelease string may contain only ASCII alphanumerics [0-9A-Za-z-].</span></span> <span data-ttu-id="dbe47-131">Prerelease 문자열은 alpha 문자로 시작하는 것이 좋습니다. 이렇게 하면 패키지 목록을 검색할 때 시험판 버전임을 쉽게 식별할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-131">It is a best practice to begin the Prerelease string with an alpha character, as it will be easier to identify that this is a prerelease version when scanning a list of packages.</span></span>
- <span data-ttu-id="dbe47-132">현재 SemVer v1.0.0 시험판 문자열만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-132">Only SemVer v1.0.0 prerelease strings are supported at this time.</span></span> <span data-ttu-id="dbe47-133">Prerelease 문자열에는 마침표 또는 +[.+]가 **포함되지 않아야** 하지만, SemVer 2.0에서는 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-133">Prerelease string **must not** contain either period or + [.+], which are allowed in SemVer 2.0.</span></span>
- <span data-ttu-id="dbe47-134">지원되는 Prerelease 문자열의 예: -alpha, -alpha1, -BETA, -update20171020</span><span class="sxs-lookup"><span data-stu-id="dbe47-134">Examples of supported Prerelease string are: -alpha, -alpha1, -BETA, -update20171020</span></span>

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a><span data-ttu-id="dbe47-135">정렬 순서 및 설치 폴더에 대한 시험판 버전 관리 효과</span><span class="sxs-lookup"><span data-stu-id="dbe47-135">Prerelease versioning impact on sort order and installation folders</span></span>

<span data-ttu-id="dbe47-136">시험판 버전을 사용하면 정렬 순서가 변경됩니다. 이는 PowerShell 갤러리에 게시할 때 및 PowerShellGet 명령을 사용하여 모듈을 설치할 때 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-136">Sort order changes when using a prerelease version, which is important when publishing to the PowerShell Gallery, and when installing modules using PowerShellGet commands.</span></span> <span data-ttu-id="dbe47-137">두 모듈에 대한 Prerelease 문자열이 지정되면 정렬 순서는 하이픈 다음의 문자열 부분을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-137">If the Prerelease string is specified for two modules, the sort order is based on the string portion following the hyphen.</span></span> <span data-ttu-id="dbe47-138">따라서 2.5.0-alpha 버전은 2.5.0-beta보다 낮으며, 2.5.0-beta는 2.5.0-gamma보다 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-138">So, version 2.5.0-alpha is less than 2.5.0-beta, which is less than 2.5.0-gamma.</span></span> <span data-ttu-id="dbe47-139">두 모듈에 동일한 ModuleVersion이 있고 그 중 하나에만 Prerelease 문자열이 있는 경우, Prerelease 문자열이 없는 모듈이 프로덕션 준비 버전으로 간주되며 Prerelease 문자열이 포함된 시험판 버전보다 높은 버전으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-139">If two modules have the same ModuleVersion, and only one has a Prerelease string, the module without the Prerelease string is assumed to be the production-ready version and will be sorted as a greater version than the prerelease version (which includes the Prerelease string).</span></span> <span data-ttu-id="dbe47-140">예를 들어 릴리스 2.5.0과 2.5.0-beta를 비교하는 경우 2.5.0 버전이 두 버전 중 더 높은 버전으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-140">As an example, when comparing releases 2.5.0 and 2.5.0-beta, the 2.5.0 version will be considered the greater of the two.</span></span>

<span data-ttu-id="dbe47-141">PowerShell 갤러리에 게시할 때 게시되는 모듈의 버전은 기본적으로 PowerShell 갤러리에 있는 이전에 게시한 버전보다 더 높은 버전이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-141">When publishing to the PowerShell Gallery, by default the version of the module being published must have a greater version than any previously-published version that is in the PowerShell Gallery.</span></span>

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a><span data-ttu-id="dbe47-142">PowerShellGet 명령으로 시험판 패키지 찾기 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="dbe47-142">Finding and acquiring prerelease packages using PowerShellGet commands</span></span>

<span data-ttu-id="dbe47-143">Find-Module, Install-Module, Update-Module 및 Save-Module PowerShellGet 명령을 사용하여 시험판 패키지를 처리하려면 -AllowPrerelease 플래그를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-143">Dealing with prerelease packages using PowerShellGet Find-Module, Install-Module, Update-Module, and Save-Module commands requires adding the -AllowPrerelease flag.</span></span> <span data-ttu-id="dbe47-144">-AllowPrerelease 플래그를 지정하면 시험판 패키지가 있는 경우 해당 패키지가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-144">If -AllowPrerelease is specified, prerelease packages will be included if they are present.</span></span> <span data-ttu-id="dbe47-145">-AllowPrerelease 플래그를 지정하지 않으면 시험판 패키지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-145">If -AllowPrerelease flag is not specified, prerelease packages will not be shown.</span></span>

<span data-ttu-id="dbe47-146">PowerShellGet 모듈 명령에서 이 플래그에 대한 유일한 예외로 Get-InstalledModule 및 Uninstall-Module을 사용하는 일부 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-146">The only exceptions to this in the PowerShellGet module commands are Get-InstalledModule, and some cases with Uninstall-Module.</span></span>

- <span data-ttu-id="dbe47-147">Get-InstalledModule은 항상 모듈에 대한 버전 문자열에 있는 시험판 정보를 자동으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-147">Get-InstalledModule always will automatically show the prerelease information in the version string for modules.</span></span>
- <span data-ttu-id="dbe47-148">__지정된 버전이 없는 경우__ Uninstall-Module은 기본적으로 모듈의 최신 버전을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-148">Uninstall-Module will by default uninstall the most recent version of a module, if __no version__ is specified.</span></span> <span data-ttu-id="dbe47-149">해당 동작은 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-149">That behavior has not changed.</span></span> <span data-ttu-id="dbe47-150">그러나 -RequiredVersion을 사용하여 시험판 버전이 지정되는 경우 -AllowPrerelease가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-150">However, if a prerelease version is specified using -RequiredVersion, -AllowPrerelease will be required.</span></span>

## <a name="examples"></a><span data-ttu-id="dbe47-151">예</span><span class="sxs-lookup"><span data-stu-id="dbe47-151">Examples</span></span>

<span data-ttu-id="dbe47-152">PowerShell 갤러리에 TestPackage 모듈 버전 1.8.0 및 1.9.0-alpha가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-152">Assume the PowerShell Gallery has TestPackage module versions 1.8.0 and 1.9.0-alpha.</span></span> <span data-ttu-id="dbe47-153">`-AllowPrerelease`가 지정되지 않은 경우에는 버전 1.8.0만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-153">If `-AllowPrerelease` is not specified, only version 1.8.0 will be returned.</span></span>

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="dbe47-154">시험판을 설치하려면 항상 -AllowPrerelease를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-154">To install a prerelease, always specify -AllowPrerelease.</span></span> <span data-ttu-id="dbe47-155">시험판 버전 문자열을 지정하는 것은 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-155">Specifying a prerelease version string is not sufficient.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

<span data-ttu-id="dbe47-156">-AllowPrerelease가 지정되지 않았으므로 이전 명령이 실패했습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-156">The previous command failed because -AllowPrerelease was not specified.</span></span> <span data-ttu-id="dbe47-157">`-AllowPrerelease`를 추가하면 성공합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-157">Adding `-AllowPrerelease` will result in success.</span></span>

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

<span data-ttu-id="dbe47-158">지정된 시험판으로 인해서만 다른 모듈 버전을 나란히 설치하는 것은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-158">Side-by-side installation of versions of a module that differ only due to the prerelease specified is not supported.</span></span> <span data-ttu-id="dbe47-159">PowerShellGet을 사용하여 모듈을 설치할 때 ModuleVersion을 사용하여 폴더 이름을 만들어 동일한 모듈의 다른 버전을 나란히 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-159">When installing a module using PowerShellGet, different versions of the same module are installed side-by-side by creating a folder name using the ModuleVersion.</span></span> <span data-ttu-id="dbe47-160">시험판 문자열이 없는 ModuleVersion이 폴더 이름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-160">The ModuleVersion, without the prerelease string, is used for the folder name.</span></span> <span data-ttu-id="dbe47-161">사용자가 MyModule 버전 2.5.0-alpha를 설치하면 `MyModule\2.5.0` 폴더에 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-161">If a user installs MyModule version 2.5.0-alpha, it will be installed to the `MyModule\2.5.0` folder.</span></span> <span data-ttu-id="dbe47-162">그런 다음 사용자가 2.5.0-beta를 설치하면 2.5.0-beta 버전은 `MyModule\2.5.0` 폴더의 내용을 **덮어씁니다**.</span><span class="sxs-lookup"><span data-stu-id="dbe47-162">If the user then installs 2.5.0-beta, the 2.5.0-beta version will **overwrite** the contents of the folder `MyModule\2.5.0`.</span></span> <span data-ttu-id="dbe47-163">이 방법의 장점 중 하나는 프로덕션 준비 버전을 설치한 후에 시험판 버전을 제거할 필요가 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-163">One advantage to this approach is that there is no need to un-install the prerelease version after installing the production-ready version.</span></span> <span data-ttu-id="dbe47-164">아래 예제에서는 예상되는 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-164">The example below shows what to expect:</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

<span data-ttu-id="dbe47-165">-RequiredVersion이 제공되지 않은 경우 Uninstall-Module은 최신 버전의 모듈을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-165">Uninstall-Module will remove the latest version of a module when -RequiredVersion is not supplied.</span></span>
<span data-ttu-id="dbe47-166">-RequiredVersion을 지정하고 시험판인 경우 -AllowPrerelease를 명령에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dbe47-166">If -RequiredVersion is specified, and is a prerelease, -AllowPrerelease must be added to the command.</span></span>

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a><span data-ttu-id="dbe47-167">자세한 내용</span><span class="sxs-lookup"><span data-stu-id="dbe47-167">More details</span></span>

- [<span data-ttu-id="dbe47-168">시험판 스크립트 버전</span><span class="sxs-lookup"><span data-stu-id="dbe47-168">Prerelease Script Versions</span></span>](script-prerelease-support.md)
- [<span data-ttu-id="dbe47-169">Find-Module</span><span class="sxs-lookup"><span data-stu-id="dbe47-169">Find-Module</span></span>](/powershell/module/powershellget/find-module)
- [<span data-ttu-id="dbe47-170">Install-Module</span><span class="sxs-lookup"><span data-stu-id="dbe47-170">Install-Module</span></span>](/powershell/module/powershellget/install-module)
- [<span data-ttu-id="dbe47-171">Save-Module</span><span class="sxs-lookup"><span data-stu-id="dbe47-171">Save-Module</span></span>](/powershell/module/powershellget/save-module)
- [<span data-ttu-id="dbe47-172">Update-Module</span><span class="sxs-lookup"><span data-stu-id="dbe47-172">Update-Module</span></span>](/powershell/module/powershellget/Update-Module)
- [<span data-ttu-id="dbe47-173">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="dbe47-173">Get-InstalledModule</span></span>](/powershell/module/powershellget/get-installedmodule)
- [<span data-ttu-id="dbe47-174">UnInstall-Module</span><span class="sxs-lookup"><span data-stu-id="dbe47-174">UnInstall-Module</span></span>](/powershell/module/powershellget/uninstall-module)
