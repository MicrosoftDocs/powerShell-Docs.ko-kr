---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,setup
contributor: jianyunt, quoctruong
title: WMF 5.1의 향상된 패키지 관리
ms.openlocfilehash: 30ef59ed9dc0d56636d85cc6e53523a9a73963a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055618"
---
# <a name="improvements-to-package-management-in-wmf-51"></a><span data-ttu-id="1db50-103">WMF 5.1의 향상된 패키지 관리</span><span class="sxs-lookup"><span data-stu-id="1db50-103">Improvements to Package Management in WMF 5.1</span></span>

## <a name="improvements-in-packagemanagement"></a><span data-ttu-id="1db50-104">패키지 관리의 개선 사항</span><span class="sxs-lookup"><span data-stu-id="1db50-104">Improvements in PackageManagement</span></span>

<span data-ttu-id="1db50-105">WMF 5.1에서 수정된 사항은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-105">The following are the fixes made in the WMF 5.1:</span></span>

### <a name="version-alias"></a><span data-ttu-id="1db50-106">버전 별칭</span><span class="sxs-lookup"><span data-stu-id="1db50-106">Version Alias</span></span>

<span data-ttu-id="1db50-107">**시나리오**: 시스템에 P1 패키지의 버전 1.0 및 2.0이 설치되어 있고, 버전 1.0을 제거하려는 경우 `Uninstall-Package -Name P1 -Version 1.0`을 실행하면 cmdlet을 실행한 후에 버전 1.0이 제거되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-107">**Scenario**: If you have version 1.0 and 2.0 of a package, P1, installed on your system, and you want to uninstall version 1.0, you would run `Uninstall-Package -Name P1 -Version 1.0` and expect version 1.0 to be uninstalled after running the cmdlet.</span></span> <span data-ttu-id="1db50-108">그러나 결과로 버전 2.0이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-108">However the result is that version 2.0 gets uninstalled.</span></span>

<span data-ttu-id="1db50-109">이는 `-Version` 매개 변수가 `-MinimumVersion` 매개 변수의 별칭이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-109">This occurs because the `-Version` parameter is an alias of the `-MinimumVersion` parameter.</span></span> <span data-ttu-id="1db50-110">PackageManagement에서 최소 버전이 1.0인 정규화된 패키지를 찾을 경우 최신 버전을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-110">When PackageManagement is looking for a qualified package with the minimum version of 1.0, it returns the latest version.</span></span> <span data-ttu-id="1db50-111">일반적으로 최신 버전을 찾는 것이 필요한 결과이므로 일반적인 사례에서는 이 동작이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-111">This behavior is expected in normal cases because finding the latest version is usually the desired result.</span></span> <span data-ttu-id="1db50-112">그러나 `Uninstall-Package` 사례에는 적용하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-112">However, it should not apply to the `Uninstall-Package` case.</span></span>

