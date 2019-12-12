---
title: TableControl 요소 (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368202"
---
# <a name="tablecontrol-element-format"></a>TableControl 요소(형식)

뷰의 테이블 형식을 정의 합니다.

ViewDefinitions 요소 (Format) View 요소 (format) TableControl 요소 (Format)

## <a name="syntax"></a>구문

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 섹션에서는 특성, 자식 요소 및 `TableControl` 요소의 부모 요소에 대해 설명 합니다. 테이블의 행을 지정 해야 합니다. 다른 모든 자식 요소는 선택 사항입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl에 대 한 AutoSize 요소 (형식)](./autosize-element-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다.|
|[TableControl에 대 한 HideTableHeaders 요소 (형식)](./hidetableheaders-element-format.md)|선택적 요소입니다.<br /><br /> 테이블의 헤더가 표시 되지 않는지 여부를 나타냅니다.|
|[TableControl (형식)의 TableHeaders 요소](./tableheaders-element-format.md)|필수적 요소입니다.<br /><br /> 테이블 뷰의 열에 대 한 레이블, 너비 및 데이터 맞춤을 정의 합니다.|
|[TableControl에 대 한 TableRowEntries 요소 (형식)](./tablerowentries-element-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 테이블 뷰의 정의를 제공 합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[View 요소 (Format)](./view-element-format.md)|하나 이상의 개체 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

테이블 뷰의 구성 요소에 대 한 자세한 내용은 [테이블 뷰 만들기](./creating-a-table-view.md)를 참조 하세요.

## <a name="example"></a>예제

이 예제에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체의 속성을 표시 하는 데 사용 되는 `TableControl` 요소를 보여 줍니다.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a>참고 항목

[테이블 뷰 만들기](./creating-a-table-view.md)

[View 요소 (Format)](./view-element-format.md)

[TableControl에 대 한 AutoSize 요소 (형식)](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders 요소 (Format)](./hidetableheaders-element-format.md)

[TableHeaders 요소 (Format)](./tableheaders-element-format.md)

[TableRowEntries 요소 (Format)](./tablerowentries-element-for-tablecontrol-format.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
