---
ms.date: 06/12/2017
contributor: manikb
keywords: gallery,powershell,cmdlet,psget
title: NuGet 부트스트랩
ms.openlocfilehash: 6d8f106bc3b8741203e87e4c097948a843f06d6e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328434"
---
# <a name="bootstrap-the-nuget-provider-and-nugetexe"></a><span data-ttu-id="81baf-103">NuGet 공급자 및 NuGet.exe 부트스트래프</span><span class="sxs-lookup"><span data-stu-id="81baf-103">Bootstrap the NuGet provider and NuGet.exe</span></span>

<span data-ttu-id="81baf-104">NuGet.exe는 최신 NuGet 공급자에 포함되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-104">NuGet.exe is not included in the latest NuGet provider.</span></span> <span data-ttu-id="81baf-105">모듈이나 스크립트의 게시 작업을 수행하려면 PowerShellGet에 이진 실행 파일 NuGet.exe가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-105">For publish operations of either a module or script, PowerShellGet requires the binary executable NuGet.exe.</span></span> <span data-ttu-id="81baf-106">*찾기*, *설치*, *저장*, *제거* 등 기타 모든 작업을 수행할 때는 NuGet 공급자만 있으면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-106">Only the NuGet provider is required for all other operations, including *find*, *install*, *save*, and *uninstall*.</span></span>
<span data-ttu-id="81baf-107">PowerShellGet에는 NuGet 공급자와 NuGet.exe 부트스트랩을 함께 처리하거나 NuGet 공급자 부트스트랩만 처리하는 논리가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-107">PowerShellGet includes logic to handle either a combined bootstrap of the NuGet provider and NuGet.exe, or bootstrap of only the NuGet provider.</span></span> <span data-ttu-id="81baf-108">두 가지 경우 모두 프롬프트 메시지가 하나만 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-108">In either case, only a single prompt message should occur.</span></span> <span data-ttu-id="81baf-109">컴퓨터가 인터넷에 연결되어 있지 않으면 사용자나 관리자는 연결이 끊긴 컴퓨터에 NuGet 공급자 및/또는 NuGet.exe 파일의 신뢰할 수 있는 인스턴스를 복사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-109">If the machine is not connected to the Internet, the user or an administrator must copy a trusted instance of the NuGet provider and/or the NuGet.exe file to the disconnected machine.</span></span>

> [!NOTE]
> <span data-ttu-id="81baf-110">버전 6부터는 NuGet 공급자가 PowerShell 설치에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-110">Starting with version 6, the NuGet provider is included in the installation of PowerShell.</span></span>

## <a name="resolving-error-when-the-nuget-provider-has-not-been-installed-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="81baf-111">인터넷에 연결된 컴퓨터에 NuGet 공급자가 설치되지 않은 경우의 오류 해결</span><span class="sxs-lookup"><span data-stu-id="81baf-111">Resolving error when the NuGet provider has not been installed on a machine that is Internet connected</span></span>

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): n
Find-Module : NuGet provider is required to interact with NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed.
At line:1 char:1
+ Find-Module -Repository PSGallery -Verbose -Name Contoso
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Find-Module], InvalidOperationException
   + FullyQualifiedErrorId : CouldNotInstallNuGetProvider,Find-Module
```

```powershell
Find-Module -Repository PSGallery -Verbose -Name Contoso
```

```output
NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program Files\PackageManagement\ProviderAssemblies' or
'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running 'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider
now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
2.5        Contoso                             Module     PSGallery        Contoso module
```

## <a name="resolving-error-when-the-nuget-provider-is-available-and-nugetexe-is-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="81baf-112">인터넷에 연결된 컴퓨터에서 게시 작업을 수행하는 중에 NuGet 공급자는 사용할 수 있는데 NuGet.exe는 사용할 수 없는 경우의 오류 해결</span><span class="sxs-lookup"><span data-stu-id="81baf-112">Resolving error when the NuGet provider is available and NuGet.exe is not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : NuGet.exe is required to interact with NuGet-based repositories. Please ensure that NuGet.exe is available under one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetExe,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe is required to continue
PowerShellGet requires NuGet.exe to publish an item to the NuGet-based repositories. NuGet.exe must be available under one of the paths specified in PATH environment variable value. Do you want PowerShellGet to install NuGet.exe now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="resolving-error-when-both-nuget-provider-and-nugetexe-are-not-available-during-the-publish-operation-on-a-machine-that-is-internet-connected"></a><span data-ttu-id="81baf-113">인터넷에 연결된 컴퓨터에서 게시 작업을 수행하는 중에 NuGet 공급자와 NuGet.exe를 모두 사용할 수 없는 경우의 오류 해결</span><span class="sxs-lookup"><span data-stu-id="81baf-113">Resolving error when both NuGet provider and NuGet.exe are not available during the publish operation on a machine that is Internet connected</span></span>

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): N
Publish-Module : PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Please ensure that '2.8.5.201' or newer version of NuGet provider is installed and NuGet.exe is available under
one of the paths specified in PATH environment variable value.
At line:1 char:1
+ Publish-Module -Name Contoso -Repository PSGallery -Verbose
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Publish-Module], InvalidOperationException
    + FullyQualifiedErrorId : CouldNotInstallNuGetBinaries,Publish-Module
```

