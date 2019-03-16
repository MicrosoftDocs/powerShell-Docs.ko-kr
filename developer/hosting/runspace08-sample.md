---
title: Runspace08 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1100d91d-249d-4af7-9854-2d6a423ac2f4
caps.latest.revision: 7
ms.openlocfilehash: 70577a6a42ce26e9791360fa30baae9d7a492daf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057742"
---
# <a name="runspace08-sample"></a>Runspace08 샘플

이 샘플의 파이프라인에 명령 및 인수를 추가 하는 방법을 보여 줍니다는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체와 동기적으로 명령을 실행 하는 방법입니다.

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

이 샘플이 실행 되는 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 하 고 [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet를 사용 하 여를 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace08
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands. The
    /// PowerShell object builds a pipeline that include the get-process cmdlet,
    /// which is then piped to the sort-object cmdlet. Parameters are added to the
    /// sort-object cmdlet to sort the HandleCount property in descending order.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates:
    /// 1. Creating a PowerShell object
    /// 2. Adding individual commands to the PowerShell object.
    /// 3. Adding parameters to the commands.
    /// 4. Running the pipeline of the PowerShell object synchronously.
    /// 5. Working with PSObject objects to extract properties
    ///    from the objects returned by the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      Collection<PSObject> results; // Holds the result of the pipeline execution.

      // Create the PowerShell object. Notice that no runspace is specified so a
      // new default runspace is used.
      PowerShell powershell = PowerShell.Create();

      // Use the using statement so that we can dispose of the PowerShell object
      // when we are done.
      using (powershell)
      {
        // Add the get-process cmdlet to the pipeline of the PowerShell object.
        powershell.AddCommand("get-process");

        // Add the sort-object cmdlet and its parameters to the pipeline of
        // the PowerShell object so that we can sort the HandleCount property
        //  in descending order.
        powershell.AddCommand("sort-object").AddParameter("descending").AddParameter("property", "handlecount");

        // Run the commands of the pipeline synchronously.
        results = powershell.Invoke();
      }

      // Even after disposing of the PowerShell object, we still
      // need to set the powershell variable to null so that the
      // garbage collector can clean it up.
      powershell = null;

      Console.WriteLine("Process              HandleCount");
      Console.WriteLine("--------------------------------");

      // Display the results returned by the commands.
      foreach (PSObject result in results)
      {
        Console.WriteLine(
                          "{0,-20} {1}",
                          result.Members["ProcessName"].Value,
                          result.Members["HandleCount"].Value);
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 호스트 응용 프로그램 작성](./writing-a-windows-powershell-host-application.md)