---
ms.date: 09/13/2016
ms.topic: reference
title: ViewDefinitions 요소(형식)
description: ViewDefinitions 요소(형식)
ms.openlocfilehash: fceef0e5ec91e8c59a7b2b90fd31ca422ff0c94d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664583"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="3369e-103">ViewDefinitions 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3369e-103">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="3369e-104">.NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3369e-104">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="3369e-105">이러한 뷰에서는 개체의 속성 및 스크립트 값을 테이블 형식, 목록 형식, 넓은 형식 및 사용자 지정 컨트롤 형식으로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3369e-105">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="3369e-106">Configuration 요소 (Format) ViewDefinitions (Format XML) 요소</span><span class="sxs-lookup"><span data-stu-id="3369e-106">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="3369e-107">구문</span><span class="sxs-lookup"><span data-stu-id="3369e-107">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3369e-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3369e-108">Attributes and Elements</span></span>

<span data-ttu-id="3369e-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ViewDefinitions` .</span><span class="sxs-lookup"><span data-stu-id="3369e-109">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="3369e-110">서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없으며 순서에 관계 없이 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3369e-110">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="3369e-111">특성</span><span class="sxs-lookup"><span data-stu-id="3369e-111">Attributes</span></span>

<span data-ttu-id="3369e-112">없음</span><span class="sxs-lookup"><span data-stu-id="3369e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3369e-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3369e-113">Child Elements</span></span>

|<span data-ttu-id="3369e-114">요소</span><span class="sxs-lookup"><span data-stu-id="3369e-114">Element</span></span>|<span data-ttu-id="3369e-115">설명</span><span class="sxs-lookup"><span data-stu-id="3369e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3369e-116">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3369e-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="3369e-117">하나 이상의 .NET 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3369e-117">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3369e-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3369e-118">Parent Elements</span></span>

|<span data-ttu-id="3369e-119">요소</span><span class="sxs-lookup"><span data-stu-id="3369e-119">Element</span></span>|<span data-ttu-id="3369e-120">설명</span><span class="sxs-lookup"><span data-stu-id="3369e-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3369e-121">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3369e-121">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="3369e-122">서식 파일의 최상위 요소를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3369e-122">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3369e-123">설명</span><span class="sxs-lookup"><span data-stu-id="3369e-123">Remarks</span></span>

<span data-ttu-id="3369e-124">여러 유형의 보기 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="3369e-124">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="3369e-125">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3369e-125">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="3369e-126">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3369e-126">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="3369e-127">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3369e-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="3369e-128">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="3369e-128">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="3369e-129">예제</span><span class="sxs-lookup"><span data-stu-id="3369e-129">Example</span></span>

<span data-ttu-id="3369e-130">이 예에서는 `ViewDefinitions` 테이블 뷰의 부모 요소와 목록 뷰를 포함 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3369e-130">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3369e-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3369e-131">See Also</span></span>

[<span data-ttu-id="3369e-132">Configuration 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3369e-132">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="3369e-133">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3369e-133">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="3369e-134">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3369e-134">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="3369e-135">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3369e-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3369e-136">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3369e-136">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3369e-137">사용자 지정 컨트롤</span><span class="sxs-lookup"><span data-stu-id="3369e-137">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="3369e-138">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3369e-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
