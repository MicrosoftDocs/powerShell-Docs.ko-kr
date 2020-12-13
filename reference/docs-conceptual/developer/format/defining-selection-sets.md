---
ms.date: 09/13/2016
ms.topic: reference
title: 선택 영역 집합 정의
description: 선택 영역 집합 정의
ms.openlocfilehash: d709a368a45623d56fdbf4e98a11a5e5f8a193fa
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92648259"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="9e018-103">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="9e018-103">Defining Selection Sets</span></span>

<span data-ttu-id="9e018-104">여러 뷰와 컨트롤을 만들 때 선택 집합으로 참조 되는 개체 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-104">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="9e018-105">선택 집합을 사용 하면 각 뷰나 컨트롤에 대해 반복적으로 정의 하지 않고도 개체를 한 번 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-105">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="9e018-106">일반적으로 선택 집합은 관련 된 .NET 개체 집합이 있는 경우 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-106">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="9e018-107">예를 들어 `FileSystem` 형식 지정 파일 (FileSystem.format.ps1xml)은 여러 보기에서 사용 하는 파일 시스템 형식의 선택 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-107">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="9e018-108">선택 집합이 정의 되 고 참조 되는 위치</span><span class="sxs-lookup"><span data-stu-id="9e018-108">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="9e018-109">서식 파일에 정의 된 모든 뷰와 컨트롤에서 사용할 수 있는 공통 데이터의 일부로 선택 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-109">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="9e018-110">다음 예에서는 세 개의 선택 집합을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-110">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="9e018-111">다음과 같은 방법으로 선택 집합을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-111">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="9e018-112">각 뷰에는 `ViewSelectedBy` 뷰를 사용 하 여 표시 되는 개체를 정의 하는 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-112">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="9e018-113">요소에는 `ViewSelectedBy` `SelectionSetName` 뷰의 모든 정의에 사용 되는 선택 집합을 지정 하는 자식 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-113">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="9e018-114">뷰에서 참조할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-114">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="9e018-115">뷰나 컨트롤의 각 정의에서 `EntrySelectedBy` 요소는 해당 정의를 사용 하 여 표시 되는 개체를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-115">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="9e018-116">일반적으로 뷰 또는 컨트롤에는 하나의 정의만 있으므로 개체가 요소에 의해 정의 됩니다 `ViewSelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="9e018-116">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="9e018-117">`EntrySelectedBy`정의의 요소에는 `SelectionSetName` 선택 집합을 지정 하는 자식 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-117">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="9e018-118">정의에 대 한 선택 집합을 지정 하는 경우 요소의 다른 자식 요소를 지정할 수 없습니다 `EntrySelectedBy` .</span><span class="sxs-lookup"><span data-stu-id="9e018-118">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="9e018-119">뷰나 컨트롤의 각 정의에서 `SelectionCondition` 요소를 사용 하 여 정의를 사용 하는 경우에 대 한 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-119">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="9e018-120">요소에는 `SelectionCondition` `SelectionSetName` 조건을 트리거하는 선택 집합을 지정 하는 자식 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-120">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="9e018-121">선택 집합에 정의 된 개체가 표시 될 때 조건이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-121">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="9e018-122">이러한 조건을 설정 하는 방법에 대 한 자세한 내용은 [데이터 표시 시기에 대 한 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e018-122">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="9e018-123">선택 집합 예제</span><span class="sxs-lookup"><span data-stu-id="9e018-123">Selection Set Example</span></span>

<span data-ttu-id="9e018-124">다음 예제에서는 `FileSystem` Windows PowerShell에서 제공 하는 서식 파일에서 직접 가져온 선택 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-124">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="9e018-125">다른 Windows PowerShell 형식 지정 파일에 대 한 자세한 내용은 [Windows Powershell 형식 지정 파일](./powershell-formatting-files.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e018-125">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

```xml
<SelectionSets>
  <SelectionSet>
    <Name>FileSystemTypes</Name>
    <Types>
     <TypeName>System.IO.DirectoryInfo</TypeName>
     <TypeName>System.IO.FileInfo</TypeName>
     <TypeName>Deserialized.System.IO.DirectoryInfo</TypeName>
     <TypeName>Deserialized.System.IO.FileInfo</TypeName>
    </Types>
  </SelectionSet>
</SelectionSets>
```

