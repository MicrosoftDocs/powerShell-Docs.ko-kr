---
title: View의 Name 요소 (Format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670b089f850fa4b39b7b100ca1e1ce45b05ea72d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773235"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="ef1a8-102">View에 대한 Name 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ef1a8-102">Name Element for View (Format)</span></span>

<span data-ttu-id="ef1a8-103">뷰를 식별 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="ef1a8-104">Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) Name 요소 (Format)</span><span class="sxs-lookup"><span data-stu-id="ef1a8-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef1a8-105">구문</span><span class="sxs-lookup"><span data-stu-id="ef1a8-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef1a8-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="ef1a8-106">Attributes and Elements</span></span>

<span data-ttu-id="ef1a8-107">다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="ef1a8-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="ef1a8-108">`Name`각 뷰에는 하나의 요소만 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef1a8-109">특성</span><span class="sxs-lookup"><span data-stu-id="ef1a8-109">Attributes</span></span>

<span data-ttu-id="ef1a8-110">없음</span><span class="sxs-lookup"><span data-stu-id="ef1a8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef1a8-111">자식 요소</span><span class="sxs-lookup"><span data-stu-id="ef1a8-111">Child Elements</span></span>

<span data-ttu-id="ef1a8-112">없음</span><span class="sxs-lookup"><span data-stu-id="ef1a8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef1a8-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="ef1a8-113">Parent Elements</span></span>

|<span data-ttu-id="ef1a8-114">요소</span><span class="sxs-lookup"><span data-stu-id="ef1a8-114">Element</span></span>|<span data-ttu-id="ef1a8-115">설명</span><span class="sxs-lookup"><span data-stu-id="ef1a8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef1a8-116">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ef1a8-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ef1a8-117">하나 이상의 .NET 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ef1a8-118">텍스트 값</span><span class="sxs-lookup"><span data-stu-id="ef1a8-118">Text Value</span></span>

<span data-ttu-id="ef1a8-119">보기의 고유 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="ef1a8-120">이 이름에는 뷰 형식 (예: 테이블 뷰 또는 목록 뷰)에 대 한 참조, 뷰를 사용 하는 개체 또는 개체 집합, 개체를 반환 하는 명령 또는 이러한 항목의 조합이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef1a8-121">설명</span><span class="sxs-lookup"><span data-stu-id="ef1a8-121">Remarks</span></span>

<span data-ttu-id="ef1a8-122">다양 한 보기 유형에 대 한 자세한 내용은 [테이블 뷰](./creating-a-table-view.md), [목록 뷰](./creating-a-list-view.md), [넓은 뷰](./creating-a-wide-view.md)및 [사용자 지정 보기](./creating-custom-controls.md)항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="ef1a8-123">예제</span><span class="sxs-lookup"><span data-stu-id="ef1a8-123">Example</span></span>

<span data-ttu-id="ef1a8-124">다음 예에서는 `View` [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="ef1a8-125">뷰 이름은 "service"입니다.</span><span class="sxs-lookup"><span data-stu-id="ef1a8-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="ef1a8-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef1a8-126">See Also</span></span>

[<span data-ttu-id="ef1a8-127">목록 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ef1a8-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ef1a8-128">테이블 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ef1a8-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ef1a8-129">넓게 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="ef1a8-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ef1a8-130">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="ef1a8-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ef1a8-131">View 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="ef1a8-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ef1a8-132">PowerShell 형식 지정 파일 작성</span><span class="sxs-lookup"><span data-stu-id="ef1a8-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
