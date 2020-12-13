---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration에 대한 Controls 요소(형식)
description: Configuration에 대한 Controls 요소(형식)
ms.openlocfilehash: 53f874ddccf3b4f1f0a23aad608e786524bde830
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668102"
---
# <a name="controls-element-for-configuration-format"></a>Configuration에 대한 Controls 요소(형식)

서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.

구성 요소 (형식) 컨트롤 구성 요소 (형식)

## <a name="syntax"></a>구문

```xml
<Controls>
  <Control>...</Control>
</Controls>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Controls` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Configuration의 Controls에 대한 Control 요소(형식)](./control-element-for-controls-for-configuration-format.md)|필수적 요소입니다.<br /><br /> 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[Configuration 요소(형식)](./configuration-element-format.md)|서식 파일의 최상위 요소를 나타냅니다.|

## <a name="remarks"></a>설명

원하는 수의 공용 컨트롤을 만들 수 있습니다. 각 컨트롤에 대해 컨트롤을 참조 하는 데 사용 되는 이름과 컨트롤의 구성 요소를 지정 해야 합니다.

## <a name="see-also"></a>참고 항목

[Configuration 요소(형식)](./configuration-element-format.md)

[Configuration의 Controls에 대한 Control 요소(형식)](./control-element-for-controls-for-configuration-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
