---
ms.date: 09/13/2016
ms.topic: reference
title: 형식 지정 파일 사용자 지정
description: 형식 지정 파일 사용자 지정
ms.openlocfilehash: 16e1c1046e25b35ff346585a5fd930c449c04bf8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92653250"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="3aea9-103">형식 지정 파일 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="3aea9-103">Custom Formatting Files</span></span>

<span data-ttu-id="3aea9-104">Cmdlet, 함수 및 스크립트가 반환 하는 개체에 대 한 표시 형식은 형식 지정 파일 (format.ps1xml 파일)을 사용 하 여 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-104">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="3aea9-105">이러한 파일 중 일부는 windows powershell cmdlet에서 반환 되는 개체에 대 한 기본 표시 형식을 정의 하기 위해 Windows PowerShell에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-105">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="3aea9-106">그러나 사용자 고유의 사용자 지정 서식 파일을 만들어 기본 표시 형식을 덮어쓰거나 사용자의 명령으로 반환 되는 개체의 표시를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-106">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="3aea9-107">Windows PowerShell은 이러한 서식 지정 파일의 데이터를 사용 하 여 표시 되는 내용과 데이터의 형식 지정 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-107">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="3aea9-108">표시 되는 데이터에는 개체의 속성 또는 스크립트 블록의 값이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-108">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="3aea9-109">스크립트 블록은 개체의 속성에서 직접 사용할 수 없는 일부 값을 표시 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-109">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="3aea9-110">예를 들어 개체의 두 속성 값을 추가 하 고 합계를 별도의 데이터로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-110">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="3aea9-111">사용자 고유의 서식 지정 파일을 작성 하는 경우 표시할 개체에 대 한 *보기* 를 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-111">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="3aea9-112">각 개체에 대해 단일 뷰를 정의 하거나, 여러 개체에 대해 단일 뷰를 정의 하거나, 동일한 개체에 대해 여러 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="3aea9-113">정의할 수 있는 뷰 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-113">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3aea9-114">파일 서식 지정은 파이프라인에 반환 되는 개체의 요소를 결정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-114">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="3aea9-115">개체가 파이프라인으로 반환 되 면 해당 개체의 모든 멤버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-115">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="3aea9-116">뷰 서식</span><span class="sxs-lookup"><span data-stu-id="3aea9-116">Format Views</span></span>

<span data-ttu-id="3aea9-117">서식 보기에서는 개체를 테이블 형식으로 표시 하 고, 목록 형식, 너비를 지정 하 고, 사용자 지정 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-117">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="3aea9-118">대부분의 경우 각 서식 정의는 뷰를 설명 하는 XML 태그 집합으로 설명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-118">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="3aea9-119">각 뷰에는 뷰 이름, 뷰를 사용 하는 개체 및 뷰의 요소 (예: 테이블 뷰의 열 및 행 정보)가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-119">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="3aea9-120">다음 뷰를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-120">The following views are available.</span></span>

<span data-ttu-id="3aea9-121">테이블 뷰 하나 이상의 열에 있는 개체 또는 스크립트 블록 값의 속성을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-121">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="3aea9-122">각 열은 개체의 속성 또는 스크립트 블록 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-122">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="3aea9-123">개체의 모든 속성, 개체 속성의 하위 집합 또는 속성 및 스크립트 블록 값의 조합을 표시 하는 테이블 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-123">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="3aea9-124">테이블의 각 행은 반환 된 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-124">Each row of the table represents a returned object.</span></span> <span data-ttu-id="3aea9-125">이 보기에 대 한 자세한 내용은 [테이블 뷰](../format/creating-a-table-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3aea9-125">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="3aea9-126">목록 뷰 단일 열에 개체 또는 스크립트 블록 값의 속성을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-126">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="3aea9-127">목록의 각 행에는 선택적 레이블 또는 속성 이름과 속성 또는 스크립트 블록 값이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-127">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="3aea9-128">이 보기에 대 한 자세한 내용은 [목록 뷰](../format/creating-a-list-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3aea9-128">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="3aea9-129">넓은 뷰 하나 이상의 열에 있는 단일 개체 속성 또는 스크립트 블록 값을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-129">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="3aea9-130">이 보기에 대 한 레이블이나 머리글이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-130">There is no label or header for this view.</span></span> <span data-ttu-id="3aea9-131">이 보기에 대 한 자세한 내용은 [Wide view](../format/creating-a-wide-view.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3aea9-131">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="3aea9-132">사용자 지정 뷰는 테이블 뷰, 목록 뷰 또는 넓은 보기의 고정 구조를 따르지 않는 개체 속성 또는 스크립트 블록 값의 사용자 지정 가능한 뷰를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-132">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="3aea9-133">독립 실행형 사용자 지정 보기를 정의 하거나, 다른 보기에서 사용 되는 사용자 지정 보기 (예: 테이블 뷰 또는 목록 보기)를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-133">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="3aea9-134">이 보기에 대 한 자세한 내용은 [사용자 지정 뷰](../format/creating-custom-controls.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3aea9-134">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="3aea9-135">XML 요소 보기</span><span class="sxs-lookup"><span data-stu-id="3aea9-135">View XML Elements</span></span>

<span data-ttu-id="3aea9-136">다음 예에서는 두 개의 열이 포함 된 테이블 뷰를 정의 하는 데 사용 되는 XML 태그를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-136">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="3aea9-137">[Viewdefinitions](../format/viewdefinitions-element-format.md) 요소는 서식 파일에 정의 된 모든 뷰에 대 한 컨테이너 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-137">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="3aea9-138">[View](../format/view-element-format.md) 요소는 특정 테이블, 목록, 전체 또는 사용자 지정 뷰를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-138">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="3aea9-139">각 뷰 내에서 [name](../format/name-element-for-view-format.md) 요소는 뷰의 이름을 지정 하 고 [viewselectedby](../format/viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 하며 요소와 같은 다른 컨트롤 요소는 `TableControl` 뷰의 형식을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3aea9-139">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="3aea9-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3aea9-140">See Also</span></span>

[<span data-ttu-id="3aea9-141">테이블 보기</span><span class="sxs-lookup"><span data-stu-id="3aea9-141">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="3aea9-142">목록 보기</span><span class="sxs-lookup"><span data-stu-id="3aea9-142">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="3aea9-143">넓은 보기</span><span class="sxs-lookup"><span data-stu-id="3aea9-143">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="3aea9-144">사용자 지정 보기</span><span class="sxs-lookup"><span data-stu-id="3aea9-144">Custom View</span></span>](../format/creating-custom-controls.md)

<span data-ttu-id="3aea9-145">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)(Windows PowerShell Cmdlet 작성)</span><span class="sxs-lookup"><span data-stu-id="3aea9-145">[Writing a Windows PowerShell Cmdlet](./writing-a-windows-powershell-cmdlet.md)</span></span>
