---
title: 형식에 대 한 TypeName 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368032"
---
# <a name="typename-element-for-types-format"></a>Types에 대한 TypeName 요소(형식)

선택 집합에 속하는 개체의 .NET 유형을 지정 합니다.

Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Types 요소 (format) TypeName 요소 (형식)

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 하나 이상의 `TypeName` 요소가 선택 집합에 포함 되어야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Types 요소 (Format)](./types-element-for-selectionset-format.md)|선택 집합에 있는 .NET 개체를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름을 지정 합니다.

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체 집합과 같이 단일 이름을 사용 하 여 참조 하려는 관련 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 뷰를 정의할 때 각 보기 내에 모든 개체를 나열 하는 대신 선택 집합의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.

일반 선택 집합은 형식 지정 파일의 뷰를 정의할 때 이름으로 지정 됩니다. 이 경우 뷰의 `ViewSelectedBy` 요소에 있는 `SelectionSetName` 자식 요소는 집합을 지정 합니다. 그러나 뷰의 다른 항목은 뷰의 해당 항목에만 적용 되는 선택 집합을 지정할 수도 있습니다. 선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 네 가지 .NET 형식을 정의 하는 `SelectionSet` 요소를 보여 줍니다.

```
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

[SelectionSets 요소 (형식)](./selectionsets-element-format.md)

[Types 요소 (Format)](./types-element-for-selectionset-format.md)

[Windows PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
