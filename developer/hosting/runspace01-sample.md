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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082790"
---
# <a name="runspace01-sample"></a>Runspace01 샘플

이 샘플에 사용 하는 방법을 보여 줍니다 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 실행 하는 클래스는 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet 동기적으로 합니다. 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 반환 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 로컬 컴퓨터에서 실행 중인 각 프로세스에 대 한 개체입니다. 값을 [System.Diagnostics.Process.Processname*](/dotnet/api/System.Diagnostics.Process.ProcessName) 하 고 [System.Diagnostics.Process.Handlecount*](/dotnet/api/System.Diagnostics.Process.Handlecount) 속성 다음 반환된 된 개체에서 추출 되 고 콘솔에 표시 창입니다.

## <a name="requirements"></a>요구 사항

 이 샘플 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>데모

- 만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 명령을 실행 하는 개체입니다.

- 파이프라인에 명령을 추가 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.

- 동기적으로 명령을 실행 합니다.

- 사용 하 여 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 명령에 의해 반환 된 개체에서 속성을 추출 하는 개체입니다.

## <a name="example"></a>예제

 이 샘플을 실행 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet Windows PowerShell에서 제공 하는 기본 runspace에 동기적으로 합니다.

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
