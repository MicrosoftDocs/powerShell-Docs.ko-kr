---
title: SelectionSet (Format)의 Types 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367962"
---
# <a name="types-element-for-selectionset-format"></a>SelectionSet에 대한 Types 요소(형식)

선택 집합에 있는 .NET 개체를 정의 합니다.

Configuration 요소 (Format) SelectionSets 요소 (Format) Selectionsets 요소 (format) Types 요소 (Format)

## <a name="syntax"></a>구문

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `Types` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 자식 요소가 하나 이상 있어야 하지만 추가할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[형식의 TypeName 요소 (형식)](./typename-element-for-types-format.md)|필수 요소입니다.<br /><br /> 선택 집합에 속하는 .NET 개체를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet 요소 (형식)](./selectionset-element-format.md)|집합의 이름으로 참조할 수 있는 .NET 개체 집합을 정의 합니다.|

## <a name="remarks"></a>설명

이 요소에 의해 정의 되는 개체는 뷰에서 사용할 수 있는 선택 집합을 구성 합니다. 뷰 정의를 통해 뷰가 여러 정의를 가질 수 있습니다. 또는 선택 조건을 지정할 수 있습니다.  선택 집합에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 네 가지 .NET 형식을 정의 하는 `SelectionSet` 요소를 보여 줍니다.

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

[개체 집합 정의](./defining-selection-sets.md)

[SelectionSet 요소 (형식)](./selectionset-element-format.md)

[형식의 TypeName 요소 (형식)](./typename-element-for-types-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
