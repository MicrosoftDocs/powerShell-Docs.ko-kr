---
title: ListItem 요소 ListItems ListControl (형식)에 대 한 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855159"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="cbe72-102">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cbe72-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="cbe72-103">속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="cbe72-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListControl (형식)에 대 한 ListControl (형식) ListItems 요소에 대 한 ListEntry 요소의 ListControl (형식) ListItem ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cbe72-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cbe72-105">구문</span><span class="sxs-lookup"><span data-stu-id="cbe72-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cbe72-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-106">Attributes and Elements</span></span>

<span data-ttu-id="cbe72-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListItem` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="cbe72-108">속성 또는 스크립트를 하나만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="cbe72-109">특성</span><span class="sxs-lookup"><span data-stu-id="cbe72-109">Attributes</span></span>

<span data-ttu-id="cbe72-110">없음</span><span class="sxs-lookup"><span data-stu-id="cbe72-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="cbe72-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-111">Child Elements</span></span>

|<span data-ttu-id="cbe72-112">요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-112">Element</span></span>|<span data-ttu-id="cbe72-113">설명</span><span class="sxs-lookup"><span data-stu-id="cbe72-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbe72-114">ListItem ListControl (형식)에 대 한 FormatString 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="cbe72-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-115">Optional element.</span></span><br /><br /> <span data-ttu-id="cbe72-116">스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="cbe72-117">ListItem ListControl (형식)에 대 한 ItemSelectionCondition 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="cbe72-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-118">Optional element.</span></span><br /><br /> <span data-ttu-id="cbe72-119">이 목록 항목을 사용할 수 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="cbe72-120">ListItem ListControl (형식)에 대 한 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="cbe72-121">선택적 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-121">Optional element</span></span><br /><br /> <span data-ttu-id="cbe72-122">행의 속성이 나 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="cbe72-123">PropertyName ListControl (형식)에 대 한 ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="cbe72-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-124">Optional element.</span></span><br /><br /> <span data-ttu-id="cbe72-125">.NET 속성 값을 갖는 행에 표시 됩니다 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="cbe72-126">ScriptBlock ListControl (형식)에 대 한 ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="cbe72-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-127">Optional element.</span></span><br /><br /> <span data-ttu-id="cbe72-128">행에 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cbe72-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-129">Parent Elements</span></span>

|<span data-ttu-id="cbe72-130">요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-130">Element</span></span>|<span data-ttu-id="cbe72-131">설명</span><span class="sxs-lookup"><span data-stu-id="cbe72-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cbe72-132">목록 컨트롤 (형식)에 대 한 ListItems 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="cbe72-133">속성 및 값을 목록 보기에 표시 되는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cbe72-134">설명</span><span class="sxs-lookup"><span data-stu-id="cbe72-134">Remarks</span></span>

<span data-ttu-id="cbe72-135">목록 뷰 구성 요소에 대 한 자세한 내용은 참조 [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cbe72-136">예제</span><span class="sxs-lookup"><span data-stu-id="cbe72-136">Example</span></span>

<span data-ttu-id="cbe72-137">이 예제에서는 목록 보기의 3 개의 행을 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="cbe72-138">.NET 속성의 값을 표시 하는 처음 두 행 및 마지막 행을 스크립트에 의해 생성 된 값을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="cbe72-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cbe72-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbe72-139">See Also</span></span>

[<span data-ttu-id="cbe72-140">ListItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="cbe72-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="cbe72-141">ListItem (형식)에 대 한 FormatString 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="cbe72-142">ListItem (형식)에 대 한 레이블 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="cbe72-143">ListItem (형식)에 대 한 PropertyName 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="cbe72-144">ListItem (형식)에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="cbe72-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="cbe72-145">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="cbe72-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cbe72-146">Windows PowerShell 형식 지정을 작성 하 고 파일 형식</span><span class="sxs-lookup"><span data-stu-id="cbe72-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
