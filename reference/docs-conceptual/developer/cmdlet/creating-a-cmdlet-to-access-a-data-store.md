---
title: 데이터 저장소에 액세스하는 Cmdlet 만들기
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 3096965ba9f99f70994f2fb5b180cc58691b04f8
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74415704"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a><span data-ttu-id="03e6c-102">데이터 저장소에 액세스하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="03e6c-102">Creating a Cmdlet to Access a Data Store</span></span>

<span data-ttu-id="03e6c-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span><span class="sxs-lookup"><span data-stu-id="03e6c-103">This section describes how to create a cmdlet that accesses stored data by way of a Windows PowerShell provider.</span></span> <span data-ttu-id="03e6c-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span><span class="sxs-lookup"><span data-stu-id="03e6c-104">This type of cmdlet uses the Windows PowerShell provider infrastructure of the Windows PowerShell runtime and, therefore, the cmdlet class must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span>

<span data-ttu-id="03e6c-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span><span class="sxs-lookup"><span data-stu-id="03e6c-105">The Select-Str cmdlet described here can locate and select strings in a file or object.</span></span> <span data-ttu-id="03e6c-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span><span class="sxs-lookup"><span data-stu-id="03e6c-106">The patterns used to identify the string can be specified explicitly through the `Path` parameter of the cmdlet or implicitly through the `Script` parameter.</span></span>

<span data-ttu-id="03e6c-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span><span class="sxs-lookup"><span data-stu-id="03e6c-107">The cmdlet is designed to use any Windows PowerShell provider that derives from [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider).</span></span> <span data-ttu-id="03e6c-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="03e6c-108">For example, the cmdlet can specify the FileSystem provider or the Variable provider that is provided by Windows PowerShell.</span></span> <span data-ttu-id="03e6c-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="03e6c-109">For more information aboutWindows PowerShell providers, see [Designing Your Windows PowerShell provider](../prog-guide/designing-your-windows-powershell-provider.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="03e6c-110">Defining the Cmdlet Class</span><span class="sxs-lookup"><span data-stu-id="03e6c-110">Defining the Cmdlet Class</span></span>

<span data-ttu-id="03e6c-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03e6c-111">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="03e6c-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span><span class="sxs-lookup"><span data-stu-id="03e6c-112">This cmdlet detects certain strings, so the verb name chosen here is "Select", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) class.</span></span> <span data-ttu-id="03e6c-113">The noun name "Str" is used because the cmdlet acts upon strings.</span><span class="sxs-lookup"><span data-stu-id="03e6c-113">The noun name "Str" is used because the cmdlet acts upon strings.</span></span> <span data-ttu-id="03e6c-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span><span class="sxs-lookup"><span data-stu-id="03e6c-114">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span> <span data-ttu-id="03e6c-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="03e6c-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="03e6c-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span><span class="sxs-lookup"><span data-stu-id="03e6c-116">The .NET class for this cmdlet must derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class, because it provides the support needed by the Windows PowerShell runtime to expose the Windows PowerShell provider infrastructure.</span></span> <span data-ttu-id="03e6c-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span><span class="sxs-lookup"><span data-stu-id="03e6c-117">Note that this cmdlet also makes use of the .NET Framework regular expressions classes, such as [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).</span></span>

<span data-ttu-id="03e6c-118">The following code is the class definition for this Select-Str cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03e6c-118">The following code is the class definition for this Select-Str cmdlet.</span></span>

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

<span data-ttu-id="03e6c-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span><span class="sxs-lookup"><span data-stu-id="03e6c-119">This cmdlet defines a default parameter set by adding the `DefaultParameterSetName` attribute keyword to the class declaration.</span></span> <span data-ttu-id="03e6c-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span><span class="sxs-lookup"><span data-stu-id="03e6c-120">The default parameter set `PatternParameterSet` is used when the `Script` parameter is not specified.</span></span> <span data-ttu-id="03e6c-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span><span class="sxs-lookup"><span data-stu-id="03e6c-121">For more information about this parameter set, see the `Pattern` and `Script` parameter discussion in the following section.</span></span>

## <a name="defining-parameters-for-data-access"></a><span data-ttu-id="03e6c-122">Defining Parameters for Data Access</span><span class="sxs-lookup"><span data-stu-id="03e6c-122">Defining Parameters for Data Access</span></span>

