---
title: 구성 (형식)의 컨트롤용 프레임에 대 한 FirstLineIndent 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9ac1d8dc74af12b87f0b490d7c1f75d028e3521f
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773592"
---
# <a name="firstlineindent-element-for-frame-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 Frame에 대한 FirstLineIndent 요소(형식)

첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (format) 컨트롤 요소 구성 (format) CustomControl 요소에 대 한 컨트롤의 요소 구성 (format) CustomEntries 요소에 대 한 CustomControl for Configuration (format) Customentries 요소 CustomControl for Controls for configuration (Format) Customentries 요소에 대 한 컨트롤의 customentries 요소 구성의 컨트롤에 대 한 Customentries 요소

## <a name="syntax"></a>구문

```xml
<FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `FirstLineIndent` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-controls-for-configuration-format.md)|데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 줄을 이동할 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 [Firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 Frame에 대한 FirstLineHanging 요소(형식)](./firstlinehanging-element-for-frame-for-controls-for-configuration-format.md)

[Configuration에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
