---
title: 테이블 뷰 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f405afb-70b5-4fe0-9986-bc07401d93fd
caps.latest.revision: 23
ms.openlocfilehash: 862f942facafff6cea66c4f8f1040772c6a62ec3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066841"
---
# <a name="creating-a-table-view"></a>테이블 보기 만들기

테이블 뷰를 하나 이상의 열에 데이터를 표시합니다. 표의 각 행.NET 개체를 나타내며 테이블의 각 열에 스크립트 값 또는 개체의 속성을 나타냅니다. 개체의 모든 속성 또는 개체의 속성 하위 집합을 표시 하는 테이블 보기를 정의할 수 있습니다.

## <a name="a-table-view-display"></a>테이블 뷰 표시

다음 예제에서는 Windows PowerShell의 표시 하는 방법을 보여 줍니다.는 [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) 에서 반환 되는 개체를 [Get-service](/powershell/module/microsoft.powershell.management/get-service) cmdlet. Windows PowerShell이이 개체에 대해 표시 되는 테이블 뷰를 정의 했습니다를 `Status` 속성을 `Name` 속성 (이 속성에 대 한 별칭 속성인를 `ServiceName` 속성), 및 `DisplayName` 속성. 표의 각 행은 cmdlet에서 반환 된 개체를 나타냅니다.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>테이블 보기를 정의합니다.

