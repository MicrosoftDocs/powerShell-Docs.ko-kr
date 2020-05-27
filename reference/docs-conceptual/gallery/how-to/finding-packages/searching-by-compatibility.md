---
ms.date: 12/11/2018
contributor: JKeithB, SydneyhSmith
keywords: gallery,powershell,cmdlet,psgallery
title: 호환 가능한 PowerShell 버전 또는 운영 체제가 있는 패키지
ms.openlocfilehash: fce1383fa604a555a40b050ce92c5cc45ca7054c
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83691456"
---
# <a name="packages-with-compatible-powershell-editions-or-operating-systems"></a><span data-ttu-id="f5569-103">호환 가능한 PowerShell 버전 또는 운영 체제가 있는 패키지</span><span class="sxs-lookup"><span data-stu-id="f5569-103">Packages with compatible PowerShell Editions or Operating Systems</span></span>

<span data-ttu-id="f5569-104">버전 5.1부터 PowerShell은 다양한 기능 세트 및 플랫폼 호환성을 나타내는 다양한 버전으로 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibilities.</span></span>

## <a name="searching-by-powershell-edition"></a><span data-ttu-id="f5569-105">PowerShell 버전으로 검색</span><span class="sxs-lookup"><span data-stu-id="f5569-105">Searching by PowerShell Edition</span></span>

<span data-ttu-id="f5569-106">두 버전의 PowerShell은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-106">The two editions of PowerShell are:</span></span>

- <span data-ttu-id="f5569-107">**Desktop Edition:** .NET Framework를 기반으로 구축되며 Server Core 및 Windows Desktop과 같은 전체 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 지정하는 스크립트 및 모듈과 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-107">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="f5569-108">**Core Edition:** .NET Framework를 기반으로 구축되며 Nano 서버 및 Windows IoT와 같은 축소된 버전의 Windows에서 실행되는 PowerShell 버전을 대상으로 지정하는 스크립트 및 모듈과 호환성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-108">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

### <a name="powershell-gallery-allows-you-to-filter-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="f5569-109">PowerShell 갤러리를 사용하면 특정 PowerShell 버전에서 호환 가능한 패키지를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-109">PowerShell Gallery allows you to filter packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="f5569-110">패키지에서 호환되는 PSEdition을 지정한 경우 패키지 표시 페이지 및 패키지 결과에 'PowerShell 버전'의 일부로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-110">If a package has compatible PSEditions specified, they are listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>
<span data-ttu-id="f5569-111">PowerShell을 사용하여 호환 가능한 패키지를 검색할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-111">You can also search for compatible packages using PowerShell.</span></span>

![PSEditions가 있는 항목 표시 페이지](media/searching-by-compatibility/packagedisplaypagewithpseditions.PNG)

### <a name="search-for-packages-in-the-gallery-ui-that-work-on-powershell-core"></a><span data-ttu-id="f5569-113">PowerShell Core에서 작동하는 패키지 갤러리 UI에서 검색</span><span class="sxs-lookup"><span data-stu-id="f5569-113">Search for packages in the gallery UI that work on PowerShell Core</span></span>

<span data-ttu-id="f5569-114">Tags:"PSEdition_Desktop" 및 Tags:"PSEdition_Core"를 사용하여 PowerShell 갤러리에 있는 패키지를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-114">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspsedition_core-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="f5569-115">Tags:"PSEdition_Core"를 사용하여 PowerShell Core Edition과 호환되는 항목을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-115">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Core PSEdition과 호환되는 항목에 대한 검색 결과](media/searching-by-compatibility/searchresultswithpseditions.PNG)

### <a name="use-tagspsedition_desktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="f5569-117">Tags:"PSEdition_Desktop"을 사용하여 PowerShell Desktop Edition과 호환되는 항목을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-117">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Desktop PSEdition과 호환되는 항목에 대한 검색 결과](media/searching-by-compatibility/searchresultswithpseditionsdesktop.PNG)

### <a name="search-for-packages-to-find-compatible-editions-using-powershell"></a><span data-ttu-id="f5569-119">패키지를 검색하여 PowerShell을 사용하여 호환 가능한 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="f5569-119">Search for packages to find compatible editions using PowerShell</span></span>
<span data-ttu-id="f5569-120">PowerShell 버전 및 OS에서 필터링할 태그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-120">You can specify tags to filter for the PowerShell edition and OS.</span></span>
<span data-ttu-id="f5569-121">`-Tag` 매개 변수를 지정하는 `Find-Package` cmdlet을 사용하여 대상으로 지정한 버전(및 OS)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-121">You use the `Find-Package` cmdlet specifying the `-Tag` parameter to specify the edition (and OS) you are targeting.</span></span>
<span data-ttu-id="f5569-122">다음과 같이:</span><span class="sxs-lookup"><span data-stu-id="f5569-122">Like this:</span></span>

