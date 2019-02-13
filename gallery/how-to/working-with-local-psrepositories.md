---
ms.date: 11/06/2018
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery,psget,갤러리
title: 로컬 PSRepositories 사용
ms.openlocfilehash: 94824ea584c097838b24c6f2cd02407b6147a781
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682673"
---
# <a name="working-with-local-powershellget-repositories"></a><span data-ttu-id="a58fd-103">로컬 PowerShellGet 리포지토리 작업</span><span class="sxs-lookup"><span data-stu-id="a58fd-103">Working with local PowerShellGet Repositories</span></span>

<span data-ttu-id="a58fd-104">PowerShell 갤러리 이외의 PowerShellGet 모듈 지원 리포지토리.</span><span class="sxs-lookup"><span data-stu-id="a58fd-104">The PowerShellGet module support repositories other than the PowerShell Gallery.</span></span>
<span data-ttu-id="a58fd-105">이러한 cmdlet을 사용 하는 다음과 같은 시나리오:</span><span class="sxs-lookup"><span data-stu-id="a58fd-105">These cmdlets enable the following scenarios:</span></span>

- <span data-ttu-id="a58fd-106">사용자 환경에서 사용 하기 위해 신뢰할 수 있는, 사전 검증 된 일련의 PowerShell 모듈을 지원</span><span class="sxs-lookup"><span data-stu-id="a58fd-106">Support a trusted, pre-validated set of PowerShell modules for use in your environment</span></span>
- <span data-ttu-id="a58fd-107">PowerShell 모듈 또는 스크립트를 작성 하는 CI/CD 파이프라인 테스트</span><span class="sxs-lookup"><span data-stu-id="a58fd-107">Testing a CI/CD pipeline that builds PowerShell modules or scripts</span></span>
- <span data-ttu-id="a58fd-108">인터넷에 액세스할 수 없는 시스템에 PowerShell 스크립트 및 모듈 제공</span><span class="sxs-lookup"><span data-stu-id="a58fd-108">Deliver PowerShell scripts and modules to systems that can't access the internet</span></span>

<span data-ttu-id="a58fd-109">이 문서에서는 로컬 PowerShell 리포지토리를 설정 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-109">This article describes how to set up a local PowerShell repository.</span></span> <span data-ttu-id="a58fd-110">문서에 대해서도 설명 합니다 [OfflinePowerShellGetDeploy][] PowerShell 갤러리에서 모듈을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-110">The article also covers the [OfflinePowerShellGetDeploy][] module available from the PowerShell Gallery.</span></span> <span data-ttu-id="a58fd-111">이 모듈에는 로컬 리포지토리를 최신 버전의 PowerShellGet 설치 하기 위한 cmdlet 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-111">This module contains cmdlets to install the latest version of PowerShellGet into your local repository.</span></span>

## <a name="local-repository-types"></a><span data-ttu-id="a58fd-112">로컬 저장소 유형</span><span class="sxs-lookup"><span data-stu-id="a58fd-112">Local repository types</span></span>

<span data-ttu-id="a58fd-113">두 가지 방법으로 로컬 PSRepository를 만들려면: NuGet 서버 또는 파일 공유입니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-113">There are two ways to create a local PSRepository: NuGet server or file share.</span></span> <span data-ttu-id="a58fd-114">각 형식에는 각각 장단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-114">Each type has advantages and disadvantages:</span></span>

<span data-ttu-id="a58fd-115">NuGet 서버</span><span class="sxs-lookup"><span data-stu-id="a58fd-115">NuGet Server</span></span>

