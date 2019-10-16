---
title: View 컨트롤의 컨트롤에 대 한 Name 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26437467-d578-4e8d-8cdd-17dfe644957a
caps.latest.revision: 7
ms.openlocfilehash: 7e24aa60f7abae5768707d2527826c452b709002
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365102"
---
# <a name="name-element-for-control-for-controls-for-view-format"></a>View에 대한 Controls의 Control에 대한 Name 요소(형식)

컨트롤의 이름을 지정 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (Format) View 요소 (format) Controls 요소에 대 한 컨트롤 요소 (format) 컨트롤 요소 (형식)의 컨트롤에 대 한 뷰 (format) Name 요소

## <a name="syntax"></a>구문

```xml
<Name>ControlName</Name>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 `Name` 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[보기에 대 한 컨트롤 요소 (형식)](./control-element-for-controls-for-view-format.md)|뷰에서 사용할 수 있는 컨트롤 및 컨트롤을 참조 하는 데 사용 되는 이름을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.

## <a name="remarks"></a>설명

여기에 지정 된 이름은 다음 요소에서이 컨트롤을 참조 하는 데 사용할 수 있습니다.

- 테이블, 목록, 전체 또는 사용자 지정 컨트롤 뷰를 만들 때 컨트롤은 [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md) 와 같은 요소로 지정할 수 있습니다.

- 뷰에서 사용할 수 있는 다른 컨트롤을 만들 때 다음 요소를 사용 하 여이 컨트롤을 지정할 수 있습니다. [뷰 컨트롤의 CustomItem에 대 한 Expressionbinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[보기에 대 한 GroupBy 요소 (형식)](./groupby-element-for-view-format.md)

[뷰에 대 한 컨트롤 CustomItem의 ExpressionBinding 요소 (형식)](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[보기에 대 한 컨트롤 요소 (형식)](./control-element-for-controls-for-view-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
