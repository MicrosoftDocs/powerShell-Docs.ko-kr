---
title: Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 931ccace-c565-4a98-8dcc-df00f86394b1
caps.latest.revision: 8
ms.openlocfilehash: d210a852a90d94df2ab360dd86f0b83a396330e3
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415649"
---
# <a name="adding-aliases-wildcard-expansion-and-help-to-cmdlet-parameters"></a><span data-ttu-id="0b97b-102">Cmdlet 매개 변수에 별칭, 와일드카드 확장 및 도움말 추가</span><span class="sxs-lookup"><span data-stu-id="0b97b-102">Adding Aliases, Wildcard Expansion, and Help to Cmdlet Parameters</span></span>

<span data-ttu-id="0b97b-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="0b97b-103">This section describes how to add aliases, wildcard expansion, and Help messages to the parameters of the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span>

<span data-ttu-id="0b97b-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="0b97b-104">This Stop-Proc cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="0b97b-105">Defining the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b97b-105">Defining the Cmdlet</span></span>

<span data-ttu-id="0b97b-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b97b-106">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="0b97b-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span><span class="sxs-lookup"><span data-stu-id="0b97b-107">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="0b97b-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span><span class="sxs-lookup"><span data-stu-id="0b97b-108">Because this cmdlet stops system processes, it uses the verb "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate process.</span></span> <span data-ttu-id="0b97b-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="0b97b-109">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="0b97b-110">The following code is the class definition for this Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b97b-110">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="0b97b-111">Defining Parameters for System Modification</span><span class="sxs-lookup"><span data-stu-id="0b97b-111">Defining Parameters for System Modification</span></span>

<span data-ttu-id="0b97b-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span><span class="sxs-lookup"><span data-stu-id="0b97b-112">Your cmdlet needs to define parameters that support system modifications and user feedback.</span></span> <span data-ttu-id="0b97b-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span><span class="sxs-lookup"><span data-stu-id="0b97b-113">The cmdlet should define a `Name` parameter or equivalent so that the cmdlet will be able to modify the system by some sort of identifier.</span></span> <span data-ttu-id="0b97b-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span><span class="sxs-lookup"><span data-stu-id="0b97b-114">In addition, the cmdlet should define the `Force` and `PassThru` parameters.</span></span> <span data-ttu-id="0b97b-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="0b97b-115">For more information about these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="defining-a-parameter-alias"></a><span data-ttu-id="0b97b-116">Defining a Parameter Alias</span><span class="sxs-lookup"><span data-stu-id="0b97b-116">Defining a Parameter Alias</span></span>

<span data-ttu-id="0b97b-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span><span class="sxs-lookup"><span data-stu-id="0b97b-117">A parameter alias can be an alternate name or a well-defined 1-letter or 2-letter short name for a cmdlet parameter.</span></span> <span data-ttu-id="0b97b-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span><span class="sxs-lookup"><span data-stu-id="0b97b-118">In both cases, the goal of using aliases is to simplify user entry from the command line.</span></span> <span data-ttu-id="0b97b-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span><span class="sxs-lookup"><span data-stu-id="0b97b-119">Windows PowerShell supports parameter aliases through the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, which uses the declaration syntax [Alias()].</span></span>

<span data-ttu-id="0b97b-120">The following code shows how an alias is added to the `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="0b97b-120">The following code shows how an alias is added to the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
[Alias("ProcessName")]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;
```

<span data-ttu-id="0b97b-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span><span class="sxs-lookup"><span data-stu-id="0b97b-121">In addition to using the [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute, the Windows PowerShell runtime performs partial name matching, even if no aliases are specified.</span></span> <span data-ttu-id="0b97b-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span><span class="sxs-lookup"><span data-stu-id="0b97b-122">For example, if your cmdlet has a `FileName` parameter and that is the only parameter that starts with `F`, the user could enter `Filename`, `Filenam`, `File`, `Fi`, or `F` and still recognize the entry as the `FileName` parameter.</span></span>

