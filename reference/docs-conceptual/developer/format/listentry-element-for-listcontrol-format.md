---
title: 이 listcontrol에 대 한 ListEntry 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362752"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="5661b-102">ListControl에 대한 ListEntry 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5661b-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="5661b-103">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="5661b-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries Element (format) ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5661b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5661b-105">구문</span><span class="sxs-lookup"><span data-stu-id="5661b-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5661b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5661b-106">Attributes and Elements</span></span>

<span data-ttu-id="5661b-107">다음 섹션에서는 특성, 자식 요소 및 `ListEntry` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5661b-108">특성</span><span class="sxs-lookup"><span data-stu-id="5661b-108">Attributes</span></span>

<span data-ttu-id="5661b-109">없음</span><span class="sxs-lookup"><span data-stu-id="5661b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5661b-110">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5661b-110">Child Elements</span></span>

|<span data-ttu-id="5661b-111">요소</span><span class="sxs-lookup"><span data-stu-id="5661b-111">Element</span></span>|<span data-ttu-id="5661b-112">설명</span><span class="sxs-lookup"><span data-stu-id="5661b-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5661b-113">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="5661b-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="5661b-114">선택적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-114">Optional element.</span></span><br /><br /> <span data-ttu-id="5661b-115">이 목록 뷰 정의를 사용 하는 .NET 개체 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="5661b-116">ListItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5661b-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="5661b-117">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-117">Required element.</span></span><br /><br /> <span data-ttu-id="5661b-118">목록 뷰에서 값이 표시 되는 속성 및 스크립트를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5661b-119">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5661b-119">Parent Elements</span></span>

|<span data-ttu-id="5661b-120">요소</span><span class="sxs-lookup"><span data-stu-id="5661b-120">Element</span></span>|<span data-ttu-id="5661b-121">설명</span><span class="sxs-lookup"><span data-stu-id="5661b-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5661b-122">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5661b-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="5661b-123">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5661b-124">설명</span><span class="sxs-lookup"><span data-stu-id="5661b-124">Remarks</span></span>

<span data-ttu-id="5661b-125">목록 뷰는 각 개체에 대 한 속성 값 또는 스크립트 값을 표시 하는 목록 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="5661b-126">목록 뷰에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5661b-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5661b-127">예제</span><span class="sxs-lookup"><span data-stu-id="5661b-127">Example</span></span>

<span data-ttu-id="5661b-128">이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 목록 뷰를 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5661b-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5661b-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5661b-129">See Also</span></span>

[<span data-ttu-id="5661b-130">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="5661b-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5661b-131">ListEntry (형식)에 대 한 EntrySelectedBy 요소</span><span class="sxs-lookup"><span data-stu-id="5661b-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="5661b-132">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5661b-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="5661b-133">ListItems 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5661b-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="5661b-134">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5661b-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
