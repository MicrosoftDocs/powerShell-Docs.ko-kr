---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 Name 요소(형식)
description: View에 대한 Name 요소(형식)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666463"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="d2a39-103">View에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d2a39-103">Name Element for View (Format)</span></span>

<span data-ttu-id="d2a39-104">뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2a39-104">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="d2a39-105">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="d2a39-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2a39-106">구문</span><span class="sxs-lookup"><span data-stu-id="d2a39-106">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2a39-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="d2a39-107">Attributes and Elements</span></span>

<span data-ttu-id="d2a39-108">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="d2a39-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="d2a39-109">`Name`각 뷰에는 하나의 요소만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2a39-109">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2a39-110">특성</span><span class="sxs-lookup"><span data-stu-id="d2a39-110">Attributes</span></span>

<span data-ttu-id="d2a39-111">없음</span><span class="sxs-lookup"><span data-stu-id="d2a39-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2a39-112">자식 요소</span><span class="sxs-lookup"><span data-stu-id="d2a39-112">Child Elements</span></span>

<span data-ttu-id="d2a39-113">없음</span><span class="sxs-lookup"><span data-stu-id="d2a39-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d2a39-114">부모 요소</span><span class="sxs-lookup"><span data-stu-id="d2a39-114">Parent Elements</span></span>

|<span data-ttu-id="d2a39-115">요소</span><span class="sxs-lookup"><span data-stu-id="d2a39-115">Element</span></span>|<span data-ttu-id="d2a39-116">설명</span><span class="sxs-lookup"><span data-stu-id="d2a39-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2a39-117">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d2a39-117">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="d2a39-118">하나 이상의 .NET 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2a39-118">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d2a39-119">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="d2a39-119">Text Value</span></span>

<span data-ttu-id="d2a39-120">보기의 고유 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2a39-120">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="d2a39-121">이 이름에는 뷰 형식 (예: 테이블 뷰 또는 목록 뷰)에 대 한 참조, 뷰를 사용 하는 개체 또는 개체 집합, 개체를 반환 하는 명령 또는 이러한 항목의 조합이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2a39-121">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="d2a39-122">설명</span><span class="sxs-lookup"><span data-stu-id="d2a39-122">Remarks</span></span>

<span data-ttu-id="d2a39-123">다양 한 보기 유형에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md), [목록 뷰](./creating-a-list-view.md), [넓은 뷰](./creating-a-wide-view.md)및 [사용자 지정 보기](./creating-custom-controls.md)항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2a39-123">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2a39-124">예제</span><span class="sxs-lookup"><span data-stu-id="d2a39-124">Example</span></span>

<span data-ttu-id="d2a39-125">다음 예에서는 `View` [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2a39-125">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="d2a39-126">뷰 이름은 "service"입니다.</span><span class="sxs-lookup"><span data-stu-id="d2a39-126">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="d2a39-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d2a39-127">See Also</span></span>

[<span data-ttu-id="d2a39-128">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d2a39-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d2a39-129">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d2a39-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d2a39-130">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="d2a39-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d2a39-131">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="d2a39-131">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="d2a39-132">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="d2a39-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="d2a39-133">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="d2a39-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
