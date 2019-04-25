---
title: ListEntry 요소 ListControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065226"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="0609d-102">ListControl에 대한 ListEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0609d-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="0609d-103">목록 보기의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="0609d-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식) ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0609d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0609d-105">구문</span><span class="sxs-lookup"><span data-stu-id="0609d-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0609d-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0609d-106">Attributes and Elements</span></span>

<span data-ttu-id="0609d-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListEntry` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0609d-108">특성</span><span class="sxs-lookup"><span data-stu-id="0609d-108">Attributes</span></span>

<span data-ttu-id="0609d-109">없음</span><span class="sxs-lookup"><span data-stu-id="0609d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0609d-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0609d-110">Child Elements</span></span>

|<span data-ttu-id="0609d-111">요소</span><span class="sxs-lookup"><span data-stu-id="0609d-111">Element</span></span>|<span data-ttu-id="0609d-112">설명</span><span class="sxs-lookup"><span data-stu-id="0609d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0609d-113">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="0609d-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0609d-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="0609d-115">이 목록 뷰 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0609d-116">ListItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0609d-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0609d-117">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-117">Required element.</span></span><br /><br /> <span data-ttu-id="0609d-118">속성 및 값을 목록 보기에서 표시 하는 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0609d-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0609d-119">Parent Elements</span></span>

|<span data-ttu-id="0609d-120">요소</span><span class="sxs-lookup"><span data-stu-id="0609d-120">Element</span></span>|<span data-ttu-id="0609d-121">설명</span><span class="sxs-lookup"><span data-stu-id="0609d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0609d-122">ListEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0609d-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="0609d-123">목록 보기의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0609d-124">설명</span><span class="sxs-lookup"><span data-stu-id="0609d-124">Remarks</span></span>

<span data-ttu-id="0609d-125">목록 뷰를 목록 형식으로 속성 값 이나 각 개체에 대 한 스크립트 값을 표시 하는 경우</span><span class="sxs-lookup"><span data-stu-id="0609d-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="0609d-126">목록 보기에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0609d-127">예제</span><span class="sxs-lookup"><span data-stu-id="0609d-127">Example</span></span>

<span data-ttu-id="0609d-128">목록 뷰를 정의 하는 XML 요소를 보여 주는이 예제는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="0609d-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0609d-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0609d-129">See Also</span></span>

[<span data-ttu-id="0609d-130">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="0609d-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0609d-131">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="0609d-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0609d-132">ListEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0609d-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="0609d-133">ListItems 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="0609d-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0609d-134">Windows PowerShell 형식 지정을 작성 하 고 파일 형식</span><span class="sxs-lookup"><span data-stu-id="0609d-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
