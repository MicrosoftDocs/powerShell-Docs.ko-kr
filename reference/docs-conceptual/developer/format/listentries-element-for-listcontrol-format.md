---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl에 대한 ListEntries 요소(형식)
description: ListControl에 대한 ListEntries 요소(형식)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666606"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="0e490-103">ListControl에 대한 ListEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0e490-103">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="0e490-104">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e490-104">Provides the definitions of the list view.</span></span> <span data-ttu-id="0e490-105">목록 뷰에서 하나 이상의 정의를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e490-105">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="0e490-106">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0e490-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0e490-107">구문</span><span class="sxs-lookup"><span data-stu-id="0e490-107">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0e490-108">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="0e490-108">Attributes and Elements</span></span>

<span data-ttu-id="0e490-109">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListEntries` .</span><span class="sxs-lookup"><span data-stu-id="0e490-109">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="0e490-110">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e490-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="0e490-111">특성</span><span class="sxs-lookup"><span data-stu-id="0e490-111">Attributes</span></span>

<span data-ttu-id="0e490-112">없음</span><span class="sxs-lookup"><span data-stu-id="0e490-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0e490-113">자식 요소</span><span class="sxs-lookup"><span data-stu-id="0e490-113">Child Elements</span></span>

|<span data-ttu-id="0e490-114">요소</span><span class="sxs-lookup"><span data-stu-id="0e490-114">Element</span></span>|<span data-ttu-id="0e490-115">설명</span><span class="sxs-lookup"><span data-stu-id="0e490-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e490-116">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0e490-116">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="0e490-117">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e490-117">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0e490-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="0e490-118">Parent Elements</span></span>

|<span data-ttu-id="0e490-119">요소</span><span class="sxs-lookup"><span data-stu-id="0e490-119">Element</span></span>|<span data-ttu-id="0e490-120">설명</span><span class="sxs-lookup"><span data-stu-id="0e490-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0e490-121">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0e490-121">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="0e490-122">뷰의 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="0e490-122">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0e490-123">설명</span><span class="sxs-lookup"><span data-stu-id="0e490-123">Remarks</span></span>

<span data-ttu-id="0e490-124">목록 뷰에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0e490-124">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0e490-125">예제</span><span class="sxs-lookup"><span data-stu-id="0e490-125">Example</span></span>

<span data-ttu-id="0e490-126">이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 목록 뷰를 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0e490-126">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0e490-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0e490-127">See Also</span></span>

[<span data-ttu-id="0e490-128">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="0e490-128">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="0e490-129">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="0e490-129">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="0e490-130">목록 보기</span><span class="sxs-lookup"><span data-stu-id="0e490-130">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0e490-131">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="0e490-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
