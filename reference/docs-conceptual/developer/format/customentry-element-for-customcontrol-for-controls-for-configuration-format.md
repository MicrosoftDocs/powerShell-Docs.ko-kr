---
title: 구성 (형식)에 대 한 CustomControl의 CustomEntry 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dfba86f-29b2-473c-9e98-9d679176acce
caps.latest.revision: 11
ms.openlocfilehash: 497485a388d1cdc834ecc1d1079b0714a7d7f9db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364072"
---
# <a name="customentry-element-for-customcontrol-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 CustomControl에 대한 CustomEntry 요소(형식)

공용 컨트롤의 정의를 제공 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 요소의 구성 (format) CustomControl 요소에 대 한 Control 요소 구성의 CustomControl에 대 한 구성 (형식) CustomEntries 요소 Format) 구성에 대 한 CustomControl의 CustomEntry 요소 (형식)

## <a name="syntax"></a>구문

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `CustomEntry` 요소의 부모 요소에 대해 설명 합니다. 정의에 표시 되는 항목을 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 컨트롤의 CustomEntry에 대 한 EntrySelectedBy 요소 (형식)](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤의 정의를 사용 하는 .NET 형식 또는이 컨트롤을 사용 하기 위해 존재 해야 하는 조건을 정의 합니다.|
|[구성에 대 한 컨트롤 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)|필수적 요소입니다.<br /><br /> 컨트롤에 표시 되는 데이터와 표시 방법을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 CustomControl의 CustomEntries 요소 (형식)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|공용 컨트롤의 정의를 제공 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 각 공용 사용자 지정 컨트롤에는 하나의 정의만 필요 하지만 동일한 컨트롤을 사용 하 여 다른 .NET 개체를 표시 하려는 경우에는 정의가 여러 개 있을 수 있습니다. 이러한 경우 각 개체 또는 개체 집합에 대 한 별도의 정의를 제공할 수 있습니다.

## <a name="see-also"></a>참고 항목

[구성에 대 한 CustomControl의 CustomEntries 요소 (형식)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[구성에 대 한 컨트롤 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-controls-for-configuration-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
