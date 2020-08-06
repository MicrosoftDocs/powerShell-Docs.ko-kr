---
title: GroupBy (Format)의 프레임에 대 한 FirstLineIndent 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: def5b4e9ca98a15edbb36675ca506e886de567dc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781667"
---
# <a name="firstlineindent-element-for-frame-for-groupby-format"></a>GroupBy의 Frame에 대한 FirstLineIndent 요소(형식)

첫 번째 데이터 줄이 오른쪽으로 이동 하는 문자 수를 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

구성 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) CustomControl 요소의 groupby (format) CustomEntries 요소에 대해 groupby (format) customentries에 대 한 CustomControl 요소 groupby (format) Customentries 요소에 대 한 CustomControl 요소의 경우 customentries에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 Customentries에 대 한 FirstLineIndent 요소에 대 한 groupby (형식)

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
|[GroupBy의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-groupby-format.md)|데이터를 왼쪽 또는 오른쪽으로 이동 하는 것과 같이 데이터를 표시 하는 방법을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

데이터의 첫 줄을 이동할 문자 수를 지정 합니다.

## <a name="remarks"></a>설명

이 요소를 지정 하는 경우 [Firstlinehanging](./firstlinehanging-element-for-frame-for-groupby-format.md) 요소를 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[GroupBy의 Frame에 대한 FirstLineHanging 요소(형식)](./firstlinehanging-element-for-frame-for-groupby-format.md)

[GroupBy의 CustomItem에 대한 Frame 요소(형식)](./frame-element-for-customitem-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
