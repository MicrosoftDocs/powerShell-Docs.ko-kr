---
title: Cmdlet을 설정 하는 매개 변수 추가 | Microsoft Docs
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
ms.openlocfilehash: f0bff11618c18bf53b9c2a185445795a17306fa3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068840"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="93722-102">Cmdlet에 매개 변수 집합 추가</span><span class="sxs-lookup"><span data-stu-id="93722-102">Adding Parameter Sets to a Cmdlet</span></span>

<span data-ttu-id="93722-103">이 섹션에서는 추가 중지 Proc cmdlet에 매개 변수를 설정 하는 방법에 설명 합니다 (에서 설명한 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)).</span><span class="sxs-lookup"><span data-stu-id="93722-103">This section describes how to add parameter sets to the Stop-Proc cmdlet (described in [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md)).</span></span> <span data-ttu-id="93722-104">이 Programmer's이 Guide에 설명 된 다른 중지 Proc cmdlet와 마찬가지로,이 cmdlet은 하려고 Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 (에서 설명한 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="93722-104">Similar to the other Stop-Proc cmdlets described in this Programmer's Guide, this cmdlet attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

<span data-ttu-id="93722-105">이 섹션의에서 항목에서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-105">Topics in this section include the following:</span></span>

- [<span data-ttu-id="93722-106">매개 변수 집합에 대해 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="93722-106">Things to Know About Parameter Sets</span></span>](#Adding-Parameter-Sets-to-a-Cmdlet)

- [<span data-ttu-id="93722-107">Cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="93722-107">Declaring the Cmdlet Class</span></span>](#Declaring-the-Cmdlet-Class)

- [<span data-ttu-id="93722-108">Cmdlet의 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-108">Declaring the Parameters of the Cmdlet</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="93722-109">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-109">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="93722-110">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="93722-110">Code Sample</span></span>](#Declaring-the-Parameters-of-the-Cmdlet)

- [<span data-ttu-id="93722-111">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="93722-111">Defining Object Types and Formatting</span></span>](#Defining-Object-Types-and-Formatting)

- [<span data-ttu-id="93722-112">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="93722-112">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="93722-113">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="93722-113">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="93722-114">매개 변수 집합에 대해 알아야 할 내용</span><span class="sxs-lookup"><span data-stu-id="93722-114">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="93722-115">Windows PowerShell은 함께 작동 하는 매개 변수는 그룹으로 설정 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-115">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="93722-116">Cmdlet의 매개 변수를 그룹화 하 여 사용자가 지정 하는 매개 변수 그룹을 기반으로 해당 기능을 변경할 수 있는 단일 cmdlet를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-116">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="93722-117">두 매개 변수 집합을 사용 하 여 다양 한 기능을 정의 하는 cmdlet의 예로 `Get-EventLog` Windows PowerShell에서 제공 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="93722-117">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="93722-118">사용자 지정 하는 경우이 cmdlet은 다른 정보를 반환 합니다 `List` 또는 `LogName` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="93722-118">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="93722-119">경우는 `LogName` 매개 변수가 지정 된, 지정 된 이벤트 로그의 이벤트에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-119">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="93722-120">경우는 `List` 매개 변수 지정 된 경우 cmdlet은 로그에 대 한 정보를 파일 자체가 (이벤트 정보가 아니라 포함)를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-120">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="93722-121">이 경우에 `List` 및 `LogName` 매개 변수 두 개의 별도 매개 변수 집합을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-121">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="93722-122">매개 변수 집합에 대 한 기억 하기 두 가지 중요 한 특정 입력에 대해 설정 하는 하나의 매개 변수를 사용 하는 Windows PowerShell 런타임에 각 매개 변수 집합 하나 이상의 매개 변수가 있어야 하는 해당 매개 변수 집합에 대 한 고유 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="93722-122">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="93722-123">중지 Proc cmdlet이 해당 마지막 지점을 보여 주기 위해 세 개의 매개 변수 집합을 사용 합니다. `ProcessName`, `ProcessId`, 및 `InputObject`합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-123">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="93722-124">각 매개 변수 집합에 다른 매개 변수 집합에 없는 매개 변수가 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-124">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="93722-125">매개 변수 집합에는 다른 매개 변수를 공유할 수 있지만 고유한 매개 변수를 사용 하는 cmdlet `ProcessName`, `ProcessId`, 및 `InputObject` Windows PowerShell 런타임을 사용 해야 하는 매개 변수 집합을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-125">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="93722-126">Cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="93722-126">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="93722-127">Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-127">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="93722-128">이 cmdlet에 대 한 수명 주기 동사 "Stop" cmdlet은 시스템 프로세스를 중지 하기 때문에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93722-128">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="93722-129">Cmdlet은 프로세스에서 작동 하기 때문에 "Proc" 명사 이름 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="93722-129">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="93722-130">다음 선언에는 cmdlet 클래스 이름을 cmdlet 동사 / 명사 이름이 내용이 반영 되었는지 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-130">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="93722-131">Cmdlet은 승인 된 동사 이름에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-131">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="93722-132">다음 코드는이 중지 Proc cmdlet에 대 한 클래스 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="93722-132">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="93722-133">Cmdlet의 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-133">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="93722-134">(정의 된 매개 변수 집합 이러한 매개 변수)에 있는 cmdlet에 대 한 입력으로 필요한 세 가지 매개 변수를 정의 하는이 cmdlet은 뿐만 `Force` 가 관리 하는 매개 변수 및 `PassThru` cmdlet를 보낼지 여부를 결정 하는 매개 변수는 파이프라인을 통해 개체를 출력 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-134">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="93722-135">기본적으로이 cmdlet은 파이프라인을 통해 개체를 전달 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-135">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="93722-136">이러한 마지막 두 매개 변수에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-136">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="93722-137">Name 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-137">Declaring the Name Parameter</span></span>

<span data-ttu-id="93722-138">이 입력된 매개 변수를 중지할 프로세스의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-138">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="93722-139">`ParameterSetName` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성을 지정 합니다 `ProcessName` 이 매개 변수에 대 한 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-139">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

[!code-csharp[StopProcessSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/StopProcessSample04/StopProcessSample04.cs#L44-L58 "StopProcessSample04.cs")]

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

<span data-ttu-id="93722-140">이 매개 변수를 사용 하는 "ProcessName" 별칭 지정 된는 또한 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-140">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="93722-141">Id 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-141">Declaring the Id Parameter</span></span>

<span data-ttu-id="93722-142">이 입력된 매개 변수를 중지할 프로세스의 식별자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-142">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="93722-143">`ParameterSetName` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성을 지정 합니다 `ProcessId` 매개 변수 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="93722-143">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="93722-144">이 매개 변수를 사용 하는 "ProcessId" 별칭 지정 된는 또한 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-144">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="93722-145">InputObject 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-145">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="93722-146">이 입력된 매개 변수를 중지할 프로세스에 대 한 정보를 포함 하는 입력된 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-146">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="93722-147">`ParameterSetName` 특성의 키워드를 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성을 지정 합니다 `InputObject` 이 매개 변수에 대 한 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-147">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="93722-148">이 매개 변수 없는 별칭에도 note 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-148">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="93722-149">여러 매개 변수 집합에 대 한 매개 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-149">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="93722-150">각 매개 변수 집합에 대 한 고유한 매개 변수 여야 합니다 하지만 매개 변수 둘 이상의 매개 변수 집합에 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-150">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="93722-151">이러한 경우에 공유 매개 변수를 제공 된 [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언을 각각 설정 하 고 있는 매개 변수에 속하는.</span><span class="sxs-lookup"><span data-stu-id="93722-151">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="93722-152">매개 변수는 모든 매개 변수 집합에만 매개 변수 특성을 한 번만 선언 해야를 매개 변수 이름 집합을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-152">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="93722-153">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-153">Overriding an Input Processing Method</span></span>

<span data-ttu-id="93722-154">가장 일반적인, 모든 cmdlet을 입력 처리 메서드를 재정의 해야 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.</span><span class="sxs-lookup"><span data-stu-id="93722-154">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="93722-155">이 cmdlet에는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet 개수에 관계 없이 프로세스를 처리할 수 있도록 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-155">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="93722-156">사용자는 매개 변수 집합에 따라 다양 한 메서드 호출에 지정 하는 Select 문을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-156">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="93722-157">Select 문에서 호출 하는 도우미 메서드는 여기에서 설명 되지 않지만 구현과 다음 섹션에서 전체 코드 샘플에서을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-157">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="93722-158">코드 예제</span><span class="sxs-lookup"><span data-stu-id="93722-158">Code Sample</span></span>

<span data-ttu-id="93722-159">전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample04 샘플](./stopprocesssample04-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-159">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="93722-160">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="93722-160">Defining Object Types and Formatting</span></span>

<span data-ttu-id="93722-161">Windows PowerShell.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-161">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="93722-162">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-162">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="93722-163">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-163">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="93722-164">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="93722-164">Building the Cmdlet</span></span>

<span data-ttu-id="93722-165">Cmdlet를 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell을 사용 하 여 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-165">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="93722-166">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-166">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="93722-167">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="93722-167">Testing the Cmdlet</span></span>

<span data-ttu-id="93722-168">Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-168">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="93722-169">다음은 몇 가지 테스트 보여 주는 하는 방법을 `ProcessId` 및 `InputObject` 프로세스를 중지 하려면 해당 매개 변수 집합을 테스트 하려면 매개 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="93722-169">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="93722-170">Windows powershell 시작을 사용 하 여 중지 Proc cmdlet을 실행 하는 `ProcessId` 해당 식별자를 기반으로 하는 프로세스를 중지 하려면 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-170">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="93722-171">Cmdlet을 사용 하 여이 경우에 `ProcessId` 프로세스를 중지 하려면 매개 변수를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="93722-171">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="93722-172">시작 하는 Windows powershell을 사용 하 여 중지 Proc cmdlet을 실행 합니다 `InputObject` 메모장에서 검색 한 개체에 프로세스를 중지 하려면 매개 변수 설정를 `Get-Process` 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="93722-172">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="93722-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="93722-173">See Also</span></span>

[<span data-ttu-id="93722-174">시스템을 수정 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="93722-174">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="93722-175">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="93722-175">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="93722-176">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="93722-176">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="93722-177">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="93722-177">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="93722-178">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="93722-178">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
