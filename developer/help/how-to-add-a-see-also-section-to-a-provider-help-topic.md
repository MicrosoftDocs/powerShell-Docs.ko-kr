---
title: 추가 하는 방법 참조도 섹션 공급자 도움말 항목 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858349"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="6ce9e-102">공급자 도움말 항목에 참고 항목 섹션을 추가하는 방법</span><span class="sxs-lookup"><span data-stu-id="6ce9e-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="6ce9e-103">이 섹션에서는를 채우는 방법을 설명 합니다 **참고** 공급자 도움말 항목의 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="6ce9e-104">합니다 **참고** 공급자에 게 관련 된 또는 사용자를 더 잘 이해 하 고 공급자를 사용 하 여는 데 도움이 되는 항목의 목록 섹션으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="6ce9e-105">항목 목록에는 cmdlet 도움말, 공급자 도움말 포함 될 수 있습니다 ("정보") 도움말 항목 Windows PowerShell의 개념 및 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="6ce9e-106">온라인 설명서, 백서, 및 현재 공급자 도움말 항목의 온라인 버전을 비롯 하 여 온라인 항목에 대 한 참조를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="6ce9e-107">온라인 항목을 참조 하는 경우 URI 또는 일반 텍스트에서 검색어를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="6ce9e-108">`Get-Help` cmdlet에 연결 하지 않거나 목록의 항목 중 하나에 리디렉션합니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="6ce9e-109">또한 합니다 `Online` 의 매개 변수는 `Get-Help` 공급자 도움말을 사용 하 여 cmdlet이 작동 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="6ce9e-110">참고 항목 섹션에서 만든는 `RelatedLinks` 요소 및 포함 하는 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="6ce9e-111">다음 XML 태그를 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="6ce9e-112">"참조" 항목을 추가 하려면</span><span class="sxs-lookup"><span data-stu-id="6ce9e-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="6ce9e-113">에 *AssemblyName*help.xml.dll 파일 내 합니다 `providerHelp` 요소를 추가 `RelatedLinks` 요소.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="6ce9e-114">합니다 `RelatedLinks` 요소에는 마지막 요소 여야 합니다.는 `providerHelp` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="6ce9e-115">하나의 `RelatedLinks` 요소는 각 공급자 도움말 항목에 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="6ce9e-116">예:</span><span class="sxs-lookup"><span data-stu-id="6ce9e-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="6ce9e-117">각 항목에 대 합니다 **참고** 섹션 내는 `RelatedLinks` 요소를 추가 `navigationLink` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="6ce9e-118">그런 다음, 각 `navigationLink` 요소를 추가할 `linkText` 요소와 `uri` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="6ce9e-119">사용 하지 않는 경우는 `uri` 요소를 추가할 수 있습니다 빈 요소로 (\<uri / >).</span><span class="sxs-lookup"><span data-stu-id="6ce9e-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="6ce9e-120">예:</span><span class="sxs-lookup"><span data-stu-id="6ce9e-120">For example:</span></span>

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

3. <span data-ttu-id="6ce9e-121">이름을 입력 하 고 항목 간에 `linkText` 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="6ce9e-122">URI를 제공 하는 경우 입력 간에 `uri` 태그입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="6ce9e-123">현재 공급자 도움말 항목의 온라인 버전 간에 나타내려면는 `linkText` 태그, 형식 "온라인 버전:" 항목 이름 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="6ce9e-124">일반적으로 "온라인 버전:" 링크 참고 항목 목록에서 첫 번째 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="6ce9e-125">다음 예제에서는 세 가지 참고 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="6ce9e-126">첫 번째 현재 항목의 온라인 버전을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="6ce9e-127">두 번째 Windows PowerShell cmdlet 도움말 항목을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="6ce9e-128">세 번째 다른 온라인 항목을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="6ce9e-128">The third refers to another online topic.</span></span>

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
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```