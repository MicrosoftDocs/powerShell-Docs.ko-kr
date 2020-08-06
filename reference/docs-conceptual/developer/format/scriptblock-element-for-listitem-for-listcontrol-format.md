---
title: 이 listcontrol (형식)의 ListItem 요소에 대 한 ScriptBlock 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785458"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="19527-102">ListControl의 ListItem에 대한 ScriptBlock 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="19527-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="19527-103">행에 값이 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19527-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="19527-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries 요소에 대 한 ListEntries의 경우이 listcontrol에 대 한 ListItems (format) ListItem 요소의 ListEntry for이 listcontrol (format) 요소</span><span class="sxs-lookup"><span data-stu-id="19527-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="19527-105">구문</span><span class="sxs-lookup"><span data-stu-id="19527-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="19527-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="19527-106">Attributes and Elements</span></span>

<span data-ttu-id="19527-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ScriptBlock` .</span><span class="sxs-lookup"><span data-stu-id="19527-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="19527-108">특성</span><span class="sxs-lookup"><span data-stu-id="19527-108">Attributes</span></span>

<span data-ttu-id="19527-109">없음</span><span class="sxs-lookup"><span data-stu-id="19527-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="19527-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="19527-110">Child Elements</span></span>

<span data-ttu-id="19527-111">없음</span><span class="sxs-lookup"><span data-stu-id="19527-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="19527-112">부모 요소</span><span class="sxs-lookup"><span data-stu-id="19527-112">Parent Elements</span></span>

|<span data-ttu-id="19527-113">요소</span><span class="sxs-lookup"><span data-stu-id="19527-113">Element</span></span>|<span data-ttu-id="19527-114">설명</span><span class="sxs-lookup"><span data-stu-id="19527-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="19527-115">ListItem 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="19527-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="19527-116">목록 뷰의 행에 값이 표시 되는 속성 또는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="19527-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="19527-117">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="19527-117">Text Value</span></span>

<span data-ttu-id="19527-118">해당 값이 행에 표시 되는 스크립트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19527-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="19527-119">설명</span><span class="sxs-lookup"><span data-stu-id="19527-119">Remarks</span></span>

<span data-ttu-id="19527-120">이 요소를 지정 하면 [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소를 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="19527-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="19527-121">목록 뷰에서 스크립트를 지정 하는 방법에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="19527-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="19527-122">예제</span><span class="sxs-lookup"><span data-stu-id="19527-122">Example</span></span>

<span data-ttu-id="19527-123">다음 예에서는 값이 표시 되는 속성을 지정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="19527-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="19527-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19527-124">See Also</span></span>

[<span data-ttu-id="19527-125">ListControl의 ListItem에 대한 PropertyName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="19527-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="19527-126">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="19527-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="19527-127">ListControl의 ListItems에 대한 ListItem 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="19527-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="19527-128">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="19527-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