## <a name="creating-help-for-parameters"></a><span data-ttu-id="0b97b-123">Creating Help for Parameters</span><span class="sxs-lookup"><span data-stu-id="0b97b-123">Creating Help for Parameters</span></span>

<span data-ttu-id="0b97b-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span><span class="sxs-lookup"><span data-stu-id="0b97b-124">Windows PowerShell allows you to create Help for cmdlet parameters.</span></span> <span data-ttu-id="0b97b-125">Do this for any parameter used for system modification and user feedback.</span><span class="sxs-lookup"><span data-stu-id="0b97b-125">Do this for any parameter used for system modification and user feedback.</span></span> <span data-ttu-id="0b97b-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span><span class="sxs-lookup"><span data-stu-id="0b97b-126">For each parameter to support Help, you can set the `HelpMessage` attribute keyword in the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="0b97b-127">This keyword defines the text to display to the user for assistance in using the parameter.</span><span class="sxs-lookup"><span data-stu-id="0b97b-127">This keyword defines the text to display to the user for assistance in using the parameter.</span></span> <span data-ttu-id="0b97b-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span><span class="sxs-lookup"><span data-stu-id="0b97b-128">You can also set the `HelpMessageBaseName` keyword to identify the base name of a resource to use for the message.</span></span> <span data-ttu-id="0b97b-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span><span class="sxs-lookup"><span data-stu-id="0b97b-129">If you set this keyword, you must also set the `HelpMessageResourceId` keyword to specify the resource identifier.</span></span>

<span data-ttu-id="0b97b-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="0b97b-130">The following code from this Stop-Proc cmdlet defines the `HelpMessage` attribute keyword for the `Name` parameter.</span></span>

