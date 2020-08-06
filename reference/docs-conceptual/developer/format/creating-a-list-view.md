---
title: 목록 뷰 만들기 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 24eb673e0db011a1439fa5ba1f2966fcc3bdc338
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783775"
---
# <a name="creating-a-list-view"></a>목록 보기 만들기

목록 뷰는 단일 열 (순서 대로)에 데이터를 표시 합니다. 목록에 표시 되는 데이터는 .NET 속성의 값 또는 스크립트의 값일 수 있습니다.

## <a name="a-list-view-display"></a>목록 보기 표시

다음 출력은 Windows PowerShell에서 Servicecontroller의 속성을 표시 하는 방법을 보여 줍니다 [. Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) cmdlet에 의해 반환 [되는](/powershell/module/microsoft.powershell.management/get-service) Fullname 개체입니다. 이 예제에서는 세 개의 개체가 반환 되 고 각 개체는 이전 개체와 빈 줄로 구분 됩니다.

```powershell
Get-Service | format-list
```

```output
Name                : AEADIFilters
DisplayName         : Andrea ADI Filters Service
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess

Name                : AeLookupSvc
DisplayName         : Application Experience
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32ShareProcess

Name                : AgereModemAudio
DisplayName         : Agere Modem Call Progress Audio
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : False
CanStop             : True
ServiceType         : Win32OwnProcess
...
```

## <a name="defining-the-list-view"></a>목록 뷰 정의

다음 XML은 Servicecontroller의 여러 속성을 표시 하기 위한 목록 뷰 스키마를 보여 줍니다 [. Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) 개체입니다. 목록 뷰에 표시 하려는 각 속성을 지정 해야 합니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

다음 XML 요소를 사용 하 여 목록 뷰를 정의 합니다.

- [뷰](./view-element-format.md) 요소는 목록 뷰의 부모 요소입니다. 이는 테이블, 전체 및 사용자 지정 컨트롤 뷰의 부모 요소와 동일 합니다.

- [Name](./name-element-for-view-format.md) 요소는 뷰의 이름을 지정 합니다. 이 요소는 모든 뷰에 필요 합니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 뷰를 사용 하는 개체를 정의 합니다. 이 요소는 필수 요소입니다.

- [GroupBy](./groupby-element-for-view-format.md) 요소는 새 개체 그룹이 표시 되는 시기를 정의 합니다. 특정 속성 또는 스크립트의 값이 변경 될 때마다 새 그룹이 시작 됩니다. 이 요소는 선택적입니다.

- [Controls](./controls-element-for-view-format.md) 요소는 목록 뷰에서 정의 된 사용자 지정 컨트롤을 정의 합니다. 컨트롤을 통해 데이터 표시 방법을 추가로 지정할 수 있습니다. 이 요소는 선택적입니다. 뷰는 자체 사용자 지정 컨트롤을 정의 하거나 서식 파일의 뷰에서 사용할 수 있는 공용 컨트롤을 사용할 수 있습니다. 사용자 지정 컨트롤에 대 한 자세한 내용은 [사용자 지정 컨트롤 만들기](./creating-custom-controls.md)를 참조 하세요.

- [이 listcontrol](./listcontrol-element-format.md) 요소는 뷰에 표시 되는 내용 및 형식을 지정 하는 방법을 정의 합니다. 다른 모든 뷰와 마찬가지로 목록 보기에는 스크립트에 의해 생성 된 개체 속성 또는 값의 값이 표시 될 수 있습니다.

간단한 목록 뷰를 정의 하는 전체 서식 파일의 예는 [목록 뷰 (Basic)](./list-view-basic.md)를 참조 하세요.

## <a name="providing-definitions-for-your-list-view"></a>목록 뷰에 대 한 정의 제공

목록 뷰는 [이 listcontrol](./listcontrol-element-format.md) 요소의 자식 요소를 사용 하 여 하나 이상의 정의를 제공할 수 있습니다. 일반적으로 보기에는 하나의 정의만 있습니다. 다음 예제에서 뷰는 System.object의 여러 속성을 표시 하는 단일 정의를 제공 합니다. [ Displayproperty = Fullname](/dotnet/api/System.Diagnostics.Process) 개체입니다. 목록 뷰에는 속성 값 또는 스크립트 값 (예제에는 표시 되지 않음)이 표시 될 수 있습니다.

```xml
<ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>

```

다음 XML 요소를 사용 하 여 목록 뷰에 대 한 정의를 제공할 수 있습니다.

- [이 listcontrol](./listcontrol-element-format.md) 요소 및 해당 자식 요소는 뷰에 표시 되는 내용을 정의 합니다.

- [ListEntries](./listentries-element-for-listcontrol-format.md) 요소는 뷰의 정의를 제공 합니다. 대부분의 경우 보기에는 하나의 정의만 있습니다. 이 요소는 필수 요소입니다.

