---
ms.date: 09/13/2016
ms.topic: reference
title: 테이블 보기 만들기
description: 테이블 보기 만들기
ms.openlocfilehash: 035d42f7968a9e8babec692a7a5873e24b36cd97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660296"
---
# <a name="creating-a-table-view"></a>테이블 보기 만들기

테이블 뷰는 하나 이상의 열에 데이터를 표시 합니다. 테이블의 각 행은 .NET 개체를 나타내고, 테이블의 각 열은 개체 또는 스크립트 값의 속성을 나타냅니다. 개체의 모든 속성 또는 개체 속성의 하위 집합을 표시 하는 테이블 뷰를 정의할 수 있습니다.

## <a name="a-table-view-display"></a>테이블 보기 표시

다음 예제에서는 Windows [PowerShell에서 Servicecontroller cmdlet이](/powershell/module/microsoft.powershell.management/get-service) 반환 하는 [](/dotnet/api/System.ServiceProcess.ServiceController) 개체를 표시 하는 방법을 보여 줍니다. 이 개체의 경우 Windows PowerShell은 속성 `Status` , 속성 `Name` (이 속성은 속성의 별칭 속성 `ServiceName` ) 및 속성을 표시 하는 테이블 뷰를 정의 했습니다 `DisplayName` . 테이블의 각 행은 cmdlet에서 반환 된 개체를 나타냅니다.

```output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
Running  Appinfo            Application Information
```

## <a name="defining-the-table-view"></a>테이블 뷰 정의

