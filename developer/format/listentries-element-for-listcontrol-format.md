---
title: ListEntries 요소 ListControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065396"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="f7de6-102">ListControl에 대한 ListEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="f7de6-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="f7de6-103">목록 보기의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="f7de6-104">목록 뷰에 하나 이상의 정의 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="f7de6-105">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식) ListEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f7de6-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7de6-106">구문</span><span class="sxs-lookup"><span data-stu-id="f7de6-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7de6-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f7de6-107">Attributes and Elements</span></span>

<span data-ttu-id="f7de6-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListEntries` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="f7de6-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7de6-110">특성</span><span class="sxs-lookup"><span data-stu-id="f7de6-110">Attributes</span></span>

<span data-ttu-id="f7de6-111">없음</span><span class="sxs-lookup"><span data-stu-id="f7de6-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7de6-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f7de6-112">Child Elements</span></span>

|<span data-ttu-id="f7de6-113">요소</span><span class="sxs-lookup"><span data-stu-id="f7de6-113">Element</span></span>|<span data-ttu-id="f7de6-114">설명</span><span class="sxs-lookup"><span data-stu-id="f7de6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7de6-115">ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f7de6-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="f7de6-116">목록 보기의 정의 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f7de6-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f7de6-117">Parent Elements</span></span>

|<span data-ttu-id="f7de6-118">요소</span><span class="sxs-lookup"><span data-stu-id="f7de6-118">Element</span></span>|<span data-ttu-id="f7de6-119">설명</span><span class="sxs-lookup"><span data-stu-id="f7de6-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7de6-120">ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f7de6-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="f7de6-121">뷰를 목록 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7de6-122">설명</span><span class="sxs-lookup"><span data-stu-id="f7de6-122">Remarks</span></span>

<span data-ttu-id="f7de6-123">목록 보기에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f7de6-124">예제</span><span class="sxs-lookup"><span data-stu-id="f7de6-124">Example</span></span>

<span data-ttu-id="f7de6-125">목록 뷰를 정의 하는 XML 요소를 보여 주는이 예제는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="f7de6-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f7de6-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f7de6-126">See Also</span></span>

[<span data-ttu-id="f7de6-127">ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f7de6-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="f7de6-128">ListEntry 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="f7de6-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="f7de6-129">목록 보기</span><span class="sxs-lookup"><span data-stu-id="f7de6-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f7de6-130">Windows PowerShell 형식 지정을 작성 하 고 파일 형식</span><span class="sxs-lookup"><span data-stu-id="f7de6-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
