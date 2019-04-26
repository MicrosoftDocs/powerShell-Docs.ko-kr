---
title: 선택 영역 집합을 정의 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 00dbb5ee-93d4-4914-a082-ef4d8b236b5c
caps.latest.revision: 16
ms.openlocfilehash: 596212f2e64401a751cf3dca0ee7d60b80912c00
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066314"
---
# <a name="defining-selection-sets"></a><span data-ttu-id="f9481-102">선택 영역 집합 정의</span><span class="sxs-lookup"><span data-stu-id="f9481-102">Defining Selection Sets</span></span>

<span data-ttu-id="f9481-103">여러 보기와 컨트롤을 만들 때 선택 집합으로 참조 하는 개체 집합을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-103">When creating multiple views and controls, you can define sets of objects that are referred to as selection sets.</span></span> <span data-ttu-id="f9481-104">선택 집합을 사용 하면 각 뷰 또는 컨트롤에 대해 반복적으로 정의 하지 않고 개체를 한 번 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-104">A selection set enables you to define the objects one time, without having to define them repeatedly for each view or control.</span></span> <span data-ttu-id="f9481-105">일반적으로 선택 집합 관련된.NET 개체 집합이 있는 경우 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-105">Typically, selection sets are used when you have a set of related .NET objects.</span></span> <span data-ttu-id="f9481-106">예를 들어를 `FileSystem` 형식 지정 파일 (FileSystem.format.ps1xml) 여러 뷰를 사용 하는 파일 시스템 유형 선택 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-106">For example, The `FileSystem` formatting file (FileSystem.format.ps1xml) defines a selection set of the file system types that several views use.</span></span>

## <a name="where-selection-sets-are-defined-and-referenced"></a><span data-ttu-id="f9481-107">선택 영역 집합은 정의 이며 참조</span><span class="sxs-lookup"><span data-stu-id="f9481-107">Where Selection Sets are Defined and Referenced</span></span>

<span data-ttu-id="f9481-108">모든 보기 및 형식 지정 파일에 정의 된 컨트롤에서 사용할 수 있는 일반적인 데이터의 일부로 선택 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-108">You define selection sets as part of the common data that can be used by all the views and controls defined in the formatting file.</span></span> <span data-ttu-id="f9481-109">다음 예제에서는 세 가지 선택 집합을 정의 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-109">The following example shows how to define three selection sets.</span></span>

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

<span data-ttu-id="f9481-110">선택 영역을 참조할 수 있습니다 다음 방법으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-110">You can reference a selection sets in the following ways:</span></span>

- <span data-ttu-id="f9481-111">각 보기에는 `ViewSelectedBy` 뷰를 사용 하 여 표시 되는 객체를 정의 하는 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-111">Each view has a `ViewSelectedBy` element that defines which objects are displayed by using the view.</span></span> <span data-ttu-id="f9481-112">합니다 `ViewSelectedBy` 요소에는 `SelectionSetName` 사용 리소스 보기의 모든 정의 선택 항목을 지정 하는 자식 요소 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-112">The `ViewSelectedBy` element has a `SelectionSetName` child element that specifies the selection set that all the definitions of the view use.</span></span> <span data-ttu-id="f9481-113">보기에서 참조할 수 있는 선택 항목 집합 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-113">There is no restriction on the number of selection sets that you can reference from a view.</span></span>

- <span data-ttu-id="f9481-114">뷰 또는 컨트롤의 각 정의에 `EntrySelectedBy` 요소 정의 개체는 해당 정의 사용 하 여 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-114">In each definition of a view or control, the `EntrySelectedBy` element defines which objects are displayed by using that definition.</span></span> <span data-ttu-id="f9481-115">일반적으로 뷰 또는 컨트롤 있으므로 하나만 정의 하 여 정의 된 개체는 `ViewSelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-115">Typically a view or control has only one definition so the objects are defined by the `ViewSelectedBy` element.</span></span> <span data-ttu-id="f9481-116">합니다 `EntrySelectedBy` 정의의 요소에는 `SelectionSetName` 선택 세트를 지정 하는 자식 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-116">The `EntrySelectedBy` element of the definition has a `SelectionSetName` child element that specifies the selection set.</span></span> <span data-ttu-id="f9481-117">선택 정의 세트를 지정 하는 경우의 다른 자식 요소 중 하나를 지정할 수 없습니다 하 여 `EntrySelectedBy` 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-117">If you specify the selection set for a definition, you cannot specify any of the other child elements of the `EntrySelectedBy` element.</span></span>

