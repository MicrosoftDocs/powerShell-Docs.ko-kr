---
title: 이 listcontrol (형식)에 대 한 ListItems의 ListItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365132"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="0e037-102">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0e037-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="0e037-103">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="0e037-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소의이 listcontrol (format) ListItems 요소 (형식) 이 listcontrol 요소에 대 한 ListItem (형식)</span><span class="sxs-lookup"><span data-stu-id="0e037-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e037-105">구문</span><span class="sxs-lookup"><span data-stu-id="0e037-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e037-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0e037-106">Attributes and Elements</span></span>

<span data-ttu-id="0e037-107">다음 섹션에서는 `ListItem` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="0e037-108">하나의 속성 또는 스크립트만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e037-109">특성</span><span class="sxs-lookup"><span data-stu-id="0e037-109">Attributes</span></span>

<span data-ttu-id="0e037-110">없음</span><span class="sxs-lookup"><span data-stu-id="0e037-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e037-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0e037-111">Child Elements</span></span>

|<span data-ttu-id="0e037-112">요소</span><span class="sxs-lookup"><span data-stu-id="0e037-112">Element</span></span>|<span data-ttu-id="0e037-113">설명</span><span class="sxs-lookup"><span data-stu-id="0e037-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e037-114">이 listcontrol의 ListItem 요소에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0e037-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0e037-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0e037-116">속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 서식 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="0e037-117">이 listcontrol의 ListItem에 대 한 ItemSelectionCondition 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0e037-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0e037-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0e037-119">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="0e037-120">이 listcontrol (형식)의 ListItem에 대 한 Label 요소</span><span class="sxs-lookup"><span data-stu-id="0e037-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0e037-121">선택적 요소</span><span class="sxs-lookup"><span data-stu-id="0e037-121">Optional element</span></span><br /><br /> <span data-ttu-id="0e037-122">행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="0e037-123">이 listcontrol의 ListItem 요소에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0e037-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0e037-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0e037-125">해당 값이 행에 표시 되는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="0e037-126">이 listcontrol (형식)의 ListItem 요소에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="0e037-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="0e037-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-127">Optional element.</span></span><br /><br /> <span data-ttu-id="0e037-128">행에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0e037-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0e037-129">Parent Elements</span></span>

|<span data-ttu-id="0e037-130">요소</span><span class="sxs-lookup"><span data-stu-id="0e037-130">Element</span></span>|<span data-ttu-id="0e037-131">설명</span><span class="sxs-lookup"><span data-stu-id="0e037-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e037-132">List 컨트롤 (Format)의 ListItems 요소</span><span class="sxs-lookup"><span data-stu-id="0e037-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0e037-133">값이 목록 뷰에 표시 되는 속성 및 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0e037-134">설명</span><span class="sxs-lookup"><span data-stu-id="0e037-134">Remarks</span></span>

<span data-ttu-id="0e037-135">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0e037-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0e037-136">예제</span><span class="sxs-lookup"><span data-stu-id="0e037-136">Example</span></span>

<span data-ttu-id="0e037-137">이 예에서는 목록 뷰의 세 행을 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="0e037-138">처음 두 행에는 .NET 속성의 값이 표시 되 고 마지막 행에는 스크립트에 의해 생성 된 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0e037-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0e037-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e037-139">See Also</span></span>

[<span data-ttu-id="0e037-140">ListItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0e037-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0e037-141">ListItem의 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0e037-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0e037-142">ListItem의 Label 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0e037-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0e037-143">ListItem의 PropertyName 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0e037-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0e037-144">ListItem의 ScriptBlock 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0e037-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="0e037-145">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="0e037-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0e037-146">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="0e037-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
