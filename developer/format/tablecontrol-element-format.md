---
title: TableControl 요소 (형식) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62063831"
---
# <a name="tablecontrol-element-format"></a>TableControl 요소(형식)

보기에 대 한 테이블 형식으로 정의합니다.

ViewDefinitions 요소 (형식) 보기 (형식) TableControl 요소 (형식)

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

다음 섹션에서는 특성, 자식 요소 및 부모 요소에는 `TableControl` 요소입니다. 테이블의 행을 지정 해야 합니다. 다른 모든 자식 요소는 선택적입니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[TableControl (형식)에 대 한 자동 크기 조정 요소](./autosize-element-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 조정 여부를 열 크기 및 열 개수는 데이터의 크기를 기준으로 지정 합니다.|
|[TableControl (형식)에 대 한 HideTableHeaders 요소](./hidetableheaders-element-format.md)|선택적 요소입니다.<br /><br /> 테이블의 머리글을 표시 하지 여부를 나타냅니다.|
|[TableControl (형식)에 대 한 TableHeaders 요소](./tableheaders-element-format.md)|필수 요소입니다.<br /><br /> 레이블, 너비 및 테이블 뷰의 열에 대 한 데이터의 맞춤을 정의합니다.|
|[TableControl (형식)에 대 한 TableRowEntries 요소](./tablerowentries-element-for-tablecontrol-format.md)|선택적 요소입니다.<br /><br /> 테이블 보기의 정의 제공합니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[뷰 요소 (형식)](./view-element-format.md)|하나 이상의 개체의 멤버를 표시 하는 데 사용 되는 뷰를 정의 합니다.|

## <a name="remarks"></a>설명

테이블 보기의 구성 요소에 대 한 자세한 내용은 참조 [테이블 뷰를 만드는](./creating-a-table-view.md)합니다.

## <a name="example"></a>예제

이 예제는 `TableControl` 의 속성을 표시 하는 데 사용 되는 요소는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다.

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

[뷰 요소 (형식)](./view-element-format.md)

[TableControl (형식)에 대 한 자동 크기 조정 요소](./autosize-element-for-tablecontrol-format.md)

[HideTableHeaders 요소 (형식)](./hidetableheaders-element-format.md)

[TableHeaders 요소 (형식)](./tableheaders-element-format.md)

[TableRowEntries 요소 (형식)](./tablerowentries-element-for-tablecontrol-format.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
