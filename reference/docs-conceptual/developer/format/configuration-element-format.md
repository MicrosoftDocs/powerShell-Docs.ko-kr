---
ms.date: 09/13/2016
ms.topic: reference
title: Configuration 요소(형식)
description: Configuration 요소(형식)
ms.openlocfilehash: 0524736d40dd7a7acb0b6fb61d1438b75672c240
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655683"
---
# <a name="configuration-element-format"></a>Configuration 요소(형식)

서식 파일의 최상위 요소를 나타냅니다.

구성 요소

## <a name="syntax"></a>구문

```xml
<Configuration>
  <DefaultSettings>...</DefaultSettings>
  <SelectionSets>...</SelectionSets>
  <Controls>...</Controls>
  <ViewDefinitions>...</ViewDefinitions>
</Configuration>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `Configuration` . 이 요소는 각 서식 파일에 대 한 루트 요소 여야 하 고이 요소에는 자식 요소가 하나 이상 포함 되어야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[Configuration에 대한 Controls 요소(형식)](./controls-element-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.|
|[DefaultSettings 요소(형식)](./defaultsettings-element-format.md)|선택적 요소입니다.<br /><br /> 서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.|
|[SelectionSets 형식 설정](./selectionsets-element-format.md)|선택적 요소입니다.<br /><br /> 서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.|
|[ViewDefinitions 요소(형식)](./viewdefinitions-element-format.md)|선택적 요소입니다.<br /><br /> 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

없음

## <a name="remarks"></a>설명

서식 파일은 개체가 표시 되는 방식을 정의 합니다. 대부분의 경우이 루트 요소는 서식 파일의 테이블, 목록 및 넓은 뷰를 정의 하는 [Viewdefinitions](./viewdefinitions-element-format.md) 요소를 포함 합니다. 뷰 정의 외에도 서식 파일은 해당 뷰에서 사용할 수 있는 일반 선택 집합, 설정 및 컨트롤을 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls 요소(형식)](./controls-element-for-configuration-format.md)

[DefaultSettings 요소(형식)](./defaultsettings-element-format.md)

[SelectionSets 요소(형식)](./selectionsets-element-format.md)

[ViewDefinitions 요소(형식)](./viewdefinitions-element-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
