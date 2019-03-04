---
title: 구성 (형식)에 대 한 컨트롤에 대 한 컨트롤에 대 한 요소 이름을 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4371d45-49a4-4303-8384-5b54105bd0d6
caps.latest.revision: 8
ms.openlocfilehash: 2704a530e0ae269efb772ac10e531bcbb12f6eff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860089"
---
# <a name="name-element-for-control-for-controls-for-configuration-format"></a>Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)

컨트롤의 이름을 지정합니다. 이 요소는 서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의할 때 사용 됩니다.

구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 Name 요소 (형식) 구성에 대 한 컨트롤에 대 한 Control 요소 구성 (형식)의 구성 요소 (형식) 컨트롤 요소

## <a name="syntax"></a>구문

```xml
<Name>NameOfControl</Name>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `Name` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[구성 (형식)에 대 한 컨트롤에 대 한 control 요소](./control-element-for-controls-for-configuration-format.md)|컨트롤을 참조 하는 데 사용 되는 이름과 형식 지정 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 정의 합니다.|

## <a name="text-value"></a>텍스트 값

이 컨트롤을 참조 하는 데 사용 되는 이름을 지정 합니다.

## <a name="remarks"></a>설명

여기에 지정 된 이름은이 컨트롤을 참조 하는 다음 요소에 사용할 수 있습니다.

- 테이블, 목록, 와이드 또는 사용자 지정 컨트롤 뷰를 만들 때 다음 요소에서 컨트롤을 지정할 수 있습니다. [뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)

- 다른 공용 컨트롤을 만들 때이 컨트롤은 다음 요소로 지정할 수 있습니다. [구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- 컨트롤을 만들 수 있습니다을 사용 하는 뷰를 하는 경우이 컨트롤은 다음 요소로 지정할 수 있습니다. [뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[구성 (형식)에 대 한 컨트롤에 대 한 control 요소](./control-element-for-controls-for-configuration-format.md)

[구성 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
