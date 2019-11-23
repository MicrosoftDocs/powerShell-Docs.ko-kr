---
title: Adding Parameter Sets to a Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- parameter sets [PowerShell Programmer's Guide]
ms.assetid: a6131db4-fd6e-45f1-bd47-17e7174afd56
caps.latest.revision: 8
ms.openlocfilehash: c9c0b9a7a587e856efc82b4d277cee373e3f8b38
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416317"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="5cc64-102">Cmdlet에 매개 변수 집합 추가</span><span class="sxs-lookup"><span data-stu-id="5cc64-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="5cc64-103">Things to Know About Parameter Sets</span><span class="sxs-lookup"><span data-stu-id="5cc64-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="5cc64-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span><span class="sxs-lookup"><span data-stu-id="5cc64-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="5cc64-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span><span class="sxs-lookup"><span data-stu-id="5cc64-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="5cc64-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cc64-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="5cc64-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span><span class="sxs-lookup"><span data-stu-id="5cc64-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="5cc64-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span><span class="sxs-lookup"><span data-stu-id="5cc64-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="5cc64-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span><span class="sxs-lookup"><span data-stu-id="5cc64-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="5cc64-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span><span class="sxs-lookup"><span data-stu-id="5cc64-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="5cc64-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span><span class="sxs-lookup"><span data-stu-id="5cc64-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="5cc64-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span><span class="sxs-lookup"><span data-stu-id="5cc64-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="5cc64-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span><span class="sxs-lookup"><span data-stu-id="5cc64-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="5cc64-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span><span class="sxs-lookup"><span data-stu-id="5cc64-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="5cc64-115">Declaring the Cmdlet Class</span><span class="sxs-lookup"><span data-stu-id="5cc64-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="5cc64-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5cc64-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="5cc64-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span><span class="sxs-lookup"><span data-stu-id="5cc64-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="5cc64-118">The noun name "Proc" is used because the cmdlet works on processes.</span><span class="sxs-lookup"><span data-stu-id="5cc64-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="5cc64-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span><span class="sxs-lookup"><span data-stu-id="5cc64-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="5cc64-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="5cc64-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="5cc64-121">The following code is the class definition for this Stop-Proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5cc64-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        DefaultParameterSetName = "ProcessId",
        SupportsShouldProcess = true)]
public class StopProcCommand : PSCmdlet
```

```vb
<Cmdlet(VerbsLifecycle.Stop, "Proc", DefaultParameterSetName:="ProcessId", _
SupportsShouldProcess:=True)> _
Public Class StopProcCommand
    Inherits PSCmdlet
```

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="5cc64-122">Declaring the Parameters of the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cc64-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="5cc64-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span><span class="sxs-lookup"><span data-stu-id="5cc64-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="5cc64-124">By default, this cmdlet does not pass an object through the pipeline.</span><span class="sxs-lookup"><span data-stu-id="5cc64-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="5cc64-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span><span class="sxs-lookup"><span data-stu-id="5cc64-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="5cc64-126">Declaring the Name Parameter</span><span class="sxs-lookup"><span data-stu-id="5cc64-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="5cc64-127">This input parameter allows the user to specify the names of the processes to be stopped.</span><span class="sxs-lookup"><span data-stu-id="5cc64-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="5cc64-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span><span class="sxs-lookup"><span data-stu-id="5cc64-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

```vb
<Parameter(Position:=0, ParameterSetName:="ProcessName", _
Mandatory:=True, _
ValueFromPipeline:=True, ValueFromPipelineByPropertyName:=True, _
HelpMessage:="The name of one or more processes to stop. " & _
    "Wildcards are permitted."), [Alias]("ProcessName")> _
Public Property Name() As String()
    Get
        Return processNames
    End Get
    Set(ByVal value As String())
        processNames = value
    End Set
End Property

Private processNames() As String
```

<span data-ttu-id="5cc64-129">Note also that the alias "ProcessName" is given to this parameter.</span><span class="sxs-lookup"><span data-stu-id="5cc64-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="5cc64-130">Declaring the Id Parameter</span><span class="sxs-lookup"><span data-stu-id="5cc64-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="5cc64-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span><span class="sxs-lookup"><span data-stu-id="5cc64-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="5cc64-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span><span class="sxs-lookup"><span data-stu-id="5cc64-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

```csharp
[Parameter(
           ParameterSetName = "ProcessId",
           Mandatory = true,
           ValueFromPipelineByPropertyName = true,
           ValueFromPipeline = true
)]
[Alias("ProcessId")]
public int[] Id
{
  get { return processIds; }
  set { processIds = value; }
}
private int[] processIds;
```

```vb
<Parameter(ParameterSetName:="ProcessId", _
Mandatory:=True, _
ValueFromPipelineByPropertyName:=True, _
ValueFromPipeline:=True), [Alias]("ProcessId")> _
Public Property Id() As Integer()
    Get
        Return processIds
    End Get
    Set(ByVal value As Integer())
        processIds = value
    End Set
