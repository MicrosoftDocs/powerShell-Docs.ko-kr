---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget,갤러리
title: 로컬 PSRepository 작업
ms.openlocfilehash: c1bd905674ae76a3badd3eff50780f0e1bb5fc64
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/22/2020
ms.locfileid: "75415831"
---
# <a name="working-with-private-powershellget-repositories"></a><span data-ttu-id="38723-103">프라이빗 PowerShellGet 리포지토리 작업</span><span class="sxs-lookup"><span data-stu-id="38723-103">Working with Private PowerShellGet Repositories</span></span>

<span data-ttu-id="38723-104">PowerShellGet 모듈은 PowerShell 갤러리 이외의 리포지토리를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="38723-105">이 cmdlet을 통해 다음 시나리오가 가능해집니다.</span><span class="sxs-lookup"><span data-stu-id="38723-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="38723-106">사용자 환경에서 사용할 신뢰할 수 있는 미리 유효성 검사된 PowerShell 모듈 세트 지원</span><span class="sxs-lookup"><span data-stu-id="38723-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="38723-107">PowerShell 모듈 또는 스크립트를 빌드하는 CI/CD 파이프라인 테스트</span><span class="sxs-lookup"><span data-stu-id="38723-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="38723-108">인터넷에 액세스할 수 없는 시스템에 PowerShell 스크립트 및 모듈 전달</span><span class="sxs-lookup"><span data-stu-id="38723-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>
- <span data-ttu-id="38723-109">조직에서만 사용할 수 있는 PowerShell 스크립트 및 모듈 전달</span><span class="sxs-lookup"><span data-stu-id="38723-109">Deliver PowerShell scripts and modules only available to your organization</span></span>

<span data-ttu-id="38723-110">이 문서에서는 로컬 PowerShell 리포지토리를 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-110">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="38723-111">또한 PowerShell 갤러리에서 사용할 수 있는 [OfflinePowerShellGetDeploy][] 모듈을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="38723-111">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="38723-112">이 모듈에는 최신 버전의 PowerShellGet을 로컬 리포지토리에 설치하는 cmdlet이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="38723-112">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="38723-113">로컬 리포지토리 유형</span><span class="sxs-lookup"><span data-stu-id="38723-113">Local repository types</span></span>

<span data-ttu-id="38723-114">로컬 PSRepository를 만드는 두 가지 방법은 NuGet 서버 또는 파일 공유입니다.</span><span class="sxs-lookup"><span data-stu-id="38723-114">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="38723-115">각 유형에는 다음과 같은 장단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-115">Each type has advantages and disadvantages:</span></span>

### <a name="nuget-server"></a><span data-ttu-id="38723-116">NuGet 서버</span><span class="sxs-lookup"><span data-stu-id="38723-116">NuGet Server</span></span>

| <span data-ttu-id="38723-117">장점</span><span class="sxs-lookup"><span data-stu-id="38723-117">Advantages</span></span>| <span data-ttu-id="38723-118">단점</span><span class="sxs-lookup"><span data-stu-id="38723-118">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="38723-119">Powershell 갤러리 기능을 최대한 가깝게 모방</span><span class="sxs-lookup"><span data-stu-id="38723-119">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="38723-120">다중 계층 앱에 작업 계획 및 지원 필요</span><span class="sxs-lookup"><span data-stu-id="38723-120">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="38723-121">NuGet이 Visual Studio, 기타 도구에 통합</span><span class="sxs-lookup"><span data-stu-id="38723-121">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="38723-122">인증 모델 및 NuGet 계정 관리 필요</span><span class="sxs-lookup"><span data-stu-id="38723-122">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="38723-123">NuGet이 `.Nupkg` 패키지의 메타데이터 지원</span><span class="sxs-lookup"><span data-stu-id="38723-123">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="38723-124">게시에 API 키 관리 및 유지 관리 필요</span><span class="sxs-lookup"><span data-stu-id="38723-124">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="38723-125">검색, 패키지 관리 등 제공</span><span class="sxs-lookup"><span data-stu-id="38723-125">Provides search, package administration, etc.</span></span> | |

### <a name="file-share"></a><span data-ttu-id="38723-126">파일 공유</span><span class="sxs-lookup"><span data-stu-id="38723-126">File Share</span></span>

