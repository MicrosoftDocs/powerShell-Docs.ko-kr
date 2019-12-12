---
title: 이 listcontrol (형식)의 ListItem 요소에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364812"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="06157-102">ListControl의 ListItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="06157-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="06157-103">행에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="06157-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="06157-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한이 listcontrol (format) ListEntry 요소 ListEntries의이 listcontrol (Format) ListItems 요소 이 listcontrol (Format)의 ListItem 요소에 대 한 ListItems for이 listcontrol (format)이 listcontrol 요소에 대 한 for (format) ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="06157-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06157-105">구문</span><span class="sxs-lookup"><span data-stu-id="06157-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06157-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="06157-106">Attributes and Elements</span></span>

<span data-ttu-id="06157-107">다음 섹션에서는 특성, 자식 요소 및 `ScriptBlock` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="06157-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06157-108">특성</span><span class="sxs-lookup"><span data-stu-id="06157-108">Attributes</span></span>

<span data-ttu-id="06157-109">없음</span><span class="sxs-lookup"><span data-stu-id="06157-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06157-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="06157-110">Child Elements</span></span>

<span data-ttu-id="06157-111">없음</span><span class="sxs-lookup"><span data-stu-id="06157-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="06157-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="06157-112">Parent Elements</span></span>

|<span data-ttu-id="06157-113">요소</span><span class="sxs-lookup"><span data-stu-id="06157-113">Element</span></span>|<span data-ttu-id="06157-114">설명</span><span class="sxs-lookup"><span data-stu-id="06157-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06157-115">ListItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="06157-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="06157-116">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="06157-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="06157-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="06157-117">Text Value</span></span>

<span data-ttu-id="06157-118">해당 값이 행에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="06157-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="06157-119">설명</span><span class="sxs-lookup"><span data-stu-id="06157-119">Remarks</span></span>

<span data-ttu-id="06157-120">이 요소를 지정 하면 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="06157-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="06157-121">목록 뷰에서 스크립트를 지정 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="06157-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="06157-122">예제</span><span class="sxs-lookup"><span data-stu-id="06157-122">Example</span></span>

<span data-ttu-id="06157-123">다음 예에서는 값이 표시 되는 속성을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06157-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="06157-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06157-124">See Also</span></span>

[<span data-ttu-id="06157-125">이 listcontrol의 ListItem 요소에 대 한 PropertyName 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="06157-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="06157-126">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="06157-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="06157-127">이 listcontrol에 대 한 ListItems의 ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="06157-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="06157-128">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="06157-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
