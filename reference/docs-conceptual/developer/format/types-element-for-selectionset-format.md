---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet에 대한 Types 요소(형식)
description: SelectionSet에 대한 Types 요소(형식)
ms.openlocfilehash: ff3c24e7f52f862dc416b88d50983196ce907012
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645458"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="bc0f0-103">SelectionSet에 대한 Types 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="bc0f0-103">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="bc0f0-104">선택 집합에 있는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-104">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="bc0f0-105">Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="bc0f0-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc0f0-106">구문</span><span class="sxs-lookup"><span data-stu-id="bc0f0-106">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc0f0-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="bc0f0-107">Attributes and Elements</span></span>

<span data-ttu-id="bc0f0-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Types` .</span><span class="sxs-lookup"><span data-stu-id="bc0f0-108">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="bc0f0-109">자식 요소가 하나 이상 있어야 하지만 추가할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-109">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc0f0-110">특성</span><span class="sxs-lookup"><span data-stu-id="bc0f0-110">Attributes</span></span>

<span data-ttu-id="bc0f0-111">없음</span><span class="sxs-lookup"><span data-stu-id="bc0f0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc0f0-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="bc0f0-112">Child Elements</span></span>

|<span data-ttu-id="bc0f0-113">요소</span><span class="sxs-lookup"><span data-stu-id="bc0f0-113">Element</span></span>|<span data-ttu-id="bc0f0-114">설명</span><span class="sxs-lookup"><span data-stu-id="bc0f0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc0f0-115">형식의 TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="bc0f0-115">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="bc0f0-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-116">Required element.</span></span><br /><br /> <span data-ttu-id="bc0f0-117">선택 집합에 속하는 .NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-117">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc0f0-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="bc0f0-118">Parent Elements</span></span>

|<span data-ttu-id="bc0f0-119">요소</span><span class="sxs-lookup"><span data-stu-id="bc0f0-119">Element</span></span>|<span data-ttu-id="bc0f0-120">설명</span><span class="sxs-lookup"><span data-stu-id="bc0f0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc0f0-121">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="bc0f0-121">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="bc0f0-122">집합의 이름으로 참조할 수 있는 .NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-122">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc0f0-123">설명</span><span class="sxs-lookup"><span data-stu-id="bc0f0-123">Remarks</span></span>

<span data-ttu-id="bc0f0-124">이 요소에 의해 정의 되는 개체는 뷰에서 사용할 수 있는 선택 집합을 구성 합니다. 뷰 정의를 통해 뷰가 여러 정의를 가질 수 있습니다. 또는 선택 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-124">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="bc0f0-125">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-125">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="bc0f0-126">예제</span><span class="sxs-lookup"><span data-stu-id="bc0f0-126">Example</span></span>

<span data-ttu-id="bc0f0-127">이 예제에서는 `SelectionSet` 네 가지 .net 형식을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bc0f0-127">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

## <a name="see-also"></a><span data-ttu-id="bc0f0-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc0f0-128">See Also</span></span>

[<span data-ttu-id="bc0f0-129">개체 집합 정의</span><span class="sxs-lookup"><span data-stu-id="bc0f0-129">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="bc0f0-130">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="bc0f0-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="bc0f0-131">형식의 TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="bc0f0-131">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="bc0f0-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="bc0f0-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
