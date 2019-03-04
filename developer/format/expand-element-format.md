---
title: 확장 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858579"
---
# <a name="expand-element-format"></a><span data-ttu-id="62840-102">Expand 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="62840-102">Expand Element (Format)</span></span>

<span data-ttu-id="62840-103">이 정의 대 한 컬렉션 개체는 확장 하는 방법을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-103">Specifies how the collection object is expanded for this definition.</span></span>

<span data-ttu-id="62840-104">구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) (형식) 요소를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) Expand Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="62840-105">구문</span><span class="sxs-lookup"><span data-stu-id="62840-105">Syntax</span></span>

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="62840-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="62840-106">Attributes and Elements</span></span>

<span data-ttu-id="62840-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Expand` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="62840-107">The following sections describe attributes, child elements, and the parent element of the `Expand` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="62840-108">특성</span><span class="sxs-lookup"><span data-stu-id="62840-108">Attributes</span></span>

<span data-ttu-id="62840-109">없음</span><span class="sxs-lookup"><span data-stu-id="62840-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="62840-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="62840-110">Child Elements</span></span>

<span data-ttu-id="62840-111">없음</span><span class="sxs-lookup"><span data-stu-id="62840-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="62840-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="62840-112">Parent Elements</span></span>

|<span data-ttu-id="62840-113">요소</span><span class="sxs-lookup"><span data-stu-id="62840-113">Element</span></span>|<span data-ttu-id="62840-114">설명</span><span class="sxs-lookup"><span data-stu-id="62840-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="62840-115">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="62840-115">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="62840-116">개체는 뷰에서 표시 되는 확장은 어떻게 특정.NET 컬렉션을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-116">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="62840-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="62840-117">Text Value</span></span>

<span data-ttu-id="62840-118">다음 값 중 하나를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-118">Specify one of the following values:</span></span>

- <span data-ttu-id="62840-119">EnumOnly: 컬렉션에서 개체의 속성만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-119">EnumOnly: Displays only the properties of the objects in the collection.</span></span>

- <span data-ttu-id="62840-120">CoreOnly: 컬렉션 개체의 속성만 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-120">CoreOnly: Displays only the properties of the collection object.</span></span>

- <span data-ttu-id="62840-121">모두: 컬렉션 및 컬렉션 개체의 속성에서 개체의 속성을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-121">Both: Displays the properties of the objects in the collection and the properties of the collection object.</span></span>

## <a name="remarks"></a><span data-ttu-id="62840-122">설명</span><span class="sxs-lookup"><span data-stu-id="62840-122">Remarks</span></span>

<span data-ttu-id="62840-123">이 요소를 사용 하 여 컬렉션 개체 및 컬렉션의 개체 표시 되는 방식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="62840-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="62840-124">컬렉션 개체를 지 원하는 개체를 참조 하는 경우에 **System.Collections.ICollection** 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="62840-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="62840-125">기본 동작은 컬렉션에서 개체의 속성만 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="62840-125">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="62840-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="62840-126">See Also</span></span>

[<span data-ttu-id="62840-127">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="62840-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
