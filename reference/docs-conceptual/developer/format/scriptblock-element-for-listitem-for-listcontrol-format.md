---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl의 ListItem에 대한 ScriptBlock 요소(형식)
description: ListControl의 ListItem에 대한 ScriptBlock 요소(형식)
ms.openlocfilehash: 0635ac2622cc203a2dc895873621901d956f87da
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664973"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="490e7-103">ListControl의 ListItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="490e7-103">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="490e7-104">행에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="490e7-104">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="490e7-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한 ListEntries의 경우이 listcontrol에 대 한 ListItems (format) ListItem 요소의 ListEntry for이 listcontrol (format) 요소</span><span class="sxs-lookup"><span data-stu-id="490e7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="490e7-106">구문</span><span class="sxs-lookup"><span data-stu-id="490e7-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="490e7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="490e7-107">Attributes and Elements</span></span>

<span data-ttu-id="490e7-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="490e7-108">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="490e7-109">특성</span><span class="sxs-lookup"><span data-stu-id="490e7-109">Attributes</span></span>

<span data-ttu-id="490e7-110">없음</span><span class="sxs-lookup"><span data-stu-id="490e7-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="490e7-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="490e7-111">Child Elements</span></span>

<span data-ttu-id="490e7-112">없음</span><span class="sxs-lookup"><span data-stu-id="490e7-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="490e7-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="490e7-113">Parent Elements</span></span>

|<span data-ttu-id="490e7-114">요소</span><span class="sxs-lookup"><span data-stu-id="490e7-114">Element</span></span>|<span data-ttu-id="490e7-115">설명</span><span class="sxs-lookup"><span data-stu-id="490e7-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="490e7-116">ListItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="490e7-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="490e7-117">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="490e7-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="490e7-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="490e7-118">Text Value</span></span>

<span data-ttu-id="490e7-119">해당 값이 행에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="490e7-119">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="490e7-120">설명</span><span class="sxs-lookup"><span data-stu-id="490e7-120">Remarks</span></span>

<span data-ttu-id="490e7-121">이 요소를 지정 하면 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="490e7-121">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="490e7-122">목록 뷰에서 스크립트를 지정 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="490e7-122">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="490e7-123">예제</span><span class="sxs-lookup"><span data-stu-id="490e7-123">Example</span></span>

<span data-ttu-id="490e7-124">다음 예에서는 값이 표시 되는 속성을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="490e7-124">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="490e7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="490e7-125">See Also</span></span>

[<span data-ttu-id="490e7-126">ListControl의 ListItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="490e7-126">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="490e7-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="490e7-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="490e7-128">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="490e7-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="490e7-129">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="490e7-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
