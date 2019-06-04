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
# <a name="defining-selection-sets"></a>선택 영역 집합 정의

여러 보기와 컨트롤을 만들 때 선택 집합으로 참조 하는 개체 집합을 정의할 수 있습니다. 선택 집합을 사용 하면 각 뷰 또는 컨트롤에 대해 반복적으로 정의 하지 않고 개체를 한 번 정의할 수 있습니다. 일반적으로 선택 집합 관련된.NET 개체 집합이 있는 경우 사용 됩니다. 예를 들어를 `FileSystem` 형식 지정 파일 (FileSystem.format.ps1xml) 여러 뷰를 사용 하는 파일 시스템 유형 선택 집합을 정의 합니다.

## <a name="where-selection-sets-are-defined-and-referenced"></a>선택 영역 집합은 정의 이며 참조

모든 보기 및 형식 지정 파일에 정의 된 컨트롤에서 사용할 수 있는 일반적인 데이터의 일부로 선택 집합을 정의 합니다. 다음 예제에서는 세 가지 선택 집합을 정의 하는 방법을 보여 줍니다.

```xml
<Configuration>
  <SelectionSets>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
    <SelectionSet>...</SelectionSet>
  </SelectionSets>
</Configuration>
```

선택 영역을 참조할 수 있습니다 다음 방법으로 설정 합니다.

- 각 보기에는 `ViewSelectedBy` 뷰를 사용 하 여 표시 되는 객체를 정의 하는 요소입니다. 합니다 `ViewSelectedBy` 요소에는 `SelectionSetName` 사용 리소스 보기의 모든 정의 선택 항목을 지정 하는 자식 요소 집합입니다. 보기에서 참조할 수 있는 선택 항목 집합 수에 제한은 없습니다.

- 뷰 또는 컨트롤의 각 정의에 `EntrySelectedBy` 요소 정의 개체는 해당 정의 사용 하 여 표시 됩니다. 일반적으로 뷰 또는 컨트롤 있으므로 하나만 정의 하 여 정의 된 개체는 `ViewSelectedBy` 요소입니다. 합니다 `EntrySelectedBy` 정의의 요소에는 `SelectionSetName` 선택 세트를 지정 하는 자식 요소입니다. 선택 정의 세트를 지정 하는 경우의 다른 자식 요소 중 하나를 지정할 수 없습니다 하 여 `EntrySelectedBy` 요소입니다.

- 뷰 또는 컨트롤의 각 정의에 `SelectionCondition` 요소 정의 사용 하는 경우에 대 한 조건을 지정 하려면 사용할 수 있습니다. 합니다 `SelectionCondition` 요소에는 `SelectionSetName` 선택 집합을 지정 하는 자식 요소 트리거 조건. 조건 선택 집합에 정의 된 개체 중 하나가 표시 되 면 트리거됩니다. 이러한 조건을 설정 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터를 표시 하는 경우에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="selection-set-example"></a>선택 영역 집합 예제

다음 예제에서는에서 직접 수행 되는 선택 집합을 `FileSystem` Windows PowerShell에서 제공 하는 파일 서식 지정. 다른 Windows PowerShell 형식 지정 파일에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 형식 지정 파일](./powershell-formatting-files.md)합니다.

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

이전 선택 항목 집합에서 참조 되는 `ViewSelectedBy` 테이블 뷰 요소입니다.

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

## <a name="xml-elements"></a>XML 요소

 정의할 수 있는 선택 항목 집합 수에 제한은 없습니다. 다음 XML 요소가 선택 집합을 만드는 사용 됩니다.

- 합니다 [SelectionSets](./selectionsets-element-format.md) 뷰에서 참조 되는.NET 개체 집합 및 서식 파일의 컨트롤 요소를 정의 합니다.

- 합니다 [SelectionSet](./selectionset-element-format.md) 요소는 단일.NET 개체 집합을 정의 합니다.

- 합니다 [이름을](./name-element-for-selectionset-format.md) 요소 선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.

- 합니다 [형식](./types-element-for-selectionset-format.md) 요소 선택 집합 개체의.NET 유형을 지정 합니다. (파일 형식 내에서 개체 지정 된.NET 형식에 따라 합니다.)

 선택 영역 집합을 지정 하려면 다음 XML 요소가 사용 됩니다.

- 다음 요소에는 보기의 모든 정의에 사용 하도록 설정 선택을 지정 합니다.

    - [ViewSelectedBy (형식)에 대 한 SelectionSetName 요소](./selectionsetname-element-for-viewselectedby-format.md)

    - [GroupBy (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

- 다음 요소를 단일 뷰 정의에서 사용 하는 선택 집합을 지정 합니다.

    - [ListControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

    - [TableControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

    - [WideControl (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

    - [CustomControl 보려면 (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format.md)

- 일반적인 사용 선택 집합을 지정 하는 다음 요소 및 컨트롤 정의 보기:

    - [뷰 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-controls-for-view-format.md)

    - [구성 (형식)에 대 한 컨트롤에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-controls-for-configuration-format.md)

- 다음 요소를 확장 하는 개체를 정의 하는 경우 사용할 선택 집합을 지정 합니다.

    - [EnumerableExpansion (형식)에 대 한 EntrySelectedBy SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

- 다음 요소를 선택 조건으로 사용할 선택 집합을 지정 합니다.

    - [구성 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

    - [뷰 (형식)에 대 한 컨트롤에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

    - [CustomControl 보려면 (형식)에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

    - [EntrySelectedBy EnumerableExpansion (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

    - [EntrySelectedBy ListEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)

    - [TableControl (형식)에 대 한 EntrySelectedBy에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

    - [EntrySelectedBy WideEntry (형식)에 대 한에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

    - [GroupBy (형식)에 대 한 SelectionCondition SelectionSetName 요소](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)

## <a name="see-also"></a>참고 항목

[SelectionSets](./selectionsets-element-format.md)

[SelectionSet](./selectionset-element-format.md)

[이름](./name-element-for-selectionset-format.md)

[유형](./types-element-for-selectionset-format.md)

[PowerShell 서식 파일](./powershell-formatting-files.md)

[데이터 표시 되 면에 대 한 조건을 정의 합니다.](./defining-conditions-for-displaying-data.md)

[PowerShell 서식 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
