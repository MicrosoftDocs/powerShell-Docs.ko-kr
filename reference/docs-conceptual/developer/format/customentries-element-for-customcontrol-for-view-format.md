---
ms.date: 09/13/2016
ms.topic: reference
title: View의 CustomControl에 대한 CustomEntries 요소(형식)
description: View의 CustomControl에 대한 CustomEntries 요소(형식)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649973"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a>View의 CustomControl에 대한 CustomEntries 요소(형식)

사용자 지정 컨트롤 뷰의 정의를 제공 합니다. 사용자 지정 컨트롤 뷰에서 하나 이상의 정의를 지정 해야 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) CustomControl Element (format) CustomEntries 요소에 대 한 CustomControl for View (Format)

## <a name="syntax"></a>구문

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlEntries` . 하나 이상의 자식 요소를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|필수적 요소입니다.<br /><br /> 사용자 지정 컨트롤 뷰의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 CustomControl 요소(형식)](./customcontrol-element-for-view-format.md)|필수적 요소입니다.<br /><br /> 뷰의 사용자 지정 컨트롤 형식을 정의 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 컨트롤에는 단일 요소에 정의 된 정의가 하나만 있습니다 `CustomEntry` . 그러나 같은 컨트롤을 사용 하 여 서로 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 사용할 수 있습니다. 이러한 경우 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소를 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[View에 대한 CustomControl 요소(형식)](./customcontrol-element-for-view-format.md)

[뷰의 Customentry 요소에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