| <span data-ttu-id="a58fd-116">이점</span><span class="sxs-lookup"><span data-stu-id="a58fd-116">Advantages</span></span>| <span data-ttu-id="a58fd-117">단점</span><span class="sxs-lookup"><span data-stu-id="a58fd-117">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="a58fd-118">Powershell 갤러리 기능을 최대한 가깝게 모방합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-118">Closely mimics PowerShellGallery functionality</span></span> | <span data-ttu-id="a58fd-119">다중 계층 앱에 필요한 계획 하는 작업 및 지원</span><span class="sxs-lookup"><span data-stu-id="a58fd-119">Multi-tier app requires operations planning & support</span></span> |
| <span data-ttu-id="a58fd-120">Visual Studio 나 다른 도구를 사용 하 여 NuGet 통합</span><span class="sxs-lookup"><span data-stu-id="a58fd-120">NuGet integrates with Visual Studio, other tools</span></span> | <span data-ttu-id="a58fd-121">인증 모델 및 필요한 NuGet 계정 관리</span><span class="sxs-lookup"><span data-stu-id="a58fd-121">Authentication model and NuGet accounts management needed</span></span> |
| <span data-ttu-id="a58fd-122">NuGet 메타 데이터를 지 원하는 `.Nupkg` 패키지</span><span class="sxs-lookup"><span data-stu-id="a58fd-122">NuGet supports metadata in `.Nupkg` packages</span></span> | <span data-ttu-id="a58fd-123">게시를 위해 API 키 관리 및 유지 관리</span><span class="sxs-lookup"><span data-stu-id="a58fd-123">Publishing requires API Key management & maintenance</span></span> |
| <span data-ttu-id="a58fd-124">검색, 패키지 관리 등을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-124">Provides search, package administration, etc.</span></span> | |

<span data-ttu-id="a58fd-125">파일 공유</span><span class="sxs-lookup"><span data-stu-id="a58fd-125">File Share</span></span>

| <span data-ttu-id="a58fd-126">이점</span><span class="sxs-lookup"><span data-stu-id="a58fd-126">Advantages</span></span>| <span data-ttu-id="a58fd-127">단점</span><span class="sxs-lookup"><span data-stu-id="a58fd-127">Disadvantages</span></span> |
| --- | --- |
| <span data-ttu-id="a58fd-128">설정, 백업 및 유지 관리 하는 작업을 쉽게</span><span class="sxs-lookup"><span data-stu-id="a58fd-128">Easy to set up, back up, and maintain</span></span> | <span data-ttu-id="a58fd-129">PowerShellGet에서 사용 하는 메타 데이터를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-129">Metadata used by PowerShellGet isn't available</span></span> |
| <span data-ttu-id="a58fd-130">간단한 보안 모델-사용자의 공유 권한</span><span class="sxs-lookup"><span data-stu-id="a58fd-130">Simple security model - user permissions on the share</span></span> | <span data-ttu-id="a58fd-131">기본 파일 공유 이외의 UI</span><span class="sxs-lookup"><span data-stu-id="a58fd-131">No UI beyond basic file share</span></span> |
| <span data-ttu-id="a58fd-132">기존 항목 바꾸기와 같은 제약 조건이 없는</span><span class="sxs-lookup"><span data-stu-id="a58fd-132">No constraints such as replacing existing items</span></span> | <span data-ttu-id="a58fd-133">제한 된 보안 및 항목을 업데이트 하는 기록 없음</span><span class="sxs-lookup"><span data-stu-id="a58fd-133">Limited security and no recording of who updates what</span></span> |

<span data-ttu-id="a58fd-134">PowerShellGet 형식 및 지원 버전 및 종속성 설치를 찾는 중 하나를 사용 하 여 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-134">PowerShellGet works with either type and supports locating versions and dependency installation.</span></span>
<span data-ttu-id="a58fd-135">그러나 PowerShell 갤러리에 대해 작동 하는 일부 기능은 기본 NuGet 서버 또는 파일 공유에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-135">However, some features that work for the PowerShell Gallery aren't available for base NuGet servers or file shares.</span></span>

- <span data-ttu-id="a58fd-136">모든 항목은 패키지-스크립트, 모듈, DSC 리소스 또는 역할 기능 차이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-136">Everything is a package - no differentiation of scripts, modules, DSC resources, or role capabilities.</span></span>
- <span data-ttu-id="a58fd-137">파일 공유 서버는 태그를 포함 하는 패키지 메타 데이터를 볼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-137">File share servers can't see package metadata, including tags.</span></span>