<span data-ttu-id="9e018-126">이전 선택 집합은 `ViewSelectedBy` 테이블 뷰의 요소에서 참조 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-126">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

```xml
<ViewDefinitions>
  <View>
    <Name>Files</Name>
    <ViewSelectedBy>
      <SelectionSetName>FileSystemTypes</SelectionSetName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="xml-elements"></a><span data-ttu-id="9e018-127">XML 요소</span><span class="sxs-lookup"><span data-stu-id="9e018-127">XML Elements</span></span>

 <span data-ttu-id="9e018-128">정의할 수 있는 선택 집합 수에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-128">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="9e018-129">다음 XML 요소를 사용 하 여 선택 집합을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-129">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="9e018-130">[Selectionsets](./selectionsets-element-format.md) 요소는 서식 파일의 뷰 및 컨트롤에서 참조 하는 .net 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-130">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="9e018-131">[Selectionset](./selectionset-element-format.md) 요소는 단일 .net 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-131">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="9e018-132">[Name](./name-element-for-selectionset-format.md) 요소는 선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-132">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="9e018-133">[Types](./types-element-for-selectionset-format.md) 요소는 선택 집합의 개체에 대 한 .net 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-133">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="9e018-134">형식 지정 파일 내에서 개체는 .NET 형식으로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-134">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="9e018-135">다음 XML 요소를 사용 하 여 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-135">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="9e018-136">다음 요소는 뷰의 모든 정의에 사용할 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-136">The following element specifies the selection set to use in all the definitions of the view:</span></span>

  - [<span data-ttu-id="9e018-137">ViewSelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-137">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

  - [<span data-ttu-id="9e018-138">GroupBy의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-138">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="9e018-139">다음 요소는 단일 뷰 정의에서 사용 되는 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-139">The following elements specify the selection set used by a single view definition:</span></span>

  - [<span data-ttu-id="9e018-140">ListControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

  - [<span data-ttu-id="9e018-141">TableControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-141">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="9e018-142">WideControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-142">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

  - [<span data-ttu-id="9e018-143">View에 대한 CustomControl의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-143">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="9e018-144">다음 요소는 공용 및 뷰 컨트롤 정의에서 사용 되는 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-144">The following elements specify the selection set used by common and view control definitions:</span></span>

  - [<span data-ttu-id="9e018-145">View에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-145">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

  - [<span data-ttu-id="9e018-146">Configuration에 대한 Controls의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-146">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="9e018-147">다음 요소는 확장할 개체를 정의할 때 사용 되는 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-147">The following elements specify the selection set used when you define which object to expand:</span></span>

  - [<span data-ttu-id="9e018-148">EnumerableExpansion의 EntrySelectedBy에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-148">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="9e018-149">다음 요소는 선택 조건에 사용 되는 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e018-149">The following elements specify the selection set used by selection conditions.</span></span>

  - [<span data-ttu-id="9e018-150">Configuration에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-150">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

  - [<span data-ttu-id="9e018-151">View에 대한 Controls의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-151">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

  - [<span data-ttu-id="9e018-152">View에 대한 CustomControl의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-152">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

  - [<span data-ttu-id="9e018-153">EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

  - [<span data-ttu-id="9e018-154">ListEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

  - [<span data-ttu-id="9e018-155">TableControl에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

  - [<span data-ttu-id="9e018-156">WideEntry에 대한 EntrySelectedBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-156">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

  - [<span data-ttu-id="9e018-157">GroupBy의 SelectionCondition에 대한 SelectionSetName 요소(형식)</span><span class="sxs-lookup"><span data-stu-id="9e018-157">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="9e018-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e018-158">See Also</span></span>

[<span data-ttu-id="9e018-159">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="9e018-159">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="9e018-160">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="9e018-160">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="9e018-161">이름</span><span class="sxs-lookup"><span data-stu-id="9e018-161">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="9e018-162">유형</span><span class="sxs-lookup"><span data-stu-id="9e018-162">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="9e018-163">PowerShell 형식 지정 파일</span><span class="sxs-lookup"><span data-stu-id="9e018-163">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="9e018-164">데이터가 표시 되는 시점에 대 한 조건 정의</span><span class="sxs-lookup"><span data-stu-id="9e018-164">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="9e018-165">PowerShell 서식 지정 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="9e018-165">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
