---
title: View의 Name 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a31010d-1db9-44ae-a7f3-6ed32cb641cb
caps.latest.revision: 16
ms.openlocfilehash: 097d20cb6a04635124d1f96823248df6095ca1af
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72362642"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="5d7d3-102">View에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="5d7d3-102">Name Element for View (Format)</span></span>

<span data-ttu-id="5d7d3-103">뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="5d7d3-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5d7d3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5d7d3-105">구문</span><span class="sxs-lookup"><span data-stu-id="5d7d3-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5d7d3-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="5d7d3-106">Attributes and Elements</span></span>

<span data-ttu-id="5d7d3-107">다음 섹션에서는 특성, 자식 요소 및 `Name` 요소의 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="5d7d3-108">각 뷰에는 하나의 `Name` 요소만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="5d7d3-109">특성</span><span class="sxs-lookup"><span data-stu-id="5d7d3-109">Attributes</span></span>

<span data-ttu-id="5d7d3-110">없음</span><span class="sxs-lookup"><span data-stu-id="5d7d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5d7d3-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="5d7d3-111">Child Elements</span></span>

<span data-ttu-id="5d7d3-112">없음</span><span class="sxs-lookup"><span data-stu-id="5d7d3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5d7d3-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="5d7d3-113">Parent Elements</span></span>

|<span data-ttu-id="5d7d3-114">요소</span><span class="sxs-lookup"><span data-stu-id="5d7d3-114">Element</span></span>|<span data-ttu-id="5d7d3-115">설명</span><span class="sxs-lookup"><span data-stu-id="5d7d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5d7d3-116">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5d7d3-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5d7d3-117">하나 이상의 .NET 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5d7d3-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="5d7d3-118">Text Value</span></span>

<span data-ttu-id="5d7d3-119">보기의 고유 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="5d7d3-120">이 이름에는 뷰 형식 (예: 테이블 뷰 또는 목록 뷰)에 대 한 참조, 뷰를 사용 하는 개체 또는 개체 집합, 개체를 반환 하는 명령 또는 이러한 항목의 조합이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d7d3-121">설명</span><span class="sxs-lookup"><span data-stu-id="5d7d3-121">Remarks</span></span>

<span data-ttu-id="5d7d3-122">다양 한 보기 유형에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md), [목록 뷰](./creating-a-list-view.md), [넓은 뷰](./creating-a-wide-view.md)및 [사용자 지정 보기](./creating-custom-controls.md)항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="5d7d3-123">예제</span><span class="sxs-lookup"><span data-stu-id="5d7d3-123">Example</span></span>

<span data-ttu-id="5d7d3-124">다음 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 `View` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="5d7d3-125">뷰 이름은 "service"입니다.</span><span class="sxs-lookup"><span data-stu-id="5d7d3-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="5d7d3-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5d7d3-126">See Also</span></span>

[<span data-ttu-id="5d7d3-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="5d7d3-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5d7d3-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="5d7d3-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5d7d3-129">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="5d7d3-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="5d7d3-130">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="5d7d3-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="5d7d3-131">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="5d7d3-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5d7d3-132">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="5d7d3-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
