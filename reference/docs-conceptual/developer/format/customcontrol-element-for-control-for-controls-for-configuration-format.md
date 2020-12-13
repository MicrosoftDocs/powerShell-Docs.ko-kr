---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)
description: Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)
ms.openlocfilehash: 631995c6a50c0f020cb2e991cfbf58a09a75cc72
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649995"
---
# <a name="customcontrol-element-for-control-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 Control에 대한 CustomControl 요소(형식)

컨트롤을 정의 합니다. 이 요소는 서식 파일의 모든 뷰에서 사용할 수 있는 공용 컨트롤을 정의 하는 데 사용 됩니다.

구성 요소 (format) 컨트롤 요소 구성 (format)의 컨트롤 요소 구성 (format)의 컨트롤에 대 한 CustomControl 요소

## <a name="syntax"></a>구문

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `CustomControl` . 이 요소에는 자식 요소가 하나 이상 있어야 합니다. 지정할 수 있는 자식 요소 수에 대 한 최대 제한은 없습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[구성에 대 한 CustomControl의 CustomEntries 요소 (형식)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)|필수적 요소입니다.<br /><br /> 컨트롤의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration의 Controls에 대한 Control 요소(형식)](./control-element-for-controls-for-configuration-format.md)|서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.|

## <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[Configuration의 Controls에 대한 Control 요소(형식)](./control-element-for-controls-for-configuration-format.md)

[구성에 대 한 CustomControl의 CustomEntries 요소 (형식)](./customentries-element-for-customcontrol-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
