---
title: Name 요소 (형식) 보기에 대 한 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065073"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="1ed3c-102">View에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="1ed3c-102">Name Element for View (Format)</span></span>

<span data-ttu-id="1ed3c-103">뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="1ed3c-104">구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 이름 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1ed3c-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1ed3c-105">구문</span><span class="sxs-lookup"><span data-stu-id="1ed3c-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1ed3c-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="1ed3c-106">Attributes and Elements</span></span>

<span data-ttu-id="1ed3c-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Name` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="1ed3c-108">하나의 `Name` 각 보기에 대 한 요소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="1ed3c-109">특성</span><span class="sxs-lookup"><span data-stu-id="1ed3c-109">Attributes</span></span>

<span data-ttu-id="1ed3c-110">없음</span><span class="sxs-lookup"><span data-stu-id="1ed3c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1ed3c-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="1ed3c-111">Child Elements</span></span>

<span data-ttu-id="1ed3c-112">없음</span><span class="sxs-lookup"><span data-stu-id="1ed3c-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="1ed3c-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="1ed3c-113">Parent Elements</span></span>

|<span data-ttu-id="1ed3c-114">요소</span><span class="sxs-lookup"><span data-stu-id="1ed3c-114">Element</span></span>|<span data-ttu-id="1ed3c-115">설명</span><span class="sxs-lookup"><span data-stu-id="1ed3c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1ed3c-116">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1ed3c-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="1ed3c-117">하나 이상의.NET 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="1ed3c-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="1ed3c-118">Text Value</span></span>

<span data-ttu-id="1ed3c-119">뷰에 대 한 고유한 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="1ed3c-120">이 이름에는 어떤 개체 또는 개체 집합을 사용 하 여 어떤 명령이 반환 된 개체 또는 이들의 조합으로 뷰를 뷰 (예: 테이블 뷰 또는 목록 보기)의 형식에 대 한 참조를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ed3c-121">설명</span><span class="sxs-lookup"><span data-stu-id="1ed3c-121">Remarks</span></span>

<span data-ttu-id="1ed3c-122">다양 한 보기에 대 한 자세한 내용은 다음 항목을 참조 합니다. [테이블 뷰](./creating-a-table-view.md), [목록 보기](./creating-a-list-view.md), [와이드 보기인](./creating-a-wide-view.md), 및 [사용자 지정 보기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="1ed3c-123">예제</span><span class="sxs-lookup"><span data-stu-id="1ed3c-123">Example</span></span>

<span data-ttu-id="1ed3c-124">에서는 다음 예제는 `View` 테이블 뷰를 정의 하는 요소는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="1ed3c-125">뷰의 이름을 "service"입니다.</span><span class="sxs-lookup"><span data-stu-id="1ed3c-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="1ed3c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ed3c-126">See Also</span></span>

[<span data-ttu-id="1ed3c-127">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="1ed3c-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="1ed3c-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="1ed3c-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="1ed3c-129">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="1ed3c-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1ed3c-130">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="1ed3c-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="1ed3c-131">뷰 요소 (형식)</span><span class="sxs-lookup"><span data-stu-id="1ed3c-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="1ed3c-132">서식 파일을 PowerShell 작성</span><span class="sxs-lookup"><span data-stu-id="1ed3c-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
