---
ms.date: 07/29/2020
keywords: powershell,cmdlet
title: PowerShell 설명서를 사용하는 방법
description: 이 문서에서는 검색 필터링 및 버전 선택을 포함하여 이 사이트의 기능을 사용하는 방법을 설명합니다.
ms.openlocfilehash: b7e036fce0abb12f6c1ab4c0092784321a41a916
ms.sourcegitcommit: 2fc6ee49a70bda4c59135136bd5cc7782836a124
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94810303"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="af2da-104">PowerShell 설명서를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="af2da-104">How to use the PowerShell documentation</span></span>

<span data-ttu-id="af2da-105">PowerShell 온라인 설명서에 오신 것을 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-105">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="af2da-106">이 사이트에는 다음 버전의 PowerShell에 대한 cmdlet 참조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-106">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="af2da-107">PowerShell 7.2(시험판)</span><span class="sxs-lookup"><span data-stu-id="af2da-107">PowerShell 7.2 (prerelease)</span></span>
- <span data-ttu-id="af2da-108">PowerShell 7.1(현재)</span><span class="sxs-lookup"><span data-stu-id="af2da-108">PowerShell 7.1 (current)</span></span>
- <span data-ttu-id="af2da-109">PowerShell 7.0(LTS)</span><span class="sxs-lookup"><span data-stu-id="af2da-109">PowerShell 7.0 (LTS)</span></span>
- <span data-ttu-id="af2da-110">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="af2da-110">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="af2da-111">문서 찾기 및 버전 선택</span><span class="sxs-lookup"><span data-stu-id="af2da-111">Finding articles and selecting a version</span></span>

<span data-ttu-id="af2da-112">문서에서 콘텐츠를 검색하는 방법에는 두 가지가 있습니다. 가장 간단한 방법은 버전 선택기에서 필터 상자를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-112">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="af2da-113">문서의 제목에 표시되는 단어를 입력하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-113">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="af2da-114">페이지에 일치하는 문서 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-114">The page displays a list of matching articles.</span></span> <span data-ttu-id="af2da-115">해당 목록에서 전체 사이트를 검색하는 옵션을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-115">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="af2da-116">기본적으로 이 사이트에는 출시된 최신 버전의 PowerShell에 대한 설명서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-116">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="af2da-117">일부 cmdlet은 다양한 버전의 PowerShell에서 다르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-117">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="af2da-118">사용 중인 PowerShell 버전에 대한 설명서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="af2da-118">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="af2da-119">페이지 위쪽의 버전 선택기를 사용하여 원하는 PowerShell 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-119">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![버전 선택기 사용](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="af2da-121">사용 중인 PowerShell의 버전은 `$PSversionTable.PSVersion` 값을 검사해서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-121">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="af2da-122">다음 예제에서는 Windows PowerShell v5.1의 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-122">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="af2da-123">PowerShell을 처음 사용하고 명령 구문을 이해하는 데 도움이 필요하면 [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af2da-123">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="af2da-124">이전 버전에 대한 문서 찾기</span><span class="sxs-lookup"><span data-stu-id="af2da-124">Finding articles for previous versions</span></span>

<span data-ttu-id="af2da-125">이전 버전의 PowerShell에 대한 설명서는 [이전 버전](https://aka.ms/PSLegacyDocs) 사이트에서 보관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-125">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="af2da-126">이 사이트에는 다음 항목에 대한 설명서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af2da-126">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="af2da-127">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="af2da-127">PowerShell 3.0</span></span>
- <span data-ttu-id="af2da-128">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="af2da-128">PowerShell 4.0</span></span>
- <span data-ttu-id="af2da-129">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="af2da-129">PowerShell 5.0</span></span>
- <span data-ttu-id="af2da-130">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="af2da-130">PowerShell 6</span></span>
- <span data-ttu-id="af2da-131">PowerShell 워크플로</span><span class="sxs-lookup"><span data-stu-id="af2da-131">PowerShell Workflows</span></span>
- <span data-ttu-id="af2da-132">PowerShell 웹 액세스</span><span class="sxs-lookup"><span data-stu-id="af2da-132">PowerShell Web Access</span></span>