<span data-ttu-id="03e6c-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span><span class="sxs-lookup"><span data-stu-id="03e6c-123">This cmdlet defines several parameters that allow the user to access and examine stored data.</span></span> <span data-ttu-id="03e6c-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span><span class="sxs-lookup"><span data-stu-id="03e6c-124">These parameters include a `Path` parameter that indicates the location of the data store, a `Pattern` parameter that specifies the pattern to be used in the search, and several other parameters that support how the search is performed.</span></span>

> [!NOTE]
> <span data-ttu-id="03e6c-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span><span class="sxs-lookup"><span data-stu-id="03e6c-125">For more information about the basics of defining parameters, see [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

### <a name="declaring-the-path-parameter"></a><span data-ttu-id="03e6c-126">Declaring the Path Parameter</span><span class="sxs-lookup"><span data-stu-id="03e6c-126">Declaring the Path Parameter</span></span>

<span data-ttu-id="03e6c-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span><span class="sxs-lookup"><span data-stu-id="03e6c-127">To locate the data store, this cmdlet must use a Windows PowerShell path to identify the Windows PowerShell provider that is designed to access the data store.</span></span> <span data-ttu-id="03e6c-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span><span class="sxs-lookup"><span data-stu-id="03e6c-128">Therefore, it defines a `Path` parameter of type string array to indicate the location of the provider.</span></span>

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

<span data-ttu-id="03e6c-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span><span class="sxs-lookup"><span data-stu-id="03e6c-129">Note that this parameter belongs to two different parameter sets and that it has an alias.</span></span>

<span data-ttu-id="03e6c-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="03e6c-130">Two [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attributes declare that the `Path` parameter belongs to the `ScriptParameterSet` and the `PatternParameterSet`.</span></span> <span data-ttu-id="03e6c-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="03e6c-131">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

<span data-ttu-id="03e6c-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span><span class="sxs-lookup"><span data-stu-id="03e6c-132">The [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) attribute declares a `PSPath` alias for the `Path` parameter.</span></span> <span data-ttu-id="03e6c-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span><span class="sxs-lookup"><span data-stu-id="03e6c-133">Declaring this alias is strongly recommended for consistency with other cmdlets that access Windows PowerShell providers.</span></span> <span data-ttu-id="03e6c-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="03e6c-134">For more information aboutWindows PowerShell paths, see "PowerShell Path Concepts" in [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

### <a name="declaring-the-pattern-parameter"></a><span data-ttu-id="03e6c-135">Declaring the Pattern Parameter</span><span class="sxs-lookup"><span data-stu-id="03e6c-135">Declaring the Pattern Parameter</span></span>

<span data-ttu-id="03e6c-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span><span class="sxs-lookup"><span data-stu-id="03e6c-136">To specify the patterns to search for, this cmdlet declares a `Pattern` parameter that is an array of strings.</span></span> <span data-ttu-id="03e6c-137">A positive result is returned when any of the patterns are found in the data store.</span><span class="sxs-lookup"><span data-stu-id="03e6c-137">A positive result is returned when any of the patterns are found in the data store.</span></span> <span data-ttu-id="03e6c-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span><span class="sxs-lookup"><span data-stu-id="03e6c-138">Note that these patterns can be compiled into an array of compiled regular expressions or an array of wildcard patterns used for literal searches.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

<span data-ttu-id="03e6c-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span><span class="sxs-lookup"><span data-stu-id="03e6c-139">When this parameter is specified, the cmdlet uses the default parameter set `PatternParameterSet`.</span></span> <span data-ttu-id="03e6c-140">In this case, the cmdlet uses the patterns specified here to select strings.</span><span class="sxs-lookup"><span data-stu-id="03e6c-140">In this case, the cmdlet uses the patterns specified here to select strings.</span></span> <span data-ttu-id="03e6c-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span><span class="sxs-lookup"><span data-stu-id="03e6c-141">In contrast, the `Script` parameter could also be used to provide a script that contains the patterns.</span></span> <span data-ttu-id="03e6c-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span><span class="sxs-lookup"><span data-stu-id="03e6c-142">The `Script` and `Pattern` parameters define two separate parameter sets, so they are mutually exclusive.</span></span>

