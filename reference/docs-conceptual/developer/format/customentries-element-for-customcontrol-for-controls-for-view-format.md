---
title: View 컨트롤의 CustomControl에 대 한 CustomEntries 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72368812"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>View에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)

컨트롤에 대 한 정의를 제공 합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) 컨트롤 요소 컨트롤에 대 한 컨트롤의 요소 (format) 컨트롤 요소 뷰 (format) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤의 요소입니다. CustomControl for Controls (Format)

## <a name="syntax"></a>구문

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `CustomEntries` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다. 지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰의 컨트롤에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-controls-for-view-format.md)|필수 요소입니다.<br /><br /> 컨트롤의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 컨트롤의 컨트롤에 대 한 CustomControl 요소 (형식)](./customcontrol-element-for-control-for-controls-for-view-format.md)|뷰에 사용 되는 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 컨트롤에는 단일 `CustomEntry` 요소에 지정 된 정의가 하나만 있습니다. 그러나 같은 컨트롤을 사용 하 여 서로 다른 .NET 개체를 표시 하려는 경우에는 여러 정의를 제공할 수 있습니다. 이러한 경우 각 개체 또는 개체 집합에 대 한 `CustomEntry` 요소를 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[뷰의 컨트롤에 대 한 CustomEntry 요소 (형식)](./customentry-element-for-customentries-for-controls-for-view-format.md)

[View 컨트롤의 컨트롤에 대 한 CustomControl 요소 (형식)](./customcontrol-element-for-control-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
