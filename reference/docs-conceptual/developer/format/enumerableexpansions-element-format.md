---
title: EnumerableExpansions 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363302"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="59765-102">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="59765-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="59765-103">.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="59765-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="59765-104">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="59765-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="59765-105">구문</span><span class="sxs-lookup"><span data-stu-id="59765-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59765-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="59765-106">Attributes and Elements</span></span>

<span data-ttu-id="59765-107">다음 섹션에서는 `EnumerableExpansions` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="59765-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="59765-108">사용할 수 있는 자식 요소 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59765-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="59765-109">특성</span><span class="sxs-lookup"><span data-stu-id="59765-109">Attributes</span></span>

<span data-ttu-id="59765-110">없음</span><span class="sxs-lookup"><span data-stu-id="59765-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="59765-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="59765-111">Child Elements</span></span>

|<span data-ttu-id="59765-112">요소</span><span class="sxs-lookup"><span data-stu-id="59765-112">Element</span></span>|<span data-ttu-id="59765-113">설명</span><span class="sxs-lookup"><span data-stu-id="59765-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59765-114">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="59765-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="59765-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="59765-115">Optional element.</span></span><br /><br /> <span data-ttu-id="59765-116">뷰에 표시 될 때 확장 되는 특정 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="59765-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="59765-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="59765-117">Parent Elements</span></span>

|<span data-ttu-id="59765-118">요소</span><span class="sxs-lookup"><span data-stu-id="59765-118">Element</span></span>|<span data-ttu-id="59765-119">설명</span><span class="sxs-lookup"><span data-stu-id="59765-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="59765-120">DefaultSettings 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="59765-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="59765-121">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="59765-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="59765-122">설명</span><span class="sxs-lookup"><span data-stu-id="59765-122">Remarks</span></span>

<span data-ttu-id="59765-123">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="59765-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="59765-124">이 경우 컬렉션 개체는 **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="59765-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="59765-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="59765-125">See Also</span></span>

[<span data-ttu-id="59765-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="59765-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
