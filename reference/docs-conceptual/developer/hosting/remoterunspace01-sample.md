---
title: RemoteRunspace01 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: f9ae846d70412858b32bfe32ba5bfbf2063d9eb1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783214"
---
# <a name="remoterunspace01-sample"></a><span data-ttu-id="b147f-102">RemoteRunspace01 샘플</span><span class="sxs-lookup"><span data-stu-id="b147f-102">RemoteRunspace01 Sample</span></span>

<span data-ttu-id="b147f-103">이 샘플에서는 원격 연결을 설정 하는 데 사용 되는 원격 runspace를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b147f-103">This sample shows how to create a remote runspace that is used to establish a remote connection.</span></span>

## <a name="requirements"></a><span data-ttu-id="b147f-104">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b147f-104">Requirements</span></span>

 <span data-ttu-id="b147f-105">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b147f-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b147f-106">데모</span><span class="sxs-lookup"><span data-stu-id="b147f-106">Demonstrates</span></span>

- <span data-ttu-id="b147f-107">[Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b147f-107">Creating a [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="b147f-108">Runspace. [Opentimeout 개체의](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) [Runspaceconnectioninfo \*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) 및 [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) 속성을 설정 하는 중입니다. runspace. Wsmanconnectioninfo 개체의 속성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b147f-108">Setting the [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Operationtimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) and [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Opentimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) properties of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="b147f-109">[Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 개체를 사용 하 여 원격 연결을 설정 하는 원격 runspace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b147f-109">Creating a remote runspace that uses the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object to establish the remote connection.</span></span>

- <span data-ttu-id="b147f-110">원격 연결을 해제 하기 위해 원격 runspace를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="b147f-110">Closing the remote runspace to release the remote connection.</span></span>

## <a name="example"></a><span data-ttu-id="b147f-111">예제</span><span class="sxs-lookup"><span data-stu-id="b147f-111">Example</span></span>

<span data-ttu-id="b147f-112">이 샘플에서는 원격 연결을 정의한 다음 해당 연결 정보를 사용 하 여 원격 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b147f-112">This sample defines a remote connection and then uses that connection information to establish a remote connection.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;             // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;   // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class RemoteRunspace01
  {
    /// <summary>
    /// This sample shows how to use a WSManConnectionInfo object to set
    /// various timeouts and how to establish a remote connection.
    /// </summary>
    /// <param name="args">This parameter is not used.</param>
    public static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Set the OperationTimeout property. The OperationTimeout is used to tell
      // Windows PowerShell how long to wait (in milliseconds) before timing out
      // for any operation. This includes sending input data to the remote computer,
      // receiving output data from the remote computer, and more. The user can
      // change this timeout depending on whether the connection is to a computer
      // in the data center or across a slow WAN.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.

      // Set the OpenTimeout property. OpenTimeout is used to tell Windows PowerShell
      // how long to wait (in milliseconds) before timing out while establishing a
      // remote connection. The user can change this timeout depending on whether the
      // connection is to a computer in the data center or across a slow WAN.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
        remoteRunspace.Open();

        // Add the code to run commands in the remote runspace here. The
        // OperationTimeout value set previously will play a role here because
        // running commands involves sending and receiving data.

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
