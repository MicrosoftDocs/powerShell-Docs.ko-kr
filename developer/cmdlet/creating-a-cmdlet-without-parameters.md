---
title: 매개 변수 없이 Cmdlet 만들기 | Microsoft Docs
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
ms.openlocfilehash: 2685215f41c96955fc662d5eee27fc0e7a31da83
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733957"
---
# <a name="creating-a-cmdlet-without-parameters"></a><span data-ttu-id="abeef-102">매개 변수 없이 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="abeef-102">Creating a Cmdlet without Parameters</span></span>

<span data-ttu-id="abeef-103">이 섹션에는 매개 변수를 사용 하지 않고 로컬 컴퓨터에서 정보를 검색 한 다음 파이프라인에 정보를 기록 하는 cmdlet을 만드는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-103">This section describes how to create a cmdlet that retrieves information from the local computer without the use of parameters, and then writes the information to the pipeline.</span></span> <span data-ttu-id="abeef-104">여기에 설명 된 cmdlet은 로컬 컴퓨터의 프로세스에 대 한 정보를 검색 하 고 다음 명령줄에서 해당 정보를 표시 하는 Get-proc cmdlet.</span><span class="sxs-lookup"><span data-stu-id="abeef-104">The cmdlet described here is a Get-Proc cmdlet that retrieves information about the processes of the local computer, and then displays that information at the command line.</span></span>

> [!NOTE]
> <span data-ttu-id="abeef-105">Cmdlet를 작성할 때 Windows PowerShell® 참조 어셈블리를 다운로드 된 디스크에 기본적으로 C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0에 주의 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-105">Be aware that when writing cmdlets, the Windows PowerShell® reference assemblies are downloaded onto disk (by default at C:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\v1.0).</span></span> <span data-ttu-id="abeef-106">이러한 전역 어셈블리 캐시 (GAC)에 설치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-106">They are not installed in the Global Assembly Cache (GAC).</span></span>

## <a name="naming-the-cmdlet"></a><span data-ttu-id="abeef-107">Cmdlet 이름 지정</span><span class="sxs-lookup"><span data-stu-id="abeef-107">Naming the Cmdlet</span></span>

<span data-ttu-id="abeef-108">Cmdlet 이름은 cmdlet 동작 사용 여부를 나타내는 동사와 명사 cmdlet을 실행 하는 항목을 나타내는 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-108">A cmdlet name consists of a verb that indicates the action the cmdlet takes and a noun that indicates the items that the cmdlet acts upon.</span></span> <span data-ttu-id="abeef-109">이 샘플 Get-proc cmdlet은 프로세스 개체를 검색 하기 때문에 사용 하 여 동사 "Get", 정의한 합니다 [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) 열거 및 명사 "Proc" 항목을 처리에서 cmdlet이 작동 하는지 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-109">Because this sample Get-Proc cmdlet retrieves process objects, it uses the verb "Get", defined by the [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) enumeration, and the noun "Proc" to indicate that the cmdlet works on process items.</span></span>

<span data-ttu-id="abeef-110">Cmdlet 이름을 지정 하는 경우 사용 하지 마십시오는 다음 문자: #, () {} &-/ \ $;: "' <> &#124; ?</span><span class="sxs-lookup"><span data-stu-id="abeef-110">When naming cmdlets, do not use any of the following characters: # , () {} [] & - /\ $ ; : " '<> &#124; ?</span></span> <span data-ttu-id="abeef-111">@ \` .</span><span class="sxs-lookup"><span data-stu-id="abeef-111">@ \` .</span></span>

### <a name="choosing-a-noun"></a><span data-ttu-id="abeef-112">명사를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-112">Choosing a Noun</span></span>

<span data-ttu-id="abeef-113">관련 된 명사를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-113">You should choose a noun that is specific.</span></span> <span data-ttu-id="abeef-114">제품 이름의 약식된 버전 접두사로 단 수 명사를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-114">It is best to use a singular noun prefixed with a shortened version of the product name.</span></span> <span data-ttu-id="abeef-115">예제에서는 cmdlet이이 종류의 이름은 "`Get-SQLServer`"입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-115">An example cmdlet name of this type is "`Get-SQLServer`".</span></span>

