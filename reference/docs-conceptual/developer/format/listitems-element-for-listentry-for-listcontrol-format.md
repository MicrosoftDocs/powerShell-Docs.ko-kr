---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ListEntry에 대한 ListItems 요소(형식)
description: ListControl의 ListEntry에 대한 ListItems 요소(형식)
ms.openlocfilehash: 1553c81bc559020223a3c1fea10336baf017c9a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666538"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="b8e1c-103">ListControl의 ListEntry에 대한 ListItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8e1c-103">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="b8e1c-104">목록 뷰의 행에 값이 표시 되는 속성 및 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-104">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="b8e1c-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol element (format) ListEntries Element for이 listcontrol (format) ListItems Element for이 listcontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="b8e1c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b8e1c-106">구문</span><span class="sxs-lookup"><span data-stu-id="b8e1c-106">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8e1c-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b8e1c-107">Attributes and Elements</span></span>

<span data-ttu-id="b8e1c-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListItems` .</span><span class="sxs-lookup"><span data-stu-id="b8e1c-108">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="b8e1c-109">지정할 수 있는 자식 요소 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-109">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="b8e1c-110">자식 요소의 순서는 목록 보기에 값이 표시 되는 순서를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-110">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8e1c-111">특성</span><span class="sxs-lookup"><span data-stu-id="b8e1c-111">Attributes</span></span>

<span data-ttu-id="b8e1c-112">없음</span><span class="sxs-lookup"><span data-stu-id="b8e1c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b8e1c-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b8e1c-113">Child Elements</span></span>

|<span data-ttu-id="b8e1c-114">요소</span><span class="sxs-lookup"><span data-stu-id="b8e1c-114">Element</span></span>|<span data-ttu-id="b8e1c-115">설명</span><span class="sxs-lookup"><span data-stu-id="b8e1c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8e1c-116">이 listcontrol에 대 한 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b8e1c-116">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="b8e1c-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-117">Required element.</span></span><br /><br /> <span data-ttu-id="b8e1c-118">목록 뷰에서 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-118">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b8e1c-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b8e1c-119">Parent Elements</span></span>

|<span data-ttu-id="b8e1c-120">요소</span><span class="sxs-lookup"><span data-stu-id="b8e1c-120">Element</span></span>|<span data-ttu-id="b8e1c-121">설명</span><span class="sxs-lookup"><span data-stu-id="b8e1c-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b8e1c-122">ListControl에 대한 ListEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8e1c-122">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="b8e1c-123">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-123">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8e1c-124">설명</span><span class="sxs-lookup"><span data-stu-id="b8e1c-124">Remarks</span></span>

<span data-ttu-id="b8e1c-125">이 유형의 보기에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-125">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b8e1c-126">예제</span><span class="sxs-lookup"><span data-stu-id="b8e1c-126">Example</span></span>

<span data-ttu-id="b8e1c-127">이 예에서는 목록 뷰의 세 행을 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8e1c-127">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="b8e1c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b8e1c-128">See Also</span></span>

[<span data-ttu-id="b8e1c-129">ListControl에 대한 ListEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b8e1c-129">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="b8e1c-130">이 listcontrol에 대 한 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b8e1c-130">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="b8e1c-131">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="b8e1c-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b8e1c-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b8e1c-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
