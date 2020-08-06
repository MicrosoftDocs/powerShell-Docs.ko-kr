---
title: 뷰의 컨트롤에 대 한 CustomEntry 요소 (형식) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4fc960ab803580f684ce0f224b1db4d7d4af1720
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785900"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a>View에 대한 Controls의 CustomEntries에 대한 CustomEntry 요소(형식)

컨트롤의 정의를 제공 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format) 컨트롤에 대 한 컨트롤의 컨트롤 요소 (format) CustomControl 요소 컨트롤의 컨트롤에 대 한 컨트롤의 요소 (format) Customentries 요소에 대 한 컨트롤의 컨트롤에 대 한 CustomEntries 요소

## <a name="syntax"></a>구문

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomEntry` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 Controls의 CustomEntry에 대한 EntrySelectedBy 요소(형식)](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤 정의를 사용 하는 .NET 형식 또는이 정의를 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|
|[View에 대한 Controls의 CustomEntry에 대한 CustomItem 요소(형식)](./customitem-element-for-customentry-for-controls-for-view-format.md)|필수적 요소입니다.<br /><br /> 컨트롤에서 데이터를 표시 하는 방법을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View의 CustomControl에 대한 CustomEntries 요소(형식)](./customentries-element-for-customcontrol-for-view-format.md)|컨트롤에 대 한 정의를 제공 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[View의 CustomControl에 대한 CustomEntries 요소(형식)](./customentries-element-for-customcontrol-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