### <a name="declaring-search-support-parameters"></a><span data-ttu-id="03e6c-143">Declaring Search Support Parameters</span><span class="sxs-lookup"><span data-stu-id="03e6c-143">Declaring Search Support Parameters</span></span>

<span data-ttu-id="03e6c-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03e6c-144">This cmdlet defines the following support parameters that can be used to modify the search capabilities of the cmdlet.</span></span>

<span data-ttu-id="03e6c-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03e6c-145">The `Script` parameter specifies a script block that can be used to provide an alternate search mechanism for the cmdlet.</span></span> <span data-ttu-id="03e6c-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span><span class="sxs-lookup"><span data-stu-id="03e6c-146">The script must contain the patterns used for matching and return a [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) object.</span></span> <span data-ttu-id="03e6c-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span><span class="sxs-lookup"><span data-stu-id="03e6c-147">Note that this parameter is also the unique parameter that identifies the `ScriptParameterSet` parameter set.</span></span> <span data-ttu-id="03e6c-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span><span class="sxs-lookup"><span data-stu-id="03e6c-148">When the Windows PowerShell runtime sees this parameter, it uses only parameters that belong to the `ScriptParameterSet` parameter set.</span></span>

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

<span data-ttu-id="03e6c-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span><span class="sxs-lookup"><span data-stu-id="03e6c-149">The `SimpleMatch` parameter is a switch parameter that indicates whether the cmdlet is to explicitly match the patterns as they are supplied.</span></span> <span data-ttu-id="03e6c-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span><span class="sxs-lookup"><span data-stu-id="03e6c-150">When the user specifies the parameter at the command line (`true`), the cmdlet uses the patterns as they are supplied.</span></span> <span data-ttu-id="03e6c-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span><span class="sxs-lookup"><span data-stu-id="03e6c-151">If the parameter is not specified (`false`), the cmdlet uses regular expressions.</span></span> <span data-ttu-id="03e6c-152">The default for this parameter is `false`.</span><span class="sxs-lookup"><span data-stu-id="03e6c-152">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

<span data-ttu-id="03e6c-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span><span class="sxs-lookup"><span data-stu-id="03e6c-153">The `CaseSensitive` parameter is a switch parameter that indicates whether a case-sensitive search is performed.</span></span> <span data-ttu-id="03e6c-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span><span class="sxs-lookup"><span data-stu-id="03e6c-154">When the user specifies the parameter at the command line (`true`), the cmdlet checks for the uppercase and lowercase of characters when comparing patterns.</span></span> <span data-ttu-id="03e6c-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span><span class="sxs-lookup"><span data-stu-id="03e6c-155">If the parameter is not specified (`false`), the cmdlet does not distinguish between uppercase and lowercase.</span></span> <span data-ttu-id="03e6c-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span><span class="sxs-lookup"><span data-stu-id="03e6c-156">For example "MyFile" and "myfile" would both be returned as positive hits.</span></span> <span data-ttu-id="03e6c-157">The default for this parameter is `false`.</span><span class="sxs-lookup"><span data-stu-id="03e6c-157">The default for this parameter is `false`.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

<span data-ttu-id="03e6c-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span><span class="sxs-lookup"><span data-stu-id="03e6c-158">The `Exclude` and `Include` parameters identify items that are explicitly excluded from or included in the search.</span></span> <span data-ttu-id="03e6c-159">By default, the cmdlet will search all items in the data store.</span><span class="sxs-lookup"><span data-stu-id="03e6c-159">By default, the cmdlet will search all items in the data store.</span></span> <span data-ttu-id="03e6c-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span><span class="sxs-lookup"><span data-stu-id="03e6c-160">However, to limit the search performed by the cmdlet, these parameters can be used to explicitly indicate items to be included in the search or omitted.</span></span>

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a><span data-ttu-id="03e6c-161">Declaring Parameter Sets</span><span class="sxs-lookup"><span data-stu-id="03e6c-161">Declaring Parameter Sets</span></span>

