---
title: 이 listcontrol 요소 (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 0173b9797bffcca74f1a32903686f771366ebb1b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785730"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="81822-102">ListControl 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="81822-102">ListControl Element (Format)</span></span>

<span data-ttu-id="81822-103">뷰의 목록 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="81822-103">Defines a list format for the view.</span></span>

<span data-ttu-id="81822-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="81822-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="81822-105">구문</span><span class="sxs-lookup"><span data-stu-id="81822-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="81822-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="81822-106">Attributes and Elements</span></span>

<span data-ttu-id="81822-107">다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListControl` .</span><span class="sxs-lookup"><span data-stu-id="81822-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="81822-108">이 요소는 자식 요소를 하나만 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81822-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="81822-109">특성</span><span class="sxs-lookup"><span data-stu-id="81822-109">Attributes</span></span>

<span data-ttu-id="81822-110">없음</span><span class="sxs-lookup"><span data-stu-id="81822-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="81822-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="81822-111">Child Elements</span></span>

|<span data-ttu-id="81822-112">요소</span><span class="sxs-lookup"><span data-stu-id="81822-112">Element</span></span>|<span data-ttu-id="81822-113">설명</span><span class="sxs-lookup"><span data-stu-id="81822-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81822-114">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="81822-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="81822-115">필수적 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="81822-115">Required element.</span></span><br /><br /> <span data-ttu-id="81822-116">목록 뷰의 정의를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="81822-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="81822-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="81822-117">Parent Elements</span></span>

|<span data-ttu-id="81822-118">요소</span><span class="sxs-lookup"><span data-stu-id="81822-118">Element</span></span>|<span data-ttu-id="81822-119">설명</span><span class="sxs-lookup"><span data-stu-id="81822-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="81822-120">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="81822-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="81822-121">하나 이상의 개체 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="81822-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="81822-122">설명</span><span class="sxs-lookup"><span data-stu-id="81822-122">Remarks</span></span>

<span data-ttu-id="81822-123">목록 뷰를 만드는 방법에 대 한 자세한 내용은 [목록 뷰 만들기](./creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="81822-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="81822-124">예제</span><span class="sxs-lookup"><span data-stu-id="81822-124">Example</span></span>

<span data-ttu-id="81822-125">이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 목록 뷰를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81822-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="81822-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="81822-126">See Also</span></span>

[<span data-ttu-id="81822-127">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="81822-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="81822-128">ListEntries 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="81822-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="81822-129">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="81822-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="81822-130">Windows PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="81822-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
