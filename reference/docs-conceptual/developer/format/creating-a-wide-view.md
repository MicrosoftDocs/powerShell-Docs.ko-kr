---
title: 넓은 뷰 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72368952"
---
# <a name="creating-a-wide-view"></a>넓게 보기 만들기

넓은 보기에는 표시 되는 각 개체에 대 한 단일 값이 표시 됩니다. 표시 되는 값은 .NET 개체 속성의 값 또는 스크립트의 값일 수 있습니다. 이 보기에는 기본적으로 레이블이나 머리글이 없습니다.

## <a name="a-wide-view-display"></a>넓은 보기 표시

다음 예제에서는 Windows PowerShell에서 출력이 [형식 전체](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet으로 파이프 되는 경우에는 [Get process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet에 의해 반환 되는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체를 표시 하는 방법을 보여 줍니다. 기본적으로, [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet은 테이블 뷰를 반환 합니다. 이 예에서는 두 개의 열을 사용 하 여 반환 된 각 개체에 대 한 프로세스의 이름을 표시 합니다. 개체의 속성 이름이 표시 되지 않고 속성의 값만 표시 됩니다.

```
Get-Process | format-wide
AEADISRV                     agrsmsvc
Ati2evxx                     Ati2evxx
audiodg                      CCC
CcmExec                      communicator
Crypserv                     csrss
csrss                        DevDtct2
DM1Service                   dpupdchk
dwm                          DxStudio
EXCEL                        explorer
GoogleToolbarNotifier        GrooveMonitor
hpqwmiex                     hpservice
Idle                         InoRpc
InoRT                        InoTask
ipoint                       lsass
lsm                          MOM
MSASCui                      notepad
...                          ...

```

## <a name="defining-the-wide-view"></a>넓은 뷰 정의

다음 XML에서는 [system.object](/dotnet/api/System.Diagnostics.Process) 개체에 대 한 넓은 뷰 스키마를 보여 줍니다.

```xml
View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <GroupBy>...</GroupBy>
  <Controls>...</Controls>
  <WideControl>
    <WideEntries>
      <WideEntry>
        <WideItem>
          <PropertyName>ProcessName</PropertyName>
        </WideItem>
      </WideEntry>
    </WideEntries>
  </WideControl>
</View>

```

다음 XML 요소는 넓은 뷰를 정의 하는 데 사용 됩니다.

- [뷰](./view-element-format.md) 요소는 넓은 뷰의 부모 요소입니다. 이 요소는 테이블, 목록 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.

- [Name](./name-element-for-view-format.md) 요소는 뷰의 이름을 지정 합니다. 이 요소는 모든 뷰에 필요 합니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 합니다. 필수적 요소로,

- [GroupBy](./groupby-element-for-view-format.md) 요소는 새 개체 그룹이 표시 되는 시기를 정의 합니다. 특정 속성 또는 스크립트의 값이 변경 될 때마다 새 그룹이 시작 됩니다. 이 요소는 선택적입니다.

- [Controls](./controls-element-for-view-format.md) 요소는 넓은 뷰로 정의 된 사용자 지정 컨트롤을 정의 합니다. 컨트롤을 통해 데이터 표시 방법을 추가로 지정할 수 있습니다. 이 요소는 선택적입니다. 뷰는 자체 사용자 지정 컨트롤을 정의 하거나 서식 파일의 뷰에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다. 사용자 지정 컨트롤에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.

- [WideControl](./widecontrol-element-format.md) 요소 및 해당 자식 요소는 뷰에 표시 되는 내용을 정의 합니다. 위의 예제에서 뷰는 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성을 표시 하도록 디자인 되었습니다.

간단한 넓은 뷰를 정의 하는 전체 서식 파일의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="providing-definitions-for-your-wide-view"></a>넓은 보기에 대 한 정의 제공

넓은 보기는 [WideControl](./widecontrol-element-format.md) 요소의 자식 요소를 사용 하 여 하나 이상의 정의를 제공할 수 있습니다. 일반적으로 보기에는 하나의 정의만 있습니다. 다음 예제에서는 뷰가 [Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성의 값을 표시 하는 단일 정의를 제공 합니다. 넓은 보기에는 속성 값 또는 스크립트 값 (예제에는 표시 되지 않음)이 표시 될 수 있습니다.

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber></ColumnNumber>
  <WideEntries>
    <WideEntry>
      <WideItem>
        <PropertyName>ProcessName</PropertyName>
      </WideItem>
    </WideEntry>
  </WideEntries>
</WideControl>
```

다음 XML 요소를 사용 하 여 넓은 보기에 대 한 정의를 제공할 수 있습니다.

- [WideControl](./widecontrol-element-format.md) 요소 및 해당 자식 요소는 뷰에 표시 되는 내용을 정의 합니다.

- [AutoSize](./autosize-element-for-widecontrol-format.md) 요소는 데이터 크기에 따라 열 크기 및 열 수를 조정 하는지 여부를 지정 합니다. 이 요소는 선택적입니다.

- [Columnnumber](./columnnumber-element-for-widecontrol-format.md) 요소는 넓은 보기에 표시 되는 열 수를 지정 합니다. 이 요소는 선택적입니다.

- [WideEntries](./wideentries-element-for-widecontrol-format.md) 요소는 뷰의 정의를 제공 합니다. 대부분의 경우 보기에는 하나의 정의만 있습니다. 필수적 요소로,

- [WideEntry](./wideentry-element-for-widecontrol-format.md) 요소는 뷰의 정의를 제공 합니다. 하나 이상의 [WideEntry](./wideentry-element-for-widecontrol-format.md) 가 필요 합니다. 그러나 추가할 수 있는 요소 수에 대 한 최대 제한은 없습니다. 대부분의 경우 보기에는 하나의 정의만 있습니다.

- [Entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소는 특정 정의에 의해 표시 되는 개체를 지정 합니다. 이 요소는 선택 사항이 며 다른 개체를 표시 하는 여러 [WideEntry](./wideentry-element-for-widecontrol-format.md) 요소를 정의 하는 경우에만 필요 합니다.

- [WideItem](./wideitem-element-for-widecontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다. 다른 뷰 형식과 달리, 넓은 컨트롤은 하나의 항목만 표시할 수 있습니다.

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소는 값이 뷰에 표시 되는 속성을 지정 합니다. 속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소는 값이 뷰에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 요소는 데이터를 표시 하는 데 사용 되는 패턴을 지정 합니다. 이 요소는 선택적입니다.

넓은 뷰 정의를 정의 하는 전체 서식 파일의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

## <a name="defining-the-objects-that-use-the-wide-view"></a>넓은 뷰를 사용 하는 개체 정의

넓은 뷰를 사용 하는 .NET 개체를 정의 하는 방법에는 두 가지가 있습니다. [Viewselectedby](./viewselectedby-element-format.md) 요소를 사용 하 여 뷰의 모든 정의에서 표시할 수 있는 개체를 정의 하거나, [entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소를 사용 하 여 뷰의 특정 정의에 표시 되는 개체를 정의할 수 있습니다. 대부분의 경우 뷰에는 정의가 하나만 있으므로 개체는 일반적으로 [Viewselectedby](./viewselectedby-element-format.md) 요소에 의해 정의 됩니다.

다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 사용 하 여 넓은 뷰로 표시 되는 개체를 정의 하는 방법을 보여 줍니다. 지정할 수 있는 [TypeName](./typename-element-for-viewselectedby-format.md) 요소의 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

다음 XML 요소를 사용 하 여 넓은 보기에서 사용 되는 개체를 지정할 수 있습니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 넓은 뷰로 표시 되는 개체를 정의 합니다.

- [TypeName](./typename-element-for-viewselectedby-format.md) 요소는 뷰에 표시 되는 .net을 지정 합니다. 정규화 된 .NET 형식 이름이 필요 합니다. 뷰에 대해 하나 이상의 유형 또는 선택 집합을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

전체 서식 파일의 예는 [넓은 뷰 (기본)](./wide-view-basic.md)를 참조 하세요.

다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소를 사용 합니다. 여러 뷰를 사용 하 여 표시 되는 관련 개체 집합을 사용 하는 선택 집합을 사용 합니다. 예를 들어, 동일한 개체에 대 한 넓은 뷰와 테이블 뷰를 정의할 수 있습니다. 선택 집합을 만드는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

다음 XML 요소를 사용 하 여 넓은 보기에서 사용 되는 개체를 지정할 수 있습니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 넓은 뷰로 표시 되는 개체를 정의 합니다.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소는 뷰에서 표시할 수 있는 개체 집합을 지정 합니다. 뷰에 대해 하나 이상의 선택 집합 또는 유형을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

다음 예제에서는 [Entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소를 사용 하 여 넓은 뷰의 특정 정의에 표시 되는 개체를 정의 하는 방법을 보여 줍니다. 이 요소를 사용 하 여 개체의 .NET 형식 이름, 개체의 선택 집합 또는 정의가 사용 되는 시기를 지정 하는 선택 조건을 지정할 수 있습니다. 선택 조건을 만드는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

다음 XML 요소를 사용 하 여 넓은 보기의 특정 정의에 사용 되는 개체를 지정할 수 있습니다.

- [Entryselectedby](./entryselectedby-element-for-wideentry-format.md) 요소는 정의에 의해 표시 되는 개체를 정의 합니다.

- [TypeName](./typename-element-for-viewselectedby-format.md) 요소는 정의에 의해 표시 되는 .net을 지정 합니다. 이 요소를 사용 하는 경우 정규화 된 .NET 형식 이름이 필요 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 (표시 되지 않음)는이 정의에 의해 표시 될 수 있는 개체 집합을 지정 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

- [Selectioncondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) 요소 (표시 되지 않음)는이 정의를 사용 하기 위해 존재 해야 하는 조건을 지정 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다. 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>넓은 보기에서 개체 그룹 표시

넓은 보기에 표시 되는 개체를 그룹으로 구분할 수 있습니다. 이는 그룹을 정의 하는 것이 아니라 특정 속성이 나 스크립트의 값이 변경 될 때마다 Windows PowerShell이 새 그룹을 시작 한다는 의미는 아닙니다. 다음 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 값이 변경 될 때마다 새 그룹을 시작 합니다.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

다음 XML 요소는 그룹이 시작 되는 시기를 정의 하는 데 사용 됩니다.

- [GroupBy](./groupby-element-for-view-format.md) 요소는 새 그룹을 시작 하 고 그룹이 표시 되는 방법을 정의 하는 속성 또는 스크립트를 정의 합니다.

- [PropertyName](./propertyname-element-for-groupby-format.md) 요소는 값이 변경 될 때마다 새 그룹을 시작 하는 속성을 지정 합니다. 그룹을 시작 하려면 속성이 나 스크립트를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소는 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다. 그룹을 시작 하려면 스크립트나 속성을 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [Label](./label-element-for-groupby-format.md) 요소는 각 그룹의 시작 부분에 표시 되는 레이블을 정의 합니다. 이 요소에 지정 된 텍스트 외에도 Windows PowerShell은 새 그룹을 트리거한 값을 표시 하 고 레이블 앞뒤에 빈 줄을 추가 합니다. 이 요소는 선택적입니다.

- [CustomControl](./customcontrol-element-for-groupby-format.md) 요소는 데이터를 표시 하는 데 사용 되는 컨트롤을 정의 합니다. 이 요소는 선택적입니다.

- [Customcontrolname](./customcontrolname-element-for-groupby-format.md) 요소는 데이터를 표시 하는 데 사용 되는 공용 또는 뷰 컨트롤을 지정 합니다. 이 요소는 선택적입니다.

그룹을 정의 하는 전체 서식 파일의 예는 [전체 뷰 (GroupBy)](./wide-view-groupby.md)를 참조 하세요.

## <a name="using-format-strings"></a>서식 문자열 사용

서식 문자열을 넓은 보기에 추가 하 여 데이터가 표시 되는 방법을 추가로 정의할 수 있습니다. 다음 예제에서는 `StartTime` 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

다음 XML 요소를 사용 하 여 형식 패턴을 지정할 수 있습니다.

- [WideItem](./wideitem-element-for-widecontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.

- [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소는 값이 뷰에 표시 되는 속성을 지정 합니다. 속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 요소는 속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

다음 예제에서는 스크립트의 값에 대 한 서식을 지정 하기 위해 `ToString` 메서드를 호출 합니다. 스크립트는 개체의 메서드를 호출할 수 있습니다. 따라서 개체에 형식 지정 매개 변수가 있는 `ToString`와 같은 메서드가 있는 경우 스크립트는 해당 메서드를 호출 하 여 스크립트의 출력 값에 대 한 형식을 지정할 수 있습니다.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

다음 XML 요소를 사용 하 여 `ToString` 메서드를 호출할 수 있습니다.

- [WideItem](./wideitem-element-for-widecontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.

- [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[넓은 보기 (기본)](./wide-view-basic.md)

[넓은 뷰 (GroupBy)](./wide-view-groupby.md)

[PowerShell 서식 파일 작성](./writing-a-powershell-formatting-file.md)
