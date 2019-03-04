---
title: Windows PowerShell 호스트 빠른 시작 | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a134b81-bd0c-4e1c-a2f0-9acbe852745a
caps.latest.revision: 9
ms.openlocfilehash: 2c6a4bca03ee7f62371cbc296f854464167e5a62
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857399"
---
# <a name="windows-powershell-host-quickstart"></a><span data-ttu-id="6ba86-102">Windows PowerShell 호스트 빠른 시작</span><span class="sxs-lookup"><span data-stu-id="6ba86-102">Windows PowerShell Host Quickstart</span></span>

<span data-ttu-id="6ba86-103">응용 프로그램에서 Windows PowerShell 호스트를 사용 하 여 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-103">To host Windows PowerShell in your application, you use the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class.</span></span> <span data-ttu-id="6ba86-104">이 클래스는 명령의 파이프라인 만들기 및 runspace에 명령을 실행 하 여 다음 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-104">This class provides methods that create a pipeline of commands and then execute those commands in a runspace.</span></span> <span data-ttu-id="6ba86-105">호스트 응용 프로그램을 만드는 가장 간단한 방법은 기본 runspace를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-105">The simplest way to create a host application is to use the default runspace.</span></span> <span data-ttu-id="6ba86-106">기본 runspace 모든 핵심 Windows PowerShell 명령이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-106">The default runspace contains all of the core Windows PowerShell commands.</span></span> <span data-ttu-id="6ba86-107">Windows PowerShell 명령의 하위 집합만 노출 하도록 응용 프로그램을 원하는 경우 사용자 지정 runspace를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-107">If you want your application to expose only a subset of the Windows PowerShell commands, you must create a custom runspace.</span></span>

## <a name="using-the-default-runspace"></a><span data-ttu-id="6ba86-108">기본 runspace를 사용 하 여</span><span class="sxs-lookup"><span data-stu-id="6ba86-108">Using the default runspace</span></span>

<span data-ttu-id="6ba86-109">를 시작 하려면에서는 기본 runspace를 사용 하 고의 메서드를 사용 합니다 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 파이프라인에 명령, 매개 변수, 문 및 스크립트를 추가 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-109">To start, we'll use the default runspace, and use the methods of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands, parameters, statements, and scripts to a pipeline.</span></span>

### <a name="addcommand"></a><span data-ttu-id="6ba86-110">AddCommand</span><span class="sxs-lookup"><span data-stu-id="6ba86-110">AddCommand</span></span>

<span data-ttu-id="6ba86-111">사용할 합니다 [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) 메서드는 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 파이프라인에 명령을 추가 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-111">You use the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method of the [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) class to add commands to the pipeline.</span></span> <span data-ttu-id="6ba86-112">예를 들어 컴퓨터에서 실행 중인 프로세스 목록을 가져오려고 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-112">For example, suppose you want to get the list of running processes on the machine.</span></span> <span data-ttu-id="6ba86-113">이 명령을 실행 하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-113">The way to run this command is as follows.</span></span>

