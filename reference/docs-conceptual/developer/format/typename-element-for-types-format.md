---
title: 형식에 대 한 TypeName 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 40fad73c66124d6c3b0d969b4268713a492c963a
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772538"
---
# <a name="typename-element-for-types-format"></a><span data-ttu-id="477b2-102">Types에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="477b2-102">TypeName Element for Types (Format)</span></span>

<span data-ttu-id="477b2-103">선택 집합에 속하는 개체의 .NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-103">Specifies the .NET type of an object that belongs to the selection set.</span></span>

<span data-ttu-id="477b2-104">Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Types 요소 (format) TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="477b2-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Types Element (Format) TypeName Element of Types (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="477b2-105">구문</span><span class="sxs-lookup"><span data-stu-id="477b2-105">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="477b2-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="477b2-106">Attributes and Elements</span></span>

<span data-ttu-id="477b2-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="477b2-107">The following sections describe the attributes, child elements, and the parent element of the `TypeName` element.</span></span> <span data-ttu-id="477b2-108">하나 이상의 `TypeName` 요소가 선택 집합에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-108">At least one `TypeName` element must be included in the selection set.</span></span>

### <a name="attributes"></a><span data-ttu-id="477b2-109">특성</span><span class="sxs-lookup"><span data-stu-id="477b2-109">Attributes</span></span>

<span data-ttu-id="477b2-110">없음</span><span class="sxs-lookup"><span data-stu-id="477b2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="477b2-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="477b2-111">Child Elements</span></span>

<span data-ttu-id="477b2-112">없음</span><span class="sxs-lookup"><span data-stu-id="477b2-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="477b2-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="477b2-113">Parent Elements</span></span>

|<span data-ttu-id="477b2-114">요소</span><span class="sxs-lookup"><span data-stu-id="477b2-114">Element</span></span>|<span data-ttu-id="477b2-115">설명</span><span class="sxs-lookup"><span data-stu-id="477b2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="477b2-116">Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="477b2-116">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)|<span data-ttu-id="477b2-117">선택 집합에 있는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-117">Defines the .NET objects that are in the selection set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="477b2-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="477b2-118">Text Value</span></span>

<span data-ttu-id="477b2-119">.NET 형식의 정규화 된 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-119">Specify the fully qualified name for the .NET type.</span></span>

## <a name="remarks"></a><span data-ttu-id="477b2-120">설명</span><span class="sxs-lookup"><span data-stu-id="477b2-120">Remarks</span></span>

<span data-ttu-id="477b2-121">상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-121">You can use selection sets when you have a set of related objects that you want to reference by using a single name, such as a set of objects that are related through inheritance.</span></span> <span data-ttu-id="477b2-122">뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-122">When defining your views, you can specify the set of objects by using the name of the selection set instead of listing all the objects within each view.</span></span>

<span data-ttu-id="477b2-123">일반 선택 집합은 형식 지정 파일의 뷰를 정의할 때 이름으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-123">Common selection sets are specified by their name when defining the views of the formatting file.</span></span> <span data-ttu-id="477b2-124">이러한 경우 `SelectionSetName` 뷰에서 요소의 자식 요소는 집합을 `ViewSelectedBy` 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-124">In these cases, the `SelectionSetName` child element of the `ViewSelectedBy` element for the view specifies the set.</span></span> <span data-ttu-id="477b2-125">그러나 뷰의 다른 항목은 뷰의 해당 항목에만 적용 되는 선택 집합을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-125">However, different entries of a view can also specify a selection set that applies to only that entry of the view.</span></span> <span data-ttu-id="477b2-126">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="477b2-126">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="477b2-127">예제</span><span class="sxs-lookup"><span data-stu-id="477b2-127">Example</span></span>

<span data-ttu-id="477b2-128">다음 예제에서는 `SelectionSet` 네 가지 .net 형식을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="477b2-128">The following example shows a `SelectionSet` element that defines four .NET types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="477b2-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="477b2-129">See Also</span></span>

[<span data-ttu-id="477b2-130">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="477b2-130">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="477b2-131">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="477b2-131">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="477b2-132">SelectionSets 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="477b2-132">SelectionSets Element (Format)</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="477b2-133">Types 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="477b2-133">Types Element (Format)</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="477b2-134">Windows PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="477b2-134">Writing a Windows PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
