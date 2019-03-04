---
title: PropertyName ListControl (형식)에 대 한 ListItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855739"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="e1f84-102">ListControl의 ListItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="e1f84-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="e1f84-103">값 목록에 표시 되는.NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="e1f84-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식) ListItems 요소 (형식) ListItem 요소 (형식) PropertyName 요소에 대 한 ListItem (형식)</span><span class="sxs-lookup"><span data-stu-id="e1f84-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e1f84-105">구문</span><span class="sxs-lookup"><span data-stu-id="e1f84-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1f84-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e1f84-106">Attributes and Elements</span></span>

<span data-ttu-id="e1f84-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `PropertyName` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e1f84-108">특성</span><span class="sxs-lookup"><span data-stu-id="e1f84-108">Attributes</span></span>

<span data-ttu-id="e1f84-109">없음</span><span class="sxs-lookup"><span data-stu-id="e1f84-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e1f84-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e1f84-110">Child Elements</span></span>

<span data-ttu-id="e1f84-111">없음</span><span class="sxs-lookup"><span data-stu-id="e1f84-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e1f84-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e1f84-112">Parent Elements</span></span>

|<span data-ttu-id="e1f84-113">요소</span><span class="sxs-lookup"><span data-stu-id="e1f84-113">Element</span></span>|<span data-ttu-id="e1f84-114">설명</span><span class="sxs-lookup"><span data-stu-id="e1f84-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e1f84-115">ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="e1f84-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e1f84-116">속성 또는 목록 뷰의 행에 해당 값이 표시 되는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e1f84-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="e1f84-117">Text Value</span></span>

<span data-ttu-id="e1f84-118">값은 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1f84-119">설명</span><span class="sxs-lookup"><span data-stu-id="e1f84-119">Remarks</span></span>

<span data-ttu-id="e1f84-120">이 요소를 지정 하는 경우 지정할 수 없습니다는 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="e1f84-121">속성 값을 표시 하는 것 외에도 값 또는 값의 표시를 변경 하는 형식 문자열에 대 한 레이블을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="e1f84-122">목록 뷰에서 데이터를 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e1f84-123">예제</span><span class="sxs-lookup"><span data-stu-id="e1f84-123">Example</span></span>

<span data-ttu-id="e1f84-124">다음 예에서는 레이블 및 해당 값이 표시 하는 속성을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e1f84-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="e1f84-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1f84-125">See Also</span></span>

[<span data-ttu-id="e1f84-126">ScriptBlock ListControl (형식)에 대 한 ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="e1f84-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="e1f84-127">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="e1f84-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e1f84-128">ListControl(Format) ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="e1f84-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e1f84-129">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="e1f84-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
