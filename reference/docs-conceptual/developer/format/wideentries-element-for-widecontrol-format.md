---
title: WideControl에 대 한 WideEntries 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 74383b288c945008c1d7b5119363a166c04802ae
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785050"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideControl에 대한 WideEntries 요소(형식)

넓은 뷰의 정의를 제공 합니다. 넓은 보기는 하나 이상의 정의를 지정 해야 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) WideControl Element (format) WideEntries Element (Format)

## <a name="syntax"></a>구문

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `WideEntries` . 하나 이상의 자식 요소를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry 요소 (Format)](./wideentry-element-for-widecontrol-format.md)|넓은 뷰의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideControl 요소(형식)](./widecontrol-element-format.md)|뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.|

## <a name="remarks"></a>설명

넓은 보기는 각 개체에 대 한 단일 속성 값 또는 스크립트 값을 표시 하는 목록 형식입니다. 넓은 보기의 구성 요소에 대 한 자세한 내용은 [Wide View 구성 요소](./creating-a-wide-view.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 `WideEntries` 단일 요소를 정의 하는 요소를 보여 줍니다 `WideEntry` . `WideEntry`요소는 `WideItem` 뷰에 표시 되는 속성 또는 스크립트 값을 정의 하는 단일 요소를 포함 합니다.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

넓은 보기의 전체 예제는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[넓게 보기 만들기](./creating-a-wide-view.md)

[WideControl 요소(형식)](./widecontrol-element-format.md)

[WideEntry 요소 (Format)](./wideentry-element-for-widecontrol-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