- <span data-ttu-id="f9481-118">뷰 또는 컨트롤의 각 정의에 `SelectionCondition` 요소 정의 사용 하는 경우에 대 한 조건을 지정 하려면 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-118">In each definition of a view or control, the `SelectionCondition` element can be used to specify a condition for when the definition is used.</span></span> <span data-ttu-id="f9481-119">합니다 `SelectionCondition` 요소에는 `SelectionSetName` 선택 집합을 지정 하는 자식 요소 트리거 조건.</span><span class="sxs-lookup"><span data-stu-id="f9481-119">The `SelectionCondition` element has a `SelectionSetName` child element that specifies the selection set that triggers the condition.</span></span> <span data-ttu-id="f9481-120">조건 선택 집합에 정의 된 개체 중 하나가 표시 되 면 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-120">The condition is triggered when any of the objects defined in the selection set are displayed.</span></span> <span data-ttu-id="f9481-121">이러한 조건을 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-121">For more information about how to set these conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="selection-set-example"></a><span data-ttu-id="f9481-122">선택 영역 집합 예제</span><span class="sxs-lookup"><span data-stu-id="f9481-122">Selection Set Example</span></span>

<span data-ttu-id="f9481-123">다음 예제에서는에서 직접 수행 되는 선택 집합을 `FileSystem` Windows PowerShell에서 제공 하는 파일 서식 지정.</span><span class="sxs-lookup"><span data-stu-id="f9481-123">The following example shows a selection set that is taken directly from the `FileSystem` formatting file provided by Windows PowerShell.</span></span> <span data-ttu-id="f9481-124">다른 Windows PowerShell 형식 지정 파일에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 형식 지정 파일](./powershell-formatting-files.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-124">For more information about other Windows PowerShell formatting files, see [Windows PowerShell Formatting Files](./powershell-formatting-files.md).</span></span>

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

<span data-ttu-id="f9481-125">이전 선택 항목 집합에서 참조 되는 `ViewSelectedBy` 테이블 뷰 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-125">The previous selection set is referenced in the `ViewSelectedBy` element of a table view.</span></span>

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

## <a name="xml-elements"></a><span data-ttu-id="f9481-126">XML 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-126">XML Elements</span></span>

 <span data-ttu-id="f9481-127">정의할 수 있는 선택 항목 집합 수에 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-127">There is no limit to the number of selection sets that you can define.</span></span> <span data-ttu-id="f9481-128">다음 XML 요소가 선택 집합을 만드는 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-128">The following XML elements are used to create a selection set.</span></span>

- <span data-ttu-id="f9481-129">합니다 [SelectionSets](./selectionsets-element-format.md) 뷰에서 참조 되는.NET 개체 집합 및 서식 파일의 컨트롤 요소를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-129">The [SelectionSets](./selectionsets-element-format.md) element defines the sets of .NET objects that are referenced by the views and controls of the formatting file.</span></span>

- <span data-ttu-id="f9481-130">합니다 [SelectionSet](./selectionset-element-format.md) 요소는 단일.NET 개체 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-130">The [SelectionSet](./selectionset-element-format.md) element defines a single set of .NET objects.</span></span>

- <span data-ttu-id="f9481-131">합니다 [이름을](./name-element-for-selectionset-format.md) 요소 선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-131">The [Name](./name-element-for-selectionset-format.md) element specifies the name that is used to reference the selection set.</span></span>

- <span data-ttu-id="f9481-132">합니다 [형식](./types-element-for-selectionset-format.md) 요소 선택 집합 개체의.NET 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-132">The [Types](./types-element-for-selectionset-format.md) element specifies the .NET types of the objects of the selection set.</span></span> <span data-ttu-id="f9481-133">(파일 형식 내에서 개체 지정 된.NET 형식에 따라 합니다.)</span><span class="sxs-lookup"><span data-stu-id="f9481-133">(Within formatting files, objects are specified by their .NET type.)</span></span>

 <span data-ttu-id="f9481-134">선택 영역 집합을 지정 하려면 다음 XML 요소가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-134">The following XML elements are used to specify a selection set.</span></span>

- <span data-ttu-id="f9481-135">다음 요소에는 보기의 모든 정의에 사용 하도록 설정 선택을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-135">The following element specifies the selection set to use in all the definitions of the view:</span></span>

    - [<span data-ttu-id="f9481-136">ViewSelectedBy (형식)에 대 한 SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-136">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

    - [<span data-ttu-id="f9481-137">GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-137">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- <span data-ttu-id="f9481-138">다음 요소를 단일 뷰 정의에서 사용 하는 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-138">The following elements specify the selection set used by a single view definition:</span></span>

    - [<span data-ttu-id="f9481-139">ListControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-139">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [<span data-ttu-id="f9481-140">TableControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-140">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="f9481-141">WideControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-141">SelectionSetName Element for EntrySelectedBy for WideControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [<span data-ttu-id="f9481-142">CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-142">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- <span data-ttu-id="f9481-143">일반적인 사용 선택 집합을 지정 하는 다음 요소 및 컨트롤 정의 보기:</span><span class="sxs-lookup"><span data-stu-id="f9481-143">The following elements specify the selection set used by common and view control definitions:</span></span>

    - [<span data-ttu-id="f9481-144">뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-144">SelectionSetName Element for EntrySelectedBy for Controls for View (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [<span data-ttu-id="f9481-145">구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-145">SelectionSetName Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- <span data-ttu-id="f9481-146">다음 요소를 확장 하는 개체를 정의 하는 경우 사용할 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-146">The following elements specify the selection set used when you define which object to expand:</span></span>

    - [<span data-ttu-id="f9481-147">EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-147">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- <span data-ttu-id="f9481-148">다음 요소를 선택 조건으로 사용할 선택 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-148">The following elements specify the selection set used by selection conditions.</span></span>

    - [<span data-ttu-id="f9481-149">구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-149">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [<span data-ttu-id="f9481-150">뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-150">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [<span data-ttu-id="f9481-151">CustomControl 보려면 (형식)에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-151">SelectionSetName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [<span data-ttu-id="f9481-152">EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-152">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [<span data-ttu-id="f9481-153">EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-153">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [<span data-ttu-id="f9481-154">TableControl (형식)에 대 한 EntrySelectedBy에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-154">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [<span data-ttu-id="f9481-155">EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-155">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [<span data-ttu-id="f9481-156">GroupBy (형식)에 대 한 SelectionCondition SelectionSetName 요소</span><span class="sxs-lookup"><span data-stu-id="f9481-156">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a><span data-ttu-id="f9481-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f9481-157">See Also</span></span>

[<span data-ttu-id="f9481-158">SelectionSets</span><span class="sxs-lookup"><span data-stu-id="f9481-158">SelectionSets</span></span>](./selectionsets-element-format.md)

[<span data-ttu-id="f9481-159">SelectionSet</span><span class="sxs-lookup"><span data-stu-id="f9481-159">SelectionSet</span></span>](./selectionset-element-format.md)

[<span data-ttu-id="f9481-160">이름</span><span class="sxs-lookup"><span data-stu-id="f9481-160">Name</span></span>](./name-element-for-selectionset-format.md)

[<span data-ttu-id="f9481-161">유형</span><span class="sxs-lookup"><span data-stu-id="f9481-161">Types</span></span>](./types-element-for-selectionset-format.md)

[<span data-ttu-id="f9481-162">PowerShell 서식 파일</span><span class="sxs-lookup"><span data-stu-id="f9481-162">PowerShell Formatting Files</span></span>](./powershell-formatting-files.md)

[<span data-ttu-id="f9481-163">데이터 표시 되 면에 대 한 조건을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f9481-163">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f9481-164">PowerShell 서식 및 형식 파일 작성</span><span class="sxs-lookup"><span data-stu-id="f9481-164">Writing a PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
