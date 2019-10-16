---
title: GroupBy (형식)의 프레임에 대 한 FirstLineHanging 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cdcf66e-96a5-47b5-9269-b4330bde29f2
caps.latest.revision: 6
ms.openlocfilehash: 08db1f2d89c3fe6c1e9a5a522de3071425042c3f
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363822"
---
# <a name="firstlinehanging-element-for-frame-for-groupby-format"></a>GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)

첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 customitem 요소에 대 한 customitem에 대 한 CustomItem의 경우 groupby (형식)에 대 한 프레임의 groupby (format) FirstLineHanging 요소에 대 한 CustomControl입니다.

## <a name="syntax"></a>구문

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `FirstLineHanging` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-groupby-format.md)|데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 줄을 이동할 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[GroupBy의 프레임에 대 한 FirstLineIndent 요소 (형식)](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-groupby-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
