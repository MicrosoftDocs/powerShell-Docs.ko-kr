---
ms.date: 07/29/2020
keywords: powershell,cmdlet
title: PowerShell 설명서를 사용하는 방법
ms.openlocfilehash: 1cfeb9eea564e7618062e1b8ada4948bd9e22969
ms.sourcegitcommit: 9f9eb95bc859e9e0fed48101327a602b2ced351d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87821532"
---
# <a name="how-to-use-the-powershell-documentation"></a><span data-ttu-id="56544-103">PowerShell 설명서를 사용하는 방법</span><span class="sxs-lookup"><span data-stu-id="56544-103">How to use the PowerShell documentation</span></span>

<span data-ttu-id="56544-104">PowerShell 온라인 설명서에 오신 것을 환영합니다.</span><span class="sxs-lookup"><span data-stu-id="56544-104">Welcome to the PowerShell online documentation.</span></span> <span data-ttu-id="56544-105">이 사이트에는 다음 버전의 PowerShell에 대한 cmdlet 참조가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56544-105">This site contains cmdlet reference for the following versions of PowerShell:</span></span>

- <span data-ttu-id="56544-106">PowerShell 7</span><span class="sxs-lookup"><span data-stu-id="56544-106">PowerShell 7</span></span>
- <span data-ttu-id="56544-107">PowerShell 6</span><span class="sxs-lookup"><span data-stu-id="56544-107">PowerShell 6</span></span>
- <span data-ttu-id="56544-108">PowerShell 5.1</span><span class="sxs-lookup"><span data-stu-id="56544-108">PowerShell 5.1</span></span>

## <a name="finding-articles-and-selecting-a-version"></a><span data-ttu-id="56544-109">문서 찾기 및 버전 선택</span><span class="sxs-lookup"><span data-stu-id="56544-109">Finding articles and selecting a version</span></span>

<span data-ttu-id="56544-110">문서에서 콘텐츠를 검색하는 방법에는 두 가지가 있습니다. 가장 간단한 방법은 버전 선택기에서 필터 상자를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="56544-110">There are two ways to search for content in Docs. The simplest way is to use the filter box under the version selector.</span></span> <span data-ttu-id="56544-111">문서의 제목에 표시되는 단어를 입력하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="56544-111">Just enter a word that appears in the title of an article.</span></span> <span data-ttu-id="56544-112">페이지에 일치하는 문서 목록이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56544-112">The page displays a list of matching articles.</span></span> <span data-ttu-id="56544-113">해당 목록에서 전체 사이트를 검색하는 옵션을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56544-113">You can also select the option to search the entire site from that list.</span></span>

<span data-ttu-id="56544-114">기본적으로 이 사이트에는 출시된 최신 버전의 PowerShell에 대한 설명서가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56544-114">By default, this site displays documentation for the latest released version of PowerShell.</span></span> <span data-ttu-id="56544-115">일부 cmdlet은 다양한 버전의 PowerShell에서 다르게 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="56544-115">Some cmdlets work differently in various versions of PowerShell.</span></span> <span data-ttu-id="56544-116">사용 중인 PowerShell 버전에 대한 설명서를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="56544-116">Be sure you are viewing the documentation for the version of PowerShell you are using.</span></span>

<span data-ttu-id="56544-117">페이지 위쪽의 버전 선택기를 사용하여 원하는 PowerShell 버전을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="56544-117">Use the version picker at the top of the page to select the version of PowerShell you want.</span></span>

![버전 선택기 사용](media/how-to-use-docs/version-search.gif)

<span data-ttu-id="56544-119">사용 중인 PowerShell의 버전은 `$PSversionTable.PSVersion` 값을 검사해서 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56544-119">You can verify the version of PowerShell you are using by inspecting the `$PSversionTable.PSVersion` value.</span></span> <span data-ttu-id="56544-120">다음 예제에서는 Windows PowerShell v5.1의 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56544-120">The following example shows the output for Windows PowerShell 5.1.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      19041  1
```

<span data-ttu-id="56544-121">PowerShell을 처음 사용하고 명령 구문을 이해하는 데 도움이 필요하면 [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="56544-121">If you are new to PowerShell and need help understanding the command syntax, see [about_Command_Syntax](/powershell/module/microsoft.powershell.core/about/about_command_syntax).</span></span>

## <a name="finding-articles-for-previous-versions"></a><span data-ttu-id="56544-122">이전 버전에 대한 문서 찾기</span><span class="sxs-lookup"><span data-stu-id="56544-122">Finding articles for previous versions</span></span>

<span data-ttu-id="56544-123">이전 버전의 PowerShell에 대한 설명서는 [이전 버전](https://aka.ms/PSLegacyDocs) 사이트에서 보관되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56544-123">Documentation for older versions of PowerShell has been archived in our [Previous Versions](https://aka.ms/PSLegacyDocs) site.</span></span>

<span data-ttu-id="56544-124">이 사이트에는 다음 항목에 대한 설명서가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56544-124">This site contains documentation for the following topics:</span></span>

- <span data-ttu-id="56544-125">PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="56544-125">PowerShell 3.0</span></span>
- <span data-ttu-id="56544-126">PowerShell 4.0</span><span class="sxs-lookup"><span data-stu-id="56544-126">PowerShell 4.0</span></span>
- <span data-ttu-id="56544-127">PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="56544-127">PowerShell 5.0</span></span>
- <span data-ttu-id="56544-128">PowerShell 워크플로</span><span class="sxs-lookup"><span data-stu-id="56544-128">PowerShell Workflows</span></span>
- <span data-ttu-id="56544-129">PowerShell 웹 액세스</span><span class="sxs-lookup"><span data-stu-id="56544-129">PowerShell Web Access</span></span>
