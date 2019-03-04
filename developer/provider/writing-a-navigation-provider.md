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
ms.openlocfilehash: a789b392bddd344ad583c93a1a55302329df9917
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863539"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="389df-102">탐색 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="389df-102">Writing a navigation provider</span></span>

<span data-ttu-id="389df-103">이 항목에는 항목 및 상대 경로 이동 합니다. 중첩 된 컨테이너 (여러 수준 데이터 저장소)를 지 원하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="389df-104">탐색 공급자에서 파생 되어야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="389df-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="389df-105">이 항목의 예제에서 공급자 데이터 저장소로 Access 데이터베이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="389df-106">도우미 메서드 및 클래스는 데이터베이스 상호 작용 하는 데 사용 되는 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="389df-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="389df-107">도우미 메서드를 포함 하는 전체 샘플을 참조 하세요 [AccessDBProviderSample05](./accessdbprovidersample05.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="389df-108">Windows PowerShell 공급자에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="389df-109">탐색 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-109">Implementing navigation methods</span></span>

<span data-ttu-id="389df-110">합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스는 중첩 된 컨테이너, 상대 경로 및 항목을 이동 지 원하는 메서드를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="389df-111">이러한 메서드의 전체 목록은 참조 하세요 [NavigationCmdletProvider 메서드](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx)합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="389df-112">이 항목의 정보를 빌드 [Windows PowerShell 공급자 퀵 스타트](./windows-powershell-provider-quickstart.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="389df-113">이 항목에서는 기본 공급자 프로젝트를 설정 하는 방법 다루지 않습니다 또는 메서드를 구현 하는 방법에서 상속 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 만들고 드라이브를 제거 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="389df-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="389df-114">이 항목에서는 또한 다루지 않습니다 의해 노출 된 메서드를 구현 하는 방법을 합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 또는 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="389df-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="389df-115">Item cmdlet을 구현 하는 방법을 보여 주는 예제를 보려면 [항목 공급자 작성](./writing-an-item-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="389df-116">컨테이너 cmdlet을 구현 하는 방법을 보여 주는 예제를 보려면 [컨테이너 공급자 작성](./writing-a-container-provider.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="389df-117">공급자 클래스를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-117">Declaring the provider class</span></span>

<span data-ttu-id="389df-118">파생 하는 공급자를 선언 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 사용 하 여 데코 레이트 된 [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="389df-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="389df-119">IsItemContainer 구현</span><span class="sxs-lookup"><span data-stu-id="389df-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="389df-120">합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드는 지정된 된 경로에 항목 컨테이너 인지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="389df-121">GetChildName 구현</span><span class="sxs-lookup"><span data-stu-id="389df-121">Implementing GetChildName</span></span>

<span data-ttu-id="389df-122">합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드는 지정된 된 경로에 자식 항목의 이름 속성을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="389df-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="389df-123">지정된 된 경로에 있는 항목을 컨테이너의 자식이 없으면이 메서드는 경로 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="389df-124">GetParentPath 구현</span><span class="sxs-lookup"><span data-stu-id="389df-124">Implementing GetParentPath</span></span>

<span data-ttu-id="389df-125">합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드는 지정된 된 경로에 항목의 부모 경로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="389df-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="389df-126">지정된 된 경로에 있는 항목 (따라서 부모가 없는) 데이터 저장소의 루트 이면이 메서드는 루트 경로 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="389df-127">MakePath 구현</span><span class="sxs-lookup"><span data-stu-id="389df-127">Implementing MakePath</span></span>

<span data-ttu-id="389df-128">합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드 조인를 지정한 부모 경로 지정 된 자식 경로 (형식에 대 한 경로 대 한 정보는 공급자-내부 경로 만들려면 공급자 지원을 참조 하세요 [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="389df-129">PowerShell 엔진을 사용자 호출 하는 경우이 메서드를 호출 합니다 [Microsoft.Powershell.Commands.Join 경로](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="389df-129">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Join-Path](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="389df-130">NormalizeRelativePath 구현</span><span class="sxs-lookup"><span data-stu-id="389df-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="389df-131">합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드 `path` 및 `basepath` 매개 변수를 에해당하는정규화된경로반환합니다`path`매개 변수 및 상대 하는 `basepath` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="389df-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="389df-132">MoveItem 구현</span><span class="sxs-lookup"><span data-stu-id="389df-132">Implementing MoveItem</span></span>

<span data-ttu-id="389df-133">합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드 지정된 된 경로에서 지정 된 대상 경로에 항목을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="389df-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="389df-134">PowerShell 엔진을 사용자 호출 하는 경우이 메서드를 호출 합니다 [Microsoft.Powershell.Commands.Move 항목](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="389df-134">The PowerShell engine calls this method when a user calls the [Microsoft.Powershell.Commands.Move-Item](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="389df-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="389df-135">See Also</span></span>

[<span data-ttu-id="389df-136">컨테이너 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="389df-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="389df-137">Windows PowerShell 공급자 개요</span><span class="sxs-lookup"><span data-stu-id="389df-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)