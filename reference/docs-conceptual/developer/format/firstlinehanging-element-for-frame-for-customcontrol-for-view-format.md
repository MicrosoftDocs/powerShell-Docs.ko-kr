---
title: 보기에 대 한 CustomControl Frame의 FirstLineHanging 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: fa428c1fbe4cd8070e40cf0bc732eb335489ba4e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773643"
---
# <a name="firstlinehanging-element-for-frame-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 Frame에 대한 FirstLineHanging 요소(형식)

첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소 (형식) Customentries 요소 customentries에 대 한 customentries의 Customentries에 대 한 CustomControl for View (Format) FirstLineHanging 요소에 대 한 CustomControl for Frame for View (format)

## <a name="syntax"></a>구문

```xml
<FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `FirstLineHanging` .

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

이 요소를 지정 하는 경우 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[View에 대한 CustomControl의 Frame에 대한 FirstLineIndent 요소(형식)](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
