---
title: 원격 runspace 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: c97b0dfc12d96f99c53383d3578579f1988efd52
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143544"
---
# <a name="creating-remote-runspaces"></a><span data-ttu-id="876b9-102">원격 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="876b9-102">Creating remote runspaces</span></span>

<span data-ttu-id="876b9-103">**ComputerName** 매개 변수를 사용 하는 PowerShell 명령은 powershell을 실행 하는 모든 컴퓨터에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="876b9-103">PowerShell commands that take a **ComputerName** parameter can be run on any computer that runs PowerShell.</span></span> <span data-ttu-id="876b9-104">**ComputerName** 매개 변수를 사용 하지 않는 명령을 실행 하려면 ws-management를 사용 하 여 지정 된 컴퓨터에 연결 되는 runspace를 구성 하 고 해당 컴퓨터에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="876b9-104">To run commands that don't take a **ComputerName** parameter, you can use WS-Management to configure a runspace that connects to a specified computer, and run commands on that computer.</span></span>

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a><span data-ttu-id="876b9-105">WSManConnection을 사용 하 여 원격 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="876b9-105">Using a WSManConnection to create a remote runspace</span></span>

 <span data-ttu-id="876b9-106">원격 컴퓨터에 연결 하는 runspace를 만들려면 [runspace. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="876b9-106">To create a runspace that connects to a remote computer, you create a [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span> <span data-ttu-id="876b9-107">개체의 [Runspace WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) 속성을 설정 하 여 연결에 대 한 대상 끝점을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="876b9-107">You specify the target endpoint for the connection by setting the [System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) property of the object.</span></span> <span data-ttu-id="876b9-108">그런 다음 CreateRunspace 메서드를 호출 하 고 [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) `connectionInfo` 개체를로 지정 하 여 runspace를 만듭니다. [runspace](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 개체를 변수에.</span><span class="sxs-lookup"><span data-stu-id="876b9-108">You then create a runspace by calling the [System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) method, specifying the [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object as the `connectionInfo` parameter.</span></span>

 <span data-ttu-id="876b9-109">다음 예에서는 원격 컴퓨터에 연결 하는 runspace를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="876b9-109">The following example shows how to create a runspace that connects to a remote computer.</span></span> <span data-ttu-id="876b9-110">예제 `RemoteComputerUri` 에서는 원격 컴퓨터의 실제 URI에 대 한 자리 표시자로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="876b9-110">In the example, `RemoteComputerUri` is used as a placeholder for the actual URI of a remote computer.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // PowerShell namespace.
  using System.Management.Automation.Runspaces;  // PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      Uri RemoteComputerUri = new uri("http://Server01:5985/WSMAN");
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo(RemoteComputerUri);

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