- [ListEntry](./listentry-element-for-listcontrol-format.md) 요소는 뷰의 정의를 제공 합니다. 하나 이상의 [ListEntry](./listentry-element-for-listcontrol-format.md) 가 필요 합니다. 그러나 추가할 수 있는 요소 수에 대 한 최대 제한은 없습니다. 대부분의 경우 보기에는 하나의 정의만 있습니다.

- [Entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소는 특정 정의에 의해 표시 되는 개체를 지정 합니다. 이 요소는 선택 사항이 며 다른 개체를 표시 하는 여러 [ListEntry](./listentry-element-for-listcontrol-format.md) 요소를 정의 하는 경우에만 필요 합니다.

- [ListItems](./listitems-element-for-listentry-for-listcontrol-format.md) 요소는 목록 뷰의 행에 값이 표시 되는 속성 및 스크립트를 지정 합니다.

- [ListItem](./listitems-element-for-listentry-for-listcontrol-format.md) 요소는 값이 목록 뷰의 행에 표시 되는 속성 또는 스크립트를 지정 합니다. 목록 뷰에서 하나 이상의 속성 또는 스크립트를 지정 해야 합니다. 지정할 수 있는 행 수에 대 한 최대 제한은 없습니다.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소는 값이 행에 표시 되는 속성을 지정 합니다. 속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소는 값이 행에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [Label](./label-element-for-listitem-for-listcontrol-format.md) 요소는 행에서 속성 또는 스크립트 값의 왼쪽에 표시 되는 레이블을 지정 합니다. 이 요소는 선택적입니다. 레이블을 지정 하지 않으면 속성이 나 스크립트의 이름이 표시 됩니다. 전체 예제는 [목록 뷰 (레이블)](./list-view-labels.md)를 참조 하세요.

- [Itemselectioncondition](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md) 요소는 행을 표시 하기 위해 존재 해야 하는 조건을 지정 합니다. 목록 뷰에 조건을 추가 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요. 이 요소는 선택적입니다.

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) 요소는 속성이 나 스크립트의 값을 표시 하는 데 사용 되는 패턴을 지정 합니다. 이 요소는 선택적입니다.

간단한 목록 뷰를 정의 하는 전체 서식 파일의 예는 [목록 뷰 (Basic)](./list-view-basic.md)를 참조 하세요.

## <a name="defining-the-objects-that-use-the-list-view"></a>목록 뷰를 사용 하는 개체 정의

