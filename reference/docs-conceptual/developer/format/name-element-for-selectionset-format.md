---
title: SelectionSet (Format)의 Name 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1fc33eeb87a6912ed6793629ab1969cd65b5f0c5
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773303"
---
# <a name="name-element-for-selectionset-format"></a><span data-ttu-id="cb62c-102">SelectionSet에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cb62c-102">Name Element for SelectionSet (Format)</span></span>

<span data-ttu-id="cb62c-103">선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb62c-103">Specifies the name used to reference the selection set.</span></span>

<span data-ttu-id="cb62c-104">Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Name 요소 Selectionsets (Format)</span><span class="sxs-lookup"><span data-stu-id="cb62c-104">Configuration Element (Format) SelectionSets Element (Format) SelectionSet Element (Format) Name Element of SelectionSet (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cb62c-105">구문</span><span class="sxs-lookup"><span data-stu-id="cb62c-105">Syntax</span></span>

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cb62c-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cb62c-106">Attributes and Elements</span></span>

<span data-ttu-id="cb62c-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="cb62c-107">The following sections describe the attributes, child elements, and parent element of the `Name` Element.</span></span>

### <a name="attributes"></a><span data-ttu-id="cb62c-108">특성</span><span class="sxs-lookup"><span data-stu-id="cb62c-108">Attributes</span></span>

<span data-ttu-id="cb62c-109">없음</span><span class="sxs-lookup"><span data-stu-id="cb62c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cb62c-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cb62c-110">Child Elements</span></span>

<span data-ttu-id="cb62c-111">없음</span><span class="sxs-lookup"><span data-stu-id="cb62c-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="cb62c-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cb62c-112">Parent Elements</span></span>

|<span data-ttu-id="cb62c-113">요소</span><span class="sxs-lookup"><span data-stu-id="cb62c-113">Element</span></span>|<span data-ttu-id="cb62c-114">설명</span><span class="sxs-lookup"><span data-stu-id="cb62c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cb62c-115">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cb62c-115">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)|<span data-ttu-id="cb62c-116">집합의 이름으로 참조할 수 있는 단일 .NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb62c-116">Defines a single set of .NET objects that can be referenced by the name of the set.</span></span>|

## <a name="text-value"></a><span data-ttu-id="cb62c-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="cb62c-117">Text Value</span></span>

<span data-ttu-id="cb62c-118">선택 집합을 참조 하는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb62c-118">Specify the name to reference the selection set.</span></span> <span data-ttu-id="cb62c-119">사용할 수 있는 문자에 대 한 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb62c-119">There are no restrictions as to what characters can be used.</span></span>

## <a name="remarks"></a><span data-ttu-id="cb62c-120">설명</span><span class="sxs-lookup"><span data-stu-id="cb62c-120">Remarks</span></span>

<span data-ttu-id="cb62c-121">여기에 지정 된 이름은 요소에 사용 됩니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="cb62c-121">The name specified here is used in the `SelectionSetName` element.</span></span> <span data-ttu-id="cb62c-122">뷰에서 사용할 수 있는 선택 집합으로, 보기의 정의에 의해 (보기에 여러 정의가 있을 수 있음) 또는 선택 조건을 지정할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb62c-122">The selection set that can be used by a view, by a definition of a view (views can have multiple definitions), or when specifying a selection condition.</span></span> <span data-ttu-id="cb62c-123">선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cb62c-123">For more information about selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="cb62c-124">예제</span><span class="sxs-lookup"><span data-stu-id="cb62c-124">Example</span></span>

<span data-ttu-id="cb62c-125">이 예제에서는 `SelectionSet` 네 가지 .net 형식을 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cb62c-125">This example shows a `SelectionSet` element that defines four .NET types.</span></span> <span data-ttu-id="cb62c-126">선택 집합의 이름은 "FileSystemTypes"입니다.</span><span class="sxs-lookup"><span data-stu-id="cb62c-126">The name of the selection set is "FileSystemTypes".</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cb62c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb62c-127">See Also</span></span>

[<span data-ttu-id="cb62c-128">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="cb62c-128">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="cb62c-129">SelectionSet 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cb62c-129">SelectionSet Element (Format)</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="cb62c-130">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="cb62c-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
