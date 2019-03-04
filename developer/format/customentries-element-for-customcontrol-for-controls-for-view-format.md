---
title: 뷰 (형식)에 대 한 컨트롤에 대 한 CustomControl CustomEntries 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3485958a-ba87-4932-907c-a8f140c4abdb
caps.latest.revision: 8
ms.openlocfilehash: 4856aee930285781a101868bd6cb67824585bce1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861809"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-view-format"></a>View에 대한 Controls의 CustomControl에 대한 CustomEntries 요소(형식)

컨트롤에 대 한 정의 제공합니다. 이 요소는 뷰에서 사용할 수 있는 컨트롤을 정의할 때 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) 컨트롤 요소 (형식) 컨트롤 요소에 대 한 보기 (형식) CustomEntries 요소에 대 한 컨트롤에 대 한 컨트롤에 대 한 보기 (형식) CustomControl 요소에 대 한 컨트롤에 대 한 뷰 (형식)에 대 한 컨트롤에 대 한 CustomControl

## <a name="syntax"></a>구문

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소는 `CustomEntries` 요소입니다. 지정할 수 있는 자식 요소의 수를 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-controls-for-view-format.md)|필수 요소입니다.<br /><br /> 컨트롤의 정의 제공합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-view-format.md)|뷰를 사용 하는 컨트롤을 정의 합니다.|

## <a name="remarks"></a>설명

대부분의 경우 컨트롤에 단일에서 지정 되는 정의가 하나만 `CustomEntry` 요소입니다. 그러나 다른.NET 개체를 표시 하려면 동일한 컨트롤을 사용 하려는 경우 여러 정의 제공 하는 것이 같습니다. 이러한 경우에 정의할 수 있습니다는 `CustomEntry` 각 개체 또는 개체 집합에 대 한 요소입니다.

## <a name="see-also"></a>참고 항목

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomEntries CustomEntry 요소](./customentry-element-for-customentries-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 CustomControl 요소](./customcontrol-element-for-control-for-controls-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
