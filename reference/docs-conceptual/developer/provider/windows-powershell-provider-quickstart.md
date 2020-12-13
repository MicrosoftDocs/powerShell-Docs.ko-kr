---
ms.date: 09/13/2016
ms.topic: reference
title: Windows PowerShell 공급자 빠른 시작
description: Windows PowerShell 공급자 빠른 시작
ms.openlocfilehash: f0fe0ad60e9d10efd505cda60af995c597226b92
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664339"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="466c5-103">Windows PowerShell 공급자 빠른 시작</span><span class="sxs-lookup"><span data-stu-id="466c5-103">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="466c5-104">이 항목에서는 새 드라이브를 만드는 기본적인 기능을 포함 하는 Windows PowerShell 공급자를 만드는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-104">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="466c5-105">공급자에 대 한 일반 정보는 [Windows PowerShell 공급자 개요](./windows-powershell-provider-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="466c5-105">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="466c5-106">보다 완전 한 기능을 제공 하는 공급자의 예는 [공급자 샘플](./provider-samples.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="466c5-106">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="466c5-107">기본 공급자 작성</span><span class="sxs-lookup"><span data-stu-id="466c5-107">Writing a basic provider</span></span>

<span data-ttu-id="466c5-108">Windows PowerShell 공급자의 가장 기본적인 기능은 드라이브를 만들고 제거 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-108">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="466c5-109">이 예제에서는 [Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 및 Removedrive \* 메서드를 구현 합니다 .이 메서드는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 의 [\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드를 구현 하는 것입니다.. c d m. c d m. c d m.</span><span class="sxs-lookup"><span data-stu-id="466c5-109">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="466c5-110">공급자 클래스를 선언 하는 방법도 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-110">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="466c5-111">공급자를 작성할 때 공급자를 사용할 수 있을 때 자동으로 생성 되는 기본 드라이브 드라이브를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-111">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="466c5-112">또한 메서드를 정의 하 여 해당 공급자를 사용 하는 새 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-112">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="466c5-113">이 항목에서 제공 하는 예제는 Access 데이터베이스를 Windows PowerShell 드라이브로 나타내는 큰 샘플의 일부인 [AccessDBProviderSample02](./accessdbprovidersample02.md) 샘플을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-113">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="466c5-114">프로젝트 설정</span><span class="sxs-lookup"><span data-stu-id="466c5-114">Setting up the project</span></span>

<span data-ttu-id="466c5-115">Visual Studio에서 AccessDBProviderSample 이라는 클래스 라이브러리 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-115">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="466c5-116">다음 단계를 완료 하 여 Windows PowerShell이 시작 되 고 프로젝트를 빌드하고 시작할 때 공급자가 세션에 로드 되도록 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-116">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="466c5-117">공급자 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="466c5-117">Configure the provider project</span></span>

1. <span data-ttu-id="466c5-118">프로젝트에 대 한 참조로 System.web 어셈블리를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-118">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="466c5-119">**Project > AccessDBProviderSample 속성 > 디버그** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-119">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="466c5-120">**시작 프로젝트** 에서 **시작 외부 프로그램** 을 클릭 하 고 Windows PowerShell 실행 파일 (일반적으로 c:\Windows\System32\WindowsPowerShell\v1.0 \\.powershell.exe)로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-120">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="466c5-121">**시작 옵션** 아래에서 **명령줄 인수** 상자에 다음을 입력 합니다.`-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="466c5-121">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="466c5-122">공급자 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="466c5-122">Declaring the provider class</span></span>

<span data-ttu-id="466c5-123">이 공급자는 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) 에서 파생 된 공급자 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-123">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="466c5-124">실제 기능을 제공 하는 대부분의 공급자 (항목 액세스 및 조작, 데이터 저장소 탐색, 항목 내용 가져오기 및 설정)는 [system.object](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) 에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-124">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="466c5-125">클래스가 [system.object](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider)에서 파생 되도록 지정 하는 것 외에도 예제에 표시 된 것 처럼 [Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) 를 사용 하 여 데코 레이트 된 클래스를 사용 하도록 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-125">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="466c5-126">NewDrive 구현</span><span class="sxs-lookup"><span data-stu-id="466c5-126">Implementing NewDrive</span></span>

<span data-ttu-id="466c5-127">사용자가 공급자의 이름을 지정 하 여 [NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet을 호출 하는 경우 [Newdrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) 메서드는 Windows powershell 엔진에 의해 호출 되는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-127">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="466c5-128">PSDriveInfo 매개 변수는 Windows PowerShell 엔진에 의해 전달 되 고, 메서드는 새 드라이브를 Windows PowerShell 엔진에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-128">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="466c5-129">이 메서드는 위에서 만든 클래스 내에서 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-129">This method must be declared within the class created above.</span></span>

<span data-ttu-id="466c5-130">메서드는 먼저 전달 된 드라이브 개체와 드라이브 루트를 모두 사용 하는지 확인 하 고, 둘 중 하나가 없는 `null` 경우를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-130">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="466c5-131">그런 다음 내부 클래스 AccessDBPSDriveInfo의 생성자를 사용 하 여 드라이브가 나타내는 액세스 데이터베이스에 대 한 연결 및 새 드라이브를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-131">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="466c5-132">다음은 새 드라이브를 만드는 데 사용 되는 생성자를 포함 하는 AccessDBPSDriveInfo 내부 클래스 이며 드라이브의 상태 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-132">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="466c5-133">RemoveDrive 구현</span><span class="sxs-lookup"><span data-stu-id="466c5-133">Implementing RemoveDrive</span></span>

<span data-ttu-id="466c5-134">사용자가 [RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet을 호출 하는 경우 [Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) 메서드는 Windows PowerShell 엔진에서 호출 하는 경우에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-134">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="466c5-135">이 공급자의 메서드는 Access 데이터베이스에 대 한 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="466c5-135">The method in this provider closes the connection to the Access database.</span></span>

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
