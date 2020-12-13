---
ms.date: 09/13/2016
ms.topic: reference
title: View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)
description: View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)
ms.openlocfilehash: ff481f13e6f16267bdda4c3053faebc96d9a6d3a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646052"
---
# <a name="customentry-element-for-customentries-for-customcontrol-for-view-format"></a>View에 대한 CustomControl의 CustomEntries에 대한 CustomEntry 요소(형식)

사용자 지정 컨트롤 뷰의 정의를 제공 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 Customentries 요소에 대 한 customentries 요소 (형식)

## <a name="syntax"></a>구문

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomEntry` . 정의에 표시 되는 항목을 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|선택적 요소입니다.<br /><br /> 사용자 지정 컨트롤 뷰의 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|
|[View 항목에 대 한 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)|사용자 지정 컨트롤 정의에 대 한 컨트롤을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View의 CustomControl에 대한 CustomEntries 요소(형식)](./customentries-element-for-customcontrol-for-view-format.md)|사용자 지정 컨트롤 뷰의 정의를 제공 합니다. 사용자 지정 컨트롤 뷰에서 하나 이상의 정의를 지정 해야 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 각 사용자 지정 컨트롤 뷰에 대해 정의가 하나만 필요 하지만 동일한 뷰를 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 정의가 여러 개 있을 수 있습니다. 이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.

## <a name="see-also"></a>참고 항목

[View에 대한 CustomControl 요소(형식)](./customcontrol-element-for-view-format.md)

[View 항목에 대 한 CustomItem 요소 (형식)](./customitem-element-for-customentry-for-customcontrol-for-view-format.md)

[View의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