1. <span data-ttu-id="6ba86-114">만들기는 [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-114">Create a [System.Management.Automation.PowerShell](/dotnet/api/System.Management.Automation.PowerShell) object.</span></span>

   ```csharp
   PowerShell ps = PowerShell.Create();
   ```

2. <span data-ttu-id="6ba86-115">실행 하려는 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-115">Add the command that you want to execute.</span></span>

   ```csharp
   ps.AddCommand("Get-Process");
   ```

3. <span data-ttu-id="6ba86-116">명령을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-116">Invoke the command.</span></span>

   ```csharp
   ps.Invoke();
   ```

<span data-ttu-id="6ba86-117">호출 하는 경우는 [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) 메서드를 호출 하기 전에 두 번 이상 합니다 [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) 메서드, 결과 첫 번째 명령은 두 번째, 및 등으로 파이프 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-117">If you call the [System.Management.Automation.Powershell.AddCommand\*](/dotnet/api/System.Management.Automation.PowerShell.AddCommand) method more than once before you call the [System.Management.Automation.Powershell.Invoke\*](/dotnet/api/System.Management.Automation.PowerShell.Invoke) method, the result of the first command is piped to the second, and so on.</span></span> <span data-ttu-id="6ba86-118">명령에는 이전 명령의 결과 파이프 하려면 호출 하 여 추가 합니다 [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 대신 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-118">If you do not want to pipe the result of a previous command to a command, add it by calling the [System.Management.Automation.Powershell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) instead.</span></span>

### <a name="addparameter"></a><span data-ttu-id="6ba86-119">AddParameter</span><span class="sxs-lookup"><span data-stu-id="6ba86-119">AddParameter</span></span>

<span data-ttu-id="6ba86-120">이전 예제에서는 단일 매개 변수 없이 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-120">The previous example executes a single command without any parameters.</span></span> <span data-ttu-id="6ba86-121">사용 하 여 명령에 매개 변수를 추가할 수는 [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 메서드 예를 들어, 다음 코드의 목록을 가져옵니다 모든 명명 된 프로세스 `PowerShell` 에서 실행 되는 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-121">You can add parameters to the command by using the [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) method For example, the following code gets a list of all of the processes that are named `PowerShell` running on the machine.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .Invoke();
```

<span data-ttu-id="6ba86-122">호출 하 여 추가 매개 변수를 추가할 수 있습니다 [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) 반복적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-122">You can add additional parameters by calling [System.Management.Automation.PSCommand.AddParameter\*](/dotnet/api/System.Management.Automation.PSCommand.AddParameter) repeatedly.</span></span>

```csharp
PowerShell.Create().AddCommand("Get-Process")
                   .AddParameter("Name", "PowerShell")
                   .AddParameter("Id", "12768")
                   .Invoke();
```

<span data-ttu-id="6ba86-123">호출 하 여 매개 변수 이름 및 값의 사전을 추가할 수도 있습니다는 [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) 메서드.</span><span class="sxs-lookup"><span data-stu-id="6ba86-123">You can also add a dictionary of parameter names and values by calling the [System.Management.Automation.PowerShell.AddParameters\*](/dotnet/api/System.Management.Automation.PowerShell.AddParameters) method.</span></span>

```csharp
IDictionary parameters = new Dictionary<String, String>();
parameters.Add("Name", "PowerShell");

parameters.Add("Id", "12768");
PowerShell.Create().AddCommand("Get-Process")
   .AddParameters(parameters)
      .Invoke()

```

### <a name="addstatement"></a><span data-ttu-id="6ba86-124">AddStatement</span><span class="sxs-lookup"><span data-stu-id="6ba86-124">AddStatement</span></span>

<span data-ttu-id="6ba86-125">사용 하 여 일괄 처리를 시뮬레이션할 수 있습니다 합니다 [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) 는 추가 문을 다음 코드는 이름을 사용 하 여 실행 중인 프로세스 목록을 가져옵니다 파이프라인의 끝에 추가 하는 메서드 `PowerShell`, 한 다음 실행 중인 서비스 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-125">You can simulate batching by using the [System.Management.Automation.PowerShell.AddStatement\*](/dotnet/api/System.Management.Automation.PowerShell.AddStatement) method, which adds an additional statement to the end of the pipeline The following code gets a list of running processes with the name `PowerShell`, and then gets the list of running services.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddCommand("Get-Process").AddParameter("Name", "PowerShell");
ps.AddStatement().AddCommand("Get-Service");
ps.Invoke();
```

### <a name="addscript"></a><span data-ttu-id="6ba86-126">AddScript</span><span class="sxs-lookup"><span data-stu-id="6ba86-126">AddScript</span></span>

<span data-ttu-id="6ba86-127">호출 하 여 기존 스크립트를 실행할 수 있습니다 합니다 [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 메서드.</span><span class="sxs-lookup"><span data-stu-id="6ba86-127">You can run an existing script by calling the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method.</span></span> <span data-ttu-id="6ba86-128">다음 예제에서는 파이프라인에 스크립트를 추가 하 고 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-128">The following example adds a script to the pipeline and runs it.</span></span> <span data-ttu-id="6ba86-129">이 예제에서는 라는 스크립트를 이미 있다고 가정 `MyScript.ps1` 라는 폴더에 `D:\PSScripts`입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-129">This example assumes there is already a script named `MyScript.ps1` in a folder named `D:\PSScripts`.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript("D:\PSScripts\MyScript.ps1").Invoke();
```

<span data-ttu-id="6ba86-130">버전을 [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) 라는 부울 매개 변수를 갖는 메서드의 `useLocalScope`합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-130">There is also a version of the [System.Management.Automation.PowerShell.AddScript\*](/dotnet/api/System.Management.Automation.PowerShell.AddScript) method that takes a boolean parameter named `useLocalScope`.</span></span> <span data-ttu-id="6ba86-131">이 매개 변수가 설정 된 경우 `true`, 다음 스크립트를 로컬 범위에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-131">If this parameter is set to `true`, then the script is run in the local scope.</span></span> <span data-ttu-id="6ba86-132">다음 코드를 로컬 범위에는 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-132">The following code will run the script in the local scope.</span></span>

```csharp
PowerShell ps = PowerShell.Create();
ps.AddScript(@"D:\PSScripts\MyScript.ps1", true).Invoke();
```

## <a name="creating-a-custom-runspace"></a><span data-ttu-id="6ba86-133">사용자 지정 runspace 만들기</span><span class="sxs-lookup"><span data-stu-id="6ba86-133">Creating a custom runspace</span></span>

<span data-ttu-id="6ba86-134">앞의 예제에 사용 되는 기본 runspace 핵심 Windows PowerShell 명령을 모두 로드 하는 동안에 모든 명령의 지정 된 하위 집합만 로드 하는 사용자 지정 runspace를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-134">While the default runspace used in the previous examples loads all of the core Windows PowerShell commands, you can create a custom runspace that loads only a specified subset of all commands.</span></span> <span data-ttu-id="6ba86-135">성능 향상을 위해이 작업을 수행 하는 것이 좋습니다 (성능 저하는 많은 명령 로드), 또는 작업을 수행 하는 사용자의 기능을 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-135">You might want to do this to improve performance (loading a larger number of commands is a performance hit), or to restrict the capability of the user to perform operations.</span></span> <span data-ttu-id="6ba86-136">제한 된 수의 명령 노출 하는 runspace가 제한 된 runspace를 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-136">A runspace that exposes only a limited number of commands is called a constrained runspace.</span></span> <span data-ttu-id="6ba86-137">사용 제한 된 runspace를 만들려면 합니다 [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) 하 고 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-137">To create a constrained runspace, you use the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) and [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) classes.</span></span>

### <a name="creating-an-initialsessionstate-object"></a><span data-ttu-id="6ba86-138">InitialSessionState 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="6ba86-138">Creating an InitialSessionState object</span></span>

<span data-ttu-id="6ba86-139">Runspace를 만드는 사용자 지정을 먼저 만들어야 합니다는 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-139">To create a custom runspace, you must first create an [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span> <span data-ttu-id="6ba86-140">다음 예에서는 사용 합니다 [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) 기본값을 만든 후를 ruspace를 만들려면 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-140">In the following example, we use the [System.Management.Automation.Runspaces.RunspaceFactory](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory) to create a ruspace after creating a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.CreateDefault();
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
PowerShell ps = PowerShell.Create();
ps.Runspace = rs;
ps.AddCommand("Get-Command");
ps.Invoke();
```

### <a name="constraining-the-runspace"></a><span data-ttu-id="6ba86-141">제한 된 runspace</span><span class="sxs-lookup"><span data-stu-id="6ba86-141">Constraining the runspace</span></span>

<span data-ttu-id="6ba86-142">기본값 이전 예에서 만들었습니다 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 모든 기본 제공 핵심 Windows PowerShell을 로드 하는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-142">In the previous example, we created a default [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object that loads all of the built-in core Windows PowerShell.</span></span> <span data-ttu-id="6ba86-143">에서는 호출할 수도 있습니다. 또한 합니다 [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) InitialSessionState 개체는 Mirosoft.PowerShell.Core의 명령만 로드를 만드는 방법 스냅인입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-143">We could also have called the [System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.CreateDefault2) method to create an InitialSessionState object that would load only the commands in the Mirosoft.PowerShell.Core snapin.</span></span> <span data-ttu-id="6ba86-144">빈 더 제한 된 runspace를 만들려면 만들어야 [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) 를 호출 하 여 개체를 [ System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) 메서드를 다음 명령에는 InitialSessionState을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-144">To create a more constrained runspace, you must create an empty [System.Management.Automation.Runspaces.InitialSessionState](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object by calling the [System.Management.Automation.Runspaces.InitialSessionState.Create\*](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState.Create) method, and then add commands to the InitialSessionState.</span></span>

<span data-ttu-id="6ba86-145">지정 하는 명령만 로드 하는 runspace를 사용 하 여 성능이 크게 향상 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-145">Using a runspace that loads only the commands that you specify provides significantly improved performance.</span></span>

<span data-ttu-id="6ba86-146">메서드를 사용 합니다 [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) 초기 세션 상태에 대 한 cmdlet을 정의 하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-146">You use the methods of the [System.Management.Automation.Runspaces.SessionStateCmdletEntry](/dotnet/api/System.Management.Automation.Runspaces.SessionStateCmdletEntry) class to define cmdlets for the initial session state.</span></span> <span data-ttu-id="6ba86-147">다음 예제에서는 빈 초기 세션 상태를 다음 정의 만들고 추가 합니다 `Get-Command` 및 `Import-Module` 초기 세션 상태에 명령 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-147">The following example creates an empty initial session state, then defines and adds the `Get-Command` and `Import-Module` commands to the initial session state.</span></span> <span data-ttu-id="6ba86-148">그런 다음 해당 초기 세션 상태에 의해 제한 된 runspace 만들고 해당 runspace에서 명령을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-148">We then create a runspace constrained by that initial session state, and execute the commands in that runspace.</span></span>

<span data-ttu-id="6ba86-149">초기 세션 상태를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-149">Create the initial session state.</span></span>

```csharp
InitialSessionState iss = InitialSessionState.Create();
```

<span data-ttu-id="6ba86-150">정의 하 고 초기 세션 상태에 명령을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-150">Define and add commands to the initial session state.</span></span>

```csharp
SessionStateCmdletEntry getCommand = new SessionStateCmdletEntry(
        "Get-Command", typeof(Microsoft.PowerShell.Commands.GetCommandCommand), "");
SessionStateCmdletEntry importModule = new SessionStateCmdletEntry(
        "Import-Module", typeof(Microsoft.PowerShell.Commands.ImportModuleCommand), "");
iss.Commands.Add(getCommand);
iss.Commands.Add(importModule);
```

<span data-ttu-id="6ba86-151">만들고 runspace를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-151">Create and open the runspace.</span></span>

```csharp
Runspace rs = RunspaceFactory.CreateRunspace(iss);
rs.Open();
```

<span data-ttu-id="6ba86-152">명령을 실행 하 고 결과 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-152">Execute a command and show the result.</span></span>

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

<span data-ttu-id="6ba86-153">를 실행 하는 경우이 코드의 출력 다음과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6ba86-153">When run, the output of this code will look as follows.</span></span>

```powershell
Get-Command
Import-Module
```
