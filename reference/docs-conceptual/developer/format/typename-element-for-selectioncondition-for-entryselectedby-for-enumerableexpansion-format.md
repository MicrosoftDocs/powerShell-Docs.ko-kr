---
title: EnumerableExpansion (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 TypeName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f47384be10705b913d52b5cc8cb4ecf9ba83f17c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787345"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)

조건을 트리거하는 .NET 유형을 지정 합니다.

구성 요소 DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format)에 대 한 요소 (형식)-enumerableexpansions (형식)에 대 한 entryselectedby에 대 한 By enumerableexpansions (형식)의 entryselectedby

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
|[EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예:)을 지정 합니다 `System.IO.DirectoryInfo` .

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[EnumerableExpansion의 EntrySelectedBy에 대한 SelectionCondition 요소(형식)](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
