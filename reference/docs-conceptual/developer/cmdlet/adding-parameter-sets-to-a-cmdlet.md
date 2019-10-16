---
title: Cmdlet에 매개 변수 집합 추가 | Microsoft Docs
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
ms.openlocfilehash: 59db96cf03ff7086e8c89fb45bc96fd805078ac8
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364592"
---
# <a name="adding-parameter-sets-to-a-cmdlet"></a><span data-ttu-id="95b6c-102">Cmdlet에 매개 변수 집합 추가</span><span class="sxs-lookup"><span data-stu-id="95b6c-102">Adding Parameter Sets to a Cmdlet</span></span>

## <a name="things-to-know-about-parameter-sets"></a><span data-ttu-id="95b6c-103">매개 변수 집합에 대해 알아야 할 사항</span><span class="sxs-lookup"><span data-stu-id="95b6c-103">Things to Know About Parameter Sets</span></span>

<span data-ttu-id="95b6c-104">Windows PowerShell은 함께 작동 하는 매개 변수 그룹으로 매개 변수 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-104">Windows PowerShell defines a parameter set as a group of parameters that operate together.</span></span> <span data-ttu-id="95b6c-105">Cmdlet의 매개 변수를 그룹화 하 여 사용자가 지정 하는 매개 변수 그룹에 따라 해당 기능을 변경할 수 있는 단일 cmdlet을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-105">By grouping the parameters of a cmdlet, you can create a single cmdlet that can change its functionality based on what group of parameters the user specifies.</span></span>

<span data-ttu-id="95b6c-106">다른 기능을 정의 하는 두 개의 매개 변수 집합을 사용 하는 cmdlet의 예는 Windows PowerShell에서 제공 하는 `Get-EventLog` cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-106">An example of a cmdlet that uses two parameter sets to define different functionalities is the `Get-EventLog` cmdlet that is provided by Windows PowerShell.</span></span> <span data-ttu-id="95b6c-107">이 cmdlet은 사용자가 `List` 또는 `LogName` 매개 변수를 지정할 때 다른 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-107">This cmdlet returns different information when the user specifies the `List` or `LogName` parameter.</span></span> <span data-ttu-id="95b6c-108">@No__t-0 매개 변수가 지정 된 경우 cmdlet은 지정 된 이벤트 로그의 이벤트에 대 한 정보를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-108">If the `LogName` parameter is specified, the cmdlet returns information about the events in a given event log.</span></span> <span data-ttu-id="95b6c-109">@No__t-0 매개 변수가 지정 된 경우 cmdlet은 로그 파일 자체에 대 한 정보를 반환 합니다 (포함 된 이벤트 정보가 아님).</span><span class="sxs-lookup"><span data-stu-id="95b6c-109">If the `List` parameter is specified, the cmdlet returns information about the log files themselves (not the event information they contain).</span></span> <span data-ttu-id="95b6c-110">이 경우 `List` 및 `LogName` 매개 변수는 두 개의 개별 매개 변수 집합을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-110">In this case, the `List` and `LogName` parameters identify two separate parameter sets.</span></span>

<span data-ttu-id="95b6c-111">매개 변수 집합에 대해 기억해 야 하는 두 가지 중요 한 사항은 Windows PowerShell 런타임이 특정 입력에 대해 하나의 매개 변수 집합만 사용 하 고 각 매개 변수 집합에 해당 매개 변수 집합에 대해 고유한 매개 변수를 하나 이상 포함 해야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-111">Two important things to remember about parameter sets is that the Windows PowerShell runtime uses only one parameter set for a particular input, and that each parameter set must have at least one parameter that is unique for that parameter set.</span></span>

<span data-ttu-id="95b6c-112">마지막 지점을 설명 하기 위해이 Stop Proc cmdlet은 `ProcessName`, `ProcessId` 및 `InputObject`의 세 가지 매개 변수 집합을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-112">To illustrate that last point, this Stop-Proc cmdlet uses three parameter sets: `ProcessName`, `ProcessId`, and `InputObject`.</span></span> <span data-ttu-id="95b6c-113">이러한 각 매개 변수 집합에는 다른 매개 변수 집합에 없는 매개 변수가 하나 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-113">Each of these parameter sets has one parameter that is not in the other parameter sets.</span></span> <span data-ttu-id="95b6c-114">매개 변수 집합은 다른 매개 변수를 공유할 수 있지만 cmdlet은 고유 매개 변수 `ProcessName`, `ProcessId`, `InputObject`를 사용 하 여 Windows PowerShell 런타임에서 사용 해야 하는 매개 변수 집합을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-114">The parameter sets could share other parameters, but the cmdlet uses the unique parameters `ProcessName`, `ProcessId`, and `InputObject` to identify which set of parameters that the Windows PowerShell runtime should use.</span></span>

## <a name="declaring-the-cmdlet-class"></a><span data-ttu-id="95b6c-115">Cmdlet 클래스 선언</span><span class="sxs-lookup"><span data-stu-id="95b6c-115">Declaring the Cmdlet Class</span></span>

