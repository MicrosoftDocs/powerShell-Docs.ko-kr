---
title: 항목 공급자 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080818"
---
# <a name="writing-an-item-provider"></a>항목 공급자 작성

이 항목에 액세스 하 고 데이터 저장소의 항목을 조작 하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법을 설명 합니다. 항목에 액세스할 수 있어야 하는 공급자에서 파생 되어야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.

이 항목의 예제에서 공급자 데이터 저장소로 Access 데이터베이스를 사용합니다. 도우미 메서드 및 클래스는 데이터베이스 상호 작용 하는 데 사용 되는 몇 가지 있습니다. 도우미 메서드를 포함 하는 전체 샘플을 참조 하세요. [AccessDBProviderSample03](./accessdbprovidersample03.md)

Windows PowerShell 공급자에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다.

## <a name="implementing-item-methods"></a>항목 메서드를 구현합니다.

합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에 액세스 하는 데이터 저장소에서 항목을 조작할 수 있는 여러 메서드를 노출 합니다. 이러한 메서드의 전체 목록은 참조 하세요 [ItemCmdletProvider 메서드](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx)합니다. 이 예제에서는 이러한 메서드 중 4 개를 구현 합니다. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 지정된 된 경로에 항목을 가져옵니다. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 지정된 된 항목의 값을 설정 합니다. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 항목이 지정된 된 경로에 있는지 여부를 확인 합니다. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 데이터 저장소의 위치에 매핑되는 경우 참조에 대 한 경로 확인 합니다.

> [!NOTE]
> 이 항목의 정보를 빌드 [Windows PowerShell 공급자 퀵 스타트](./windows-powershell-provider-quickstart.md)합니다. 이 항목에서는 기본 공급자 프로젝트를 설정 하는 방법 다루지 않습니다 또는 메서드를 구현 하는 방법에서 상속 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 만들고 드라이브를 제거 하는 클래스입니다.

### <a name="declaring-the-provider-class"></a>공급자 클래스를 선언합니다.

파생 하는 공급자를 선언 합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스를 사용 하 여 데코 레이트 된 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>GetItem 구현

합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 사용자를 호출할 때 PowerShell 엔진에 의해 호출 됩니다 합니다 [Microsoft.PowerShell.Commands.Get 항목](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet에 공급자입니다. 메서드는 지정된 된 경로에 있는 항목을 반환합니다. Access 데이터베이스 예제에서는 메서드 항목에 드라이브를 자체 데이터베이스 또는 데이터베이스에서 행의 테이블 인지 여부를 확인 합니다. 메서드를 호출 하 여 PowerShell 엔진에 항목을 전송 합니다 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드.

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>SetItem 구현

합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드는 PowerShell 엔진을 호출 하 여 사용자를 호출할 때 합니다 [Microsoft.PowerShell.Commands.Set 항목](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet . 지정된 된 경로에 있는 항목의 값을 설정합니다.

해당 항목 이므로 행에는 메서드가 throw 하는 경우에 있는 항목의 값을 설정 하려면 편이 Access 데이터베이스 예제에서 [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) 항목이 없는 경우 행입니다.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>ItemExists 구현

합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 메서드는 PowerShell 엔진에서 호출 하는 사용자는 [Microsoft.PowerShell.Commands.Test 경로](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet. 메서드는 지정된 된 경로에 항목이 있는지 여부를 결정 합니다. 항목이 없으면 메서드가 전달 PowerShell 엔진으로 다시 호출 하 여 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)합니다.

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>IsValidPath 구현

합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드 구문상 유효한 현재 공급자에 대 한 지정된 된 경로 인지 확인 합니다. 항목 경로에 있는지 여부를 확인 하지 않습니다.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>다음 단계

일반적인 실제 공급자는 하나의 경로에서 드라이브 내에서 다른 항목을 이동 및 기타 항목을 포함 하는 항목을 지원할 수 있습니다. 컨테이너를 지 원하는 공급자의 예제를 보려면 [컨테이너 공급자 작성](./writing-a-container-provider.md)합니다. 이동 된 항목을 지 원하는 공급자의 예제를 참조 하세요 [탐색 공급자 작성](./writing-a-navigation-provider.md)합니다.

## <a name="see-also"></a>참고 항목

[컨테이너 공급자 작성](./writing-a-container-provider.md)

[탐색 공급자 작성](./writing-a-navigation-provider.md)

[Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)