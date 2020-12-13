---
ms.date: 09/13/2016
ms.topic: reference
title: RemoteRunspacePool01 샘플
description: RemoteRunspacePool01 샘플
ms.openlocfilehash: 6594faca17b472140b6b0843bf8ede8e803675e3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657968"
---
# <a name="remoterunspacepool01-sample"></a>RemoteRunspacePool01 샘플

이 샘플에서는 원격 runspace 풀을 생성 하는 방법과이 풀을 사용 하 여 여러 명령을 동시에 실행 하는 방법을 보여 줍니다.

## <a name="requirements"></a>요구 사항

 이 샘플에는 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

- [Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 개체를 만듭니다.

- Runspace. [Opentimeout 개체의](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) [Runspaceconnectioninfo *](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) 및 [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) 속성을 설정 하는 중입니다. runspace. Wsmanconnectioninfo 개체의 속성을 설정 합니다.

- [Runspace Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) 개체를 사용 하 여 원격 연결을 설정 하는 원격 runspace를 만듭니다.

- 원격 runspace 풀을 사용 하 여 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 및 [get Service](/powershell/module/microsoft.powershell.management/get-service) cmdlet을 동시에 실행 합니다.

- 원격 연결을 해제 하기 위해 원격 runspace 풀을 닫는 중입니다.

## <a name="example"></a>예제

 이 샘플에서는 원격 runspace 풀을 생성 하는 방법과이 풀을 사용 하 여 여러 명령을 동시에 실행 하는 방법을 보여 줍니다.

```csharp
namespace Samples
{
  using System;
  using System.Management.Automation;            // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;  // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class RemoteRunspacePool01
  {
    /// <summary>
    /// This sample shows how to construct a remote RunspacePool and how to
    /// concurrently run the get-process and get-service commands using the
    /// runspaces of the pool.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    public static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor to
      // connect to the "localhost". The WSManConnectionInfo object can also
      // specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Create a remote runspace pool that uses the WSManConnectionInfo object.
      // The minimum runspaces value of 1 specifies that Windows PowerShell will
      // keep at least 1 runspace open. The maximum runspaces value of 2 specifies
      // that Windows PowerShell will allows 2 runspaces to be opened at the
      // same time so that two commands can be run concurrently.
      using (RunspacePool remoteRunspacePool =
             RunspaceFactory.CreateRunspacePool(1, 2, connectionInfo))
      {
        // Call the Open() method to open the runspace pool and establish
        // the connection.
        remoteRunspacePool.Open();

        // Call the Create() method to create a pipeline, call the AddCommand(string)
        // method to add the "get-process" command, and then call the BeginInvoke()
        // method to run the command asynchronously using a runspace of the pool.
        PowerShell gpsCommand = PowerShell.Create().AddCommand("get-process");
        gpsCommand.RunspacePool = remoteRunspacePool;
        IAsyncResult gpsCommandAsyncResult = gpsCommand.BeginInvoke();

        // The previous call does not block the current thread because it is
        // running asynchronously. Because the remote runspace pool can open two
        // runspaces, the second command can be run.
        PowerShell getServiceCommand = PowerShell.Create().AddCommand("get-service");
        getServiceCommand.RunspacePool = remoteRunspacePool;
        IAsyncResult getServiceCommandAsyncResult = getServiceCommand.BeginInvoke();

        // When you are ready to handle the output, wait for the command to complete
        // before extracting results. A call to the EndInvoke() method will block and return
        // the output.
        PSDataCollection<PSObject> gpsCommandOutput = gpsCommand.EndInvoke(gpsCommandAsyncResult);

        // Process the output from the first command.
        if ((gpsCommandOutput != null) && (gpsCommandOutput.Count > 0))
        {
          Console.WriteLine("The first output from running get-process command: ");
          Console.WriteLine(
                            "Process Name: {0} Process Id: {1}",
                            gpsCommandOutput[0].Properties["ProcessName"].Value,
                            gpsCommandOutput[0].Properties["Id"].Value);
          Console.WriteLine();
        }

        // Now process the output from the second command. As discussed previously, wait
        // for the command to complete before extracting the results.
        PSDataCollection<PSObject> getServiceCommandOutput = getServiceCommand.EndInvoke(
                                   getServiceCommandAsyncResult);

        // Process the output of the second command as needed.
        if ((getServiceCommandOutput != null) && (getServiceCommandOutput.Count > 0))
        {
          Console.WriteLine("The first output from running get-service command: ");
          Console.WriteLine(
                            "Service Name: {0} Description: {1} State: {2}",
                            getServiceCommandOutput[0].Properties["ServiceName"].Value,
                            getServiceCommandOutput[0].Properties["DisplayName"].Value,
                            getServiceCommandOutput[0].Properties["Status"].Value);
        }

        // Once done with running all the commands, close the remote runspace pool.
        // The Dispose() method (called by using primitive) will call Close(), if it
        // is not already called.
        remoteRunspacePool.Close();
      } // End Using.
    } // End Main.
  } // End RemoteRunspacePool01 class
}
```

## <a name="see-also"></a>참고 항목
