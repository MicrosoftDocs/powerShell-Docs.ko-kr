---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansion 요소(형식)
description: EnumerableExpansion 요소(형식)
ms.openlocfilehash: 207ad99d5335e99701660159ab77279b55b0b6b5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668017"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="ca7a3-103">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ca7a3-103">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="ca7a3-104">특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-104">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="ca7a3-105">Configuration 요소 (Format) DefaultSettings 요소 (Format) EnumerableExpansions 요소 (format) Enumerableexpansions 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="ca7a3-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ca7a3-106">구문</span><span class="sxs-lookup"><span data-stu-id="ca7a3-106">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca7a3-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ca7a3-107">Attributes and Elements</span></span>

<span data-ttu-id="ca7a3-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EnumerableExpansion` .</span><span class="sxs-lookup"><span data-stu-id="ca7a3-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca7a3-109">특성</span><span class="sxs-lookup"><span data-stu-id="ca7a3-109">Attributes</span></span>

<span data-ttu-id="ca7a3-110">없음</span><span class="sxs-lookup"><span data-stu-id="ca7a3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ca7a3-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ca7a3-111">Child Elements</span></span>

|<span data-ttu-id="ca7a3-112">요소</span><span class="sxs-lookup"><span data-stu-id="ca7a3-112">Element</span></span>|<span data-ttu-id="ca7a3-113">설명</span><span class="sxs-lookup"><span data-stu-id="ca7a3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca7a3-114">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ca7a3-114">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="ca7a3-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ca7a3-116">이 정의에 의해 확장 되는 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-116">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="ca7a3-117">Expand 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ca7a3-117">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="ca7a3-118">이 정의에 대해 컬렉션 개체를 확장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-118">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ca7a3-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ca7a3-119">Parent Elements</span></span>

|<span data-ttu-id="ca7a3-120">요소</span><span class="sxs-lookup"><span data-stu-id="ca7a3-120">Element</span></span>|<span data-ttu-id="ca7a3-121">설명</span><span class="sxs-lookup"><span data-stu-id="ca7a3-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ca7a3-122">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ca7a3-122">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="ca7a3-123">.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-123">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca7a3-124">설명</span><span class="sxs-lookup"><span data-stu-id="ca7a3-124">Remarks</span></span>

<span data-ttu-id="ca7a3-125">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-125">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="ca7a3-126">이 경우 컬렉션 개체는  **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-126">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="ca7a3-127">기본 동작은 컬렉션에 있는 개체의 속성만 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ca7a3-127">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca7a3-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca7a3-128">See Also</span></span>

[<span data-ttu-id="ca7a3-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ca7a3-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
