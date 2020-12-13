---
ms.date: 09/13/2016
ms.topic: reference
title: 컨테이너 공급자 작성
description: 컨테이너 공급자 작성
ms.openlocfilehash: 17ec3e11258ee77a8e569df1af3a0e9bcd9798b6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93354935"
---
# <a name="writing-a-container-provider"></a><span data-ttu-id="b32e2-103">컨테이너 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="b32e2-103">Writing a container provider</span></span>

<span data-ttu-id="b32e2-104">이 항목에서는 파일 시스템 공급자의 폴더와 같은 다른 항목을 포함 하는 항목을 지 원하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-104">This topic describes how to implement the methods of a Windows PowerShell provider that support items that contain other items, such as folders in the file system provider.</span></span> <span data-ttu-id="b32e2-105">컨테이너를 지원할 수 있으려면 공급자가 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-105">To be able to support containers, a provider must derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span>

<span data-ttu-id="b32e2-106">이 항목의 예제 공급자는 Access 데이터베이스를 데이터 저장소로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="b32e2-107">데이터베이스와 상호 작용 하는 데 사용 되는 여러 가지 도우미 메서드 및 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="b32e2-108">도우미 메서드를 포함 하는 전체 샘플은 [AccessDBProviderSample04](./accessdbprovidersample04.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b32e2-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>

<span data-ttu-id="b32e2-109">Windows PowerShell 공급자에 대 한 자세한 내용은 [Windows Powershell 공급자 개요](./windows-powershell-provider-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b32e2-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-container-methods"></a><span data-ttu-id="b32e2-110">컨테이너 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="b32e2-110">Implementing container methods</span></span>

<span data-ttu-id="b32e2-111">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스는 컨테이너를 지원 하 고 항목을 만들고, 복사 하 고, 제거 하는 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-111">The [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class implements methods that support containers, and create, copy, and remove items.</span></span> <span data-ttu-id="b32e2-112">이러한 메서드의 전체 목록을 보려면 [ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider#methods)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="b32e2-112">For a complete list of these methods, see [System.Management.Automation.Provider.ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="b32e2-113">이 항목은 [Windows PowerShell 공급자 빠른](./windows-powershell-provider-quickstart.md)시작의 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-113">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="b32e2-114">이 항목에서는 공급자 프로젝트를 설정 하는 방법에 대 한 기본 사항을 다루지 않으며, 드라이브를 만들고 제거 하는 [system.web](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .. c a c.</span><span class="sxs-lookup"><span data-stu-id="b32e2-114">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="b32e2-115">또한이 항목에서는 [system.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 에서 노출 하는 메서드를 구현 하는 방법에 대해서는 설명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-115">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="b32e2-116">항목 cmdlet을 구현 하는 방법을 보여 주는 예제는 [항목 공급자 작성](./writing-an-item-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b32e2-116">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="b32e2-117">공급자 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="b32e2-117">Declaring the provider class</span></span>

<span data-ttu-id="b32e2-118">[Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스에서 파생 되도록 공급자를 선언 하 고 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)를 사용 하 여 데코 레이트 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-118">Declare the provider to derive from the [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
   {

   }
```

### <a name="implementing-getchilditems"></a><span data-ttu-id="b32e2-119">GetChildItems 구현</span><span class="sxs-lookup"><span data-stu-id="b32e2-119">Implementing GetChildItems</span></span>

<span data-ttu-id="b32e2-120">PowerShell 엔진은 사용자가 Containercmdletprovider cmdlet을 호출 하는 경우 [Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드를 호출 하 [고,](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand)</span><span class="sxs-lookup"><span data-stu-id="b32e2-120">The PowerShell engine calls the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method when a user calls the [Microsoft.PowerShell.Commands.GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) cmdlet.</span></span> <span data-ttu-id="b32e2-121">이 메서드는 지정 된 경로에 있는 항목의 자식인 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-121">This method gets the items that are the children of the item at the specified path.</span></span>

<span data-ttu-id="b32e2-122">Access 데이터베이스 예제에서 [Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드의 동작은 지정 된 항목의 형식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-122">In the Access database example, the behavior of the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method depends on the type of the specified item.</span></span> <span data-ttu-id="b32e2-123">항목이 드라이브인 경우 자식은 테이블이 고 메서드는 데이터베이스에서 테이블 집합을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-123">If the item is the drive, then the children are tables, and the method returns the set of tables from the database.</span></span> <span data-ttu-id="b32e2-124">지정 된 항목이 테이블인 경우 자식은 해당 테이블의 행입니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-124">If the specified item is a table, then the children are the rows of that table.</span></span> <span data-ttu-id="b32e2-125">항목이 행 인 경우에는 자식이 없고 메서드는 해당 행만 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-125">If the item is a row, then it has no children, and the method returns that row only.</span></span> <span data-ttu-id="b32e2-126">모든 자식 항목은 System.object에서 PowerShell 엔진으로 다시 전송 됩니다. [Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-126">All child items are sent back to the PowerShell engine by the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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
       }
```

### <a name="implementing-getchildnames"></a><span data-ttu-id="b32e2-127">GetChildNames 구현</span><span class="sxs-lookup"><span data-stu-id="b32e2-127">Implementing GetChildNames</span></span>

<span data-ttu-id="b32e2-128">[Containercmdletprovider. Getchildnames \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) 메서드는 항목 자체가 아니라 항목의 name 속성만 반환 한다는 점을 제외 하 고 [Containercmdletprovider. Getchilditems \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) 메서드와 유사 하 게 제공 됩니다 (예를 들어).</span><span class="sxs-lookup"><span data-stu-id="b32e2-128">The [System.Management.Automation.Provider.Containercmdletprovider.Getchildnames\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) method is similar to the [System.Management.Automation.Provider.Containercmdletprovider.Getchilditems\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) method, except that it returns only the name property of the items, and not the items themselves.</span></span>

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
       }
```

### <a name="implementing-newitem"></a><span data-ttu-id="b32e2-129">NewItem 구현</span><span class="sxs-lookup"><span data-stu-id="b32e2-129">Implementing NewItem</span></span>

<span data-ttu-id="b32e2-130">[Containercmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드는 지정 된 경로에 지정 된 형식의 새 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-130">The [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method creates a new item of the specified type at the specified path.</span></span> <span data-ttu-id="b32e2-131">PowerShell 엔진은 사용자가 [NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) cmdlet을 호출할 때이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-131">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) cmdlet.</span></span>

<span data-ttu-id="b32e2-132">이 예제에서 메서드는 논리를 구현 하 여 경로와 형식이 일치 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-132">In this example, the method implements logic to determine that the path and type match.</span></span> <span data-ttu-id="b32e2-133">즉, 테이블은 드라이브 (데이터베이스) 바로 아래에서 만들 수 있으며 한 행만 테이블에 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-133">That is, only a table can be created directly under the drive (the database), and only a row can be created under a table.</span></span> <span data-ttu-id="b32e2-134">지정 된 경로와 항목 형식이 이러한 방식으로 일치 하지 않는 경우 메서드는 예외를 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-134">If the specified path and item type don't match in this way, the method throws an exception.</span></span>

```csharp
protected override void NewItem(string path, string type,
                                   object newItemValue)
       {
           string tableName;
           int rowNumber;

           PathType pt = GetNamesFromPath(path, out tableName, out rowNumber);

           if (pt == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           // Check if type is either "table" or "row", if not throw an
           // exception
           if (!String.Equals(type, "table", StringComparison.OrdinalIgnoreCase)
               && !String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
           {
               WriteError(new ErrorRecord
                                 (new ArgumentException("Type must be either a table or row"),
                                     "CannotCreateSpecifiedObject",
                                        ErrorCategory.InvalidArgument,
                                             path
                                  )
                         );

               throw new ArgumentException("This provider can only create items of type \"table\" or \"row\"");
           }

           // Path type is the type of path of the container. So if a drive
           // is specified, then a table can be created under it and if a table
           // is specified, then a row can be created under it. For the sake of
           // completeness, if a row is specified, then if the row specified by
           // the path does not exist, a new row is created. However, the row
           // number may not match as the row numbers only get incremented based
           // on the number of rows

           if (PathIsDrive(path))
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   // Execute command using ODBC connection to create a table
                   try
                   {
                       // create the table using an sql statement
                       string newTableName = newItemValue.ToString();

                       if (!TableNameIsValid(newTableName))
                       {
                           return;
                       }
                       string sql = "create table " + newTableName
                                            + " (ID INT)";

                       // Create the table using the Odbc connection from the
                       // drive.
                       AccessDBPSDriveInfo di = this.PSDriveInfo as AccessDBPSDriveInfo;

                       if (di == null)
                       {
                           return;
                       }
                       OdbcConnection connection = di.Connection;

                       if (ShouldProcess(newTableName, "create"))
                       {
                           OdbcCommand cmd = new OdbcCommand(sql, connection);
                           cmd.ExecuteScalar();
                       }
                   }
                   catch (Exception ex)
                   {
                       WriteError(new ErrorRecord(ex, "CannotCreateSpecifiedTable",
                                 ErrorCategory.InvalidOperation, path)
                                 );
                   }
               } // if (String...
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   throw new
                       ArgumentException("A row cannot be created under a database, specify a path that represents a Table");
               }
           }// if (PathIsDrive...
           else
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   if (rowNumber < 0)
                   {
                       throw new
                           ArgumentException("A table cannot be created within another table, specify a path that represents a database");
                   }
                   else
                   {
                       throw new
                           ArgumentException("A table cannot be created inside a row, specify a path that represents a database");
                   }
               } //if (String.Equals....
               // if path specified is a row, create a new row
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   // The user is required to specify the values to be inserted
                   // into the table in a single string separated by commas
                   string value = newItemValue as string;

                   if (String.IsNullOrEmpty(value))
                   {
                       throw new
                           ArgumentException("Value argument must have comma separated values of each column in a row");
                   }
                   string[] rowValues = value.Split(',');

                   OdbcDataAdapter da = GetAdapterForTable(tableName);

                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   if (rowValues.Length != table.Columns.Count)
                   {
                       string message =
                            String.Format(CultureInfo.CurrentCulture,
                                            "The table has {0} columns and the value specified must have so many comma separated values",
                                                table.Columns.Count);

                       throw new ArgumentException(message);
                   }

                   if (!Force && (rowNumber >=0 && rowNumber < table.Rows.Count))
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                                        "The row {0} already exists. To create a new row specify row number as {1}, or specify path to a table, or use the -Force parameter",
                                                            rowNumber, table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   if (rowNumber > table.Rows.Count)
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                            "To create a new row specify row number as {0}, or specify path to a table",
                                                table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   // Create a new row and update the row with the input
                   // provided by the user
                   DataRow row = table.NewRow();
                   for (int i = 0; i < rowValues.Length; i++)
                   {
                       row[i] = rowValues[i];
                   }
                   table.Rows.Add(row);

                   if (ShouldProcess(tableName, "update rows"))
                   {
                       // Update the table from memory back to the data source
                       da.Update(ds, tableName);
                   }

               }// else if (String...
           }// else ...

       }
