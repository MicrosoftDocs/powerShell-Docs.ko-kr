---
title: SelectionSet (Format)의 Name 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362672"
---
# <a name="name-element-for-selectionset-format"></a>SelectionSet에 대한 Name 요소(형식)

선택 집합을 참조 하는 데 사용 되는 이름을 지정 합니다.

Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Name 요소 Selectionsets (Format)

## <a name="syntax"></a>구문

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `Name` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet 요소 (형식)](./selectionset-element-format.md)|집합의 이름으로 참조할 수 있는 단일 .NET 개체 집합을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 집합을 참조 하는 이름을 지정 합니다. 사용할 수 있는 문자에 대 한 제한은 없습니다.

## <a name="remarks"></a>설명

여기에 지정 된 이름은 `SelectionSetName` 요소에 사용 됩니다. 뷰에서 사용할 수 있는 선택 집합으로, 보기의 정의에 의해 (보기에 여러 정의가 있을 수 있음) 또는 선택 조건을 지정할 때 사용할 수 있습니다. 선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 네 가지 .NET 형식을 정의 하는 `SelectionSet` 요소를 보여 줍니다. 선택 집합의 이름은 "FileSystemTypes"입니다.

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

[SelectionSet 요소 (형식)](./selectionset-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
