---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy 요소(형식)
description: ViewSelectedBy 요소(형식)
ms.openlocfilehash: ac3c7de299b3009a067a476a024c6a6fcb5dce02
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667711"
---
# <a name="viewselectedby-element-format"></a>ViewSelectedBy 요소(형식)

뷰에 표시 되는 .NET 개체를 정의 합니다. 각 보기는 하나 이상의 .NET 개체를 지정 해야 합니다.

ViewDefinitions 요소 (Format) View 요소 (format) ViewSelectedBy 요소 (형식)

## <a name="syntax"></a>구문

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ViewSelectedBy` . 이 요소는 하나 이상의 `TypeName` 또는 자식 요소를 포함 해야 합니다 `SelectionSetName` . 지정할 수 있는 자식 요소 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ViewSelectedBy에 대한 TypeName 요소(형식)](./typename-element-for-viewselectedby-format.md)|선택적 요소입니다.<br /><br /> 뷰에 표시 되는 .NET 개체를 지정 합니다.|
|[ViewSelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-viewselectedby-format.md)|선택적 요소입니다.<br /><br /> 뷰에 표시 되는 .NET 개체의 집합을 지정 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 요소(형식)](./view-element-format.md)|하나 이상의 .NET 개체를 표시 하는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

다른 뷰에서이 요소를 사용 하는 방법에 대 한 자세한 내용은 [테이블 뷰 구성 요소](./creating-a-table-view.md), [목록 뷰 구성 요소](./creating-a-list-view.md), [넓은 뷰 구성](./creating-a-wide-view.md)요소 및 [사용자 지정 컨트롤 구성 요소](./creating-custom-controls.md)를 참조 하세요.

`SelectionSetName`서식 파일에서 여러 뷰에 표시 되는 개체 집합을 정의할 때 요소가 사용 됩니다. 선택 집합을 정의 하 고 참조 하는 방법에 대 한 자세한 내용은 [개체 집합 정의](./defining-selection-sets.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 목록 뷰에 대 한 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체를 지정 하는 방법을 보여 줍니다. 테이블, 전체 및 사용자 지정 보기에도 동일한 스키마가 사용 됩니다.

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

[목록 보기 만들기](./creating-a-list-view.md)

[테이블 보기 만들기](./creating-a-table-view.md)

[넓게 보기 만들기](./creating-a-wide-view.md)

[사용자 지정 컨트롤 만들기](./creating-custom-controls.md)

[선택 영역 집합 정의](./defining-selection-sets.md)

[ViewSelectedBy에 대한 SelectionSetName 요소(형식)](./selectionsetname-element-for-viewselectedby-format.md)

[TypeName 요소 (Format)](./typename-element-for-viewselectedby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
