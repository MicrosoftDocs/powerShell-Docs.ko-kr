---
title: 공급자 도움말 항목에 대 한 참고 항목 섹션을 추가 하는 방법 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: b6561120d1bbe848ab4ebcdec7de92c6cad96314
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564826"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="9fb10-102">공급자 도움말 항목에 참고 항목 섹션을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="9fb10-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="9fb10-103">이 섹션에서는 공급자 도움말 항목의 **참고** 항목 섹션을 채우는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="9fb10-104">**참고** 항목 섹션은 공급자와 관련 된 항목의 목록으로 구성 되거나 사용자가 공급자를 보다 잘 이해 하 고 사용 하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="9fb10-105">항목 목록에는 Windows PowerShell의 cmdlet 도움말, 공급자 도움말 및 개념 ("about") 도움말 항목이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="9fb10-106">또한 현재 공급자 도움말 항목의 온라인 버전을 비롯 하 여 책, 용지 및 온라인 항목에 대 한 참조를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="9fb10-107">온라인 항목을 참조 하는 경우 URI 또는 검색 용어를 일반 텍스트로 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="9fb10-108">`Get-Help`Cmdlet은 목록에 있는 항목에 연결 하거나 리디렉션하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="9fb10-109">또한 `Online` cmdlet의 매개 변수는 `Get-Help` 공급자 도움말에서 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="9fb10-110">참고 항목 섹션은 `RelatedLinks` 요소와 요소에 포함 된 태그에서 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="9fb10-111">다음 XML은 태그를 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="9fb10-112">"참고 항목" 항목을 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="9fb10-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="9fb10-113">Dll-help 파일 *AssemblyName*의 요소 내에서 `providerHelp` 요소를 추가 `RelatedLinks` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="9fb10-114">요소는 `RelatedLinks` 요소의 마지막 요소 여야 합니다 `providerHelp` .</span><span class="sxs-lookup"><span data-stu-id="9fb10-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="9fb10-115">`RelatedLinks`각 공급자 도움말 항목에는 하나의 요소만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="9fb10-116">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="9fb10-117">**참고** 항목 섹션의 각 항목에 대해 요소 내에서 `RelatedLinks` 요소를 추가 `navigationLink` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="9fb10-118">그런 다음 각 요소 내에서 `navigationLink` 요소 하 나와 요소 하나를 추가 `linkText` `uri` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="9fb10-119">요소를 사용 하지 않는 경우 `uri` 해당 요소를 빈 요소 ( \< uri/>)로 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="9fb10-120">다음은 그 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="9fb10-121">태그 사이에 항목 이름을 입력 합니다 `linkText` .</span><span class="sxs-lookup"><span data-stu-id="9fb10-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="9fb10-122">URI를 제공 하는 경우 태그 사이에 입력 `uri` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="9fb10-123">현재 공급자 도움말 항목의 온라인 버전을 나타내려면 태그 사이에 `linkText` 항목 이름 대신 "online version:"을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="9fb10-124">일반적으로 "온라인 버전:" 링크는 항목 항목 목록의 첫 번째 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="9fb10-125">다음 예제에는 세 개의 참고 항목 항목이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="9fb10-126">첫 번째는 현재 항목의 온라인 버전을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="9fb10-127">두 번째는 Windows PowerShell cmdlet 도움말 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="9fb10-128">세 번째는 다른 온라인 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fb10-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
