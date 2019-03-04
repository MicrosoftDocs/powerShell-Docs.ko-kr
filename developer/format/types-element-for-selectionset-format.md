---
title: SelectionSet (형식)에 대 한 요소 형식 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4606fec0-ff31-4d36-af68-227405335ec3
caps.latest.revision: 15
ms.openlocfilehash: 0427367efa2c8a7e352d718706d1341a0c8e3621
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862379"
---
# <a name="types-element-for-selectionset-format"></a>SelectionSet에 대한 Types 요소(형식)

선택 영역에 설정 된.NET 개체를 정의 합니다.

구성 요소 (형식) SelectionSets 요소 (형식) SelectionSet 요소 (형식) 형식 요소 (형식)

## <a name="syntax"></a>구문

```xml
<Types>
  <TypeName>Nameof.NetType</TypeName>
</Types>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Types` 요소입니다. 하나 이상의 자식 요소가 있어야 하지만 추가할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TypeName 요소의 형식 (형식)](./typename-element-for-types-format.md)|필수 요소입니다.<br /><br /> 선택 영역 집합에 속해 있는.NET 개체를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet 요소 (형식)](./selectionset-element-format.md)|집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.|

## <a name="remarks"></a>설명

이 요소에 의해 정의 된 개체 뷰의 정의 의해 뷰를 사용할 수 있는 선택 집합 구성 (뷰 정의가 여러 개 있을 수 있음)를 선택 조건을 지정할 때 또는 합니다.  선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

## <a name="example"></a>예제

이 예제에서는 `SelectionSet` .NET 유형은 정의 하는 요소입니다.

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

[개체 집합을 정의합니다.](./defining-selection-sets.md)

[SelectionSet 요소 (형식)](./selectionset-element-format.md)

[TypeName 요소의 형식 (형식)](./typename-element-for-types-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
