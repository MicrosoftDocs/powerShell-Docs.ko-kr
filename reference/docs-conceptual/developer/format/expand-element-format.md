---
ms.date: 09/13/2016
ms.topic: reference
title: Expand 요소(형식)
description: Expand 요소(형식)
ms.openlocfilehash: 518e132e3e74b921d4e51966fc60088a22ef63f1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667949"
---
# <a name="expand-element-format"></a>Expand 요소(형식)

이 정의에 대해 컬렉션 개체를 확장 하는 방법을 지정 합니다.

Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (format) Enumerableexpansions 요소 (format) Expand 요소 (Format)

## <a name="syntax"></a>구문

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Expand` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion 요소(형식)](./enumerableexpansion-element-format.md)|특정 .NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

다음 값 중 하나를 지정합니다.

- EnumOnly: 컬렉션에 있는 개체의 속성만 표시 합니다.

- CoreOnly: 컬렉션 개체의 속성만 표시 합니다.

- Both: 컬렉션의 개체 속성 및 컬렉션 개체의 속성을 표시 합니다.

## <a name="remarks"></a>설명

이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다. 이 경우 컬렉션 개체는  **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.

기본 동작은 컬렉션에 있는 개체의 속성만 표시 하는 것입니다.

## <a name="see-also"></a>참고 항목

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
