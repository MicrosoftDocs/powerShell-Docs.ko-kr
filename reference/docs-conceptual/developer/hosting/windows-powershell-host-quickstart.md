---
ms.date: 09/12/2016
ms.topic: reference
title: Windows PowerShell 호스트 빠른 시작
description: Windows PowerShell 호스트 빠른 시작
ms.openlocfilehash: 4cb7dae60342abb40bd7a989a27a692826b360e5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657423"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="2e75a-103">Windows PowerShell 호스트 빠른 시작</span><span class="sxs-lookup"><span data-stu-id="2e75a-103">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="2e75a-104">응용 프로그램에서 Windows PowerShell을 호스팅하려면 [system.web. PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-104">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span>
<span data-ttu-id="2e75a-105">이 클래스는 명령의 파이프라인을 만든 다음 runspace에서 해당 명령을 실행 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-105">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span>
<span data-ttu-id="2e75a-106">호스트 응용 프로그램을 만드는 가장 간단한 방법은 기본 runspace를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-106">The simplest way to create a host application is to use the default runspace.</span></span>
<span data-ttu-id="2e75a-107">기본 runspace는 모든 핵심 Windows PowerShell 명령을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-107">The default runspace contains all of the core Windows PowerShell commands.</span></span>
<span data-ttu-id="2e75a-108">응용 프로그램에서 Windows PowerShell 명령의 하위 집합만 노출 하도록 하려면 사용자 지정 runspace를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-108">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="2e75a-109">기본 runspace 사용</span><span class="sxs-lookup"><span data-stu-id="2e75a-109">Using the default runspace</span></span>

<span data-ttu-id="2e75a-110">먼저 기본 runspace를 사용 하 고 [, 클래스의](/dotnet/api/System.Management.Automation.PowerShell) 메서드를 사용 하 여 명령, 매개 변수, 문 및 스크립트를 파이프라인에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-110">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="2e75a-111">AddCommand</span><span class="sxs-lookup"><span data-stu-id="2e75a-111">AddCommand</span></span>

