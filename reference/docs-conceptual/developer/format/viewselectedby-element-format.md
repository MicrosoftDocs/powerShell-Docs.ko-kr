---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy 요소(형식)
description: ViewSelectedBy 요소(형식)
ms.openlocfilehash: ac3c7de299b3009a067a476a024c6a6fcb5dce02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667711"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="d8f65-103">ViewSelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d8f65-103">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="d8f65-104">뷰에 표시 되는 .NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-104">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="d8f65-105">각 보기는 하나 이상의 .NET 개체를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-105">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="d8f65-106">ViewDefinitions 요소 (Format) View 요소 (format) ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="d8f65-106">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d8f65-107">구문</span><span class="sxs-lookup"><span data-stu-id="d8f65-107">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d8f65-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d8f65-108">Attributes and Elements</span></span>

<span data-ttu-id="d8f65-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ViewSelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="d8f65-109">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="d8f65-110">이 요소는 하나 이상의 `TypeName` 또는 자식 요소를 포함 해야 합니다 `SelectionSetName` .</span><span class="sxs-lookup"><span data-stu-id="d8f65-110">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="d8f65-111">지정할 수 있는 자식 요소 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-111">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="d8f65-112">특성</span><span class="sxs-lookup"><span data-stu-id="d8f65-112">Attributes</span></span>

<span data-ttu-id="d8f65-113">없음</span><span class="sxs-lookup"><span data-stu-id="d8f65-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d8f65-114">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d8f65-114">Child Elements</span></span>

|<span data-ttu-id="d8f65-115">요소</span><span class="sxs-lookup"><span data-stu-id="d8f65-115">Element</span></span>|<span data-ttu-id="d8f65-116">설명</span><span class="sxs-lookup"><span data-stu-id="d8f65-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8f65-117">ViewSelectedBy에 대한 TypeName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d8f65-117">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="d8f65-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-118">Optional element.</span></span><br /><br /> <span data-ttu-id="d8f65-119">뷰에 표시 되는 .NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-119">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="d8f65-120">ViewSelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d8f65-120">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="d8f65-121">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-121">Optional element.</span></span><br /><br /> <span data-ttu-id="d8f65-122">뷰에 표시 되는 .NET 개체의 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-122">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d8f65-123">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d8f65-123">Parent Elements</span></span>

|<span data-ttu-id="d8f65-124">요소</span><span class="sxs-lookup"><span data-stu-id="d8f65-124">Element</span></span>|<span data-ttu-id="d8f65-125">설명</span><span class="sxs-lookup"><span data-stu-id="d8f65-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d8f65-126">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d8f65-126">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d8f65-127">하나 이상의 .NET 개체를 표시 하는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-127">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d8f65-128">설명</span><span class="sxs-lookup"><span data-stu-id="d8f65-128">Remarks</span></span>

<span data-ttu-id="d8f65-129">다른 뷰에서이 요소를 사용 하는 방법에 대 한 자세한 내용은 [테이블 뷰 구성 요소](./creating-a-table-view.md), [목록 뷰 구성 요소](./creating-a-list-view.md), [넓은 뷰 구성](./creating-a-wide-view.md)요소 및 [사용자 지정 컨트롤 구성 요소](./creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8f65-129">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="d8f65-130">`SelectionSetName`서식 파일에서 여러 뷰에 표시 되는 개체 집합을 정의할 때 요소가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-130">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="d8f65-131">선택 집합을 정의 하 고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d8f65-131">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="d8f65-132">예제</span><span class="sxs-lookup"><span data-stu-id="d8f65-132">Example</span></span>

<span data-ttu-id="d8f65-133">다음 예제에서는 목록 뷰에 대 한 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체를 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-133">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="d8f65-134">테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d8f65-134">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="d8f65-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d8f65-135">See Also</span></span>

[<span data-ttu-id="d8f65-136">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d8f65-136">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d8f65-137">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d8f65-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d8f65-138">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d8f65-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d8f65-139">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="d8f65-139">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d8f65-140">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="d8f65-140">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d8f65-141">ViewSelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d8f65-141">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="d8f65-142">TypeName 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="d8f65-142">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="d8f65-143">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d8f65-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
