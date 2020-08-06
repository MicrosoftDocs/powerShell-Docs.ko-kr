---
title: 파이프라인 입력을 처리 하는 매개 변수 추가 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- cmdlets [PowerShell Programmer's Guide], pipeline input
- parameters [PowerShell Programmer's Guide], pipeline input
ms.openlocfilehash: a678df30a13086b317d5680ee0fbc4d3c3391235
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784557"
---
# <a name="adding-parameters-that-process-pipeline-input"></a><span data-ttu-id="b7cae-102">파이프라인 입력을 처리하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="b7cae-102">Adding Parameters that Process Pipeline Input</span></span>

<span data-ttu-id="b7cae-103">Cmdlet에 대 한 입력의 한 원본은 업스트림 cmdlet에서 발생 하는 파이프라인의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-103">One source of input for a cmdlet is an object on the pipeline that originates from an upstream cmdlet.</span></span> <span data-ttu-id="b7cae-104">이 섹션에서는 cmdlet이 파이프라인 개체를 처리할 수 있도록 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)에 설명 된 대로 매개 변수를 Get Proc cmdlet에 추가 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-104">This section describes how to add a parameter to the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)) so that the cmdlet can process pipeline objects.</span></span>

<span data-ttu-id="b7cae-105">이 cmdlet은 `Name` 파이프라인 개체의 입력을 허용 하는 매개 변수를 사용 하 고, 제공 된 이름에 따라 로컬 컴퓨터에서 프로세스 정보를 검색 한 다음, 명령줄에서 프로세스에 대 한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-105">This Get-Proc cmdlet uses a `Name` parameter that accepts input from a pipeline object, retrieves process information from the local computer based on the supplied names, and then displays information about the processes at the command line.</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="b7cae-106">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="b7cae-106">Defining the Cmdlet Class</span></span>

<span data-ttu-id="b7cae-107">Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-107">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="b7cae-108">이 cmdlet은 프로세스 정보를 검색 하므로 여기에서 선택한 동사 이름은 "Get"입니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-108">This cmdlet retrieves process information, so the verb name chosen here is "Get".</span></span> <span data-ttu-id="b7cae-109">정보를 검색할 수 있는 거의 모든 종류의 cmdlet은 명령줄 입력을 처리할 수 있습니다. 승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7cae-109">(Almost any sort of cmdlet that is capable of retrieving information can process command-line input.) For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="b7cae-110">다음은이 In-proc cmdlet에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-110">The following is the definition for this Get-Proc cmdlet.</span></span> <span data-ttu-id="b7cae-111">이 정의에 대 한 세부 정보는 [첫 번째 Cmdlet을 만들](./creating-a-cmdlet-without-parameters.md)때 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-111">Details of this definition are given in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "proc")]
public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

## <a name="defining-input-from-the-pipeline"></a><span data-ttu-id="b7cae-112">파이프라인에서 입력 정의</span><span class="sxs-lookup"><span data-stu-id="b7cae-112">Defining Input from the Pipeline</span></span>

