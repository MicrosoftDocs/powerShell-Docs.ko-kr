---
title: GroupBy (형식)에 대 한 CustomControl의 CustomEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2987cb45-f646-45d4-b81b-7871e77af36f
caps.latest.revision: 5
ms.openlocfilehash: dcf4f8b2bbd422067ffdf9b3b4972e279e91edf9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364062"
---
# <a name="customentry-element-for-customcontrol-for-groupby-format"></a>GroupBy의 CustomControl에 대한 CustomEntry 요소(형식)

컨트롤의 정의를 제공 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl GroupBy (형식)에 대 한 CustomControl

## <a name="syntax"></a>구문

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `CustomEntry` 요소의 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomEntry의 EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|
|[GroupBy (형식)에 대 한 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-groupby-format.md)|필수적 요소입니다.<br /><br /> 컨트롤에서 데이터를 표시 하는 방법을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)의 CustomControl에 대 한 CustomEntries 요소](./customentries-element-for-customcontrol-for-groupby-format.md)|컨트롤에 대 한 정의를 제공 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 CustomEntry의 EntrySelectedBy 요소](./entryselectedby-element-for-customentry-for-groupby-format.md)

[GroupBy (형식)에 대 한 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-groupby-format.md)

[GroupBy (형식)의 CustomControl에 대 한 CustomEntries 요소](./customentries-element-for-customcontrol-for-groupby-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
