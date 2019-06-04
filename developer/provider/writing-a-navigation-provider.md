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
ms.openlocfilehash: f449c17e4c373c42f8a1d96fa9075940111c65bc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080869"
---
# <a name="writing-a-navigation-provider"></a>탐색 공급자 작성

이 항목에는 항목 및 상대 경로 이동 합니다. 중첩 된 컨테이너 (여러 수준 데이터 저장소)를 지 원하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법을 설명 합니다. 탐색 공급자에서 파생 되어야 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스입니다.

이 항목의 예제에서 공급자 데이터 저장소로 Access 데이터베이스를 사용합니다. 도우미 메서드 및 클래스는 데이터베이스 상호 작용 하는 데 사용 되는 몇 가지 있습니다. 도우미 메서드를 포함 하는 전체 샘플을 참조 하세요 [AccessDBProviderSample05](./accessdbprovidersample05.md)합니다.

Windows PowerShell 공급자에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다.

## <a name="implementing-navigation-methods"></a>탐색 메서드를 구현합니다.

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스는 중첩 된 컨테이너, 상대 경로 및 항목을 이동 지 원하는 메서드를 구현 합니다. 이러한 메서드의 전체 목록은 참조 하세요 [NavigationCmdletProvider 메서드](http://msdn.microsoft.com/library/system.management.automation.provider.navigationcmdletprovider_methods\(v=vs.85\).aspx)합니다.

> [!NOTE]
> 이 항목의 정보를 빌드 [Windows PowerShell 공급자 퀵 스타트](./windows-powershell-provider-quickstart.md)합니다. 이 항목에서는 기본 공급자 프로젝트를 설정 하는 방법 다루지 않습니다 또는 메서드를 구현 하는 방법에서 상속 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 만들고 드라이브를 제거 하는 클래스입니다. 이 항목에서는 또한 다루지 않습니다 의해 노출 된 메서드를 구현 하는 방법을 합니다 [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 또는 [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) 클래스입니다. Item cmdlet을 구현 하는 방법을 보여 주는 예제를 보려면 [항목 공급자 작성](./writing-an-item-provider.md)합니다. 컨테이너 cmdlet을 구현 하는 방법을 보여 주는 예제를 보려면 [컨테이너 공급자 작성](./writing-a-container-provider.md)합니다.

### <a name="declaring-the-provider-class"></a>공급자 클래스를 선언합니다.

파생 하는 공급자를 선언 합니다 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스를 사용 하 여 데코 레이트 된 [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>IsItemContainer 구현

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드는 지정된 된 경로에 항목 컨테이너 인지 여부를 확인 합니다.

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

### <a name="implementing-getchildname"></a>GetChildName 구현

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드는 지정된 된 경로에 자식 항목의 이름 속성을 가져옵니다. 지정된 된 경로에 있는 항목을 컨테이너의 자식이 없으면이 메서드는 경로 반환 해야 합니다.

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

### <a name="implementing-getparentpath"></a>GetParentPath 구현

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드는 지정된 된 경로에 항목의 부모 경로 가져옵니다. 지정된 된 경로에 있는 항목 (따라서 부모가 없는) 데이터 저장소의 루트 이면이 메서드는 루트 경로 반환 해야 합니다.

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

### <a name="implementing-makepath"></a>MakePath 구현

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 메서드 조인를 지정한 부모 경로 지정 된 자식 경로 (형식에 대 한 경로 대 한 정보는 공급자-내부 경로 만들려면 공급자 지원을 참조 하세요 [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다. PowerShell 엔진을 사용자 호출 하는 경우이 메서드를 호출 합니다 [Microsoft.PowerShell.Commands.Join 경로](/dotnet/api/Microsoft.PowerShell.Commands.Join-Path) cmdlet.

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

### <a name="implementing-normalizerelativepath"></a>NormalizeRelativePath 구현

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드 `path` 및 `basepath` 매개 변수를 에해당하는정규화된경로반환합니다`path`매개 변수 및 상대 하는 `basepath` 매개 변수입니다.

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

### <a name="implementing-moveitem"></a>MoveItem 구현

합니다 [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드 지정된 된 경로에서 지정 된 대상 경로에 항목을 이동 합니다. PowerShell 엔진을 사용자 호출 하는 경우이 메서드를 호출 합니다 [Microsoft.PowerShell.Commands.Move 항목](/dotnet/api/Microsoft.PowerShell.Commands.Move-Item) cmdlet.

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

## <a name="see-also"></a>참고 항목

[컨테이너 공급자 작성](./writing-a-container-provider.md)

[Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)