---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl에 대한 ListEntries 요소(형식)
description: ListControl에 대한 ListEntries 요소(형식)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666606"
---
# <a name="listentries-element-for-listcontrol-format"></a>ListControl에 대한 ListEntries 요소(형식)

목록 뷰의 정의를 제공 합니다. 목록 뷰에서 하나 이상의 정의를 지정 해야 합니다.

Configuration 요소 (Format) ViewDefinitions 요소 (format) View 요소 (format)이 listcontrol Element (format) ListEntries Element (Format)

## <a name="syntax"></a>구문

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 요소의 특성, 자식 요소 및 부모 요소에 대해 설명 합니다 `ListEntries` . 하나 이상의 자식 요소를 지정 해야 합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ListEntry 요소 (Format)](./listentry-element-for-listcontrol-format.md)|목록 뷰의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ListControl 요소(형식)](./listcontrol-element-format.md)|뷰의 목록 형식을 정의 합니다.|

## <a name="remarks"></a>설명

목록 뷰에 대 한 자세한 내용은 [목록 뷰](./creating-a-list-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체에 대 한 목록 뷰를 정의 하는 XML 요소를 보여 줍니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a>참고 항목

[ListControl 요소(형식)](./listcontrol-element-format.md)

[ListEntry 요소 (Format)](./listentry-element-for-listcontrol-format.md)

[목록 보기](./creating-a-list-view.md)

[Windows PowerShell 서식 지정 및 형식 파일 작성](./writing-a-powershell-formatting-file.md)
