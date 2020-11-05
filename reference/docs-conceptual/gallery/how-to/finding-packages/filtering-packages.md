---
ms.date: 06/12/2017
title: 검색 결과 필터링
description: 이 문서에서는 PowerShell 갤러리에서 콘텐츠를 필터링하는 데 사용되는 사용자 인터페이스에 대해 설명합니다.
ms.openlocfilehash: cc375f3ddb35c95ed134776500bd326bc3db6b1a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661402"
---
# <a name="filtering-search-results"></a><span data-ttu-id="c1828-103">검색 결과 필터링</span><span class="sxs-lookup"><span data-stu-id="c1828-103">Filtering search results</span></span>

<span data-ttu-id="c1828-104">[패키지 탭](https://www.powershellgallery.com/packages)에는 PowerShell 갤러리에서 사용 가능한 모든 패키지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-104">The [Packages tab](https://www.powershellgallery.com/packages) displays all available packages in the PowerShell Gallery.</span></span>

<span data-ttu-id="c1828-105">패키지를 필터링, 정렬 및 검색하는 방법에는 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-105">There are several ways to filter, sort, and search the packages.</span></span> <span data-ttu-id="c1828-106">특정 패키지에 대한 자세한 정보를 보려면 해당 패키지를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-106">To see more details about a particular package, click the package.</span></span>

## <a name="filter-by"></a><span data-ttu-id="c1828-107">필터 기준</span><span class="sxs-lookup"><span data-stu-id="c1828-107">Filter By</span></span>

<span data-ttu-id="c1828-108">“필터 기준” 아래의 드롭다운에서는 다음을 기준으로 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>

- <span data-ttu-id="c1828-109">시험판 포함</span><span class="sxs-lookup"><span data-stu-id="c1828-109">Include Prerelease</span></span>
- <span data-ttu-id="c1828-110">안정적인 항목만</span><span class="sxs-lookup"><span data-stu-id="c1828-110">Stable Only</span></span>

<span data-ttu-id="c1828-111">“시험판” 및 “안정적인 항목”에 대한 내용은 PowerShell 팀 블로그의 [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/)(PowerShellGet 및 PowerShell 갤러리에 추가된 시험판 버전)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1828-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="c1828-112">드롭다운의 확인란을 사용하여 다음을 기준으로 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>

- <span data-ttu-id="c1828-113">패키지 종류</span><span class="sxs-lookup"><span data-stu-id="c1828-113">Package Types</span></span>
  - <span data-ttu-id="c1828-114">모듈</span><span class="sxs-lookup"><span data-stu-id="c1828-114">Module</span></span>
  - <span data-ttu-id="c1828-115">스크립트</span><span class="sxs-lookup"><span data-stu-id="c1828-115">Script</span></span>
- <span data-ttu-id="c1828-116">범주</span><span class="sxs-lookup"><span data-stu-id="c1828-116">Categories</span></span>
  - <span data-ttu-id="c1828-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c1828-117">Cmdlet</span></span>
  - <span data-ttu-id="c1828-118">DSC 리소스</span><span class="sxs-lookup"><span data-stu-id="c1828-118">DSC Resource</span></span>
  - <span data-ttu-id="c1828-119">함수</span><span class="sxs-lookup"><span data-stu-id="c1828-119">Function</span></span>
  - <span data-ttu-id="c1828-120">역할 기능</span><span class="sxs-lookup"><span data-stu-id="c1828-120">Role Capability</span></span>
  - <span data-ttu-id="c1828-121">워크플로</span><span class="sxs-lookup"><span data-stu-id="c1828-121">Workflow</span></span>

<span data-ttu-id="c1828-122">PowerShell 갤러리의 모듈만 보려면 [패키지 종류]에서 [모듈]을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-122">To see only modules in the PowerShell Gallery, check Module in the Package Types.</span></span> <span data-ttu-id="c1828-123">마찬가지로 PowerShell 갤러리에서 스크립트만 보려면 [패키지 종류]에서 [스크립트]를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Package Types.</span></span>

> [!NOTE]
> <span data-ttu-id="c1828-124">필터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-124">Filters are inclusive.</span></span> <span data-ttu-id="c1828-125">예제: cmdlet과 함수를 둘 다 포함하는 패키지는 [Cmdlet] 또는 [함수] \(또는 둘 다)를 선택한 경우에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-125">Example: A package containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span> <span data-ttu-id="c1828-126">둘 다 선택하지 않으면 패키지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-126">If neither are selected, the package will not appear.</span></span> <span data-ttu-id="c1828-127">마찬가지로, 모든 범주를 선택하면 이러한 범주 중 하나를 포함하는 패키지만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-127">Similarly, if all categories are selected, only packages containing one of those categories will appear.</span></span> <span data-ttu-id="c1828-128">**이러한 범주에 속하지 않는 패키지는 표시되지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="c1828-128">**Packages that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="c1828-129">정렬 기준</span><span class="sxs-lookup"><span data-stu-id="c1828-129">Sort By</span></span>

<span data-ttu-id="c1828-130">[정렬 기준] 드롭다운에서 다음을 기준으로 결과를 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-130">The Sort By drop-down allows users to sort the results by:</span></span>

- <span data-ttu-id="c1828-131">인기도 - 인기도는 다운로드 횟수에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="c1828-132">A-Z - 패키지 이름을 기준으로 사전순으로 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-132">A-Z - Alphabetically by package name</span></span>
- <span data-ttu-id="c1828-133">최근 - 게시 날짜순으로 패키지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-133">Recent - Packages appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="c1828-134">검색 상자</span><span class="sxs-lookup"><span data-stu-id="c1828-134">Search Box</span></span>

<span data-ttu-id="c1828-135">검색 상자에서 키워드로 패키지를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1828-135">The Search Box allows users to search the packages on keywords.</span></span>
<span data-ttu-id="c1828-136">자세한 내용은 [갤러리 검색 구문](search-syntax.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1828-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
