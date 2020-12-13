---
ms.date: 09/13/2016
ms.topic: reference
title: Expand 요소(형식)
description: Expand 요소(형식)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667949"
---
# <a name="expand-element-format"></a><span data-ttu-id="31cbf-103">Expand 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31cbf-103">Expand Element (Format)</span></span>

<span data-ttu-id="31cbf-104">이 정의에 대해 컬렉션 개체를 확장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-104">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="31cbf-105">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (format) Enumerableexpansions 요소 (format) Expand 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="31cbf-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="31cbf-106">구문</span><span class="sxs-lookup"><span data-stu-id="31cbf-106">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="31cbf-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="31cbf-107">Attributes and Elements</span></span>

<span data-ttu-id="31cbf-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Expand` .</span><span class="sxs-lookup"><span data-stu-id="31cbf-108">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="31cbf-109">특성</span><span class="sxs-lookup"><span data-stu-id="31cbf-109">Attributes</span></span>

<span data-ttu-id="31cbf-110">없음</span><span class="sxs-lookup"><span data-stu-id="31cbf-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="31cbf-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="31cbf-111">Child Elements</span></span>

<span data-ttu-id="31cbf-112">없음</span><span class="sxs-lookup"><span data-stu-id="31cbf-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="31cbf-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="31cbf-113">Parent Elements</span></span>

|<span data-ttu-id="31cbf-114">요소</span><span class="sxs-lookup"><span data-stu-id="31cbf-114">Element</span></span>|<span data-ttu-id="31cbf-115">설명</span><span class="sxs-lookup"><span data-stu-id="31cbf-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="31cbf-116">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="31cbf-116">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="31cbf-117">특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-117">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="31cbf-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="31cbf-118">Text Value</span></span>

<span data-ttu-id="31cbf-119">다음 값 중 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-119">Specify one of the following values:</span></span>

- <span data-ttu-id="31cbf-120">EnumOnly: 컬렉션에 있는 개체의 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-120">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="31cbf-121">CoreOnly: 컬렉션 개체의 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-121">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="31cbf-122">Both: 컬렉션의 개체 속성 및 컬렉션 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-122">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="31cbf-123">설명</span><span class="sxs-lookup"><span data-stu-id="31cbf-123">Remarks</span></span>

<span data-ttu-id="31cbf-124">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="31cbf-125">이 경우 컬렉션 개체는  **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="31cbf-126">기본 동작은 컬렉션에 있는 개체의 속성만 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="31cbf-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="31cbf-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31cbf-127">See Also</span></span>

[<span data-ttu-id="31cbf-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="31cbf-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
