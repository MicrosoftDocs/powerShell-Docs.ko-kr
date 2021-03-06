---
ms.date: 09/13/2016
ms.topic: reference
title: 제한된 runspace 만들기
description: 제한된 runspace 만들기
ms.openlocfilehash: 53fee3cc7d8625425bc6a73196aee9eee7f17ed6
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651176"
---
# <a name="creating-a-constrained-runspace"></a>제한된 runspace 만들기

성능 또는 보안상의 이유로, 호스트 응용 프로그램에 사용할 수 있는 Windows PowerShell 명령을 제한 하는 것이 좋습니다. 이렇게 하려면System.Management.Automation.Runspaces.Initialsessionstate를 호출 하 여 빈 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 를 만듭니다 [ . *](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) 메서드를 만든 다음 사용 하려는 명령만 추가 합니다.

 지정 하는 명령만 로드 하는 runspace를 사용 하면 성능이 크게 향상 됩니다.

 [Runspace](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) 의 메서드를 사용 하 여 초기 세션 상태에 대 한 cmdlet을 정의 합니다.

 명령을 비공개로 만들 수도 있습니다. 전용 명령은 호스트 응용 프로그램에서 사용할 수 있지만 응용 프로그램의 사용자는 사용할 수 없습니다.

## <a name="adding-commands-to-an-empty-runspace"></a>빈 runspace에 명령 추가

 다음 예제에서는 빈 InitialSessionState을 만들고 여기에 명령을 추가 하는 방법을 보여 줍니다.

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

## <a name="making-commands-private"></a>전용 명령 만들기

 또한 [해당 속성을 system.object로](/dotnet/api/System.Management.Automation.CommandInfo.Visibility) 설정 하 여 명령을 전용으로 설정할 수 있습니다 .이 속성은 [system.object](/dotnet/api/System.Management.Automation.SessionStateEntryVisibility) 로 설정 **합니다.** 호스트 응용 프로그램 및 기타 명령은 해당 명령을 호출할 수 있지만 응용 프로그램의 사용자는 사용할 수 없습니다. 다음 예제에서 [Get ChildItem](/powershell/module/Microsoft.PowerShell.Management/Get-ChildItem) 명령은 private입니다.

```csharp
defaultSessionState = InitialSessionState.CreateDefault();
commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;

this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
this.runspace.Open();
```

## <a name="see-also"></a>참고 항목

 [InitialSessionState 만들기](./creating-an-initialsessionstate.md)
