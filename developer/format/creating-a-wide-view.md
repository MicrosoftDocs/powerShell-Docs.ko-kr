---
title: 넓은 보기 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d4303c5-b451-4ccb-9831-b17a17ceac20
caps.latest.revision: 16
ms.openlocfilehash: 651de5d3bc2619f20438f3951ac5a8c4b0bf46d4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066722"
---
# <a name="creating-a-wide-view"></a>넓게 보기 만들기

넓은 보기가 표시 되는 각 개체에 대 한 단일 값을 표시 합니다. 표시 된 값은.NET 개체 속성의 값 또는 스크립트의 값 수 있습니다. 기본적으로 레이블 또는이 보기에 대 한 헤더 없습니다.

## <a name="a-wide-view-display"></a>넓은 보기 표시

다음 예제에서는 Windows PowerShell의 표시 하는 방법을 보여 줍니다.는 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 에서 반환 되는 개체를 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet의 출력을 [ Format-wide](/powershell/module/Microsoft.PowerShell.Utility/Format-Wide) cmdlet. (기본적으로 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 테이블 뷰를 반환 합니다.) 이 예제에서는 두 열은 반환 된 각 개체에 대 한 프로세스의 이름을 표시 하려면 사용 됩니다. 개체의 속성의 이름을 표시 되지 않으면 속성의 값만 합니다.

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

## <a name="defining-the-wide-view"></a>넓은 보기를 정의합니다.

다음 XML의 넓은 보기 스키마를 표시 합니다 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 개체입니다.

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

다음 XML 요소를 와이드 뷰를 정의 하는 데 사용 됩니다.

- 합니다 [보기](./view-element-format.md) 요소는 부모 요소를 와이드 보기인 경우입니다. (테이블, 목록 및 사용자 지정 컨트롤 보기에 대 한 동일한 부모 요소입니다.)

- 합니다 [이름을](./name-element-for-view-format.md) 요소 뷰의 이름을 지정 합니다. 이 요소는 모든 보기에 필요 합니다.

- 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 뷰를 사용 하는 개체를 정의 합니다. 필수적 요소로,

- 합니다 [GroupBy](./groupby-element-for-view-format.md) 요소 개체의 새 그룹을 표시 될 때를 정의 합니다. 새 그룹을 특정 속성이 나 스크립트의 값이 변경 될 때마다 시작 됩니다. 이 요소는 선택 사항입니다.

- 합니다 [컨트롤](./controls-element-for-view-format.md) 요소 넓은 보기에서 정의한 사용자 지정 컨트롤을 정의 합니다. 컨트롤 추가 데이터가 표시 되는 방식을 지정 하는 방법을 제공 합니다. 이 요소는 선택 사항입니다. 뷰 자체 사용자 지정 컨트롤을 정의 하거나 형식 지정 파일의 보기 중 하나에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다. 사용자 지정 컨트롤에 대 한 자세한 내용은 참조 하세요. [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)합니다.