<span data-ttu-id="1db50-113">**해결 방법**: `-Version` 별칭을 PackageManagement(즉,</span><span class="sxs-lookup"><span data-stu-id="1db50-113">**Solution**:removed `-Version` alias entirely in PackageManagement (a.k.a.</span></span> <span data-ttu-id="1db50-114">OneGet) 및 PowerShellGet에서 완전히 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-114">OneGet) and PowerShellGet.</span></span>

### <a name="multiple-prompts-for-bootstrapping-the-nuget-provider"></a><span data-ttu-id="1db50-115">NuGet 공급자를 부트스트래핑할지 묻는 메시지 여러 번 표시</span><span class="sxs-lookup"><span data-stu-id="1db50-115">Multiple prompts for bootstrapping the NuGet provider</span></span>

<span data-ttu-id="1db50-116">**시나리오**: `Find-Module`이나 `Install-Module` 또는 다른 PackageManagement cmdlet을 컴퓨터에서 처음으로 실행하면 PackageManagement에서 NuGet 공급자를 부트스트랩하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-116">**Scenario**: When you run `Find-Module` or `Install-Module` or other PackageManagement cmdlets on your computer for the first time, PackageManagement tries to bootstrap the NuGet provider.</span></span> <span data-ttu-id="1db50-117">이는 PowershellGet 공급자도 NuGet 공급자를 사용하여 PowerShell 모듈을 다운로드하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-117">It does this because the PowerShellGet provider also uses the NuGet provider to download PowerShell modules.</span></span> <span data-ttu-id="1db50-118">그런 다음 PackageManagement에서는 NuGet 공급자 설치를 허용할지 묻는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-118">PackageManagement then prompts the user for permission to install the NuGet provider.</span></span> <span data-ttu-id="1db50-119">사용자가 부트스트래핑에 대해 “예"를 선택하면 NuGet 공급자의 최신 버전이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-119">After the user selects "yes" for the bootstrapping, the latest version of the NuGet provider will be installed.</span></span>

<span data-ttu-id="1db50-120">그러나 경우에 따라 컴퓨터에 이전 버전의 NuGet 공급자가 설치된 경우 이전 버전의 NuGet이 PowerShell 세션에 먼저 로드되는 경우가 있습니다. 즉, PackageManagement에서 경합 상태가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-120">However, in some cases, when you have an old version of NuGet provider installed on your computer, the older version of NuGet sometimes gets loaded first into the PowerShell session (that's the race condition in PackageManagement).</span></span> <span data-ttu-id="1db50-121">그러나 PowerShellGet이 작동하려면 최신 버전의 NuGet 공급자가 필요하므로 PowerShellGet에서는 PackageManagement에 NuGet 공급자를 다시 부트스트랩하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-121">However PowerShellGet requires the later version of the NuGet provider to work, so PowerShellGet asks PackageManagement to bootstrap the NuGet provider again.</span></span> <span data-ttu-id="1db50-122">따라서 NuGet 공급자를 부트스트래핑할지 묻는 메시지 여러 번 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-122">This results in multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="1db50-123">**해결 방법**: WMF 5.1에서 PackageManagement는 NuGet 공급자를 부트스트랩하라는 메시지가 여러 번 표시되지 않도록 최신 버전의 NuGet 공급자를 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-123">**Solution**: In WMF5.1, PackageManagement loads the latest version of the NuGet provider to avoid multiple prompts for bootstrapping the NuGet provider.</span></span>

<span data-ttu-id="1db50-124">$env:ProgramFiles\PackageManagement\ProviderAssemblies 또는 $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies에 있는 경우 NuGet 공급자(NuGet-Anycpu.exe)의 이전 버전을 수동으로 삭제하여 이 문제를 해결할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-124">You could also work around this issue by manually deleting the old version of the NuGet provider (NuGet-Anycpu.exe) if exists from $env:ProgramFiles\PackageManagement\ProviderAssemblies $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies</span></span>


### <a name="support-for-packagemanagement-on-computers-with-intranet-access-only"></a><span data-ttu-id="1db50-125">인트라넷 액세스만 가능한 컴퓨터에서 PackageManagement 지원</span><span class="sxs-lookup"><span data-stu-id="1db50-125">Support for PackageManagement on computers with Intranet access only</span></span>

<span data-ttu-id="1db50-126">**시나리오**: 기업 시나리오로 사용자가 인터넷에 연결되어 있지 않고 인트라넷만 사용하는 환경에서 작업하는 사례가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-126">**Scenario**: For the enterprise scenario, people are working under an environment where there is no Internet access but Intranet only.</span></span> <span data-ttu-id="1db50-127">WMF 5.0에서 PackageManagement는 이러한 사례를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-127">PackageManagement did not support this case in WMF 5.0.</span></span>

<span data-ttu-id="1db50-128">**시나리오**: WMF 5.0에서 PackageManagement는 인트라넷에만 연결되고 인터넷에는 연결되지 않은 컴퓨터를 지원하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-128">**Scenario**: In WMF 5.0, PackageManagement did not support computers that have only Intranet (but not Internet) access.</span></span>

<span data-ttu-id="1db50-129">**해결 방법**: WMF 5.1에서는 다음 단계에 따라 인트라넷 컴퓨터에서 PackageManagement를 사용하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-129">**Solution**: In WMF 5.1, you can follow these steps to allow Intranet computers to use PackageManagement:</span></span>

1. <span data-ttu-id="1db50-130">인터넷에 연결된 다른 컴퓨터에서 `Install-PackageProvider -Name NuGet`을 사용하여 NuGet 공급자를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-130">Download the NuGet provider using another computer that has an Internet connection by using `Install-PackageProvider -Name NuGet`.</span></span>

2. <span data-ttu-id="1db50-131">`$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget` 또는 `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`에서 NuGet 공급자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-131">Find the NuGet provider under either `$env:ProgramFiles\PackageManagement\ProviderAssemblies\nuget`  or  `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\nuget`.</span></span>

3. <span data-ttu-id="1db50-132">이 이진 파일을 인트라넷 컴퓨터에서 액세스할 수 있는 폴더 또는 네트워크 공유 위치에 복사한 다음 `Install-PackageProvider -Name NuGet -Source <Path to folder>`를 사용하여 NuGet 공급자를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-132">Copy the binaries to a folder or network share location that the Intranet computer can access, and then install the NuGet provider with `Install-PackageProvider -Name NuGet -Source <Path to folder>`.</span></span>


### <a name="event-logging-improvements"></a><span data-ttu-id="1db50-133">향상된 이벤트 로깅</span><span class="sxs-lookup"><span data-stu-id="1db50-133">Event logging improvements</span></span>

<span data-ttu-id="1db50-134">패키지를 설치하면 컴퓨터 상태가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-134">When you install packages, you are changing the state of the computer.</span></span> <span data-ttu-id="1db50-135">이제 WMF 5.1에서 PackageManagement는 `Install-Package`, `Uninstall-Package` 및 `Save-Package` 활동에 대한 이벤트를 Windows 이벤트 로그에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-135">In WMF 5.1, PackageManagement now logs events to the Windows event log for `Install-Package`, `Uninstall-Package`, and `Save-Package` activities.</span></span> <span data-ttu-id="1db50-136">이벤트 로그는 PowerShell의 경우와 동일한 `Microsoft-Windows-PowerShell, Operational`입니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-136">The Event log  is the same as for PowerShell, that is, `Microsoft-Windows-PowerShell, Operational`.</span></span>

### <a name="support-for-basic-authentication"></a><span data-ttu-id="1db50-137">기본 인증 지원</span><span class="sxs-lookup"><span data-stu-id="1db50-137">Support for basic authentication</span></span>

<span data-ttu-id="1db50-138">WMF 5.1에서 PackageManagement는 기본 인증이 필요한 리포지토리에서 패키지를 찾고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-138">In WMF 5.1, PackageManagement supports finding and installing packages from a repository that requires basic authentication.</span></span> <span data-ttu-id="1db50-139">`Find-Package` 및 `Install-Package` cmdlet에 자격 증명을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-139">You can supply your credentials to the `Find-Package` and `Install-Package` cmdlets.</span></span> <span data-ttu-id="1db50-140">예:</span><span class="sxs-lookup"><span data-stu-id="1db50-140">For example:</span></span>

``` PowerShell
Find-Package -Source <SourceWithCredential> -Credential (Get-Credential)
```

### <a name="support-for-using-packagemanagement-behind-a-proxy"></a><span data-ttu-id="1db50-141">프록시 뒤에 있는 PackageManagement 사용 지원</span><span class="sxs-lookup"><span data-stu-id="1db50-141">Support for using PackageManagement behind a proxy</span></span>

<span data-ttu-id="1db50-142">WMF 5.1에서 PackageManagement는 새 프록시 매개 변수 `-ProxyCredential` 및 `-Proxy`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-142">In WMF 5.1, PackageManagement now takes new proxy parameters `-ProxyCredential` and `-Proxy`.</span></span> <span data-ttu-id="1db50-143">이러한 매개 변수를 사용하여 PackageManagement cmdlet에 프록시 URL 및 자격 증명을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-143">Using these parameters, you can specify the proxy URL and credentials to PackageManagement cmdlets.</span></span> <span data-ttu-id="1db50-144">기본적으로 시스템 프록시 설정이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="1db50-144">By default, system proxy settings are used.</span></span> <span data-ttu-id="1db50-145">예:</span><span class="sxs-lookup"><span data-stu-id="1db50-145">For example:</span></span>

``` PowerShell
Find-Package -Source http://www.nuget.org/api/v2/ -Proxy http://www.myproxyserver.com -ProxyCredential (Get-Credential)
```
