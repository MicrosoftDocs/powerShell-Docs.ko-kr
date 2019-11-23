---
title: Creating a Cmdlet without Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmers Guide], creating
- cmdlets [PowerShell Programmers Guide], basic cmdlet
ms.assetid: 54236ef3-82db-45f8-9114-1ecb7ff65d3e
caps.latest.revision: 8
ms.openlocfilehash: af41c2c9855310d047404114a07b27180a7aa8fc
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415679"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="292d2-102">매개 변수 없이 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="292d2-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="292d2-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span><span class="sxs-lookup"><span data-stu-id="292d2-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="292d2-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span><span class="sxs-lookup"><span data-stu-id="292d2-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="292d2-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="292d2-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="292d2-106">They are not installed in the Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="292d2-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="292d2-107">Naming the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="292d2-107">Naming the Cmdlet</span></span>

<span data-ttu-id="292d2-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span><span class="sxs-lookup"><span data-stu-id="292d2-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="292d2-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span><span class="sxs-lookup"><span data-stu-id="292d2-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="292d2-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="292d2-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="292d2-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="292d2-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="292d2-112">Choosing a Noun</span><span class="sxs-lookup"><span data-stu-id="292d2-112">Choosing a Noun</span></span>

<span data-ttu-id="292d2-113">You should choose a noun that is specific.</span><span class="sxs-lookup"><span data-stu-id="292d2-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="292d2-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span><span class="sxs-lookup"><span data-stu-id="292d2-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="292d2-115">An example cmdlet name of this type is "`Get-SQLServer`".</span><span class="sxs-lookup"><span data-stu-id="292d2-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="292d2-116">Choosing a Verb</span><span class="sxs-lookup"><span data-stu-id="292d2-116">Choosing a Verb</span></span>

<span data-ttu-id="292d2-117">You should use a verb from the set of approved cmdlet verb names.</span><span class="sxs-lookup"><span data-stu-id="292d2-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="292d2-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="292d2-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="292d2-119">Defining the Cmdlet Class</span><span class="sxs-lookup"><span data-stu-id="292d2-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="292d2-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="292d2-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="292d2-121">Here is the class definition for this sample Get-Proc cmdlet:</span><span class="sxs-lookup"><span data-stu-id="292d2-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="292d2-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span><span class="sxs-lookup"><span data-stu-id="292d2-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="292d2-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span><span class="sxs-lookup"><span data-stu-id="292d2-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="292d2-124">You can set attribute keywords to further declare the class if necessary.</span><span class="sxs-lookup"><span data-stu-id="292d2-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="292d2-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="292d2-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="292d2-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span><span class="sxs-lookup"><span data-stu-id="292d2-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="292d2-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span><span class="sxs-lookup"><span data-stu-id="292d2-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="292d2-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span><span class="sxs-lookup"><span data-stu-id="292d2-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="292d2-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span><span class="sxs-lookup"><span data-stu-id="292d2-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="292d2-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span><span class="sxs-lookup"><span data-stu-id="292d2-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="292d2-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="292d2-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="292d2-132">The class for a cmdlet must be explicitly marked as public.</span><span class="sxs-lookup"><span data-stu-id="292d2-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="292d2-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span><span class="sxs-lookup"><span data-stu-id="292d2-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="292d2-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span><span class="sxs-lookup"><span data-stu-id="292d2-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="292d2-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span><span class="sxs-lookup"><span data-stu-id="292d2-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="292d2-136">Overriding an Input Processing Method</span><span class="sxs-lookup"><span data-stu-id="292d2-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="292d2-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span><span class="sxs-lookup"><span data-stu-id="292d2-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="292d2-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="292d2-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="292d2-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span><span class="sxs-lookup"><span data-stu-id="292d2-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="292d2-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span><span class="sxs-lookup"><span data-stu-id="292d2-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="292d2-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span><span class="sxs-lookup"><span data-stu-id="292d2-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="292d2-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span><span class="sxs-lookup"><span data-stu-id="292d2-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="292d2-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span><span class="sxs-lookup"><span data-stu-id="292d2-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="292d2-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span><span class="sxs-lookup"><span data-stu-id="292d2-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="292d2-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span><span class="sxs-lookup"><span data-stu-id="292d2-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="292d2-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span><span class="sxs-lookup"><span data-stu-id="292d2-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="292d2-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span><span class="sxs-lookup"><span data-stu-id="292d2-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Get the current processes
  Process[] processes = Process.GetProcesses();

  // Write the processes to the pipeline making them available
  // to the next cmdlet. The second parameter of this call tells
  // PowerShell to enumerate the array, and send one process at a
  // time to the pipeline.
  WriteObject(processes, true);
}
```

```vb
Protected Overrides Sub ProcessRecord()

    '/ Get the current processes.
    Dim processes As Process()
    processes = Process.GetProcesses()

    '/ Write the processes to the pipeline making them available
    '/ to the next cmdlet. The second parameter of this call tells
    '/ PowerShell to enumerate the array, and send one process at a
    '/ time to the pipeline.
    WriteObject(processes, True)