<span data-ttu-id="b7cae-113">이 섹션에서는 cmdlet에 대 한 파이프라인에서 입력을 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-113">This section describes how to define input from the pipeline for a cmdlet.</span></span> <span data-ttu-id="b7cae-114">이 Proc cmdlet은 `Name` [명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md)에 설명 된 대로 매개 변수를 나타내는 속성을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-114">This Get-Proc cmdlet defines a property that represents the `Name` parameter as described in [Adding Parameters that Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>
<span data-ttu-id="b7cae-115">매개 변수 선언에 대 한 일반 정보는 해당 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7cae-115">(See that topic for general information about declaring parameters.)</span></span>

<span data-ttu-id="b7cae-116">그러나 cmdlet이 파이프라인 입력을 처리 해야 하는 경우에는 Windows PowerShell 런타임에서 입력 값에 바인딩된 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-116">However, when a cmdlet needs to process pipeline input, it must have its parameters bound to input values by the Windows PowerShell runtime.</span></span> <span data-ttu-id="b7cae-117">이렇게 하려면 키워드를 추가 `ValueFromPipeline` 하거나 `ValueFromPipelineByProperty` 키워드를 System.web. [parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언에 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-117">To do this, you must add the `ValueFromPipeline` keyword or add the `ValueFromPipelineByProperty` keyword to the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration.</span></span> <span data-ttu-id="b7cae-118">`ValueFromPipeline`Cmdlet이 전체 입력 개체에 액세스 하는 경우 키워드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-118">Specify the `ValueFromPipeline` keyword if the cmdlet accesses the complete input object.</span></span> <span data-ttu-id="b7cae-119">`ValueFromPipelineByProperty`Cmdlet이 개체의 속성에만 액세스 하는 경우를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-119">Specify the `ValueFromPipelineByProperty` if the cmdlet accesses only a property of the object.</span></span>

<span data-ttu-id="b7cae-120">다음은 `Name` 파이프라인 입력을 허용 하는이 in-proc cmdlet의 매개 변수에 대 한 매개 변수 선언입니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-120">Here is the parameter declaration for the `Name` parameter of this Get-Proc cmdlet that accepts pipeline input.</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs" range="35-44":::

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

<span data-ttu-id="b7cae-121">이전 선언은 `ValueFromPipeline` 키워드를로 설정 하 여 `true` , 개체가 매개 변수와 동일한 형식인 경우 또는 동일한 형식으로 강제 변환할 수 있는 경우 Windows PowerShell 런타임이 매개 변수를 들어오는 개체에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-121">The previous declaration sets the `ValueFromPipeline` keyword to `true` so that the Windows PowerShell runtime will bind the parameter to the incoming object if the object is the same type as the parameter, or if it can be coerced to the same type.</span></span> <span data-ttu-id="b7cae-122">`ValueFromPipelineByPropertyName` `true` Windows PowerShell 런타임에서 속성에 대 한 들어오는 개체를 확인 하도록 키워드도로 설정 됩니다 `Name` .</span><span class="sxs-lookup"><span data-stu-id="b7cae-122">The `ValueFromPipelineByPropertyName` keyword is also set to `true` so that the Windows PowerShell runtime will check the incoming object for a `Name` property.</span></span> <span data-ttu-id="b7cae-123">들어오는 개체에 이러한 속성이 있으면 런타임은 `Name` `Name` 들어오는 개체의 속성에 매개 변수를 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-123">If the incoming object has such a property, the runtime will bind the `Name` parameter to the `Name` property of the incoming object.</span></span>

> [!NOTE]
> <span data-ttu-id="b7cae-124">`ValueFromPipeline`매개 변수에 대 한 attribute 키워드의 설정은 키워드의 설정 보다 우선 합니다 `ValueFromPipelineByPropertyName` .</span><span class="sxs-lookup"><span data-stu-id="b7cae-124">The setting of the `ValueFromPipeline` attribute keyword for a parameter takes precedence over the setting for the `ValueFromPipelineByPropertyName` keyword.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="b7cae-125">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="b7cae-125">Overriding an Input Processing Method</span></span>

<span data-ttu-id="b7cae-126">Cmdlet이 파이프라인 입력을 처리 하려면 적절 한 입력 처리 메서드를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-126">If your cmdlet is to handle pipeline input, it needs to override the appropriate input processing methods.</span></span> <span data-ttu-id="b7cae-127">기본 입력 처리 방법은 [첫 번째 Cmdlet을 만드는 데](./creating-a-cmdlet-without-parameters.md)도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-127">The basic input processing methods are introduced in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md).</span></span>

<span data-ttu-id="b7cae-128">이 cmdlet은 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 여 `Name` 사용자 또는 스크립트에서 제공 하는 매개 변수 입력을 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-128">This Get-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to handle the `Name` parameter input provided by the user or a script.</span></span> <span data-ttu-id="b7cae-129">이 메서드는 요청 된 각 프로세스 이름 또는 모든 프로세스에 대 한 프로세스를 가져옵니다. 이름이 제공 되지 않은 경우에는입니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-129">This method will get the processes for each requested process name or all processes if no name is provided.</span></span> <span data-ttu-id="b7cae-130">[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)내에서 [WriteObject (system.string, system.string)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) 호출은 파이프라인에 출력 개체를 전송 하는 데 필요한 출력 메커니즘을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-130">Notice that within [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), the call to [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) is the output mechanism for sending output objects to the pipeline.</span></span> <span data-ttu-id="b7cae-131">이 호출의 두 번째 매개 변수는 `enumerateCollection` 로 설정 되어 `true` 프로세스 개체의 배열을 열거 하도록 Windows PowerShell 런타임에 지시 하 고 명령줄에 프로세스를 한 번에 하나씩 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-131">The second parameter of this call, `enumerateCollection`, is set to `true` to tell the Windows PowerShell runtime to enumerate the array of process objects, and write one process at a time to the command line.</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="b7cae-132">코드 예제</span><span class="sxs-lookup"><span data-stu-id="b7cae-132">Code Sample</span></span>