### <a name="choosing-a-verb"></a><span data-ttu-id="abeef-116">동사를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-116">Choosing a Verb</span></span>

<span data-ttu-id="abeef-117">Cmdlet은 승인 된 동사 이름 집합에서 동사를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-117">You should use a verb from the set of approved cmdlet verb names.</span></span> <span data-ttu-id="abeef-118">승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-118">For more information about the approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

## <a name="defining-the-cmdlet-class"></a><span data-ttu-id="abeef-119">Cmdlet 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="abeef-119">Defining the Cmdlet Class</span></span>

<span data-ttu-id="abeef-120">Cmdlet 이름, 선택 했으면 cmdlet을 구현 하는.NET 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-120">Once you have chosen a cmdlet name, define a .NET class to implement the cmdlet.</span></span> <span data-ttu-id="abeef-121">이 샘플 Get-proc cmdlet에 대 한 클래스 정의 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-121">Here is the class definition for this sample Get-Proc cmdlet:</span></span>

```csharp
[Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
```

```vb
<Cmdlet(VerbsCommon.Get, "Proc")> _
Public Class GetProcCommand
    Inherits Cmdlet
```

<span data-ttu-id="abeef-122">클래스 정의 전에 있음을 합니다 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 구문 사용 하 여 특성을 `[Cmdlet(verb, noun, ...)]`를 cmdlet으로이 클래스를 식별 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-122">Notice that previous to the class definition, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute, with the syntax `[Cmdlet(verb, noun, ...)]`, is used to identify this class as a cmdlet.</span></span> <span data-ttu-id="abeef-123">모든 cmdlet에 대 한 필수 속성 이며 올바르게 호출 하는 Windows PowerShell 런타임에 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-123">This is the only required attribute for all cmdlets, and it allows the Windows PowerShell runtime to call them correctly.</span></span> <span data-ttu-id="abeef-124">필요한 경우 추가 클래스를 선언 하려면 키워드 특성을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-124">You can set attribute keywords to further declare the class if necessary.</span></span> <span data-ttu-id="abeef-125">샘플 GetProcCommand 클래스에 대 한 특성 선언을 Get-proc cmdlet의 명사 및 동사 이름 선언 있는지 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-125">Be aware that the attribute declaration for our sample GetProcCommand class declares only the noun and verb names for the Get-Proc cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="abeef-126">Windows PowerShell의 모든 특성 클래스에 설정할 수 있는 키워드는 특성 클래스의 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-126">For all Windows PowerShell attribute classes, the keywords that you can set correspond to properties of the attribute class.</span></span>

