---
title: 형식 지정 파일 개요 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fe888fee-1fe9-459f-9d62-35732c19a7f8
caps.latest.revision: 13
ms.openlocfilehash: d418cff70c1197aa3c331eed909f49198da139e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863299"
---
# <a name="formatting-file-overview"></a><span data-ttu-id="4f8c4-102">형식 지정 파일 개요</span><span class="sxs-lookup"><span data-stu-id="4f8c4-102">Formatting File Overview</span></span>

<span data-ttu-id="4f8c4-103">명령 (cmdlet, 함수 및 스크립트)에서 반환 되는 개체에 대 한 표시 형식은 형식 지정 파일 (format.ps1xml 파일)를 사용 하 여 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-103">The display format for the objects that are returned by commands (cmdlets, functions, and scripts) are defined by using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="4f8c4-104">와 같은 PowerShell 제공한 명령에 의해 반환 된 해당 개체에 대 한 표시 형식을 정의 하는 PowerShell에서 제공 하는 다양 한 이러한 파일을 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 에서 반환 된 개체는 `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-104">Several of these files are provided by PowerShell to define the display format for those objects returned by PowerShell-provided commands, such as the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object returned by the `Get-Process` cmdlet.</span></span> <span data-ttu-id="4f8c4-105">그러나 기본 표시 형식을 덮어쓰려면 사용자 고유의 사용자 지정 형식 지정 파일을 만들 수도 있습니다 또는 고유한 명령에서 반환 된 개체의 표시를 정의 하는 사용자 지정 형식 지정 파일을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-105">However, you can also create your own custom formatting files to overwrite the default display formats or you can write a custom formatting file to define the display of objects returned by your own commands.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4f8c4-106">서식 파일에서 파이프라인에 반환 되는 개체의 요소를 결정 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-106">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="4f8c4-107">파이프라인에 반환 되는 개체 표시 되지 않는 일부 경우에 해당 개체의 모든 멤버가 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-107">When an object is returned to the pipeline, all members of that object are available even if some are not displayed.</span></span>

<span data-ttu-id="4f8c4-108">표시 되는 항목 및 표시 된 데이터의 서식 지정 하는 방법을 확인 하려면 이러한 서식 파일의 데이터를 사용 하는 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-108">PowerShell uses the data in these formatting files to determine what is displayed and how the displayed data is formatted.</span></span> <span data-ttu-id="4f8c4-109">표시 된 데이터 개체의 속성 또는 스크립트의 값을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-109">The displayed data can include the properties of an object or the value of a script.</span></span> <span data-ttu-id="4f8c4-110">스크립트 개체의 두 속성의 값을 추가 하 고 다음 데이터 부분으로 합계를 표시 하는 등의 개체의 속성에서 직접 사용할 수 없는 일부 값을 표시 하려는 경우에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-110">Scripts are used if you want to display some value that is not available directly from the properties of an object, such as adding the value of two properties of an object and then displaying the sum as a piece of data.</span></span> <span data-ttu-id="4f8c4-111">표시 된 데이터의 서식을 표시 하려는 개체에 대 한 뷰를 정의 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-111">Formatting of the displayed data is done by defining views for the objects that you want to display.</span></span> <span data-ttu-id="4f8c4-112">각 개체에 대 한 단일 뷰를 정의할 수 있습니다, 여러 개체에 대 한 단일 뷰를 정의할 수 있습니다 또는 동일한 개체에 대 한 여러 뷰를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-112">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="4f8c4-113">뷰에서 정의할 수 있는 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-113">There is no limit to the number of views that you can define.</span></span>

## <a name="common-features-of-formatting-files"></a><span data-ttu-id="4f8c4-114">서식 파일의 일반적인 기능</span><span class="sxs-lookup"><span data-stu-id="4f8c4-114">Common Features of Formatting Files</span></span>

