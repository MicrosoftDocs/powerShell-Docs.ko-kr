---
ms.date: 09/13/2016
ms.topic: reference
title: 매개 변수 없이 Cmdlet 만들기
description: 매개 변수 없이 Cmdlet 만들기
ms.openlocfilehash: 5df27ac4c1f6dfcc3e7596d93f8db0f97aae71c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92646544"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="66f92-103">매개 변수 없이 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="66f92-103">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="66f92-104">이 섹션에서는 매개 변수를 사용 하지 않고 로컬 컴퓨터에서 정보를 검색 한 다음 파이프라인에 정보를 기록 하는 cmdlet을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-104">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="66f92-105">여기서 설명 하는 cmdlet은 로컬 컴퓨터의 프로세스에 대 한 정보를 검색 한 다음 명령줄에 해당 정보를 표시 하는 Get-Proc cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-105">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="66f92-106">Cmdlet을 작성할 때 Windows PowerShell® 참조 어셈블리가 디스크에 다운로드 됩니다 (기본적으로 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span><span class="sxs-lookup"><span data-stu-id="66f92-106">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="66f92-107">GAC (전역 어셈블리 캐시)에 설치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-107">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="66f92-108">Cmdlet 이름 지정</span><span class="sxs-lookup"><span data-stu-id="66f92-108">Naming the Cmdlet</span></span>

<span data-ttu-id="66f92-109">Cmdlet 이름은 cmdlet이 수행 하는 동작을 나타내는 동사와 cmdlet이 작동 하는 항목을 나타내는 명사로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-109">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="66f92-110">이 샘플 Get-Proc cmdlet은 프로세스 개체를 검색 하기 때문에 [Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) 열거에 의해 정의 된 동사 "Get"을 사용 하 고 cmdlet이 프로세스 항목에서 작동 함을 나타내는 명사 "Proc"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-110">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="66f92-111">Cmdlet의 이름을 지정할 때는 다음 문자를 사용 하지 마세요. #, () {} [] &-/\ $;: "' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="66f92-111">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="66f92-112">@ \` .</span><span class="sxs-lookup"><span data-stu-id="66f92-112">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="66f92-113">명사 선택</span><span class="sxs-lookup"><span data-stu-id="66f92-113">Choosing a Noun</span></span>

<span data-ttu-id="66f92-114">특정 명사를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-114">You should choose a noun that is specific.</span></span> <span data-ttu-id="66f92-115">제품 이름의 축약 된 버전이 포함 된 단 수 명사를 사용 하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-115">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="66f92-116">이 유형의 cmdlet 이름 예는 " `Get-SQLServer` "입니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-116">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="66f92-117">동사 선택</span><span class="sxs-lookup"><span data-stu-id="66f92-117">Choosing a Verb</span></span>

<span data-ttu-id="66f92-118">승인 된 cmdlet 동사 이름 집합의 동사를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-118">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="66f92-119">승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-119">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="66f92-120">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="66f92-120">Defining the Cmdlet Class</span></span>

