---
title: Runspace01 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 1ac286512f3cb3b97a6b3179c9dd45f1fefe1ecf
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87772198"
---
# <a name="runspace01-sample"></a><span data-ttu-id="86bc0-102">Runspace01 샘플</span><span class="sxs-lookup"><span data-stu-id="86bc0-102">Runspace01 Sample</span></span>

<span data-ttu-id="86bc0-103">이 샘플에서는 [system.object](/dotnet/api/system.management.automation.powershell) 를 사용 하 여 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet을 동기적으로 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="86bc0-104">이 [cmdlet은](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 로컬 컴퓨터에서 실행 되는 각 프로세스에 대해 [system.object](/dotnet/api/System.Diagnostics.Process) 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="86bc0-105">그런 다음 반환 된 개체에서 [Processname \*](/dotnet/api/System.Diagnostics.Process.ProcessName) 및 [handlecount) \*](/dotnet/api/System.Diagnostics.Process.Handlecount) 속성의 값을 추출 하 여 콘솔 창에 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="86bc0-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="86bc0-106">Requirements</span></span>

 <span data-ttu-id="86bc0-107">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="86bc0-108">데모</span><span class="sxs-lookup"><span data-stu-id="86bc0-108">Demonstrates</span></span>

- <span data-ttu-id="86bc0-109">명령을 실행 하기 위한 [system.object](/dotnet/api/system.management.automation.powershell) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="86bc0-110">[System.object](/dotnet/api/system.management.automation.powershell) 의 파이프라인에 명령을 추가 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="86bc0-111">동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-111">Running the command synchronously.</span></span>

- <span data-ttu-id="86bc0-112">[System.object](/dotnet/api/System.Management.Automation.PSObject) 를 사용 하 여 명령에 의해 반환 되는 개체에서 속성을 추출 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-112">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="86bc0-113">예제</span><span class="sxs-lookup"><span data-stu-id="86bc0-113">Example</span></span>

 <span data-ttu-id="86bc0-114">이 샘플은 Windows PowerShell에서 제공 하는 기본 runspace에서 [Get Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet을 동기적으로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="86bc0-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="86bc0-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86bc0-115">See Also</span></span>
