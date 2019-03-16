---
title: Runspace07 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4f7bf81e-4f95-4150-afc3-c0872b24d026
caps.latest.revision: 7
ms.openlocfilehash: 3205286fbbc823d21e29a328b3ba9c4c1459d9ff
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056960"
---
# <a name="runspace07-sample"></a>Runspace07 샘플

이 샘플에서는 runspace를 만들고 해당 runspace를 사용 하 여 두 개의 cmdlet을 사용 하 여 동기적으로 실행 하는 방법을 보여 줍니다.는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.

## <a name="requirements"></a>요구 사항

이 샘플 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>시연

이 샘플에는 다음 방법을 보여 줍니다.

- 만들기는 [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 사용 하 여 개체를 [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) 클래스입니다.

- 만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) runspace를 사용 하는 개체입니다.

- Cmdlet의 파이프라인에 추가 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.

- Cmdlet을 동기적으로 실행 합니다.

- 속성에서 추출 합니다 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 명령에 의해 반환 되는 개체입니다.

## <a name="example"></a>예제

이 샘플은 runspace를 사용한를 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 개체가 실행 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 및 [Measure-object](/powershell/module/microsoft.powershell.utility/measure-object) cmdlet.

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

[Windows PowerShell 호스트 응용 프로그램 작성](./writing-a-windows-powershell-host-application.md)