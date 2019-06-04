---
title: Windows PowerShell 컨테이너 공급자 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide], container provider
- container providers [PowerShell Programmer's Guide]
ms.assetid: a7926647-0d18-45b2-967e-b31f92004bc4
caps.latest.revision: 5
ms.openlocfilehash: 9e7da13ff559e802d52df475f2a555baeeeef983
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855191"
---
# <a name="creating-a-windows-powershell-container-provider"></a>Windows PowerShell 컨테이너 공급자 만들기

이 항목에서는 다중 계층 데이터 저장소에서 사용할 수 있는 Windows PowerShell 공급자를 만드는 방법을 설명 합니다. 이 유형의 데이터 저장소에 대 한 루트 항목을 포함 하는 저장소의 최상위 및 하위 항목 노드로 이어지는 각 수준 라고 합니다. 사용자가 이러한 자식 노드 작업 하도록 함으로써 사용자는 데이터 저장소를 통해 계층적으로 작용할 수 있습니다.

여러 수준의 데이터 저장소에서 사용할 수 있는 공급자는 Windows PowerShell 컨테이너 공급자 라고 합니다. 그러나 하나의 컨테이너 (중첩 된 컨테이너 없음) 항목을 사용 하 여 필요한 경우에 Windows PowerShell 컨테이너 공급자를 사용할 수 있는지 유의 합니다. 중첩 된 컨테이너의 경우 Windows PowerShell 탐색 공급자를 구현 해야 합니다. Windows PowerShell 탐색 공급자를 구현 하는 방법에 대 한 자세한 내용은 참조 하십시오 [Windows PowerShell 탐색 공급자 만들기](./creating-a-windows-powershell-navigation-provider.md)합니다.

> [!NOTE]
> 다운로드할 수 있습니다는 C# Microsoft Windows 소프트웨어 개발 키트에 대 한 Windows Vista 및.NET Framework 3.0 런타임 구성 요소를 사용 하 여이 공급자에 대 한 원본 파일 (AccessDBSampleProvider04.cs). 다운로드 지침에 대해서 [Windows PowerShell 설치 및 Windows PowerShell SDK를 다운로드 하는 방법을](/powershell/developer/installing-the-windows-powershell-sdk)합니다.
>
> 다운로드 한 소스 파일에서 사용할 수는  **\<PowerShell 샘플 >** 디렉터리입니다.
>
> 다른 Windows PowerShell 공급자 구현에 대 한 자세한 내용은 참조 하십시오 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)합니다.

여기에 설명 된 Windows PowerShell 컨테이너 공급자 데이터베이스 테이블 및 컨테이너의 항목으로 정의 된 데이터베이스의 행을 사용 하 여 단일 컨테이너를 정의 합니다.

> [!CAUTION]
> 이 디자인 이름 ID 사용 하 여 필드가 있는 데이터베이스를 가정 하 고 필드의 형식이 LongInteger 알아야 합니다.

## <a name="defining-a-windows-powershell-container-provider-class"></a>Windows PowerShell 컨테이너 공급자 클래스를 정의합니다.

Windows PowerShell 컨테이너 공급자에서 파생 되는.NET 클래스를 정의 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 기본 클래스입니다. 이 섹션에 설명 된 Windows PowerShell 컨테이너 공급자에 대 한 클래스 정의 다음과 같습니다.

