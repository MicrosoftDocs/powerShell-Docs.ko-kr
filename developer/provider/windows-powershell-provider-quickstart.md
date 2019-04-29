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
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080886"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="75078-102">Windows PowerShell 공급자 빠른 시작</span><span class="sxs-lookup"><span data-stu-id="75078-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="75078-103">이 항목에서는 새 드라이브를 만드는 기본 기능을 포함 하는 Windows PowerShell 공급자를 만드는 방법에 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="75078-104">공급자에 대 한 일반적인 정보를 참조 하세요 [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="75078-105">더 완전 한 기능을 사용 하 여 공급자의 예제를 참조 하세요 [공급자 샘플](./provider-samples.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="75078-106">기본 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="75078-106">Writing a basic provider</span></span>

<span data-ttu-id="75078-107">Windows PowerShell 공급자의 가장 기본적인 기능을 만들고 드라이브를 제거 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="75078-108">이 예제에서는 구현 된 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 하 고 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="75078-109">또한 공급자 클래스를 선언 하는 방법에 대해서도 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="75078-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="75078-110">공급자를 작성할 때 기본 드라이브 드라이브 공급자가 사용할 수 있는 때 자동으로 생성 되는 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75078-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="75078-111">해당 공급자를 사용 하는 새 드라이브를 만드는 메서드를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75078-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="75078-112">이 항목에서 제공 하는 예제를 기반으로 합니다 [AccessDBProviderSample02](./accessdbprovidersample02.md) 샘플은 Windows PowerShell 드라이브로 Access 데이터베이스를 나타내는 큰 샘플의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="75078-113">프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="75078-113">Setting up the project</span></span>

<span data-ttu-id="75078-114">Visual Studio에서 AccessDBProviderSample 라는 클래스 라이브러리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="75078-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="75078-115">빌드 및 프로젝트를 시작 하는 경우, Windows PowerShell 시작 되 고 공급자를 세션으로 로드 되는 프로젝트를 구성 하려면 다음 단계를 완료 합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="75078-116">공급자 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="75078-116">Configure the provider project</span></span>

1. <span data-ttu-id="75078-117">System.Management.Automation 어셈블리를 프로젝트에 대 한 참조로 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="75078-118">클릭 **프로젝트 > AccessDBProviderSample 속성 > 디버그**합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="75078-119">**시작 프로젝트**, 클릭 **시작 외부 프로그램**를 이동한 다음 Windows PowerShell 실행 파일 (일반적으로 c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="75078-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="75078-120">아래 **시작 옵션**, 다음을 입력 합니다 **명령줄 인수** 상자: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="75078-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="75078-121">공급자 클래스를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-121">Declaring the provider class</span></span>

<span data-ttu-id="75078-122">공급자에서 파생 된 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="75078-123">(액세스 및 항목을 조작, 데이터 저장소를 탐색 하 고 가져오기 및 설정 항목의 내용을) 실제 기능을 제공 하는 대부분의 공급자에서 파생 된 [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="75078-124">클래스에서 파생 되는 지정 하는 것 외에도 [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)를 사용 하 여 데코레이트해야 합니다 [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 예제에 표시 된 대로 합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="75078-125">NewDrive 구현</span><span class="sxs-lookup"><span data-stu-id="75078-125">Implementing NewDrive</span></span>

<span data-ttu-id="75078-126">합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드는 Windows PowerShell 엔진에서 호출 하는 사용자는 [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)공급자의 이름을 지정 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="75078-127">PSDriveInfo 매개 변수는 Windows PowerShell 엔진에 의해 전달 됩니다 및 Windows PowerShell 엔진에 새 드라이브를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="75078-128">이 메서드는 위에서 만든 클래스 내에서 선언 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="75078-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="75078-129">메서드는 먼저 드라이브 개체와 드라이브 루트에서 전달 된 존재 반환 되도록 확인 `null` 없는 둘 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="75078-130">새 드라이브를 만들려면 다음 AccessDBPSDriveInfo 내부 클래스의 생성자를 사용 하 고 Access 데이터베이스 드라이브에 대 한 연결을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="75078-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="75078-131">다음은 새 드라이브를 만드는 데 사용 된 생성자를 포함 하 고 드라이브에 대 한 상태 정보를 포함 하는 AccessDBPSDriveInfo 내부 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="75078-132">RemoveDrive 구현</span><span class="sxs-lookup"><span data-stu-id="75078-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="75078-133">합니다 [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드는 Windows PowerShell 엔진에서 호출 하는 사용자는 [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="75078-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="75078-134">이 공급자의 메서드에 Access 데이터베이스에 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="75078-134">The method in this provider closes the connection to the Access database.</span></span>

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