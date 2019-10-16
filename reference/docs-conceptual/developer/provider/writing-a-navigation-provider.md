---
title: 탐색 공급자 작성 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359872"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="f2106-102">탐색 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="f2106-102">Writing a navigation provider</span></span>

<span data-ttu-id="f2106-103">이 항목에서는 중첩 된 컨테이너 (다중 수준 데이터 저장소), 항목 이동 및 상대 경로를 지 원하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="f2106-104">탐색 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 의 클래스에서 파생 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="f2106-105">이 항목의 예제 공급자는 Access 데이터베이스를 데이터 저장소로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="f2106-106">데이터베이스와 상호 작용 하는 데 사용 되는 여러 가지 도우미 메서드 및 클래스가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="f2106-107">도우미 메서드를 포함 하는 전체 샘플은 [AccessDBProviderSample05](./accessdbprovidersample05.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2106-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="f2106-108">Windows PowerShell 공급자에 대 한 자세한 내용은 [Windows Powershell 공급자 개요](./windows-powershell-provider-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2106-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="f2106-109">탐색 메서드 구현</span><span class="sxs-lookup"><span data-stu-id="f2106-109">Implementing navigation methods</span></span>

<span data-ttu-id="f2106-110">[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스는 중첩 된 컨테이너, 상대 경로 및 이동 항목을 지 원하는 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="f2106-111">이러한 메서드의 전체 목록은 [Navigationcmdletprovider 메서드](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2106-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="f2106-112">이 항목은 [Windows PowerShell 공급자 빠른](./windows-powershell-provider-quickstart.md)시작의 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="f2106-113">이 항목에서는 공급자 프로젝트를 설정 하는 방법에 대 한 기본 사항을 다루지 않으며, 드라이브를 만들고 제거 하는 [system.web](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . c a c.</span><span class="sxs-lookup"><span data-stu-id="f2106-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="f2106-114">이 항목에서는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) [클래스에 의해](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 노출 되는 메서드를 구현 하는 방법에 대해서도 설명 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="f2106-115">항목 cmdlet을 구현 하는 방법을 보여 주는 예제는 [항목 공급자 작성](./writing-an-item-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2106-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="f2106-116">컨테이너 cmdlet을 구현 하는 방법을 보여 주는 예제는 [컨테이너 공급자 작성](./writing-a-container-provider.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f2106-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="f2106-117">공급자 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="f2106-117">Declaring the provider class</span></span>

<span data-ttu-id="f2106-118">[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)를 사용 하 여 파생 시킬 [공급자를](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 선언 하 고 해당 클래스를 사용 하 여 데코 레이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="f2106-119">IsItemContainer 구현</span><span class="sxs-lookup"><span data-stu-id="f2106-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="f2106-120">[Isitemcontainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드는 지정 된 경로에 있는 항목이 컨테이너 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a><span data-ttu-id="f2106-121">GetChildName 구현</span><span class="sxs-lookup"><span data-stu-id="f2106-121">Implementing GetChildName</span></span>

<span data-ttu-id="f2106-122">[Getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드는 지정 된 경로에 있는 자식 항목의 name 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="f2106-123">지정 된 경로에 있는 항목이 컨테이너의 자식이 아닌 경우이 메서드는 경로를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a><span data-ttu-id="f2106-124">GetParentPath 구현</span><span class="sxs-lookup"><span data-stu-id="f2106-124">Implementing GetParentPath</span></span>

<span data-ttu-id="f2106-125">[Getparentpath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드는 지정 된 경로에서 항목의 부모에 대 한 경로를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="f2106-126">지정 된 경로에 있는 항목이 데이터 저장소의 루트 (부모를 포함 하지 않음) 인 경우이 메서드는 루트 경로를 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a><span data-ttu-id="f2106-127">MakePath 구현</span><span class="sxs-lookup"><span data-stu-id="f2106-127">Implementing MakePath</span></span>

<span data-ttu-id="f2106-128">System.object는 지정 된 부모 경로와 지정 된 자식 경로를 조인 하 여 공급자 내부 경로를 만듭니다. 공급자가 지원할 수 있는 경로 형식에 대 한 자세한 내용은을 참조 하십시오 [.](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f2106-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="f2106-129">PowerShell 엔진은 사용자가 [Microsoft powershell. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet을 호출할 때이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="f2106-130">NormalizeRelativePath 구현</span><span class="sxs-lookup"><span data-stu-id="f2106-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="f2106-131">[Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드는 `path` 및 `basepath` 매개 변수를 사용 하 고 `path` 매개 변수와 동일 하 고 `basepath`를 기준으로 하는 정규화 된 경로를 반환 합니다. 변수에.</span><span class="sxs-lookup"><span data-stu-id="f2106-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a><span data-ttu-id="f2106-132">MoveItem 구현</span><span class="sxs-lookup"><span data-stu-id="f2106-132">Implementing MoveItem</span></span>

<span data-ttu-id="f2106-133">[Moveitem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드는 지정 된 경로에서 지정 된 대상 경로에 항목을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="f2106-134">PowerShell 엔진은 사용자가 [MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet을 호출할 때이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2106-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a><span data-ttu-id="f2106-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f2106-135">See Also</span></span>

[<span data-ttu-id="f2106-136">컨테이너 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="f2106-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="f2106-137">Windows PowerShell 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="f2106-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)