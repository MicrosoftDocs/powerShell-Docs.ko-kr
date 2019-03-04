---
title: 제한 된 runspace 만들기 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59125e65-7030-40bb-9926-756120b2d952
caps.latest.revision: 5
ms.openlocfilehash: 3c70296cb22c325ace10dc04c8b1fd941742857b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862999"
---
# <a name="creating-a-constrained-runspace"></a><span data-ttu-id="d4fba-102">제한된 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="d4fba-102">Creating a constrained runspace</span></span>

<span data-ttu-id="d4fba-103">성능 또는 보안상의 이유로 호스트 응용 프로그램에 사용할 수 있는 Windows PowerShell 명령을 제한 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-103">For performance or security reasons, you might want to restrict the Windows PowerShell commands available to your host application.</span></span> <span data-ttu-id="d4fba-104">이 작업을 수행 하려면 빈 만들어야 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 를 호출 하 여 합니다 [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) 메서드 사용할 수 있게 할 명령만 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-104">To do this you create an empty [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) by calling the [System.Management.Automation.Runspaces.Initialsessionstate.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add only the commands you want available.</span></span>

 <span data-ttu-id="d4fba-105">지정 하는 명령만 로드 하는 runspace를 사용 하 여 성능이 크게 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-105">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

 <span data-ttu-id="d4fba-106">메서드를 사용 합니다 [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) 초기 세션 상태에 대 한 cmdlet을 정의 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-106">You use the methods of the [System.Management.Automation.Runspaces.Sessionstatecmdletentry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>

 <span data-ttu-id="d4fba-107">개인 명령을도 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-107">You can also make commands private.</span></span> <span data-ttu-id="d4fba-108">응용 프로그램의 사용자는 호스트 응용 프로그램을 아니라 개인 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-108">Private commands can be used by the host application, but not by users of the application.</span></span>

## <a name="adding-commands-to-an-empty-runspace"></a><span data-ttu-id="d4fba-109">빈 runspace에 명령 추가</span><span class="sxs-lookup"><span data-stu-id="d4fba-109">Adding commands to an empty runspace</span></span>

 <span data-ttu-id="d4fba-110">다음 예제에는 빈 InitialSessionState 만들고에 명령을 추가 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-110">The following example demonstrates how to create an empty InitialSessionState and add commands to it.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using Microsoft.PowerShell.Commands;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class Runspace10b
  {
    /// <summary>
    /// This sample shows how to create an empty initial session state,
    /// how to add commands to the session state, and then how to create a
    /// runspace that has only those two commands. A PowerShell object
    /// is used to run the Get-Command cmdlet to show that only two commands
    /// are available.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create an empty InitialSessionState and then add two commands.
      InitialSessionState iss = InitialSessionState.Create();

      // Add the Get-Process and Get-Command cmdlets to the session state.
      SessionStateCmdletEntry ssce1 = new SessionStateCmdletEntry(
                                                            "get-process",
                                                            typeof(GetProcessCommand),
                                                            null);
      iss.Commands.Add(ssce1);

      SessionStateCmdletEntry ssce2 = new SessionStateCmdletEntry(
                                                            "get-command",
                                                            typeof(GetCommandCommand),
                                                            null);
      iss.Commands.Add(ssce2);

      // Create a runspace.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Create a pipeline with the Get-Command command.
          powershell.AddCommand("get-command");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Verb                 Noun");
          Console.WriteLine("----------------------------");

          // Display each result object.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                             "{0,-20} {1}",
                             result.Members["verb"].Value,
                             result.Members["Noun"].Value);
          }
        }

        // Close the runspace and release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="making-commands-private"></a><span data-ttu-id="d4fba-111">개인 만들기 명령</span><span class="sxs-lookup"><span data-stu-id="d4fba-111">Making commands private</span></span>

 <span data-ttu-id="d4fba-112">또한 가능 명령을 개인 설정 하 여의 [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) 속성을 [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) .</span><span class="sxs-lookup"><span data-stu-id="d4fba-112">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private).</span></span> <span data-ttu-id="d4fba-113">호스트 응용 프로그램 및 기타 명령에는 명령을 호출할 수 있지만 응용 프로그램의 사용자 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-113">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="d4fba-114">다음 예제에서는 [Get-childitem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) 개인 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-114">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>
<span data-ttu-id="d4fba-115">또한 가능 명령을 개인 설정 하 여의 [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) 속성을 [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private) .</span><span class="sxs-lookup"><span data-stu-id="d4fba-115">You can also make a command private, by setting it's [System.Management.Automation.Commandinfo.Visibility\*](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) property to [System.Management.Automation.Sessionstateentryvisibility.Private](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility.Private).</span></span> <span data-ttu-id="d4fba-116">호스트 응용 프로그램 및 기타 명령에는 명령을 호출할 수 있지만 응용 프로그램의 사용자 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-116">The host application and other commands can call that command, but the user of the application cannot.</span></span> <span data-ttu-id="d4fba-117">다음 예제에서는 [Get-childitem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) 개인 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="d4fba-117">In the following example, the [Get-ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) command is private.</span></span>

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a><span data-ttu-id="d4fba-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4fba-118">See Also</span></span>

 [<span data-ttu-id="d4fba-119">InitialSessionState 만들기</span><span class="sxs-lookup"><span data-stu-id="d4fba-119">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