```csharp
   [CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L34-L35 "AccessDBProviderSample04.cs")]

이 클래스를 정의 하는 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 두 매개 변수를 포함 하는 특성입니다. 첫 번째 매개 변수는 Windows PowerShell에서 사용 되는 공급자에 대 한 알기 쉬운 이름을 지정 합니다. 두 번째 매개 변수는 명령 처리 하는 동안 공급자가 Windows PowerShell 런타임에 노출 하는 Windows PowerShell 특정 기능을 지정 합니다. 이 공급자에 대 한 추가 되는 Windows PowerShell 특정 기능이 없으며 있습니다.

## <a name="defining-base-functionality"></a>기본 기능 정의

에 설명 된 대로 [Your Windows PowerShell 공급자 디자인](./designing-your-windows-powershell-provider.md)서 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 제공 하는 다른 여러 클래스에서 파생 되는 클래스 다른 공급자 기능입니다. 따라서 Windows PowerShell 컨테이너 공급자를 사용 하는 모든 해당 클래스에서 제공 하는 기능을 정의 해야 합니다.

특정 세션 초기화 정보를 추가 하 고 공급자가 사용 되는 리소스를 해제 하는 것에 대 한 기능을 구현 하려면 참조 [는 기본 Windows PowerShell 공급자를 만들어](./creating-a-basic-windows-powershell-provider.md)합니다. 그러나 여기에 설명 된 공급자 등 대부분의 공급자 기본적으로 Windows PowerShell에서 제공 하는이 기능을 사용할 수 있습니다.

데이터 저장소에 액세스 하려면 공급자의 메서드를 구현 해야 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 드라이브 공급자 만들기](./creating-a-windows-powershell-drive-provider.md)합니다.

가져오기, 설정 및 지우기 항목을 같은 데이터 저장소의 항목을 조작 하는 공급자에서 제공 하는 메서드를 구현 해야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 기본 클래스입니다. 이러한 메서드를 구현 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)합니다.

## <a name="retrieving-child-items"></a>자식 항목을 가져오는 중

자식 항목을 검색 하려면 Windows PowerShell 컨테이너 공급자를 재정의 해야 합니다는 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드 호출에서 지원 하기는 `Get-ChildItem` cmdlet. 이 메서드는 데이터 저장소에서 자식 항목을 검색 하 고 개체를 파이프라인으로 씁니다. 경우는 `recurse` cmdlet의 매개 변수를 지정, 메서드는 어떤 수준에 관계 없이 모든 자식을 검색 합니다. 경우는 `recurse` 매개 변수를 지정 하지 않으면 메서드는 단일 수준의 자식 검색 합니다.

여기의 구현은 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 이 공급자에 대 한 메서드. 경로 Access 데이터베이스를 나타내며 경로 데이터 테이블을 나타내는 경우 해당 테이블의 행에서 자식 항목을 검색 하는 경우이 메서드는 모든 데이터베이스 테이블의 하위 항목 검색 있는지 확인 합니다.

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L311-L362 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchilditems"></a>GetChildItems를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 메서드에 전달 된 경로 지정 된 요구 사항을 충족 해야 합니다. 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 이 메서드의 구현을 고려해 야 모든 형태의 액세스 항목을 사용자에 게 표시 하도록 할 수 있는 항목입니다. 예를 들어, 사용자에 대 한 쓰기 액세스는 FileSystem 공급자 (Windows PowerShell에서 제공)를 통해 읽기 액세스할 수는 없습니다 파일로 파일이 여전히 존재 하는지와 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 반환 `true`합니다. 구현 경우 자식을 열거할 수를 보려면 부모 항목을 검사 해야 합니다.

- 여러 항목을 작성 하는 경우는 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드는 다소 시간이 걸릴 수 있습니다. 사용 하 여 항목을 작성 하 여 공급자를 디자인할 수 있습니다 합니다 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 한 번에 하나의 메서드. 이 기술을 사용 하 여 항목 스트림에서 사용자에 게 표시 됩니다.

- 구현의 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 순환 링크와 같은 경우 무한 재귀를 방지 하는 데 일을 담당 합니다. 이러한 상태를 반영 하도록 적절 한 종료 예외가 throw 됩니다.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet"></a>Get-childitem Cmdlet에 연결 하는 동적 매개 변수

경우에 따라 합니다 `Get-ChildItem` 를 호출 하는 cmdlet [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Get-ChildItem` cmdlet.

