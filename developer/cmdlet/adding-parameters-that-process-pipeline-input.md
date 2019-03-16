---
title: 파이프라인 입력을 처리 하는 매개 변수 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.assetid: 09bf70a9-7c76-4ffe-b3f0-a1d5f10a0931
caps.latest.revision: 8
ms.openlocfilehash: bd52dc8aee7975d0899083a5c2f595b17690dc33
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054767"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="ce607-102">파이프라인 입력을 처리하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="ce607-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="ce607-103">소스 cmdlet에 대 한 입력 중 하나에 업스트림 cmdlet에서 발생 하는 파이프라인에서 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="ce607-104">이 섹션에는 Get-proc cmdlet 매개 변수를 추가 하는 방법을 설명 (에서 설명한 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)) cmdlet은 파이프라인 개체를 처리할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="ce607-105">이 Get-proc cmdlet 사용을 `Name` 파이프라인 개체의 입력을 허용 하는 매개 변수는 제공 된 이름을 기반으로 하는 로컬 컴퓨터에서 프로세스 정보를 검색 하 고 다음 명령줄은 프로세스에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

<span data-ttu-id="ce607-106">이 섹션의에서 항목에서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-106">Topics in this section include the following:</span></span>

- [<span data-ttu-id="ce607-107">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="ce607-107">Defining the Cmdlet Class</span></span>](#Defining-the-Cmdlet-Class)

- [<span data-ttu-id="ce607-108">파이프라인의 입력 정의</span><span class="sxs-lookup"><span data-stu-id="ce607-108">Defining Input from the Pipeline</span></span>](#Defining-Input-from-the-Pipeline)

- [<span data-ttu-id="ce607-109">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="ce607-110">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="ce607-110">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="ce607-111">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="ce607-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="ce607-112">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="ce607-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="ce607-113">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce607-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="ce607-114">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="ce607-114">Defining the Cmdlet Class</span></span>

<span data-ttu-id="ce607-115">Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-115">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="ce607-116">이 cmdlet은 "Get" 여기에서 선택한 동사 이름 이므로 프로세스 정보를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-116">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="ce607-117">(거의 모든 종류의 정보를 검색할 수 있는 cmdlet의 명령줄 입력을 처리할 수 있습니다.) 승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-117">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ce607-118">다음은이 Get-proc cmdlet에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-118">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="ce607-119">이 정의의 세부 정보에 제공 됩니다 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-119">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="ce607-120">파이프라인의 입력 정의</span><span class="sxs-lookup"><span data-stu-id="ce607-120">Defining Input from the Pipeline</span></span>

<span data-ttu-id="ce607-121">이 섹션에는 cmdlet에 대 한 파이프라인에서 입력을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-121">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="ce607-122">Get-proc cmdlet이 나타내는 속성을 정의 합니다 `Name` 에 설명 된 대로 매개 변수 [해당 프로세스 명령줄 입력 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-122">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span> <span data-ttu-id="ce607-123">(매개 변수를 선언 하는 방법에 대 한 일반 정보에 대 한 해당 항목을 참조 하십시오.)</span><span class="sxs-lookup"><span data-stu-id="ce607-123">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="ce607-124">그러나 cmdlet을 파이프라인 입력을 처리 해야 하는 경우 해당 매개 변수 값을 입력 하는 Windows PowerShell 런타임에 의해 바인딩된 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-124">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="ce607-125">이 작업을 수행 하려면 추가 해야 합니다 `ValueFromPipeline` 키워드 또는 추가 `ValueFromPipelineByProperty` 키워드를를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언.</span><span class="sxs-lookup"><span data-stu-id="ce607-125">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="ce607-126">지정 된 `ValueFromPipeline` cmdlet은 전체 입력된 개체에 액세스 하는 경우에 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-126">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="ce607-127">지정 된 `ValueFromPipelineByProperty` cmdlet은 개체의 속성에만 액세스 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="ce607-127">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="ce607-128">에 대 한 매개 변수 선언은 같습니다는 `Name` 파이프라인 입력 허용 하는이 Get-proc cmdlet의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-128">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L35-L44 "GetProcessSample03.cs")]

```vb
<Parameter(Position:=0, ValueFromPipeline:=True, _
ValueFromPipelineByPropertyName:=True), ValidateNotNullOrEmpty()> _
Public Property Name() As String()
    Get
        Return processNames
    End Get

    Set(ByVal value As String())
        processNames = value
    End Set

End Property
```

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#GetProc03VBNameParameter](Msh_samplesgetproc03#GetProc03VBNameParameter)]  -->

<span data-ttu-id="ce607-129">이전 선언 집합을 `ValueFromPipeline` 키워드를 `true` 아니면 동일한 형식으로 강제 변환할 수는 Windows PowerShell 런타임에 바인딩될 매개 변수는 들어오는 개체 개체가 매개 변수로 동일한 형식인 경우 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-129">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="ce607-130">`ValueFromPipelineByPropertyName` 키워드를도로 설정 됩니다 `true` 는 Windows PowerShell 런타임에 들어오는 개체를 확인 하는 `Name` 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-130">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="ce607-131">런타임에 바인딩합니다 들어오는 개체에 있는 경우 이러한 속성에는 `Name` 매개 변수를는 `Name` 들어오는 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-131">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="ce607-132">설정 합니다 `ValueFromPipeline` 매개 변수 설정을 보다 우선 키워드 특성이 `ValueFromPipelineByPropertyName` 키워드입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-132">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="ce607-133">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-133">Overriding an Input Processing Method</span></span>

<span data-ttu-id="ce607-134">Cmdlet에 파이프라인 입력을 처리할 경우 적절 한 입력 처리 메서드를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-134">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="ce607-135">에 도입 된 기본 입력된 처리 메서드로 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-135">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="ce607-136">Get-proc cmdlet이 재정의 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 처리 하는 메서드는 `Name` 사용자 또는 스크립트에서 제공 하는 매개 변수 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-136">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="ce607-137">이 메서드는 제공 된 이름이 없는 경우 각 요청 된 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-137">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="ce607-138">내 있음을 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)에 대 한 호출 [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) 출력은 출력을 보내기 위한 메커니즘을 파이프라인에는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-138">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="ce607-139">이 호출의 두 번째 매개 변수 `enumerateCollection`로 설정 된 `true` 프로세스 개체의 배열을 열거 하 고 명령줄에 한 번에 하나의 프로세스를 작성 하려면 Windows PowerShell 런타임에 알려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-139">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

```csharp
protected override void ProcessRecord()
{
  // If no process names are passed to the cmdlet, get all processes.
  if (processNames == null)
  {
      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument of this call tells
      // PowerShell to enumerate the array, and send one process at a
      // time to the pipeline.
      WriteObject(Process.GetProcesses(), true);
  }
  else
  {
    // If process names are passed to the cmdlet, get and write
    // the associated processes.
    foreach (string name in processNames)
    {
      WriteObject(Process.GetProcessesByName(name), true);
    } // End foreach (string name...).
  }
}
```

```vb
Protected Overrides Sub ProcessRecord()
    Dim processes As Process()

    '/ If no process names are passed to the cmdlet, get all processes.
    If processNames Is Nothing Then
        processes = Process.GetProcesses()
    Else

        '/ If process names are specified, write the processes to the
        '/ pipeline to display them or make them available to the next cmdlet.
        For Each name As String In processNames
            '/ The second parameter of this call tells PowerShell to enumerate the
            '/ array, and send one process at a time to the pipeline.
            WriteObject(Process.GetProcessesByName(name), True)
        Next
    End If

End Sub 'ProcessRecord
```

## <a name="code-sample"></a><span data-ttu-id="ce607-140">코드 예제</span><span class="sxs-lookup"><span data-stu-id="ce607-140">Code Sample</span></span>

<span data-ttu-id="ce607-141">전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample03 샘플](./getprocesssample03-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-141">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="ce607-142">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="ce607-142">Defining Object Types and Formatting</span></span>

<span data-ttu-id="ce607-143">Windows PowerShell.Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-143">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="ce607-144">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-144">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="ce607-145">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-145">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ce607-146">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="ce607-146">Building the Cmdlet</span></span>

<span data-ttu-id="ce607-147">Windows PowerShell을 통해 Windows PowerShell을 사용 하 여 등록 해야 하는 cmdlet을 구현 하 고 나면 스냅인.</span><span class="sxs-lookup"><span data-stu-id="ce607-147">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ce607-148">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-148">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ce607-149">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce607-149">Testing the Cmdlet</span></span>

<span data-ttu-id="ce607-150">Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-150">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="ce607-151">예를 들어 샘플 cmdlet에 대 한 코드를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-151">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="ce607-152">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-152">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="ce607-153">Windows PowerShell 프롬프트에서 파이프라인을 통해 프로세스 이름을 검색 하려면 다음 명령을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-153">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

    ```powershell
    PS> type ProcessNames | get-proc
    ```

<span data-ttu-id="ce607-154">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-154">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----   ----- -----   ------    --  -----------
        809      21  40856    4448    147    9.50  2288  iexplore
        737      21  26036   16348    144   22.03  3860  iexplore
         39       2   1024     388     30    0.08  3396  notepad
       3927      62  71836   26984    467  195.19  1848  OUTLOOK
    ```

- <span data-ttu-id="ce607-155">한 프로세스 개체를 가져오려면 다음 줄을 입력 하는 `Name` "IEXPLORE" 라는 프로세스에서 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-155">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="ce607-156">이 예제에서는 `Get-Process` "IEXPLORE" 프로세스를 검색할 업스트림 명령으로 cmdlet (Windows PowerShell에서 제공).</span><span class="sxs-lookup"><span data-stu-id="ce607-156">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

    ```powershell
    PS> get-process iexplore | get-proc
    ```

<span data-ttu-id="ce607-157">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ce607-157">The following output appears.</span></span>

    ```
    Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
    -------  ------  -----      ----- -----   ------     -- -----------
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
        801      21  40720    6544    142    9.52  2288  iexplore
        726      21  25872   16652    138   22.09  3860  iexplore
    ```

## <a name="see-also"></a><span data-ttu-id="ce607-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ce607-158">See Also</span></span>

[<span data-ttu-id="ce607-159">명령줄 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="ce607-159">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="ce607-160">첫 번째 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="ce607-160">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

[<span data-ttu-id="ce607-161">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="ce607-161">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="ce607-162">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="ce607-162">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="ce607-163">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="ce607-163">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="ce607-164">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="ce607-164">Cmdlet Samples</span></span>](./cmdlet-samples.md)
