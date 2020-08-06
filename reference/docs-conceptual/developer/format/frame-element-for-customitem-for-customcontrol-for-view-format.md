---
title: CustomControl의 CustomItem에 대 한 Frame 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4864ea1a865f77c9de6e495d7e8296e81c19b366
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781446"
---
# <a name="frame-element-for-customitem-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomItem에 대한 Frame 요소(형식)

데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 사용자 지정 컨트롤 뷰를 정의할 때 사용 됩니다.

Configuration 요소 (Format) Viewcontrolelement (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소에 대 한 customentries 요소

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
|[FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.|
|[FirstLineIndent 요소](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.|
|[왼쪽 들여쓰기 요소](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.|
|[RightIndent 요소](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 항목에 대 한 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="remarks"></a>설명

같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md) 요소를 지정할 수 없습니다 `Frame` .

## <a name="see-also"></a>참고 항목

[FirstLineHanging 요소](./firstlinehanging-element-for-frame-for-customcontrol-for-view-format.md)

[FirstLineIndent 요소](./firstlineindent-element-for-frame-for-customcontrol-for-view-format.md)

[왼쪽 들여쓰기 요소](./leftindent-element-for-frame-for-customcontrol-for-view-format.md)

[RightIndent 요소](./rightindent-element-for-frame-for-customcontrol-for-view-format.md)

[View 항목에 대 한 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
