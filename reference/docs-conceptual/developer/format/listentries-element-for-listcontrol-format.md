---
title: 이 listcontrol에 대 한 ListEntries 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0fe07e739c2d2fec153599ec6c0c0b3ecc14df18
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785713"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="cd2bd-102">ListControl에 대한 ListEntries 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cd2bd-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="cd2bd-103">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2bd-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="cd2bd-104">목록 뷰에서 하나 이상의 정의를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2bd-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="cd2bd-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="cd2bd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cd2bd-106">구문</span><span class="sxs-lookup"><span data-stu-id="cd2bd-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cd2bd-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="cd2bd-107">Attributes and Elements</span></span>

<span data-ttu-id="cd2bd-108">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListEntries` .</span><span class="sxs-lookup"><span data-stu-id="cd2bd-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="cd2bd-109">하나 이상의 자식 요소를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2bd-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd2bd-110">특성</span><span class="sxs-lookup"><span data-stu-id="cd2bd-110">Attributes</span></span>

<span data-ttu-id="cd2bd-111">없음</span><span class="sxs-lookup"><span data-stu-id="cd2bd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cd2bd-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="cd2bd-112">Child Elements</span></span>

|<span data-ttu-id="cd2bd-113">요소</span><span class="sxs-lookup"><span data-stu-id="cd2bd-113">Element</span></span>|<span data-ttu-id="cd2bd-114">설명</span><span class="sxs-lookup"><span data-stu-id="cd2bd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd2bd-115">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="cd2bd-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="cd2bd-116">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2bd-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cd2bd-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="cd2bd-117">Parent Elements</span></span>

|<span data-ttu-id="cd2bd-118">요소</span><span class="sxs-lookup"><span data-stu-id="cd2bd-118">Element</span></span>|<span data-ttu-id="cd2bd-119">설명</span><span class="sxs-lookup"><span data-stu-id="cd2bd-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cd2bd-120">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cd2bd-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="cd2bd-121">뷰의 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd2bd-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cd2bd-122">설명</span><span class="sxs-lookup"><span data-stu-id="cd2bd-122">Remarks</span></span>

<span data-ttu-id="cd2bd-123">목록 뷰에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cd2bd-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cd2bd-124">예제</span><span class="sxs-lookup"><span data-stu-id="cd2bd-124">Example</span></span>

<span data-ttu-id="cd2bd-125">이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 목록 뷰를 정의 하는 XML 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="cd2bd-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cd2bd-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cd2bd-126">See Also</span></span>

[<span data-ttu-id="cd2bd-127">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="cd2bd-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="cd2bd-128">ListEntry 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="cd2bd-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="cd2bd-129">목록 보기</span><span class="sxs-lookup"><span data-stu-id="cd2bd-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cd2bd-130">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="cd2bd-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
