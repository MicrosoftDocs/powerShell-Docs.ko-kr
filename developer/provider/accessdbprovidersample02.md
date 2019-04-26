---
title: AccessDBProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: d291e401bbf3da998735ebb00f1eb35521f9a19c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081059"
---
# <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

이 샘플에서는를 덮어쓰는 방법을 보여 줍니다.는 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 고 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)메서드 호출을 지원 하기는 `New-PSDrive` 고 `Remove-PSDrive` cmdlet. 이 샘플의 공급자 클래스에서 파생 된 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다.

## <a name="demonstrates"></a>데모

> [!IMPORTANT]
> 공급자 클래스는 대부분 다음 클래스 중 하나에서 파생 되며 다른 공급자 인터페이스를 구현할 수 있습니다.
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class. 참조 [AccessDBProviderSample03](./accessdbprovidersample03.md)합니다.
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. 참조 [AccessDBProviderSample04](./accessdbprovidersample04.md)합니다.
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class. 참조 [AccessDBProviderSample05](./accessdbprovidersample05.md)합니다.
>
> 자세한 내용은 공급자 기능에 따라에서 파생 되는 공급자 클래스를 선택 하는 방법에 대 한 [Your Windows PowerShell 공급자 디자인](./provider-types.md)합니다.

이 샘플에는 다음 방법을 보여 줍니다.

- 선언 된 `CmdletProvider` 특성입니다.

- 구동 하는 공급자 클래스를 정의 합니다 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다.

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 새 드라이브를 만들기를 지 원하는 메서드. (이 샘플의 동적 매개 변수를 추가 하는 방법을 보여주지 않습니다는 `New-PSDrive` cmdlet입니다.)

- 덮어쓰기 합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 지원 기존 드라이브를 제거 하는 방법입니다.

## <a name="example"></a>예제

이 샘플에서는를 덮어쓰는 방법을 보여 줍니다.는 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 고 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive)메서드. 이 샘플 공급자에 대 한 드라이브를 만들 때 해당 연결 정보에 저장 됩니다는 `AccessDBPsDriveInfo` 개체입니다.

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  /// <summary>
  /// This sample implements a Windows PowerShell provider class
  /// that acts upon an Access database.
  /// </summary>
  /// <remarks>
  /// This example demonstrates only the drive overrides used to
  /// add and remove drives from the database.</remarks>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {
    #region Drive Manipulation

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// New-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method creates a connection to the database
    /// file and sets the Connection property of the PSDriveInfo object.
    /// </summary>
    /// <param name="drive">
    /// Information describing the drive to create.
    /// </param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the new drive.</returns>
    protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    } // End NewDrive.

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// Remove-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method closes the ODBC connection of the drive.
    /// </summary>
    /// <param name="drive">The drive to remove.</param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the removed drive.</returns>
    protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    } // End RemoveDrive.

    #endregion Drive Manipulation
  } // End AccessDBProvider class.

  #endregion AccessDBProvider

  #region AccessDBPSDriveInfo

  /// <summary>
  /// Any state associated with the drive is held here. In this
  /// case, the state information is the connection to the database.
  /// </summary>
  internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  } // End AccessDBPSDriveInfo class.

  #endregion AccessDBPSDriveInfo
}
```

## <a name="see-also"></a>참고 항목

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Windows PowerShell 공급자를 디자인합니다.](./provider-types.md)