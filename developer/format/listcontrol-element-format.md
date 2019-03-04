---
title: ListControl 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857459"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="6b683-102">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="6b683-102">ListControl Element (Format)</span></span>

<span data-ttu-id="6b683-103">뷰를 목록 형식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-103">Defines a list format for the view.</span></span>

<span data-ttu-id="6b683-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) ListControl 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="6b683-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6b683-105">구문</span><span class="sxs-lookup"><span data-stu-id="6b683-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="6b683-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="6b683-106">Attributes and Elements</span></span>

<span data-ttu-id="6b683-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ListControl` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="6b683-108">이 요소는 단일 자식 요소만을 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6b683-109">특성</span><span class="sxs-lookup"><span data-stu-id="6b683-109">Attributes</span></span>

<span data-ttu-id="6b683-110">없음</span><span class="sxs-lookup"><span data-stu-id="6b683-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6b683-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="6b683-111">Child Elements</span></span>

|<span data-ttu-id="6b683-112">요소</span><span class="sxs-lookup"><span data-stu-id="6b683-112">Element</span></span>|<span data-ttu-id="6b683-113">설명</span><span class="sxs-lookup"><span data-stu-id="6b683-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b683-114">ListEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="6b683-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="6b683-115">필수 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-115">Required element.</span></span><br /><br /> <span data-ttu-id="6b683-116">목록 보기의 정의 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6b683-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="6b683-117">Parent Elements</span></span>

|<span data-ttu-id="6b683-118">요소</span><span class="sxs-lookup"><span data-stu-id="6b683-118">Element</span></span>|<span data-ttu-id="6b683-119">설명</span><span class="sxs-lookup"><span data-stu-id="6b683-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6b683-120">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="6b683-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="6b683-121">하나 이상의 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6b683-122">설명</span><span class="sxs-lookup"><span data-stu-id="6b683-122">Remarks</span></span>

<span data-ttu-id="6b683-123">목록 뷰를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [목록 뷰를 만들면](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="6b683-124">예제</span><span class="sxs-lookup"><span data-stu-id="6b683-124">Example</span></span>

<span data-ttu-id="6b683-125">이 예제에 대 한 목록 뷰를 표시 합니다 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6b683-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6b683-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b683-126">See Also</span></span>

[<span data-ttu-id="6b683-127">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="6b683-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="6b683-128">ListEntries 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="6b683-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="6b683-129">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="6b683-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6b683-130">Windows PowerShell 형식 지정을 작성 하 고 파일 형식</span><span class="sxs-lookup"><span data-stu-id="6b683-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