```powershell
# Find modules compatible with PowerShell Core:
Find-Module -Tag PSEdition_Core

# Find modules compatible with PowerShell Core on Linux:
Find-Module -Tag PSEdition_Core, Linux
```

## <a name="searching-by-operating-system"></a><span data-ttu-id="f5569-123">운영 체제로 검색</span><span class="sxs-lookup"><span data-stu-id="f5569-123">Searching by Operating System</span></span>

<span data-ttu-id="f5569-124">PowerShell Core가 Windows, Linux 및 MacOS에서 제공되므로 갤러리에 있는 패키지는 이러한 운영 체제 조합에 대해서 설계되었을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-124">Since PowerShell Core is available for Windows, Linux, and MacOS, packages in the Gallery may be designed for any combination of these operating systems.</span></span> <span data-ttu-id="f5569-125">갤러리 UI에서 다음 검색 태그를 사용하여 운영 체제별로 태그가 지정된 패키지를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-125">In the gallery UI use the following searchs tags to find packages tagged by operating system:</span></span>

- <span data-ttu-id="f5569-126">태그: "Windows"</span><span class="sxs-lookup"><span data-stu-id="f5569-126">Tags: "Windows"</span></span>
- <span data-ttu-id="f5569-127">태그: "Linux"</span><span class="sxs-lookup"><span data-stu-id="f5569-127">Tags: "Linux"</span></span>
- <span data-ttu-id="f5569-128">태그: "MacOS"</span><span class="sxs-lookup"><span data-stu-id="f5569-128">Tags: "MacOS"</span></span>

<span data-ttu-id="f5569-129">다음과 같이 `Find-Module`에서 이러한 태그(및 PowerShellGet 모듈의 다른 cmdlet)를 지정할 수 있습니다</span><span class="sxs-lookup"><span data-stu-id="f5569-129">You can specify these tags on `Find-Module` (and other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find Modules compatible with Windows
Find-Module -Tag Linux
```

## <a name="searching-for-multiple-compatibilities"></a><span data-ttu-id="f5569-130">여러 호환성 검색</span><span class="sxs-lookup"><span data-stu-id="f5569-130">Searching for Multiple Compatibilities</span></span>

<span data-ttu-id="f5569-131">다음 구문을 사용하여 여러 호환성을 포함하는 패키지를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-131">You can look for a package that has multiple compatibilities by using the syntax:</span></span>

<span data-ttu-id="f5569-132">태그: "Compatibility1" "Compatibility2"</span><span class="sxs-lookup"><span data-stu-id="f5569-132">Tags: "Compatibility1" "Compatibility2"</span></span>

<span data-ttu-id="f5569-133">예를 들어 내 Windows 및 Linux 머신 모두에서 실행되는 PowerShell Core와 호환 가능한 패키지를 찾는 경우 다음 검색 태그를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f5569-133">For example, if you are looking for a package with PowerShell Core Compatibility that runs on both my Windows and Linux machines, use the search tags:</span></span>

<span data-ttu-id="f5569-134">태그: "PSEdition_Core" "Windows" "Linux"</span><span class="sxs-lookup"><span data-stu-id="f5569-134">Tags: "PSEdition_Core" "Windows" "Linux"</span></span>

<span data-ttu-id="f5569-135">PowerShell을 사용하여 검색하려면 다음과 같이 `Find-Module`(및 PowerShellGet 모듈의 다른 cmdlet)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5569-135">To search using PowerShell, you can use the `Find-Module` (and the other cmdlets in the PowerShellGet module), like this:</span></span>

```powershell
# Find scripts compatible with PowerShell Core, Windows, and Linux
Find-Script -Tag PSEdition_Core,Linux,Windows

# Find modules compatible with PowerSHellCore and MacOS
Find-Module -Tag PSEdition_Core,MacOS
```

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="f5569-136">호환되는 PowerShell 버전이 있는 패키지를 작성 및 찾는 방법에 대한 자세한 내용</span><span class="sxs-lookup"><span data-stu-id="f5569-136">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="f5569-137">PSEditions가 있는 모듈</span><span class="sxs-lookup"><span data-stu-id="f5569-137">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="f5569-138">PSEditions가 있는 스크립트</span><span class="sxs-lookup"><span data-stu-id="f5569-138">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
