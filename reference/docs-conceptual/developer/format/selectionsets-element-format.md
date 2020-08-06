---
title: SelectionSets 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 718b08e02220f285ef215fdca727492fd4407466
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785203"
---
# <a name="selectionsets-element-format"></a><span data-ttu-id="a79f2-102">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a79f2-102">SelectionSets Element (Format)</span></span>

<span data-ttu-id="a79f2-103">서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-103">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span> <span data-ttu-id="a79f2-104">서식 파일의 뷰 및 컨트롤은 선택 집합의 이름만 사용 하 여 개체의 전체 집합을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-104">The views and controls of the formatting file can reference the complete set of objects by using only the name of the selection set.</span></span>

<span data-ttu-id="a79f2-105">구성 요소 SelectionSets 요소 형식</span><span class="sxs-lookup"><span data-stu-id="a79f2-105">Configuration Element SelectionSets Element Format</span></span>

## <a name="syntax"></a><span data-ttu-id="a79f2-106">구문</span><span class="sxs-lookup"><span data-stu-id="a79f2-106">Syntax</span></span>

```xml
<SelectionSets>
  <SelectionSet>...</SelectionSet>
</SelectionSets>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a79f2-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a79f2-107">Attributes and Elements</span></span>

<span data-ttu-id="a79f2-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSets` .</span><span class="sxs-lookup"><span data-stu-id="a79f2-108">The following sections describe the attributes, child elements, and parent element of the `SelectionSets` element.</span></span> <span data-ttu-id="a79f2-109">각 자식 요소는 집합의 이름으로 참조할 수 있는 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-109">Each child element defines a set of objects that can be referenced by the name of the set.</span></span> <span data-ttu-id="a79f2-110">자식 요소의 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-110">The order of the child elements is not significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="a79f2-111">특성</span><span class="sxs-lookup"><span data-stu-id="a79f2-111">Attributes</span></span>

<span data-ttu-id="a79f2-112">없음</span><span class="sxs-lookup"><span data-stu-id="a79f2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a79f2-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a79f2-113">Child Elements</span></span>

|<span data-ttu-id="a79f2-114">요소</span><span class="sxs-lookup"><span data-stu-id="a79f2-114">Element</span></span>|<span data-ttu-id="a79f2-115">설명</span><span class="sxs-lookup"><span data-stu-id="a79f2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a79f2-116">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a79f2-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="a79f2-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-117">Required element.</span></span><br /><br /> <span data-ttu-id="a79f2-118">집합의 이름으로 참조할 수 있는 단일 .NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-118">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a79f2-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a79f2-119">Parent Elements</span></span>

|<span data-ttu-id="a79f2-120">요소</span><span class="sxs-lookup"><span data-stu-id="a79f2-120">Element</span></span>|<span data-ttu-id="a79f2-121">설명</span><span class="sxs-lookup"><span data-stu-id="a79f2-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a79f2-122">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a79f2-122">Configuration Element</span></span>](./configuration-element-format.md)|<span data-ttu-id="a79f2-123">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-123">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a79f2-124">설명</span><span class="sxs-lookup"><span data-stu-id="a79f2-124">Remarks</span></span>

<span data-ttu-id="a79f2-125">상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-125">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a79f2-126">뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-126">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="a79f2-127">일반 선택 집합은 형식 지정 파일의 뷰나 뷰의 정의를 정의할 때 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-127">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="a79f2-128">이러한 경우 `SelectionSetName` 및 요소의 자식 요소는 `ViewSelectedBy` `EntrySelectedBy` 사용할 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a79f2-128">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="a79f2-129">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a79f2-129">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a79f2-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a79f2-130">See Also</span></span>

[<span data-ttu-id="a79f2-131">구성 요소</span><span class="sxs-lookup"><span data-stu-id="a79f2-131">Configuration Element</span></span>](./configuration-element-format.md)

[<span data-ttu-id="a79f2-132">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="a79f2-132">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a79f2-133">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a79f2-133">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a79f2-134">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a79f2-134">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
