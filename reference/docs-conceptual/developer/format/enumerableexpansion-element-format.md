---
title: EnumerableExpansion 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368752"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion 요소(형식)

특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.

Configuration 요소 (Format) DefaultSettings 요소 (Format) EnumerableExpansions 요소 (format) Enumerableexpansions 요소 (Format)

## <a name="syntax"></a>구문

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `EnumerableExpansion` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 이 정의에 의해 확장 되는 .NET 컬렉션 개체를 정의 합니다.|
|[Expand 요소 (Format)](./expand-element-format.md)|이 정의에 대해 컬렉션 개체를 확장 하는 방법을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansions 요소 (형식)](./enumerableexpansions-element-format.md)|.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 다양 한 방법을 정의 합니다.|

## <a name="remarks"></a>설명

이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다. 이 경우 컬렉션 개체는 **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.

기본 동작은 컬렉션에 있는 개체의 속성만 표시 하는 것입니다.

## <a name="see-also"></a>참고 항목

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
