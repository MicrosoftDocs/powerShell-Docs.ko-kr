---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet 요소(형식)
description: SelectionSet 요소(형식)
ms.openlocfilehash: 944aa83569ad8ca789746a71f60e5da5c19fbf01
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647872"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="a7066-103">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a7066-103">SelectionSet Element (Format)</span></span>

<span data-ttu-id="a7066-104">집합의 이름으로 참조할 수 있는 .NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-104">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="a7066-105">Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a7066-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a7066-106">구문</span><span class="sxs-lookup"><span data-stu-id="a7066-106">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a7066-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a7066-107">Attributes and Elements</span></span>

<span data-ttu-id="a7066-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `SelectionSet` .</span><span class="sxs-lookup"><span data-stu-id="a7066-108">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="a7066-109">각 선택 집합에는 이름이 있어야 하며 집합의 .NET 개체를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-109">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7066-110">특성</span><span class="sxs-lookup"><span data-stu-id="a7066-110">Attributes</span></span>

<span data-ttu-id="a7066-111">없음</span><span class="sxs-lookup"><span data-stu-id="a7066-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a7066-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a7066-112">Child Elements</span></span>

|<span data-ttu-id="a7066-113">요소</span><span class="sxs-lookup"><span data-stu-id="a7066-113">Element</span></span>|<span data-ttu-id="a7066-114">설명</span><span class="sxs-lookup"><span data-stu-id="a7066-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7066-115">SelectionSet에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a7066-115">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="a7066-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-116">Required element.</span></span><br /><br /> <span data-ttu-id="a7066-117">선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-117">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="a7066-118">Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a7066-118">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="a7066-119">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-119">Required element.</span></span><br /><br /> <span data-ttu-id="a7066-120">선택 집합에 있는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-120">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a7066-121">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a7066-121">Parent Elements</span></span>

|<span data-ttu-id="a7066-122">요소</span><span class="sxs-lookup"><span data-stu-id="a7066-122">Element</span></span>|<span data-ttu-id="a7066-123">설명</span><span class="sxs-lookup"><span data-stu-id="a7066-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7066-124">SelectionSets 형식 설정</span><span class="sxs-lookup"><span data-stu-id="a7066-124">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="a7066-125">서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-125">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a7066-126">설명</span><span class="sxs-lookup"><span data-stu-id="a7066-126">Remarks</span></span>

<span data-ttu-id="a7066-127">상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-127">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="a7066-128">뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-128">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="a7066-129">일반 선택 집합은 형식 지정 파일의 뷰나 뷰의 정의를 정의할 때 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-129">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="a7066-130">이러한 경우 `SelectionSetName` 및 요소의 자식 요소는 `ViewSelectedBy` `EntrySelectedBy` 사용할 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-130">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="a7066-131">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7066-131">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="a7066-132">예제</span><span class="sxs-lookup"><span data-stu-id="a7066-132">Example</span></span>

<span data-ttu-id="a7066-133">다음 예제에서는 `SelectionSet` 네 가지 .net 형식을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a7066-133">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a7066-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7066-134">See Also</span></span>

[<span data-ttu-id="a7066-135">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="a7066-135">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="a7066-136">SelectionSet의 Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a7066-136">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="a7066-137">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a7066-137">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="a7066-138">Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a7066-138">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="a7066-139">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a7066-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
