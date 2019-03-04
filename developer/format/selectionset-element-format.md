---
title: SelectionSet 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861159"
---
# <a name="selectionset-element-format"></a><span data-ttu-id="ef55a-102">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ef55a-102">SelectionSet Element (Format)</span></span>

<span data-ttu-id="ef55a-103">집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-103">Defines a set of .NET objects that can be referenced by the name of the set.</span></span>

<span data-ttu-id="ef55a-104">구성 요소 (형식) SelectionSets 요소 (형식) SelectionSet 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ef55a-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef55a-105">구문</span><span class="sxs-lookup"><span data-stu-id="ef55a-105">Syntax</span></span>

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef55a-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ef55a-106">Attributes and Elements</span></span>

<span data-ttu-id="ef55a-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSet` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-107">The following sections describe the attributes, child elements, and the parent element of the `SelectionSet` element.</span></span> <span data-ttu-id="ef55a-108">각 선택 집합에는 이름이 있어야 합니다. 한 집합의.NET 개체를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-108">Each selection set must have a name, and it must specify the .NET objects of the set.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef55a-109">특성</span><span class="sxs-lookup"><span data-stu-id="ef55a-109">Attributes</span></span>

<span data-ttu-id="ef55a-110">없음</span><span class="sxs-lookup"><span data-stu-id="ef55a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef55a-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ef55a-111">Child Elements</span></span>

|<span data-ttu-id="ef55a-112">요소</span><span class="sxs-lookup"><span data-stu-id="ef55a-112">Element</span></span>|<span data-ttu-id="ef55a-113">설명</span><span class="sxs-lookup"><span data-stu-id="ef55a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef55a-114">SelectionSet (형식)의 name 요소</span><span class="sxs-lookup"><span data-stu-id="ef55a-114">Name Element for SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)|<span data-ttu-id="ef55a-115">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-115">Required element.</span></span><br /><br /> <span data-ttu-id="ef55a-116">선택 영역 집합을 참조 하는 데 사용 하는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-116">Specifies the name used to reference the selection set.</span></span>|
|[<span data-ttu-id="ef55a-117">형식 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ef55a-117">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="ef55a-118">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-118">Required element.</span></span><br /><br /> <span data-ttu-id="ef55a-119">선택 영역에 설정 된.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-119">Defines the .NET objects that are in the selection set.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef55a-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ef55a-120">Parent Elements</span></span>

|<span data-ttu-id="ef55a-121">요소</span><span class="sxs-lookup"><span data-stu-id="ef55a-121">Element</span></span>|<span data-ttu-id="ef55a-122">설명</span><span class="sxs-lookup"><span data-stu-id="ef55a-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef55a-123">SelectionSets 요소 형식</span><span class="sxs-lookup"><span data-stu-id="ef55a-123">SelectionSets Element Format</span></span>](./selectionsets-element-format.md)|<span data-ttu-id="ef55a-124">서식 파일의 모든 보기에서 사용할 수 있는.NET 개체의 공통 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-124">Defines the common sets of .NET objects that can be used by all views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef55a-125">설명</span><span class="sxs-lookup"><span data-stu-id="ef55a-125">Remarks</span></span>

<span data-ttu-id="ef55a-126">상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-126">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="ef55a-127">뷰를 정의할 때 각 보기 내에서 모든 개체를 나열 하는 대신 설정 선택 항목의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-127">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="ef55a-128">서식 파일의 뷰 또는 뷰의 정의 정의 하는 경우 일반적인 선택 집합 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-128">Common selection sets are specified by their name when defining the views of the formatting file or the definitions of the views.</span></span> <span data-ttu-id="ef55a-129">이러한 경우에는 `SelectionSetName` 자식 요소를 `ViewSelectedBy` 및 `EntrySelectedBy` 요소에 사용할 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-129">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` and `EntrySelectedBy` elements specifies the set to be used.</span></span> <span data-ttu-id="ef55a-130">선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-130">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ef55a-131">예제</span><span class="sxs-lookup"><span data-stu-id="ef55a-131">Example</span></span>

<span data-ttu-id="ef55a-132">다음 예제와 `SelectionSet` .NET 유형은 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ef55a-132">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef55a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef55a-133">See Also</span></span>

[<span data-ttu-id="ef55a-134">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="ef55a-134">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ef55a-135">SelectionSet (형식)의 name 요소</span><span class="sxs-lookup"><span data-stu-id="ef55a-135">Name Element of SelectionSet (Format)</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="ef55a-136">SelectionSets 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ef55a-136">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="ef55a-137">형식 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="ef55a-137">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="ef55a-138">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="ef55a-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
