---
title: Runspace05 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1685cfc4-b32c-4bed-b221-e0c4482db955
caps.latest.revision: 9
ms.openlocfilehash: eb227b5fa5e91f59b6fc99981ff5affca1cf63fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082705"
---
# <a name="runspace05-sample"></a><span data-ttu-id="8a2df-102">Runspace05 샘플</span><span class="sxs-lookup"><span data-stu-id="8a2df-102">Runspace05 Sample</span></span>

<span data-ttu-id="8a2df-103">이 샘플에서는 스냅인을 추가 하는 방법을 보여 줍니다.는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) runspace를 열 때 스냅인의 cmdlet을 사용할 수 있도록 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-103">This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="8a2df-104">스냅인 Get-proc cmdlet을 제공 (정의한 합니다 [GetProcessSample01 샘플](../cmdlet/getprocesssample01-sample.md))를 사용 하 여 동기적으로 실행 되는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체.</span><span class="sxs-lookup"><span data-stu-id="8a2df-104">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a2df-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8a2df-105">Requirements</span></span>

<span data-ttu-id="8a2df-106">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="8a2df-107">데모</span><span class="sxs-lookup"><span data-stu-id="8a2df-107">Demonstrates</span></span>

<span data-ttu-id="8a2df-108">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="8a2df-109">만들기는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="8a2df-110">스냅인을 추가 합니다 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-110">Adding the snap-in to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="8a2df-111">만들기는 [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 사용 하는 개체를 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="8a2df-112">만들기는 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) runspace를 사용 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="8a2df-113">스냅인의 get proc cmdlet의 파이프라인에 추가 합니다 [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-113">Adding the snap-in's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="8a2df-114">동기적으로 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-114">Running the command synchronously.</span></span>

- <span data-ttu-id="8a2df-115">속성에서 추출 합니다 [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) 명령에 의해 반환 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="8a2df-116">예제</span><span class="sxs-lookup"><span data-stu-id="8a2df-116">Example</span></span>

<span data-ttu-id="8a2df-117">이 샘플에서는 사용 하는 runspace 만듭니다는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) runspace를 열 때 사용할 수 있는 요소를 정의 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="8a2df-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="8a2df-118">이 샘플에서는 Get-proc cmdlet을 정의 하는 스냅인에 추가 됩니다 초기 세션 상태.</span><span class="sxs-lookup"><span data-stu-id="8a2df-118">In this sample, a snap-in that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }
      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="8a2df-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8a2df-119">See Also</span></span>

[<span data-ttu-id="8a2df-120">Windows PowerShell 호스트 응용 프로그램 작성</span><span class="sxs-lookup"><span data-stu-id="8a2df-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)