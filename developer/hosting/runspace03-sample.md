---
title: Runspace03 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 31df99d7-6954-4fdc-b6f5-06ecba094f43
caps.latest.revision: 8
ms.openlocfilehash: fe513a47908fc3020895fcb26f1840faad76210a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857299"
---
# <a name="runspace03-sample"></a>Runspace03 샘플

이 샘플에서는 사용 하는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 동기적으로 스크립트를 실행 하는 클래스 및 종료 되지 않는 오류를 처리 하는 방법입니다. 스크립트는 프로세스 이름 목록을 받은 다음 해당 프로세스를 검색합니다. 스크립트를 실행할 때 생성된 종료되지 않는 오류를 포함하여 스크립트의 결과가 콘솔 창에 표시됩니다.

## <a name="requirements"></a>요구 사항

이 샘플 Windows PowerShell 2.0이 필요 합니다.

## <a name="demonstrates"></a>시연

이 샘플에는 다음 방법을 보여 줍니다.

- 만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 스크립트를 실행 하는 개체입니다.

- 파이프라인에 스크립트를 추가 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.

- 전달 입력된 개체를 스크립트 호출 프로그램 으로부터 합니다.

- 스크립트를 동기적으로 실행 합니다.

- 사용 하 여 [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) 개체를 추출 하 고 스크립트에서 반환한 개체의 속성을 표시 합니다.

- 검색 하 고 스크립트를 실행할 때 생성 된 오류 레코드를 표시 합니다.

## <a name="example"></a>예제

이 샘플 스크립트를 동기적으로 Windows PowerShell에서 제공 하는 기본 runspace에서 실행 됩니다. 스크립트 및 생성 된 종료 되지 않는 오류 출력을 콘솔 창에 표시 됩니다.

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a>참고 항목

[Windows PowerShell 호스트 응용 프로그램 작성](./writing-a-windows-powershell-host-application.md)