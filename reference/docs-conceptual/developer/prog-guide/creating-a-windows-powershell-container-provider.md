---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 컨테이너 공급자 만들기
description: Windows PowerShell 컨테이너 공급자 만들기
ms.openlocfilehash: 999bd69e3c16bfc0a74519986654ec15bbc0da6d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645356"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Windows PowerShell 컨테이너 공급자 만들기

이 항목에서는 다중 계층 데이터 저장소에서 작동할 수 있는 Windows PowerShell 공급자를 만드는 방법에 대해 설명 합니다. 이러한 유형의 데이터 저장소의 경우 저장소의 최상위 수준에 루트 항목이 포함 되 고 각 후속 수준은 자식 항목의 노드 라고 합니다. 사용자는 이러한 자식 노드에 대해 작업을 수행할 수 있으므로 데이터 저장소를 통해 계층적으로 상호 작용할 수 있습니다.

다중 수준 데이터 저장소에서 작업할 수 있는 공급자를 Windows PowerShell 컨테이너 공급자 라고 합니다. 그러나 Windows PowerShell 컨테이너 공급자는 항목을 포함 하는 컨테이너 (중첩 된 컨테이너 없음)가 하나 있는 경우에만 사용할 수 있습니다. 중첩 된 컨테이너가 있는 경우 Windows PowerShell 탐색 공급자를 구현 해야 합니다. Windows PowerShell 탐색 공급자를 구현 하는 방법에 대 한 자세한 내용은 [Windows Powershell 탐색 공급자 만들기](./creating-a-windows-powershell-navigation-provider.md)를 참조 하세요.

> [!NOTE]
> Windows Vista 및 .NET Framework 3.0 런타임 구성 요소에 대 한 Microsoft Windows 소프트웨어 개발 키트를 사용 하 여이 공급자에 대 한 c # 소스 파일 (AccessDBSampleProvider04.cs)을 다운로드할 수 있습니다. 다운로드 지침은 [Windows powershell을 설치 하 고 Windows POWERSHELL SDK를 다운로드 하는 방법](/powershell/scripting/developer/installing-the-windows-powershell-sdk)을 참조 하세요.
> 다운로드 된 원본 파일은 디렉터리에서 사용할 수 있습니다 **\<PowerShell Samples>** . 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 [Windows Powershell 공급자 디자인](./designing-your-windows-powershell-provider.md)을 참조 하세요.

여기에 설명 된 Windows PowerShell 컨테이너 공급자는 데이터베이스의 테이블 및 행이 컨테이너의 항목으로 정의 된 단일 컨테이너로 데이터베이스를 정의 합니다.

> [!CAUTION]
> 이 설계에서는 이름이 ID가 인 필드가 있는 데이터베이스를 가정 하 고 해당 필드의 형식은가 중 정수 라는 것을 알고 있어야 합니다.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Windows PowerShell 컨테이너 공급자 클래스 정의

Windows PowerShell 컨테이너 공급자는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스에서 파생 되는 .net 클래스를 정의 해야 합니다. 이 섹션에서 설명 하는 Windows PowerShell 컨테이너 공급자에 대 한 클래스 정의는 다음과 같습니다.

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
public class AccessDBProvider : ContainerCmdletProvider
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="34-35":::

이 클래스 정의에서 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 특성에는 두 개의 매개 변수가 포함 되어 있습니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 친숙 한 이름을 지정 합니다. 두 번째 매개 변수는 명령을 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자의 경우 추가 되는 Windows PowerShell 관련 기능이 없습니다.

## <a name="defining-base-functionality"></a>기본 기능 정의

[Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)에 설명 된 대로 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스는 다른 공급자 기능을 제공 하는 다른 여러 클래스에서 파생 됩니다. 따라서 Windows PowerShell 컨테이너 공급자는 해당 클래스에서 제공 하는 기능을 모두 정의 해야 합니다.

