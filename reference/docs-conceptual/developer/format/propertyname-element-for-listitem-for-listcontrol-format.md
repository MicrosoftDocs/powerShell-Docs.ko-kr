---
title: 이 listcontrol의 ListItem 요소에 대 한 PropertyName 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362382"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="1b3a0-102">ListControl의 ListItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1b3a0-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="1b3a0-103">값이 목록에 표시 되는 .NET 속성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="1b3a0-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry element (format) ListItems Element (format) ListItem 요소 (format) PropertyName 요소 ListItem (형식)</span><span class="sxs-lookup"><span data-stu-id="1b3a0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1b3a0-105">구문</span><span class="sxs-lookup"><span data-stu-id="1b3a0-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1b3a0-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1b3a0-106">Attributes and Elements</span></span>

<span data-ttu-id="1b3a0-107">다음 섹션에서는 특성, 자식 요소 및 `PropertyName` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1b3a0-108">특성</span><span class="sxs-lookup"><span data-stu-id="1b3a0-108">Attributes</span></span>

<span data-ttu-id="1b3a0-109">없음</span><span class="sxs-lookup"><span data-stu-id="1b3a0-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1b3a0-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1b3a0-110">Child Elements</span></span>

<span data-ttu-id="1b3a0-111">없음</span><span class="sxs-lookup"><span data-stu-id="1b3a0-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1b3a0-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1b3a0-112">Parent Elements</span></span>

|<span data-ttu-id="1b3a0-113">요소</span><span class="sxs-lookup"><span data-stu-id="1b3a0-113">Element</span></span>|<span data-ttu-id="1b3a0-114">설명</span><span class="sxs-lookup"><span data-stu-id="1b3a0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1b3a0-115">ListItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="1b3a0-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="1b3a0-116">목록 뷰의 행에 값이 표시 되는 속성이 나 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1b3a0-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1b3a0-117">Text Value</span></span>

<span data-ttu-id="1b3a0-118">값이 표시 되는 속성의 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1b3a0-119">설명</span><span class="sxs-lookup"><span data-stu-id="1b3a0-119">Remarks</span></span>

<span data-ttu-id="1b3a0-120">이 요소를 지정 하면 [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="1b3a0-121">속성 값을 표시 하는 것 외에도 값의 표시를 변경 하는 데 사용할 수 있는 서식 문자열 또는 값에 대 한 레이블을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="1b3a0-122">목록 뷰에서 데이터를 지정 하는 방법에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1b3a0-123">예제</span><span class="sxs-lookup"><span data-stu-id="1b3a0-123">Example</span></span>

<span data-ttu-id="1b3a0-124">다음 예에서는 값이 표시 되는 레이블 및 속성을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b3a0-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="1b3a0-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b3a0-125">See Also</span></span>

[<span data-ttu-id="1b3a0-126">이 listcontrol (형식)의 ListItem 요소에 대 한 ScriptBlock 요소</span><span class="sxs-lookup"><span data-stu-id="1b3a0-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="1b3a0-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="1b3a0-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1b3a0-128">이 listcontrol에 대 한 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1b3a0-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="1b3a0-129">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="1b3a0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
