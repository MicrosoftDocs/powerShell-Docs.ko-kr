---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSet에 대한 Name 요소(형식)
description: SelectionSet에 대한 Name 요소(형식)
ms.openlocfilehash: 98c13be6ea352055231fbdb3a60f0eb508f661b8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666464"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="2cdf1-103">SelectionSet에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cdf1-103">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="2cdf1-104">선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-104">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="2cdf1-105">Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Name 요소 Selectionsets (Format)</span><span class="sxs-lookup"><span data-stu-id="2cdf1-105">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2cdf1-106">구문</span><span class="sxs-lookup"><span data-stu-id="2cdf1-106">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2cdf1-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="2cdf1-107">Attributes and Elements</span></span>

<span data-ttu-id="2cdf1-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="2cdf1-108">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2cdf1-109">특성</span><span class="sxs-lookup"><span data-stu-id="2cdf1-109">Attributes</span></span>

<span data-ttu-id="2cdf1-110">없음</span><span class="sxs-lookup"><span data-stu-id="2cdf1-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2cdf1-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="2cdf1-111">Child Elements</span></span>

<span data-ttu-id="2cdf1-112">없음</span><span class="sxs-lookup"><span data-stu-id="2cdf1-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2cdf1-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="2cdf1-113">Parent Elements</span></span>

|<span data-ttu-id="2cdf1-114">요소</span><span class="sxs-lookup"><span data-stu-id="2cdf1-114">Element</span></span>|<span data-ttu-id="2cdf1-115">설명</span><span class="sxs-lookup"><span data-stu-id="2cdf1-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2cdf1-116">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cdf1-116">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="2cdf1-117">집합의 이름으로 참조할 수 있는 단일 .NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-117">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2cdf1-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="2cdf1-118">Text Value</span></span>

<span data-ttu-id="2cdf1-119">선택 집합을 참조 하는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-119">Specify the name to reference the selection set.</span></span> <span data-ttu-id="2cdf1-120">사용할 수 있는 문자에 대 한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-120">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="2cdf1-121">설명</span><span class="sxs-lookup"><span data-stu-id="2cdf1-121">Remarks</span></span>

<span data-ttu-id="2cdf1-122">여기에 지정 된 이름은 요소에 사용 됩니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="2cdf1-122">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="2cdf1-123">뷰에서 사용할 수 있는 선택 집합으로, 보기의 정의에 의해 (보기에 여러 정의가 있을 수 있음) 또는 선택 조건을 지정할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-123">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="2cdf1-124">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-124">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="2cdf1-125">예제</span><span class="sxs-lookup"><span data-stu-id="2cdf1-125">Example</span></span>

<span data-ttu-id="2cdf1-126">이 예제에서는 `SelectionSet` 네 가지 .net 형식을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-126">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="2cdf1-127">선택 집합의 이름은 "FileSystemTypes"입니다.</span><span class="sxs-lookup"><span data-stu-id="2cdf1-127">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2cdf1-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2cdf1-128">See Also</span></span>

[<span data-ttu-id="2cdf1-129">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="2cdf1-129">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2cdf1-130">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="2cdf1-130">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="2cdf1-131">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="2cdf1-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