<span data-ttu-id="66f92-121">Cmdlet 이름을 선택한 후에는 cmdlet을 구현 하는 .NET 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-121">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="66f92-122">다음은이 샘플 Get-Proc cmdlet에 대 한 클래스 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-122">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="66f92-123">클래스 정의의 이전에는 구문을 사용 하 [](/dotnet/api/System.Management.Automation.CmdletAttribute) 여 `[Cmdlet(verb, noun, ...)]` 이 클래스를 cmdlet으로 식별 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-123">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="66f92-124">이는 모든 cmdlet에 대해 유일 하 게 필요한 특성이 며 Windows PowerShell 런타임에서 올바르게 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-124">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="66f92-125">필요한 경우 특성 키워드를 설정 하 여 클래스를 추가로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-125">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="66f92-126">샘플 GetProcCommand 클래스에 대 한 특성 선언은 Get-Proc cmdlet에 대 한 명사 및 verb 이름만 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-126">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="66f92-127">모든 Windows PowerShell 특성 클래스에 대해 설정할 수 있는 키워드는 특성 클래스의 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-127">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="66f92-128">Cmdlet의 클래스 이름을 지정할 때는 클래스 이름에 cmdlet 이름을 반영 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-128">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="66f92-129">이렇게 하려면 "VerbNounCommand" 형식을 사용 하 고 cmdlet 이름에 사용 되는 동사 및 명사로 "Verb" 및 "명사"를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-129">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="66f92-130">위의 클래스 정의에 표시 된 것 처럼 샘플 Get-Proc cmdlet은 GetProcCommand 라는 클래스를 정의 합니다 .이 클래스는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet) 기본 클래스에서 파생 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-130">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66f92-131">Windows PowerShell 런타임에 액세스 하는 cmdlet을 직접 정의 하려면 .NET 클래스가 [PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 기본 클래스에서 파생 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-131">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="66f92-132">이 클래스에 대 한 자세한 내용은 [매개 변수 집합을 정의 하는 Cmdlet 만들기](./adding-parameter-sets-to-a-cmdlet.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-132">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="66f92-133">Cmdlet에 대 한 클래스는 명시적으로 public으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-133">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="66f92-134">Public으로 표시 되지 않은 클래스는 기본적으로 내부로 표시 되 고 Windows PowerShell 런타임에는 검색 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-134">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="66f92-135">Windows PowerShell은 cmdlet 클래스에 대해 [Microsoft. powershell](/dotnet/api/Microsoft.PowerShell.Commands) 네임 스페이스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-135">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="66f92-136">API 네임 스페이스의 Commands 네임 스페이스에 cmdlet 클래스를 추가 하는 것이 좋습니다 (예: xxx. p. p. p. s.</span><span class="sxs-lookup"><span data-stu-id="66f92-136">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="66f92-137">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="66f92-137">Overriding an Input Processing Method</span></span>

<span data-ttu-id="66f92-138">[System.object](/dotnet/api/System.Management.Automation.Cmdlet) 클래스는 세 가지 주요 입력 처리 메서드를 제공 합니다 .이 중 하나는 Cmdlet에서 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-138">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="66f92-139">Windows PowerShell에서 레코드를 처리 하는 방법에 대 한 자세한 내용은 [Windows powershell의 작동 방식](/previous-versions//ms714658(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-139">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="66f92-140">모든 형식의 입력에 대해 Windows PowerShell 런타임은 처리를 사용 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-140">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="66f92-141">Cmdlet에서 일부 전처리 또는 설치를 수행 해야 하는 경우이 메서드를 재정의 하 여이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-141">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="66f92-142">Windows PowerShell은 "record" 라는 용어를 사용 하 여 cmdlet이 호출 될 때 제공 되는 매개 변수 값 집합을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-142">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="66f92-143">Cmdlet이 파이프라인 입력을 허용 하는 경우 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 고 필요에 따라 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-143">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="66f92-144">예를 들어 cmdlet은 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 를 사용 하 여 모든 입력을 수집한 다음, cmdlet과 같이 한 번에 하나의 요소가 아닌 전체적으로 입력에 대해 작동 하는 경우 두 메서드를 재정의할 수 있습니다. `Sort-Object`</span><span class="sxs-lookup"><span data-stu-id="66f92-144">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="66f92-145">Cmdlet이 파이프라인 입력을 사용 하지 않는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-145">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="66f92-146">이 메서드는 정렬 cmdlet의 경우와 같이 한 번에 하나의 요소에 대해 실행 될 수 [없는 경우에](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 는이 메서드를 사용 하는 것이 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-146">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="66f92-147">이 샘플 Get-Proc cmdlet은 파이프라인 입력을 수신 해야 하기 때문에 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 고에 대 한 기본 구현을 [사용 하며,](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)이 [는 system.object를](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-147">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="66f92-148">[ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 재정의는 프로세스를 검색 하 고 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드를 사용 하 여이를 명령줄에 기록 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-148">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="66f92-149">입력 처리에 대해 기억할 사항</span><span class="sxs-lookup"><span data-stu-id="66f92-149">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="66f92-150">입력의 기본 소스는 명령줄에서 사용자가 제공 하는 명시적 개체 (예: 문자열)입니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-150">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="66f92-151">자세한 내용은 [명령줄 입력을 처리 하는 Cmdlet 만들기](./adding-parameters-that-process-command-line-input.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-151">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="66f92-152">입력 처리 메서드는 파이프라인의 업스트림 cmdlet 출력 개체에서 입력을 받을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-152">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="66f92-153">자세한 내용은 [파이프라인을 만들어 파이프라인 입력 처리를](./adding-parameters-that-process-pipeline-input.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-153">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="66f92-154">Cmdlet은 명령줄 및 파이프라인 원본 조합에서 입력을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-154">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="66f92-155">다운스트림 cmdlet은 오랜 시간 동안 반환 되지 않을 수도 있고 그렇지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-155">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="66f92-156">이러한 이유로, cmdlet의 입력 처리 메서드는 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)를 호출 하는 동안 잠금을 유지 하면 안 됩니다. 특히 범위가 cmdlet 인스턴스 이상으로 확장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-156">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66f92-157">Cmdlet은 [system.web. Writeline \*](/dotnet/api/System.Console.WriteLine) 또는 이와 동등한 것을 호출 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-157">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="66f92-158">Cmdlet에는 처리가 완료 될 때 정리 하는 개체 변수가 있을 수 [있습니다. 예](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 를 들어, [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)에서 파일 핸들을 열고이를 사용 하기 위해 핸들을 열어 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-158">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="66f92-159">Windows PowerShell 런타임은 개체 정리를 수행 해야 하는 항상 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 호출 하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-159">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="66f92-160">예를 들어 cmdlet을 중간에 취소 하거나 cmdlet의 일부에서 종료 오류가 발생 하는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-160">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="66f92-161">따라서 개체 정리를 필요로 하는 cmdlet은 종료자를 비롯 [한 전체 system.string](/dotnet/api/System.IDisposable) 패턴을 구현 해야 합니다. 이렇게 하면 런타임에서 처리가 끝날 때 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 와 [system.object](/dotnet/api/System.IDisposable.Dispose) 를 모두 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-161">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="66f92-162">코드 예제</span><span class="sxs-lookup"><span data-stu-id="66f92-162">Code Sample</span></span>

<span data-ttu-id="66f92-163">전체 c # 샘플 코드는 [GetProcessSample01 샘플](./getprocesssample01-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-163">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="66f92-164">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="66f92-164">Defining Object Types and Formatting</span></span>

<span data-ttu-id="66f92-165">Windows PowerShell은 .NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-165">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="66f92-166">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-166">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="66f92-167">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-167">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="66f92-168">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="66f92-168">Building the Cmdlet</span></span>

<span data-ttu-id="66f92-169">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-169">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="66f92-170">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-170">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="66f92-171">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="66f92-171">Testing the Cmdlet</span></span>

<span data-ttu-id="66f92-172">Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-172">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="66f92-173">샘플 Get-Proc cmdlet에 대 한 코드는 작지만 Windows PowerShell 런타임과 기존 .NET 개체를 계속 사용 하므로 유용 하 게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-173">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="66f92-174">Get-Proc 수행할 수 있는 작업과 출력을 사용 하는 방법을 더 잘 이해 하도록 테스트 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-174">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="66f92-175">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="66f92-175">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="66f92-176">Windows PowerShell을 시작 하 고 컴퓨터에서 실행 중인 현재 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-176">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="66f92-177">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-177">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="66f92-178">더 쉽게 조작을 위해 변수를 cmdlet 결과에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-178">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="66f92-179">프로세스 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-179">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="66f92-180">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-180">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="66f92-181">특정 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-181">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="66f92-182">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-182">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="66f92-183">이 프로세스의 시작 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-183">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="66f92-184">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-184">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="66f92-185">핸들 수가 500 보다 큰 프로세스를 가져오고 결과를 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-185">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="66f92-186">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-186">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="66f92-187">Cmdlet을 사용 `Get-Member` 하 여 각 프로세스에 사용할 수 있는 속성을 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-187">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="66f92-188">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="66f92-188">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="66f92-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="66f92-189">See Also</span></span>

[<span data-ttu-id="66f92-190">명령줄 입력을 처리 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="66f92-190">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="66f92-191">파이프라인을 만들어 파이프라인 입력 처리</span><span class="sxs-lookup"><span data-stu-id="66f92-191">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="66f92-192">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="66f92-192">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="66f92-193">[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="66f92-193">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="66f92-194">[Windows PowerShell 작동 방법](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="66f92-194">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="66f92-195">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="66f92-195">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="66f92-196">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="66f92-196">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="66f92-197">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="66f92-197">Cmdlet Samples</span></span>](./cmdlet-samples.md)
