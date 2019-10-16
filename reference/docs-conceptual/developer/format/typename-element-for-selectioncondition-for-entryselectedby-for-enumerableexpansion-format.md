---
title: EnumerableExpansion (형식)의 경우 EntrySelectedBy에 대 한 SelectionCondition의 TypeName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9100ab7-fbdc-4c0d-bb56-57669ef42b95
caps.latest.revision: 9
ms.openlocfilehash: 316e54d11647aedc1552a0bb74b943de7e4e3588
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361582"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a>EnumerableExpansion에 대한 EntrySelectedBy의 SelectionCondition에 대한 TypeName 요소(형식)

조건을 트리거하는 .NET 유형을 지정 합니다.

구성 요소 DefaultSettings 요소 (format) enumerableexpansions 요소 (format) enumerableexpansions 요소 (format) EntrySelectedBy 요소에 대 한 요소 (format) SelectionCondition 요소에 대 한 EnumerableExpansion (Format) TypeName 요소 (형식)에 대 한 EntrySelectedBy의 SelectionCondition

## <a name="syntax"></a>구문

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `TypeName` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|이 정의의 컬렉션 개체를 확장 하기 위해 있어야 하는 조건을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

.NET 형식의 정규화 된 이름 (예: `System.IO.DirectoryInfo`)을 지정 합니다.

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[EnumerableExpansion (형식)에 대 한 EntrySelectedBy의 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
