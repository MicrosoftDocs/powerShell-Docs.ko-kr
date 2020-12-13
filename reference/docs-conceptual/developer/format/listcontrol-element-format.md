---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl 요소(형식)
description: ListControl 요소(형식)
ms.openlocfilehash: cd5687ac8e94e2245d1ae2de8b2206185e5b8ca4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666589"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="a39b7-103">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a39b7-103">ListControl Element (Format)</span></span>

<span data-ttu-id="a39b7-104">뷰의 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39b7-104">Defines a list format for the view.</span></span>

<span data-ttu-id="a39b7-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a39b7-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a39b7-106">구문</span><span class="sxs-lookup"><span data-stu-id="a39b7-106">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="a39b7-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="a39b7-107">Attributes and Elements</span></span>

<span data-ttu-id="a39b7-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListControl` .</span><span class="sxs-lookup"><span data-stu-id="a39b7-108">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="a39b7-109">이 요소는 자식 요소를 하나만 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39b7-109">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a39b7-110">특성</span><span class="sxs-lookup"><span data-stu-id="a39b7-110">Attributes</span></span>

<span data-ttu-id="a39b7-111">없음</span><span class="sxs-lookup"><span data-stu-id="a39b7-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a39b7-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="a39b7-112">Child Elements</span></span>

|<span data-ttu-id="a39b7-113">요소</span><span class="sxs-lookup"><span data-stu-id="a39b7-113">Element</span></span>|<span data-ttu-id="a39b7-114">설명</span><span class="sxs-lookup"><span data-stu-id="a39b7-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a39b7-115">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a39b7-115">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="a39b7-116">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a39b7-116">Required element.</span></span><br /><br /> <span data-ttu-id="a39b7-117">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39b7-117">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a39b7-118">부모 요소</span><span class="sxs-lookup"><span data-stu-id="a39b7-118">Parent Elements</span></span>

|<span data-ttu-id="a39b7-119">요소</span><span class="sxs-lookup"><span data-stu-id="a39b7-119">Element</span></span>|<span data-ttu-id="a39b7-120">설명</span><span class="sxs-lookup"><span data-stu-id="a39b7-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a39b7-121">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a39b7-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="a39b7-122">하나 이상의 개체 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="a39b7-122">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a39b7-123">설명</span><span class="sxs-lookup"><span data-stu-id="a39b7-123">Remarks</span></span>

<span data-ttu-id="a39b7-124">목록 뷰를 만드는 방법에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a39b7-124">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a39b7-125">예제</span><span class="sxs-lookup"><span data-stu-id="a39b7-125">Example</span></span>

<span data-ttu-id="a39b7-126">이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 목록 뷰를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a39b7-126">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="a39b7-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a39b7-127">See Also</span></span>

[<span data-ttu-id="a39b7-128">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="a39b7-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="a39b7-129">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="a39b7-129">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="a39b7-130">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="a39b7-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a39b7-131">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="a39b7-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
