---
title: 탐색 공급자 작성 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 2fd27314a2b8547a15dd1bb72aa8f970d40b18cc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786784"
---
# <a name="writing-a-navigation-provider"></a>탐색 공급자 작성

이 항목에서는 중첩 된 컨테이너 (다중 수준 데이터 저장소), 항목 이동 및 상대 경로를 지 원하는 Windows PowerShell 공급자의 메서드를 구현 하는 방법에 대해 설명 합니다. 탐색 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 의 클래스에서 파생 되어야 합니다.

이 항목의 예제 공급자는 Access 데이터베이스를 데이터 저장소로 사용 합니다. 데이터베이스와 상호 작용 하는 데 사용 되는 여러 가지 도우미 메서드 및 클래스가 있습니다. 도우미 메서드를 포함 하는 전체 샘플은 [AccessDBProviderSample05](./accessdbprovidersample05.md)를 참조 하세요.

Windows PowerShell 공급자에 대 한 자세한 내용은 [Windows Powershell 공급자 개요](./windows-powershell-provider-overview.md)를 참조 하세요.

## <a name="implementing-navigation-methods"></a>탐색 메서드 구현

[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스는 중첩 된 컨테이너, 상대 경로 및 이동 항목을 지 원하는 메서드를 구현 합니다. 이러한 메서드의 전체 목록은 [Navigationcmdletprovider 메서드](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods)를 참조 하세요.

> [!NOTE]
> 이 항목은 [Windows PowerShell 공급자 빠른](./windows-powershell-provider-quickstart.md)시작의 정보를 기반으로 합니다. 이 항목에서는 공급자 프로젝트를 설정 하는 방법에 대 한 기본 사항을 다루지 않으며, 드라이브를 만들고 제거 하는 [system.web](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .. c a c. 이 항목에서는 [Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) [클래스에 의해](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) 노출 되는 메서드를 구현 하는 방법에 대해서도 설명 하지 않습니다. 항목 cmdlet을 구현 하는 방법을 보여 주는 예제는 [항목 공급자 작성](./writing-an-item-provider.md)을 참조 하세요. 컨테이너 cmdlet을 구현 하는 방법을 보여 주는 예제는 [컨테이너 공급자 작성](./writing-a-container-provider.md)을 참조 하세요.

### <a name="declaring-the-provider-class"></a>공급자 클래스 선언

[Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute)를 사용 하 여 파생 시킬 [공급자를](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 선언 하 고 해당 클래스를 사용 하 여 데코 레이트 합니다.

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>IsItemContainer 구현

[Isitemcontainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) 메서드는 지정 된 경로에 있는 항목이 컨테이너 인지 여부를 확인 합니다.

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

[Getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) 메서드는 지정 된 경로에 있는 자식 항목의 name 속성을 가져옵니다.. 지정 된 경로에 있는 항목이 컨테이너의 자식이 아닌 경우이 메서드는 경로를 반환 해야 합니다.

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

[Getparentpath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) 메서드는 지정 된 경로에서 항목의 부모에 대 한 경로를 가져옵니다. 지정 된 경로에 있는 항목이 데이터 저장소의 루트 (부모를 포함 하지 않음) 인 경우이 메서드는 루트 경로를 반환 해야 합니다.

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

[System.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) 는 지정 된 부모 경로와 지정 된 자식 경로를 조인 하 여 공급자 내부 경로를 만듭니다. 공급자가 지원할 수 있는 경로 형식에 대 한 자세한 내용은 [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)를 참조 하세요. PowerShell 엔진은 사용자가 [Microsoft powershell. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet을 호출할 때이 메서드를 호출 합니다.

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

[Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) 메서드는 및 매개 변수를 사용 하 고 매개 변수에 `path` 해당 하 `basepath` `path` 고 매개 변수를 기준으로 하는 정규화 된 경로를 반환 합니다. `basepath`

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

[Moveitem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) 메서드는 지정 된 경로에서 지정 된 대상 경로에 항목을 이동 합니다. PowerShell 엔진은 사용자가 [MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet을 호출할 때이 메서드를 호출 합니다.

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
