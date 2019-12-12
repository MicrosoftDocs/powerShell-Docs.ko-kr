---
title: Runspace01 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367422"
---
# <a name="runspace01-sample"></a>Runspace01 샘플

이 샘플에서는 [system.object](/dotnet/api/system.management.automation.powershell) 를 사용 하 여 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet을 동기적으로 실행 하는 방법을 보여 줍니다. 이 [cmdlet은](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 로컬 컴퓨터에서 실행 되는 각 프로세스에 대해 [system.object](/dotnet/api/System.Diagnostics.Process) 개체를 반환 합니다. 그런 다음 반환 된 개체에서 [Processname *](/dotnet/api/System.Diagnostics.Process.ProcessName) 및 [handlecount) *](/dotnet/api/System.Diagnostics.Process.Handlecount) 속성의 값을 추출 하 여 콘솔 창에 표시 합니다.

## <a name="requirements"></a>요구 사항

 이 샘플에는 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

- 명령을 실행 하기 위한 [system.object](/dotnet/api/system.management.automation.powershell) 개체를 만듭니다.

- [System.object](/dotnet/api/system.management.automation.powershell) 의 파이프라인에 명령을 추가 하는 중입니다.

- 동기적으로 명령을 실행 합니다.

- [System.object](/dotnet/api/System.Management.Automation.PSObject) 를 사용 하 여 명령에 의해 반환 되는 개체에서 속성을 추출 합니다.

## <a name="example"></a>예제

 이 샘플은 Windows PowerShell에서 제공 하는 기본 runspace에서 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet을 동기적으로 실행 합니다.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>참고 항목