다음 XML은 Servicecontroller을 표시 하기 위한 테이블 뷰 스키마를 보여 줍니다. [ Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다. 테이블 뷰에 표시 하려는 각 속성을 지정 해야 합니다.

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

다음 XML 요소를 사용 하 여 목록 뷰를 정의 합니다.

- [뷰](./view-element-format.md) 요소는 테이블 뷰의 부모 요소입니다. 이 요소는 목록, 전체 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.

- [Name](./name-element-for-view-format.md) 요소는 뷰의 이름을 지정 합니다. 이 요소는 모든 뷰에 필요 합니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 합니다. 이 요소는 필수 요소입니다.

- [GroupBy](./groupby-element-for-view-format.md) 요소 (이 예제에는 표시 되지 않음)는 새 개체 그룹이 표시 되는 시점을 정의 합니다. 특정 속성 또는 스크립트의 값이 변경 될 때마다 새 그룹이 시작 됩니다. 이 요소는 선택적입니다.

- [Controls](./controls-element-for-view-format.md) 요소 (이 예제에는 표시 되지 않음)는 테이블 뷰로 정의 된 사용자 지정 컨트롤을 정의 합니다. 컨트롤을 통해 데이터 표시 방법을 추가로 지정할 수 있습니다. 이 요소는 선택적입니다. 뷰는 자체 사용자 지정 컨트롤을 정의 하거나 서식 파일의 뷰에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다. 사용자 지정 컨트롤에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.

- [HideTableHeaders](./hidetableheaders-element-format.md) 요소 (이 예에서는 표시 되지 않음)는 테이블의 맨 위에 레이블을 표시 하지 않도록 지정 합니다. 이 요소는 선택적입니다.

- 테이블의 헤더 및 행 정보를 정의 하는 [TableControl](./tablecontrol-element-format.md) 요소입니다. 다른 모든 뷰와 마찬가지로, 테이블 뷰에서는 스크립트에 의해 생성 된 개체 속성 또는 값의 값을 표시할 수 있습니다.

## <a name="defining-column-headers"></a>열 머리글 정의

1. [Tableheaders](./tableheaders-element-format.md) 요소와 해당 자식 요소는 테이블의 맨 위에 표시 되는 내용을 정의 합니다.

2. [TableColumnHeader](./tablecolumnheader-element-format.md) 요소는 테이블의 열 맨 위에 표시 되는 항목을 정의 합니다. 헤더를 표시할 순서 대로 이러한 요소를 지정 합니다.

   사용할 수 있는 이러한 요소 수에는 제한이 없지만 테이블 뷰의 [TableColumnHeader](./tablecolumnheader-element-format.md) 요소 수는 사용 하는 [TableRowEntry](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md) 요소 수와 같아야 합니다.

3. [Label](./label-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 표시 되는 텍스트를 지정 합니다. 이 요소는 선택적입니다.

4. [Width](./width-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 열의 너비 (문자)를 지정 합니다. 이 요소는 선택적입니다.

5. [Alignment](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md) 요소는 레이블이 표시 되는 방법을 지정 합니다. 레이블은 왼쪽, 오른쪽 또는 가운데에 맞출 수 있습니다. 이 요소는 선택적입니다.

## <a name="defining-the-table-rows"></a>테이블 행 정의

테이블 뷰는 [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소의 자식 요소를 사용 하 여 테이블의 행에 표시 되는 데이터를 지정 하는 하나 이상의 정의를 제공할 수 있습니다. 테이블의 행에 대 한 여러 정의를 지정할 수 있지만 행의 머리글은 사용 되는 행 정의에 관계 없이 동일 하 게 유지 됩니다. 일반적으로 테이블에는 정의가 하나만 있습니다.

다음 예제에서 뷰는 System.object의 여러 속성 값을 표시 하는 단일 정의를 제공 합니다. [ Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 개체입니다. 테이블 뷰에서는 속성 값 또는 스크립트 값 (예제에서는 표시 되지 않음)을 행에 표시할 수 있습니다.

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

다음 XML 요소를 사용 하 여 행에 대 한 정의를 제공할 수 있습니다.

- [TableRowEntries](./tablerowentries-element-for-tablecontrol-format.md) 요소 및 해당 자식 요소는 테이블의 행에 표시 되는 항목을 정의 합니다.

- [TableRowEntry](./listentry-element-for-listcontrol-format.md) 요소는 행의 정의를 제공 합니다. 하나 이상의 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 가 필요 합니다. 그러나 추가할 수 있는 요소 수에 대 한 최대 제한은 없습니다. 대부분의 경우 보기에는 하나의 정의만 있습니다.

- [Entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 특정 정의에 의해 표시 되는 개체를 지정 합니다. 이 요소는 선택 사항이 며 다른 개체를 표시 하는 여러 [TableRowEntry](./listentry-element-for-listcontrol-format.md) 요소를 정의 하는 경우에만 필요 합니다.

- [Wrap](./wrap-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 열 너비를 초과 하는 텍스트를 다음 줄에 표시 하도록 지정 합니다. 기본적으로 열 너비를 초과하는 텍스트는 잘립니다.

- [TableColumnItems](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 속성 또는 스크립트를 정의 합니다.

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다. 행의 각 열에는 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소가 필요 합니다. 첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 속성을 지정 합니다. 속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소는 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다. 이 요소는 선택적입니다.

- [Alignment](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 속성이 나 스크립트의 값이 표시 되는 방법을 지정 합니다. 값을 왼쪽, 오른쪽 또는 가운데에 맞출 수 있습니다. 이 요소는 선택적입니다.

## <a name="defining-the-objects-that-use-the-table-view"></a>테이블 뷰를 사용 하는 개체 정의

테이블 뷰를 사용 하는 .NET 개체를 정의 하는 방법에는 두 가지가 있습니다. [Viewselectedby](./viewselectedby-element-format.md) 요소를 사용 하 여 뷰의 모든 정의에서 표시할 수 있는 개체를 정의 하거나, [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소를 사용 하 여 뷰의 특정 정의에 표시 되는 개체를 정의할 수 있습니다. 대부분의 경우 뷰에는 정의가 하나만 있으므로 개체는 일반적으로 [Viewselectedby](./viewselectedby-element-format.md) 요소에 의해 정의 됩니다.

다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 사용 하 여 테이블 뷰에 표시 되는 개체를 정의 하는 방법을 보여 줍니다. 지정할 수 있는 [TypeName](./typename-element-for-viewselectedby-format.md) 요소의 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

다음 XML 요소를 사용 하 여 테이블 뷰에서 사용 되는 개체를 지정할 수 있습니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.

- [TypeName](./typename-element-for-viewselectedby-format.md) 요소는 뷰에 표시 되는 .net 개체를 지정 합니다. 정규화 된 .NET 형식 이름이 필요 합니다. 뷰에 대해 하나 이상의 유형 또는 선택 집합을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소를 사용 합니다. 동일한 개체에 대 한 목록 뷰 및 테이블 뷰를 정의 하는 경우와 같이 여러 뷰를 사용 하 여 표시 되는 관련 개체 집합이 있는 선택 집합을 사용 합니다. 선택 집합을 만드는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>
```

다음 XML 요소는 목록 뷰에서 사용 되는 개체를 지정 하는 데 사용할 수 있습니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소는 뷰에서 표시할 수 있는 개체 집합을 지정 합니다. 뷰에 대해 하나 이상의 선택 집합 또는 유형을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

다음 예에서는 [Entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소를 사용 하 여 테이블 뷰의 특정 정의에 표시 되는 개체를 정의 하는 방법을 보여 줍니다. 이 요소를 사용 하 여 개체의 .NET 형식 이름, 개체의 선택 집합 또는 정의가 사용 되는 시기를 지정 하는 선택 조건을 지정할 수 있습니다. 선택 조건을 만드는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

> [!NOTE]
> 테이블 뷰의 정의를 여러 개 만들 때 다른 열 머리글을 지정할 수 없습니다. 표시 되는 개체와 같이 테이블의 행에 표시 되는 항목을 지정할 수 있습니다.

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</TableRowEntry>
```

다음 XML 요소를 사용 하 여 목록 뷰의 특정 정의에서 사용 되는 개체를 지정할 수 있습니다.

- [Entryselectedby](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md) 요소는 정의에 의해 표시 되는 개체를 정의 합니다.

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) 요소는 정의에 의해 표시 되는 .net 개체를 지정 합니다. 이 요소를 사용 하는 경우 정규화 된 .NET 형식 이름이 필요 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의에 의해 표시 될 수 있는 개체 집합을 지정 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

- [Selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의를 사용 하기 위해 존재 해야 하는 조건을 지정 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다. 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="using-format-strings"></a>서식 문자열 사용

서식 문자열을 뷰에 추가 하 여 데이터 표시 방법을 추가로 정의할 수 있습니다. 다음 예제에서는 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다 `StartTime` .

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

다음 XML 요소를 사용 하 여 형식 패턴을 지정할 수 있습니다.

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다. 행의 각 열에는 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소가 필요 합니다. 첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.

- [PropertyName](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 속성을 지정 합니다. 속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [FormatString](./label-element-for-listitem-for-listcontrol-format.md) 요소는 속성 또는 스크립트 값이 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.

다음 예제에서는 `ToString` 메서드를 호출 하 여 스크립트의 값에 대 한 형식을 지정 합니다. 스크립트는 개체의 메서드를 호출할 수 있습니다. 따라서 개체에 `ToString` 형식 매개 변수를 포함 하는 등의 메서드가 있는 경우 스크립트는 해당 메서드를 호출 하 여 스크립트의 출력 값에 대 한 형식을 지정할 수 있습니다.

```xml
<ListItem>
  <ScriptBlock>
    [String]::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

다음 XML 요소를 사용 하 여 메서드를 호출할 수 있습니다 `ToString` .

- [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소는 행의 열에 값이 표시 되는 속성이 나 스크립트를 정의 합니다. 행의 각 열에는 [TableColumnItem](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md) 요소가 필요 합니다. 첫 번째 항목이 첫 번째 열에 표시 되 고 두 번째 열에 두 번째 항목이 표시 됩니다.

- [ScriptBlock](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md) 요소는 값이 행에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[PowerShell 형식 지정 파일 작성](./writing-a-powershell-formatting-file.md)
