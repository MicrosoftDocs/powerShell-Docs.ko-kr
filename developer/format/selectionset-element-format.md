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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861159"
---
# <a name="selectionset-element-format"></a>SelectionSet 요소(형식)

집합의 이름으로 참조할 수 있는.NET 개체 집합을 정의 합니다.

구성 요소 (형식) SelectionSets 요소 (형식) SelectionSet 요소 (형식)

## <a name="syntax"></a>구문

```xml
<SelectionSet>
  <Name>SelectionSetName</Name>
  <Types>...</Types>
</SelectionSet>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `SelectionSet` 요소입니다. 각 선택 집합에는 이름이 있어야 합니다. 한 집합의.NET 개체를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSet (형식)의 name 요소](./name-element-for-selectionset-format.md)|필수 요소입니다.<br /><br /> 선택 영역 집합을 참조 하는 데 사용 하는 이름을 지정 합니다.|
|[형식 요소 (형식)](./types-element-for-selectionset-format.md)|필수 요소입니다.<br /><br /> 선택 영역에 설정 된.NET 개체를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SelectionSets 요소 형식](./selectionsets-element-format.md)|서식 파일의 모든 보기에서 사용할 수 있는.NET 개체의 공통 집합을 정의 합니다.|

## <a name="remarks"></a>설명

상속을 통해 관련 된 개체와 같이 단일 이름을 사용 하 여 참조 하려는 관련된 개체 집합이 있는 경우 선택 집합을 사용할 수 있습니다. 뷰를 정의할 때 각 보기 내에서 모든 개체를 나열 하는 대신 설정 선택 항목의 이름을 사용 하 여 개체 집합을 지정할 수 있습니다.

서식 파일의 뷰 또는 뷰의 정의 정의 하는 경우 일반적인 선택 집합 이름으로 지정 됩니다. 이러한 경우에는 `SelectionSetName` 자식 요소를 `ViewSelectedBy` 및 `EntrySelectedBy` 요소에 사용할 집합을 지정 합니다. 선택 영역 집합에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

## <a name="example"></a>예제

다음 예제와 `SelectionSet` .NET 유형은 정의 하는 요소입니다.

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

[SelectionSet (형식)의 name 요소](./name-element-for-selectionset-format.md)

[SelectionSets 요소 (형식)](./selectionsets-element-format.md)

[형식 요소 (형식)](./types-element-for-selectionset-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
