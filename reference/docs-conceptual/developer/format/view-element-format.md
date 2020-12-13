---
ms.date: 09/13/2016
ms.topic: reference
title: View 요소(형식)
description: View 요소(형식)
ms.openlocfilehash: 6fed1304d94339cc90b6ae53e06483c08d937c12
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649733"
---
# <a name="view-element-format"></a>View 요소(형식)

하나 이상의 .NET 개체를 표시 하는 뷰를 정의 합니다. 서식 파일에서 정의할 수 있는 뷰 수에는 제한이 없습니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (Format)

## <a name="syntax"></a>구문

```xml
<View>
  <Name>Friendly name of view.</Name>
  <ViewSelectedBy>...</ViewSelectedBy>
  <Controls>...</Controls>
  <GroupBy>...</GroupBy>
  <TableControl>...</TableControl>
  <ListControl>...</ListControl>
  <WideControl>...</WideControl>
  <CustomControl>...</CustomControl>
</View>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `View` . 컨트롤 자식 요소 중 하나만 지정 해야 하며 뷰 이름 및 뷰를 사용 하는 개체를 지정 해야 합니다. 사용자 지정 컨트롤을 정의 하 고, 개체를 그룹화 하 고, 뷰가 대역외 인지 여부를 지정 하는 것은 선택 사항입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[View에 대한 Controls 요소(형식)](./controls-element-for-view-format.md)|선택적 요소입니다.<br /><br /> 뷰 내에서 이름으로 참조할 수 있는 컨트롤의 집합을 정의 합니다.|
|[CustomControl 요소 (Format)](./customcontrol-element-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 뷰의 사용자 지정 컨트롤 형식을 정의 합니다.|
|[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)|선택적 요소입니다.<br /><br /> .NET 개체의 멤버를 그룹화 하는 방법을 정의 합니다.|
|[ListControl 요소(형식)](./listcontrol-element-format.md)|선택적 요소입니다.<br /><br /> 뷰의 목록 형식을 정의 합니다.|
|[View에 대한 Name 요소(형식)](./name-element-for-view-format.md)|필수적 요소입니다.<br /><br /> 뷰를 참조 하는 데 사용 되는 이름을 지정 합니다.|
|[TableControl 요소(형식)](./tablecontrol-element-format.md)|선택적 요소입니다.<br /><br /> 뷰의 테이블 형식을 정의 합니다.|
|[보기에 대 한 ViewSelectedBy 요소 (형식)](./viewselectedby-element-format.md)|필수적 요소입니다.<br /><br /> 이 뷰가 표시 하는 .NET 개체를 정의 합니다.|
|[WideControl 요소(형식)](./widecontrol-element-format.md)|선택적 요소입니다.<br /><br /> 뷰의 넓은 (단일 값) 목록 형식을 정의 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ViewDefinitions 요소(형식)](./viewdefinitions-element-format.md)|개체를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

다양 한 보기 및 사용자 지정 컨트롤의 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 하십시오.

- [테이블 뷰 구성 요소](./creating-a-table-view.md)

- [목록 뷰 구성 요소](./creating-a-list-view.md)

- [넓은 뷰 구성 요소](./creating-a-wide-view.md)

- [사용자 지정 컨트롤](./creating-custom-controls.md)

## <a name="example"></a>예제

이 예에서는 `View` [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 테이블 뷰를 정의 하는 요소를 보여 줍니다.

```xml
<ViewDefinitions>
  <View>
    <Name>service</Name>
    <ViewSelectedBy>
      <TypeName>System.ServiceProcess.ServiceController</TypeName>
    </ViewSelectedBy>
    <TableControl>...</TableControl>
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a>참고 항목

[ViewDefinitions 요소(형식)](./viewdefinitions-element-format.md)

[View에 대한 Name 요소(형식)](./name-element-for-view-format.md)

[ViewSelectedBy 요소(형식)](./viewselectedby-element-format.md)

[View에 대한 Controls 요소(형식)](./controls-element-for-view-format.md)

[View에 대한 GroupBy 요소(형식)](./groupby-element-for-view-format.md)

[TableControl 요소(형식)](./tablecontrol-element-format.md)

[ListControl 요소(형식)](./listcontrol-element-format.md)

[WideControl 요소(형식)](./widecontrol-element-format.md)

[CustomControl 요소 (Format)](./customcontrol-element-for-groupby-format.md)

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
