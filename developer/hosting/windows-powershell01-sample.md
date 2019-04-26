---
title: Windows PowerShell01 샘플 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f607a5ad-5372-4392-b2dc-ef3532fabd0f
caps.latest.revision: 9
ms.openlocfilehash: 7fafbc6bc19082abb8f37b68c031e0995bf879f6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082535"
---
# <a name="windows-powershell01-sample"></a><span data-ttu-id="e393f-102">Windows PowerShell01 샘플</span><span class="sxs-lookup"><span data-stu-id="e393f-102">Windows PowerShell01 Sample</span></span>

<span data-ttu-id="e393f-103">이 샘플에서는 사용 하는 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) runspace의 기능을 제한 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-103">This sample shows how to use an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to limit the functionality of a runspace.</span></span> <span data-ttu-id="e393f-104">이 샘플의 출력에 runspace, 개인용으로 cmdlet을 표시 하는 방법, 추가 하는 방법 및 제거 cmdlet 및 공급자, 언어 모드를 제한 하는 방법을 보여 줍니다. 프록시 명령을 등을 추가 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-104">The output of this sample demonstrates how to restrict the language mode of the runspace, how to mark a cmdlet as private, how to add and remove cmdlets and providers, how to add a proxy command, and more.</span></span> <span data-ttu-id="e393f-105">이 샘플 runspace를 프로그래밍 방식으로 제한 하는 방법에 중점적으로 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-105">This sample concentrates on how to restrict the runspace programmatically.</span></span> <span data-ttu-id="e393f-106">제한 된 runspace에 대 한 스크립팅 대안 $ExecutionContext.SessionState.LanguageMode 및 PSSessionConfiguration 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-106">Scripting alternatives to restricting the runspace include the $ExecutionContext.SessionState.LanguageMode and PSSessionConfiguration commands.</span></span>

## <a name="requirements"></a><span data-ttu-id="e393f-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e393f-107">Requirements</span></span>

<span data-ttu-id="e393f-108">이 샘플 Windows PowerShell 2.0이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e393f-109">데모</span><span class="sxs-lookup"><span data-stu-id="e393f-109">Demonstrates</span></span>

<span data-ttu-id="e393f-110">이 샘플에는 다음 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-110">This sample demonstrates the following:</span></span>

- <span data-ttu-id="e393f-111">언어를 설정 하 여 제한 된 [System.Management.Automation.Runspaces.Initialsessionstate.Languagemode](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.LanguageMode) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-111">Restricting the language by setting the [System.Management.Automation.Runspaces.Initialsessionstate.Languagemode](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.LanguageMode) property.</span></span>

- <span data-ttu-id="e393f-112">별칭을 사용 하 여 초기 세션 상태에 추가 된 [System.Management.Automation.Runspaces.Sessionstatealiasentry? Displayproperty =](/dotnet/api/System.Management.Automation.Runspaces.SessionStateAliasEntry) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-112">Adding aliases to the initial session state by using a [System.Management.Automation.Runspaces.Sessionstatealiasentry?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Runspaces.SessionStateAliasEntry) object.</span></span>

- <span data-ttu-id="e393f-113">개인으로 명령을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-113">Marking commands as private.</span></span>

- <span data-ttu-id="e393f-114">사용 하 여 초기 세션 상태에서 공급자를 제거 합니다 [System.Management.Automation.Runspaces.Initialsessionstate.Providers](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Providers) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-114">Removing providers from the initial session state by using the [System.Management.Automation.Runspaces.Initialsessionstate.Providers](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Providers) property.</span></span>

- <span data-ttu-id="e393f-115">사용 하 여 초기 세션 상태에서 명령을 제거 합니다 [System.Management.Automation.Runspaces.Initialsessionstate.Commands](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Commands) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-115">Removing commands from the initial session state by using the [System.Management.Automation.Runspaces.Initialsessionstate.Commands](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Commands) property.</span></span>