| <span data-ttu-id="38723-127">장점</span><span class="sxs-lookup"><span data-stu-id="38723-127">Advantages</span></span>| <span data-ttu-id="38723-128">단점</span><span class="sxs-lookup"><span data-stu-id="38723-128">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="38723-129">간편한 설정, 백업 및 유지 관리</span><span class="sxs-lookup"><span data-stu-id="38723-129">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="38723-130">PowerShellGet에서 사용되는 메타데이터를 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="38723-130">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="38723-131">간단한 보안 모델 - 공유에 대한 사용자 권한</span><span class="sxs-lookup"><span data-stu-id="38723-131">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="38723-132">기본 파일 공유 이외의 UI 없음</span><span class="sxs-lookup"><span data-stu-id="38723-132">No UI beyond basic file share</span></span> |
| <span data-ttu-id="38723-133">기존 항목 바꾸기와 같은 제약 조건 없음</span><span class="sxs-lookup"><span data-stu-id="38723-133">No constraints such as replacing existing items</span></span> | <span data-ttu-id="38723-134">제한된 보안 및 누가 무엇을 업데이트하는지에 대한 기록 없음</span><span class="sxs-lookup"><span data-stu-id="38723-134">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="38723-135">PowerShellGet은 하나의 유형을 사용하고 버전 찾기 및 종속성 설치를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-135">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="38723-136">그러나 PowerShell 갤러리에서 작동하는 일부 기능은 기본 NuGet 서버 또는 파일 공유에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-136">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="38723-137">모든 것이 패키지로 제공 - 스크립트, 모듈, DSC 리소스 또는 역할 기능의 구별 없음</span><span class="sxs-lookup"><span data-stu-id="38723-137">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="38723-138">파일 공유 서버에서는 태그를 포함한 패키지 메타데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-138">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="38723-139">로컬 리포지토리 만들기</span><span class="sxs-lookup"><span data-stu-id="38723-139">Creating a local repository</span></span>

<span data-ttu-id="38723-140">다음 문서에는 고유한 NuGet 서버를 설정하는 단계가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-140">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="38723-141">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="38723-141">[NuGet.Server][]</span></span>

<span data-ttu-id="38723-142">패키지를 추가하는 지점까지 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-142">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="38723-143">[패키지 게시](#publishing-to-a-local-repository) 단계는 이 문서의 뒷부분에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-143">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="38723-144">파일 공유 기반 리포지토리의 경우 사용자에게 파일 공유에 액세스할 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-144">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="38723-145">로컬 리포지토리 등록</span><span class="sxs-lookup"><span data-stu-id="38723-145">Registering a local repository</span></span>

<span data-ttu-id="38723-146">리포지토리를 사용하려면 먼저 `Register-PSRepository` 명령을 사용하여 리포지토리를 등록해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-146">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="38723-147">아래 예제에서는 고유한 리포지토리를 신뢰한다고 가정하여 **InstallationPolicy**가 *Trusted*로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="38723-147">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="38723-148">두 가지 명령이 **ScriptSourceLocation**을 처리하는 방식의 차이에 주의하세요.</span><span class="sxs-lookup"><span data-stu-id="38723-148">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="38723-149">파일 공유 기반 리포지토리의 경우 **SourceLocation** 및 **ScriptSourceLocation**이 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-149">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="38723-150">웹 기반 리포지토리의 경우 두 항목이 달라야 하므로, 이 예제에서는 후행 "/"가 **SourceLocation**에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="38723-150">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="38723-151">새로 생성된 PSRepository를 기본 리포지토리로 설정하려면 모든 다른 PSRepository를 등록 취소해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-151">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="38723-152">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="38723-152">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="38723-153">리포지토리 이름 'PSGallery'는 PowerShell 갤러리에서 사용하도록 예약되었습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-153">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="38723-154">PSGallery를 등록 취소할 수 있지만 이름 PSGallery를 다른 리포지토리에 사용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-154">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="38723-155">PSGallery를 복원해야 할 경우 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-155">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="38723-156">로컬 리포지토리 게시</span><span class="sxs-lookup"><span data-stu-id="38723-156">Publishing to a local repository</span></span>

<span data-ttu-id="38723-157">로컬 PSRepository를 등록한 후 로컬 PSRepository에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-157">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="38723-158">두 가지 기본 게시 시나리오는 고유한 모듈을 게시하는 것과 PSGallery에서 모듈을 게시하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="38723-158">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="38723-159">직접 작성한 모듈 게시</span><span class="sxs-lookup"><span data-stu-id="38723-159">Publishing a module you authored</span></span>

