---
title: Runspace06 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c16324c61ee3c7123777294952999f75b2f7aef2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771994"
---
# <a name="runspace06-sample"></a>Runspace06 샘플

이 샘플에서는 runspace를 열 때 모듈이 로드 되도록 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체에 모듈을 추가 하는 방법을 보여 줍니다. 이 모듈은 GetProcessSample02 개체를 사용 하 여 동기적으로 실행 되는 Get Proc cmdlet ( [샘플](../cmdlet/getprocesssample02-sample.md)에서 정의 됨)을 제공 [합니다.](/dotnet/api/system.management.automation.powershell)

## <a name="requirements"></a>요구 사항

이 샘플에는 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

이 샘플에서는 다음을 보여 줍니다.

- [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만듭니다.

- [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체에 모듈을 추가 합니다.

- [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 사용 하는 [runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 개체를 만듭니다.

- Runspace를 사용 하는 [system.web. Powershell](/dotnet/api/system.management.automation.powershell) 개체를 만듭니다.

- 모듈의 import-module cmdlet을 [system.xml 개체의](/dotnet/api/system.management.automation.powershell) 파이프라인에 추가 합니다.

- 동기적으로 명령을 실행 합니다.

- 명령에 의해 반환 되는 [system.web. PSObject](/dotnet/api/System.Management.Automation.PSObject) 개체에서 속성을 추출 합니다.

## <a name="example"></a>예제

이 샘플에서는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 사용 하 여 runspace를 열 때 사용할 수 있는 요소를 정의 하는 runspace를 만듭니다. 이 샘플에서는 Get Proc cmdlet을 정의 하는 모듈이 초기 세션 상태에 추가 됩니다.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

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

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 호스트 애플리케이션 작성](./writing-a-windows-powershell-host-application.md)
