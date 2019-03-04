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
ms.openlocfilehash: c156b2d6a7e7d3fcbd1679d2d61c94f31be0f76a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854729"
---
# <a name="runspace07-sample"></a><span data-ttu-id="ece31-102">Runspace07 샘플</span><span class="sxs-lookup"><span data-stu-id="ece31-102">Runspace07 Sample</span></span>

<span data-ttu-id="ece31-103">이 샘플에서는 runspace를 만들고 해당 runspace를 사용 하 여 두 개의 cmdlet을 사용 하 여 동기적으로 실행 하는 방법을 보여 줍니다.는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-103">This sample shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="ece31-104">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ece31-104">Requirements</span></span>

<span data-ttu-id="ece31-105">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-105">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ece31-106">시연</span><span class="sxs-lookup"><span data-stu-id="ece31-106">Demonstrates</span></span>

<span data-ttu-id="ece31-107">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-107">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ece31-108">만들기는 [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 사용 하 여 개체를 [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-108">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object by using the [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) class.</span></span>

- <span data-ttu-id="ece31-109">만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) runspace를 사용 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="ece31-110">Cmdlet의 파이프라인에 추가 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-110">Adding cmdlets to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="ece31-111">Cmdlet을 동기적으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-111">Running the cmdlets synchronously.</span></span>

- <span data-ttu-id="ece31-112">속성에서 추출 합니다 [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) 명령에 의해 반환 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ece31-112">Extracting properties from the [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="ece31-113">예제</span><span class="sxs-lookup"><span data-stu-id="ece31-113">Example</span></span>

<span data-ttu-id="ece31-114">이 샘플은 runspace를 사용한를 [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) 개체가 실행 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 및 [Measure-object](/powershell/module/microsoft.powershell.utility/measure-object) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ece31-114">This sample creates a runspace that used by a [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) object to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Measure-Object](/powershell/module/microsoft.powershell.utility/measure-object) cmdlets.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ece31-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ece31-115">See Also</span></span>

[<span data-ttu-id="ece31-116">Windows PowerShell 호스트 응용 프로그램 작성</span><span class="sxs-lookup"><span data-stu-id="ece31-116">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)