<span data-ttu-id="95b6c-116">Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-116">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="95b6c-117">이 cmdlet의 경우 cmdlet은 시스템 프로세스를 중지 하므로 수명 주기 동사 "Stop"이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-117">For this cmdlet, the life-cycle verb "Stop" is used because the cmdlet stops system processes.</span></span> <span data-ttu-id="95b6c-118">명사 이름 "Proc"는 cmdlet이 프로세스에서 작동 하기 때문에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-118">The noun name "Proc" is used because the cmdlet works on processes.</span></span> <span data-ttu-id="95b6c-119">아래 선언에서 cmdlet 동사와 명사 이름이 cmdlet 클래스의 이름에 반영 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-119">In the declaration below, note that the cmdlet verb and noun name are reflected in the name of the cmdlet class.</span></span>

> [!NOTE]
> <span data-ttu-id="95b6c-120">승인 된 cmdlet 동사 이름에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95b6c-120">For more information about approved cmdlet verb names, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="95b6c-121">다음 코드는이 Stop Proc cmdlet에 대 한 클래스 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-121">The following code is the class definition for this Stop-Proc cmdlet.</span></span>

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

## <a name="declaring-the-parameters-of-the-cmdlet"></a><span data-ttu-id="95b6c-122">Cmdlet의 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="95b6c-122">Declaring the Parameters of the Cmdlet</span></span>

<span data-ttu-id="95b6c-123">이 cmdlet은 cmdlet에 대 한 입력으로 필요한 매개 변수 3 개 (매개 변수 집합도 정의)를 정의 하 고 cmdlet이 수행 하는 작업을 관리 하는 `Force` 매개 변수와 cmdlet이 출력 개체를 보낼지 여부를 결정 하는 `PassThru` 매개 변수를 정의 합니다. 파이프라인을 통해.</span><span class="sxs-lookup"><span data-stu-id="95b6c-123">This cmdlet defines three parameters needed as input to the cmdlet (these parameters also define the parameter sets), as well as a `Force` parameter that manages what the cmdlet does and a `PassThru` parameter that determines whether the cmdlet sends an output object through the pipeline.</span></span> <span data-ttu-id="95b6c-124">기본적으로이 cmdlet은 파이프라인을 통해 개체를 전달 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-124">By default, this cmdlet does not pass an object through the pipeline.</span></span> <span data-ttu-id="95b6c-125">이러한 마지막 두 매개 변수에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95b6c-125">For more information about these last two parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

### <a name="declaring-the-name-parameter"></a><span data-ttu-id="95b6c-126">Name 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="95b6c-126">Declaring the Name Parameter</span></span>

