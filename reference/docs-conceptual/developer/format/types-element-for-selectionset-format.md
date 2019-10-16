---
title: SelectionSet (Format)의 Types 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367962"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="a1852-102">SelectionSet에 대한 Types 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a1852-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="a1852-103">선택 집합에 있는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="a1852-104">Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a1852-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a1852-105">구문</span><span class="sxs-lookup"><span data-stu-id="a1852-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a1852-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a1852-106">Attributes and Elements</span></span>

<span data-ttu-id="a1852-107">다음 섹션에서는 `Types` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="a1852-108">자식 요소가 하나 이상 있어야 하지만 추가할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="a1852-109">특성</span><span class="sxs-lookup"><span data-stu-id="a1852-109">Attributes</span></span>

<span data-ttu-id="a1852-110">없음</span><span class="sxs-lookup"><span data-stu-id="a1852-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a1852-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a1852-111">Child Elements</span></span>

|<span data-ttu-id="a1852-112">요소</span><span class="sxs-lookup"><span data-stu-id="a1852-112">Element</span></span>|<span data-ttu-id="a1852-113">설명</span><span class="sxs-lookup"><span data-stu-id="a1852-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1852-114">형식의 TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a1852-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="a1852-115">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-115">Required element.</span></span><br /><br /> <span data-ttu-id="a1852-116">선택 집합에 속하는 .NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a1852-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a1852-117">Parent Elements</span></span>

|<span data-ttu-id="a1852-118">요소</span><span class="sxs-lookup"><span data-stu-id="a1852-118">Element</span></span>|<span data-ttu-id="a1852-119">설명</span><span class="sxs-lookup"><span data-stu-id="a1852-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a1852-120">SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a1852-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="a1852-121">집합의 이름으로 참조할 수 있는 .NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a1852-122">설명</span><span class="sxs-lookup"><span data-stu-id="a1852-122">Remarks</span></span>

<span data-ttu-id="a1852-123">이 요소에 의해 정의 되는 개체는 뷰에서 사용할 수 있는 선택 집합을 구성 합니다. 뷰 정의를 통해 뷰가 여러 정의를 가질 수 있습니다. 또는 선택 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="a1852-124">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a1852-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="a1852-125">예제</span><span class="sxs-lookup"><span data-stu-id="a1852-125">Example</span></span>

<span data-ttu-id="a1852-126">이 예제에서는 네 가지 .NET 형식을 정의 하는 `SelectionSet` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a1852-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a1852-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1852-127">See Also</span></span>

[<span data-ttu-id="a1852-128">개체 집합 정의</span><span class="sxs-lookup"><span data-stu-id="a1852-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a1852-129">SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a1852-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a1852-130">형식의 TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a1852-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="a1852-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a1852-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
