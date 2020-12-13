---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace08 샘플
description: Runspace08 샘플
ms.openlocfilehash: ce60e85919a78143f26ff695a9c9104c86cd4f6a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657653"
---
# <a name="runspace08-sample"></a><span data-ttu-id="e202f-103">Runspace08 샘플</span><span class="sxs-lookup"><span data-stu-id="e202f-103">Runspace08 Sample</span></span>

<span data-ttu-id="e202f-104">이 샘플에서는 명령과 인수를 [system.object](/dotnet/api/system.management.automation.powershell) 의 파이프라인에 추가 하는 방법과 명령을 동기적으로 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-104">This sample shows how to add commands and arguments to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

## <a name="requirements"></a><span data-ttu-id="e202f-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e202f-105">Requirements</span></span>

<span data-ttu-id="e202f-106">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e202f-107">데모</span><span class="sxs-lookup"><span data-stu-id="e202f-107">Demonstrates</span></span>

<span data-ttu-id="e202f-108">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e202f-109">Runspacefactory 클래스를 사용 하 여 [runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 개체를 만듭니다. [runspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-109">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object by using the [System.Management.Automation.Runspaces.Runspacefactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) class.</span></span>

- <span data-ttu-id="e202f-110">Runspace를 사용 하는 [system.web. Powershell](/dotnet/api/system.management.automation.powershell) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="e202f-111">Cmdlet을 [system.web. Powershell](/dotnet/api/system.management.automation.powershell) 개체의 파이프라인에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-111">Adding cmdlets to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e202f-112">Cmdlet을 동기적으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-112">Running the cmdlets synchronously.</span></span>

- <span data-ttu-id="e202f-113">명령에 의해 반환 되는 [system.web. PSObject](/dotnet/api/System.Management.Automation.PSObject) 개체에서 속성을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-113">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="e202f-114">예제</span><span class="sxs-lookup"><span data-stu-id="e202f-114">Example</span></span>

<span data-ttu-id="e202f-115">이 샘플에서는 [system.object](/dotnet/api/system.management.automation.powershell) 및 [Sort](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) 개체 cmdlet을 사용 하 여 [프로세스](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="e202f-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e202f-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e202f-116">See Also</span></span>

[<span data-ttu-id="e202f-117">Windows PowerShell 호스트 애플리케이션 작성</span><span class="sxs-lookup"><span data-stu-id="e202f-117">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
