---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansions 요소(형식)
description: EnumerableExpansions 요소(형식)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660185"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="4851a-103">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4851a-103">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="4851a-104">.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4851a-104">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="4851a-105">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="4851a-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4851a-106">구문</span><span class="sxs-lookup"><span data-stu-id="4851a-106">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4851a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="4851a-107">Attributes and Elements</span></span>

<span data-ttu-id="4851a-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EnumerableExpansions` .</span><span class="sxs-lookup"><span data-stu-id="4851a-108">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="4851a-109">사용할 수 있는 자식 요소 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4851a-109">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="4851a-110">특성</span><span class="sxs-lookup"><span data-stu-id="4851a-110">Attributes</span></span>

<span data-ttu-id="4851a-111">없음</span><span class="sxs-lookup"><span data-stu-id="4851a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4851a-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="4851a-112">Child Elements</span></span>

|<span data-ttu-id="4851a-113">요소</span><span class="sxs-lookup"><span data-stu-id="4851a-113">Element</span></span>|<span data-ttu-id="4851a-114">설명</span><span class="sxs-lookup"><span data-stu-id="4851a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4851a-115">EnumerableExpansion 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4851a-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="4851a-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4851a-116">Optional element.</span></span><br /><br /> <span data-ttu-id="4851a-117">뷰에 표시 될 때 확장 되는 특정 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4851a-117">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4851a-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="4851a-118">Parent Elements</span></span>

|<span data-ttu-id="4851a-119">요소</span><span class="sxs-lookup"><span data-stu-id="4851a-119">Element</span></span>|<span data-ttu-id="4851a-120">설명</span><span class="sxs-lookup"><span data-stu-id="4851a-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4851a-121">DefaultSettings 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="4851a-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="4851a-122">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4851a-122">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4851a-123">설명</span><span class="sxs-lookup"><span data-stu-id="4851a-123">Remarks</span></span>

<span data-ttu-id="4851a-124">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4851a-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="4851a-125">이 경우 컬렉션 개체는  **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="4851a-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="4851a-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4851a-126">See Also</span></span>

[<span data-ttu-id="4851a-127">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4851a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
