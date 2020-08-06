---
title: GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 06e612b25accf81467108ca48500943153efd575
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786002"
---
# <a name="customcontrolname-element-for-expressionbinding-for-groupby-format"></a>GroupBy의 ExpressionBinding에 대한 CustomControlName 요소(형식)

공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

구성 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 GroupBy 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소 (형식) Customentries 요소에 대 한 CustomControl CustomControl for GroupBy (format) Customentries 요소에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 customentries에 대 한 Customentries의 경우 groupby (형식)에 대 한 ExpressionBinding의 CustomControlName 요소입니다.

## <a name="syntax"></a>구문

```xml
<CustomControlName>NameofCustomControl</CustomControlName>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 요소의 부모 요소에 대해 설명 합니다 `CustomControlName` .

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-groupby-format.md)|컨트롤에 표시 되는 데이터를 정의 합니다.|

## <a name="text-value"></a>텍스트 값

컨트롤의 이름을 지정 합니다.

## <a name="remarks"></a>설명

서식 파일의 모든 보기에서 사용할 수 있는 공용 컨트롤을 만들 수 있으며, 특정 뷰에서 사용할 수 있는 뷰 컨트롤을 만들 수 있습니다. 다음 요소는 이러한 컨트롤의 이름을 지정 합니다.

- [Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

- [View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

## <a name="see-also"></a>참고 항목

[Configuration에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-configuration-format.md)

[View에 대한 Controls의 Control에 대한 Name 요소(형식)](./name-element-for-control-for-controls-for-view-format.md)

[GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)](./expressionbinding-element-for-customitem-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
