---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace07 샘플
description: Runspace07 샘플
ms.openlocfilehash: 4356f33a1d962a0a6c5ca1ebb8c3e4c579463022
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657668"
---
# <a name="runspace07-sample"></a>Runspace07 샘플

이 샘플은 runspace를 만든 다음이 runspace를 사용 하 여 두 개의 cmdlet을 동기적으로 실행 하는 방법을 보여 [줍니다.](/dotnet/api/system.management.automation.powershell)

## <a name="requirements"></a>요구 사항

이 샘플에는 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

이 샘플에서는 다음을 보여 줍니다.

- Runspacefactory 클래스를 사용 하 여 [runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 개체를 만듭니다. [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) 클래스를 사용 합니다.

- Runspace를 사용 하는 [system.web. Powershell](/dotnet/api/system.management.automation.powershell) 개체를 만듭니다.

- Cmdlet을 [system.web. Powershell](/dotnet/api/system.management.automation.powershell) 개체의 파이프라인에 추가 합니다.

- Cmdlet을 동기적으로 실행 합니다.

- 명령에 의해 반환 되는 [system.web. PSObject](/dotnet/api/System.Management.Automation.PSObject) 개체에서 속성을 추출 합니다.

## <a name="example"></a>예제

이 샘플은 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 및 [Measure-object](/powershell/module/microsoft.powershell.utility/measure-object) cmdlet을 실행 하기 위해 [system.object](/dotnet/api/System.Management.Automation.PSObject) 에서 사용 하는 runspace를 만듭니다.

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
  internal class Runspace07
  {
    /// <summary>
    /// This sample shows how to create a runspace and how to run commands
    /// using a PowerShell object. It builds a pipeline that runs the
    /// get-process cmdlet, which is piped to the measure-object
    /// cmdlet to count the number of processes running on the system.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a runspace using the RunspaceFactory class.
    /// 2. Creating a PowerShell object that uses the runspace.
    /// 3. Adding cmdlets to the pipeline of the PowerShell object.
    /// 4. Running the cmdlets synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the cmdlets.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> result;     // Will hold the result
                                       // of running the cmdlets.

      // Create a runspace. We can not use the RunspaceInvoke class
      // because we need to get at the underlying runspace to
      // explicitly add the commands. Notice that no PSHost object is
      // supplied to the CreateRunspace method so the default host is
      // used. See the Host samples for more information on creating
      // your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace())
      {
        myRunSpace.Open();

        // Create a PowerShell object and specify the runspace.
        PowerShell powershell = PowerShell.Create();
        powershell.Runspace = myRunSpace;

        // Use the using statement so we dispose of the PowerShell object
        // when we're done.
        using (powershell)
        {
          // Add the get-process cmdlet to the PowerShell object. Notice
          // we are specify the name of the cmdlet, not a script.
          powershell.AddCommand("get-process");

          // Add the measure-object cmdlet to count the number
          // of objects being returned. Commands are always added to the end
          // of the pipeline.
          powershell.AddCommand("measure-object");

          // Run the cmdlets synchronously and save the objects returned.
          result = powershell.Invoke();
        }

        // Even after disposing of the pipeLine, we still need to set
        // the powershell variable to null so that the garbage collector
        // can clean it up.
        powershell = null;

        // Display the results of running the commands (checking that
        // everything is ok first.
        if (result == null || result.Count != 1)
        {
          throw new InvalidOperationException(
                    "pipeline.Invoke() returned the wrong number of objects");
        }

        PSMemberInfo count = result[0].Properties["Count"];
        if (count == null)
        {
          throw new InvalidOperationException(
                    "The object returned doesn't have a 'count' property");
        }

        Console.WriteLine(
                   "Runspace07: The Get-Process cmdlet returned {0} objects",
                   count.Value);

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
