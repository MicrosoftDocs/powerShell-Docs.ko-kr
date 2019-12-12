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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361422"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="94e86-102">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="94e86-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="94e86-103">.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e86-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="94e86-104">이러한 뷰에서는 개체의 속성 및 스크립트 값을 테이블 형식, 목록 형식, 넓은 형식 및 사용자 지정 컨트롤 형식으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94e86-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="94e86-105">Configuration 요소 (Format) ViewDefinitions (Format XML) 요소</span><span class="sxs-lookup"><span data-stu-id="94e86-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="94e86-106">구문</span><span class="sxs-lookup"><span data-stu-id="94e86-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94e86-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="94e86-107">Attributes and Elements</span></span>

<span data-ttu-id="94e86-108">다음 섹션에서는 `ViewDefinitions` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e86-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="94e86-109">서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없으며 순서에 관계 없이 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="94e86-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="94e86-110">특성</span><span class="sxs-lookup"><span data-stu-id="94e86-110">Attributes</span></span>

<span data-ttu-id="94e86-111">없음</span><span class="sxs-lookup"><span data-stu-id="94e86-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="94e86-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="94e86-112">Child Elements</span></span>

|<span data-ttu-id="94e86-113">요소</span><span class="sxs-lookup"><span data-stu-id="94e86-113">Element</span></span>|<span data-ttu-id="94e86-114">설명</span><span class="sxs-lookup"><span data-stu-id="94e86-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94e86-115">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="94e86-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="94e86-116">하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="94e86-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94e86-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="94e86-117">Parent Elements</span></span>

|<span data-ttu-id="94e86-118">요소</span><span class="sxs-lookup"><span data-stu-id="94e86-118">Element</span></span>|<span data-ttu-id="94e86-119">설명</span><span class="sxs-lookup"><span data-stu-id="94e86-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="94e86-120">Configuration 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="94e86-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="94e86-121">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="94e86-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94e86-122">설명</span><span class="sxs-lookup"><span data-stu-id="94e86-122">Remarks</span></span>

<span data-ttu-id="94e86-123">여러 유형의 보기 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="94e86-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="94e86-124">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="94e86-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="94e86-125">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="94e86-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="94e86-126">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="94e86-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="94e86-127">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="94e86-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="94e86-128">예제</span><span class="sxs-lookup"><span data-stu-id="94e86-128">Example</span></span>

<span data-ttu-id="94e86-129">이 예에서는 테이블 뷰의 부모 요소와 목록 뷰를 포함 하는 `ViewDefinitions` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="94e86-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="94e86-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="94e86-130">See Also</span></span>

[<span data-ttu-id="94e86-131">Configuration 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="94e86-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="94e86-132">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="94e86-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="94e86-133">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="94e86-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="94e86-134">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="94e86-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="94e86-135">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="94e86-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="94e86-136">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="94e86-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="94e86-137">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="94e86-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
