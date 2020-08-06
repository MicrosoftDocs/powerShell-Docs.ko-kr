---
title: EnumerableExpansion 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 81a8959c19502a2e56f4cfa48a1e480509d84b6e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774051"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="5474c-102">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5474c-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="5474c-103">특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="5474c-104">Configuration 요소 (Format) DefaultSettings 요소 (Format) EnumerableExpansions 요소 (format) Enumerableexpansions 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5474c-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5474c-105">구문</span><span class="sxs-lookup"><span data-stu-id="5474c-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5474c-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5474c-106">Attributes and Elements</span></span>

<span data-ttu-id="5474c-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EnumerableExpansion` .</span><span class="sxs-lookup"><span data-stu-id="5474c-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5474c-108">특성</span><span class="sxs-lookup"><span data-stu-id="5474c-108">Attributes</span></span>

<span data-ttu-id="5474c-109">없음</span><span class="sxs-lookup"><span data-stu-id="5474c-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5474c-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5474c-110">Child Elements</span></span>

|<span data-ttu-id="5474c-111">요소</span><span class="sxs-lookup"><span data-stu-id="5474c-111">Element</span></span>|<span data-ttu-id="5474c-112">설명</span><span class="sxs-lookup"><span data-stu-id="5474c-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5474c-113">EnumerableExpansion에 대한 EntrySelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5474c-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="5474c-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5474c-115">이 정의에 의해 확장 되는 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="5474c-116">Expand 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5474c-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="5474c-117">이 정의에 대해 컬렉션 개체를 확장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5474c-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5474c-118">Parent Elements</span></span>

|<span data-ttu-id="5474c-119">요소</span><span class="sxs-lookup"><span data-stu-id="5474c-119">Element</span></span>|<span data-ttu-id="5474c-120">설명</span><span class="sxs-lookup"><span data-stu-id="5474c-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5474c-121">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5474c-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="5474c-122">.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5474c-123">설명</span><span class="sxs-lookup"><span data-stu-id="5474c-123">Remarks</span></span>

<span data-ttu-id="5474c-124">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="5474c-125">이 경우 컬렉션 개체는 **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="5474c-126">기본 동작은 컬렉션에 있는 개체의 속성만 표시 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5474c-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="5474c-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5474c-127">See Also</span></span>

[<span data-ttu-id="5474c-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5474c-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
