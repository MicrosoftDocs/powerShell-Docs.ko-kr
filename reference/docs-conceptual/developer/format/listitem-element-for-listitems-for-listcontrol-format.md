---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ListItems에 대한 ListItem 요소(형식)
description: ListControl의 ListItems에 대한 ListItem 요소(형식)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666555"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="b4c66-103">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4c66-103">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="b4c66-104">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-104">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="b4c66-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry Element for이 listcontrol (format) ListItem for ListItems 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="b4c66-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b4c66-106">구문</span><span class="sxs-lookup"><span data-stu-id="b4c66-106">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b4c66-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="b4c66-107">Attributes and Elements</span></span>

<span data-ttu-id="b4c66-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListItem` .</span><span class="sxs-lookup"><span data-stu-id="b4c66-108">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="b4c66-109">하나의 속성 또는 스크립트만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-109">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="b4c66-110">특성</span><span class="sxs-lookup"><span data-stu-id="b4c66-110">Attributes</span></span>

<span data-ttu-id="b4c66-111">None</span><span class="sxs-lookup"><span data-stu-id="b4c66-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="b4c66-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="b4c66-112">Child Elements</span></span>

|<span data-ttu-id="b4c66-113">요소</span><span class="sxs-lookup"><span data-stu-id="b4c66-113">Element</span></span>|<span data-ttu-id="b4c66-114">설명</span><span class="sxs-lookup"><span data-stu-id="b4c66-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4c66-115">이 listcontrol의 ListItem 요소에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4c66-115">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b4c66-116">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b4c66-117">속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 서식 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-117">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="b4c66-118">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4c66-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b4c66-119">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b4c66-120">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-120">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="b4c66-121">ListControl의 ListItem에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4c66-121">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b4c66-122">선택적 요소</span><span class="sxs-lookup"><span data-stu-id="b4c66-122">Optional element</span></span><br /><br /> <span data-ttu-id="b4c66-123">행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-123">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="b4c66-124">ListControl의 ListItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4c66-124">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b4c66-125">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b4c66-126">해당 값이 행에 표시 되는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-126">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="b4c66-127">ListControl의 ListItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="b4c66-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="b4c66-128">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-128">Optional element.</span></span><br /><br /> <span data-ttu-id="b4c66-129">행에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-129">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b4c66-130">부모 요소</span><span class="sxs-lookup"><span data-stu-id="b4c66-130">Parent Elements</span></span>

|<span data-ttu-id="b4c66-131">요소</span><span class="sxs-lookup"><span data-stu-id="b4c66-131">Element</span></span>|<span data-ttu-id="b4c66-132">설명</span><span class="sxs-lookup"><span data-stu-id="b4c66-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b4c66-133">List 컨트롤 (Format)의 ListItems 요소</span><span class="sxs-lookup"><span data-stu-id="b4c66-133">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b4c66-134">값이 목록 뷰에 표시 되는 속성 및 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-134">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b4c66-135">설명</span><span class="sxs-lookup"><span data-stu-id="b4c66-135">Remarks</span></span>

<span data-ttu-id="b4c66-136">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4c66-136">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4c66-137">예제</span><span class="sxs-lookup"><span data-stu-id="b4c66-137">Example</span></span>

<span data-ttu-id="b4c66-138">이 예에서는 목록 뷰의 세 행을 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-138">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="b4c66-139">처음 두 행에는 .NET 속성의 값이 표시 되 고 마지막 행에는 스크립트에 의해 생성 된 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4c66-139">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="b4c66-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4c66-140">See Also</span></span>

[<span data-ttu-id="b4c66-141">ListItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b4c66-141">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b4c66-142">ListItem의 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="b4c66-142">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b4c66-143">ListItem의 Label 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b4c66-143">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b4c66-144">ListItem의 PropertyName 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b4c66-144">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b4c66-145">ListItem의 ScriptBlock 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="b4c66-145">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="b4c66-146">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="b4c66-146">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b4c66-147">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="b4c66-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
