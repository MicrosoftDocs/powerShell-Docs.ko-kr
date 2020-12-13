---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)
description: Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)
ms.openlocfilehash: fddb8ddbac7c9292a05cadfa31f98db6439a557d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659676"
---
# <a name="typename-element-for-selectioncondition-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 SelectionCondition에 대한 TypeName 요소(형식)

조건을 트리거하는 .NET 유형을 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (format) 컨트롤의 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 구성 (형식) Customentries 요소 구성에 대 한 컨트롤 (형식) EntrySelectedBy 요소 구성 (형식)에 대 한 컨트롤에 대 한 customentries에 대 한 컨트롤에 대 한 Customentries에 대 한 컨트롤에 대 한 SelectionCondition 요소

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
|[구성 (형식)에 대 한 CustomEntry에 대해 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)|컨트롤 정의를 사용 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[구성 (형식)에 대 한 CustomEntry에 대해 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