<span data-ttu-id="4f8c4-115">각 형식 지정 파일 파일에서 정의 된 모든 뷰 간에 공유할 수 있는 다음 구성 요소를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-115">Each formatting file can define the following components that can be shared across all the views defined by the file:</span></span>

- <span data-ttu-id="4f8c4-116">기본 여부 테이블의 행에 표시 되는 데이터에 표시한 다음 줄 데이터 열의 너비 보다 길 경우와 같은 구성 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-116">Default configuration setting, such as whether the data displayed in the rows of tables will be displayed on the next line if the data is longer than the width of the column.</span></span> <span data-ttu-id="4f8c4-117">이러한 설정에 대 한 자세한 내용은 참조 하세요. [일반 구성 설정을 정의](./defining-common-configuration-features.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-117">For more information about these settings, see [Defining Common Configuration Settings](./defining-common-configuration-features.md).</span></span>

- <span data-ttu-id="4f8c4-118">서식 파일의 뷰 중 하나에서 표시 될 수 있는 개체의 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-118">Sets of objects that can be displayed by any of the views of the formatting file.</span></span> <span data-ttu-id="4f8c4-119">이러한 설정에 대 한 자세한 (이라고 *선택 집합*)를 참조 하세요 [설정의 개체 정의](./defining-selection-sets.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-119">For more information about these sets (referred to as *selection sets*), see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