<span data-ttu-id="95b6c-127">사용자는이 입력 매개 변수를 사용 하 여 중지할 프로세스의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-127">This input parameter allows the user to specify the names of the processes to be stopped.</span></span> <span data-ttu-id="95b6c-128">[System.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성의 `ParameterSetName` attribute 키워드는이 매개 변수에 대해 설정 된 `ProcessName` 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-128">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessName` parameter set for this parameter.</span></span>

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

<span data-ttu-id="95b6c-129">또한이 매개 변수에는 "ProcessName" 별칭이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-129">Note also that the alias "ProcessName" is given to this parameter.</span></span>

### <a name="declaring-the-id-parameter"></a><span data-ttu-id="95b6c-130">Id 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="95b6c-130">Declaring the Id Parameter</span></span>

<span data-ttu-id="95b6c-131">사용자는이 입력 매개 변수를 사용 하 여 중지할 프로세스의 식별자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-131">This input parameter allows the user to specify the identifiers of the processes to be stopped.</span></span> <span data-ttu-id="95b6c-132">[System.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성의 `ParameterSetName` attribute 키워드는 `ProcessId` 매개 변수 집합을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-132">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `ProcessId` parameter set.</span></span>

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

<span data-ttu-id="95b6c-133">또한이 매개 변수에는 별칭 "ProcessId"가 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-133">Note also that the alias "ProcessId" is given to this parameter.</span></span>

### <a name="declaring-the-inputobject-parameter"></a><span data-ttu-id="95b6c-134">InputObject 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="95b6c-134">Declaring the InputObject Parameter</span></span>

<span data-ttu-id="95b6c-135">사용자는이 입력 매개 변수를 사용 하 여 중지할 프로세스에 대 한 정보를 포함 하는 입력 개체를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-135">This input parameter allows the user to specify an input object that contains information about the processes to be stopped.</span></span> <span data-ttu-id="95b6c-136">[System.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성의 `ParameterSetName` attribute 키워드는이 매개 변수에 대해 설정 된 `InputObject` 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-136">Note that the `ParameterSetName` attribute keyword of the [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute specifies the `InputObject` parameter set for this parameter.</span></span>

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

<span data-ttu-id="95b6c-137">또한이 매개 변수에는 별칭이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-137">Note also that this parameter has no alias.</span></span>

### <a name="declaring-parameters-in-multiple-parameter-sets"></a><span data-ttu-id="95b6c-138">여러 매개 변수 집합에서 매개 변수 선언</span><span class="sxs-lookup"><span data-stu-id="95b6c-138">Declaring Parameters in Multiple Parameter Sets</span></span>

<span data-ttu-id="95b6c-139">각 매개 변수 집합에 대 한 고유한 매개 변수가 있어야 하지만 매개 변수는 둘 이상의 매개 변수 집합에 속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-139">Although there must be a unique parameter for each parameter set, parameters can belong to more than one parameter set.</span></span> <span data-ttu-id="95b6c-140">이러한 경우 매개 변수가 속한 각 집합에 대해 shared 매개 변수를 [system.object](/dotnet/api/System.Management.Automation.ParameterAttribute) 특성 선언으로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-140">In these cases, give the shared parameter a [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) attribute declaration for each set to which that the parameter belongs.</span></span> <span data-ttu-id="95b6c-141">매개 변수가 모든 매개 변수 집합에 있는 경우 매개 변수 특성을 한 번만 선언 하면 되며 매개 변수 집합 이름을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-141">If a parameter is in all parameter sets, you only have to declare the parameter attribute once and do not need to specify the parameter set name.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="95b6c-142">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="95b6c-142">Overriding an Input Processing Method</span></span>

<span data-ttu-id="95b6c-143">모든 cmdlet은 입력 처리 메서드를 재정의 해야 합니다. 대부분의 경우 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드가 가장 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-143">Every cmdlet must override an input processing method, most often this will be the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="95b6c-144">이 cmdlet에서는 cmdlet이 원하는 수의 프로세스를 처리할 수 있도록 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-144">In this cmdlet, the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method is overridden so that the cmdlet can process any number of processes.</span></span> <span data-ttu-id="95b6c-145">사용자가 지정한 매개 변수 집합에 따라 다른 메서드를 호출 하는 Select 문이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-145">It contains a Select statement that calls a different method based on which parameter set the user has specified.</span></span>

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

<span data-ttu-id="95b6c-146">Select 문에서 호출 하는 도우미 메서드는 여기서 설명 하지 않지만, 다음 섹션의 전체 코드 샘플에서 해당 구현을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-146">The Helper methods called by the Select statement are not described here, but you can see their implementation in the complete code sample in the next section.</span></span>

## <a name="code-sample"></a><span data-ttu-id="95b6c-147">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="95b6c-147">Code Sample</span></span>

<span data-ttu-id="95b6c-148">전체 C# 샘플 코드는 [StopProcessSample04 샘플](./stopprocesssample04-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95b6c-148">For the complete C# sample code, see [StopProcessSample04 Sample](./stopprocesssample04-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="95b6c-149">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="95b6c-149">Defining Object Types and Formatting</span></span>

<span data-ttu-id="95b6c-150">Windows PowerShell은 .NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-150">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="95b6c-151">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-151">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="95b6c-152">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95b6c-152">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="95b6c-153">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="95b6c-153">Building the Cmdlet</span></span>

<span data-ttu-id="95b6c-154">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-154">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="95b6c-155">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="95b6c-155">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="95b6c-156">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="95b6c-156">Testing the Cmdlet</span></span>

<span data-ttu-id="95b6c-157">Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-157">When your cmdlet has been registered with Windows PowerShell, test it by running it on the command line.</span></span> <span data-ttu-id="95b6c-158">@No__t-0 및 `InputObject` 매개 변수를 사용 하 여 프로세스를 중지 하는 매개 변수 집합을 테스트 하는 방법을 보여 주는 몇 가지 테스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-158">Here are some tests that show how the `ProcessId` and `InputObject` parameters can be used to test their parameter sets to stop a process.</span></span>

- <span data-ttu-id="95b6c-159">Windows PowerShell이 시작 되 면 `ProcessId` 매개 변수 집합을 사용 하 여 Stop Proc cmdlet을 실행 하 여 해당 식별자를 기반으로 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-159">With Windows PowerShell started, run the Stop-Proc cmdlet with the `ProcessId` parameter set to stop a process based on its identifier.</span></span> <span data-ttu-id="95b6c-160">이 경우 cmdlet은 `ProcessId` 매개 변수 집합을 사용 하 여 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-160">In this case, the cmdlet is using the `ProcessId` parameter set to stop the process.</span></span>

    ```
    PS> stop-proc -Id 444
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="95b6c-161">Windows PowerShell을 시작한 상태에서 `InputObject` 매개 변수 집합을 사용 하 여 `Get-Process` 명령으로 검색 된 메모장 개체의 프로세스를 중지 하는 Stop Proc cmdlet을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="95b6c-161">With Windows PowerShell started, run the Stop-Proc cmdlet with the `InputObject` parameter set to stop processes on the Notepad object retrieved by the `Get-Process` command.</span></span>

    ```
    PS> get-process notepad | stop-proc
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (444)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="95b6c-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="95b6c-162">See Also</span></span>

[<span data-ttu-id="95b6c-163">시스템을 수정 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="95b6c-163">Creating a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="95b6c-164">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="95b6c-164">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="95b6c-165">[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="95b6c-165">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="95b6c-166">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="95b6c-166">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="95b6c-167">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="95b6c-167">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