- 합니다 [WideControl](./widecontrol-element-format.md) 요소와 해당 자식 요소 보기에 표시 되는 항목을 정의 합니다. 앞의 예제에서 뷰를 표시 하도록 디자인 된 [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성입니다.

간단한 넓은 보기가 정의 하는 전체 서식 파일의 예제를 참조 하세요 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

## <a name="providing-definitions-for-your-wide-view"></a>넓은 보기에 대 한 정의 제공합니다.

와이드 뷰가의 자식 요소를 사용 하 여 하나 이상의 정의 제공할 수는 [WideControl](./widecontrol-element-format.md) 요소입니다. 일반적으로 뷰를 하나만 정의 해야 합니다. 다음 예제에서 보기의 값을 표시 하는 단일 정의 제공 합니다 [System.Diagnostics.Process.Processname](/dotnet/api/System.Diagnostics.Process.ProcessName) 속성입니다. 속성의 값 또는 값 (이 예제에 표시 되지 않음) 스크립트의 넓은 보기를 표시할 수 있습니다.

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

넓은 보기에 대 한 정의 제공 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [WideControl](./widecontrol-element-format.md) 요소와 해당 자식 요소 보기에 표시 되는 항목을 정의 합니다.

- 합니다 [AutoSize](./autosize-element-for-widecontrol-format.md) 조정 여부를 열 크기 및 열 개수는 데이터의 크기를 기준으로 요소를 지정 합니다. 이 요소는 선택 사항입니다.

- 합니다 [ColumnNumber](./columnnumber-element-for-widecontrol-format.md) 요소 넓은 보기에 표시 된 열의 수를 지정 합니다. 이 요소는 선택 사항입니다.

- 합니다 [WideEntries](./wideentries-element-for-widecontrol-format.md) 요소는 뷰의 정의 제공 합니다. 대부분의 경우에서 뷰를 하나만 정의 해야 합니다. 필수적 요소로,

- 합니다 [WideEntry](./wideentry-element-for-widecontrol-format.md) 요소 뷰의 정의 제공 합니다. 하나 이상의 [WideEntry](./wideentry-element-for-widecontrol-format.md) 필수 사항입니다; 그러나는 추가할 수 있는 요소의 수를 최대 제한이 있습니다. 대부분의 경우에서 뷰를 하나만 정의 해야 합니다.

- 합니다 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 요소는 특정 정의 의해 표시 되는 개체를 지정 합니다. 이 요소는 선택 사항이 며 여러 개를 정의 하는 경우에 필요 [WideEntry](./wideentry-element-for-widecontrol-format.md) 다른 개체를 표시 하는 요소입니다.

- 합니다 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다. 다른 유형의 보기와 달리 와이드 컨트롤 항목을 하나만 표시할 수 있습니다.

- 합니다 [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소 보기에서 해당 값이 표시 속성을 지정 합니다. 속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다. 스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 요소 데이터를 표시 하는 데 사용 되는 패턴을 지정 합니다. 이 요소는 선택 사항입니다.

넓은 보기 정의 정의 하는 전체 서식 파일의 예제를 보려면 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

## <a name="defining-the-objects-that-use-the-wide-view"></a>넓은 보기를 사용 하는 개체를 정의 합니다.

넓은 보기를 사용 하 여.NET 개체를 정의 하는 방법은 두 가지가 있습니다. 사용할 수는 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 정의의 보기를 통해 표시 될 수 있는 개체 정의를 사용할 수는 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 정의 개체를 표시 하는 요소는 특정 뷰의 정의 합니다. 대부분의 경우에서 보기 있으므로 하나만 정의 하 여 개체는 일반적으로 정의 된 [ViewSelectedBy](./viewselectedby-element-format.md) 요소입니다.

다음 예제에서는 와이드 보기인 경우 사용 하 여 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [TypeName](./typename-element-for-viewselectedby-format.md) 요소입니다. 수에 제한이 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 지정 하 고 해당 순서는 중요 하지 않습니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

넓은 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 넓은 보기에서 표시 되는 객체를 정의 합니다.

- 합니다 [TypeName](./typename-element-for-viewselectedby-format.md) 요소 보기에 표시 되는.NET을 지정 합니다. 정규화 된.NET 유형 이름이 필요 합니다. 하나 이상의 형식 또는 선택이 보기에 대 한 설정 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.

전체 서식 파일의 예제를 보려면 [와이드 보기인 경우 (기본)](./wide-view-basic.md)합니다.

다음 예제에서는 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 하 고 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소입니다. 관련된 넓은 보기를 정의 하는 경우와 같은 여러 뷰와 테이블 뷰를 사용 하 여 동일한 개체에 대해 표시 되는 개체 집합이 있는 선택 집합을 사용 합니다. 선택 영역 집합을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [선택 집합 정의](./defining-selection-sets.md)합니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <WideControl>...</WideControl>
</View>
```

넓은 보기에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [ViewSelectedBy](./viewselectedby-element-format.md) 요소 넓은 보기에서 표시 되는 객체를 정의 합니다.

- 합니다 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 보기에서 표시할 수 있는 개체 집합을 지정 합니다. 하나 이상 선택 집합 또는 보기에 대 한 형식을 지정 해야 하지만 지정할 수 있는 요소의 최대 수 없습니다.

다음 예제에서는 사용 하 여 와이드 보기인 경우 특정 정의 의해 표시 되는 개체를 정의 하는 방법을 보여 줍니다 합니다 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 요소입니다. 이 요소를 사용 하 여, 개체, 개체 집합을 선택 또는 선택 조건 정의 사용 하는 경우를 지정 하는.NET 형식 이름을 지정할 수 있습니다. 선택 조건을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

```xml
<WideEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</WideEntry>
```

넓은 보기 특정 정의에서 사용 되는 개체를 지정 하려면 다음 XML 요소를 사용할 수 있습니다.

- 합니다 [EntrySelectedBy](./entryselectedby-element-for-wideentry-format.md) 요소 정의 의해 표시 되는 객체를 정의 합니다.

- 합니다 [TypeName](./typename-element-for-viewselectedby-format.md) 요소 정의 의해 표시 되는.NET을 지정 합니다. 이 요소를 사용 하는 경우 정규화 된.NET 유형 이름이 필요 합니다. 하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.

- 합니다 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소 (표시 되지 않음)이이 정의 의해 표시 될 수 있는 개체 집합을 지정 합니다. 하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다.

- 합니다 [SelectionCondition](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md) 요소 (표시 되지 않음)이이 정의를 사용할 수 있어야 하는 조건을 지정 합니다. 하나 이상의 형식, 선택 항목 집합 또는 정의 대 한 선택 조건 지정 해야 하지만 지정할 수 있는 요소의 최대입니다. 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [표시 데이터에 대 한 조건을 정의](./defining-conditions-for-displaying-data.md)합니다.

## <a name="displaying-groups-of-objects-in-a-wide-view"></a>넓은 보기에서 개체의 그룹 표시

그룹으로 넓은 보기에 표시 되는 개체를 분리할 수 있습니다. 그렇다고 그룹을 정의 하는 Windows PowerShell 스크립트 또는 특정 속성의 값이 변경 될 때마다 새 그룹을 시작만 합니다. 다음 예제에서는 새 그룹을 시작 됩니다 때마다 값은 [System.Serviceprocess.Servicecontroller.Servicetype](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 변경 합니다.

```xml
<GroupBy>
  <Label>Service Type</Label>
  <PropertyName>ServiceType</PropertyName>
</GroupBy>

```

다음 XML 요소가 그룹 시작 될 때를 정의 하는 데 사용 됩니다.

- 합니다 [GroupBy](./groupby-element-for-view-format.md) 속성 또는 새 그룹을 시작 하 고 그룹 표시 되는 방식을 정의 하는 스크립트 요소를 정의 합니다.

- 합니다 [PropertyName](./propertyname-element-for-groupby-format.md) 요소 값이 변경 될 때마다 새 그룹을 시작 하는 속성을 지정 합니다. 속성 또는 그룹을 시작 하는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [ScriptBlock](./scriptblock-element-for-groupby-format.md) 요소는 해당 값이 변경 될 때마다 새 그룹을 시작 하는 스크립트를 지정 합니다. 스크립트 또는 그룹을 시작 하는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [레이블](./label-element-for-groupby-format.md) 요소는 각 그룹의 시작 부분에 표시 되는 레이블을 정의 합니다. 이 요소에 의해 지정 된 텍스트를 외에도 Windows PowerShell에는 새 그룹 트리거되고 레이블을 전후에 빈 줄을 추가 하는 값을 표시 합니다. 이 요소는 선택 사항입니다.

- 합니다 [CustomControl](./customcontrol-element-for-groupby-format.md) 요소에는 데이터를 표시 하는 데 사용 되는 컨트롤을 정의 합니다. 이 요소는 선택 사항입니다.

- [CustomControlName](./customcontrolname-element-for-groupby-format.md) 요소 지정 일반적인 보거나 데이터를 표시 하는 데 사용 되는 컨트롤입니다. 이 요소는 선택 사항입니다.

그룹을 정의 하는 전체 서식 파일의 예제를 보려면 [넓은 보기 (GroupBy)](./wide-view-groupby.md)합니다.

## <a name="using-format-strings"></a>서식 문자열 사용

데이터 표시 되는 방법을 추가로 정의할 넓은 보기로 서식 문자열을 추가할 수 있습니다. 다음 예제에서는 값의 서식 지정 문자열을 정의 하는 방법의 `StartTime` 속성입니다.

```xml
<WideItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</WideItem>
```

다음 XML 요소가 형식 패턴을 지정 하려면 사용할 수 있습니다.

- 합니다 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다.

- 합니다 [PropertyName](./propertyname-element-for-wideitem-for-widecontrol-format.md) 요소 보기에서 해당 값이 표시 속성을 지정 합니다. 속성 또는 스크립트를 지정 해야 하지만 둘 다 지정할 수 없습니다.

- 합니다 [FormatString](./formatstring-element-for-wideitem-for-widecontrol-format.md) 스크립트나 속성 값을 보기에 표시 되는 방식을 정의 하는 형식 패턴을 지정 하는 요소

- 합니다 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음) 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다. 스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.

다음 예제에서는 `ToString` 메서드를 호출 하는 스크립트의 값의 형식을 지정 합니다. 스크립트 개체의 모든 메서드를 호출할 수 있습니다. 따라서 개체에 있는 경우 메서드를 같은 `ToString`형식 매개 변수가 있는, 스크립트는 스크립트의 출력 값의 서식을 지정 하는 메서드를 호출할 수 있습니다.

```xml
<WideItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</WideItem>
```

호출 하는 다음 XML 요소를 사용할 수는 `ToString` 메서드:

- 합니다 [WideItem](./wideitem-element-for-widecontrol-format.md) 요소 보기에 표시 되는 데이터를 지정 합니다.

- 합니다 [ScriptBlock](./scriptblock-element-for-wideitem-for-widecontrol-format.md) 요소 (표시 되지 않음) 보기에서 해당 값이 표시 하는 스크립트를 지정 합니다. 스크립트 또는 속성을 지정 해야 하지만 둘 다 지정할 수 없습니다.

## <a name="see-also"></a>참고 항목

[넓은 보기 (Basic)](./wide-view-basic.md)

[넓은 보기 (GroupBy)](./wide-view-groupby.md)

[서식 파일을 PowerShell 작성](./writing-a-powershell-formatting-file.md)
