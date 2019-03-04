---
title: ViewDefinitions 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862089"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="32e0a-102">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="32e0a-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="32e0a-103">.NET 개체를 표시 하는 데 사용 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="32e0a-104">이러한 뷰는 테이블 형식, 목록 형식으로, 넓은 형식 및 사용자 지정 컨트롤 형식에 속성 및 개체의 스크립트 값을 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="32e0a-105">구성 요소 (형식) (XML 형식) ViewDefinitions 요소</span><span class="sxs-lookup"><span data-stu-id="32e0a-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="32e0a-106">구문</span><span class="sxs-lookup"><span data-stu-id="32e0a-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="32e0a-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="32e0a-107">Attributes and Elements</span></span>

<span data-ttu-id="32e0a-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ViewDefinitions` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="32e0a-109">서식 파일에서 정의 될 수 있는 수에 제한이 없음을 이며 순서에 관계 없이 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="32e0a-110">특성</span><span class="sxs-lookup"><span data-stu-id="32e0a-110">Attributes</span></span>

<span data-ttu-id="32e0a-111">없음</span><span class="sxs-lookup"><span data-stu-id="32e0a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="32e0a-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="32e0a-112">Child Elements</span></span>

|<span data-ttu-id="32e0a-113">요소</span><span class="sxs-lookup"><span data-stu-id="32e0a-113">Element</span></span>|<span data-ttu-id="32e0a-114">설명</span><span class="sxs-lookup"><span data-stu-id="32e0a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32e0a-115">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="32e0a-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="32e0a-116">하나 이상의.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="32e0a-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="32e0a-117">Parent Elements</span></span>

|<span data-ttu-id="32e0a-118">요소</span><span class="sxs-lookup"><span data-stu-id="32e0a-118">Element</span></span>|<span data-ttu-id="32e0a-119">설명</span><span class="sxs-lookup"><span data-stu-id="32e0a-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="32e0a-120">구성 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="32e0a-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="32e0a-121">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="32e0a-122">설명</span><span class="sxs-lookup"><span data-stu-id="32e0a-122">Remarks</span></span>

<span data-ttu-id="32e0a-123">다양 한 유형의 보기의 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="32e0a-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="32e0a-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="32e0a-125">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="32e0a-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="32e0a-126">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="32e0a-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="32e0a-127">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="32e0a-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="32e0a-128">예제</span><span class="sxs-lookup"><span data-stu-id="32e0a-128">Example</span></span>

<span data-ttu-id="32e0a-129">이 예제는 `ViewDefinitions` 테이블 뷰 및 목록 보기에 대 한 부모 요소를 포함 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="32e0a-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="32e0a-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="32e0a-130">See Also</span></span>

[<span data-ttu-id="32e0a-131">구성 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="32e0a-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="32e0a-132">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="32e0a-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="32e0a-133">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="32e0a-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="32e0a-134">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="32e0a-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="32e0a-135">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="32e0a-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="32e0a-136">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="32e0a-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="32e0a-137">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="32e0a-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
