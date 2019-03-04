---
title: SelectionSet (형식)에 대 한 요소 형식 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862379"
---
# <a name="types-element-for-selectionset-format"></a><span data-ttu-id="4e142-102">SelectionSet에 대한 Types 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4e142-102">Types Element for SelectionSet (Format)</span></span>

<span data-ttu-id="4e142-103">선택 영역에 설정 된.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-103">Defines the .NET objects that are in the selection set.</span></span>

<span data-ttu-id="4e142-104">구성 요소 (형식) SelectionSets 요소 (형식) SelectionSet 요소 (형식) 형식 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4e142-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e142-105">구문</span><span class="sxs-lookup"><span data-stu-id="4e142-105">Syntax</span></span>

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e142-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4e142-106">Attributes and Elements</span></span>

<span data-ttu-id="4e142-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Types` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-107">The following sections describe the attributes, child elements, and the parent element of the `Types` element.</span></span> <span data-ttu-id="4e142-108">하나 이상의 자식 요소가 있어야 하지만 추가할 수 있는 자식 요소의 수를 최대 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-108">There must be at least one child element, but there is no maximum limit to the number of child elements that can be added.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e142-109">특성</span><span class="sxs-lookup"><span data-stu-id="4e142-109">Attributes</span></span>

<span data-ttu-id="4e142-110">없음</span><span class="sxs-lookup"><span data-stu-id="4e142-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e142-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4e142-111">Child Elements</span></span>

|<span data-ttu-id="4e142-112">요소</span><span class="sxs-lookup"><span data-stu-id="4e142-112">Element</span></span>|<span data-ttu-id="4e142-113">설명</span><span class="sxs-lookup"><span data-stu-id="4e142-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e142-114">TypeName 요소의 형식 (형식)</span><span class="sxs-lookup"><span data-stu-id="4e142-114">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)|<span data-ttu-id="4e142-115">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-115">Required element.</span></span><br /><br /> <span data-ttu-id="4e142-116">선택 영역 집합에 속해 있는.NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-116">Specifies the .NET object that belongs to the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e142-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4e142-117">Parent Elements</span></span>

|<span data-ttu-id="4e142-118">요소</span><span class="sxs-lookup"><span data-stu-id="4e142-118">Element</span></span>|<span data-ttu-id="4e142-119">설명</span><span class="sxs-lookup"><span data-stu-id="4e142-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e142-120">SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4e142-120">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="4e142-121">집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-121">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e142-122">설명</span><span class="sxs-lookup"><span data-stu-id="4e142-122">Remarks</span></span>

<span data-ttu-id="4e142-123">이 요소에 의해 정의 된 개체 뷰의 정의 의해 뷰를 사용할 수 있는 선택 집합 구성 (뷰 정의가 여러 개 있을 수 있음)를 선택 조건을 지정할 때 또는 합니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-123">The objects defined by this element make up a selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span>  <span data-ttu-id="4e142-124">선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e142-125">예제</span><span class="sxs-lookup"><span data-stu-id="4e142-125">Example</span></span>

<span data-ttu-id="4e142-126">이 예제에서는 `SelectionSet` .NET 유형은 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4e142-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4e142-127">See Also</span></span>

[<span data-ttu-id="4e142-128">개체 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4e142-128">Defining Sets of Objects</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="4e142-129">SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="4e142-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="4e142-130">TypeName 요소의 형식 (형식)</span><span class="sxs-lookup"><span data-stu-id="4e142-130">TypeName Element of Types (Format)</span></span>](./typename-element-for-types-format.md)

[<span data-ttu-id="4e142-131">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="4e142-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