이 Windows PowerShell 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters](Msh_samplestestcmdlets#testprovidergetchilditemsdynamicparameters)]  -->

## <a name="retrieving-child-item-names"></a>자식 항목 이름을 검색

자식 항목의 이름을 검색 하려면 Windows PowerShell 컨테이너 공급자를 재정의 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드를 지원 합니다 호출`Get-ChildItem`cmdlet 때 해당 `Name` 매개 변수를 지정 합니다. 이 메서드는 모든 컨테이너에 대해 지정 된 경로 또는 자식 항목 이름에 대 한 자식 항목의 이름을 검색 하는 경우는 `returnAllContainers` cmdlet의 매개 변수를 지정 합니다. 자식 이름을 리프 부분 경로입니다. 예를 들어, 자식 경로 c:\windows\system32\abc.dll 이름은 "abc.dll"입니다. 자식 디렉터리 c:\windows\system32 이름은 "system32"입니다.

여기의 구현은 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 이 공급자에 대 한 메서드. 지정된 된 경로 나타내는 경우 Access 데이터베이스 (드라이브) 및 행 번호를 경로 테이블을 나타내는 경우 메서드 테이블 이름을 검색 하는 알 수 있습니다.

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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L369-L411 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-getchildnames"></a>GetChildNames를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 메서드에 전달 된 경로 지정 된 요구 사항을 충족 해야 합니다. 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

  > [!NOTE]
  > 이 규칙에 예외가 발생할 때를 `returnAllContainers` cmdlet의 매개 변수를 지정 합니다. 이 경우 통해 메서드의 값과 일치 하지 않는 경우에 컨테이너의 자식 이름을 검색 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Filter*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Filter), [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include), 또는 [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 속성입니다.

- 기본적으로이 메서드는 재정의 하지 않는 한 일반적으로 사용자 로부터 숨겨진 개체의 이름을 검색 하지 않아야 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성을 지정 합니다. 지정된 된 경로 컨테이너를 나타내면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 필요 하지 않습니다.

- 구현의 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 순환 링크와 같은 경우 무한 재귀를 방지 하는 데 일을 담당 합니다. 이러한 상태를 반영 하도록 적절 한 종료 예외가 throw 됩니다.

## <a name="attaching-dynamic-parameters-to-the-get-childitem-cmdlet-name"></a>Get-childitem Cmdlet (이름)에 연결 하는 동적 매개 변수

경우에 따라 합니다 `Get-ChildItem` cmdlet (사용 하 여는 `Name` 매개 변수) 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Get-ChildItem` cmdlet.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters](Msh_samplestestcmdlets#testprovidergetchildnamesdynamicparameters)]  -->

## <a name="renaming-items"></a>항목 이름 바꾸기

항목의 이름을 바꾸려면 Windows PowerShell 컨테이너 공급자를 재정의 해야 합니다는 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드 호출에서 지원 하기는 `Rename-Item` cmdlet. 이 메서드는 제공 된 새 이름으로 지정된 된 경로에 있는 항목의 이름을 변경 합니다. 새 이름은 항상 부모 항목 (컨테이너)를 기준으로 해야 합니다.

이 공급자를 재정의 하지 않습니다 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드. 그러나 다음은 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitem](Msh_samplestestcmdlets#testproviderrenameitem)]  -->

#### <a name="things-to-remember-about-implementing-renameitem"></a>RenameItem를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 메서드에 전달 된 경로 지정 된 요구 사항을 충족 해야 합니다. 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드 이동 작업 한 없습니다만, 항목의 이름을 수정 합니다. 메서드를 구현 하는 경우 오류를 작성 해야 합니다 `newName` 매개 변수를 경로 구분 기호를 포함 합니다. 또는 해당 부모 위치를 변경 하려면 항목을 일으킬 수 있습니다.

- 기본적으로이 메서드는 재정의 이름을 바꾸지 않아야 개체 경우가 아니면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성을 지정 합니다. 지정된 된 경로 컨테이너를 나타내면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 필요 하지 않습니다.

- 구현 된 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 이 메서드는 변경 될 때 시스템 상태를 예를 들어, 파일 이름 바꾸기 작업의 실행을 확인 하려면 사용 됩니다. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 명령줄 설정이 나 기본 설정 변수에서 고려 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 표시할 내용을 결정 합니다.

  호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Containercmdletprovider.Renameitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItem) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 메서드. 이 메서드는 작업을 계속 해야 하는 경우에 추가 의견을 허용 하도록 사용자에 게 메시지를 확인 메시지를 보냅니다. 공급자를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 때문입니다.

## <a name="attaching-dynamic-parameters-to-the-rename-item-cmdlet"></a>Rename-item Cmdlet에 연결 하는 동적 매개 변수

경우에 따라는 `Rename-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Rename-Item` cmdlet.

이 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters](Msh_samplestestcmdlets#testproviderrenameitemdynamicparameters)]  -->

## <a name="creating-new-items"></a>새 항목 만들기

새 항목을 만들려면 컨테이너 공급자를 구현 해야 합니다는 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드 호출에서 지원 하기는 `New-Item` cmdlet. 이 메서드는 지정된 된 경로에 있는 데이터 항목을 만듭니다. `type` cmdlet의 매개 변수는 새 항목에 대 한 공급자가 정의한 형식을 포함 합니다. 예를 들어, 파일 시스템 공급자 사용을 `type` 매개 변수 값이 "file" 또는 "directory" 인 합니다. `newItemValue` cmdlet의 매개 변수는 새 항목에 대 한 공급자별 값을 지정 합니다.

여기의 구현은 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 이 공급자에 대 한 메서드.

```csharp
protected override void NewItem( string path, string type,
                                 object newItemValue )
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

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L939-L955 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-newitem"></a>NewItem를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드는 전달 된 문자열의 대/소문자 구분 비교를 수행 하는 `type` 매개 변수입니다. 또한 이상 모호한 일치를 허용 해야 합니다. 예를 들어 형식이 "file" 및 "directory"의 경우 첫 번째 문자만 필요 명확 하 게 합니다. 경우는 `type` 매개 변수 공급자를 만들 수 없는 유형을 나타냅니다는 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드는 메시지를 사용 하 여 ArgumentException 써야 합니다. 형식을 나타내는 공급자를 만들 수 있습니다.

- 에 대 한 합니다 `newItemValue` 매개 변수를 구현 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 방법은 최소한 문자열을 수락 하도록 권장 됩니다. 검색 된 개체의 형식에도 허용 해야 하는 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 동일한 경로 대 한 메서드. 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드는 사용할 수는 [System.Management.Automation.Languageprimitives.Convertto*](/dotnet/api/System.Management.Automation.LanguagePrimitives.ConvertTo) 형식을 변환 하는 방법 원하는 형식입니다.

- 구현 된 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) true를 반환 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 때문 메서드.

