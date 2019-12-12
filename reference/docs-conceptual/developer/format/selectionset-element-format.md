---
title: SelectionSet 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 848e7acd-d578-4fd1-a575-c0c3b9b5e68a
caps.latest.revision: 17
ms.openlocfilehash: c809aa6c3a40d16cfd2fd99065a846d265ec0f61
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368382"
---
# <a name="selectionset-element-format"></a>SelectionSet 요소(형식)

집합의 이름으로 참조할 수 있는 .NET 개체 집합을 정의 합니다.

Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (Format)

## <a name="syntax"></a>구문

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `SelectionSet` 요소의 부모 요소에 대해 설명 합니다. 각 선택 집합에는 이름이 있어야 하며 집합의 .NET 개체를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet (Format)의 Name 요소](./name-element-for-selectionset-format.md)|필수적 요소입니다.<br /><br /> 선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.|
|[Types 요소 (Format)](./types-element-for-selectionset-format.md)|필수적 요소입니다.<br /><br /> 선택 집합에 있는 .NET 개체를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSets 형식 설정](./selectionsets-element-format.md)|서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.|

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.

일반 선택 집합은 형식 지정 파일의 뷰나 뷰의 정의를 정의할 때 이름으로 지정 됩니다. 이러한 경우 `ViewSelectedBy` 및 `EntrySelectedBy` 요소의 `SelectionSetName` 자식 요소는 사용할 집합을 지정 합니다. 선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 네 가지 .NET 형식을 정의 하는 `SelectionSet` 요소를 보여 줍니다.

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

## <a name="see-also"></a>참고 항목

[선택 집합 정의](./defining-selection-sets.md)

[SelectionSet의 Name 요소 (Format)](./name-element-for-selectionset-format.md)

[SelectionSets 요소 (형식)](./selectionsets-element-format.md)

[Types 요소 (Format)](./types-element-for-selectionset-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