<span data-ttu-id="abeef-127">Cmdlet의 클래스 이름 지정 때 클래스 이름에 cmdlet 이름을 반영 하도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-127">When naming the class of the cmdlet, it is a good practice to reflect the cmdlet name in the class name.</span></span> <span data-ttu-id="abeef-128">이렇게 하려면 "VerbNounCommand" 형식을 사용 하 여 및 동사와 명사 cmdlet 이름에 사용 되는 "동사" 및 "명사"를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-128">To do this, use the form "VerbNounCommand" and replace "Verb" and "Noun" with the verb and noun used in the cmdlet name.</span></span> <span data-ttu-id="abeef-129">이전 클래스 정의에 표시 된 대로 샘플 Get-proc cmdlet에서 파생 되는 GetProcCommand 라는 클래스를 정의 하는 합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-129">As is shown in the previous class definition, the sample Get-Proc cmdlet defines a class called GetProcCommand, which derives from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) base class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abeef-130">.NET 클래스에서 파생 해야 Windows PowerShell 런타임에 직접 액세스 하는 cmdlet을 정의 하려는 경우는 [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-130">If you want to define a cmdlet that accesses the Windows PowerShell runtime directly, your .NET class should derive from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) base class.</span></span> <span data-ttu-id="abeef-131">이 클래스에 대 한 자세한 내용은 참조 하세요. [Cmdlet을 해당 정의 매개 변수 집합을 만드는](./adding-parameter-sets-to-a-cmdlet.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-131">For more information about this class, see [Creating a Cmdlet that Defines Parameter Sets](./adding-parameter-sets-to-a-cmdlet.md).</span></span>

> [!NOTE]
> <span data-ttu-id="abeef-132">Cmdlet에 대 한 클래스 해야 명시적으로 공용으로 표시 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-132">The class for a cmdlet must be explicitly marked as public.</span></span> <span data-ttu-id="abeef-133">공용으로 표시 되지 않는 클래스는 기본적으로 내부 및 Windows PowerShell 런타임에 의해 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-133">Classes that are not marked as public will default to internal and will not be found by the Windows PowerShell runtime.</span></span>

<span data-ttu-id="abeef-134">Windows PowerShell을 사용 합니다 [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) 해당 cmdlet 클래스에 대 한 네임 스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-134">Windows PowerShell uses the [Microsoft.PowerShell.Commands](/dotnet/api/Microsoft.PowerShell.Commands) namespace for its cmdlet classes.</span></span> <span data-ttu-id="abeef-135">예를 들어 xxx.PS.Commands API 네임 스페이스의 명령 네임 스페이스의 cmdlet 클래스를 배치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-135">It is recommended to place your cmdlet classes in a Commands namespace of your API namespace, for example, xxx.PS.Commands.</span></span>

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="abeef-136">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-136">Overriding an Input Processing Method</span></span>

<span data-ttu-id="abeef-137">합니다 [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) 클래스는 cmdlet를 재정의 해야 하는 중 하나 이상이 세 개의 기본 입력된 처리 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-137">The [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class provides three main input processing methods, at least one of which your cmdlet must override.</span></span> <span data-ttu-id="abeef-138">Windows PowerShell에서 레코드를 처리 하는 방법에 대 한 자세한 내용은 참조 하세요. [Windows PowerShell 작동 방식](/previous-versions//ms714658(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-138">For more information about how Windows PowerShell processes records, see [How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85)).</span></span>

<span data-ttu-id="abeef-139">Windows PowerShell 런타임에 입력의 모든 형식에 대 한 호출 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 처리를 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-139">For all types of input, the Windows PowerShell runtime calls [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) to enable processing.</span></span> <span data-ttu-id="abeef-140">Cmdlet에 몇 가지 전처리 또는 설치를 수행 해야 하는 경우이 메서드를 재정의 하 여이 수행할 수 것입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-140">If your cmdlet must perform some preprocessing or setup, it can do this by overriding this method.</span></span>

> [!NOTE]
> <span data-ttu-id="abeef-141">Windows PowerShell cmdlet를 호출할 때 제공 하는 매개 변수 값의 집합을 설명 "레코드" 라는 용어를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-141">Windows PowerShell uses the term "record" to describe the set of parameter values supplied when a cmdlet is called.</span></span>

<span data-ttu-id="abeef-142">Cmdlet가 파이프라인 입력을 수락 재정의 해야 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 및 필요에 따라는 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)메서드.</span><span class="sxs-lookup"><span data-stu-id="abeef-142">If your cmdlet accepts pipeline input, it must override the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method, and optionally the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="abeef-143">예를 들어 통해 cmdlet을 사용 하 여 모든 입력 수집 하는 경우 모두 메서드를 재정의할 수 있습니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 한 다음 입력에 하나의 요소가 아닌 전체 번으로 `Sort-Object` cmdlet은 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-143">For example, a cmdlet might override both methods if it gathers all input using [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) and then operates on the input as a whole rather than one element at a time, as the `Sort-Object` cmdlet does.</span></span>