- <span data-ttu-id="e393f-116">명령 및 공급자를 추가 합니다 [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-116">Adding commands and providers to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

## <a name="example"></a><span data-ttu-id="e393f-117">예제</span><span class="sxs-lookup"><span data-stu-id="e393f-117">Example</span></span>

<span data-ttu-id="e393f-118">이 샘플에서는 runspace의 기능을 제한 하는 여러 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e393f-118">This sample shows several ways to limit the functionality of a runspace.</span></span>

```csharp
namespace Sample
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class PowerShell01
  {
    /// <summary>
    /// The runspace used to run commands.
    /// </summary>
    private Runspace runspace;

    /// <summary>
    /// Return the first index of the entry in <paramref name="entries"/>
    /// with the name <paramref name="name"/>. Return -1 if it is not found.
    /// </summary>
    /// <typeparam name="T">Type of ConstrainedSessionStateEntry</typeparam>
    /// <param name="entries">Collection of entries to search for <paramref name="name"/> in.</param>
    /// <param name="name">Named of the entry we are looking for</param>
    /// <returns>
    /// The first index of the entry in <paramref name="entries"/> with the
    /// name <paramref name="name"/>, or return -1 if it is not found.
    /// </returns>
    private static int GetIndexOfEntry<T>(
            InitialSessionStateEntryCollection<T> entries,
            string name) where T : ConstrainedSessionStateEntry
    {
      int foundIndex = 0;
      foreach (T entry in entries)
      {
        if (entry.Name.Equals(name, StringComparison.OrdinalIgnoreCase))
        {
          return foundIndex;
        }

        foundIndex++;
      }

      return -1;
    }

    /// <summary>
    /// Run commands to demonstrate the ways to constrain the runspace.
    /// </summary>
    /// <param name="args">This parameter is unused.</param>
    private static void Main(string[] args)
    {
      new PowerShell01().RunCommands();
    }

    /// <summary>
    /// Run a script to display the results and errors.
    /// </summary>
    /// <param name="script">Script to be run.</param>
    /// <param name="scriptComment">Comment to be printed about
    /// the script.</param>
    private void RunScript(string script, string scriptComment)
    {
      Console.WriteLine("Running '{0}'\n{1}.\n\nPowerShell Output:", script, scriptComment);

      // Using a PowerShell object, create a pipeline, add the script to the
      //  pipeline, and specify the runspace where the pipeline is invoked.
      PowerShell powerShellCommand = PowerShell.Create();
      powerShellCommand.AddScript(script);
      powerShellCommand.Runspace = this.runspace;

      try
      {
        Collection<PSObject> results = powerShellCommand.Invoke();

        // Display the results.
        foreach (PSObject result in results)
        {
          Console.WriteLine(result);
        }

        // Display any non-terminating errors.
        foreach (ErrorRecord error in powerShellCommand.Streams.Error)
        {
          Console.WriteLine("PowerShell Error: {0}", error);
        }
      }
      catch (RuntimeException ex)
      {
        Console.WriteLine("PowerShell Error: {0}", ex.Message);
        Console.WriteLine();
      }

      Console.WriteLine("\n-----------------------------\n");
    }

    /// <summary>
    /// Run some commands to demonstrate the script capabilities.
    /// </summary>
    private void RunCommands()
    {
      this.runspace = RunspaceFactory.CreateRunspace(InitialSessionState.CreateDefault());
      this.runspace.Open();
      this.RunScript("$a=0;$a", "Assigning to a variable will work for a default InitialSessionState");
      this.runspace.Close();

      this.runspace = RunspaceFactory.CreateRunspace(InitialSessionState.CreateDefault());
      this.runspace.InitialSessionState.LanguageMode = PSLanguageMode.RestrictedLanguage;
      this.runspace.Open();
      this.RunScript("$a=0;$a", "Assigning to a variable will not work in RestrictedLanguage LanguageMode");
      this.runspace.Close();

      this.runspace = RunspaceFactory.CreateRunspace(InitialSessionState.CreateDefault());
      this.runspace.InitialSessionState.LanguageMode = PSLanguageMode.NoLanguage;
      this.runspace.Open();
      this.RunScript("10/2", "A script will not work in NoLanguage LanguageMode.");
      this.runspace.Close();

      this.runspace = RunspaceFactory.CreateRunspace(InitialSessionState.CreateDefault());
      this.runspace.Open();
      string scriptComment = "get-childitem with a default InitialSessionState will work since the standard \n" +
           "PowerShell cmdlets are included in the default InitialSessionState";
      this.RunScript("get-childitem", scriptComment);
      this.runspace.Close();

      InitialSessionState defaultSessionState = InitialSessionState.CreateDefault();
      defaultSessionState.Commands.Add(new SessionStateAliasEntry("dir2", "get-childitem"));
      this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
      this.runspace.Open();
      this.RunScript("dir2", "An alias, like dir2, can be added to InitialSessionState");
      this.runspace.Close();

      defaultSessionState = InitialSessionState.CreateDefault();
      int commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
      defaultSessionState.Commands.RemoveItem(commandIndex);
      this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
      this.runspace.Open();
      scriptComment = "get-childitem was removed from the list of commands so it\nwill no longer be found";
      this.RunScript("get-childitem", scriptComment);
      this.runspace.Close();

      defaultSessionState = InitialSessionState.CreateDefault();
      defaultSessionState.Providers.Clear();
      this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
      this.runspace.Open();
      this.RunScript("get-childitem", "There are no providers so get-childitem will not work");
      this.runspace.Close();

      // Marks a command as private, and then defines a proxy command
      // that uses the private command.  One reason to define a proxy for
      // a command is to remove a parameter of the original command.
      // For a more complete sample of a proxy command, see the Runspace11
      // sample.
      defaultSessionState = InitialSessionState.CreateDefault();
      commandIndex = GetIndexOfEntry(defaultSessionState.Commands, "get-childitem");
      defaultSessionState.Commands[commandIndex].Visibility = SessionStateEntryVisibility.Private;
      CommandMetadata getChildItemMetadata = new CommandMetadata(
           typeof(Microsoft.PowerShell.Commands.GetChildItemCommand));
      getChildItemMetadata.Parameters.Remove("Recurse");
      string getChildItemBody = ProxyCommand.Create(getChildItemMetadata);
      defaultSessionState.Commands.Add(new SessionStateFunctionEntry("get-childitem2", getChildItemBody));
      this.runspace = RunspaceFactory.CreateRunspace(defaultSessionState);
      this.runspace.Open();
      this.RunScript("get-childitem", "get-childitem is private so it will not be available");
      scriptComment = "get-childitem2 is a proxy to get-childitem. \n" +
                    "It works even when get-childitem is private.";
      this.RunScript("get-childitem2", scriptComment);
      scriptComment = "This will fail. Unlike get-childitem, get-childitem2 does not have -Recurse";
      this.RunScript("get-childitem2 -Recurse", scriptComment);

      InitialSessionState cleanSessionState = InitialSessionState.Create();
      this.runspace = RunspaceFactory.CreateRunspace(cleanSessionState);
      this.runspace.Open();
      scriptComment = "A script will not work because \n" +
                   "InitialSessionState.Create() will have the default LanguageMode of NoLanguage";
      this.RunScript("10/2", scriptComment);
      this.runspace.Close();

      cleanSessionState = InitialSessionState.Create();
      cleanSessionState.LanguageMode = PSLanguageMode.FullLanguage;
      this.runspace = RunspaceFactory.CreateRunspace(cleanSessionState);
      this.runspace.Open();
      scriptComment = "get-childitem, standard cmdlets and providers are not present \n" +
                   "in an InitialSessionState returned from InitialSessionState.Create()";
      this.RunScript("get-childitem", scriptComment);
      this.runspace.Close();

      cleanSessionState = InitialSessionState.Create();
      cleanSessionState.Commands.Add(
                new SessionStateCmdletEntry(
                    "Get-ChildItem",
                    typeof(Microsoft.PowerShell.Commands.GetChildItemCommand),
                    null));
      cleanSessionState.Providers.Add(
                new SessionStateProviderEntry(
                    "FileSystem",
                    typeof(Microsoft.PowerShell.Commands.FileSystemProvider),
                    null));
      cleanSessionState.LanguageMode = PSLanguageMode.FullLanguage;
      this.runspace = RunspaceFactory.CreateRunspace(cleanSessionState);
      this.runspace.Open();
      scriptComment = "get-childitem and the FileSystem provider were explicitly added\n" +
                "so get-childitem will work";
      this.RunScript("get-childitem", scriptComment);
      this.runspace.Close();

      Console.Write("Done...");
      Console.ReadLine();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e393f-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e393f-119">See Also</span></span>

[<span data-ttu-id="e393f-120">Windows PowerShell 호스트 응용 프로그램 작성</span><span class="sxs-lookup"><span data-stu-id="e393f-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)