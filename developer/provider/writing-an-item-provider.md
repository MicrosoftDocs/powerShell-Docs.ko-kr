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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058195"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="cb6cb-102">항목 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="cb6cb-102">Writing an item provider</span></span>

<span data-ttu-id="cb6cb-103">이 항목에 액세스 하 고 데이터 저장소의 항목을 조작 하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="cb6cb-104">항목에 액세스할 수 있어야 하는 공급자에서 파생 되어야 합니다는 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="cb6cb-105">이 항목의 예제에서 공급자 데이터 저장소로 Access 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="cb6cb-106">도우미 메서드 및 클래스는 데이터베이스 상호 작용 하는 데 사용 되는 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="cb6cb-107">도우미 메서드를 포함 하는 전체 샘플을 참조 하세요. [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="cb6cb-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="cb6cb-108">Windows PowerShell 공급자에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="cb6cb-109">항목 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-109">Implementing item methods</span></span>

<span data-ttu-id="cb6cb-110">합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스에 액세스 하는 데이터 저장소에서 항목을 조작할 수 있는 여러 메서드를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="cb6cb-111">이러한 메서드의 전체 목록은 참조 하세요 [ItemCmdletProvider 메서드](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="cb6cb-112">이 예제에서는 이러한 메서드 중 4 개를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="cb6cb-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 지정된 된 경로에 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="cb6cb-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 지정된 된 항목의 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="cb6cb-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 항목이 지정된 된 경로에 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="cb6cb-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 데이터 저장소의 위치에 매핑되는 경우 참조에 대 한 경로 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="cb6cb-117">이 항목의 정보를 빌드 [Windows PowerShell 공급자 퀵 스타트](./windows-powershell-provider-quickstart.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="cb6cb-118">이 항목에서는 기본 공급자 프로젝트를 설정 하는 방법 다루지 않습니다 또는 메서드를 구현 하는 방법에서 상속 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 만들고 드라이브를 제거 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="cb6cb-119">공급자 클래스를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-119">Declaring the provider class</span></span>

<span data-ttu-id="cb6cb-120">파생 하는 공급자를 선언 합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 클래스를 사용 하 여 데코 레이트 된 [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="cb6cb-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="cb6cb-121">GetItem 구현</span><span class="sxs-lookup"><span data-stu-id="cb6cb-121">Implementing GetItem</span></span>

<span data-ttu-id="cb6cb-122">합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) 사용자를 호출할 때 PowerShell 엔진에 의해 호출 됩니다 합니다 [Microsoft.PowerShell.Commands.Get 항목](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet에 공급자입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="cb6cb-123">메서드는 지정된 된 경로에 있는 항목을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="cb6cb-124">Access 데이터베이스 예제에서는 메서드 항목에 드라이브를 자체 데이터베이스 또는 데이터베이스에서 행의 테이블 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="cb6cb-125">메서드를 호출 하 여 PowerShell 엔진에 항목을 전송 합니다 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) 메서드.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="cb6cb-126">SetItem 구현</span><span class="sxs-lookup"><span data-stu-id="cb6cb-126">Implementing SetItem</span></span>

<span data-ttu-id="cb6cb-127">합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) 메서드는 PowerShell 엔진을 호출 하 여 사용자를 호출할 때 합니다 [Microsoft.PowerShell.Commands.Set 항목](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet .</span><span class="sxs-lookup"><span data-stu-id="cb6cb-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="cb6cb-128">지정된 된 경로에 있는 항목의 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="cb6cb-129">해당 항목 이므로 행에는 메서드가 throw 하는 경우에 있는 항목의 값을 설정 하려면 편이 Access 데이터베이스 예제에서 [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) 항목이 없는 경우 행입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="cb6cb-130">ItemExists 구현</span><span class="sxs-lookup"><span data-stu-id="cb6cb-130">Implementing ItemExists</span></span>

<span data-ttu-id="cb6cb-131">합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) 메서드는 PowerShell 엔진에서 호출 하는 사용자는 [Microsoft.PowerShell.Commands.Test 경로](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="cb6cb-132">메서드는 지정된 된 경로에 항목이 있는지 여부를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="cb6cb-133">항목이 없으면 메서드가 전달 PowerShell 엔진으로 다시 호출 하 여 [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="cb6cb-134">IsValidPath 구현</span><span class="sxs-lookup"><span data-stu-id="cb6cb-134">Implementing IsValidPath</span></span>

<span data-ttu-id="cb6cb-135">합니다 [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) 메서드 구문상 유효한 현재 공급자에 대 한 지정된 된 경로 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="cb6cb-136">항목 경로에 있는지 여부를 확인 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="cb6cb-137">다음 단계</span><span class="sxs-lookup"><span data-stu-id="cb6cb-137">Next steps</span></span>

<span data-ttu-id="cb6cb-138">일반적인 실제 공급자는 하나의 경로에서 드라이브 내에서 다른 항목을 이동 및 기타 항목을 포함 하는 항목을 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="cb6cb-139">컨테이너를 지 원하는 공급자의 예제를 보려면 [컨테이너 공급자 작성](./writing-a-container-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="cb6cb-140">이동 된 항목을 지 원하는 공급자의 예제를 참조 하세요 [탐색 공급자 작성](./writing-a-navigation-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6cb-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb6cb-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb6cb-141">See Also</span></span>

[<span data-ttu-id="cb6cb-142">컨테이너 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="cb6cb-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="cb6cb-143">탐색 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="cb6cb-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="cb6cb-144">Windows PowerShell 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="cb6cb-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)