세션 관련 초기화 정보를 추가 하 고 공급자가 사용 하는 리소스를 해제 하는 기능을 구현 하려면 [기본 Windows PowerShell 공급자 만들기](./creating-a-basic-windows-powershell-provider.md)를 참조 하세요.
그러나 여기에 설명 된 공급자를 비롯 한 대부분의 공급자는 Windows PowerShell에서 제공 하는이 기능의 기본 구현을 사용할 수 있습니다.

데이터 저장소에 대 한 액세스 권한을 얻으려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 의 메서드를 구현 해야 합니다 (예를 들어, 공급자는 클래스의 메서드를 구현 해야 합니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)를 참조 하세요.

항목 가져오기, 설정 및 지우기와 같은 데이터 저장소의 항목을 조작 하려면 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 에서 제공 하는 메서드를 구현 해야 합니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)를 참조 하세요.

## <a name="retrieving-child-items"></a>자식 항목 검색

Windows PowerShell 컨테이너 공급자는 자식 항목을 검색 하기 위해 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 재정의 하 여 cmdlet의 호출을 지원 해야 합니다. `Get-ChildItem` 이 메서드는 데이터 저장소에서 자식 항목을 검색 하 여 파이프라인에 개체로 씁니다. `recurse`Cmdlet의 매개 변수를 지정 하는 경우 메서드는의 수준에 관계 없이 모든 자식을 검색 합니다. `recurse`매개 변수를 지정 하지 않으면 메서드는 단일 수준의 자식만 검색 합니다.

이 공급자에 대 한 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드의 구현은 다음과 같습니다. 이 메서드는 경로가 Access 데이터베이스를 나타내는 경우 모든 데이터베이스 테이블의 자식 항목을 검색 하 고 경로가 데이터 테이블을 나타내는 경우 해당 테이블의 행에서 자식 항목을 검색 합니다.

