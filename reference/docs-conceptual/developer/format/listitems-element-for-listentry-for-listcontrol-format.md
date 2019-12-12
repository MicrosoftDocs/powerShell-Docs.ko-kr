---
title: ListEntry의이 listcontrol 요소에 대 한 ListItems 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362742"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="843f0-102">ListControl의 ListEntry에 대한 ListItems 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="843f0-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="843f0-103">목록 뷰의 행에 값이 표시 되는 속성 및 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="843f0-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View Element (format)이 listcontrol element (format) ListEntries Element for이 listcontrol (format) ListItems Element for이 listcontrol (Format)</span><span class="sxs-lookup"><span data-stu-id="843f0-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="843f0-105">구문</span><span class="sxs-lookup"><span data-stu-id="843f0-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="843f0-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="843f0-106">Attributes and Elements</span></span>

<span data-ttu-id="843f0-107">다음 섹션에서는 `ListItems` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="843f0-108">지정할 수 있는 자식 요소 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="843f0-109">자식 요소의 순서는 목록 보기에 값이 표시 되는 순서를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="843f0-110">특성</span><span class="sxs-lookup"><span data-stu-id="843f0-110">Attributes</span></span>

<span data-ttu-id="843f0-111">없음</span><span class="sxs-lookup"><span data-stu-id="843f0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="843f0-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="843f0-112">Child Elements</span></span>

|<span data-ttu-id="843f0-113">요소</span><span class="sxs-lookup"><span data-stu-id="843f0-113">Element</span></span>|<span data-ttu-id="843f0-114">설명</span><span class="sxs-lookup"><span data-stu-id="843f0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="843f0-115">이 listcontrol에 대 한 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="843f0-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="843f0-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-116">Required element.</span></span><br /><br /> <span data-ttu-id="843f0-117">목록 뷰에서 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="843f0-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="843f0-118">Parent Elements</span></span>

|<span data-ttu-id="843f0-119">요소</span><span class="sxs-lookup"><span data-stu-id="843f0-119">Element</span></span>|<span data-ttu-id="843f0-120">설명</span><span class="sxs-lookup"><span data-stu-id="843f0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="843f0-121">이 listcontrol에 대 한 ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="843f0-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="843f0-122">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="843f0-123">설명</span><span class="sxs-lookup"><span data-stu-id="843f0-123">Remarks</span></span>

<span data-ttu-id="843f0-124">이 유형의 보기에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="843f0-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="843f0-125">예제</span><span class="sxs-lookup"><span data-stu-id="843f0-125">Example</span></span>

<span data-ttu-id="843f0-126">이 예에서는 목록 뷰의 세 행을 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="843f0-126">This example shows the XML elements that define three rows of the list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="843f0-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="843f0-127">See Also</span></span>

[<span data-ttu-id="843f0-128">이 listcontrol에 대 한 ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="843f0-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="843f0-129">이 listcontrol에 대 한 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="843f0-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="843f0-130">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="843f0-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="843f0-131">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="843f0-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
