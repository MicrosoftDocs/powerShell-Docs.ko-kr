---
title: Runspace11 샘플 | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6e8a4080bb4fb33f7e0d428e24483b5cfac5c70e
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784931"
---
# <a name="runspace11-sample"></a><span data-ttu-id="3d985-102">Runspace11 샘플</span><span class="sxs-lookup"><span data-stu-id="3d985-102">Runspace11 Sample</span></span>

<span data-ttu-id="3d985-103">이 샘플에서는 [system.object](/dotnet/api/System.Management.Automation.ProxyCommand) 를 사용 하 여 기존 cmdlet을 호출 하지만 사용 가능한 매개 변수 집합을 제한 하는 프록시 명령을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-103">This sample shows how to use the [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span> <span data-ttu-id="3d985-104">프록시 명령은 제한된 runspace를 만드는 데 사용되는 초기 세션 상태에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-104">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span> <span data-ttu-id="3d985-105">따라서 사용자가 프록시 명령을 통해서만 cmdlet의 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-105">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d985-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3d985-106">Requirements</span></span>

<span data-ttu-id="3d985-107">이 샘플에는 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3d985-108">데모</span><span class="sxs-lookup"><span data-stu-id="3d985-108">Demonstrates</span></span>

<span data-ttu-id="3d985-109">이 샘플에서는 다음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="3d985-110">기존 cmdlet의 메타 데이터를 설명 하는 [system.web 메타 데이터](/dotnet/api/System.Management.Automation.CommandMetadata) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-110">Creating a [System.Management.Automation.Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) object that describes the metadata of an existing cmdlet.</span></span>

- <span data-ttu-id="3d985-111">[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-111">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="3d985-112">Cmdlet 메타 데이터를 수정 하 여 cmdlet의 매개 변수를 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-112">Modifying the cmdlet metadata to remove a parameter of the cmdlet.</span></span>

- <span data-ttu-id="3d985-113">[System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체에 cmdlet을 추가 하 고 cmdlet을 전용으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-113">Adding the cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and making the cmdlet private.</span></span>

- <span data-ttu-id="3d985-114">기존 cmdlet을 호출 하지만 제한 된 매개 변수 집합만 노출 하는 프록시 함수를 만드는 경우</span><span class="sxs-lookup"><span data-stu-id="3d985-114">Creating a proxy function that calls the existing cmdlet, but exposes only a restricted set of parameters.</span></span>

- <span data-ttu-id="3d985-115">초기 세션 상태에 프록시 함수를 추가 하는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-115">Adding the proxy function to the initial session state.</span></span>

- <span data-ttu-id="3d985-116">[Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 개체를 사용 하는 [system.web](/dotnet/api/system.management.automation.powershell) . n a m a 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-116">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="3d985-117">제약이 있는 runspace를 보여 주기 위해 [system.object](/dotnet/api/system.management.automation.powershell) 를 사용 하 여 private cmdlet 및 프록시 함수를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-117">Calling the private cmdlet and the proxy function using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to demonstrate the constrained runspace.</span></span>

## <a name="example"></a><span data-ttu-id="3d985-118">예제</span><span class="sxs-lookup"><span data-stu-id="3d985-118">Example</span></span>

<span data-ttu-id="3d985-119">이렇게 하면 제한 된 runspace를 보여 주는 전용 cmdlet에 대 한 프록시 명령이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d985-119">This creates a proxy command for a private cmdlet to demonstrate a constrained runspace.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet. It has been copied
  /// verbatim from the GetProcessSample02.cs sample.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes to act on.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // if (processNames...
    } // ProcessRecord

    #endregion Cmdlet Overrides
  } // GetProcCommand

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace11
  {
    /// <summary>
    /// This shows how to use the ProxyCommand class to create a proxy
    /// command that calls an existing cmdlet, but restricts the set of
    /// available parameters. The proxy command is then added to an initial
    /// session state that is used to create a constrained runspace. This
    /// means that the user can access the cmdlet only through the proxy
    /// command.
    /// </summary>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a CommandMetadata object that describes the metadata of an
    ///    existing cmdlet.
    /// 2. Modifying the cmdlet metadata to remove a parameter of the cmdlet.
    /// 3. Adding the cmdlet to an initial session state and making it private.
    /// 4. Creating a proxy function that calls the existing cmdlet, but exposes
    ///    only a restricted set of parameters.
    /// 6. Adding the proxy function to the initial session state.
    /// 7. Calling the private cmdlet and the proxy function to demonstrate the
    ///    constrained runspace.
    /// </remarks>
    private static void Main()
    {
      // Create a default initial session state. The default initial session state
      // includes all the elements that are provided by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the initial session state.
      SessionStateCmdletEntry cmdletEntry = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(cmdletEntry);

      // Make the cmdlet private so that it is not accessible.
      cmdletEntry.Visibility = SessionStateEntryVisibility.Private;

      // Set the language mode of the initial session state to NoLanguage to
      //prevent users from using language features. Only the invocation of
      // public commands is allowed.
      iss.LanguageMode = PSLanguageMode.NoLanguage;

      // Create the proxy command using cmdlet metadata to expose the
      // get-proc cmdlet.
      CommandMetadata cmdletMetadata = new CommandMetadata(typeof(GetProcCommand));

      // Remove one of the parameters from the command metadata.
      cmdletMetadata.Parameters.Remove("Name");

      // Generate the body of a proxy function that calls the original cmdlet,
      // but does not have the removed parameter.
      string bodyOfProxyFunction = ProxyCommand.Create(cmdletMetadata);

      // Add the proxy function to the initial session state. The name of the proxy
      // function can be the same as the name of the cmdlet, but to clearly
      // demonstrate that the original cmdlet is not available a different name is
      // used for the proxy function.
      iss.Commands.Add(new SessionStateFunctionEntry("get-procProxy", bodyOfProxyFunction));

      // Create the constrained runspace using the initial session state.
      using (Runspace myRunspace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunspace.Open();

        // Call the private cmdlet to demonstrate that it is not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-proc").AddParameter("Name", "*explore*");
            powershell.Invoke();
          }
        }
        catch (CommandNotFoundException e)
        {
          System.Console.WriteLine(
                        "Invoking 'get-proc' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that the -Name parameter is
        // not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-procProxy").AddParameter("Name", "idle");
            powershell.Invoke();
          }
        }
        catch (ParameterBindingException e)
        {
          System.Console.WriteLine(
                        "\nInvoking 'get-procProxy -Name idle' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that it calls into the
        // private cmdlet to retrieve the processes.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunspace;
          powershell.AddCommand("get-procProxy");
          List<Process> processes = new List<Process>(powershell.Invoke<Process>());
          System.Console.WriteLine(
                        "\nInvoking the get-procProxy function called into the get-proc cmdlet and returned {0} processes",
                        processes.Count);
        }

        // Close the runspace to release resources.
        myRunspace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="3d985-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d985-120">See Also</span></span>

[<span data-ttu-id="3d985-121">Windows PowerShell 호스트 애플리케이션 작성</span><span class="sxs-lookup"><span data-stu-id="3d985-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