```csharp
protected override void GetChildItems(string path, bool recurse)
{
    // If path represented is a drive then the children in the path are
    // tables. Hence all tables in the drive represented will have to be
    // returned
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table, path, true);

            // if the specified item exists and recurse has been set then
            // all child items within it have to be obtained as well
            if (ItemExists(path) && recurse)
            {
                GetChildItems(path + pathSeparator + table.Name, recurse);
            }
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get the table name, row number and type of path from the
        // path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Obtain all the rows within the table
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);
            WriteItemObject(row, path + pathSeparator + row.RowNumber,
                        false);
        }
        else
        {
            // In this case, the path specified is not valid
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="311-362":::

#### <a name="things-to-remember-about-implementing-getchilditems"></a>GetChildItems 구현에 대해 기억할 사항

다음 조건은 Containercmdletprovider의 구현에 적용 될 수 있습니다. [Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 이 메서드의 구현에서는 항목이 사용자에 게 표시 될 수 있도록 하는 항목에 대 한 모든 형태의 액세스를 고려해 야 합니다. 예를 들어, 사용자가 파일 시스템 공급자 (Windows PowerShell에서 제공)를 통해 파일에 대 한 쓰기 권한을가지고 있지만 읽기 액세스 권한이 없는 경우 파일은 여전히 존재 하 고 System.object를 반환 합니다. [Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 를 반환 `true` 합니다. 구현에서 부모 항목을 확인 하 여 자식을 열거할 수 있는지 확인 해야 할 수 있습니다.

- 여러 항목을 작성할 때 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드는 약간의 시간이 걸릴 수 있습니다. 공급자를 디자인 하 여 한 번에 하나씩, [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 를 사용 하 여 항목을 작성할 수 있습니다. 이 기술을 사용 하면 사용자에 게 스트림의 항목이 표시 됩니다.

- [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 을 구현 하는 것은 순환 링크가 있는 경우 무한 재귀를 방지 하는 것입니다. 이러한 조건을 반영 하려면 적절 한 종료 예외를 throw 해야 합니다.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Get-ChildItem Cmdlet에 동적 매개 변수 연결

경우에 따라 `Get-ChildItem` Containercmdletprovider. [Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 를 호출 하는 cmdlet에는 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자가 [Containercmdletprovider. Getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다 `Get-ChildItem` .

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>자식 항목 이름 검색

자식 항목의 이름을 검색 하려면 Windows PowerShell 컨테이너 공급자가 [Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드를 재정의 하 여 `Get-ChildItem` `Name` 매개 변수가 지정 된 경우 cmdlet의 호출을 지원 해야 합니다. 이 메서드는 `returnAllContainers` cmdlet의 매개 변수가 지정 된 경우 모든 컨테이너에 대해 지정 된 경로 또는 자식 항목 이름에 대 한 자식 항목의 이름을 검색 합니다. 자식 이름은 경로의 리프 부분입니다. 예를 들어 c:\windows\system32\abc.dll 경로에 대 한 자식 이름은 "abc.dll"입니다. 디렉터리 \ 디렉터리의 자식 이름이 "system32"입니다.

이 공급자에 대 한 [Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드의 구현은 다음과 같습니다. 지정 된 경로가 테이블을 나타내는 경우에는 지정 된 경로가 Access 데이터베이스 (드라이브) 및 행 번호를 나타내는 경우이 메서드는 테이블 이름을 검색 합니다.

```csharp
protected override void GetChildNames(string path,
                            ReturnContainers returnContainers)
{
    // If the path represented is a drive, then the child items are
    // tables. get the names of all the tables in the drive.
    if (PathIsDrive(path))
    {
        foreach (DatabaseTableInfo table in GetTables())
        {
            WriteItemObject(table.Name, path, true);
        } // foreach (DatabaseTableInfo...
    } // if (PathIsDrive...
    else
    {
        // Get type, table name and row number from path specified
        string tableName;
        int rowNumber;

        PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

        if (type == PathType.Table)
        {
            // Get all the rows in the table and then write out the
            // row numbers.
            foreach (DatabaseRowInfo row in GetRows(tableName))
            {
                WriteItemObject(row.RowNumber, path, false);
            } // foreach (DatabaseRowInfo...
        }
        else if (type == PathType.Row)
        {
            // In this case the user has directly specified a row, hence
            // just give that particular row
            DatabaseRowInfo row = GetRow(tableName, rowNumber);

            WriteItemObject(row.RowNumber, path, false);
        }
        else
        {
            ThrowTerminatingInvalidPathException(path);
        }
    } // else
} // GetChildNames
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="369-411":::

#### <a name="things-to-remember-about-implementing-getchildnames"></a>GetChildNames 구현에 대해 기억할 사항

