---
title: 보기 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d837d5d4-ed2e-4d84-a306-0b5d2ad2d0bf
caps.latest.revision: 24
ms.openlocfilehash: 2361c1117757569bef0815018c75764430a9e7a8
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083725"
---
# <a name="view-element-format"></a>View 요소(형식)

하나 이상의.NET 개체를 표시 하는 보기를 정의 합니다. 서식 파일에 정의 될 수 있는 뷰의 수 제한은 없습니다.

구성 요소 (형식) ViewDefinitions 요소 (형식) 보기 요소 (형식)

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `View` 요소입니다. 컨트롤 자식 요소를 하나만 지정 해야 하며 뷰와 뷰를 사용 하는 개체의 이름을 지정 해야 합니다. 사용자 지정 컨트롤을 정의 그룹화 하는 방법을 개체 및 있으면 뷰는 대역을 지정 하는 것은 선택 사항입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[뷰 (형식)에 대 한 controls 요소](./controls-element-for-view-format.md)|선택적 요소입니다.<br /><br /> 뷰 내에서 이름으로 참조할 수 있는 컨트롤의 집합을 정의 합니다.|
|[CustomControl 요소 (형식)](./customcontrol-element-for-groupby-format.md)|선택적 요소입니다.<br /><br /> 뷰에 대 한 사용자 지정 컨트롤 형식을 정의 합니다.|
|[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)|선택적 요소입니다.<br /><br /> .NET 개체 멤버의 그룹화 방식을 정의 합니다.|
|[ListControl 요소 (형식)](./listcontrol-element-format.md)|선택적 요소입니다.<br /><br /> 뷰를 목록 형식으로 정의합니다.|
|[뷰 (형식)의 name 요소](./name-element-for-view-format.md)|필수 요소입니다.<br /><br /> 뷰를 참조 하는 데 사용 하는 이름을 지정 합니다.|
|[TableControl 요소 (형식)](./tablecontrol-element-format.md)|선택적 요소입니다.<br /><br /> 뷰에 대 한 테이블 형식으로 정의합니다.|
|[뷰 (형식)에 대 한 ViewSelectedBy 요소](./viewselectedby-element-format.md)|필수 요소입니다.<br /><br /> 이 보기를 표시 하는.NET 개체를 정의 합니다.|
|[WideControl 요소 (형식)](./widecontrol-element-format.md)|선택적 요소입니다.<br /><br /> 와이드 (단일 값)을 정의 뷰에 대 한 목록 형식입니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ViewDefinitions 요소 (형식)](./viewdefinitions-element-format.md)|개체를 표시 하는 데 사용 하는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

다른 보기와 사용자 지정 컨트롤의 구성 요소에 대 한 자세한 내용은 다음 항목을 참조 합니다.

- [테이블 뷰 구성 요소](./creating-a-table-view.md)

- [목록 뷰 구성 요소](./creating-a-list-view.md)

- [와이드 보기인 경우 구성 요소](./creating-a-wide-view.md)

- [사용자 지정 컨트롤](./creating-custom-controls.md)

## <a name="example"></a>예제

보여 주는이 예제는 `View` 테이블 뷰를 정의 하는 요소는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.

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

[ViewDefinitions 요소 (형식)](./viewdefinitions-element-format.md)

[뷰 (형식)의 name 요소](./name-element-for-view-format.md)

[ViewSelectedBy 요소 (형식)](./viewselectedby-element-format.md)

[뷰 (형식)에 대 한 controls 요소](./controls-element-for-view-format.md)

[뷰 (형식)에 대 한 GroupBy 요소](./groupby-element-for-view-format.md)

[TableControl 요소 (형식)](./tablecontrol-element-format.md)

[ListControl 요소 (형식)](./listcontrol-element-format.md)

[WideControl 요소 (형식)](./widecontrol-element-format.md)

[CustomControl 요소 (형식)](./customcontrol-element-for-groupby-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
