---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 Frame에 대한 FirstLineIndent 요소(형식)
description: View에 대한 CustomControl의 Frame에 대한 FirstLineIndent 요소(형식)
ms.openlocfilehash: 8dce8b4b072b754c3b7d631b3e5c321a5a3e5a3e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645878"
---
# <a name="firstlineindent-element-for-frame-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 Frame에 대한 FirstLineIndent 요소(형식)

첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) Viewcontrolelement (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 customentries 요소에 대 한 CustomEntries의 customentries 요소에 대 한 customentries 요소에 대 한 Customentries 요소

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
|[View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 줄을 이동할 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 [Firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[View에 대한 CustomControl의 Frame에 대한 FirstLineHanging 요소(형식)](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