## <a name="attaching-dynamic-parameters-to-the-new-item-cmdlet"></a>New-item Cmdlet에 연결 하는 동적 매개 변수

경우에 따라는 `New-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 컨테이너 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) 메서드. 이 메서드는 지정 된 경로에 있는 항목에 대 한 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `New-Item` cmdlet.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는이 메서드의 기본 구현입니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewitemdynamicparameters](Msh_samplestestcmdlets#testprovidernewitemdynamicparameters)]  -->

## <a name="removing-items"></a>항목 제거

항목을 제거 하려면 Windows PowerShell 공급자를 재정의 해야 합니다는 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드 호출에서 지원 하기는 `Remove-Item` cmdlet. 이 메서드는 지정된 된 경로에 데이터 저장소에서 항목을 삭제합니다. 경우는 `recurse` 의 매개 변수를 `Remove-Item` cmdlet으로 설정 되어 `true`, 해당 수준에 관계 없이 모든 자식 항목을 제거 하는 메서드. 매개 변수 설정 된 경우 `false`, 지정된 된 경로에 하나의 항목만 제거 합니다.

이 공급자에서 항목 제거를 지원 하지 않습니다. 그러나 다음 코드는 기본 구현의 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem)합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitem](Msh_samplestestcmdlets#testproviderremoveitem)]  -->

#### <a name="things-to-remember-about-implementing-removeitem"></a>RemoveItem을 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Containercmdletprovider.Newitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 메서드에 전달 된 경로 지정 된 요구 사항을 충족 해야 합니다. 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 해야 개체가 제거 되지 않으면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 true로 합니다. 지정된 된 경로 컨테이너를 나타내면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 필요 하지 않습니다.

- 구현의 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 순환 링크와 같은 경우 무한 재귀를 방지 하는 데 일을 담당 합니다. 이러한 상태를 반영 하도록 적절 한 종료 예외가 throw 됩니다.

- 구현 된 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 반환 `true`는 [System.Management.Automation.Provider.Containercmdletprovider.Removeitem*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 때문 메서드.

## <a name="attaching-dynamic-parameters-to-the-remove-item-cmdlet"></a>Remove-item Cmdlet에 연결 하는 동적 매개 변수

경우에 따라는 `Remove-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 컨테이너 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) 이러한 매개 변수를 처리 하는 방법입니다. 이 메서드는 지정 된 경로에 있는 항목에 대 한 동적 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Remove-Item` cmdlet.

이 컨테이너 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 기본 구현의 [System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters)합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters](Msh_samplestestcmdlets#testproviderremoveitemdynamicparameters)]  -->

## <a name="querying-for-child-items"></a>자식 항목에 대 한 쿼리

자식 항목이 지정된 된 경로에 있는지 참조를 확인 하려면 Windows PowerShell 컨테이너 공급자를 재정의 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 메서드. 이 메서드는 반환 `true` 항목에 자식이 있으면 및 `false` 그렇지 않은 경우. Null 또는 빈 경로 대해를 메서드 하위 데이터 저장소에 있는 모든 항목을 고려 하 고 반환 `true`합니다.

여기에 대 한 재정의가 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 메서드. 메서드가 반환 ChunkPath 도우미 메서드에 의해 생성 되는 두 개 이상의 경로 부분이 있는지 `false`때문만 데이터베이스 컨테이너 및 테이블 컨테이너 정의 됩니다. 이 도우미 메서드에 대 한 자세한 내용은 참조 ChunkPath 메서드 부분은 [Windows PowerShell 항목 공급자 만들기](./creating-a-windows-powershell-item-provider.md)합니다.

```csharp
protected override bool HasChildItems( string path )
{
    return false;
} // HasChildItems
```

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L1094-L1097 "AccessDBProviderSample04.cs")]

#### <a name="things-to-remember-about-implementing-haschilditems"></a>HasChildItems를 구현 하는 방법에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems):

- 컨테이너 공급자 구현의 흥미로운 탑재 지점을 포함 하는 루트를 노출 하는 경우는 [System.Management.Automation.Provider.Containercmdletprovider.Haschilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.HasChildItems) 메서드 반환할지`true`를 null 또는 빈 문자열은 전달 되 면에서 경로 대 한 합니다.

## <a name="copying-items"></a>항목 복사

항목을 복사 하려면 컨테이너 공급자를 구현 해야 합니다는 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 메서드 호출에서 지원 하기는 `Copy-Item` cmdlet. 가 나타내는 위치에서 데이터 항목을 복사 하는이 메서드는 `path` 가 나타내는 위치 cmdlet의 매개 변수는 `copyPath` 매개 변수입니다. 경우는 `recurse` 모든 하위 컨테이너를 복사 하는 메서드, 매개 변수를 지정 합니다. 매개 변수를 지정 하지 않으면 경우 메서드는 단일 수준의 항목을 복사 합니다.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 기본 구현의 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem)합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitem](Msh_samplestestcmdlets#testprovidercopyitem)]  -->

#### <a name="things-to-remember-about-implementing-copyitem"></a>CopyItem 구현에 대 한 고려해 야 할 사항

다음과의 구현에 적용 될 수 있습니다 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem):

- 공급자 클래스를 정의 하는 경우 Windows PowerShell 컨테이너 공급자에서 ExpandWildcards, 필터, 포함 또는 제외의 공급자 기능을 선언할 수 있습니다는 [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) 열거형입니다. 이러한 경우의 구현에는 [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 메서드에 전달 된 경로 지정 된 요구 사항을 충족 해야 합니다. 기능입니다. 이 작업을 수행 하는 메서드 액세스 해야 적절 한 속성을 예를 들어, [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) 고 [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) 속성입니다.

- 기본적으로이 메서드는 재정의 복사 안 됩니다. 개체가 기존 개체에 대해 경우가 아니면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 예를 들어, 파일 시스템 공급자는 복사 하지 c:\temp\abc.txt 기존 c:\abc.txt 파일 경우가 아니면 합니다 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 `true`합니다. 경로에 지정 된 경우는 `copyPath` 매개 변수 존재 하 고 컨테이너를 나타냅니다는 [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) 속성이 필요 하지 않습니다. 이 경우 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 가리키는 항목을 복사 해야 합니다 `path` 매개 변수는 컨테이너를 가리키는 `copyPath` 자식으로 매개 변수.

- 구현의 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 순환 링크와 같은 경우 무한 재귀를 방지 하는 데 일을 담당 합니다. 이러한 상태를 반영 하도록 적절 한 종료 예외가 throw 됩니다.

- 구현 된 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 메서드를 호출 해야 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) 데이터 저장소로 변경 하기 전에 해당 반환 값을 확인 합니다. 호출한 후 [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) true를 반환 합니다 [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 메서드를 호출 해야 합니다 [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 때문 메서드. 이러한 메서드를 호출 하는 방법에 대 한 자세한 내용은 참조 하세요. [항목의 이름을 바꾸는](#renaming-items)합니다.

## <a name="attaching-dynamic-parameters-to-the-copy-item-cmdlet"></a>Copy-item Cmdlet에 연결 하는 동적 매개 변수

경우에 따라는 `Copy-Item` cmdlet에는 런타임에 동적으로 지정 된 추가 매개 변수가 필요 합니다. 이러한 동적 매개 변수를 제공 하려면 Windows PowerShell 컨테이너 공급자를 구현 해야 합니다 [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) 이러한 처리 하는 방법 매개 변수입니다. 이 메서드는 지정 된 경로에 있는 항목에 대 한 매개 변수를 검색 하 고 속성 및 cmdlet 클래스와 유사한 특성을 구문 분석 된 필드에 있는 개체를 반환 또는 [System.Management.Automation.Runtimedefinedparameterdictionary ](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) 개체입니다. Windows PowerShell 런타임에 반환 되는 개체를 사용 하 여 매개 변수를 추가 하 여 `Copy-Item` cmdlet.

이 공급자는이 메서드를 구현 하지 않습니다. 그러나 다음 코드는 기본 구현의 [System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters)합니다.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters](Msh_samplestestcmdlets#testprovidercopyitemdynamicparameters)]  -->

## <a name="code-sample"></a>코드 예제

전체 샘플 코드를 보려면 [AccessDbProviderSample04 코드 샘플](./accessdbprovidersample04-code-sample.md)합니다.

## <a name="building-the-windows-powershell-provider"></a>Windows PowerShell 공급자 작성

참조 [Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.

## <a name="testing-the-windows-powershell-provider"></a>Windows PowerShell 공급자 테스트

Windows PowerShell을 사용 하 여 Windows PowerShell 공급자가 등록 하는 경우 명령줄에서 지원 되는 cmdlet을 실행 하 여 테스트할 수 있습니다. 다음 예제 출력에서는 가상의 Access 데이터베이스는 주의 합니다.

1. 실행 된 `Get-ChildItem` Access 데이터베이스의 Customers 테이블에서 자식 항목의 목록을 검색 하는 cmdlet입니다.

   ```powershell
   Get-ChildItem mydb:customers
   ```

   다음과 같은 출력이 표시 됩니다.

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

2. 실행 된 `Get-ChildItem` 테이블의 데이터를 검색 하기 위한 다시 cmdlet.

   ```powershell
   (Get-ChildItem mydb:customers).data
   ```

   다음과 같은 출력이 표시 됩니다.

   ```output
   TABLE_CAT   : c:\PS\northwind
   TABLE_SCHEM :
   TABLE_NAME  : Customers
   TABLE_TYPE  : TABLE
   REMARKS     :
   ```

3. 사용 하 여 이제는 `Get-Item` 데이터 테이블의 행 0에 있는 항목을 검색 하기 위한 cmdlet입니다.

   ```powershell
   Get-Item mydb:\customers\0
   ```

   다음과 같은 출력이 표시 됩니다.

   ```output
   PSPath        : AccessDB::customers\0
   PSDrive       : mydb
   PSProvider    : System.Management.Automation.ProviderInfo
   PSIsContainer : False
   Data          : System.Data.DataRow
   RowNumber     : 0
   ```

4. 다시 사용할 `Get-Item` 행 0에에서 있는 항목에 대 한 데이터를 검색 합니다.

   ```powershell
   (Get-Item mydb:\customers\0).data
   ```

   다음과 같은 출력이 표시 됩니다.

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

5. 사용 하 여 이제는 `New-Item` 기존 테이블에 행을 추가 하는 cmdlet입니다. `Path` 매개 변수 행의 전체 경로 지정 하 고 행 번호를 나타내야 하는 기존 테이블의 행 수보다 큽니다. `Type` "행" 추가할 항목의 해당 형식을 지정 하려면 매개 변수를 나타냅니다. 마지막으로 `Value` 매개 변수 행의 열 값의 쉼표로 구분 된 목록을 지정 합니다.

   ```powershell
   New-Item -Path mydb:\Customers\3 -ItemType "row" -Value "3,CustomerFirstName,CustomerLastName,CustomerEmailAddress,CustomerTitle,CustomerCompany,CustomerPhone, CustomerAddress,CustomerCity,CustomerState,CustomerZip,CustomerCountry"
   ```

6. 다음과 같이 새 항목 작업의 정확성을 확인 합니다.

   ```none
   PS mydb:\> cd Customers
   PS mydb:\Customers> (Get-Item 3).data
   ```

   다음과 같은 출력이 표시 됩니다.

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

[Windows PowerShell 공급자를 디자인합니다.](./designing-your-windows-powershell-provider.md)

[Windows PowerShell 항목 공급자 구현](./creating-a-windows-powershell-item-provider.md)

[Windows PowerShell 탐색 공급자 구현](./creating-a-windows-powershell-navigation-provider.md)

[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell 프로그래머 가이드](./windows-powershell-programmer-s-guide.md)