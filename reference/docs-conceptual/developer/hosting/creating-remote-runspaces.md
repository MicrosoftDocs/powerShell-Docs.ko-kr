---
ms.date: 09/12/2016
ms.topic: reference
title: 원격 runspace 만들기
description: 원격 runspace 만들기
ms.openlocfilehash: 4a2af4094ff2503fc12ee460d49565f035f0e4fe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649372"
---
# <a name="creating-remote-runspaces"></a>원격 runspace 만들기

**ComputerName** 매개 변수를 사용 하는 PowerShell 명령은 powershell을 실행 하는 모든 컴퓨터에서 실행할 수 있습니다. **ComputerName** 매개 변수를 사용 하지 않는 명령을 실행 하려면 WS-Management를 사용 하 여 지정 된 컴퓨터에 연결 되는 runspace를 구성 하 고 해당 컴퓨터에서 명령을 실행 합니다.

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a>WSManConnection을 사용 하 여 원격 runspace 만들기

 원격 컴퓨터에 연결 하는 runspace를 만들려면 [runspace. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 개체를 만듭니다. 개체의 [Runspace WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) 속성을 설정 하 여 연결에 대 한 대상 끝점을 지정 합니다. 그런 다음 RunspaceFactory [개체를](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 매개 변수로 지정 하 여 [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) 메서드를 호출 하 여 runspace를 만듭니다 (예를 들어). `connectionInfo`

 다음 예에서는 원격 컴퓨터에 연결 하는 runspace를 만드는 방법을 보여 줍니다. 예제에서 `RemoteComputerUri` 는 원격 컴퓨터의 실제 URI에 대 한 자리 표시자로 사용 됩니다.

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
      Uri RemoteComputerUri = new Uri("http://Server01:5985/WSMAN");
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
