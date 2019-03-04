---
title: Runspace02 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7630bb63-ef39-4abd-b795-8000f984c1e5
caps.latest.revision: 9
ms.openlocfilehash: 6352169cffbb8a8bf59a42f79979f5003c150fa4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56854289"
---
# <a name="runspace02-sample"></a><span data-ttu-id="346dd-102">Runspace02 샘플</span><span class="sxs-lookup"><span data-stu-id="346dd-102">Runspace02 Sample</span></span>

<span data-ttu-id="346dd-103">이 샘플에 사용 하는 방법을 보여 줍니다 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 실행 하는 클래스를 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 하 고 [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet 동기적으로.</span><span class="sxs-lookup"><span data-stu-id="346dd-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span> <span data-ttu-id="346dd-104">[Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 반환 [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) 로컬 컴퓨터에서 실행 중인 각 프로세스에 대 한 개체와 `Sort-Object` 기반으로 개체를 정렬 해당 [ System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [System.Diagnostics.Process.Id\*](/dotnet/api/System.Diagnostics.Process.Id) property.</span></span> <span data-ttu-id="346dd-105">이러한 명령의 결과 사용 하 여 표시 되는 [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-105">The results of these commands is displayed by using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

## <a name="requirements"></a><span data-ttu-id="346dd-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="346dd-106">Requirements</span></span>

<span data-ttu-id="346dd-107">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="346dd-108">시연</span><span class="sxs-lookup"><span data-stu-id="346dd-108">Demonstrates</span></span>

<span data-ttu-id="346dd-109">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="346dd-110">만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 명령을 실행 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run commands.</span></span>

- <span data-ttu-id="346dd-111">파이프라인에 명령 추가 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-111">Adding commands to the pipeline of [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="346dd-112">동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-112">Running the commands synchronously.</span></span>

- <span data-ttu-id="346dd-113">사용 하는 [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) Windows Forms 응용 프로그램에서 명령의 출력을 표시 하는 컨트롤입니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-113">Using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control to display the output of the commands in a Windows Forms application.</span></span>

## <a name="example"></a><span data-ttu-id="346dd-114">예제</span><span class="sxs-lookup"><span data-stu-id="346dd-114">Example</span></span>

<span data-ttu-id="346dd-115">이 샘플을 실행 합니다 [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) 하 고 [Sort-object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlet Windows PowerShell에서 제공 하는 기본 runspace에 동기적으로.</span><span class="sxs-lookup"><span data-stu-id="346dd-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="346dd-116">출력을 사용 하 여 폼에 표시 됩니다는 [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="346dd-116">The output is displayed in a form using a [System.Windows.Forms.Datagridview](/dotnet/api/System.Windows.Forms.DataGridView) control.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using System.Windows.Forms;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace02
  {
    /// <summary>
    /// This method creates the form where the output is displayed.
    /// </summary>
    private static void CreateForm()
    {
      Form form = new Form();
      DataGridView grid = new DataGridView();
      form.Controls.Add(grid);
      grid.Dock = DockStyle.Fill;

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddCommand("get-process").AddCommand("sort-object").AddArgument("ID");
        if (Runspace.DefaultRunspace == null)
        {
          Runspace.DefaultRunspace = powershell.Runspace;
        }

        Collection<PSObject> results = powershell.Invoke();

        // The generic collection needs to be re-wrapped in an ArrayList
        // for data-binding to work.
        ArrayList objects = new ArrayList();
        objects.AddRange(results);

        // The DataGridView will use the PSObjectTypeDescriptor type
        // to retrieve the properties.
        grid.DataSource = objects;
      }

      form.ShowDialog();
    }

    /// <summary>
    /// This sample uses a PowerShell object to run the Get-Process
    /// and Sort-Object cmdlets synchronously. Windows Forms and
    /// data binding are then used to display the results in a
    /// DataGridView control.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding commands and arguments to the pipeline of
    ///    the PowerShell object.
    /// 3. Running the commands synchronously.
    /// 4. Using a DataGridView control to display the output
    ///    of the commands in a Windows Forms application.
    /// </remarks>
    private static void Main(string[] args)
    {
      Runspace02.CreateForm();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="346dd-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="346dd-117">See Also</span></span>

[<span data-ttu-id="346dd-118">Windows PowerShell 호스트 응용 프로그램 작성</span><span class="sxs-lookup"><span data-stu-id="346dd-118">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)