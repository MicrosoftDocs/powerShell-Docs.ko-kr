---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl에 대한 ListEntry 요소(형식)
description: ListControl에 대한 ListEntry 요소(형식)
ms.openlocfilehash: 96ae5fcdd837d2491d6c7ff6a375fef1d83ae3e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666572"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="0d0ca-103">ListControl에 대한 ListEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0d0ca-103">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="0d0ca-104">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-104">Provides a definition of the list view.</span></span>

<span data-ttu-id="0d0ca-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0d0ca-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0d0ca-106">구문</span><span class="sxs-lookup"><span data-stu-id="0d0ca-106">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0d0ca-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0d0ca-107">Attributes and Elements</span></span>

<span data-ttu-id="0d0ca-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListEntry` .</span><span class="sxs-lookup"><span data-stu-id="0d0ca-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d0ca-109">특성</span><span class="sxs-lookup"><span data-stu-id="0d0ca-109">Attributes</span></span>

<span data-ttu-id="0d0ca-110">없음</span><span class="sxs-lookup"><span data-stu-id="0d0ca-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0d0ca-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0d0ca-111">Child Elements</span></span>

|<span data-ttu-id="0d0ca-112">요소</span><span class="sxs-lookup"><span data-stu-id="0d0ca-112">Element</span></span>|<span data-ttu-id="0d0ca-113">설명</span><span class="sxs-lookup"><span data-stu-id="0d0ca-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d0ca-114">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="0d0ca-114">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0d0ca-115">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0d0ca-116">이 목록 뷰 정의를 사용 하는 .NET 개체 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-116">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0d0ca-117">ListItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0d0ca-117">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0d0ca-118">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-118">Required element.</span></span><br /><br /> <span data-ttu-id="0d0ca-119">목록 뷰에서 값이 표시 되는 속성 및 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-119">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0d0ca-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0d0ca-120">Parent Elements</span></span>

|<span data-ttu-id="0d0ca-121">요소</span><span class="sxs-lookup"><span data-stu-id="0d0ca-121">Element</span></span>|<span data-ttu-id="0d0ca-122">설명</span><span class="sxs-lookup"><span data-stu-id="0d0ca-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0d0ca-123">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0d0ca-123">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="0d0ca-124">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-124">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0d0ca-125">설명</span><span class="sxs-lookup"><span data-stu-id="0d0ca-125">Remarks</span></span>

<span data-ttu-id="0d0ca-126">목록 뷰는 각 개체에 대 한 속성 값 또는 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-126">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="0d0ca-127">목록 뷰에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-127">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d0ca-128">예제</span><span class="sxs-lookup"><span data-stu-id="0d0ca-128">Example</span></span>

<span data-ttu-id="0d0ca-129">이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 목록 뷰를 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d0ca-129">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="0d0ca-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0d0ca-130">See Also</span></span>

[<span data-ttu-id="0d0ca-131">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="0d0ca-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0d0ca-132">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="0d0ca-132">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0d0ca-133">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0d0ca-133">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="0d0ca-134">ListItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0d0ca-134">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0d0ca-135">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="0d0ca-135">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
