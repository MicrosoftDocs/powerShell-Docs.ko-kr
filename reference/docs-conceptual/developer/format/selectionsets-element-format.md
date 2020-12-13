---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSets 요소(형식)
description: SelectionSets 요소(형식)
ms.openlocfilehash: e5c928dfb82bc6963b4a87aef9ec06d34cacfdcb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92654925"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="a2031-103">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a2031-103">SelectionSets Element (Format)</span></span>

<span data-ttu-id="a2031-104">서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-104">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="a2031-105">서식 파일의 뷰 및 컨트롤은 선택 집합의 이름만 사용 하 여 개체의 전체 집합을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-105">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="a2031-106">구성 요소 SelectionSets 요소 형식</span><span class="sxs-lookup"><span data-stu-id="a2031-106">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="a2031-107">구문</span><span class="sxs-lookup"><span data-stu-id="a2031-107">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a2031-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a2031-108">Attributes and Elements</span></span>

<span data-ttu-id="a2031-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSets` .</span><span class="sxs-lookup"><span data-stu-id="a2031-109">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="a2031-110">각 자식 요소는 집합의 이름으로 참조할 수 있는 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-110">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="a2031-111">자식 요소의 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-111">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="a2031-112">특성</span><span class="sxs-lookup"><span data-stu-id="a2031-112">Attributes</span></span>

<span data-ttu-id="a2031-113">없음</span><span class="sxs-lookup"><span data-stu-id="a2031-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a2031-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a2031-114">Child Elements</span></span>

|<span data-ttu-id="a2031-115">요소</span><span class="sxs-lookup"><span data-stu-id="a2031-115">Element</span></span>|<span data-ttu-id="a2031-116">설명</span><span class="sxs-lookup"><span data-stu-id="a2031-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2031-117">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a2031-117">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="a2031-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-118">Required element.</span></span><br /><br /> <span data-ttu-id="a2031-119">집합의 이름으로 참조할 수 있는 단일 .NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-119">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a2031-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a2031-120">Parent Elements</span></span>

|<span data-ttu-id="a2031-121">요소</span><span class="sxs-lookup"><span data-stu-id="a2031-121">Element</span></span>|<span data-ttu-id="a2031-122">설명</span><span class="sxs-lookup"><span data-stu-id="a2031-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a2031-123">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a2031-123">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="a2031-124">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-124">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a2031-125">설명</span><span class="sxs-lookup"><span data-stu-id="a2031-125">Remarks</span></span>

<span data-ttu-id="a2031-126">상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a2031-127">뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="a2031-128">일반 선택 집합은 형식 지정 파일의 뷰나 뷰의 정의를 정의할 때 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="a2031-129">이러한 경우 `SelectionSetName` 및 요소의 자식 요소는 `ViewSelectedBy` `EntrySelectedBy` 사용할 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a2031-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="a2031-130">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a2031-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2031-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a2031-131">See Also</span></span>

[<span data-ttu-id="a2031-132">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a2031-132">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a2031-133">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="a2031-133">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a2031-134">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a2031-134">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a2031-135">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a2031-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