```powershell
Publish-Module -Name Contoso -Repository PSGallery -Verbose
```

```output
NuGet.exe and NuGet provider are required to continue
PowerShellGet requires NuGet.exe and NuGet provider version '2.8.5.201' or newer to interact with the NuGet-based repositories. Do you want PowerShellGet to install both NuGet.exe and NuGet provider now?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: Installing NuGet.exe.
VERBOSE: Successfully published module 'Contoso' to the module publish location 'https://www.powershellgallery.com/api/v2/'. Please allow few minutes for 'Contoso' to show up in the search results.
```

## <a name="manually-bootstrapping-the-nuget-provider-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="81baf-114">인터넷에 연결되지 않은 컴퓨터에서 수동으로 NuGet 공급자 부트스트래핑</span><span class="sxs-lookup"><span data-stu-id="81baf-114">Manually bootstrapping the NuGet provider on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="81baf-115">위에 나와 있는 프로세스에서는 컴퓨터가 인터넷에 연결되어 있으며 공용 위치에서 파일을 다운로드할 수 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-115">The processes demonstrated above assume the machine is connected to the Internet and can download files from a public location.</span></span> <span data-ttu-id="81baf-116">파일을 다운로드할 수 없는 경우에는 위에 제공된 프로세스를 사용하여 컴퓨터를 부트스트래핑하고, 신뢰할 수 있는 오프라인 프로세스를 통해 격리된 노드에 공급자를 수동으로 복사하는 방법만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-116">If that is not possible, the only option is to bootstrap a machine using the processes given above, and manually copy the provider to the isolated node through an offline trusted process.</span></span> <span data-ttu-id="81baf-117">격리된 환경을 지원하는 비공개 갤러리를 사용할 수 있는 경우에 이 시나리오를 가장 흔히 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-117">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span>

<span data-ttu-id="81baf-118">위의 프로세스에 따라 인터넷에 연결된 컴퓨터를 부트스트래핑하고 나면 다음 위치에서 공급자 파일을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-118">After following the process above to bootstrap an Internet connected machine, you will find provider files in the location:</span></span>

