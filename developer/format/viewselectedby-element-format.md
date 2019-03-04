---
title: ViewSelectedBy 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863189"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy 요소(형식)

보기에 표시 되는.NET 개체를 정의 합니다. 각 보기에는.NET 개체를 하나 이상 지정 해야 합니다.

ViewDefinitions 요소 (형식) 보기 (형식) ViewSelectedBy 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `ViewSelectedBy` 요소입니다. 이 요소는 하나 이상 포함 해야 합니다 `TypeName` 또는 `SelectionSetName` 자식 요소입니다. 지정 될 수 있는 자식 요소의 수에 제한이 나 순서는 중요 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ViewSelectedBy (형식)에 대 한 TypeName 요소](./typename-element-for-viewselectedby-format.md)|선택적 요소입니다.<br /><br /> 보기에 표시 되는.NET 개체를 지정 합니다.|
|[ViewSelectedBy (형식)에 대 한 SelectionSetName 요소](./selectionsetname-element-for-viewselectedby-format.md)|선택적 요소입니다.<br /><br /> 보기에 표시 되는.NET 개체 집합을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 요소 (형식)](./view-element-format.md)|하나 이상의.NET 개체를 표시 하는 보기를 정의 합니다.|

## <a name="remarks"></a>설명

다른 보기에이 요소를 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [테이블 뷰 구성 요소](./creating-a-table-view.md)를 [목록 뷰 구성 요소](./creating-a-list-view.md)합니다 [뷰 구성 요소를 와이드](./creating-a-wide-view.md), 및 [사용자 지정 컨트롤 구성 요소](./creating-custom-controls.md)합니다.

`SelectionSetName` 요소는 서식 파일은 여러 뷰에서 표시 되는 개체 집합을 정의 하는 경우 사용 합니다. 선택 집합이 정의 되어 있고 참조 하는 방법에 대 한 자세한 내용은 참조 하세요. [설정의 개체 정의](./defining-selection-sets.md)합니다.

## <a name="example"></a>예제

다음 예제에서는 지정 하는 방법을 보여 줍니다 합니다 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 목록 보기에 대 한 개체입니다. 동일한 스키마는 테이블, 넓게 및 사용자 지정 보기에 사용 됩니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a>참고 항목

[목록 뷰 만들기](./creating-a-list-view.md)

[테이블 뷰 만들기](./creating-a-table-view.md)

[넓은 보기 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[선택 영역 집합을 정의](./defining-selection-sets.md)

[ViewSelectedBy (형식)에 대 한 SelectionSetName 요소](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName 요소 (형식)](./typename-element-for-viewselectedby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
