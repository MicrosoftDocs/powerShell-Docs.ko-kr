---
ms.date: 09/13/2016
ms.topic: reference
title: 항목 공급자 작성
description: 항목 공급자 작성
ms.openlocfilehash: f70c6ee50277988c4e3b7c255dc4548bc30319dd
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355207"
---
# <a name="writing-an-item-provider"></a>항목 공급자 작성

이 항목에서는 데이터 저장소의 항목에 액세스 하 고 조작 하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법에 대해 설명 합니다. 항목에 액세스할 수 있으려면 공급자가 [system.web. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 되어야 합니다.

이 항목의 예제 공급자는 Access 데이터베이스를 데이터 저장소로 사용 합니다. 데이터베이스와 상호 작용 하는 데 사용 되는 여러 가지 도우미 메서드 및 클래스가 있습니다. 도우미 메서드를 포함 하는 전체 샘플은 [AccessDBProviderSample03](./accessdbprovidersample03.md) 를 참조 하세요.

Windows PowerShell 공급자에 대 한 자세한 내용은 [Windows Powershell 공급자 개요](./windows-powershell-provider-overview.md)를 참조 하세요.

## <a name="implementing-item-methods"></a>항목 메서드 구현

[System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 는 데이터 저장소의 항목에 액세스 하 고 조작 하는 데 사용할 수 있는 여러 메서드를 노출 합니다.
이러한 메서드의 전체 목록은 [Itemcmdletprovider 메서드](/dotnet/api/system.management.automation.provider.itemcmdletprovider#methods)를 참조 하세요.
이 예제에서는 네 가지 메서드를 구현 합니다.
[Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 지정 된 경로에 있는 항목을 가져오거나 지정 합니다.
[Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 지정 된 항목의 값을 설정 하는입니다.
[System.object. Itemexists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 지정 된 경로에 항목이 있는지 여부를 확인 합니다.
[System.object. isvalidpath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 는 경로를 확인 하 여 데이터 저장소의 특정 위치에 매핑되는지 여부를 확인 합니다.

> [!NOTE]
> 이 항목은 [Windows PowerShell 공급자 빠른](./windows-powershell-provider-quickstart.md)시작의 정보를 기반으로 합니다. 이 항목에서는 공급자 프로젝트를 설정 하는 방법에 대 한 기본 사항을 다루지 않으며, 드라이브를 만들고 제거 하는 [system.web](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .. c a c.

### <a name="declaring-the-provider-class"></a>공급자 클래스 선언

[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)를 사용 하 여 파생 시킬 [공급자를](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 선언 하 고 해당 클래스를 사용 하 여 데코 레이트 합니다.

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>GetItem 구현

사용자가 공급자의 [GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet을 호출 하면 [Getitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 가 PowerShell 엔진에 의해 호출 됩니다 (영문으로 제공 됨). 메서드는 지정 된 경로에 있는 항목을 반환 합니다. Access 데이터베이스 예제에서 메서드는 항목이 드라이브 자체 인지, 데이터베이스의 테이블 또는 데이터베이스의 행 인지를 확인 합니다. 메서드는 System.object를 호출 하 여 PowerShell 엔진에 항목을 전송 합니다. [Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드.

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

[Setitem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드는 사용자가 [SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) Cmdlet을 호출할 때 powershell 엔진 호출에 의해 호출 됩니다 (영문) (영문). 지정 된 경로에 있는 항목의 값을 설정 합니다.

Access 데이터베이스 예제에서는 항목이 행 인 경우에만 항목의 값을 설정 하는 것이 좋습니다. 따라서 항목이 행이 아닐 때 메서드는 [NotSupportedException](/dotnet/api/system.notsupportedexception) 을 throw 합니다.

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

사용자가 Microsoft powershell 엔진에 의해 호출 되는 경우에는 사용자가 [Microsoft powershell](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) 엔진에 의해 호출 [됩니다.-](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) . 메서드는 지정 된 경로에 항목이 있는지 여부를 확인 합니다. 항목이 존재 하는 경우 메서드는 System.object를 호출 하 여 PowerShell 엔진에 다시 전달 합니다. [Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

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

### <a name="implementing-isvalidpath"></a>Is유효한 경로 구현

[System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 는 지정 된 경로가 현재 공급자에 대해 구문적으로 유효한 지 여부를 확인 하는 데 사용할 수 있습니다. 항목이 경로에 있는지 여부는 확인 하지 않습니다.

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

일반적인 실제 공급자는 다른 항목을 포함 하는 항목을 지원 하 고 드라이브 내에서 다른 경로로 항목을 이동할 수 있습니다. 컨테이너를 지 원하는 공급자의 예는 [컨테이너 공급자 작성](./writing-a-container-provider.md)을 참조 하세요. 항목 이동을 지 원하는 공급자의 예는 [탐색 공급자 작성](./writing-a-navigation-provider.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[컨테이너 공급자 작성](./writing-a-container-provider.md)

[탐색 공급자 작성](./writing-a-navigation-provider.md)

[Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)