<span data-ttu-id="38723-160">`Publish-Module` 및 `Publish-Script`를 사용하여 PowerShell 갤러리에 게시한 것과 동일한 방법으로 로컬 PSRepository에 모듈을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-160">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="38723-161">코드 위치 지정</span><span class="sxs-lookup"><span data-stu-id="38723-161">Specify the location for your code</span></span>
- <span data-ttu-id="38723-162">API 키 제공</span><span class="sxs-lookup"><span data-stu-id="38723-162">Supply an API key</span></span>
- <span data-ttu-id="38723-163">리포지토리 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-163">Specify the repository name.</span></span> <span data-ttu-id="38723-164">예를 들어 `-PSRepository LocalPSRepo`</span><span class="sxs-lookup"><span data-stu-id="38723-164">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="38723-165">NuGet 서버에서 계정을 만든 후 로그인하여 API 키를 생성하고 저장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-165">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="38723-166">파일 공유의 경우 NuGetApiKey 값에 비어 있지 않은 문자열을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-166">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="38723-167">예제:</span><span class="sxs-lookup"><span data-stu-id="38723-167">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'
```

```powershell
# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="38723-168">보안을 적용하려면 API 키가 스크립트에서 하드 코드되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-168">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="38723-169">보안 키 관리 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-169">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="38723-170">PSGallery에서 모듈 게시</span><span class="sxs-lookup"><span data-stu-id="38723-170">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="38723-171">PSGallery의 모듈을 로컬 PSRepository에 게시하려면 'Save-Package' cmdlet을 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38723-171">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="38723-172">패키지 이름 지정</span><span class="sxs-lookup"><span data-stu-id="38723-172">Specify the Name of the Package</span></span>
- <span data-ttu-id="38723-173">'NuGet'을 공급자로 지정</span><span class="sxs-lookup"><span data-stu-id="38723-173">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="38723-174">PSGallery 위치를 원본으로 지정(https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="38723-174">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="38723-175">로컬 리포지토리의 경로 지정</span><span class="sxs-lookup"><span data-stu-id="38723-175">Specify the path to your local Repository</span></span>

<span data-ttu-id="38723-176">예제:</span><span class="sxs-lookup"><span data-stu-id="38723-176">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider NuGet -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="38723-177">로컬 PSRepository가 웹 기반인 경우 게시할 때 nuget.exe를 사용하는 추가 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-177">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="38723-178">[nuget.exe][] 사용에 대한 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38723-178">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="38723-179">연결이 끊어진 시스템에 PowerShellGet 설치</span><span class="sxs-lookup"><span data-stu-id="38723-179">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="38723-180">시스템에서 인터넷 연결이 끊어져야 하는 환경에는 PowerShellGet을 배포하는 것이 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-180">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="38723-181">PowerShellGet에는 처음 사용될 때 최신 버전을 설치하는 부트스트랩 프로세스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-181">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="38723-182">PowerShell 갤러리의 OfflinePowerShellGetDeploy 모듈은 부트스트랩 프로세스를 지원하는 cmdlet을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-182">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="38723-183">오프라인 배포를 부트스트랩하려면 다음을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-183">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="38723-184">인터넷에 연결된 시스템 및 연결이 끊어진 시스템에 OfflinePowerShellGetDeploy 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="38723-184">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="38723-185">`Save-PowerShellGetForOffline` cmdlet을 사용하여 인터넷에 연결된 시스템에 PowerShellGet 및 해당 종속성 다운로드</span><span class="sxs-lookup"><span data-stu-id="38723-185">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="38723-186">인터넷에 연결된 시스템에서 연결이 끊어진 시스템으로 PowerShellGet 및 해당 종속성 복사</span><span class="sxs-lookup"><span data-stu-id="38723-186">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="38723-187">연결이 끊어진 시스템에서 `Install-PowerShellGetOffline`을 사용하여 PowerShellGet 및 해당 종속성을 적절한 폴더에 저장</span><span class="sxs-lookup"><span data-stu-id="38723-187">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="38723-188">다음 명령은 `Save-PowerShellGetForOffline`을 사용하여 모든 구성 요소를 `f:\OfflinePowerShellGet` 폴더에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-188">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="38723-189">이때 `F:\OfflinePowerShellGet`의 콘텐츠를 연결이 끊어진 시스템에서 사용할 수 있도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-189">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="38723-190">`Install-PowerShellGetOffline` cmdlet을 사용하여 연결이 끊어진 시스템에 PowerShellGet을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-190">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="38723-191">이 명령을 실행하기 전에 PowerShell 세션에서 PowerShellGet을 실행하지 않는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-191">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="38723-192">PowerShellGet이 세션에 로드된 후에는 구성 요소를 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-192">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="38723-193">실수로 PowerShellGet을 시작하는 경우에는 PowerShell을 종료하고 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-193">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="38723-194">이 명령을 실행하면 PowerShellGet을 로컬 리포지토리에 게시할 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="38723-194">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

## <a name="use-packaging-solutions-to-host-powershellget-repositories"></a><span data-ttu-id="38723-195">패키지 솔루션을 사용하여 PowerShellGet 리포지토리 호스트</span><span class="sxs-lookup"><span data-stu-id="38723-195">Use Packaging solutions to host PowerShellGet repositories</span></span>

<span data-ttu-id="38723-196">Azure Artifacts와 같은 패키지 솔루션을 사용하여 프라이빗 또는 퍼블릭 PowerShellGet 리포지토리를 호스트할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="38723-196">You can also use packaging solutions like Azure Artifacts to host a private or public PowerShellGet repository.</span></span> <span data-ttu-id="38723-197">자세한 내용 및 지침은 [Azure Artifacts 설명서](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="38723-197">For more information and instructions, see the [Azure Artifacts documentation](https://docs.microsoft.com/azure/devops/artifacts/tutorials/private-powershell-library).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38723-198">보안을 적용하려면 API 키가 스크립트에서 하드 코드되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-198">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="38723-199">보안 키 관리 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="38723-199">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
