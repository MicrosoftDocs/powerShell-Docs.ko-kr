---
title: View (Format)의 CustomControl에 대 한 Frame의 FirstLineIndent 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bb4e1564-3fd3-4be3-b93e-ac90480e05c0
caps.latest.revision: 6
ms.openlocfilehash: 3130ecc69f7d1568bcbd392dd24e8cdcc3382905
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363062"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 Frame에 대한 FirstLineIndent 요소(형식)

첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 view (format) Customentries 요소에 대 한 CustomEntries 요소 CustomControl for View (Format) FirstLineIndent 요소에 대 한 Customentry에 대 한 CustomControlView (Format) Frame 요소의 CustomEntry

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
|[CustomControl의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 줄을 이동할 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 [Firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[보기에 대 한 CustomControl Frame의 FirstLineHanging 요소 (형식)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[CustomControl의 CustomItem에 대 한 Frame 요소 (형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