<span data-ttu-id="2e75a-112">파이프라인에 명령을 추가 하는 데는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-112">You use the [System.Management.Automation.Powershell.AddCommand](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method to add commands to the pipeline.</span></span>
<span data-ttu-id="2e75a-113">예를 들어, 컴퓨터에서 실행 중인 프로세스 목록을 가져오려고 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-113">For example, suppose you want to get the list of running processes on the machine.</span></span>
<span data-ttu-id="2e75a-114">이 명령을 실행 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-114">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="2e75a-115">System.web. [PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-115">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="2e75a-116">실행할 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-116">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="2e75a-117">명령을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-117">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="2e75a-118">[System.object](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 를 호출 하기 전에 addcommand 메서드를 두 번 이상 호출 하는 경우 첫 번째 명령의 결과는 두 번째로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-118">If you call the AddCommand method more than once before you call the [System.Management.Automation.Powershell.Invoke](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span>
<span data-ttu-id="2e75a-119">이전 명령의 결과를 명령에 파이프 하지 않으려는 경우에는 대신 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 를 호출 하 여 명령에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-119">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="2e75a-120">AddParameter</span><span class="sxs-lookup"><span data-stu-id="2e75a-120">AddParameter</span></span>

<span data-ttu-id="2e75a-121">이전 예제에서는 매개 변수 없이 단일 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-121">The previous example executes a single command without any parameters.</span></span>
<span data-ttu-id="2e75a-122">명령을 사용 하 여 매개 변수를 추가할 수 있습니다. [AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 메서드.</span><span class="sxs-lookup"><span data-stu-id="2e75a-122">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method.</span></span>
<span data-ttu-id="2e75a-123">예를 들어 다음 코드는 `PowerShell` 컴퓨터에서 실행 되는 이라는 모든 프로세스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-123">For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="2e75a-124">AddParameter 메서드를 반복 해 서 호출 하 여 추가 매개 변수를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-124">You can add additional parameters by calling the AddParameter method repeatedly.</span></span>

```csharp                   
PowerShell.Create().AddCommand("Get-ChildItem")
                   .AddParameter("Path", @"c:\Windows")
                   .AddParameter("Filter", "*.exe")
                   .Invoke();
```

<span data-ttu-id="2e75a-125">또한, 매개 변수 이름 및 값의 사전은 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 를 호출 하 여 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-125">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Path", @"c:\Windows");
parameters.Add("Filter", "*.exe");

PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="2e75a-126">AddStatement</span><span class="sxs-lookup"><span data-stu-id="2e75a-126">AddStatement</span></span>

<span data-ttu-id="2e75a-127">파이프라인의 끝에 문을 추가 하는 [system.object](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 를 사용 하 여 일괄 처리를 시뮬레이션할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-127">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline.</span></span>
<span data-ttu-id="2e75a-128">다음 코드는 이름이 인 실행 중인 프로세스 목록을 가져온 `PowerShell` 다음 실행 중인 서비스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-128">The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="2e75a-129">AddScript</span><span class="sxs-lookup"><span data-stu-id="2e75a-129">AddScript</span></span>

<span data-ttu-id="2e75a-130">[System.object](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 메서드를 호출 하 여 기존 스크립트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-130">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span>
<span data-ttu-id="2e75a-131">다음 예제에서는 스크립트를 파이프라인에 추가 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-131">The following example adds a script to the pipeline and runs it.</span></span>
<span data-ttu-id="2e75a-132">이 예에서는 라는 폴더에 라는 스크립트가 이미 있다고 가정 `MyScript.ps1` `D:\PSScripts` 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-132">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="2e75a-133">라는 부울 매개 변수를 사용 하는 AddScript 메서드의 버전도 있습니다 `useLocalScope` .</span><span class="sxs-lookup"><span data-stu-id="2e75a-133">There is also a version of the AddScript method that takes a boolean parameter named `useLocalScope`.</span></span>
<span data-ttu-id="2e75a-134">이 매개 변수를로 설정 하면 `true` 스크립트는 로컬 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-134">If this parameter is set to `true`, then the script is run in the local scope.</span></span>
<span data-ttu-id="2e75a-135">다음 코드에서는 로컬 범위에서 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-135">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="2e75a-136">사용자 지정 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="2e75a-136">Creating a custom runspace</span></span>

<span data-ttu-id="2e75a-137">이전 예제에서 사용 된 기본 runspace는 모든 핵심 Windows PowerShell 명령을 로드 하지만 모든 명령의 지정 된 하위 집합만 로드 하는 사용자 지정 runspace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-137">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span>
<span data-ttu-id="2e75a-138">이 작업을 수행 하 여 성능을 향상 시키거나 (많은 수의 명령을 로드 하 여 성능이 저하 됨) 사용자가 작업을 수행 하는 기능을 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-138">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span>
<span data-ttu-id="2e75a-139">제한 된 개수의 명령만 노출 하는 runspace를 제한 된 runspace 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-139">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span>
<span data-ttu-id="2e75a-140">제한 된 runspace를 만들려면 [runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 및 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 클래스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-140">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="2e75a-141">InitialSessionState 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="2e75a-141">Creating an InitialSessionState object</span></span>

<span data-ttu-id="2e75a-142">사용자 지정 runspace를 만들려면 먼저 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-142">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>
<span data-ttu-id="2e75a-143">다음 예제에서는 기본 InitialSessionState 개체를 만든 후 [runspace. RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) 를 사용 하 여 runspace를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-143">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a runspace after creating a default InitialSessionState object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="2e75a-144">Runspace 제한</span><span class="sxs-lookup"><span data-stu-id="2e75a-144">Constraining the runspace</span></span>

<span data-ttu-id="2e75a-145">이전 예제에서는 기본 제공 핵심 Windows PowerShell을 모두 로드 하는 기본 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-145">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span>
<span data-ttu-id="2e75a-146">[System.Management.Automation.Runspaces.Iniinitialsessionstate.createdefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) 메서드를 호출 하 여 tialSessionState 스냅인의 명령만 로드 하는 InitialSessionState 개체를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-146">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Microsoft.PowerShell.Core snapin.</span></span>
<span data-ttu-id="2e75a-147">더 제한 된 runspace를 만들려면 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) 메서드를 호출 하 여 빈 InitialSessionState 개체를 만든 다음 InitialSessionState에 명령을 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-147">To create a more constrained runspace, you must create an empty InitialSessionState object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="2e75a-148">지정 하는 명령만 로드 하는 runspace를 사용 하면 성능이 크게 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-148">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="2e75a-149">[Runspace](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) 의 메서드를 사용 하 여 초기 세션 상태에 대 한 cmdlet을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-149">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span>
<span data-ttu-id="2e75a-150">다음 예에서는 빈 초기 세션 상태를 만든 다음 및 명령을 정의 하 고 `Get-Command` `Import-Module` 초기 세션 상태에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-150">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span>
<span data-ttu-id="2e75a-151">그런 다음 해당 초기 세션 상태에 의해 제한 되는 runspace를 만들고 해당 runspace에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-151">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="2e75a-152">초기 세션 상태를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-152">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="2e75a-153">초기 세션 상태에 명령을 정의 하 고 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-153">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="2e75a-154">Runspace를 만들고 엽니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-154">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="2e75a-155">명령을 실행 하 고 결과를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-155">Execute a command and show the result.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
Collection<CommandInfo> result = ps.Invoke<CommandInfo>();
foreach (var entry in result)
{
       Console.WriteLine(entry.Name);
}
```

<span data-ttu-id="2e75a-156">실행 하는 경우이 코드의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2e75a-156">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