```csharp
/// <summary>
/// Specify the mandatory Name parameter used to identify the
/// processes to be stopped.
/// </summary>
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true,
           HelpMessage = "The name of one or more processes to stop. Wildcards are permitted."
)]
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="0b97b-131">Overriding an Input Processing Method</span><span class="sxs-lookup"><span data-stu-id="0b97b-131">Overriding an Input Processing Method</span></span>

<span data-ttu-id="0b97b-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span><span class="sxs-lookup"><span data-stu-id="0b97b-132">Your cmdlet must override an input processing method, most often this will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="0b97b-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span><span class="sxs-lookup"><span data-stu-id="0b97b-133">When modifying the system, the cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to allow the user to provide feedback before a change is made.</span></span> <span data-ttu-id="0b97b-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="0b97b-134">For more information about these methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="supporting-wildcard-expansion"></a><span data-ttu-id="0b97b-135">Supporting Wildcard Expansion</span><span class="sxs-lookup"><span data-stu-id="0b97b-135">Supporting Wildcard Expansion</span></span>

<span data-ttu-id="0b97b-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span><span class="sxs-lookup"><span data-stu-id="0b97b-136">To allow the selection of multiple objects, your cmdlet can use the [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) and [System.Management.Automation.Wildcardoptions](/dotnet/api/System.Management.Automation.WildcardOptions) classes to provide wildcard expansion support for parameter input.</span></span> <span data-ttu-id="0b97b-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span><span class="sxs-lookup"><span data-stu-id="0b97b-137">Examples of wildcard patterns are lsa\*, \*.txt, and [a-c]\*.</span></span> <span data-ttu-id="0b97b-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span><span class="sxs-lookup"><span data-stu-id="0b97b-138">Use the back-quote character (\`) as an escape character when the pattern contains a character that should be used literally.</span></span>

<span data-ttu-id="0b97b-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span><span class="sxs-lookup"><span data-stu-id="0b97b-139">Wildcard expansions of file and path names are examples of common scenarios where the cmdlet may want to allow support for path inputs when the selection of multiple objects is required.</span></span> <span data-ttu-id="0b97b-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span><span class="sxs-lookup"><span data-stu-id="0b97b-140">A common case is in the file system, where a user wants to see all files residing in the current folder.</span></span>

<span data-ttu-id="0b97b-141">You should need a customized wildcard pattern matching implementation only rarely.</span><span class="sxs-lookup"><span data-stu-id="0b97b-141">You should need a customized wildcard pattern matching implementation only rarely.</span></span> <span data-ttu-id="0b97b-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span><span class="sxs-lookup"><span data-stu-id="0b97b-142">In this case, your cmdlet should support either the full POSIX 1003.2, 3.13 specification for wildcard expansion or the following simplified subset:</span></span>

- <span data-ttu-id="0b97b-143">**Question mark (?).**</span><span class="sxs-lookup"><span data-stu-id="0b97b-143">**Question mark (?).**</span></span> <span data-ttu-id="0b97b-144">Matches any character at the specified location.</span><span class="sxs-lookup"><span data-stu-id="0b97b-144">Matches any character at the specified location.</span></span>

- <span data-ttu-id="0b97b-145">**Asterisk (\*).**</span><span class="sxs-lookup"><span data-stu-id="0b97b-145">**Asterisk (\*).**</span></span> <span data-ttu-id="0b97b-146">Matches zero or more characters starting at the specified location.</span><span class="sxs-lookup"><span data-stu-id="0b97b-146">Matches zero or more characters starting at the specified location.</span></span>

- <span data-ttu-id="0b97b-147">**Open bracket ([).**</span><span class="sxs-lookup"><span data-stu-id="0b97b-147">**Open bracket ([).**</span></span> <span data-ttu-id="0b97b-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span><span class="sxs-lookup"><span data-stu-id="0b97b-148">Introduces a pattern bracket expression that can contain characters or a range of characters.</span></span> <span data-ttu-id="0b97b-149">If a range is required, a hyphen (-) is used to indicate the range.</span><span class="sxs-lookup"><span data-stu-id="0b97b-149">If a range is required, a hyphen (-) is used to indicate the range.</span></span>

- <span data-ttu-id="0b97b-150">**Close bracket (]).**</span><span class="sxs-lookup"><span data-stu-id="0b97b-150">**Close bracket (]).**</span></span> <span data-ttu-id="0b97b-151">Ends a pattern bracket expression.</span><span class="sxs-lookup"><span data-stu-id="0b97b-151">Ends a pattern bracket expression.</span></span>

- <span data-ttu-id="0b97b-152">**Back-quote escape character (\`).**</span><span class="sxs-lookup"><span data-stu-id="0b97b-152">**Back-quote escape character (\`).**</span></span> <span data-ttu-id="0b97b-153">Indicates that the next character should be taken literally.</span><span class="sxs-lookup"><span data-stu-id="0b97b-153">Indicates that the next character should be taken literally.</span></span> <span data-ttu-id="0b97b-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span><span class="sxs-lookup"><span data-stu-id="0b97b-154">Be aware that when specifying the back-quote character from the command line (as opposed to specifying it programmatically), the back-quote escape character must be specified twice.</span></span>

> [!NOTE]
> <span data-ttu-id="0b97b-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="0b97b-155">For more information about wildcard patterns, see [Supporting Wildcards in Cmdlet Parameters](./supporting-wildcard-characters-in-cmdlet-parameters.md).</span></span>

<span data-ttu-id="0b97b-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b97b-156">The following code shows how to set wildcard options and define the wildcard pattern used for resolving the `Name` parameter for this cmdlet.</span></span>

```csharp
WildcardOptions options = WildcardOptions.IgnoreCase |
                          WildcardOptions.Compiled;
