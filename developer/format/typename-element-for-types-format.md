---
title: TypeName 요소 형식 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0595b99e-b438-4240-b47b-555cf0316f33
caps.latest.revision: 15
ms.openlocfilehash: bd5baa03c2050b2c3bbe1d7697c253d923175d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083793"
---
# <a name="typename-element-for-types-format"></a>Types에 대한 TypeName 요소(형식)

선택 영역 집합에 속한 개체의.NET 유형을 지정 합니다.

구성 요소 (형식) SelectionSets 요소 (형식) SelectionSet 요소 (형식) 형식은 (형식) TypeName 요소 형식 (형식)

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</Name>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TypeName` 요소입니다. 하나 이상의 `TypeName` 요소 선택 집합에 포함 되어야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[형식 요소 (형식)](./types-element-for-selectionset-format.md)|선택 영역에 설정 된.NET 개체를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식에 대 한 정규화 된 이름을 지정 합니다.

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 뷰를 정의할 때 각 보기 내에서 모든 개체를 나열 하는 대신 설정 선택 항목의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.

서식 파일의 뷰를 정의 하는 경우 일반적인 선택 집합 이름으로 지정 됩니다. 이러한 경우에는 `SelectionSetName` 자식 요소는 `ViewSelectedBy` 뷰에 대 한 요소 집합을 지정 합니다. 그러나 뷰의 다른 항목 보기의 해당 항목에만 적용 되는 선택 집합을 지정할 수도 있습니다. 선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

## <a name="example"></a>예제

다음 예제와 `SelectionSet` .NET 유형은 정의 하는 요소입니다.

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

[선택 영역 집합을 정의](./defining-selection-sets.md)

[SelectionSet 요소 (형식)](./selectionset-element-format.md)

[SelectionSets 요소 (형식)](./selectionsets-element-format.md)

[형식 요소 (형식)](./types-element-for-selectionset-format.md)

[서식 파일을 Windows PowerShell을 작성](./writing-a-powershell-formatting-file.md)