<span data-ttu-id="abeef-144">Cmdlet은 파이프라인 입력에 수행 하지 하는 경우 재정의 해야 합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 메서드.</span><span class="sxs-lookup"><span data-stu-id="abeef-144">If your cmdlet does not take pipeline input, it should override the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method.</span></span> <span data-ttu-id="abeef-145">이 메서드 대신 자주 사용 됩니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 경우 cmdlet은 작업할 수 없습니다. 하나의 요소가 한 번에 정렬 cmdlet의 경우와 마찬가지로 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-145">Be aware that this method is frequently used in place of [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) when the cmdlet cannot operate on one element at a time, as is the case for a sorting cmdlet.</span></span>

<span data-ttu-id="abeef-146">재정의 샘플 Get-proc cmdlet이 파이프라인 입력을 수신 해야, 하므로 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드 사용에 대 한 기본 구현을 [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 하 고 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-146">Because this sample Get-Proc cmdlet must receive pipeline input, it overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method and uses the default implementations for [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) and [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing).</span></span> <span data-ttu-id="abeef-147">합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 재정의 프로세스를 검색 하 고 사용 하 여 명령줄에 기록 합니다 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 메서드.</span><span class="sxs-lookup"><span data-stu-id="abeef-147">The [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override retrieves processes and writes them to the command line using the [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) method.</span></span>

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

#### <a name="things-to-remember-about-input-processing"></a><span data-ttu-id="abeef-148">입력된 처리를 기억해 야 할 사항</span><span class="sxs-lookup"><span data-stu-id="abeef-148">Things to Remember About Input Processing</span></span>

- <span data-ttu-id="abeef-149">입력에 대 한 기본 소스는 명령줄에서 사용자가 제공한 명시적 개체 (예를 들어, 문자열).</span><span class="sxs-lookup"><span data-stu-id="abeef-149">The default source for input is an explicit object (for example, a string) provided by the user on the command line.</span></span> <span data-ttu-id="abeef-150">자세한 내용은 [프로세스 명령줄 입력 하는 Cmdlet 만들기](./adding-parameters-that-process-command-line-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-150">For more information, see [Creating a Cmdlet to Process Command Line Input](./adding-parameters-that-process-command-line-input.md).</span></span>

- <span data-ttu-id="abeef-151">입력 처리 메서드는 파이프라인에는 업스트림 cmdlet의 출력 개체에서 입력을 받을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-151">An input processing method can also receive input from the output object of an upstream cmdlet on the pipeline.</span></span> <span data-ttu-id="abeef-152">자세한 내용은 [프로세스 파이프라인 입력 하는 Cmdlet 만들기](./adding-parameters-that-process-pipeline-input.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-152">For more information, see [Creating a Cmdlet to Process Pipeline Input](./adding-parameters-that-process-pipeline-input.md).</span></span> <span data-ttu-id="abeef-153">주의 cmdlet을 조합 명령줄 입력을 수신 하 고 파이프라인 수는 원본입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-153">Be aware that your cmdlet can receive input from a combination of command-line and pipeline sources.</span></span>

- <span data-ttu-id="abeef-154">오랜 시간 동안, 또는 전혀 다운스트림 cmdlet 반환 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-154">The downstream cmdlet might not return for a long time, or not at all.</span></span> <span data-ttu-id="abeef-155">따라서 입력 cmdlet에서 메서드를 처리 해야 잠금을 보유 하지 호출 하는 동안 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject)는 범위를 벗어나는 cmdlet 인스턴스 잠금을 특히 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-155">For that reason, the input processing method in your cmdlet should not hold locks during calls to [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), especially locks for which the scope extends beyond the cmdlet instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abeef-156">Cmdlet을 호출 하지 말아야 [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) 또는 이와 동등한 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-156">Cmdlets should never call [System.Console.Writeline\*](/dotnet/api/System.Console.WriteLine) or its equivalent.</span></span>

- <span data-ttu-id="abeef-157">Cmdlet을 마치면 정리 하기 위해 개체 변수 있을 수 있습니다 처리 (에서 파일 핸들이 열릴 경우에 예를 들어, 합니다 [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) 메서드와 핸들 여 용도로 유지[ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span><span class="sxs-lookup"><span data-stu-id="abeef-157">Your cmdlet might have object variables to clean up when it is finished processing (for example, if it opens a file handle in the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method and keeps the handle open for use by [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)).</span></span> <span data-ttu-id="abeef-158">것이 Windows PowerShell 런타임에 항상 호출 하지 않습니다 고려해 야 합니다 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 개체 정리를 수행 해야 하는 메서드.</span><span class="sxs-lookup"><span data-stu-id="abeef-158">It is important to remember that the Windows PowerShell runtime does not always call the [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) method, which should perform object cleanup.</span></span>

<span data-ttu-id="abeef-159">예를 들어 [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) cmdlet 중간 취소 되거나 종료 하는 경우 cmdlet의 모든 부분에서 오류가 발생 하는 경우 호출 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-159">For example, [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) might not be called if the cmdlet is canceled midway or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="abeef-160">개체를 정리 해야 하는 cmdlet 전체 구현 해야 하므로 [System.IDisposable](/dotnet/api/System.IDisposable) 패턴을 둘 다 런타임에 호출할 수 있도록 종료자를 포함 하 여 [ System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) 하 고 [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) 처리의 끝입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-160">Therefore, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including the finalizer, so that the runtime can call both [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) at the end of processing.</span></span>

## <a name="code-sample"></a><span data-ttu-id="abeef-161">코드 예제</span><span class="sxs-lookup"><span data-stu-id="abeef-161">Code Sample</span></span>

<span data-ttu-id="abeef-162">전체 C# 코드 샘플을 참조 하십시오 [GetProcessSample01 샘플](./getprocesssample01-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-162">For the complete C# sample code, see [GetProcessSample01 Sample](./getprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="abeef-163">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="abeef-163">Defining Object Types and Formatting</span></span>

<span data-ttu-id="abeef-164">Windows PowerShell.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-164">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="abeef-165">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-165">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="abeef-166">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](/previous-versions//ms714665(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-166">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="abeef-167">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="abeef-167">Building the Cmdlet</span></span>

<span data-ttu-id="abeef-168">Cmdlet를 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell을 사용 하 여 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-168">After implementing a cmdlet, you must register it with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="abeef-169">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](/previous-versions//ms714644(v=vs.85))합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-169">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="abeef-170">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="abeef-170">Testing the Cmdlet</span></span>

<span data-ttu-id="abeef-171">Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-171">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="abeef-172">이 샘플 Get-proc cmdlet에 대 한 코드 크지 않지만 Windows PowerShell 런타임 및을 유용 하 게 있는 기존.NET 개체를 계속 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-172">The code for our sample Get-Proc cmdlet is small, but it still uses the Windows PowerShell runtime and an existing .NET object, which is enough to make it useful.</span></span> <span data-ttu-id="abeef-173">Get-proc 수행할 수 있는 작업 및 해당 출력 사용할 수 있는 방법을 더 잘 이해 하 고 테스트해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-173">Let's test it to better understand what Get-Proc can do and how its output can be used.</span></span> <span data-ttu-id="abeef-174">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-174">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

1. <span data-ttu-id="abeef-175">Windows PowerShell을 시작 하 고 컴퓨터에서 실행 중인 현재 프로세스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-175">Start Windows PowerShell, and get the current processes running on the computer.</span></span>

    ```powershell
    get-proc
    ```

    <span data-ttu-id="abeef-176">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-176">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    254      7       7664   12048  66     173.75  1200  QCTRAY
    32       2       1372   2628   31       0.04  1860  DLG
    271      6       1216   3688   33       0.03  3816  lg
    27       2       560    1920   24       0.01  1768  TpScrex
    ...
    ```

2. <span data-ttu-id="abeef-177">보다 쉽게 조작할 cmdlet 결과 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-177">Assign a variable to the cmdlet results for easier manipulation.</span></span>

    ```powershell
    $p=get-proc
    ```

3. <span data-ttu-id="abeef-178">프로세스의 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-178">Get the number of processes.</span></span>

    ```powershell
    $p.length
    ```

    <span data-ttu-id="abeef-179">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-179">The following output appears.</span></span>

    ```output
    63
    ```

4. <span data-ttu-id="abeef-180">특정 프로세스를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-180">Retrieve a specific process.</span></span>

    ```powershell
    $p[6]
    ```

    <span data-ttu-id="abeef-181">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-181">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id    ProcessName
    -------  ------  -----  -----  -----  ------  --    -----------
    1033     3       2400   3336   35     0.53    1588  rundll32
    ```

5. <span data-ttu-id="abeef-182">이 프로세스의 시작 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-182">Get the start time of this process.</span></span>

    ```powershell
    $p[6].starttime
    ```

    <span data-ttu-id="abeef-183">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-183">The following output appears.</span></span>

    ```output
    Tuesday, July 26, 2005 9:34:15 AM
    ```

    ```powershell
    $p[6].starttime.dayofyear
    ```

    ```output
    207
    ```

6. <span data-ttu-id="abeef-184">핸들 개수는 500을 초과 하는 프로세스를 가져옵니다 하 고 결과 정렬 합니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-184">Get the processes for which the handle count is greater than 500, and sort the result.</span></span>

    ```powershell
    $p | Where-Object {$_.HandleCount -gt 500 } | Sort-Object HandleCount
    ```

    <span data-ttu-id="abeef-185">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-185">The following output appears.</span></span>

    ```output
    Handles  NPM(K)  PM(K)  WS(K)  VS(M)  CPU(s)  Id   ProcessName
    -------  ------  -----  -----  -----  ------  --   ----------
    568      14      2164   4972   39     5.55    824  svchost
    716       7      2080   5332   28    25.38    468  csrss
    761      21      33060  56608  440  393.56    3300 WINWORD
    791      71      7412   4540   59     3.31    492  winlogon
    ...
    ```

7. <span data-ttu-id="abeef-186">사용 된 `Get-Member` 각 프로세스에 대해 사용할 수 있는 속성을 나열 하는 cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-186">Use the `Get-Member` cmdlet to list the properties available for each process.</span></span>

    ```powershell
    $p | Get-Member -MemberType property
    ```

    ```output
        TypeName: System.Diagnostics.Process
    ```

    <span data-ttu-id="abeef-187">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="abeef-187">The following output appears.</span></span>

    ```output
    Name                     MemberType Definition
    ----                     ---------- ----------
    BasePriority             Property   System.Int32 BasePriority {get;}
    Container                Property   System.ComponentModel.IContainer Conta...
    EnableRaisingEvents      Property   System.Boolean EnableRaisingEvents {ge...
    ...
    ```

## <a name="see-also"></a><span data-ttu-id="abeef-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="abeef-188">See Also</span></span>

[<span data-ttu-id="abeef-189">명령줄 입력을 처리 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="abeef-189">Creating a Cmdlet to Process Command Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="abeef-190">파이프라인 입력을 처리 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="abeef-190">Creating a Cmdlet to Process Pipeline Input</span></span>](./adding-parameters-that-process-pipeline-input.md)

[<span data-ttu-id="abeef-191">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="abeef-191">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="abeef-192">[확장 개체 형식 및 서식 지정](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="abeef-192">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="abeef-193">[Windows PowerShell의 작동 원리](/previous-versions//ms714658(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="abeef-193">[How Windows PowerShell Works](/previous-versions//ms714658(v=vs.85))</span></span>

<span data-ttu-id="abeef-194">[Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="abeef-194">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="abeef-195">Windows PowerShell 참조</span><span class="sxs-lookup"><span data-stu-id="abeef-195">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="abeef-196">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="abeef-196">Cmdlet Samples</span></span>](./cmdlet-samples.md)