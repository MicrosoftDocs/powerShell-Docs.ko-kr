---
title: Runspace09 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f19f12c0-82e9-42f6-a7df-76c45b733855
caps.latest.revision: 8
ms.openlocfilehash: d78c865b869f802c7ebe2743942b6f21681de4b3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082603"
---
# <a name="runspace09-sample"></a><span data-ttu-id="4515d-102">Runspace09 샘플</span><span class="sxs-lookup"><span data-stu-id="4515d-102">Runspace09 Sample</span></span>

<span data-ttu-id="4515d-103">이 샘플의 파이프라인에 스크립트를 추가 하는 방법을 보여 줍니다는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체 및 스크립트를 비동기적으로 실행 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-103">This sample shows how to add a script to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span> <span data-ttu-id="4515d-104">이벤트는 스크립트의 출력을 처리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-104">Events are used to handle the output of the script.</span></span>

## <a name="requirements"></a><span data-ttu-id="4515d-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4515d-105">Requirements</span></span>

<span data-ttu-id="4515d-106">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4515d-107">데모</span><span class="sxs-lookup"><span data-stu-id="4515d-107">Demonstrates</span></span>

<span data-ttu-id="4515d-108">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="4515d-109">만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) runspace를 사용 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="4515d-110">파이프라인 스크립트를 추가 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-110">Adding a script the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="4515d-111">사용 하는 [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) 파이프라인을 비동기적으로 실행 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-111">Using the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) method to run the pipeline asynchronously.</span></span>

- <span data-ttu-id="4515d-112">이벤트를 사용 하는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 스크립트의 출력을 처리 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-112">Using the events of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to process the output of the script.</span></span>

- <span data-ttu-id="4515d-113">사용 하 여 [System.Management.Automation.Powershell.Stop\*](/dotnet/api/System.Management.Automation.PowerShell.Stop) 파이프라인의 호출을 중단 하는 방법.</span><span class="sxs-lookup"><span data-stu-id="4515d-113">Using the [System.Management.Automation.Powershell.Stop\*](/dotnet/api/System.Management.Automation.PowerShell.Stop) method to interrupt the invocation of the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="4515d-114">예제</span><span class="sxs-lookup"><span data-stu-id="4515d-114">Example</span></span>

<span data-ttu-id="4515d-115">1에서 10 각 숫자 간의 지연을 사용 하 여 숫자를 생성 하는 스크립트를 실행 하려면이 샘플 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-115">This sample runs to run a script that generates the numbers from 1 to 10 with delays between each number.</span></span> <span data-ttu-id="4515d-116">스크립트를 비동기적으로 실행 하 고 이벤트 출력을 처리 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4515d-116">The script is run asynchronously and events are used to handle the output.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace09
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run a
    /// script that generates the numbers from 1 to 10 with delays
    /// between each number. The pipeline of the PowerShell object
    /// is run asynchronously and events are used to handle the output.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Using the BeginInvoke method to run the pipeline asynchronously.
    /// 4. Using the events of the PowerShell object to process the
    ///    output of the script.
    /// 5. Using the PowerShell.Stop() method to interrupt the invocation of
    ///    the pipeline.
    /// </remarks>
    private static void Main(string[] args)
    {
      Console.WriteLine("Print the numbers from 1 to 10. Hit any key to halt processing\n");

      using (PowerShell powershell = PowerShell.Create())
      {
        // Add a script to the PowerShell object. The script generates the
        // numbers from 1 to 10 in half second intervals.
        powershell.AddScript("1..10 | foreach {$_ ; start-sleep -milli 500}");

        // Add the event handlers.  If we did not care about hooking the DataAdded
        // event, we would let BeginInvoke create the output stream for us.
        PSDataCollection<PSObject> output = new PSDataCollection<PSObject>();
        output.DataAdded += new EventHandler<DataAddedEventArgs>(Output_DataAdded);
        powershell.InvocationStateChanged += new EventHandler<PSInvocationStateChangedEventArgs>(Powershell_InvocationStateChanged);

        // Invoke the pipeline asynchronously.
        IAsyncResult asyncResult = powershell.BeginInvoke<PSObject, PSObject>(null, output);

        // Wait for things to happen. If the user hits a key before the
        // script has completed, then call the PowerShell Stop() method
        // to halt processing.
        Console.ReadKey();
        if (powershell.InvocationStateInfo.State != PSInvocationState.Completed)
        {
          // Stop the invocation of the pipeline.
          Console.WriteLine("\nStopping the pipeline!\n");
          powershell.Stop();

          // Wait for the Windows PowerShell state change messages to be displayed.
          System.Threading.Thread.Sleep(500);
          Console.WriteLine("\nPress a key to exit");
          Console.ReadKey();
        }
      }
    }

    /// <summary>
    /// The output data added event handler. This event is called when
    /// data is added to the output pipe. It reads the data that is
    /// available and displays it on the console.
    /// </summary>
    /// <param name="sender">The output pipe this event is associated with.</param>
    /// <param name="e">Parameter is not used.</param>
    private static void Output_DataAdded(object sender, DataAddedEventArgs e)
    {
      PSDataCollection<PSObject> myp = (PSDataCollection<PSObject>)sender;

      Collection<PSObject> results = myp.ReadAll();
      foreach (PSObject result in results)
      {
        Console.WriteLine(result.ToString());
      }
    }

    /// <summary>
    /// This event handler is called when the pipeline state is changed.
    /// If the state change is to Completed, the handler issues a message
    /// asking the user to exit the program.
    /// </summary>
    /// <param name="sender">This parameter is not used.</param>
    /// <param name="e">The PowerShell state information.</param>
    private static void Powershell_InvocationStateChanged(object sender, PSInvocationStateChangedEventArgs e)
    {
      Console.WriteLine("PowerShell object state changed: state: {0}\n", e.InvocationStateInfo.State);
      if (e.InvocationStateInfo.State == PSInvocationState.Completed)
      {
        Console.WriteLine("Processing completed, press a key to exit!");
      }
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="4515d-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4515d-117">See Also</span></span>

[<span data-ttu-id="4515d-118">Windows PowerShell 호스트 응용 프로그램 작성</span><span class="sxs-lookup"><span data-stu-id="4515d-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)