다음 조건은 Containercmdletprovider의 구현에 적용 될 수 있습니다. [Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

  > [!NOTE]
  > 이 규칙의 예외는 `returnAllContainers` cmdlet의 매개 변수가 지정 된 경우에 발생 합니다. 이 경우 메서드는 컨테이너에 대 한 자식 이름을 검색 해야 합니다. 즉, 해당 이름이 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter)의 값과 일치 하지 않는 경우에도 [이를 검색](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include)해야 합니다 .이 경우에는 [이 속성의](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 값이 일치 하지 않는 경우에도 마찬가지입니다.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가 지정 되지 않은 경우 일반적으로 사용자에 게 숨겨지는 개체의 이름을 검색 하지 않아야 합니다. 지정 된 경로가 컨테이너를 나타내는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 지정 하지 않아도 됩니다.

- [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 을 구현 하는 것은 순환 링크가 있는 경우 무한 재귀를 방지 하는 것입니다. 이러한 조건을 반영 하려면 적절 한 종료 예외를 throw 해야 합니다.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>동적 매개 변수를 Get-ChildItem Cmdlet (이름)에 연결

Cmdlet에 `Get-ChildItem` 매개 변수를 사용 하는 경우 `Name` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자가 [Containercmdletprovider. Getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다 `Get-ChildItem` .

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>항목 이름 바꾸기

항목의 이름을 바꾸려면 Windows PowerShell 컨테이너 공급자가 [Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드를 재정의 하 여 cmdlet의 호출을 지원 해야 합니다. `Rename-Item` 이 메서드는 지정 된 경로에 있는 항목의 이름을 제공 된 새 이름으로 변경 합니다. 새 이름은 항상 부모 항목 (컨테이너)에 상대적 이어야 합니다.

이 공급자는 [Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드를 재정의 하지 않습니다. 그러나 다음은 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>RenameItem 구현에 대해 기억할 사항

다음 조건은 Containercmdletprovider의 구현에 적용 될 수 있습니다. [Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- [Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드는 이동 작업에 대 한 것이 아니라 항목의 이름만 수정 하기 위한 것입니다.
  `newName`매개 변수에 경로 구분 기호가 포함 되어 있거나, 그렇지 않으면 항목의 부모 위치가 변경 될 수 있는 경우 메서드를 구현 하면 오류가 발생 합니다.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 지정 하지 않는 한 개체의 이름을 바꾸지 않아야 합니다. 지정 된 경로가 컨테이너를 나타내는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 지정 하지 않아도 됩니다.

- [Containercmdletprovider. Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드를 구현 하면 데이터 저장소를 변경 하기 전에를 호출 하 고 해당 반환 값을 확인 [해야 하는](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 경우를 들 수 있습니다. 이 메서드는 시스템 상태가 변경 될 때 (예: 파일 이름 바꾸기) 작업 실행을 확인 하는 데 사용 됩니다.
  Windows PowerShell 런타임이 사용자에 게 변경할 리소스의 [이름을 보내고,](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 표시 되는 항목을 결정 하는 데 사용 되는 모든 명령줄 설정이 나 기본 설정 변수를 고려 하 여 Windows PowerShell 런타임을 사용 합니다.

  Containercmdletprovider를 호출한 후에는 [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 가 반환 `true` 되 고, [Renameitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드는 system.object를 호출 해야 합니다. [shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드를 호출 하는 메서드를 호출 해야 합니다. 이 메서드는 사용자에 게 확인 메시지를 보내 작업을 계속 해야 하는 경우 추가 피드백을 허용 하도록 메시지를 보냅니다. 공급자는 잠재적으로 위험한 시스템 수정에 대 한 추가 검사로 [계속 합니다.](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue)

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Rename-Item Cmdlet에 동적 매개 변수 연결

경우에 따라 cmdlet에는 `Rename-Item` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자가 [Containercmdletprovider. Renameitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다 `Rename-Item` .

이 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>새 항목 만들기

새 항목을 만들려면 컨테이너 공급자가 cmdlet의 호출을 지원 하기 위해 [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 구현 해야 합니다. `New-Item` 이 메서드는 지정 된 경로에 있는 데이터 항목을 만듭니다. `type`Cmdlet의 매개 변수에는 새 항목에 대 한 공급자 정의 형식이 포함 되어 있습니다. 예를 들어 FileSystem 공급자는 값이 `type` "file" 또는 "directory" 인 매개 변수를 사용 합니다. `newItemValue`Cmdlet의 매개 변수는 새 항목의 공급자별 값을 지정 합니다.

이 공급자에 대 한 [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드의 구현은 다음과 같습니다.

```csharp
protected override void NewItem( string path, string type, object newItemValue )
{
    // Create the new item here after
    // performing necessary validations
    //
    // WriteItemObject(newItemValue, path, false);

    // Example
    //
    // if (ShouldProcess(path, "new item"))
    // {
    //      // Create a new item and then call WriteObject
    //      WriteObject(newItemValue, path, false);
    // }

} // NewItem
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="939-955":::

#### <a name="things-to-remember-about-implementing-newitem"></a>NewItem 구현에 대해 기억할 사항

다음 조건은 Containercmdletprovider의 구현에 적용 될 수 있습니다. [Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드는 매개 변수에 전달 된 문자열에 대 한 대/소문자를 구분 하지 않는 비교를 수행 해야 합니다. `type`
  또한 모호한 일치 항목을 최소한으로 허용 해야 합니다. 예를 들어 "file" 및 "directory" 유형의 경우 모호성을 위해 첫 문자만 필요 합니다. `type`매개 변수가 공급자에서 만들 수 없는 형식을 나타내는 경우 [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드는 공급자가 만들 수 있는 형식을 나타내는 메시지와 함께 ArgumentException를 작성 해야 합니다.

- `newItemValue`매개 변수의 경우 [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 구현 하 여 최소한의 문자열을 허용 하는 것이 좋습니다. 동일한 경로에 대 한 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 메서드에서 검색 된 개체의 형식에도 동의 해야 하는 경우. [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드는 [languageprimitives.physicalhash. convertto-html *](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) 메서드를 사용 하 여 형식을 원하는 형식으로 변환할 수 있습니다.

- [Containercmdletprovider. Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 구현 하면 데이터 저장소를 변경 하기 전에를 호출 하 고 해당 반환 값을 확인 [해야 하는](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 경우를 들 수 있습니다. Containercmdletprovider를 호출한 후에는 [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 가 true를 반환 하 고, [Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) [메서드는 잠재적](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 으로 위험한 시스템 수정에 대 한 추가 검사로 메서드를 호출 해야 하는 경우를 들 수 있습니다 (예를 들어).

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>New-Item Cmdlet에 동적 매개 변수 연결

경우에 따라 cmdlet에는 `New-Item` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 컨테이너 공급자가 Containercmdletprovider. n e t [parameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 메서드를 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다 `New-Item` .

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>항목 제거

항목을 제거 하려면 Windows PowerShell 공급자가 [Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 재정의 하 여 cmdlet의 호출을 지원 해야 합니다. `Remove-Item` 이 메서드는 지정 된 경로에서 데이터 저장소의 항목을 삭제 합니다. `recurse`Cmdlet의 매개 변수가 `Remove-Item` 로 설정 된 경우 `true` 메서드는 해당 수준에 관계 없이 모든 자식 항목을 제거 합니다. 매개 변수가로 설정 되 면 `false` 메서드는 지정 된 경로에서 단일 항목만 제거 합니다.

이 공급자는 항목 제거를 지원 하지 않습니다. 그러나 다음 코드는 [Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>RemoveItem 구현에 대해 기억할 사항

다음 조건은 Containercmdletprovider의 구현에 적용 될 수 있습니다. [Newitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 가 true로 설정 된 경우를 제외 하 고는 개체를 제거 하면 안 됩니다. 지정 된 경로가 컨테이너를 나타내는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 지정 하지 않아도 됩니다.

- [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 을 구현 하는 것은 순환 링크가 있는 경우 무한 재귀를 방지 하는 것입니다. 이러한 조건을 반영 하려면 적절 한 종료 예외를 throw 해야 합니다.

- [Containercmdletprovider. Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 구현 하면 데이터 저장소를 변경 하기 전에를 호출 하 고 해당 반환 값을 확인 [해야 하는](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 경우를 들 수 있습니다. Containercmdletprovider에 대 한 호출 후에는 [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 가 반환 됩니다. `true` [Removeitem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드는 잠재적으로 위험한 시스템 수정에 대 한 추가 검사로 서 메서드를 호출 해야 하 [](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 는 경우를 들 수 있습니다.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Remove-Item Cmdlet에 동적 매개 변수 연결

경우에 따라 cmdlet에는 `Remove-Item` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 컨테이너 공급자가 이러한 매개 변수를 처리 하는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 을 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 동적 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다 `Remove-Item` .

이 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)의 기본 구현으로,이는 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>자식 항목 쿼리

지정 된 경로에 자식 항목이 있는지 여부를 확인 하려면 Windows PowerShell 컨테이너 공급자가 [Containercmdletprovider *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 메서드를 재정의 해야 합니다. 항목에 자식이 있으면이 메서드는를 반환 `true` 하 고 `false` 그렇지 않으면를 반환 합니다. Null 또는 빈 경로의 경우 메서드는 데이터 저장소의 모든 항목을 자식으로 간주 하 고를 반환 `true` 합니다.

다음은 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 에 대 한 재정의입니다 (예를 들어, 청크 경로 도우미 메서드에 의해 생성 된 경로 파트가 세 개 이상일 경우에는 `false` 데이터베이스 컨테이너와 테이블 컨테이너만 정의 되어 있기 때문에 메서드는를 반환 합니다. 이 도우미 메서드에 대 한 자세한 내용은 [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)에서 chunkpath 메서드를 참조 하세요.

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs" range="1094-1097":::

#### <a name="things-to-remember-about-implementing-haschilditems"></a>HasChildItems 구현에 대해 기억할 사항

Containercmdletprovider의 구현에는 다음 조건이 적용 될 수 있습니다. [*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- 컨테이너 공급자가 흥미로운 탑재 지점이 포함 된 루트를 노출 하는 경우 [](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) `true` 경로에 대해 null 또는 빈 문자열이 전달 되 면 Containercmdletprovider의 구현이을 반환 해야 합니다.

## <a name="copying-items"></a>항목 복사

항목을 복사 하려면 컨테이너 공급자가 cmdlet의 호출을 지원 하기 위해 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 메서드를 구현 해야 합니다. `Copy-Item` 이 메서드는 `path` cmdlet의 매개 변수에 지정 된 위치에서 매개 변수가 나타내는 위치로 데이터 항목을 복사 `copyPath` 합니다. `recurse`매개 변수가 지정 된 경우 메서드는 모든 하위 컨테이너를 복사 합니다. 매개 변수를 지정 하지 않으면 메서드는 단일 수준의 항목만 복사 합니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 ContainerCmdletProvider의 기본 구현입니다 .이 [항목](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)은

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>CopyItem 구현에 대해 기억할 사항

[ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)을 구현 하는 데 다음 조건이 적용 될 수 있습니다.

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자가 ExpandWildcards, Filter, Include 또는 Exclude의 공급자 기능을 [system.object](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형에서 선언할 수 있습니다. 이러한 경우 [Containercmdletprovider. Getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 구현 하면 메서드에 전달 된 경로가 지정 된 기능의 요구 사항을 충족 하는지 확인 해야 합니다. 이 작업을 수행 하려면 메서드가 적절 한 속성 (예: System.object)에 액세스 해야 합니다. [*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 및 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) .... n a m.

- 기본적으로이 메서드의 재정의는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를로 설정 하지 않으면 기존 개체를 통해 개체를 복사 하면 안 됩니다. `true` 예를 들어 파일 [시스템](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 공급자는 기존 c:\abc.txt 파일을 통해 c:\temp\abc.txt를 복사 하지 않습니다. 예를 들어,이 속성은로 설정 되어 있지 않습니다. `true` 매개 변수에 지정 된 경로가 `copyPath` 존재 하 고 컨테이너를 나타내는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 를 지정 하지 않아도 됩니다. 이 경우 [ContainerCmdletProvider 항목](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 은 매개 변수로 표시 되는 항목을 `path` 매개 변수로 표시 된 컨테이너에 복사 해야 합니다 `copyPath` .

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 를 구현 하는 것은 순환 링크가 있는 경우 무한 재귀를 방지 하는 것입니다. 이러한 조건을 반영 하려면 적절 한 종료 예외를 throw 해야 합니다.

- [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 메서드를 구현 하면 데이터 저장소를 변경 하기 전에 해당 반환 값을 확인 [하 고 해당 반환 값을 확인](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 하는 것도 가능 해야 합니다. ContainerCmdletProvider를 호출한 후에는 [ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 가 true를 반환 하 고, 잠재적으로 위험한 시스템 수정에 대 한 추가 확인으로 [](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) [메서드를](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 호출 해야 하는 경우를 들 수 있습니다 (예를 들어) 합니다. 이러한 메서드를 호출 하는 방법에 대 한 자세한 내용은 [항목 이름 바꾸기](#renaming-items)를 참조 하세요.

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Copy-Item Cmdlet에 동적 매개 변수 연결

경우에 따라 cmdlet에는 `Copy-Item` 런타임에 동적으로 지정 되는 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자가 이러한 매개 변수를 처리 하는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 을 구현 해야 합니다. 이 메서드는 지정 된 경로에서 항목에 대 한 매개 변수를 검색 하 고 cmdlet 클래스 또는 [Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체와 유사한 구문 분석 특성이 있는 속성 및 필드가 있는 개체를 반환 합니다. Windows PowerShell 런타임은 반환 된 개체를 사용 하 여 cmdlet에 매개 변수를 추가 합니다 `Copy-Item` .

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)의 기본 구현으로,이는 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>코드 예제

전체 샘플 코드는 [AccessDbProviderSample04 코드 샘플](./accessdbprovidersample04-code-sample.md)을 참조 하세요.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 빌드

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법을](/previous-versions/ms714644(v=vs.85))참조 하세요.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows powershell 공급자를 Windows PowerShell에 등록 한 경우 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 다음 예제 출력에서는 가상의 Access 데이터베이스를 사용 합니다.

1. Cmdlet을 실행 `Get-ChildItem` 하 여 Access 데이터베이스의 Customers 테이블에서 자식 항목 목록을 검색 합니다.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   다음 출력이 표시됩니다.

   ```output
   PSPath        : AccessDB::customers
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : True
   Data          : System.Data.DataRow
   Name          : Customers
   RowCount      : 91
   Columns       :
   ```

2. Cmdlet을 `Get-ChildItem` 다시 실행 하 여 테이블의 데이터를 검색 합니다.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   다음 출력이 표시됩니다.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. 이제 cmdlet을 사용 `Get-Item` 하 여 데이터 테이블의 0 행에 있는 항목을 검색 합니다.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   다음 출력이 표시됩니다.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. 을 다시 사용 `Get-Item` 하 여 0 행의 항목에 대 한 데이터를 검색 합니다.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   다음 출력이 표시됩니다.

   ```output
   CustomerID   : 1234
   CompanyName  : Fabrikam
   ContactName  : Eric Gruber
   ContactTitle : President
   Address      : 4567 Main Street
   City         : Buffalo
   Region       : NY
   PostalCode   : 98052
   Country      : USA
   Phone        : (425) 555-0100
   Fax          : (425) 555-0101
   ```

5. 이제 cmdlet을 사용 `New-Item` 하 여 기존 테이블에 행을 추가 합니다. `Path`매개 변수는 행의 전체 경로를 지정 하 고 테이블의 기존 행 수보다 큰 행 번호를 나타내야 합니다. `Type`매개 변수는 추가할 항목의 형식을 지정 하는 "row"를 나타냅니다.
   마지막으로 `Value` 매개 변수는 행의 열 값에 대 한 쉼표로 구분 된 목록을 지정 합니다.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. 다음과 같이 새 항목 작업이 올바른지 확인 합니다.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   다음 출력이 표시됩니다.

   ```output
   ID        : 3
   FirstName : Eric
   LastName  : Gruber
   Email     : ericgruber@fabrikam.com
   Title     : President
   Company   : Fabrikam
   WorkPhone : (425) 555-0100
   Address   : 4567 Main Street
   City      : Buffalo
   State     : NY
   Zip       : 98052
   Country   : USA
   ```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 공급자 만들기](./how-to-create-a-windows-powershell-provider.md)

[Windows PowerShell 공급자 설계](./designing-your-windows-powershell-provider.md)

[항목 Windows PowerShell 공급자 구현](./creating-a-windows-powershell-item-provider.md)

[탐색 Windows PowerShell 공급자 구현](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)