```

### <a name="implementing-copyitem"></a><span data-ttu-id="b32e2-135">CopyItem 구현</span><span class="sxs-lookup"><span data-stu-id="b32e2-135">Implementing CopyItem</span></span>

<span data-ttu-id="b32e2-136">[ContainerCmdletProvider 항목](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) 은 지정 된 항목을 지정 된 경로에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-136">The [System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copies the specified item to the specified path.</span></span> <span data-ttu-id="b32e2-137">PowerShell 엔진은 사용자가 [CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) cmdlet을 호출할 때이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-137">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) cmdlet.</span></span> <span data-ttu-id="b32e2-138">항목 자체 뿐만 아니라 모든 항목 자식을 복사 하 여이 메서드를 재귀적으로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-138">This method can also be recursive, copying all of the items children in addition to the item itself.</span></span>

<span data-ttu-id="b32e2-139">[Containercmdletprovider. Newitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) 메서드와 마찬가지로이 메서드는 지정 된 항목이 복사 되는 경로에 대 한 올바른 형식 인지 확인 하는 논리를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-139">Similarly to the [System.Management.Automation.Provider.Containercmdletprovider.Newitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) method, this method performs logic to make sure that the specified item is of the correct type for the path to which it is being copied.</span></span> <span data-ttu-id="b32e2-140">예를 들어 대상 경로가 테이블인 경우 복사할 항목은 행 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-140">For example, if the destination path is a table, the item to be copied must be a row.</span></span>

```csharp
protected override void CopyItem(string path, string copyPath, bool recurse)
       {
           string tableName, copyTableName;
           int rowNumber, copyRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);
           PathType copyType = GetNamesFromPath(copyPath, out copyTableName, out copyRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(copyPath);
           }

           // Get the table and the table to copy to
           OdbcDataAdapter da = GetAdapterForTable(tableName);
           if (da == null)
           {
               return;
           }

           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           OdbcDataAdapter cda = GetAdapterForTable(copyTableName);
           if (cda == null)
           {
               return;
           }

           DataSet cds = GetDataSetForTable(cda, copyTableName);
           DataTable copyTable = GetDataTable(cds, copyTableName);

           // if source represents a table
           if (type == PathType.Table)
           {
               // if copyPath does not represent a table
               if (copyType != PathType.Table)
               {
                   ArgumentException e = new ArgumentException("Table can only be copied on to another table location");

                   WriteError(new ErrorRecord(e, "PathNotValid",
                       ErrorCategory.InvalidArgument, copyPath));

                   throw e;
               }

               // if table already exists then force parameter should be set
               // to force a copy
               if (!Force && GetTable(copyTableName) != null)
               {
                   throw new ArgumentException("Specified path already exists");
               }

               for (int i = 0; i < table.Rows.Count; i++)
               {
                   DataRow row = table.Rows[i];
                   DataRow copyRow = copyTable.NewRow();

                   copyRow.ItemArray = row.ItemArray;
                   copyTable.Rows.Add(copyRow);
               }
           } // if (type == ...
           // if source represents a row
           else
           {
               if (copyType == PathType.Row)
               {
                   if (!Force && (copyRowNumber < copyTable.Rows.Count))
                   {
                       throw new ArgumentException("Specified path already exists.");
                   }

                   DataRow row = table.Rows[rowNumber];
                   DataRow copyRow = null;

                   if (copyRowNumber < copyTable.Rows.Count)
                   {
                       // copy to an existing row
                       copyRow = copyTable.Rows[copyRowNumber];
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                   }
                   else if (copyRowNumber == copyTable.Rows.Count)
                   {
                       // copy to the next row in the table that will
                       // be created
                       copyRow = copyTable.NewRow();
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                       copyTable.Rows.Add(copyRow);
                   }
                   else
                   {
                       // attempting to copy to a nonexistent row or a row
                       // that cannot be created now - throw an exception
                       string message = String.Format(CultureInfo.CurrentCulture,
                                             "The item cannot be specified to the copied row. Specify row number as {0}, or specify a path to the table.",
                                                    table.Rows.Count);

                       throw new ArgumentException(message);
                   }
               }
               else
               {
                   // destination path specified represents a table,
                   // create a new row and copy the item
                   DataRow copyRow = copyTable.NewRow();
                   copyRow.ItemArray = table.Rows[rowNumber].ItemArray;
                   copyRow[0] = GetNextID(copyTable);
                   copyTable.Rows.Add(copyRow);
               }
           }

           if (ShouldProcess(copyTableName, "CopyItems"))
           {
               cda.Update(cds, copyTableName);
           }

       } //CopyItem