<span data-ttu-id="b7cae-133">전체 c # 샘플 코드는 [GetProcessSample03 샘플](./getprocesssample03-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7cae-133">For the complete C# sample code, see [GetProcessSample03 Sample](./getprocesssample03-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="b7cae-134">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="b7cae-134">Defining Object Types and Formatting</span></span>

<span data-ttu-id="b7cae-135">Windows PowerShell은 .Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-135">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="b7cae-136">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-136">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="b7cae-137">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7cae-137">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="b7cae-138">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="b7cae-138">Building the Cmdlet</span></span>

<span data-ttu-id="b7cae-139">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-139">After implementing a cmdlet it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="b7cae-140">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7cae-140">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="b7cae-141">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="b7cae-141">Testing the Cmdlet</span></span>

<span data-ttu-id="b7cae-142">Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-142">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="b7cae-143">예를 들어 샘플 cmdlet에 대 한 코드를 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-143">For example, test the code for the sample cmdlet.</span></span> <span data-ttu-id="b7cae-144">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b7cae-144">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="b7cae-145">Windows PowerShell 프롬프트에서 다음 명령을 입력 하 여 파이프라인을 통해 프로세스 이름을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-145">At the Windows PowerShell prompt, enter the following commands to retrieve the process names through the pipeline.</span></span>

  ```powershell
  PS> type ProcessNames | get-proc
  ```

  <span data-ttu-id="b7cae-146">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-146">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      809      21  40856    4448    147    9.50  2288  iexplore
      737      21  26036   16348    144   22.03  3860  iexplore
       39       2   1024     388     30    0.08  3396  notepad
     3927      62  71836   26984    467  195.19  1848  OUTLOOK
  ```

- <span data-ttu-id="b7cae-147">다음 줄을 입력 하 여 `Name` "iexplore.exe" 라는 프로세스에서 속성이 있는 프로세스 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-147">Enter the following lines to get the process objects that have a `Name` property from the processes called "IEXPLORE".</span></span> <span data-ttu-id="b7cae-148">이 예에서는 `Get-Process` Windows PowerShell에서 제공 하는 cmdlet을 업스트림 명령으로 사용 하 여 "iexplore.exe" 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-148">This example uses the `Get-Process` cmdlet (provided by Windows PowerShell) as an upstream command to retrieve the "IEXPLORE" processes.</span></span>

  ```powershell
  PS> get-process iexplore | get-proc
  ```

  <span data-ttu-id="b7cae-149">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b7cae-149">The following output appears.</span></span>

  ```
  Handles  NPM(K)  PM(K)   WS(K)  VS(M)  CPU(s)    Id  ProcessName
  -------  ------  -----   ----- -----   ------    --  -----------
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
      801      21  40720    6544    142    9.52  2288  iexplore
      726      21  25872   16652    138   22.09  3860  iexplore
  ```

## <a name="see-also"></a><span data-ttu-id="b7cae-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b7cae-150">See Also</span></span>

[<span data-ttu-id="b7cae-151">명령줄 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="b7cae-151">Adding Parameters that Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="b7cae-152">첫 번째 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="b7cae-152">Creating Your First Cmdlet</span></span>](./creating-a-cmdlet-without-parameters.md)

<span data-ttu-id="b7cae-153">[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b7cae-153">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="b7cae-154">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="b7cae-154">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="b7cae-155">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="b7cae-155">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="b7cae-156">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="b7cae-156">Cmdlet Samples</span></span>](./cmdlet-samples.md)