<span data-ttu-id="03e6c-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span><span class="sxs-lookup"><span data-stu-id="03e6c-162">This cmdlet uses two parameter sets (`ScriptParameterSet` and `PatternParameterSet`, which is the default) as the names of two parameter sets used in data access.</span></span> <span data-ttu-id="03e6c-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span><span class="sxs-lookup"><span data-stu-id="03e6c-163">`PatternParameterSet` is the default parameter set and is used when the `Pattern` parameter is specified.</span></span> <span data-ttu-id="03e6c-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span><span class="sxs-lookup"><span data-stu-id="03e6c-164">`ScriptParameterSet` is used when the user specifies an alternate search mechanism through the `Script` parameter.</span></span> <span data-ttu-id="03e6c-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span><span class="sxs-lookup"><span data-stu-id="03e6c-165">For more information about parameter sets, see [Adding Parameter Sets to a Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

## <a name="overriding-input-processing-methods"></a><span data-ttu-id="03e6c-166">Overriding Input Processing Methods</span><span class="sxs-lookup"><span data-stu-id="03e6c-166">Overriding Input Processing Methods</span></span>

<span data-ttu-id="03e6c-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span><span class="sxs-lookup"><span data-stu-id="03e6c-167">Cmdlets must override one or more of the input processing methods for the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span> <span data-ttu-id="03e6c-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="03e6c-168">For more information about the input processing methods, see [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="03e6c-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span><span class="sxs-lookup"><span data-stu-id="03e6c-169">This cmdlet overrides the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method to build an array of compiled regular expressions at startup.</span></span> <span data-ttu-id="03e6c-170">This increases performance during searches that do not use simple matching.</span><span class="sxs-lookup"><span data-stu-id="03e6c-170">This increases performance during searches that do not use simple matching.</span></span>

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

<span data-ttu-id="03e6c-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span><span class="sxs-lookup"><span data-stu-id="03e6c-171">This cmdlet also overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to process the string selections that the user makes on the command line.</span></span> <span data-ttu-id="03e6c-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span><span class="sxs-lookup"><span data-stu-id="03e6c-172">It writes the results of string selection in the form of a custom object by calling a private **MatchString** method.</span></span>

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a><span data-ttu-id="03e6c-173">Accessing Content</span><span class="sxs-lookup"><span data-stu-id="03e6c-173">Accessing Content</span></span>

<span data-ttu-id="03e6c-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span><span class="sxs-lookup"><span data-stu-id="03e6c-174">Your cmdlet must open the provider indicated by the Windows PowerShell path so that it can access the data.</span></span> <span data-ttu-id="03e6c-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span><span class="sxs-lookup"><span data-stu-id="03e6c-175">The [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) object for the runspace is used for access to the provider, while the [System.Management.Automation.PSCmdlet.Invokeprovider\*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) property of the cmdlet is used to open the provider.</span></span> <span data-ttu-id="03e6c-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span><span class="sxs-lookup"><span data-stu-id="03e6c-176">Access to content is provided by retrieval of the [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) object for the provider opened.</span></span>

<span data-ttu-id="03e6c-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span><span class="sxs-lookup"><span data-stu-id="03e6c-177">This sample Select-Str cmdlet uses the [System.Management.Automation.Providerintrinsics.Content\*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) property to expose the content to scan.</span></span> <span data-ttu-id="03e6c-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span><span class="sxs-lookup"><span data-stu-id="03e6c-178">It can then call the [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader\*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) method, passing the required Windows PowerShell path.</span></span>

## <a name="code-sample"></a><span data-ttu-id="03e6c-179">Code Sample</span><span class="sxs-lookup"><span data-stu-id="03e6c-179">Code Sample</span></span>

<span data-ttu-id="03e6c-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03e6c-180">The following code shows the implementation of this version of this Select-Str cmdlet.</span></span> <span data-ttu-id="03e6c-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03e6c-181">Note that this code includes the cmdlet class, private methods used by the cmdlet, and the Windows PowerShell snap-in code used to register the cmdlet.</span></span> <span data-ttu-id="03e6c-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span><span class="sxs-lookup"><span data-stu-id="03e6c-182">For more information about registering the cmdlet, see [Building the Cmdlet](#defining-the-cmdlet-class).</span></span>

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a><span data-ttu-id="03e6c-183">Building the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="03e6c-183">Building the Cmdlet</span></span>

<span data-ttu-id="03e6c-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span><span class="sxs-lookup"><span data-stu-id="03e6c-184">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="03e6c-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span><span class="sxs-lookup"><span data-stu-id="03e6c-185">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="03e6c-186">Testing the Cmdlet</span><span class="sxs-lookup"><span data-stu-id="03e6c-186">Testing the Cmdlet</span></span>

<span data-ttu-id="03e6c-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span><span class="sxs-lookup"><span data-stu-id="03e6c-187">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="03e6c-188">The following procedure can be used to test the sample Select-Str cmdlet.</span><span class="sxs-lookup"><span data-stu-id="03e6c-188">The following procedure can be used to test the sample Select-Str cmdlet.</span></span>

1. <span data-ttu-id="03e6c-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span><span class="sxs-lookup"><span data-stu-id="03e6c-189">Start Windows PowerShell, and search the Notes file for occurrences of lines with the expression ".NET".</span></span> <span data-ttu-id="03e6c-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span><span class="sxs-lookup"><span data-stu-id="03e6c-190">Note that the quotation marks around the name of the path are required only if the path consists of more than one word.</span></span>

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    <span data-ttu-id="03e6c-191">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="03e6c-191">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. <span data-ttu-id="03e6c-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span><span class="sxs-lookup"><span data-stu-id="03e6c-192">Search the Notes file for occurrences of lines with the word "over", followed by any other text.</span></span> <span data-ttu-id="03e6c-193">The `SimpleMatch` parameter is using the default value of `false`.</span><span class="sxs-lookup"><span data-stu-id="03e6c-193">The `SimpleMatch` parameter is using the default value of `false`.</span></span> <span data-ttu-id="03e6c-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span><span class="sxs-lookup"><span data-stu-id="03e6c-194">The search is case-insensitive because the `CaseSensitive` parameter is set to `false`.</span></span>

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    <span data-ttu-id="03e6c-195">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="03e6c-195">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. <span data-ttu-id="03e6c-196">Search the Notes file using a regular expression as the pattern.</span><span class="sxs-lookup"><span data-stu-id="03e6c-196">Search the Notes file using a regular expression as the pattern.</span></span> <span data-ttu-id="03e6c-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span><span class="sxs-lookup"><span data-stu-id="03e6c-197">The cmdlet searches for alphabetical characters and blank spaces enclosed in parentheses.</span></span>

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    <span data-ttu-id="03e6c-198">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="03e6c-198">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. <span data-ttu-id="03e6c-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span><span class="sxs-lookup"><span data-stu-id="03e6c-199">Perform a case-sensitive search of the Notes file for occurrences of the word "Parameter".</span></span>

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    <span data-ttu-id="03e6c-200">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="03e6c-200">The following output appears.</span></span>

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. <span data-ttu-id="03e6c-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span><span class="sxs-lookup"><span data-stu-id="03e6c-201">Search the variable provider shipped with Windows PowerShell for variables that have numerical values from 0 through 9.</span></span>

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    <span data-ttu-id="03e6c-202">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="03e6c-202">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. <span data-ttu-id="03e6c-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span><span class="sxs-lookup"><span data-stu-id="03e6c-203">Use a script block to search the file SelectStrCommandSample.cs for the string "Pos".</span></span> <span data-ttu-id="03e6c-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span><span class="sxs-lookup"><span data-stu-id="03e6c-204">The **cmatch** function for the script performs a case-insensitive pattern match.</span></span>

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    <span data-ttu-id="03e6c-205">The following output appears.</span><span class="sxs-lookup"><span data-stu-id="03e6c-205">The following output appears.</span></span>

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a><span data-ttu-id="03e6c-206">참고 항목</span><span class="sxs-lookup"><span data-stu-id="03e6c-206">See Also</span></span>

[<span data-ttu-id="03e6c-207">How to Create a Windows PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="03e6c-207">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[<span data-ttu-id="03e6c-208">Creating Your First Cmdlet</span><span class="sxs-lookup"><span data-stu-id="03e6c-208">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="03e6c-209">Creating a Cmdlet that Modifies the System</span><span class="sxs-lookup"><span data-stu-id="03e6c-209">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="03e6c-210">Design Your Windows PowerShell Provider</span><span class="sxs-lookup"><span data-stu-id="03e6c-210">Design Your Windows PowerShell Provider</span></span>](../prog-guide/designing-your-windows-powershell-provider.md)

<span data-ttu-id="03e6c-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="03e6c-211">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="03e6c-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="03e6c-212">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="03e6c-213">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="03e6c-213">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