End Sub 'ProcessRecord
```

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="292d2-148">Things to Remember About Input Processing</span><span class="sxs-lookup"><span data-stu-id="292d2-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="292d2-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span><span class="sxs-lookup"><span data-stu-id="292d2-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="292d2-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="292d2-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="292d2-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span><span class="sxs-lookup"><span data-stu-id="292d2-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="292d2-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span><span class="sxs-lookup"><span data-stu-id="292d2-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="292d2-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span><span class="sxs-lookup"><span data-stu-id="292d2-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="292d2-154">The downstream cmdlet might not return for a long time, or not at all.</span><span class="sxs-lookup"><span data-stu-id="292d2-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="292d2-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span><span class="sxs-lookup"><span data-stu-id="292d2-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="292d2-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span><span class="sxs-lookup"><span data-stu-id="292d2-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="292d2-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="292d2-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="292d2-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span><span class="sxs-lookup"><span data-stu-id="292d2-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="292d2-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="292d2-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="292d2-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span><span class="sxs-lookup"><span data-stu-id="292d2-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="292d2-161">Code Sample</span><span class="sxs-lookup"><span data-stu-id="292d2-161">Code Sample</span></span>

<span data-ttu-id="292d2-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span><span class="sxs-lookup"><span data-stu-id="292d2-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="292d2-163">Defining Object Types and Formatting</span><span class="sxs-lookup"><span data-stu-id="292d2-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="292d2-164">Windows PowerShell passes information between cmdlets using .NET objects.</span><span class="sxs-lookup"><span data-stu-id="292d2-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="292d2-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span><span class="sxs-lookup"><span data-stu-id="292d2-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="292d2-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="292d2-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="292d2-167">Building the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="292d2-167">Building the Cmdlet</span></span>

<span data-ttu-id="292d2-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span><span class="sxs-lookup"><span data-stu-id="292d2-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="292d2-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="292d2-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="292d2-170">Testing the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="292d2-170">Testing the Cmdlet</span></span>

<span data-ttu-id="292d2-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span><span class="sxs-lookup"><span data-stu-id="292d2-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="292d2-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span><span class="sxs-lookup"><span data-stu-id="292d2-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="292d2-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span><span class="sxs-lookup"><span data-stu-id="292d2-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="292d2-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="292d2-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="292d2-175">Start Windows PowerShell, and get the current processes running on the computer.</span><span class="sxs-lookup"><span data-stu-id="292d2-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="292d2-176">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="292d2-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="292d2-177">Assign a variable to the cmdlet results for easier manipulation.</span><span class="sxs-lookup"><span data-stu-id="292d2-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="292d2-178">Get the number of processes.</span><span class="sxs-lookup"><span data-stu-id="292d2-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="292d2-179">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="292d2-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="292d2-180">Retrieve a specific process.</span><span class="sxs-lookup"><span data-stu-id="292d2-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="292d2-181">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="292d2-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="292d2-182">Get the start time of this process.</span><span class="sxs-lookup"><span data-stu-id="292d2-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="292d2-183">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="292d2-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="292d2-184">Get the processes for which the handle count is greater than 500, and sort the result.</span><span class="sxs-lookup"><span data-stu-id="292d2-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="292d2-185">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="292d2-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="292d2-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span><span class="sxs-lookup"><span data-stu-id="292d2-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="292d2-187">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="292d2-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="292d2-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="292d2-188">See Also</span></span>

[<span data-ttu-id="292d2-189">Creating a Cmdlet to Process Command Line Input</span><span class="sxs-lookup"><span data-stu-id="292d2-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="292d2-190">Creating a Cmdlet to Process Pipeline Input</span><span class="sxs-lookup"><span data-stu-id="292d2-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="292d2-191">How to Create a Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="292d2-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="292d2-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="292d2-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="292d2-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="292d2-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="292d2-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="292d2-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="292d2-195">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="292d2-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="292d2-196">Cmdlet Samples</span><span class="sxs-lookup"><span data-stu-id="292d2-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)
