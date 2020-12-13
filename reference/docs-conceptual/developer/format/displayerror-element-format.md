---
ms.date: 09/13/2016
ms.topic: reference
title: DisplayError 요소(형식)
description: DisplayError 요소(형식)
ms.openlocfilehash: fb54df86a3558263687a8c417870495b7066f563
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649928"
---
# <a name="displayerror-element-format"></a>DisplayError 요소(형식)

데이터의 일부를 표시 하는 동안 오류가 발생 하는 경우 문자열 #ERR 표시 되도록 지정 합니다.

Configuration 요소 (Format) DefaultSettings 요소 (format) DisplayError 요소 (Format)

## <a name="syntax"></a>구문

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `DisplayError` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[DefaultSettings 요소(형식)](./defaultsettings-element-format.md)|서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.|

## <a name="remarks"></a>설명

기본적으로 데이터의 일부를 표시 하는 동안 오류가 발생 하면 데이터의 위치를 비워 둡니다. 이 요소를 true로 설정 하면 #ERR 문자열이 표시 됩니다.

## <a name="see-also"></a>참고 항목

[DefaultSettings 요소(형식)](./defaultsettings-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