```

### <a name="implementing-removeitem"></a><span data-ttu-id="b32e2-141">RemoveItem 구현</span><span class="sxs-lookup"><span data-stu-id="b32e2-141">Implementing RemoveItem</span></span>

<span data-ttu-id="b32e2-142">[Containercmdletprovider. Removeitem \*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) 메서드는 지정 된 경로에서 항목을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-142">The [System.Management.Automation.Provider.Containercmdletprovider.Removeitem\*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) method removes the item at the specified path.</span></span> <span data-ttu-id="b32e2-143">PowerShell 엔진은 사용자가 [RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) cmdlet을 호출할 때이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-143">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) cmdlet.</span></span>

```csharp
protected override void RemoveItem(string path, bool recurse)
       {
           string tableName;
           int rowNumber = 0;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               // if recurse flag has been specified, delete all the rows as well
               if (recurse)
               {
                   OdbcDataAdapter da = GetAdapterForTable(tableName);
                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   for (int i = 0; i < table.Rows.Count; i++)
                   {
                       table.Rows[i].Delete();
                   }

                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       da.Update(ds, tableName);
                       RemoveTable(tableName);
                   }
               }//if (recurse...
               else
               {
                   // Remove the table
                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       RemoveTable(tableName);
                   }
               }
           }
           else if (type == PathType.Row)
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               table.Rows[rowNumber].Delete();

               if (ShouldProcess(path, "RemoveItem"))
               {
                   da.Update(ds, tableName);
               }
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

## <a name="next-steps"></a><span data-ttu-id="b32e2-144">다음 단계</span><span class="sxs-lookup"><span data-stu-id="b32e2-144">Next steps</span></span>

<span data-ttu-id="b32e2-145">일반적인 실제 공급자는 드라이브 내에서 한 경로에서 다른 경로로 항목을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b32e2-145">A typical real-world provider is capable of moving items from one path to another within the drive.</span></span>
<span data-ttu-id="b32e2-146">항목 이동을 지 원하는 공급자의 예는 [탐색 공급자 작성](./writing-a-navigation-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b32e2-146">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b32e2-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b32e2-147">See Also</span></span>

[<span data-ttu-id="b32e2-148">탐색 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="b32e2-148">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="b32e2-149">Windows PowerShell 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="b32e2-149">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