`C:\Program Files\PackageManagement\ProviderAssemblies\`

<span data-ttu-id="81baf-119">NuGet 공급자의 폴더/파일 구조는 다음과 같습니다(버전 번는 다를 수 있음).</span><span class="sxs-lookup"><span data-stu-id="81baf-119">The folder/file structure of the NuGet provider will be (possibly with a different version number):</span></span>

```
NuGet
--2.8.5.208
----Microsoft.PackageManagement.NuGetProvider.dll
```

<span data-ttu-id="81baf-120">신뢰할 수 있는 프로세스를 사용하여 오프라인 컴퓨터에 이러한 폴더와 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-120">Copy these folders and file using a trusted process to the offline machines.</span></span>

## <a name="manually-bootstrapping-nugetexe-to-support-publish-operations-on-a-machine-that-is-not-connected-to-the-internet"></a><span data-ttu-id="81baf-121">인터넷에 연결되지 않은 컴퓨터에서 게시 작업을 지원하도록 수동으로 NuGet.exe 부트스트래핑</span><span class="sxs-lookup"><span data-stu-id="81baf-121">Manually bootstrapping NuGet.exe to support publish operations on a machine that is not connected to the Internet</span></span>

<span data-ttu-id="81baf-122">컴퓨터를 사용하여 `Publish-Module` 또는 `Publish-Script` cmdlet을 통해 개인 갤러리에 모듈이나 스크립트를 게시하려는 경우에는 NuGet 공급자를 수동으로 부트스트래핑하는 프로세스 외에 NuGet.exe 이진 실행 파일도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-122">In addition to the process to manually bootstrap the NuGet provider, if the machine will be used to publish modules or scripts to a private gallery using the `Publish-Module` or `Publish-Script` cmdlets, the NuGet.exe binary executable file will be required.</span></span>

<span data-ttu-id="81baf-123">격리된 환경을 지원하는 비공개 갤러리를 사용할 수 있는 경우에 이 시나리오를 가장 흔히 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-123">The most common use case for this scenario is when a private gallery is available to support an isolated environment.</span></span> <span data-ttu-id="81baf-124">두 가지 옵션을 통해 NuGet.exe 파일을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-124">There are two options to obtain the NuGet.exe file.</span></span>

<span data-ttu-id="81baf-125">첫 번째 옵션은 인터넷에 연결된 컴퓨터를 부트스트래핑하고 신뢰할 수 있는 프로세스를 사용하여 오프라인 컴퓨터에 파일을 복사하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-125">One option is to bootstrap a machine that is Internet connected and copy the files to the offline machines using a trusted process.</span></span> <span data-ttu-id="81baf-126">인터넷에 연결된 컴퓨터를 부트스트래핑하고 나면 NuGet.exe 이진 파일이 두 폴더 중 하나에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-126">After bootstrapping the Internet connected machine, the NuGet.exe binary will be located in one of two folders:</span></span>

<span data-ttu-id="81baf-127">`Publish-Module` 또는 `Publish-Script` cmdlet을 관리자 권한으로 실행한 경우</span><span class="sxs-lookup"><span data-stu-id="81baf-127">If the `Publish-Module` or `Publish-Script` cmdlets were executed with elevated permissions (As an Administrator):</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="81baf-128">cmdlet을 관리자 권한이 없는 사용자로 실행한 경우</span><span class="sxs-lookup"><span data-stu-id="81baf-128">If the cmdlets were executed as a user without elevated permissions:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```

<span data-ttu-id="81baf-129">두 번째 옵션은 NuGet.Org 웹 사이트 [https://dist.nuget.org/index.html](https://www.nuget.org/downloads)에서 NuGet.exe를 다운로드하는 것입니다. 프로덕션 컴퓨터용 NuGet 버전을 선택할 때는 "권장" 레이블이 있는 2.8.5.208 이상 버전을 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-129">A second option is to download NuGet.exe from the NuGet.Org website: [https://dist.nuget.org/index.html](https://www.nuget.org/downloads) When selecting a NugGet version for production machines, make sure it is later than 2.8.5.208, and identify the version that has been labeled "recommended".</span></span> <span data-ttu-id="81baf-130">브라우저를 사용하여 다운로드한 파일의 경우 차단을 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-130">Remember to unblock the file if it was downloaded using a browser.</span></span> <span data-ttu-id="81baf-131">`Unblock-File` cmdlet을 사용하여 차단을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-131">This can be performed by using the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="81baf-132">두 가지 방법 중 어떤 쪽을 사용하든 `$env:path`의 모든 위치에 NuGet.exe 파일을 복사할 수 있지만, 표준 위치는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81baf-132">In either case, the NuGet.exe file can be copied to any location in `$env:path`, but the standard locations are:</span></span>

<span data-ttu-id="81baf-133">모든 사용자가 `Publish-Module` 및 `Publish-Script` cmdlet을 사용할 수 있도록 실행 파일을 제공하려는 경우</span><span class="sxs-lookup"><span data-stu-id="81baf-133">To make the executable available so that all users can use `Publish-Module` and `Publish-Script` cmdlets:</span></span>

```powershell
$env:ProgramData\Microsoft\Windows\PowerShell\PowerShellGet
```

<span data-ttu-id="81baf-134">특정 사용자에게만 실행 파일을 제공하려는 경우(해당 사용자의 프로필 내 위치에만 복사)</span><span class="sxs-lookup"><span data-stu-id="81baf-134">To make the executable available to only a specific user, copy to the location within only that user's profile:</span></span>

```powershell
$env:userprofile\AppData\Local\Microsoft\Windows\PowerShell\PowerShellGet\
```
