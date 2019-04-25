---
title: 확장 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: faa0314b-f6f1-44fd-ad2b-b00cbe38923f
caps.latest.revision: 9
ms.openlocfilehash: 8b924c989133b47e4d95d8429778003c76595d58
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066008"
---
# <a name="expand-element-format"></a>Expand 요소(형식)

이 정의 대 한 컬렉션 개체는 확장 하는 방법을 지정 합니다.

구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식) EnumerableExpansion 요소 (형식) (형식) 요소를 확장 합니다.

## <a name="syntax"></a>구문

```xml
<Expand>EnumOnly, CoreOnly, Both</Expand>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Expand` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion 요소 (형식)](./enumerableexpansion-element-format.md)|개체는 뷰에서 표시 되는 확장은 어떻게 특정.NET 컬렉션을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

다음 값 중 하나를 지정 합니다.

- EnumOnly: 컬렉션에서 개체의 속성만 표시합니다.

- CoreOnly: 컬렉션 개체의 속성만 표시합니다.

- 모두: 컬렉션 및 컬렉션 개체의 속성에서 개체의 속성을 표시합니다.

## <a name="remarks"></a>설명

이 요소를 사용 하 여 컬렉션 개체 및 컬렉션의 개체 표시 되는 방식을 정의 합니다. 컬렉션 개체를 지 원하는 개체를 참조 하는 경우에 **System.Collections.ICollection** 인터페이스입니다.

기본 동작은 컬렉션에서 개체의 속성만 표시 됩니다.

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
