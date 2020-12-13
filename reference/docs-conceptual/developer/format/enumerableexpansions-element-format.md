---
ms.date: 09/13/2016
ms.topic: reference
title: EnumerableExpansions 요소(형식)
description: EnumerableExpansions 요소(형식)
ms.openlocfilehash: 789599e6ff368b4685c7937d5b6eb38618752f9e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660185"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions 요소(형식)

.NET 컬렉션 개체가 뷰에 표시 될 때 확장 되는 방법을 정의 합니다.

Configuration 요소 (Format) DefaultSettings 요소 (format) EnumerableExpansions 요소 (Format)

## <a name="syntax"></a>구문

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `EnumerableExpansions` . 사용할 수 있는 자식 요소 수에는 제한이 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion 요소(형식)](./enumerableexpansion-element-format.md)|선택적 요소입니다.<br /><br /> 뷰에 표시 될 때 확장 되는 특정 .NET 컬렉션 개체를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[DefaultSettings 요소(형식)](./defaultsettings-element-format.md)|서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.|

## <a name="remarks"></a>설명

이 요소는 컬렉션 개체와 컬렉션의 개체가 표시 되는 방식을 정의 하는 데 사용 됩니다. 이 경우 컬렉션 개체는  **Collections** 인터페이스를 지 원하는 개체를 참조 합니다.

## <a name="see-also"></a>참고 항목

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
