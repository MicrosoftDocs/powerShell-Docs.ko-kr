---
ms.date: 09/13/2016
ms.topic: reference
title: Types에 대한 TypeName 요소(형식)
description: Types에 대한 TypeName 요소(형식)
ms.openlocfilehash: c656b8e7e5877b72ff2164e5b417857273cada61
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664618"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="a84b2-103">Types에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a84b2-103">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="a84b2-104">선택 집합에 속하는 개체의 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-104">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="a84b2-105">Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Types 요소 (format) TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="a84b2-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a84b2-106">구문</span><span class="sxs-lookup"><span data-stu-id="a84b2-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a84b2-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a84b2-107">Attributes and Elements</span></span>

<span data-ttu-id="a84b2-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="a84b2-108">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="a84b2-109">하나 이상의 `TypeName` 요소가 선택 집합에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-109">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="a84b2-110">특성</span><span class="sxs-lookup"><span data-stu-id="a84b2-110">Attributes</span></span>

<span data-ttu-id="a84b2-111">없음</span><span class="sxs-lookup"><span data-stu-id="a84b2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a84b2-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a84b2-112">Child Elements</span></span>

<span data-ttu-id="a84b2-113">없음</span><span class="sxs-lookup"><span data-stu-id="a84b2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a84b2-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a84b2-114">Parent Elements</span></span>

|<span data-ttu-id="a84b2-115">요소</span><span class="sxs-lookup"><span data-stu-id="a84b2-115">Element</span></span>|<span data-ttu-id="a84b2-116">설명</span><span class="sxs-lookup"><span data-stu-id="a84b2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a84b2-117">Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a84b2-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="a84b2-118">선택 집합에 있는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-118">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a84b2-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="a84b2-119">Text Value</span></span>

<span data-ttu-id="a84b2-120">.NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-120">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="a84b2-121">설명</span><span class="sxs-lookup"><span data-stu-id="a84b2-121">Remarks</span></span>

<span data-ttu-id="a84b2-122">상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-122">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a84b2-123">뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-123">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="a84b2-124">일반 선택 집합은 형식 지정 파일의 뷰를 정의할 때 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-124">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="a84b2-125">이러한 경우 `SelectionSetName` 뷰에서 요소의 자식 요소는 집합을 `ViewSelectedBy` 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-125">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="a84b2-126">그러나 뷰의 다른 항목은 뷰의 해당 항목에만 적용 되는 선택 집합을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-126">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="a84b2-127">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a84b2-127">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="a84b2-128">예제</span><span class="sxs-lookup"><span data-stu-id="a84b2-128">Example</span></span>

<span data-ttu-id="a84b2-129">다음 예제에서는 `SelectionSet` 네 가지 .net 형식을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a84b2-129">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

```
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

## <a name="see-also"></a><span data-ttu-id="a84b2-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a84b2-130">See Also</span></span>

[<span data-ttu-id="a84b2-131">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="a84b2-131">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a84b2-132">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a84b2-132">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="a84b2-133">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a84b2-133">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="a84b2-134">Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a84b2-134">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="a84b2-135">Windows PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a84b2-135">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