End Property
Private processIds() As Integer
```

<span data-ttu-id="5cc64-133">Note also that the alias "ProcessId" is given to this parameter.</span><span class="sxs-lookup"><span data-stu-id="5cc64-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="5cc64-134">Declaring the InputObject Parameter</span><span class="sxs-lookup"><span data-stu-id="5cc64-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="5cc64-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span><span class="sxs-lookup"><span data-stu-id="5cc64-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="5cc64-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span><span class="sxs-lookup"><span data-stu-id="5cc64-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

```csharp
[Parameter(
           ParameterSetName = "InputObject",
           Mandatory = true,
           ValueFromPipeline = true)]
public Process[] InputObject
{
  get { return inputObject; }
  set { inputObject = value; }
}
private Process[] inputObject;
```

```vb
<Parameter(ParameterSetName:="InputObject", _
Mandatory:=True, ValueFromPipeline:=True)> _
Public Property InputObject() As Process()
    Get
        Return myInputObject
    End Get
    Set(ByVal value As Process())
        myInputObject = value
    End Set
End Property
Private myInputObject() As Process
```

<span data-ttu-id="5cc64-137">Note also that this parameter has no alias.</span><span class="sxs-lookup"><span data-stu-id="5cc64-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="5cc64-138">Declaring Parameters in Multiple Parameter Sets</span><span class="sxs-lookup"><span data-stu-id="5cc64-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="5cc64-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span><span class="sxs-lookup"><span data-stu-id="5cc64-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="5cc64-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span><span class="sxs-lookup"><span data-stu-id="5cc64-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="5cc64-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span><span class="sxs-lookup"><span data-stu-id="5cc64-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="5cc64-142">Overriding an Input Processing Method</span><span class="sxs-lookup"><span data-stu-id="5cc64-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="5cc64-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span><span class="sxs-lookup"><span data-stu-id="5cc64-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="5cc64-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span><span class="sxs-lookup"><span data-stu-id="5cc64-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="5cc64-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span><span class="sxs-lookup"><span data-stu-id="5cc64-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  switch (ParameterSetName)
  {
    case "ProcessName":
         ProcessByName();
         break;

    case "ProcessId":
         ProcessById();
         break;

    case "InputObject":
         foreach (Process process in inputObject)
         {
           SafeStopProcess(process);
         }
         break;

    default:
         throw new ArgumentException("Bad ParameterSet Name");
  } // switch (ParameterSetName...
} // ProcessRecord
```

```vb
Protected Overrides Sub ProcessRecord()
    Select Case ParameterSetName
        Case "ProcessName"
            ProcessByName()

        Case "ProcessId"
            ProcessById()

        Case "InputObject"
            Dim process As Process
            For Each process In myInputObject
                SafeStopProcess(process)
            Next process

        Case Else
            Throw New ArgumentException("Bad ParameterSet Name")
    End Select

End Sub 'ProcessRecord ' ProcessRecord
```

<span data-ttu-id="5cc64-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span><span class="sxs-lookup"><span data-stu-id="5cc64-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5cc64-147">Code Sample</span><span class="sxs-lookup"><span data-stu-id="5cc64-147">Code Sample</span></span>

<span data-ttu-id="5cc64-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5cc64-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="5cc64-149">Defining Object Types and Formatting</span><span class="sxs-lookup"><span data-stu-id="5cc64-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="5cc64-150">Windows PowerShell passes information between cmdlets using .NET objects.</span><span class="sxs-lookup"><span data-stu-id="5cc64-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="5cc64-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5cc64-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="5cc64-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="5cc64-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="5cc64-153">Building the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cc64-153">Building the Cmdlet</span></span>

<span data-ttu-id="5cc64-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span><span class="sxs-lookup"><span data-stu-id="5cc64-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="5cc64-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="5cc64-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="5cc64-156">Testing the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cc64-156">Testing the Cmdlet</span></span>

<span data-ttu-id="5cc64-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span><span class="sxs-lookup"><span data-stu-id="5cc64-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="5cc64-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span><span class="sxs-lookup"><span data-stu-id="5cc64-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="5cc64-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span><span class="sxs-lookup"><span data-stu-id="5cc64-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="5cc64-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span><span class="sxs-lookup"><span data-stu-id="5cc64-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="5cc64-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span><span class="sxs-lookup"><span data-stu-id="5cc64-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="5cc64-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5cc64-162">See Also</span></span>

[<span data-ttu-id="5cc64-163">Creating a Cmdlet that Modifies the System</span><span class="sxs-lookup"><span data-stu-id="5cc64-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="5cc64-164">How to Create a Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5cc64-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="5cc64-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5cc64-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="5cc64-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="5cc64-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="5cc64-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5cc64-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