## <a name="creating-a-local-repository"></a><span data-ttu-id="a58fd-138">로컬 리포지토리 만들기</span><span class="sxs-lookup"><span data-stu-id="a58fd-138">Creating a local repository</span></span>

<span data-ttu-id="a58fd-139">다음 문서를 사용자 고유의 NuGet 서버를 설정 하는 단계를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-139">The following article lists the steps for setting up your own NuGet Server.</span></span>

- <span data-ttu-id="a58fd-140">[NuGet.Server][]</span><span class="sxs-lookup"><span data-stu-id="a58fd-140">[NuGet.Server][]</span></span>

<span data-ttu-id="a58fd-141">패키지를 추가 하는 지점까지 단계를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-141">Follow the steps up to the point of adding packages.</span></span> <span data-ttu-id="a58fd-142">단계 [패키지 게시](#publishing-to-a-local-repository) 이 문서의 뒷부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-142">The steps for [publishing a package](#publishing-to-a-local-repository) are covered later in this article.</span></span>

<span data-ttu-id="a58fd-143">파일 공유 기반 저장소를 사용자가 파일 공유에 액세스할 수 있는 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-143">For a file share-based repository, make sure that your users have permissions to access the file share.</span></span>

## <a name="registering-a-local-repository"></a><span data-ttu-id="a58fd-144">로컬 리포지토리 등록</span><span class="sxs-lookup"><span data-stu-id="a58fd-144">Registering a local repository</span></span>

<span data-ttu-id="a58fd-145">리포지토리를 사용할 수 있습니다, 전에 등록 해야 사용 하 여 `Register-PSRepository` 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-145">Before a repository can be used, it must be registered using the `Register-PSRepository` command.</span></span>
<span data-ttu-id="a58fd-146">아래 예제에서를 **InstallationPolicy** 로 설정 되어 *신뢰할 수 있는*, 사용자 고유의 리포지토리를 신뢰 하는지 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-146">In the examples below, the **InstallationPolicy** is set to *Trusted*, on the assumption that you trust your own repository.</span></span>

```powershell
# Register a NuGet-based server
Register-PSRepository -Name LocalPSRepo -SourceLocation http://MyLocalNuget/Api/V2/ -ScriptSourceLocation http://MyLocalNuget/Api/V2 -InstallationPolicy Trusted

# Register a file share on my local machine
Register-PSRepository -Name LocalPSRepo -SourceLocation '\\localhost\PSRepoLocal\' -ScriptSourceLocation '\\localhost\PSRepoLocal\' -InstallationPolicy Trusted
```

<span data-ttu-id="a58fd-147">두 명령을 처리 하는 방법 간의 차이점을 기록해 **ScriptSourceLocation**합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-147">Take note of the difference between how the two commands handle **ScriptSourceLocation**.</span></span> <span data-ttu-id="a58fd-148">파일 공유 기반 저장소에 대 한 합니다 **SourceLocation** 하 고 **ScriptSourceLocation** 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-148">For a file share-based repositories, the **SourceLocation** and **ScriptSourceLocation** must match.</span></span> <span data-ttu-id="a58fd-149">웹을 기반으로 하는 리포지토리에 대 한, 서로 달라 야 따라서이 예제의 후행 "/"에 추가 되는 **SourceLocation**합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-149">For a web-based repository, they must be different, so in this example a trailing "/" is added to the **SourceLocation**.</span></span>

<span data-ttu-id="a58fd-150">기본 리포지토리를 새로 만든된 PSRepository 원한다 면 다른 모든 PSRepositories 등록을 취소 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-150">If you want the newly created PSRepository to be the default repository, you must unregister all other PSRepositories.</span></span> <span data-ttu-id="a58fd-151">예:</span><span class="sxs-lookup"><span data-stu-id="a58fd-151">For example:</span></span>

```powershell
Unregister-PSRepository -Name PSGallery
```

> [!NOTE]
> <span data-ttu-id="a58fd-152">'PSGallery' 리포지토리 이름은 사용 하 여 PowerShell 갤러리에서 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-152">The repository name 'PSGallery' is reserved for use by the PowerShell Gallery.</span></span> <span data-ttu-id="a58fd-153">PSGallery를 등록 취소할 수 있지만 다른 리포지토리에 대 한 이름을 PSGallery를 다시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-153">You can unregister PSGallery, but you cannot reuse the name PSGallery for any other repository.</span></span>

<span data-ttu-id="a58fd-154">PSGallery를 복원 해야 할 경우 다음 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-154">If you need to restore the PSGallery, run the following command:</span></span>

```powershell
Register-PSRepository -Default
```

## <a name="publishing-to-a-local-repository"></a><span data-ttu-id="a58fd-155">로컬 리포지토리 게시</span><span class="sxs-lookup"><span data-stu-id="a58fd-155">Publishing to a local repository</span></span>

<span data-ttu-id="a58fd-156">로컬 PSRepository에 등록 한 후에 로컬 PSRepository에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-156">Once you've registered the local PSRepository, you can publish to your local PSRepository.</span></span> <span data-ttu-id="a58fd-157">두 가지 주요 게시 시나리오: 사용자 고유의 모듈을 게시 하 고 PSGallery에서 모듈을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-157">There are two main publishing scenarios: publishing your own module and publishing a module from the PSGallery.</span></span>

### <a name="publishing-a-module-you-authored"></a><span data-ttu-id="a58fd-158">작성 하는 모듈을 게시</span><span class="sxs-lookup"><span data-stu-id="a58fd-158">Publishing a module you authored</span></span>

<span data-ttu-id="a58fd-159">사용 하 여 `Publish-Module` 및 `Publish-Script` PowerShell 갤러리에서 수행한 동일한 방식으로 사용자 로컬 PSRepository에 모듈을 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-159">Use `Publish-Module` and `Publish-Script` to publish your module to your local PSRepository the same way you do for the PowerShell Gallery.</span></span>

- <span data-ttu-id="a58fd-160">코드의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-160">Specify the location for your code</span></span>
- <span data-ttu-id="a58fd-161">API 키를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-161">Supply an API key</span></span>
- <span data-ttu-id="a58fd-162">리포지토리 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-162">Specify the repository name.</span></span> <span data-ttu-id="a58fd-163">예를 들면 `-PSRepository LocalPSRepo`과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-163">For example, `-PSRepository LocalPSRepo`</span></span>

> [!NOTE]
> <span data-ttu-id="a58fd-164">NuGet 서버에서 계정을 만든 다음 생성 하 고 API 키를 저장 하려면 로그인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-164">You must create an account in the NuGet server, then sign in to generate and save the API key.</span></span>
> <span data-ttu-id="a58fd-165">파일 공유에 대 한 NuGetApiKey 값에 대 한 모든 비어 있지 않은 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-165">For a file share, use any non-blank string for the NuGetApiKey value.</span></span>

<span data-ttu-id="a58fd-166">예제:</span><span class="sxs-lookup"><span data-stu-id="a58fd-166">Examples:</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'c:\projects\MyModule' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="a58fd-167">보안을 위해 API 키 아니어야 스크립트에 하드 코딩 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-167">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="a58fd-168">안전한 키 관리 시스템을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-168">Use a secure key management system.</span></span>

### <a name="publishing-a-module-from-the-psgallery"></a><span data-ttu-id="a58fd-169">PSGallery에서 모듈을 게시</span><span class="sxs-lookup"><span data-stu-id="a58fd-169">Publishing a module from the PSGallery</span></span>

<span data-ttu-id="a58fd-170">사용자 로컬 PSRepository PSGallery에서 모듈을 게시 하려면 ' 저장-Package' cmdlet을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-170">To publish a module from the PSGallery to your local PSRepository, you can use the 'Save-Package' cmdlet.</span></span>

- <span data-ttu-id="a58fd-171">패키지의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-171">Specify the Name of the Package</span></span>
- <span data-ttu-id="a58fd-172">'NuGet' 공급자로 지정</span><span class="sxs-lookup"><span data-stu-id="a58fd-172">Specify 'NuGet' as the Provider</span></span>
- <span data-ttu-id="a58fd-173">원본 (로 PSGallery 위치를 지정 합니다. https://www.powershellgallery.com/api/v2)</span><span class="sxs-lookup"><span data-stu-id="a58fd-173">Specify the PSGallery location as the source (https://www.powershellgallery.com/api/v2)</span></span>
- <span data-ttu-id="a58fd-174">로컬 리포지토리에 대 한 경로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-174">Specify the path to your local Repository</span></span>

<span data-ttu-id="a58fd-175">예:</span><span class="sxs-lookup"><span data-stu-id="a58fd-175">Example:</span></span>

```powershell
# Publish from the PSGallery to your local Repository
Save-Package -Name 'PackageName' -Provider Nuget -Source https://www.powershellgallery.com/api/v2 -Path '\\localhost\PSRepoLocal\'
```

<span data-ttu-id="a58fd-176">로컬 PSRepository에 웹 기반 이면 게시할 nuget.exe를 사용 하는 추가 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-176">If your local PSRepository is web-based, it requires an additional step that uses nuget.exe to publish.</span></span>

<span data-ttu-id="a58fd-177">사용 하 여 설명서를 참조 하십시오 [nuget.exe][]합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-177">See the documentation for using [nuget.exe][].</span></span>

## <a name="installing-powershellget-on-a-disconnected-system"></a><span data-ttu-id="a58fd-178">연결이 끊긴된 시스템에서 PowerShellGet 설치</span><span class="sxs-lookup"><span data-stu-id="a58fd-178">Installing PowerShellGet on a disconnected system</span></span>

<span data-ttu-id="a58fd-179">PowerShellGet을 배포 하는 것은 인터넷에서 연결을 끊을 수 시스템을 필요로 하는 환경에서 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-179">Deploying PowerShellGet is difficult in environments that require systems to be disconnected from the internet.</span></span> <span data-ttu-id="a58fd-180">PowerShellGet에 처음으로 사용 되는 최신 버전을 설치 하는 부트스트랩 프로세스를 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-180">PowerShellGet has a bootstrap process that installs the latest version the first time it's used.</span></span> <span data-ttu-id="a58fd-181">PowerShell 갤러리에 있는 OfflinePowerShellGetDeploy 모듈이 부트스트랩 프로세스를 지 원하는 cmdlet을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-181">The OfflinePowerShellGetDeploy module in the PowerShell Gallery provides cmdlets that support this bootstrap process.</span></span>

<span data-ttu-id="a58fd-182">오프 라인 배포를 부트스트랩할 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-182">To bootstrap an offline deployment, you need to:</span></span>

- <span data-ttu-id="a58fd-183">인터넷 연결 OfflinePowerShellGetDeploy 시스템 및 연결이 끊긴된 시스템 다운로드 및 설치</span><span class="sxs-lookup"><span data-stu-id="a58fd-183">Download and install the OfflinePowerShellGetDeploy your internet-connected system and your disconnected systems</span></span>
- <span data-ttu-id="a58fd-184">PowerShellGet을 사용 하 여 인터넷에 연결 된 시스템에 대 한 종속성을 다운로드 합니다 `Save-PowerShellGetForOffline` cmdlet</span><span class="sxs-lookup"><span data-stu-id="a58fd-184">Download PowerShellGet and its dependencies on the internet-connected system using the `Save-PowerShellGetForOffline` cmdlet</span></span>
- <span data-ttu-id="a58fd-185">인터넷에 연결 된 시스템에서 PowerShellGet 및 해당 종속성을 연결이 끊긴된 시스템에 복사</span><span class="sxs-lookup"><span data-stu-id="a58fd-185">Copy PowerShellGet and its dependencies from the internet-connected system to the disconnected system</span></span>
- <span data-ttu-id="a58fd-186">사용 된 `Install-PowerShellGetOffline` PowerShellGet 및 해당 종속성을 적합 한 폴더를 배치할 연결이 끊긴된 시스템에서</span><span class="sxs-lookup"><span data-stu-id="a58fd-186">Use the `Install-PowerShellGetOffline` on the disconnected system to place PowerShellGet and its dependencies into the proper folders</span></span>

<span data-ttu-id="a58fd-187">다음 명령을 사용 하 여 `Save-PowerShellGetForOffline` 폴더에 모든 구성 요소를 배치 하려면 `f:\OfflinePowerShellGet`</span><span class="sxs-lookup"><span data-stu-id="a58fd-187">The following commands use `Save-PowerShellGetForOffline` to put all the components into a folder `f:\OfflinePowerShellGet`</span></span>

```powershell
# Requires -RunAsAdministrator
#Download the OfflinePowerShellGetDeploy to a location that can be accessed
# by both the connected and disconnected systems.
Save-Module -Name OfflinePowerShellGetDeploy -Path 'F:\' -Repository PSGallery
Import-Module F:\OfflinePowerShellGetDeploy

# Put PowerShellGet somewhere locally
Save-PowerShellGetForOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="a58fd-188">이 시점에서 내용의 해야 `F:\OfflinePowerShellGet` 연결이 끊긴된 시스템에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-188">At this point, you must make the contents of `F:\OfflinePowerShellGet` available to your disconnected systems.</span></span> <span data-ttu-id="a58fd-189">실행 된 `Install-PowerShellGetOffline` 연결이 끊긴된 시스템에서 PowerShellGet을 설치 하려면 cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a58fd-189">Run the `Install-PowerShellGetOffline` cmdlet to install PowerShellGet on the disconnected system.</span></span>

> [!NOTE]
> <span data-ttu-id="a58fd-190">PowerShellGet 이러한 명령을 실행 하기 전에 PowerShell 세션에서 실행 하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-190">It is important that you do not run PowerShellGet in the PowerShell session before running these commands.</span></span> <span data-ttu-id="a58fd-191">PowerShellGet을 세션으로 로드 되 면 구성 요소를 업데이트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-191">Once PowerShellGet is loaded into the session, the components cannot be updated.</span></span> <span data-ttu-id="a58fd-192">PowerShellGet을 실수로 시작 수행 하는 경우 종료 하 고 PowerShell을 다시 시작 하십시오.</span><span class="sxs-lookup"><span data-stu-id="a58fd-192">If you do start PowerShellGet by mistake, exit and restart PowerShell.</span></span>

```powershell
Import-Module F:\OfflinePowerShellGetDeploy

Install-PowerShellGetOffline -LocalFolder 'F:\OfflinePowerShellGet'
```

<span data-ttu-id="a58fd-193">이러한 명령은 실행 한 후 준비가 PowerShellGet 로컬 리포지토리에 게시 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-193">After running these commands, you are ready to publish PowerShellGet to your local repository.</span></span>

```powershell
# Publish to a NuGet Server repository using my NuGetAPI key
Publish-Module -Path 'F:\OfflinePowershellGet' -Repository LocalPsRepo -NuGetApiKey 'oy2bi4avlkjolp6bme6azdyssn6ps3iu7ib2qpiudrtbji'

# Publish to a file share repo - the NuGet API key must be a non-blank string
Publish-Module -Path 'F:\OfflinePowerShellGet' -Repository LocalPsRepo -NuGetApiKey 'AnyStringWillDo'
```

> [!IMPORTANT]
> <span data-ttu-id="a58fd-194">보안을 위해 API 키 아니어야 스크립트에 하드 코딩 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-194">To ensure security, API keys should not be hard-coded in scripts.</span></span> <span data-ttu-id="a58fd-195">안전한 키 관리 시스템을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a58fd-195">Use a secure key management system.</span></span>

<!-- external links -->
[OfflinePowerShellGetDeploy]: https://www.powershellgallery.com/packages/OfflinePowerShellGetDeploy/0.1.1
[Nuget.Server]: /nuget/hosting-packages/nuget-server
[nuget.exe]: /nuget/tools/nuget-exe-cli-reference
