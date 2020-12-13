---
ms.date: 09/13/2016
ms.topic: reference
title: GroupBy의 CustomItem에 대한 Frame 요소(형식)
description: GroupBy의 CustomItem에 대한 Frame 요소(형식)
ms.openlocfilehash: 86b51766974ebfcae06583ade237a77c6db92866
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652172"
---
# <a name="frame-element-for-customitem-for-groupby-format"></a>GroupBy의 CustomItem에 대한 Frame 요소(형식)

데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)의 groupby 요소 (format) CustomControl 요소에 대 한 CustomControl의 Customentries 요소 (groupby)의 경우 CustomControl에 대 한 customentries 요소 (형식)의 경우 customentries 요소에 대 한 Customentries 요소

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
|[GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)](./firstlinehanging-element-for-frame-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 첫 번째 데이터 줄이 왼쪽으로 이동 하는 문자 수를 지정 합니다.|
|[GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)](./firstlineindent-element-for-frame-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다.|
|[GroupBy의 Frame에 대한 LeftIndent 요소(형식)](./leftindent-element-for-frame-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 왼쪽 여백에서 데이터를 이동할 문자 수를 지정 합니다.|
|[GroupBy의 프레임에 대 한 Rightindent 요소 (형식)](./rightindent-element-for-frame-for-groupby-format.md) RightIndent 요소|선택적 요소입니다.<br /><br /> 데이터가 오른쪽 여백에서 벗어나 이동 하는 문자 수를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)](./customitem-element-for-customentry-for-groupby-format.md)|컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="remarks"></a>설명

같은 요소에서 [Firstlinehanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 및 [FirstLineIndent](./firstlineindent-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다 `Frame` .

## <a name="see-also"></a>참고 항목

[GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)](./firstlineindent-element-for-frame-for-groupby-format.md)

[GroupBy의 Frame에 대한 LeftIndent 요소(형식)](./leftindent-element-for-frame-for-groupby-format.md)

[GroupBy의 Frame에 대한 RightIndent 요소(형식)](./rightindent-element-for-frame-for-groupby-format.md)

[GroupBy의 CustomEntry에 대한 CustomItem 요소(형식)](./customitem-element-for-customentry-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
