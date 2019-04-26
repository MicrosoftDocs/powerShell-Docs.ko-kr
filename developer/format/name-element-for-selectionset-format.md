---
title: SelectionSet (형식)에 대 한 요소 이름을 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 914917f7-0efc-4d1f-88bd-de714bedd98f
caps.latest.revision: 15
ms.openlocfilehash: 29dbdbd335511e4ca2706a625541554825838f23
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065158"
---
# <a name="name-element-for-selectionset-format"></a>SelectionSet에 대한 Name 요소(형식)

선택 영역 집합을 참조 하는 데 사용 하는 이름을 지정 합니다.

SelectionSet (형식)의 구성 요소 (형식) SelectionSets 요소 (형식) SelectionSet 요소 (형식) Name 요소

## <a name="syntax"></a>구문

```xml
<Name>Name of selection set</Name>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Name` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet 요소 (형식)](./selectionset-element-format.md)|단일 집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

선택 영역 집합을 참조 이름을 지정 합니다. 어떤 문자에 대 한 제한이 사용할 수 있습니다.

## <a name="remarks"></a>설명

여기에 지정 된 이름에 사용 되는 `SelectionSetName` 요소입니다. 뷰를 정의 하 여 뷰를 사용할 수 있는 선택 세트 (뷰 정의가 여러 개 있을 수 있음)를 선택 조건을 지정할 때 또는 합니다. 선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

## <a name="example"></a>예제

이 예제에서는 `SelectionSet` .NET 유형은 정의 하는 요소입니다. 선택 항목 집합의 이름은 "FileSystemTypes"입니다.

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

[선택 영역 집합을 정의](./defining-selection-sets.md)

[SelectionSet 요소 (형식)](./selectionset-element-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
