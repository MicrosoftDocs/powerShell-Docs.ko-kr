---
title: WideEntry 요소 WideControl (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 014763cb-7716-4931-899c-8375b5d7a3dd
caps.latest.revision: 15
ms.openlocfilehash: d1d13b5c3436871053353814293d9163ea13c7fb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856529"
---
# <a name="wideentry-element-for-widecontrol-format"></a>WideControl에 대한 WideEntry 요소(형식)

넓은 보기의 정의 제공 합니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) WideControl 요소 (형식) WideEntries 요소 (형식) WideEntry 요소 (형식)

## <a name="syntax"></a>구문

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `WideEntry` 요소입니다. 단일 지정 해야 `WideItem` 자식 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[WideEntry (형식)에 대 한 EntrySelectedBy 요소](./entryselectedby-element-for-wideentry-format.md)|선택적 요소입니다.<br /><br /> 이 와이드 항목 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|
|[WideItem 요소 (형식)](./wideitem-element-for-widecontrol-format.md)|필수 요소입니다.<br /><br /> 속성 또는 해당 값이 표시 되는 스크립트를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[WideEntries 요소 (형식)](./wideentries-element-for-widecontrol-format.md)|넓은 보기의 정의 제공합니다.|

## <a name="remarks"></a>설명

와이드 보기인 경우에 단일 속성 값 또는 각 개체에 대 한 스크립트 값을 표시 하는 목록 형식입니다. 뷰의 다른 형식과 달리 각 뷰 정의 대해 하나의 항목 요소를 지정할 수 있습니다. 넓은 보기의 다른 구성 요소에 대 한 자세한 내용은 참조 [넓은 보기를 만드는](./creating-a-wide-view.md)합니다.

## <a name="example"></a>예제

에서는 다음 예제는 `WideEntry` 단일 정의 하는 요소 `WideItem` 요소입니다. `WideItem` 요소 값은 뷰에 표시 속성을 정의 합니다.

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

넓은 보기가의 전체 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

## <a name="see-also"></a>참고 항목

[넓은 보기 만들기](./creating-a-wide-view.md)

[WideEntry (형식)에 대 한 SelectionCondition 요소](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (형식)에 대 한 SelectionSetName 요소](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[WideEntry (형식)에 대 한 TypeName 요소](./typename-element-for-entryselectedby-for-wideentry-format.md)

[WideEntries 요소 (형식)](./wideentries-element-for-widecontrol-format.md)

[WideItem 요소 (형식)](./wideitem-element-for-widecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
