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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363302"
---
# <a name="enumerableexpansions-element-format"></a><span data-ttu-id="1e1bc-102">EnumerableExpansions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1e1bc-102">EnumerableExpansions Element (Format)</span></span>

<span data-ttu-id="1e1bc-103">.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-103">Defines how .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="1e1bc-104">Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1e1bc-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1e1bc-105">구문</span><span class="sxs-lookup"><span data-stu-id="1e1bc-105">Syntax</span></span>

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e1bc-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1e1bc-106">Attributes and Elements</span></span>

<span data-ttu-id="1e1bc-107">다음 섹션에서는 특성, 자식 요소 및 `EnumerableExpansions` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansions` element.</span></span> <span data-ttu-id="1e1bc-108">사용할 수 있는 자식 요소 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-108">There is no limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="1e1bc-109">특성</span><span class="sxs-lookup"><span data-stu-id="1e1bc-109">Attributes</span></span>

<span data-ttu-id="1e1bc-110">없음</span><span class="sxs-lookup"><span data-stu-id="1e1bc-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1e1bc-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1e1bc-111">Child Elements</span></span>

|<span data-ttu-id="1e1bc-112">요소</span><span class="sxs-lookup"><span data-stu-id="1e1bc-112">Element</span></span>|<span data-ttu-id="1e1bc-113">설명</span><span class="sxs-lookup"><span data-stu-id="1e1bc-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e1bc-114">EnumerableExpansion 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1e1bc-114">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="1e1bc-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1e1bc-116">뷰에 표시 될 때 확장 되는 특정 .NET 컬렉션 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-116">Defines the specific .NET collection objects that are expanded when they are displayed in a view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1e1bc-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1e1bc-117">Parent Elements</span></span>

|<span data-ttu-id="1e1bc-118">요소</span><span class="sxs-lookup"><span data-stu-id="1e1bc-118">Element</span></span>|<span data-ttu-id="1e1bc-119">설명</span><span class="sxs-lookup"><span data-stu-id="1e1bc-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1e1bc-120">DefaultSettings 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1e1bc-120">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="1e1bc-121">서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-121">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1e1bc-122">설명</span><span class="sxs-lookup"><span data-stu-id="1e1bc-122">Remarks</span></span>

<span data-ttu-id="1e1bc-123">이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-123">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="1e1bc-124">이 경우 컬렉션 개체는 **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="1e1bc-124">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="1e1bc-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1e1bc-125">See Also</span></span>

[<span data-ttu-id="1e1bc-126">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1e1bc-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
