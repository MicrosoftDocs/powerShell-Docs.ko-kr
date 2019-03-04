---
title: Windows PowerShell 공급자 빠른 시작 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: ab78bcad301215bca9b5324bdb8de863899edec6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862149"
---
# <a name="windows-powershell-provider-quickstart"></a>Windows PowerShell 공급자 빠른 시작

이 항목에서는 새 드라이브를 만드는 기본 기능을 포함 하는 Windows PowerShell 공급자를 만드는 방법에 설명 합니다. 공급자에 대 한 일반적인 정보를 참조 하세요 [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다. 더 완전 한 기능을 사용 하 여 공급자의 예제를 참조 하세요 [공급자 샘플](./provider-samples.md)합니다.

## <a name="writing-a-basic-provider"></a>기본 공급자 작성

Windows PowerShell 공급자의 가장 기본적인 기능을 만들고 드라이브를 제거 하는 것입니다. 이 예제에서는 구현 된 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 하 고 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다. 또한 공급자 클래스를 선언 하는 방법에 대해서도 나타납니다.

공급자를 작성할 때 기본 드라이브 드라이브 공급자가 사용할 수 있는 때 자동으로 생성 되는 지정할 수 있습니다. 해당 공급자를 사용 하는 새 드라이브를 만드는 메서드를 정의할 수도 있습니다.

이 항목에서 제공 하는 예제를 기반으로 합니다 [AccessDBProviderSample02](./accessdbprovidersample02.md) 샘플은 Windows PowerShell 드라이브로 Access 데이터베이스를 나타내는 큰 샘플의 일부입니다.

### <a name="setting-up-the-project"></a>프로젝트 설정

Visual Studio에서 AccessDBProviderSample 라는 클래스 라이브러리 프로젝트를 만듭니다. 빌드 및 프로젝트를 시작 하는 경우, Windows PowerShell 시작 되 고 공급자를 세션으로 로드 되는 프로젝트를 구성 하려면 다음 단계를 완료 합니다.

##### <a name="configure-the-provider-project"></a>공급자 프로젝트 구성

1. System.Management.Automation 어셈블리를 프로젝트에 대 한 참조로 추가 합니다.

2. 클릭 **프로젝트 > AccessDBProviderSample 속성 > 디버그**합니다. **시작 프로젝트**, 클릭 **시작 외부 프로그램**를 이동한 다음 Windows PowerShell 실행 파일 (일반적으로 c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. 아래 **시작 옵션**, 다음을 입력 합니다 **명령줄 인수** 상자: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>공급자 클래스를 선언합니다.

공급자에서 파생 된 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다. (액세스 및 항목을 조작, 데이터 저장소를 탐색 하 고 가져오기 및 설정 항목의 내용을) 실제 기능을 제공 하는 대부분의 공급자에서 파생 된 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스입니다.

클래스에서 파생 되는 지정 하는 것 외에도 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)를 사용 하 여 데코레이트해야 합니다 [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 예제에 표시 된 대로 합니다.

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

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a>NewDrive 구현

합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드는 Windows PowerShell 엔진에서 호출 하는 사용자는 [Microsoft.Powershell.Commands.New-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)공급자의 이름을 지정 하는 cmdlet입니다. PSDriveInfo 매개 변수는 Windows PowerShell 엔진에 의해 전달 됩니다 및 Windows PowerShell 엔진에 새 드라이브를 반환 합니다. 이 메서드는 위에서 만든 클래스 내에서 선언 되어야 합니다.

메서드는 먼저 드라이브 개체와 드라이브 루트에서 전달 된 존재 반환 되도록 확인 `null` 없는 둘 중 하나입니다. 새 드라이브를 만들려면 다음 AccessDBPSDriveInfo 내부 클래스의 생성자를 사용 하 고 Access 데이터베이스 드라이브에 대 한 연결을 나타냅니다.

```csharp
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
    }
```

다음은 새 드라이브를 만드는 데 사용 된 생성자를 포함 하 고 드라이브에 대 한 상태 정보를 포함 하는 AccessDBPSDriveInfo 내부 클래스입니다.

```csharp
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
  }
```

### <a name="implementing-removedrive"></a>RemoveDrive 구현

합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드는 Windows PowerShell 엔진에서 호출 하는 사용자는 [Microsoft.Powershell.Commands.Remove-Psdrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet입니다. 이 공급자의 메서드에 Access 데이터베이스에 연결을 닫습니다.

```csharp
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
    }
```