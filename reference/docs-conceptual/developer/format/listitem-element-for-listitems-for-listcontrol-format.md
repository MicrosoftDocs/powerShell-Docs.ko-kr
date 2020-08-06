---
title: 이 listcontrol (형식)에 대 한 ListItems의 ListItem 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e72a887e8bd1f93bacb663e3079eeaec34bdfa51
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785679"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="3d0b4-102">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="3d0b4-103">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="3d0b4-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry Element for이 listcontrol (format) ListItem for ListItems 요소 (format)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d0b4-105">구문</span><span class="sxs-lookup"><span data-stu-id="3d0b4-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d0b4-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3d0b4-106">Attributes and Elements</span></span>

<span data-ttu-id="3d0b4-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListItem` .</span><span class="sxs-lookup"><span data-stu-id="3d0b4-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="3d0b4-108">하나의 속성 또는 스크립트만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d0b4-109">특성</span><span class="sxs-lookup"><span data-stu-id="3d0b4-109">Attributes</span></span>

<span data-ttu-id="3d0b4-110">없음</span><span class="sxs-lookup"><span data-stu-id="3d0b4-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d0b4-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3d0b4-111">Child Elements</span></span>

|<span data-ttu-id="3d0b4-112">요소</span><span class="sxs-lookup"><span data-stu-id="3d0b4-112">Element</span></span>|<span data-ttu-id="3d0b4-113">설명</span><span class="sxs-lookup"><span data-stu-id="3d0b4-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d0b4-114">이 listcontrol의 ListItem 요소에 대 한 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3d0b4-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3d0b4-116">속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 서식 문자열을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="3d0b4-117">ListControl의 ListItem에 대한 ItemSelectionCondition 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3d0b4-118">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3d0b4-119">이 목록 항목을 사용 하기 위해 있어야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="3d0b4-120">ListControl의 ListItem에 대한 Label 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3d0b4-121">선택적 요소</span><span class="sxs-lookup"><span data-stu-id="3d0b4-121">Optional element</span></span><br /><br /> <span data-ttu-id="3d0b4-122">행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="3d0b4-123">ListControl의 ListItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3d0b4-124">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3d0b4-125">해당 값이 행에 표시 되는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="3d0b4-126">ListControl의 ListItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="3d0b4-127">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-127">Optional element.</span></span><br /><br /> <span data-ttu-id="3d0b4-128">행에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d0b4-129">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3d0b4-129">Parent Elements</span></span>

|<span data-ttu-id="3d0b4-130">요소</span><span class="sxs-lookup"><span data-stu-id="3d0b4-130">Element</span></span>|<span data-ttu-id="3d0b4-131">설명</span><span class="sxs-lookup"><span data-stu-id="3d0b4-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d0b4-132">List 컨트롤 (Format)의 ListItems 요소</span><span class="sxs-lookup"><span data-stu-id="3d0b4-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="3d0b4-133">값이 목록 뷰에 표시 되는 속성 및 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d0b4-134">설명</span><span class="sxs-lookup"><span data-stu-id="3d0b4-134">Remarks</span></span>

<span data-ttu-id="3d0b4-135">목록 뷰의 구성 요소에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3d0b4-136">예제</span><span class="sxs-lookup"><span data-stu-id="3d0b4-136">Example</span></span>

<span data-ttu-id="3d0b4-137">이 예에서는 목록 뷰의 세 행을 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="3d0b4-138">처음 두 행에는 .NET 속성의 값이 표시 되 고 마지막 행에는 스크립트에 의해 생성 된 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d0b4-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3d0b4-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d0b4-139">See Also</span></span>

[<span data-ttu-id="3d0b4-140">ListItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="3d0b4-141">ListItem의 FormatString 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3d0b4-142">ListItem의 Label 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3d0b4-143">ListItem의 PropertyName 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3d0b4-144">ListItem의 ScriptBlock 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="3d0b4-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="3d0b4-145">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="3d0b4-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3d0b4-146">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="3d0b4-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
