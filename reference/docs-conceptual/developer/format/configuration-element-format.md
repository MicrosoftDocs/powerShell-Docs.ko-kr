---
title: Configuration 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d46df0cb-50b7-4b81-82ba-37186a7b7a7f
caps.latest.revision: 28
ms.openlocfilehash: 296c63d0c774a0bf56e90dbaa32f2c221d4c3dbd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363502"
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

다음 섹션에서는 특성, 자식 요소 및 `Configuration` 요소의 부모 요소에 대해 설명 합니다. 이 요소는 각 서식 파일에 대 한 루트 요소 여야 하 고이 요소에는 자식 요소가 하나 이상 포함 되어야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[구성 요소에 대 한 Controls 요소 (형식)](./controls-element-for-configuration-format.md)|선택적 요소입니다.<br /><br /> 서식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.|
|[DefaultSettings 요소 (Format)](./defaultsettings-element-format.md)|선택적 요소입니다.<br /><br /> 서식 파일의 모든 뷰에 적용 되는 일반 설정을 정의 합니다.|
|[SelectionSets 형식 설정](./selectionsets-element-format.md)|선택적 요소입니다.<br /><br /> 서식 지정 파일의 모든 보기에서 사용할 수 있는 .NET 개체의 공통 집합을 정의 합니다.|
|[ViewDefinitions 요소 (형식)](./viewdefinitions-element-format.md)|선택적 요소입니다.<br /><br /> 개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

없음

## <a name="remarks"></a>설명

서식 파일은 개체가 표시 되는 방식을 정의 합니다. 대부분의 경우이 루트 요소는 서식 파일의 테이블, 목록 및 넓은 뷰를 정의 하는 [Viewdefinitions](./viewdefinitions-element-format.md) 요소를 포함 합니다. 뷰 정의 외에도 서식 파일은 해당 뷰에서 사용할 수 있는 일반 선택 집합, 설정 및 컨트롤을 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[구성 요소에 대 한 Controls 요소 (형식)](./controls-element-for-configuration-format.md)

[DefaultSettings 요소 (Format)](./defaultsettings-element-format.md)

[SelectionSets 요소 (형식)](./selectionsets-element-format.md)

[ViewDefinitions 요소 (형식)](./viewdefinitions-element-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
