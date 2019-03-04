---
title: ViewSelectedBy 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863189"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="93fdd-102">ViewSelectedBy 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="93fdd-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="93fdd-103">보기에 표시 되는.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="93fdd-104">각 보기에는.NET 개체를 하나 이상 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="93fdd-105">ViewDefinitions 요소 (형식) 보기 (형식) ViewSelectedBy 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="93fdd-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="93fdd-106">구문</span><span class="sxs-lookup"><span data-stu-id="93fdd-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="93fdd-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-107">Attributes and Elements</span></span>

<span data-ttu-id="93fdd-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ViewSelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="93fdd-109">이 요소는 하나 이상 포함 해야 합니다 `TypeName` 또는 `SelectionSetName` 자식 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="93fdd-110">지정 될 수 있는 자식 요소의 수에 제한이 나 순서는 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="93fdd-111">특성</span><span class="sxs-lookup"><span data-stu-id="93fdd-111">Attributes</span></span>

<span data-ttu-id="93fdd-112">없음</span><span class="sxs-lookup"><span data-stu-id="93fdd-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="93fdd-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-113">Child Elements</span></span>

|<span data-ttu-id="93fdd-114">요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-114">Element</span></span>|<span data-ttu-id="93fdd-115">설명</span><span class="sxs-lookup"><span data-stu-id="93fdd-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93fdd-116">ViewSelectedBy (형식)에 대 한 TypeName 요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="93fdd-117">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-117">Optional element.</span></span><br /><br /> <span data-ttu-id="93fdd-118">보기에 표시 되는.NET 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="93fdd-119">ViewSelectedBy (형식)에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="93fdd-120">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-120">Optional element.</span></span><br /><br /> <span data-ttu-id="93fdd-121">보기에 표시 되는.NET 개체 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="93fdd-122">부모 요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-122">Parent Elements</span></span>

|<span data-ttu-id="93fdd-123">요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-123">Element</span></span>|<span data-ttu-id="93fdd-124">설명</span><span class="sxs-lookup"><span data-stu-id="93fdd-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="93fdd-125">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="93fdd-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="93fdd-126">하나 이상의.NET 개체를 표시 하는 보기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="93fdd-127">설명</span><span class="sxs-lookup"><span data-stu-id="93fdd-127">Remarks</span></span>

<span data-ttu-id="93fdd-128">다른 보기에이 요소를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [테이블 뷰 구성 요소](./creating-a-table-view.md)를 [목록 뷰 구성 요소](./creating-a-list-view.md)합니다 [뷰 구성 요소를 와이드](./creating-a-wide-view.md), 및 [사용자 지정 컨트롤 구성 요소](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="93fdd-129">`SelectionSetName` 요소는 서식 파일은 여러 뷰에서 표시 되는 개체 집합을 정의 하는 경우 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="93fdd-130">선택 집합이 정의 되어 있고 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="93fdd-131">예제</span><span class="sxs-lookup"><span data-stu-id="93fdd-131">Example</span></span>

<span data-ttu-id="93fdd-132">다음 예제에서는 지정 하는 방법을 보여 줍니다 합니다 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 목록 보기에 대 한 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="93fdd-133">동일한 스키마는 테이블, 넓게 및 사용자 지정 보기에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93fdd-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="93fdd-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93fdd-134">See Also</span></span>

[<span data-ttu-id="93fdd-135">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="93fdd-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="93fdd-136">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="93fdd-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="93fdd-137">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="93fdd-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="93fdd-138">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="93fdd-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="93fdd-139">선택 영역 집합을 정의</span><span class="sxs-lookup"><span data-stu-id="93fdd-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="93fdd-140">ViewSelectedBy (형식)에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="93fdd-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="93fdd-141">TypeName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="93fdd-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="93fdd-142">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="93fdd-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
