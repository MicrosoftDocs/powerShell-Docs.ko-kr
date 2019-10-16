---
title: FirstLineIndent 요소 (형식)에 대 한 컨트롤의 프레임 Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec63f4f9-8858-4529-8646-ffbbc278f83e
caps.latest.revision: 7
ms.openlocfilehash: 694c5baaa5e90a772257276ba139d90acf7ec0e3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363092"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-view-format"></a>View에 대한 Controls의 Frame에 대한 FirstLineIndent 요소(형식)

첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for View (format) CustomEntry 요소에 대 한 컨트롤의 customentry 요소 뷰 (format)의 컨트롤에 대 한 customentry 요소 뷰 (format)의 컨트롤에 대 한 Customentry의 경우 프레임 요소 보기의 컨트롤 (형식)

## <a name="syntax"></a>구문

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `FirstLineIndent` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-controls-for-view-format.md)|데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 줄을 이동할 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 [Firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[뷰의 컨트롤 프레임에 대 한 FirstLineHanging 요소 (형식)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
