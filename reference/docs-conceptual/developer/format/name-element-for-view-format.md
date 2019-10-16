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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362642"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="50b8e-102">View에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="50b8e-102">Name Element for View (Format)</span></span>

<span data-ttu-id="50b8e-103">뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="50b8e-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="50b8e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="50b8e-105">구문</span><span class="sxs-lookup"><span data-stu-id="50b8e-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="50b8e-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="50b8e-106">Attributes and Elements</span></span>

<span data-ttu-id="50b8e-107">다음 섹션에서는 `Name` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="50b8e-108">각 뷰에는 하나의 `Name` 요소만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="50b8e-109">특성</span><span class="sxs-lookup"><span data-stu-id="50b8e-109">Attributes</span></span>

<span data-ttu-id="50b8e-110">없음</span><span class="sxs-lookup"><span data-stu-id="50b8e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="50b8e-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="50b8e-111">Child Elements</span></span>

<span data-ttu-id="50b8e-112">없음</span><span class="sxs-lookup"><span data-stu-id="50b8e-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="50b8e-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="50b8e-113">Parent Elements</span></span>

|<span data-ttu-id="50b8e-114">요소</span><span class="sxs-lookup"><span data-stu-id="50b8e-114">Element</span></span>|<span data-ttu-id="50b8e-115">설명</span><span class="sxs-lookup"><span data-stu-id="50b8e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50b8e-116">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="50b8e-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="50b8e-117">하나 이상의 .NET 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="50b8e-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="50b8e-118">Text Value</span></span>

<span data-ttu-id="50b8e-119">보기의 고유 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="50b8e-120">이 이름에는 뷰 형식 (예: 테이블 뷰 또는 목록 뷰)에 대 한 참조, 뷰를 사용 하는 개체 또는 개체 집합, 개체를 반환 하는 명령 또는 이러한 항목의 조합이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="50b8e-121">설명</span><span class="sxs-lookup"><span data-stu-id="50b8e-121">Remarks</span></span>

<span data-ttu-id="50b8e-122">다양 한 보기 유형에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md), [목록 뷰](./creating-a-list-view.md), [넓은 뷰](./creating-a-wide-view.md)및 [사용자 지정 보기](./creating-custom-controls.md)항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="50b8e-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="50b8e-123">예제</span><span class="sxs-lookup"><span data-stu-id="50b8e-123">Example</span></span>

<span data-ttu-id="50b8e-124">다음 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 `View` 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="50b8e-125">뷰 이름은 "service"입니다.</span><span class="sxs-lookup"><span data-stu-id="50b8e-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="50b8e-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="50b8e-126">See Also</span></span>

[<span data-ttu-id="50b8e-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="50b8e-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="50b8e-128">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="50b8e-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="50b8e-129">넓은 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="50b8e-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="50b8e-130">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="50b8e-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="50b8e-131">View 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="50b8e-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="50b8e-132">PowerShell 서식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="50b8e-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
