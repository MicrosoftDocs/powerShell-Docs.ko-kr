---
title: EnumerableExpansions 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50c33892-2ade-44c2-906c-81e5f5ca21f2
caps.latest.revision: 9
ms.openlocfilehash: 1ecbda8a3b623757517019105e3b1ee46ccbb55c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860259"
---
# <a name="enumerableexpansions-element-format"></a>EnumerableExpansions 요소(형식)

.NET 컬렉션 개체를 보기에 표시 될 때 확장 되는 방법을 정의 합니다.

구성 요소 (형식) DefaultSettings (형식) EnumerableExpansions 요소 (형식)

## <a name="syntax"></a>구문

```xml
<EnumerableExpansions>
  <EnumerableExpansion>...</EnumerableExpansion>
</EnumerableExpansions>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `EnumerableExpansions` 요소입니다. 사용할 수 있는 자식 요소의 수에 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[EnumerableExpansion 요소 (형식)](./enumerableexpansion-element-format.md)|선택적 요소입니다.<br /><br /> 보기에 표시 될 때 확장 되는 특정.NET 컬렉션 개체를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[DefaultSettings 요소 (형식)](./defaultsettings-element-format.md)|서식 파일의 모든 뷰에 적용 되는 일반적인 설정을 정의 합니다.|

## <a name="remarks"></a>설명

이 요소를 사용 하 여 컬렉션 개체 및 컬렉션의 개체 표시 되는 방식을 정의 합니다. 컬렉션 개체를 지 원하는 개체를 참조 하는 경우에 **System.Collections.ICollection** 인터페이스입니다.

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
