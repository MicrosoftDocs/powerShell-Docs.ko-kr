---
title: GroupBy (형식)에 대 한 CustomControl CustomEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860369"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)

컨트롤의 정의 제공합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 GroupBy (형식)에 대 한 CustomControl

## <a name="syntax"></a>구문

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `CustomEntry` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤 정의 또는이 정의를 사용할 수 있어야 하는 조건을 사용 하는.NET 형식을 정의 합니다.|
|[GroupBy (형식)에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-groupby-format.md)|필수 요소입니다.<br /><br /> 컨트롤에서 데이터를 표시 하는 방법을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-groupby-format.md)|컨트롤에 대 한 정의 제공합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 CustomEntry EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomEntry CustomItem 요소](./customitem-element-for-customentry-for-groupby-format.md)

[GroupBy (형식)에 대 한 CustomControl CustomEntries 요소](./customentries-element-for-customcontrol-for-groupby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