다음 XML에 표시 하기 위한 테이블 뷰 스키마를 보여 줍니다는 [System.Serviceprocess.Servicecontroller? Displayproperty =](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다. 테이블 보기에 표시 되는 각 속성을 지정 해야 합니다.

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>
      <TableColumnHeader>
        <Width>8</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>18</Width>
      </TableColumnHeader>
      <TableColumnHeader>
        <Width>38</Width>
      </TableColumnHeader>
    </TableHeaders>
    <TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>
  </TableControl>
</View>
```

다음 XML 요소는 목록 뷰를 정의 하는 데 사용 됩니다.

- 합니다 [보기](./view-element-format.md) 요소는 부모 요소 테이블 보기입니다. (목록, 넓게 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.)

- 합니다 [이름을](./name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다. 이 요소는 모든 보기에 필요 합니다.

- 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 뷰를 사용 하는 개체를 정의 합니다. 필수적 요소로,

- 합니다 [GroupBy](./groupby-element-for-view-format.md) 요소 (이 예제에 표시 되지 않음) 개체의 새 그룹을이 표시 되는 때를 정의 합니다. 새 그룹을 특정 속성이 나 스크립트의 값이 변경 될 때마다 시작 됩니다. 이 요소는 선택 사항입니다.

- 합니다 [컨트롤](./controls-element-for-view-format.md) 테이블 보기에서 정의한 사용자 지정 컨트롤을 정의 하는 요소 (이 예제에 표시 되지 않음). 컨트롤 추가 데이터가 표시 되는 방식을 지정 하는 방법을 제공 합니다. 이 요소는 선택 사항입니다. 뷰 자체 사용자 지정 컨트롤을 정의 하거나 형식 지정 파일의 보기 중 하나에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다. 사용자 지정 컨트롤에 대 한 자세한 내용은 참조 하세요. [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.

- 합니다 [HideTableHeaders](./hidetableheaders-element-format.md) 요소 (이 예에 표시 되지 않습니다)은 테이블의 맨 위에 있는 레이블이 표시 되지 것입니다 지정 합니다. 이 요소는 선택 사항입니다.

- 합니다 [TableControl](./tablecontrol-element-format.md) 테이블의 머리글 및 행 정보를 정의 하는 요소입니다. 다른 모든 보기와 마찬가지로 테이블 뷰를 표시할 수 있습니다 개체 속성의 값 또는 스크립트에서 생성 된 값입니다.

## <a name="defining-column-headers"></a>열 헤더를 정의합니다.

1. 합니다 [TableHeaders](./tableheaders-element-format.md) 테이블의 맨 위에 있는 표시 되는 항목 정의 요소 및 해당 자식 요소입니다.

2. 합니다 [TableColumnHeader](./tablecolumnheader-element-format.md) 요소 테이블의 열 위쪽에 표시 되는 항목을 정의 합니다. 표시 된 헤더를 원하는 순서로 이러한 요소를 지정 합니다.

   사용할 수 있는 이러한 요소의 수 있지만 수 제한이 [TableColumnHeader](./tablecolumnheader-element-format.md) 테이블 보기의 요소 수가 같아야 [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 사용 하는 요소입니다.

3. 합니다 [레이블](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소 표시 되는 텍스트를 지정 합니다. 이 요소는 선택 사항입니다.

4. 합니다 [너비](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 너비 (문자 단위) 열을 지정 합니다. 이 요소는 선택 사항입니다.

5. 합니다 [맞춤](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소 레이블이 표시 되는 방식을 지정 합니다. 레이블은 왼쪽, 오른쪽에 정렬 또는 가운데 맞춤 수 있습니다. 이 요소는 선택 사항입니다.

## <a name="defining-the-table-rows"></a>테이블 행을 정의합니다.

테이블 보기의 자식 요소를 사용 하 여 테이블의 행에 표시 되는 데이터를 지정 하는 하나 이상의 정의 제공할 수는 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소입니다. 테이블의 행에 대 한 여러 정의 지정할 수 있지만 행에 대 한 헤더 어떤 행 정의 관계 없이 동일 하 게 유지 됩니다. 일반적으로 테이블을 하나만 정의 해야 합니다.

다음 예제에서는 보기에서는 일부의 속성의 값을 표시 하는 단일 정의 [System.Diagnostics.Process? Displayproperty =](/dotnet/api/System.Diagnostics.Process) 개체입니다. 테이블 뷰를 해당 행에서 속성의 값 이나 스크립트 (예제에 표시 되지 않음)의 값을 표시할 수 있습니다.

```xml
<TableRowEntries>
      <TableRowEntry>
        <TableColumnItems>
          <TableColumnItem>
           <PropertyName>Status</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>Name</PropertyName>
          </TableColumnItem>
          <TableColumnItem>
            <PropertyName>DisplayName</PropertyName>
          </TableColumnItem>
        </TableColumnItems>
      </TableRowEntry>
    </TableRowEntries>

```

행에 대 한 정의 제공 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소와 해당 자식 요소는 테이블의 행에 표시 되는 항목을 정의 합니다.

- 합니다 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 요소 행의 정의 제공 합니다. 하나 이상의 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 필수 사항입니다; 그러나는 추가할 수 있는 요소의 수를 최대 제한이 있습니다. 대부분의 경우에서 뷰를 하나만 정의 해야 합니다.

- 합니다 [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 특정 정의 의해 표시 되는 개체를 지정 합니다. 이 요소는 선택 사항이 며 여러 개를 정의 하는 경우에 필요 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 다른 개체를 표시 하는 요소입니다.

- 합니다 [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 지정 된 열 너비를 초과 하는 텍스트가 다음 줄에 표시 됩니다. 기본적으로 열 너비를 초과하는 텍스트는 잘립니다.

- 합니다 [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) 요소 속성 또는 행의 값을 표시 하는 스크립트를 정의 합니다.

- 합니다 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 각 열에 대 한 필요 합니다. 첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.

- 합니다 [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 행에 해당 값이 표시 속성을 지정 합니다. 속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 값은 행에 표시 하는 스크립트를 지정 합니다. 스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소 스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다. 이 요소는 선택 사항입니다.

- 합니다 [맞춤](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 속성 또는 스크립트의 값이 표시 되는 방식을 지정 합니다. 값을 왼쪽, 오른쪽으로 정렬 또는 가운데 맞춤 수 있습니다. 이 요소는 선택 사항입니다.

## <a name="defining-the-objects-that-use-the-table-view"></a>테이블 보기를 사용 하는 개체를 정의 합니다.

테이블 뷰를 사용 하 여.NET 개체를 정의 하는 방법은 두 가지가 있습니다. 사용할 수는 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의의 보기를 통해 표시 될 수 있는 개체 정의를 사용할 수는 [EntrySelectedBy](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 정의 개체를 표시 하는 요소는 특정 뷰의 정의 합니다. 대부분의 경우에서 보기 있으므로 하나만 정의 하 여 개체는 일반적으로 정의 된 [ViewSelectedBy](./viewselectedby-element-format.md) 요소입니다.

다음 예제에서는 사용 하 여 테이블 보기에 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [TypeName](./typename-element-for-viewselectedby-format.md) 요소입니다. 수에 제한이 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 지정 하 고 해당 순서는 중요 하지 않습니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

테이블 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의 목록 뷰에 개체를 표시 합니다.

- 합니다 [TypeName](./typename-element-for-viewselectedby-format.md) 요소 보기에 표시 되는.NET 개체를 지정 합니다. 정규화 된.NET 유형 이름이 필요 합니다. 하나 이상의 형식 또는 선택이 보기에 대 한 설정 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.

다음 예제에서는 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소입니다. 관련된 목록 뷰를 정의 하는 경우와 같은 여러 뷰와 테이블 뷰를 사용 하 여 동일한 개체에 대해 표시 되는 개체 집합이 있는 선택 집합을 사용 합니다. 선택 영역 집합을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [선택 집합 정의](./defining-selection-sets.md)합니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

목록 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의 목록 뷰에 개체를 표시 합니다.

- 합니다 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 보기에서 표시할 수 있는 개체 집합을 지정 합니다. 하나 이상 선택 집합 또는 보기에 대 한 형식을 지정 해야 하지만 지정할 수 있는 요소의 최대 수 없습니다.

다음 예제에서는 사용 하 여 테이블 보기의 특정 정의 의해 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소입니다. 이 요소를 사용 하 여, 개체, 개체 집합을 선택 또는 선택 조건 정의 사용 하는 경우를 지정 하는.NET 형식 이름을 지정할 수 있습니다. 선택 조건을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

> [!NOTE]
> 테이블 보기의 정의가 여러 개 만들 때 다른 열 헤더를 지정할 수 없습니다. 어떤 개체는 같은 테이블의 행에 표시할 항목만 지정할 수 있습니다.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

특정 목록 보기의 정의 의해 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [EntrySelectedBy](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소 정의 의해 표시 되는 객체를 정의 합니다.

- 합니다 [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) 요소 정의 의해 표시 되는.NET 개체를 지정 합니다. 이 요소를 사용 하는 경우 정규화 된.NET 유형 이름이 필요 합니다. 하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.

- 합니다 [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)이이 정의 의해 표시 될 수 있는 개체 집합을 지정 합니다. 하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.

- 합니다 [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)이이 정의를 사용할 수 있어야 하는 조건을 지정 합니다. 하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다. 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="using-format-strings"></a>서식 문자열 사용

데이터 표시 되는 방법을 추가로 정의할 보기로 서식 문자열을 추가할 수 있습니다. 다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

다음 XML 요소가 형식 패턴을 지정 하려면 사용할 수 있습니다.

- 합니다 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 각 열에 대 한 필요 합니다. 첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.

- 합니다 [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 행에 해당 값이 표시 속성을 지정 합니다. 속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소 스크립트나 속성 값이 표시 되는 방식을 정의 하는 형식 패턴을 지정 합니다.

다음 예제에서는 `ToString` 메서드를 호출 하는 스크립트의 값의 형식을 지정 합니다. 스크립트 개체의 모든 메서드를 호출할 수 있습니다. 따라서 개체에 있는 경우 메서드를 같은 `ToString`형식 매개 변수가 있는, 스크립트는 스크립트의 출력 값의 서식을 지정 하는 메서드를 호출할 수 있습니다.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

호출 하는 다음 XML 요소를 사용할 수는 `ToString` 메서드:

- 합니다 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 속성 또는 값은 행의 열에 표시 된 스크립트를 정의 합니다. A [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 각 열에 대 한 필요 합니다. 첫 번째 항목은 두 번째 열에 두 번째 항목은 첫 번째 열에 표시 됩니다.

- 합니다 [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소 값은 행에 표시 하는 스크립트를 지정 합니다. 스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