목록 뷰를 사용 하는 .NET 개체를 정의 하는 방법에는 두 가지가 있습니다. [Viewselectedby](./viewselectedby-element-format.md) 요소를 사용 하 여 뷰의 모든 정의에서 표시할 수 있는 개체를 정의 하거나, [entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소를 사용 하 여 뷰의 특정 정의에 표시 되는 개체를 정의할 수 있습니다. 대부분의 경우 뷰에는 정의가 하나만 있으므로 개체는 일반적으로 [Viewselectedby](./viewselectedby-element-format.md) 요소에 의해 정의 됩니다.

다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [TypeName](./typename-element-for-viewselectedby-format.md) 요소를 사용 하 여 목록 뷰에 표시 되는 개체를 정의 하는 방법을 보여 줍니다. 지정할 수 있는 [TypeName](./typename-element-for-viewselectedby-format.md) 요소의 수에는 제한이 없으며 해당 순서는 중요 하지 않습니다.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

다음 XML 요소는 목록 뷰에서 사용 되는 개체를 지정 하는 데 사용할 수 있습니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.

- [TypeName](./typename-element-for-viewselectedby-format.md) 요소는 뷰에 표시 되는 .net 개체를 지정 합니다. 정규화 된 .NET 형식 이름이 필요 합니다. 뷰에 대해 하나 이상의 유형 또는 선택 집합을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

전체 서식 파일에 대 한 예제는 [목록 뷰 (기본)](./list-view-basic.md)를 참조 하세요.

다음 예제에서는 [Viewselectedby](./viewselectedby-element-format.md) 및 [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소를 사용 합니다. 동일한 개체에 대 한 목록 뷰 및 테이블 뷰를 정의 하는 경우와 같이 여러 뷰를 사용 하 여 표시 되는 관련 개체 집합이 있는 선택 집합을 사용 합니다. 선택 집합을 만드는 방법에 대 한 자세한 내용은 [선택 집합 정의](./defining-selection-sets.md)를 참조 하세요.

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <SelectionSetName>.NET Type Set</SelectionSetName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

다음 XML 요소는 목록 뷰에서 사용 되는 개체를 지정 하는 데 사용할 수 있습니다.

- [Viewselectedby](./viewselectedby-element-format.md) 요소는 목록 뷰에서 표시 되는 개체를 정의 합니다.

- [SelectionSetName](./selectionsetname-element-for-viewselectedby-format.md) 요소는 뷰에서 표시할 수 있는 개체 집합을 지정 합니다. 뷰에 대해 하나 이상의 선택 집합 또는 유형을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

다음 예제에서는 [Entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소를 사용 하 여 목록 뷰의 특정 정의에 표시 되는 개체를 정의 하는 방법을 보여 줍니다. 이 요소를 사용 하 여 개체의 .NET 형식 이름, 개체의 선택 집합 또는 정의가 사용 되는 시기를 지정 하는 선택 조건을 지정할 수 있습니다. 선택 조건을 만드는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>.NET Type</TypeName>
  </EntrySelectedBy>
</ListEntry>
```

다음 XML 요소를 사용 하 여 목록 뷰의 특정 정의에서 사용 되는 개체를 지정할 수 있습니다.

- [Entryselectedby](./entryselectedby-element-for-listentry-for-listcontrol-format.md) 요소는 정의에 의해 표시 되는 개체를 정의 합니다.

- [TypeName](./typename-element-for-entryselectedby-for-listcontrol-format.md) 요소는 정의에 의해 표시 되는 .net 개체를 지정 합니다. 이 요소를 사용 하는 경우 정규화 된 .NET 형식 이름이 필요 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

- [SelectionSetName](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의에 의해 표시 될 수 있는 개체 집합을 지정 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다.

- [Selectioncondition](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md) 요소 (표시 되지 않음)는이 정의를 사용 하기 위해 존재 해야 하는 조건을 지정 합니다. 정의에 대해 하나 이상의 유형, 선택 집합 또는 선택 조건을 지정 해야 하지만 지정할 수 있는 최대 요소 수는 없습니다. 선택 조건을 정의 하는 방법에 대 한 자세한 내용은 [데이터 표시 조건 정의](./defining-conditions-for-displaying-data.md)를 참조 하세요.

## <a name="displaying-groups-of-objects-in-a-list-view"></a>목록 뷰에서 개체 그룹 표시

목록 뷰에서 표시 되는 개체를 그룹으로 구분할 수 있습니다. 이는 그룹을 정의 하는 것이 아니라 특정 속성이 나 스크립트의 값이 변경 될 때마다 Windows PowerShell이 새 그룹을 시작 한다는 의미는 아닙니다. 다음 예에서는 [Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController.ServiceType) 속성 값이 변경 될 때마다 새 그룹을 시작 합니다.

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

그룹을 정의 하는 전체 서식 파일에 대 한 예제는 [목록 뷰 (GroupBy)](./list-view-groupby.md)를 참조 하세요.

## <a name="using-format-strings"></a>서식 문자열 사용

서식 문자열을 뷰에 추가 하 여 데이터 표시 방법을 추가로 정의할 수 있습니다. 다음 예제에서는 속성의 값에 대 한 서식 문자열을 정의 하는 방법을 보여 줍니다 `StartTime` .

```xml
<ListItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</ListItem>
```

다음 XML 요소를 사용 하 여 형식 패턴을 지정할 수 있습니다.

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.

- [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) 요소는 값이 뷰에 표시 되는 속성을 지정 합니다. 속성 또는 스크립트 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

- [FormatString](./formatstring-element-for-listitem-for-listcontrol-format.md) 요소는 속성 또는 스크립트 값이 뷰에 표시 되는 방법을 정의 하는 형식 패턴을 지정 합니다.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

다음 예제에서는 `ToString` 메서드를 호출 하 여 스크립트의 값에 대 한 형식을 지정 합니다. 스크립트는 개체의 메서드를 호출할 수 있습니다. 따라서 개체에 `ToString` 형식 매개 변수를 포함 하는 등의 메서드가 있는 경우 스크립트는 해당 메서드를 호출 하 여 스크립트의 출력 값에 대 한 형식을 지정할 수 있습니다.

```xml
<ListItem>
  <ScriptBlock>
    [String}::Format("(0,10) (1,8)", .LastWriteTime.ToString("d"),
    $_.LastWriteTime.Totring("t"))
  </ScriptBlock>
</ListItem>
```

다음 XML 요소를 사용 하 여 메서드를 호출할 수 있습니다 `ToString` .

- [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) 요소는 뷰에 표시 되는 데이터를 지정 합니다.

- [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) 요소 (표시 되지 않음)는 값이 뷰에 표시 되는 스크립트를 지정 합니다. 스크립트나 속성 중 하나를 지정 해야 하지만 둘 다 지정할 수는 없습니다.

## <a name="see-also"></a>참고 항목

[Writing a Windows PowerShell Cmdlet(Windows PowerShell Cmdlet 작성)](../cmdlet/writing-a-windows-powershell-cmdlet.md)
