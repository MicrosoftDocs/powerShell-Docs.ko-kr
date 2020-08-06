---
title: View 컨트롤의 CustomItem에 대 한 Frame 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 5ade36c183a026cb9001a2abbe91d31638a87108
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773456"
---
# <a name="frame-element-for-customitem-for-controls-for-view-format"></a>View에 대한 Controls의 CustomItem에 대한 Frame 요소(형식)

데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for View (format) Customentries 요소에 대 한 컨트롤의 customentries 요소 뷰 (format)의 컨트롤에 대 한 Customentries 요소에 대 한 컨트롤의 customentries 요소입니다 (형식).

## <a name="syntax"></a>구문

```xml
<Frame>
  <LeftIndent>NumberOfCharactersToShift</LeftIndent>
  <RightIndent>NumberOfCharactersToShift</RightIndent>
  <FirstLineHanging>NumberOfCharactersToShift</FirstLineHanging>
  <FirstLineIndent>NumberOfCharactersToShift</FirstLineIndent>
  <CustomItem>...</CustomItem>
</Frame>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `Frame` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`CustomItem Element`|Required 요소|
|[뷰 컨트롤 프레임의 FirstLineHanging 요소 (형식)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 첫 번째 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.|
|[뷰 컨트롤의 프레임 요소 FirstLineIndent 요소 (형식)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 첫 번째 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.|
|[뷰 컨트롤 프레임의 왼쪽 들여쓰기 요소 (형식)](./leftindent-element-for-frame-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.|
|[View 컨트롤 프레임의 오른쪽 들여쓰기 요소 (형식)](./rightindent-element-for-frame-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)](./customitem-element-for-customentry-for-controls-for-view-format.md)|컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="remarks"></a>설명

같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-controls-for-view-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-controls-for-view-format.md) 요소를 지정할 수 없습니다 `Frame` .

## <a name="see-also"></a>참고 항목

[뷰 컨트롤 프레임의 FirstLineHanging 요소 (형식)](./firstlinehanging-element-for-frame-for-controls-for-view-format.md)

[뷰 컨트롤의 프레임 요소 FirstLineIndent 요소 (형식)](./firstlineindent-element-for-frame-for-controls-for-view-format.md)

[뷰 컨트롤 프레임의 왼쪽 들여쓰기 요소 (형식)](./leftindent-element-for-frame-for-controls-for-view-format.md)

[View 컨트롤 프레임의 오른쪽 들여쓰기 요소 (형식)](./rightindent-element-for-frame-for-controls-for-view-format.md)

[View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)](./customitem-element-for-customentry-for-controls-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
