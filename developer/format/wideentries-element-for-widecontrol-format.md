---
title: WideEntries 요소 WideControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0c4bff45-0960-4b3a-95e7-47f2cee03ac5
caps.latest.revision: 12
ms.openlocfilehash: 083f3c8df8136858e32778ed231943ef983e47aa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083691"
---
# <a name="wideentries-element-for-widecontrol-format"></a>WideControl에 대한 WideEntries 요소(형식)

넓은 보기의 정의 제공합니다. 와이드 보기인 경우 하나 이상의 정의 지정 해야 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식)

## <a name="syntax"></a>구문

```xml
<WideEntries>
  <WideEntry>...</WideEntry>
</WideEntries>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideEntries` 요소입니다. 하나 이상의 자식 요소를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry 요소 (형식)](./wideentry-element-for-widecontrol-format.md)|넓은 보기의 정의 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideControl 요소 (형식)](./widecontrol-element-format.md)|와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다.|

## <a name="remarks"></a>설명

와이드 보기인 경우에 단일 속성 값 또는 각 개체에 대 한 스크립트 값을 표시 하는 목록 형식입니다. 넓은 보기의 구성 요소에 대 한 자세한 내용은 참조 [뷰 구성 요소를 와이드](./creating-a-wide-view.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `WideEntries` 단일 정의 하는 요소 `WideEntry` 요소입니다. 합니다 `WideEntry` 하나를 포함 하는 요소 `WideItem` 뷰에서 어떤 스크립트나 속성 값이 표시를 정의 하는 요소입니다.

```xml
<WideControl>
  <WideEntries>
    <WideEntry>
      <WideItem>...</WideItem>
    <WideEntry>
  </WideEntries>
</WideControl>
```

넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

## <a name="see-also"></a>참고 항목

[넓은 보기 만들기](./creating-a-wide-view.md)

[WideControl 요소 (형식)](./widecontrol-element-format.md)

[WideEntry 요소 (형식)](./wideentry-element-for-widecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
