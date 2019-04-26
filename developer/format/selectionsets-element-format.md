---
title: SelectionSets 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebbac73a-1c99-4388-9f47-703cd024dc6d
caps.latest.revision: 18
ms.openlocfilehash: a9356635d60d5f8c5d4dec4ec8b7d0aea2b037dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063779"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="1e4ed-102">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1e4ed-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="1e4ed-103">서식 파일의 모든 보기에서 사용할 수 있는.NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="1e4ed-104">뷰 및 서식 파일의 컨트롤을 선택 세트의 이름만 사용 하 여 개체의 전체 집합을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="1e4ed-105">구성 요소 SelectionSets 요소 형식</span><span class="sxs-lookup"><span data-stu-id="1e4ed-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="1e4ed-106">구문</span><span class="sxs-lookup"><span data-stu-id="1e4ed-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e4ed-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1e4ed-107">Attributes and Elements</span></span>

<span data-ttu-id="1e4ed-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSets` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="1e4ed-109">각 자식 요소 집합의 이름으로 참조할 수 있는 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="1e4ed-110">자식 요소의 순서가 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e4ed-111">특성</span><span class="sxs-lookup"><span data-stu-id="1e4ed-111">Attributes</span></span>

<span data-ttu-id="1e4ed-112">없음</span><span class="sxs-lookup"><span data-stu-id="1e4ed-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e4ed-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1e4ed-113">Child Elements</span></span>

|<span data-ttu-id="1e4ed-114">요소</span><span class="sxs-lookup"><span data-stu-id="1e4ed-114">Element</span></span>|<span data-ttu-id="1e4ed-115">설명</span><span class="sxs-lookup"><span data-stu-id="1e4ed-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e4ed-116">SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1e4ed-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="1e4ed-117">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-117">Required element.</span></span><br /><br /> <span data-ttu-id="1e4ed-118">단일 집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1e4ed-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1e4ed-119">Parent Elements</span></span>

|<span data-ttu-id="1e4ed-120">요소</span><span class="sxs-lookup"><span data-stu-id="1e4ed-120">Element</span></span>|<span data-ttu-id="1e4ed-121">설명</span><span class="sxs-lookup"><span data-stu-id="1e4ed-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e4ed-122">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1e4ed-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="1e4ed-123">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1e4ed-124">설명</span><span class="sxs-lookup"><span data-stu-id="1e4ed-124">Remarks</span></span>

<span data-ttu-id="1e4ed-125">상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="1e4ed-126">뷰를 정의할 때 각 보기 내에서 모든 개체를 나열 하는 대신 설정 선택 항목의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="1e4ed-127">서식 파일의 뷰 또는 뷰의 정의 정의 하는 경우 일반적인 선택 집합 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="1e4ed-128">이러한 경우에는 `SelectionSetName` 자식 요소를 `ViewSelectedBy` 및 `EntrySelectedBy` 요소에 사용할 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="1e4ed-129">선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1e4ed-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e4ed-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e4ed-130">See Also</span></span>

[<span data-ttu-id="1e4ed-131">구성 요소</span><span class="sxs-lookup"><span data-stu-id="1e4ed-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="1e4ed-132">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="1e4ed-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="1e4ed-133">SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1e4ed-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="1e4ed-134">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1e4ed-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
