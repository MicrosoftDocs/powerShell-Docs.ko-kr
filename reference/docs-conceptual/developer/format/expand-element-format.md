---
title: Expand 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368742"
---
# <a name="expand-element-format"></a><span data-ttu-id="554d6-102">Expand 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="554d6-102">Expand Element (Format)</span></span>

<span data-ttu-id="554d6-103">이 정의에 대해 컬렉션 개체를 확장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="554d6-104">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (format) Enumerableexpansions 요소 (format) Expand 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="554d6-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="554d6-105">구문</span><span class="sxs-lookup"><span data-stu-id="554d6-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="554d6-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="554d6-106">Attributes and Elements</span></span>

<span data-ttu-id="554d6-107">다음 섹션에서는 `Expand` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="554d6-108">특성</span><span class="sxs-lookup"><span data-stu-id="554d6-108">Attributes</span></span>

<span data-ttu-id="554d6-109">없음</span><span class="sxs-lookup"><span data-stu-id="554d6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="554d6-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="554d6-110">Child Elements</span></span>

<span data-ttu-id="554d6-111">없음</span><span class="sxs-lookup"><span data-stu-id="554d6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="554d6-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="554d6-112">Parent Elements</span></span>

|<span data-ttu-id="554d6-113">요소</span><span class="sxs-lookup"><span data-stu-id="554d6-113">Element</span></span>|<span data-ttu-id="554d6-114">설명</span><span class="sxs-lookup"><span data-stu-id="554d6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="554d6-115">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="554d6-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="554d6-116">특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="554d6-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="554d6-117">Text Value</span></span>

<span data-ttu-id="554d6-118">다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-118">Specify one of the following values:</span></span>

- <span data-ttu-id="554d6-119">EnumOnly: 컬렉션에 있는 개체의 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="554d6-120">CoreOnly: 컬렉션 개체의 속성만 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="554d6-121">Both: 컬렉션의 개체 속성 및 컬렉션 개체의 속성을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="554d6-122">설명</span><span class="sxs-lookup"><span data-stu-id="554d6-122">Remarks</span></span>

<span data-ttu-id="554d6-123">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="554d6-124">이 경우 컬렉션 개체는 **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="554d6-125">기본 동작은 컬렉션에 있는 개체의 속성만 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="554d6-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="554d6-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="554d6-126">See Also</span></span>

[<span data-ttu-id="554d6-127">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="554d6-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
