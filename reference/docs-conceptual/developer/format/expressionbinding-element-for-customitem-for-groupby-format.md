---
title: GroupBy (형식)의 CustomItem에 대 한 ExpressionBinding 요소 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eae5088-7605-4ef2-a703-faf3e5a5fc94
caps.latest.revision: 8
ms.openlocfilehash: 4714bfd1530585aa80aabc010b86d25bf0c7f9c4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368632"
---
# <a name="expressionbinding-element-for-customitem-for-groupby-format"></a>GroupBy의 CustomItem에 대한 ExpressionBinding 요소(형식)

컨트롤에 표시 되는 데이터를 정의 합니다. 이 요소는 새 개체 그룹이 표시 되는 방법을 정의 하는 데 사용 됩니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)의 groupby 요소 (groupby (format) CustomEntries 요소에 대 한 CustomControl 요소에 대 한 groupby (format) Customentries 요소에 대 한 CustomControl Groupby (format) CustomItem 요소에 대 한 CustomControl (형식)에 대 한 customitem에 대 한 customitem에 대 한 CustomItem 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ExpressionBinding>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameofCommonCustomControl</CustomControlName>
  <EnumerateCollection/>
  <ItemSelectionCondition>...</ItemSelectionCondition>
  <PropertyName>Nameof.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate></ScriptBlock>
</ExpressionBinding>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `ExpressionBinding` 요소의 부모 요소에 대해 설명 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|`CustomControl Element`|선택적 요소입니다.<br /><br /> 이 컨트롤에서 사용 하는 컨트롤을 정의 합니다.|
|[GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 공용 컨트롤 또는 뷰 컨트롤의 이름을 지정 합니다.|
|[GroupBy (형식)에 대 한 ExpressionBinding의 Enumeratecollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md) GroupBy (형식)에 대 한 ExpressionBinding의 EnumerateCollection 요소|선택적 요소입니다.<br /><br /> 컬렉션의 요소가 표시 되도록 지정 합니다.|
|[GroupBy (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 이 컨트롤을 사용 하기 위해 있어야 하는 조건을 정의 합니다.|
|[GroupBy (형식)에 대 한 ExpressionBinding의 PropertyName 요소](./propertyname-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 .NET 속성을 지정 합니다.|
|[GroupBy (형식)에 대 한 ExpressionBinding의 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 컨트롤에서 값을 표시 하는 스크립트를 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[GroupBy (형식)에 대 한 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-groupby-format.md)|사용자 지정 컨트롤 보기에 표시 되는 데이터와 표시 방법을 정의 합니다.|

## <a name="see-also"></a>참고 항목

[GroupBy (형식)에 대 한 ExpressionBinding의 CustomControlName 요소](./customcontrolname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (형식)에 대 한 ExpressionBinding의 EnumerateCollection 요소](./enumeratecollection-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (형식)에 대 한 ExpressionBinding의 ItemSelectionCondition 요소](./itemselectioncondition-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (형식)에 대 한 ExpressionBinding의 PropertyName 요소](./propertyname-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (형식)에 대 한 ExpressionBinding의 ScriptBlock 요소](./scriptblock-element-for-expressionbinding-for-groupby-format.md)

[GroupBy (형식)에 대 한 Customitem의 CustomItem 요소](./customitem-element-for-customentry-for-groupby-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
