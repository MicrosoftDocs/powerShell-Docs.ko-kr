---
title: GroupBy (형식)에 대 한 ExpressionBinding에 대 한 CustomControlName 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e11da8f-1e75-4d3d-b4c8-b500dec3028e
caps.latest.revision: 6
ms.openlocfilehash: 32f8a71e9818c8c1a052f3b96f442f169c1bda4a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854299"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)

공용 컨트롤에서 뷰 컨트롤의 이름을 지정합니다. 이 요소는 새 개체 그룹에 표시 되는 방식을 정의 하는 경우에 사용 됩니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 (형식) GroupBy 요소 CustomControl GroupBy (형식) CustomEntry 요소에 대 한 GroupBy (형식) CustomEntries 요소에 대 한 보기 (형식) CustomControl 요소에 대 한 CustomControl CustomEntry CustomItem GroupBy (형식)에 대 한 ExpressionBinding CustomControlName 요소 GroupBy (형식)에 대 한 GroupBy (형식) ExpressionBinding 요소에 대 한 GroupBy (형식) CustomItem 요소에

## <a name="syntax"></a>구문

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `CustomControlName` 요소입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있습니다 하 고 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 다음 요소는 이러한 컨트롤의 이름을 지정합니다.

- [구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-configuration-format.md)

- [뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[구성 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-configuration-format.md)

[뷰 (형식)에 대 한 컨트롤에 대 한 컨트롤의 name 요소](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy (형식)에 대 한 CustomItem ExpressionBinding 요소](./expressionbinding-element-for-customitem-for-groupby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
