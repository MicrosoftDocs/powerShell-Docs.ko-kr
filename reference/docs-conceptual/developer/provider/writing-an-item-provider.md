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
# <a name="writing-an-item-provider"></a><span data-ttu-id="6e676-103">항목 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="6e676-103">Writing an item provider</span></span>

<span data-ttu-id="6e676-104">이 항목에서는 데이터 저장소의 항목에 액세스 하 고 조작 하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-104">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="6e676-105">항목에 액세스할 수 있으려면 공급자가 [system.web. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에서 파생 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-105">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="6e676-106">이 항목의 예제 공급자는 Access 데이터베이스를 데이터 저장소로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-106">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="6e676-107">데이터베이스와 상호 작용 하는 데 사용 되는 여러 가지 도우미 메서드 및 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-107">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="6e676-108">도우미 메서드를 포함 하는 전체 샘플은 [AccessDBProviderSample03](./accessdbprovidersample03.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e676-108">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="6e676-109">Windows PowerShell 공급자에 대 한 자세한 내용은 [Windows Powershell 공급자 개요](./windows-powershell-provider-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e676-109">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="6e676-110">항목 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="6e676-110">Implementing item methods</span></span>

<span data-ttu-id="6e676-111">[System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 는 데이터 저장소의 항목에 액세스 하 고 조작 하는 데 사용할 수 있는 여러 메서드를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-111">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span>
<span data-ttu-id="6e676-112">이러한 메서드의 전체 목록은 [Itemcmdletprovider 메서드](/dotnet/api/system.management.automation.provider.itemcmdletprovider#methods)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e676-112">For a complete list of these methods, see [ItemCmdletProvider Methods](/dotnet/api/system.management.automation.provider.itemcmdletprovider#methods).</span></span>
<span data-ttu-id="6e676-113">이 예제에서는 네 가지 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-113">In this example, we will implement four of these methods.</span></span>
<span data-ttu-id="6e676-114">[Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 지정 된 경로에 있는 항목을 가져오거나 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-114">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span>
<span data-ttu-id="6e676-115">[Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 지정 된 항목의 값을 설정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-115">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span>
<span data-ttu-id="6e676-116">[System.object. Itemexists \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 지정 된 경로에 항목이 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-116">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span>
<span data-ttu-id="6e676-117">[System.object. isvalidpath \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 는 경로를 확인 하 여 데이터 저장소의 특정 위치에 매핑되는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-117">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="6e676-118">이 항목은 [Windows PowerShell 공급자 빠른](./windows-powershell-provider-quickstart.md)시작의 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-118">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="6e676-119">이 항목에서는 공급자 프로젝트를 설정 하는 방법에 대 한 기본 사항을 다루지 않으며, 드라이브를 만들고 제거 하는 [system.web](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .. c a c.</span><span class="sxs-lookup"><span data-stu-id="6e676-119">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="6e676-120">공급자 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="6e676-120">Declaring the provider class</span></span>

<span data-ttu-id="6e676-121">[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)를 사용 하 여 파생 시킬 [공급자를](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 선언 하 고 해당 클래스를 사용 하 여 데코 레이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-121">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="6e676-122">GetItem 구현</span><span class="sxs-lookup"><span data-stu-id="6e676-122">Implementing GetItem</span></span>

<span data-ttu-id="6e676-123">사용자가 공급자의 [GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet을 호출 하면 [Getitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 가 PowerShell 엔진에 의해 호출 됩니다 (영문으로 제공 됨).</span><span class="sxs-lookup"><span data-stu-id="6e676-123">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet on your provider.</span></span> <span data-ttu-id="6e676-124">메서드는 지정 된 경로에 있는 항목을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-124">The method returns the item at the specified path.</span></span> <span data-ttu-id="6e676-125">Access 데이터베이스 예제에서 메서드는 항목이 드라이브 자체 인지, 데이터베이스의 테이블 또는 데이터베이스의 행 인지를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-125">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="6e676-126">메서드는 System.object를 호출 하 여 PowerShell 엔진에 항목을 전송 합니다. [Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드.</span><span class="sxs-lookup"><span data-stu-id="6e676-126">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="6e676-127">SetItem 구현</span><span class="sxs-lookup"><span data-stu-id="6e676-127">Implementing SetItem</span></span>

<span data-ttu-id="6e676-128">[Setitem \*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드는 사용자가 [SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) Cmdlet을 호출할 때 powershell 엔진 호출에 의해 호출 됩니다 (영문) (영문).</span><span class="sxs-lookup"><span data-stu-id="6e676-128">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet.</span></span> <span data-ttu-id="6e676-129">지정 된 경로에 있는 항목의 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-129">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="6e676-130">Access 데이터베이스 예제에서는 항목이 행 인 경우에만 항목의 값을 설정 하는 것이 좋습니다. 따라서 항목이 행이 아닐 때 메서드는 [NotSupportedException](/dotnet/api/system.notsupportedexception) 을 throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-130">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](/dotnet/api/system.notsupportedexception) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="6e676-131">ItemExists 구현</span><span class="sxs-lookup"><span data-stu-id="6e676-131">Implementing ItemExists</span></span>

<span data-ttu-id="6e676-132">사용자가 Microsoft powershell 엔진에 의해 호출 되는 경우에는 사용자가 [Microsoft powershell](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) 엔진에 의해 호출 [됩니다.-](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) .</span><span class="sxs-lookup"><span data-stu-id="6e676-132">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet.</span></span> <span data-ttu-id="6e676-133">메서드는 지정 된 경로에 항목이 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-133">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="6e676-134">항목이 존재 하는 경우 메서드는 System.object를 호출 하 여 PowerShell 엔진에 다시 전달 합니다. [Writeitemobject \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="6e676-134">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="6e676-135">Is유효한 경로 구현</span><span class="sxs-lookup"><span data-stu-id="6e676-135">Implementing IsValidPath</span></span>

<span data-ttu-id="6e676-136">[System.object](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 는 지정 된 경로가 현재 공급자에 대해 구문적으로 유효한 지 여부를 확인 하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-136">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="6e676-137">항목이 경로에 있는지 여부는 확인 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-137">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="6e676-138">다음 단계</span><span class="sxs-lookup"><span data-stu-id="6e676-138">Next steps</span></span>

<span data-ttu-id="6e676-139">일반적인 실제 공급자는 다른 항목을 포함 하는 항목을 지원 하 고 드라이브 내에서 다른 경로로 항목을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e676-139">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="6e676-140">컨테이너를 지 원하는 공급자의 예는 [컨테이너 공급자 작성](./writing-a-container-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e676-140">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="6e676-141">항목 이동을 지 원하는 공급자의 예는 [탐색 공급자 작성](./writing-a-navigation-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e676-141">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e676-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e676-142">See Also</span></span>

[<span data-ttu-id="6e676-143">컨테이너 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="6e676-143">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="6e676-144">탐색 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="6e676-144">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="6e676-145">Windows PowerShell 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="6e676-145">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)
