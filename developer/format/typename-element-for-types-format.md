---
title: TypeName 요소 형식 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: 4f463ac6b70a00f628c5b93b112c5fa510ff3bfb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853579"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="901ed-102">Types에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="901ed-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="901ed-103">선택 영역 집합에 속한 개체의.NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="901ed-104">구성 요소 (형식) SelectionSets 요소 (형식) SelectionSet 요소 (형식) 형식은 (형식) TypeName 요소 형식 (형식)</span><span class="sxs-lookup"><span data-stu-id="901ed-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="901ed-105">구문</span><span class="sxs-lookup"><span data-stu-id="901ed-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="901ed-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="901ed-106">Attributes and Elements</span></span>

<span data-ttu-id="901ed-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="901ed-108">하나 이상의 `TypeName` 요소 선택 집합에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="901ed-109">특성</span><span class="sxs-lookup"><span data-stu-id="901ed-109">Attributes</span></span>

<span data-ttu-id="901ed-110">없음</span><span class="sxs-lookup"><span data-stu-id="901ed-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="901ed-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="901ed-111">Child Elements</span></span>

<span data-ttu-id="901ed-112">없음</span><span class="sxs-lookup"><span data-stu-id="901ed-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="901ed-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="901ed-113">Parent Elements</span></span>

|<span data-ttu-id="901ed-114">요소</span><span class="sxs-lookup"><span data-stu-id="901ed-114">Element</span></span>|<span data-ttu-id="901ed-115">설명</span><span class="sxs-lookup"><span data-stu-id="901ed-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="901ed-116">형식 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="901ed-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="901ed-117">선택 영역에 설정 된.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="901ed-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="901ed-118">Text Value</span></span>

<span data-ttu-id="901ed-119">.NET 형식에 대 한 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="901ed-120">설명</span><span class="sxs-lookup"><span data-stu-id="901ed-120">Remarks</span></span>

<span data-ttu-id="901ed-121">상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="901ed-122">뷰를 정의할 때 각 보기 내에서 모든 개체를 나열 하는 대신 설정 선택 항목의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="901ed-123">서식 파일의 뷰를 정의 하는 경우 일반적인 선택 집합 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="901ed-124">이러한 경우에는 `SelectionSetName` 자식 요소는 `ViewSelectedBy` 뷰에 대 한 요소 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="901ed-125">그러나 뷰의 다른 항목 보기의 해당 항목에만 적용 되는 선택 집합을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="901ed-126">선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="901ed-127">예제</span><span class="sxs-lookup"><span data-stu-id="901ed-127">Example</span></span>

<span data-ttu-id="901ed-128">다음 예제와 `SelectionSet` .NET 유형은 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="901ed-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="901ed-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="901ed-129">See Also</span></span>

[<span data-ttu-id="901ed-130">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="901ed-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="901ed-131">SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="901ed-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="901ed-132">SelectionSets 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="901ed-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="901ed-133">형식 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="901ed-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="901ed-134">Windows PowDefining 집합으로 ObjecterShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="901ed-134">Writing a Windows PowDefining Sets of ObjecterShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
