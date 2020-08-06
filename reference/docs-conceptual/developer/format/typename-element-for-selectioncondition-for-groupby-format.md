---
title: GroupBy (형식)에 대 한 SelectionCondition의 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ea1e0cb50c3a749f6c26d13fff4b001240ce6b95
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772555"
---
# <a name="typename-element-for-selectioncondition-for-groupby-format"></a>GroupBy의 SelectionCondition에 대한 TypeName 요소(형식)

조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl groupby (형식)에 대 한 CustomControl의 경우에는 groupby (형식)에 대 한 SelectionCondition 요소에 대해 groupby (형식)에 대 한 Customentries 요소에 대 한

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</TypeName>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `TypeName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .

## <a name="remarks"></a>설명

이 요소를 지정 하면 요소를 지정할 수 없습니다 `SelectionSetName` . 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[GroupBy의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
