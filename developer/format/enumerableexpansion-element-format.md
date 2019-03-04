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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856839"
---
# <a name="enumerableexpansion-element-format"></a>EnumerableExpansion 요소(형식)

개체는 뷰에서 표시 되는 확장은 어떻게 특정.NET 컬렉션을 정의 합니다.

구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식)

## <a name="syntax"></a>구문

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EnumerableExpansion` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-enumerableexpansion-format.md)|선택적 요소입니다.<br /><br /> 이 정의 의해 확장 되는.NET 컬렉션 개체를 정의 합니다.|
|[요소 (형식)를 확장 합니다.](./expand-element-format.md)|이 정의 대 한 컬렉션 개체는 확장 하는 방법을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansions 요소 (형식)](./enumerableexpansions-element-format.md)|다양 한 방법을 개체 뷰의 표시 될 때 확장 되는.NET 컬렉션을 정의 합니다.|

## <a name="remarks"></a>설명

이 요소를 사용 하 여 컬렉션 개체 및 컬렉션의 개체 표시 되는 방식을 정의 합니다. 컬렉션 개체를 지 원하는 개체를 참조 하는 경우에 **System.Collections.ICollection** 인터페이스입니다.

기본 동작은 컬렉션에서 개체의 속성만 표시 됩니다.

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
