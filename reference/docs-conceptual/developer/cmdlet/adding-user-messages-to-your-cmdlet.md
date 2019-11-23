---
title: Adding User Messages to Your Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: 9079f40e75dae86c22fd8b4f8a45d501c6125498
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416036"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="70a05-102">Cmdlet에 사용자 메시지 추가</span><span class="sxs-lookup"><span data-stu-id="70a05-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="70a05-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span><span class="sxs-lookup"><span data-stu-id="70a05-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="70a05-104">These messages include the following types:</span><span class="sxs-lookup"><span data-stu-id="70a05-104">These messages include the following types:</span></span>

- <span data-ttu-id="70a05-105">Verbose messages that contain general user information.</span><span class="sxs-lookup"><span data-stu-id="70a05-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="70a05-106">Debug messages that contain troubleshooting information.</span><span class="sxs-lookup"><span data-stu-id="70a05-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="70a05-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span><span class="sxs-lookup"><span data-stu-id="70a05-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="70a05-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span><span class="sxs-lookup"><span data-stu-id="70a05-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="70a05-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span><span class="sxs-lookup"><span data-stu-id="70a05-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="70a05-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70a05-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="70a05-111">Defining the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70a05-111">Defining the Cmdlet</span></span>

<span data-ttu-id="70a05-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70a05-112">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="70a05-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span><span class="sxs-lookup"><span data-stu-id="70a05-113">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="70a05-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="70a05-114">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="70a05-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span><span class="sxs-lookup"><span data-stu-id="70a05-115">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="70a05-116">The following code is the definition for this Stop-Proc cmdlet class.</span><span class="sxs-lookup"><span data-stu-id="70a05-116">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="70a05-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="70a05-117">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="70a05-118">Defining Parameters for System Modification</span><span class="sxs-lookup"><span data-stu-id="70a05-118">Defining Parameters for System Modification</span></span>

<span data-ttu-id="70a05-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span><span class="sxs-lookup"><span data-stu-id="70a05-119">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="70a05-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="70a05-120">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="70a05-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70a05-121">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="70a05-122">Overriding an Input Processing Method</span><span class="sxs-lookup"><span data-stu-id="70a05-122">Overriding an Input Processing Method</span></span>

<span data-ttu-id="70a05-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="70a05-123">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="70a05-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span><span class="sxs-lookup"><span data-stu-id="70a05-124">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="70a05-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span><span class="sxs-lookup"><span data-stu-id="70a05-125">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="70a05-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="70a05-126">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="70a05-127">Writing a Verbose Message</span><span class="sxs-lookup"><span data-stu-id="70a05-127">Writing a Verbose Message</span></span>

<span data-ttu-id="70a05-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span><span class="sxs-lookup"><span data-stu-id="70a05-128">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="70a05-129">The system administrator can then use that information to continue processing other commands.</span><span class="sxs-lookup"><span data-stu-id="70a05-129">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="70a05-130">In addition, any information written using this method should be localized as needed.</span><span class="sxs-lookup"><span data-stu-id="70a05-130">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="70a05-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span><span class="sxs-lookup"><span data-stu-id="70a05-131">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="70a05-132">Writing a Debug Message</span><span class="sxs-lookup"><span data-stu-id="70a05-132">Writing a Debug Message</span></span>

<span data-ttu-id="70a05-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70a05-133">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="70a05-134">The call is made from an input processing method.</span><span class="sxs-lookup"><span data-stu-id="70a05-134">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="70a05-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span><span class="sxs-lookup"><span data-stu-id="70a05-135">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="70a05-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="70a05-136">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="70a05-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span><span class="sxs-lookup"><span data-stu-id="70a05-137">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="70a05-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span><span class="sxs-lookup"><span data-stu-id="70a05-138">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="70a05-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span><span class="sxs-lookup"><span data-stu-id="70a05-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="70a05-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span><span class="sxs-lookup"><span data-stu-id="70a05-140">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="70a05-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70a05-141">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="70a05-142">The following command-line entry implements a tracing operation.</span><span class="sxs-lookup"><span data-stu-id="70a05-142">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="70a05-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span><span class="sxs-lookup"><span data-stu-id="70a05-143">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="70a05-144">Writing a Warning Message</span><span class="sxs-lookup"><span data-stu-id="70a05-144">Writing a Warning Message</span></span>

<span data-ttu-id="70a05-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span><span class="sxs-lookup"><span data-stu-id="70a05-145">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="70a05-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span><span class="sxs-lookup"><span data-stu-id="70a05-146">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="70a05-147">Writing a Progress Message</span><span class="sxs-lookup"><span data-stu-id="70a05-147">Writing a Progress Message</span></span>

<span data-ttu-id="70a05-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span><span class="sxs-lookup"><span data-stu-id="70a05-148">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="70a05-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span><span class="sxs-lookup"><span data-stu-id="70a05-149">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="70a05-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span><span class="sxs-lookup"><span data-stu-id="70a05-150">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="70a05-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span><span class="sxs-lookup"><span data-stu-id="70a05-151">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="70a05-152">Code Sample</span><span class="sxs-lookup"><span data-stu-id="70a05-152">Code Sample</span></span>

<span data-ttu-id="70a05-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span><span class="sxs-lookup"><span data-stu-id="70a05-153">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="70a05-154">Define Object Types and Formatting</span><span class="sxs-lookup"><span data-stu-id="70a05-154">Define Object Types and Formatting</span></span>

<span data-ttu-id="70a05-155">Windows PowerShell passes information between cmdlets using .NET objects.</span><span class="sxs-lookup"><span data-stu-id="70a05-155">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="70a05-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70a05-156">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="70a05-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="70a05-157">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="70a05-158">Building the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70a05-158">Building the Cmdlet</span></span>

<span data-ttu-id="70a05-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span><span class="sxs-lookup"><span data-stu-id="70a05-159">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="70a05-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="70a05-160">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="70a05-161">Testing the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70a05-161">Testing the Cmdlet</span></span>

<span data-ttu-id="70a05-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span><span class="sxs-lookup"><span data-stu-id="70a05-162">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="70a05-163">Let's test the sample Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70a05-163">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="70a05-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="70a05-164">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="70a05-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span><span class="sxs-lookup"><span data-stu-id="70a05-165">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="70a05-166">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="70a05-166">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="70a05-167">참고 항목</span><span class="sxs-lookup"><span data-stu-id="70a05-167">See Also</span></span>

[<span data-ttu-id="70a05-168">Create a Cmdlet that Modifies the System</span><span class="sxs-lookup"><span data-stu-id="70a05-168">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="70a05-169">How to Create a Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="70a05-169">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="70a05-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="70a05-170">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="70a05-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="70a05-171">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="70a05-172">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="70a05-172">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
