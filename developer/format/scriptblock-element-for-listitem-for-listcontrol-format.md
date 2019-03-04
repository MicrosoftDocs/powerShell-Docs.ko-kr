---
title: ScriptBlock ListControl (형식)에 대 한 ListItem 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855559"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="774cb-102">ListControl의 ListItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="774cb-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="774cb-103">행에 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="774cb-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="774cb-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 ListEntries ListEntry ListItems 요소 ListControl (형식)에 대 한 (형식) ListControl ListEntry 요소에 ListItems ListControl (형식)에 대 한 ListItem ScriptBlock 요소 ListControl (형식)에 대 한 (형식) ListControl ListItem 요소에</span><span class="sxs-lookup"><span data-stu-id="774cb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="774cb-105">구문</span><span class="sxs-lookup"><span data-stu-id="774cb-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="774cb-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="774cb-106">Attributes and Elements</span></span>

<span data-ttu-id="774cb-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ScriptBlock` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="774cb-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="774cb-108">특성</span><span class="sxs-lookup"><span data-stu-id="774cb-108">Attributes</span></span>

<span data-ttu-id="774cb-109">없음</span><span class="sxs-lookup"><span data-stu-id="774cb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="774cb-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="774cb-110">Child Elements</span></span>

<span data-ttu-id="774cb-111">없음</span><span class="sxs-lookup"><span data-stu-id="774cb-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="774cb-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="774cb-112">Parent Elements</span></span>

|<span data-ttu-id="774cb-113">요소</span><span class="sxs-lookup"><span data-stu-id="774cb-113">Element</span></span>|<span data-ttu-id="774cb-114">설명</span><span class="sxs-lookup"><span data-stu-id="774cb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="774cb-115">ListItem 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="774cb-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="774cb-116">속성 또는 목록 보기 행에 해당 값이 표시 되는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="774cb-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="774cb-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="774cb-117">Text Value</span></span>

<span data-ttu-id="774cb-118">행에 해당 값이 표시 하는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="774cb-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="774cb-119">설명</span><span class="sxs-lookup"><span data-stu-id="774cb-119">Remarks</span></span>

<span data-ttu-id="774cb-120">이 요소를 지정 하는 경우 지정할 수 없습니다는 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="774cb-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="774cb-121">목록 보기에서 스크립트를 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="774cb-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="774cb-122">예제</span><span class="sxs-lookup"><span data-stu-id="774cb-122">Example</span></span>

<span data-ttu-id="774cb-123">다음 예제에서는 값이 표시 되는 속성을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="774cb-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="774cb-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="774cb-124">See Also</span></span>

[<span data-ttu-id="774cb-125">PropertyName ListControl (형식)에 대 한 ListItem 요소</span><span class="sxs-lookup"><span data-stu-id="774cb-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="774cb-126">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="774cb-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="774cb-127">ListItem 요소 ListItems ListControl (형식)에 대 한</span><span class="sxs-lookup"><span data-stu-id="774cb-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="774cb-128">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="774cb-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