WildcardPattern wildcard = new WildcardPattern(name,options);
```

<span data-ttu-id="0b97b-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span><span class="sxs-lookup"><span data-stu-id="0b97b-157">The following code shows how to test whether the process name matches the defined wildcard pattern.</span></span> <span data-ttu-id="0b97b-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span><span class="sxs-lookup"><span data-stu-id="0b97b-158">Notice that, in this case, if the process name does not match the pattern, the cmdlet continues on to get the next process name.</span></span>

```csharp
if (!wildcard.IsMatch(processName))
{
  continue;
}
```

## <a name="code-sample"></a><span data-ttu-id="0b97b-159">Code Sample</span><span class="sxs-lookup"><span data-stu-id="0b97b-159">Code Sample</span></span>

<span data-ttu-id="0b97b-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span><span class="sxs-lookup"><span data-stu-id="0b97b-160">For the complete C# sample code, see [StopProcessSample03 Sample](./stopprocesssample03-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="0b97b-161">Define Object Types and Formatting</span><span class="sxs-lookup"><span data-stu-id="0b97b-161">Define Object Types and Formatting</span></span>

<span data-ttu-id="0b97b-162">Windows PowerShell passes information between cmdlets using .Net objects.</span><span class="sxs-lookup"><span data-stu-id="0b97b-162">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="0b97b-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b97b-163">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="0b97b-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0b97b-164">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="0b97b-165">Building the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b97b-165">Building the Cmdlet</span></span>

<span data-ttu-id="0b97b-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span><span class="sxs-lookup"><span data-stu-id="0b97b-166">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="0b97b-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="0b97b-167">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="0b97b-168">Testing the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b97b-168">Testing the Cmdlet</span></span>

<span data-ttu-id="0b97b-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span><span class="sxs-lookup"><span data-stu-id="0b97b-169">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="0b97b-170">Let's test the sample Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0b97b-170">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="0b97b-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="0b97b-171">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="0b97b-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span><span class="sxs-lookup"><span data-stu-id="0b97b-172">Start Windows PowerShell and use Stop-Proc to stop a process using the ProcessName alias for the `Name` parameter.</span></span>

    ```powershell
    PS> stop-proc -ProcessName notepad
    ```

<span data-ttu-id="0b97b-173">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="0b97b-173">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (3496)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="0b97b-174">Make the following entry on the command line.</span><span class="sxs-lookup"><span data-stu-id="0b97b-174">Make the following entry on the command line.</span></span> <span data-ttu-id="0b97b-175">Because the Name parameter is mandatory, you are prompted for it.</span><span class="sxs-lookup"><span data-stu-id="0b97b-175">Because the Name parameter is mandatory, you are prompted for it.</span></span> <span data-ttu-id="0b97b-176">Entering "!?"</span><span class="sxs-lookup"><span data-stu-id="0b97b-176">Entering "!?"</span></span> <span data-ttu-id="0b97b-177">brings up the help text associated with the parameter.</span><span class="sxs-lookup"><span data-stu-id="0b97b-177">brings up the help text associated with the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="0b97b-178">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="0b97b-178">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    (Type !? for Help.)
    Name[0]: !?
    The name of one or more processes to stop. Wildcards are permitted.
    Name[0]: notepad
    ```

- <span data-ttu-id="0b97b-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span><span class="sxs-lookup"><span data-stu-id="0b97b-179">Now make the following entry to stop all processes that match the wildcard pattern "\*note\*".</span></span> <span data-ttu-id="0b97b-180">You are prompted before stopping each process that matches the pattern.</span><span class="sxs-lookup"><span data-stu-id="0b97b-180">You are prompted before stopping each process that matches the pattern.</span></span>

    ```powershell
    PS> stop-proc -Name *note*
    ```

<span data-ttu-id="0b97b-181">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="0b97b-181">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (1112)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

<span data-ttu-id="0b97b-182">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="0b97b-182">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTEM (3712)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

<span data-ttu-id="0b97b-183">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="0b97b-183">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "ONENOTE (3592)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="0b97b-184">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0b97b-184">See Also</span></span>

[<span data-ttu-id="0b97b-185">Create a Cmdlet that Modifies the System</span><span class="sxs-lookup"><span data-stu-id="0b97b-185">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="0b97b-186">How to Create a Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0b97b-186">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="0b97b-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0b97b-187">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="0b97b-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="0b97b-188">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="0b97b-189">Supporting Wildcards in Cmdlet Parameters</span><span class="sxs-lookup"><span data-stu-id="0b97b-189">Supporting Wildcards in Cmdlet Parameters</span></span>](./supporting-wildcard-characters-in-cmdlet-parameters.md)

[<span data-ttu-id="0b97b-190">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0b97b-190">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