- <span data-ttu-id="4f8c4-120">서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-120">Common controls that can be used by all the views of the formatting file.</span></span> <span data-ttu-id="4f8c4-121">컨트롤에 데이터 표시 방법을 보다 세부적으로 제어를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-121">Controls give you finer control on how data is displayed.</span></span> <span data-ttu-id="4f8c4-122">컨트롤에 대 한 자세한 내용은 참조 하세요. [사용자 지정 컨트롤 정의](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-122">For more information about controls, see [Defining Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="formatting-views"></a><span data-ttu-id="4f8c4-123">뷰를 서식 지정</span><span class="sxs-lookup"><span data-stu-id="4f8c4-123">Formatting Views</span></span>

<span data-ttu-id="4f8c4-124">형식 뷰는 테이블 형식, 목록 형식으로, 넓은 형식 및 사용자 지정 형식에서 개체를 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-124">Formatting views can display objects in a table format, list format, wide format, and custom format.</span></span> <span data-ttu-id="4f8c4-125">대부분의 경우 각 형식 정의 집합 뷰를 설명 하는 XML 태그에 의해 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-125">For the most part, each formatting definition is described by a set of XML tags that describe the view.</span></span> <span data-ttu-id="4f8c4-126">각 뷰는 뷰의 이름을 뷰 및 뷰를 표 보기에 대 한 열 및 행 정보 등의 요소를 사용 하는 개체를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-126">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="4f8c4-127">테이블 보기 개체 또는 하나 이상의 열에 있는 스크립트 블록 값의 속성을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-127">Table View Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="4f8c4-128">각 열에는 개체 또는 스크립트 값의 단일 속성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-128">Each column represents a single property of the object or a script value.</span></span> <span data-ttu-id="4f8c4-129">개체의 속성 및 스크립트 값의 조합일 개체의 속성 하위 집합의 모든 속성을 표시 하는 테이블 보기를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-129">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script values.</span></span> <span data-ttu-id="4f8c4-130">테이블의 각 행에는 반환 된 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-130">Each row of the table represents a returned object.</span></span> <span data-ttu-id="4f8c4-131">테이블 보기를 만드는 방법과 비슷합니다 개체를 파이프 하는 경우에 `Format-Table` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-131">Creating a table view is very similar to when you pipe an object to the `Format-Table` cmdlet.</span></span> <span data-ttu-id="4f8c4-132">이 보기에 대 한 자세한 내용은 참조 하세요. [테이블 뷰](./creating-a-table-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-132">For more information about this view, see [Table View](./creating-a-table-view.md).</span></span>

<span data-ttu-id="4f8c4-133">목록 보기의 속성을 나열할 개체 또는 단일 열에 스크립트 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-133">List View Lists the properties of an object or a script value in a single column.</span></span> <span data-ttu-id="4f8c4-134">선택적 레이블을 또는 속성 또는 스크립트의 값이 오는 속성 이름 목록의 각 행에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-134">Each row of the list displays an optional label or the property name followed by the value of the property or script.</span></span> <span data-ttu-id="4f8c4-135">목록 보기를 만드는 방법과 비슷합니다 개체를 파이프 하 여 `Format-List` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-135">Creating a list view is very similar to piping an object to the `Format-List` cmdlet.</span></span> <span data-ttu-id="4f8c4-136">이 보기에 대 한 자세한 내용은 참조 하세요. [목록 뷰에](./creating-a-list-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-136">For more information about this view, see [List View](./creating-a-list-view.md).</span></span>

<span data-ttu-id="4f8c4-137">넓은 보기 개체 또는 하나 이상의 열에 스크립트 값의 단일 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-137">Wide View Lists a single property of an object or a script value in one or more columns.</span></span> <span data-ttu-id="4f8c4-138">레이블 또는이 보기에 대 한 헤더 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-138">There is no label or header for this view.</span></span> <span data-ttu-id="4f8c4-139">넓은 보기를 만드는 과정은 매우 개체를 파이프 비슷합니다는 `Format-Wide` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-139">Creating a wide view is very similar to piping an object to the `Format-Wide` cmdlet.</span></span> <span data-ttu-id="4f8c4-140">이 보기에 대 한 자세한 내용은 참조 하세요. [와이드 보기인 경우](./creating-a-wide-view.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-140">For more information about this view, see [Wide View](./creating-a-wide-view.md).</span></span>

<span data-ttu-id="4f8c4-141">사용자 지정 보기 개체 속성 또는 스크립트 값의 테이블 뷰, 목록 뷰 또는 와이드 뷰가의 고정 된 구조로를 따르지 않으면 하는 사용자 지정 가능한 보기를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-141">Custom View Displays a customizable view of object properties or script values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="4f8c4-142">독립 실행형 사용자 지정 보기를 정의 하거나 테이블 뷰 또는 목록 보기와 같은 다른 보기에서 사용 되는 사용자 지정 보기를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-142">You can define a stand-alone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="4f8c4-143">사용자 지정 보기를 만드는 방법과 비슷합니다 개체를 파이프 하 여 `Format-Custom` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-143">Creating a custom view is very similar to piping an object to the `Format-Custom` cmdlet.</span></span> <span data-ttu-id="4f8c4-144">이 보기에 대 한 자세한 내용은 참조 하세요. [사용자 지정 보기](./creating-custom-controls.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-144">For more information about this view, see [Custom View](./creating-custom-controls.md).</span></span>

## <a name="components-of-a-view"></a><span data-ttu-id="4f8c4-145">뷰 구성 요소</span><span class="sxs-lookup"><span data-stu-id="4f8c4-145">Components of a View</span></span>

<span data-ttu-id="4f8c4-146">다음 XML 예제에서는 뷰의 기본 XML 구성 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-146">The following XML examples show the basic XML components of a view.</span></span> <span data-ttu-id="4f8c4-147">개별 XML 요소를 만들려고 할 수는 보기에 따라 다르지만 뷰의 기본 구성 요소는 모두 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-147">The individual XML elements vary depending on which view you want to create, but the basic components of the views are all the same.</span></span>

<span data-ttu-id="4f8c4-148">시작 하려면 각 보기에는 `Name` 뷰를 참조 하는 데 사용 되는 알기 쉬운 이름을 지정 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-148">To start with, each view has a `Name` element that specifies a user friendly name that is used to reference the view.</span></span> <span data-ttu-id="4f8c4-149">`ViewSelectedBy` 뷰에.NET 개체를 표시를 정의 하는 요소 및 *제어* 뷰를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-149">a `ViewSelectedBy` element that defines which .NET objects are displayed by the view, and a *control* element that defines the view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <ListControl>...</ListControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <WideControl>...</WideControl>
  <View>
  <View>
    <Name>NameOfView</Name>
    <ViewSelectedBy>...</ViewSelectedBy>
    <CustomControl>...</CustomControl>
  </View>
</ViewDefinitions>

```

<span data-ttu-id="4f8c4-150">Control 요소 내에서 하나 이상 정의할 수 있습니다 *항목이* 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-150">Within the control element, you can define one or more *entry* elements.</span></span> <span data-ttu-id="4f8c4-151">여러 정의 사용 하는 경우 각 정의 사용 하 여.NET 개체를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-151">If you use multiple definitions, you must specify which .NET objects use each definition.</span></span> <span data-ttu-id="4f8c4-152">일반적으로 각 컨트롤에 대 한 하나의 정의 사용 하 여 항목이 하나만 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-152">Typically only one entry, with only one definition, is needed for each control.</span></span>

```xml
<ListControl>
  <ListEntries>
    <ListEntry>
      <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
    <ListEntry>
        <EntrySelectedBy>...</EntrySelectedBy>
      <ListItems>...</ListItems>
    <ListEntry>
  </ListEntries>
</ListControl>

```

<span data-ttu-id="4f8c4-153">뷰의 각 항목 요소 내에서 지정 된 *항목* .NET 속성 또는 보기에 표시 되는 스크립트를 정의 하는 요소.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-153">Within each entry element of a view, you specify the *item* elements that define the .NET properties or scripts that are displayed by that view.</span></span>

```xml

<ListItems>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
  <ListItem>...</ListItem>
</ListItems>

```

<span data-ttu-id="4f8c4-154">앞의 예제와 같이 서식 파일에는 여러 뷰가 포함 될 수 있습니다, 뷰 정의가 여러 개 포함할 수 있습니다 및 각 정의 여러 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-154">As shown in the preceding examples, the formatting file can contain multiple views, a view can contain multiple definitions, and each definition can contain multiple items.</span></span>

## <a name="example-of-a-table-view"></a><span data-ttu-id="4f8c4-155">테이블 보기의 예</span><span class="sxs-lookup"><span data-stu-id="4f8c4-155">Example of a Table View</span></span>

<span data-ttu-id="4f8c4-156">다음 예제에서는 두 개의 열이 포함 된 테이블 뷰를 정의 하는 데 XML 태그를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-156">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="4f8c4-157">합니다 [ViewDefinitions](./viewdefinitions-element-format.md) 요소는 서식 파일에 정의 된 모든 보기에 대 한 컨테이너 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-157">The [ViewDefinitions](./viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="4f8c4-158">합니다 [보기](./view-element-format.md) 요소는 특정 테이블, 목록, 넓게 또는 사용자 지정 보기를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-158">The [View](./view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="4f8c4-159">각 [뷰](./view-element-format.md) 요소를 [이름](./name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 뷰 및 다양 한를 사용 하는 개체를 정의 하는 요소 컨트롤 요소 (같은 `TableControl` 다음 예제에 표시 된 요소) 보기의 유형을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f8c4-159">Within each [View](./view-element-format.md) element, the [Name](./name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](./viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element shown in the following example) define the type of the view.</span></span>

```xml
<ViewDefinitions>
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

## <a name="see-also"></a><span data-ttu-id="4f8c4-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4f8c4-160">See Also</span></span>

[<span data-ttu-id="4f8c4-161">목록 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="4f8c4-161">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="4f8c4-162">테이블 뷰 만들기</span><span class="sxs-lookup"><span data-stu-id="4f8c4-162">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4f8c4-163">넓은 보기 만들기</span><span class="sxs-lookup"><span data-stu-id="4f8c4-163">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="4f8c4-164">사용자 지정 컨트롤 만들기</span><span class="sxs-lookup"><span data-stu-id="4f8c4-164">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4f8c4-165">PowerShell 서식 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="4f8c4-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
