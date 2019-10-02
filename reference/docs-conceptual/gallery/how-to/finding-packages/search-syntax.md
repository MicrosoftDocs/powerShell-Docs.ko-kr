---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: 갤러리 검색 구문
ms.openlocfilehash: aabcaa1f1b5b641ab5033c9ba2e358477c84a23b
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328454"
---
# <a name="gallery-search-syntax"></a><span data-ttu-id="82895-103">갤러리 검색 구문</span><span class="sxs-lookup"><span data-stu-id="82895-103">Gallery Search Syntax</span></span>

<span data-ttu-id="82895-104">[PowerShell 갤러리 웹 사이트](https://www.powershellgallery.com/)를 사용하여 PowerShell 갤러리를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82895-104">You can search the PowerShell Gallery using the [PowerShell Gallery's web site](https://www.powershellgallery.com/).</span></span>
<span data-ttu-id="82895-105">PowerShell 갤러리 웹 사이트는 단어, 구 및 키워드 식을 사용하여 검색 결과 범위를 좁힐 수 있는 텍스트 검색 상자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-105">PowerShell Gallery web site offers a text searchbox where you can use words, phrases and keyword expressions to narrow down search results.</span></span>

## <a name="search-by-keywords"></a><span data-ttu-id="82895-106">키워드로 검색</span><span class="sxs-lookup"><span data-stu-id="82895-106">Search by Keywords</span></span>

    dsc azure sql

<span data-ttu-id="82895-107">검색은 3가지 키워드를 모두 포함하는 관련 문서를 찾으려고 하며 일치하는 문서를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-107">Search attempts to find relevant documents containing all 3 keywords, and return matching documents.</span></span>

## <a name="search-using-phrases-and-keywords"></a><span data-ttu-id="82895-108">구문 및 키워드를 사용하여 검색</span><span class="sxs-lookup"><span data-stu-id="82895-108">Search using Phrases and keywords</span></span>

    "azure sql" deployment

<span data-ttu-id="82895-109">따옴표("") 사이에 구를 입력하면 별도 키워드가 아닌 특정 구를 찾도록 검색이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="82895-109">Entering a phrase between quotation marks ("") change the search to look for the particular phrase instead of separate keywords.</span></span>
<span data-ttu-id="82895-110">일반적으로 일치하는 문서에는 대/소문자 변형(예: "Azure SQL")을 포함하여 "azure sql" 구가 정확하게 포함되어야 하며, 대체로 '배포'라는 단어도 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="82895-110">Matching documents should usually contain the exact phrase "azure sql", including variations on capitalization e.g. "Azure SQL", and also usually contain the word 'deployment'.</span></span>

## <a name="filtering-on-fields"></a><span data-ttu-id="82895-111">필드 필터링</span><span class="sxs-lookup"><span data-stu-id="82895-111">Filtering on fields</span></span>

<span data-ttu-id="82895-112">특정 패키지 ID(또는 'Id' 또는 'id')를 검색하거나 검색어 앞에 필드 이름을 추가하여 다른 특정 필드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82895-112">You can search for a specific package ID (or 'Id' or 'id'), or certain other fields by prefixing search terms with the field name.</span></span>

<span data-ttu-id="82895-113">현재 검색 가능한 필드는 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' 및 'PowerShellVersion'입니다.</span><span class="sxs-lookup"><span data-stu-id="82895-113">Currently the searchable fields are 'Id', 'Version', 'Tags', 'Author', 'Owner', 'Functions', 'Cmdlets', 'DscResources' and 'PowerShellVersion'.</span></span>

<span data-ttu-id="82895-114">[ID와 제목 간의 차이점은 무엇인가요?</span><span class="sxs-lookup"><span data-stu-id="82895-114">[What's the difference between ID and Title?</span></span> <span data-ttu-id="82895-115">ID는 콘솔에서 사용하는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="82895-115">ID is the name you use in the console.</span></span> <span data-ttu-id="82895-116">제목은 검색 결과에서 패키지 페이지의 맨 위에 표시되는 내용입니다.]</span><span class="sxs-lookup"><span data-stu-id="82895-116">Title is what is shown at the top of the package page in search results.]</span></span>

## <a name="examples"></a><span data-ttu-id="82895-117">예</span><span class="sxs-lookup"><span data-stu-id="82895-117">Examples</span></span>

    ID:PSReadline
    
<span data-ttu-id="82895-118">"PSReadline"을 포함하는 ID를 사용하여 패키지를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="82895-118">finds packages with an ID containing "PSReadline".</span></span>

    Id:"AzureRM.Profile"

<span data-ttu-id="82895-119">ID 필드에 "AzureRM.Profile"이 포함된 패키지를 찾는 다른 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="82895-119">is another way to find packages with "AzureRM.Profile" in their ID field.</span></span>

<span data-ttu-id="82895-120">'Id' 필터는 부분 문자열 일치이므로 다음을 검색하는 경우</span><span class="sxs-lookup"><span data-stu-id="82895-120">The 'Id' filter is a substring match, so if you search for the following:</span></span>

    Id:"azure"

<span data-ttu-id="82895-121">이 검색은 'AzureRM.Profile' 및 'Azure.Storage'를 포함하는 결과를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-121">This provides results that include AzureRM.Profile' and 'Azure.Storage'.</span></span>

<span data-ttu-id="82895-122">또한 단일 필드에서 여러 키워드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82895-122">You can also search for multiple keywords in a single field.</span></span> 

    id:azure tags:intellisense

<span data-ttu-id="82895-123">또한 큰따옴표를 사용하여 구를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82895-123">And you can perform phrase searches using double quotes:</span></span>

    id:"azure.storage"

<span data-ttu-id="82895-124">DSC 태그가 있는 패키지를 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-124">To search all packages with DSC tag.</span></span>

    Tags:DSC

<span data-ttu-id="82895-125">지정된 함수가 있는 패키지를 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-125">To search all packages with the specified function.</span></span>

    Functions:Get-TreeSize

<span data-ttu-id="82895-126">지정된 cmdlet이 있는 패키지를 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-126">To search all packages with the specified cmdlet.</span></span>

    Cmdlets:Get-AzureRmEnvironment

<span data-ttu-id="82895-127">지정된 DSC 리소스 이름이 있는 패키지를 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-127">To search all packages with the specified DSC Resource name.</span></span>

    DscResources:xArchive

<span data-ttu-id="82895-128">지정된 PowerShellVersion이 있는 패키지를 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="82895-128">To search all packages with the specified PowerShellVersion</span></span>

    PowerShellVersion:2.0

<span data-ttu-id="82895-129">마지막으로, 지원되지 않는 필드(예: 'commands')를 사용하는 경우 필드가 무시되고 모든 필드가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="82895-129">Finally, if you use a field we don't support, such as 'commands', we'll just ignore it and search all the fields.</span></span> <span data-ttu-id="82895-130">따라서 다음 쿼리의 경우</span><span class="sxs-lookup"><span data-stu-id="82895-130">So the following query</span></span>

    commands:blobs storage

<span data-ttu-id="82895-131">다음 쿼리와 똑같이 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="82895-131">Is interpreted exactly the same as this query:</span></span>

    blobs storage
