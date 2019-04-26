---
title: EnumerableExpansion 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066144"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="94693-102">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="94693-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="94693-103">개체는 뷰에서 표시 되는 확장은 어떻게 특정.NET 컬렉션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="94693-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="94693-104">구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="94693-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="94693-105">구문</span><span class="sxs-lookup"><span data-stu-id="94693-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94693-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="94693-106">Attributes and Elements</span></span>

<span data-ttu-id="94693-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EnumerableExpansion` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="94693-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="94693-108">특성</span><span class="sxs-lookup"><span data-stu-id="94693-108">Attributes</span></span>

<span data-ttu-id="94693-109">없음</span><span class="sxs-lookup"><span data-stu-id="94693-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94693-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="94693-110">Child Elements</span></span>

|<span data-ttu-id="94693-111">요소</span><span class="sxs-lookup"><span data-stu-id="94693-111">Element</span></span>|<span data-ttu-id="94693-112">설명</span><span class="sxs-lookup"><span data-stu-id="94693-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94693-113">EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="94693-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="94693-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="94693-114">Optional element.</span></span><br /><br /> <span data-ttu-id="94693-115">이 정의 의해 확장 되는.NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="94693-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="94693-116">요소 (형식)를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="94693-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="94693-117">이 정의 대 한 컬렉션 개체는 확장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="94693-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94693-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="94693-118">Parent Elements</span></span>

|<span data-ttu-id="94693-119">요소</span><span class="sxs-lookup"><span data-stu-id="94693-119">Element</span></span>|<span data-ttu-id="94693-120">설명</span><span class="sxs-lookup"><span data-stu-id="94693-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94693-121">EnumerableExpansions 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="94693-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="94693-122">다양 한 방법을 개체 뷰의 표시 될 때 확장 되는.NET 컬렉션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="94693-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94693-123">설명</span><span class="sxs-lookup"><span data-stu-id="94693-123">Remarks</span></span>

<span data-ttu-id="94693-124">이 요소를 사용 하 여 컬렉션 개체 및 컬렉션의 개체 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="94693-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="94693-125">컬렉션 개체를 지 원하는 개체를 참조 하는 경우에 **System.Collections.ICollection** 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="94693-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="94693-126">기본 동작은 컬렉션에서 개체의 속성만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="94693-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="94693-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94693-127">See Also</span></span>

[<span data-ttu-id="94693-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="94693-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
