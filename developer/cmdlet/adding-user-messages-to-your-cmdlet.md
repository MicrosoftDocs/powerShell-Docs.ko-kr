---
title: 사용자 메시지를 Cmdlet에 추가 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WriteWarning
- notifications, writing
- progress notification
- WriteVerbose
- Stop-Proc
- WriteProgress
- WriteDebug
- notifications, debug
- ProgressRecord
- samples, Stop-Proc cmdlet
- notifications, progress
- notifications, warning
- WriteObject
- WriteError
- verbose notification
- ProcessRecord
- notifications, verbose
- debug notification
- cmdlet, writing notifications
- warning
- code sample, user notifications
- user notifications
ms.assetid: 14c13acb-f0b7-4613-bc7d-c361d14da1a2
caps.latest.revision: 8
ms.openlocfilehash: ffc08d2713c4bfc0938b2e07146102af8b5467d2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855989"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="3df0d-102">Cmdlet에 사용자 메시지 추가</span><span class="sxs-lookup"><span data-stu-id="3df0d-102">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="3df0d-103">Cmdlet는 여러 가지 Windows PowerShell 런타임에 의해 사용자에 게 표시 될 수 있는 메시지를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-103">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="3df0d-104">이러한 메시지 유형은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-104">These messages include the following types:</span></span>

- <span data-ttu-id="3df0d-105">일반 사용자 정보를 포함 하는 자세한 정보 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-105">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="3df0d-106">문제 해결 정보를 포함 하는 메시지를 디버그 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-106">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="3df0d-107">경고 메시지에 대 한 작업을 수행할 수 있는 cmdlet에는 알림을 포함 하는 예기치 않은 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-107">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="3df0d-108">메시지 크기에 대 한 정보를 포함 하는 cmdlet은 작업 진행률 보고서는 오래 걸리는 작업을 수행 하는 경우 완료 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-108">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="3df0d-109">Cmdlet에 쓸 수 있는 메시지 수 또는 cmdlet에 기록 하는 메시지의 형식에는 한도가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-109">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="3df0d-110">각 메시지 처리 방법 cmdlet의 입력 내에서 특정를 호출 하 여 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-110">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="3df0d-111">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3df0d-111">The StopProc Cmdlet</span></span>

<span data-ttu-id="3df0d-112">이 섹션의에서 항목에서는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-112">Topics in this section include the following:</span></span>

- [<span data-ttu-id="3df0d-113">Cmdlet을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-113">Defining the Cmdlet</span></span>](#Defining-the-Cmdlet)

- [<span data-ttu-id="3df0d-114">시스템 수정에 대 한 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-114">Defining Parameters for System Modification</span></span>](#Defining-Parameters-for-System-Modification)

- [<span data-ttu-id="3df0d-115">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-115">Overriding an Input Processing Method</span></span>](#Overriding-an-Input-Processing-Method)

- [<span data-ttu-id="3df0d-116">자세한 정보 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-116">Writing a Verbose Message</span></span>](#Writing-a-Verbose-Message)

- [<span data-ttu-id="3df0d-117">디버그 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-117">Writing a Debug Message</span></span>](#Writing-a-Debug-Message)

- [<span data-ttu-id="3df0d-118">경고 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-118">Writing a Warning Message</span></span>](#Writing-a-Warning-Message)

- [<span data-ttu-id="3df0d-119">진행률 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-119">Writing a Progress Message</span></span>](#Writing-a-Progress-Message)

- [<span data-ttu-id="3df0d-120">코드 샘플</span><span class="sxs-lookup"><span data-stu-id="3df0d-120">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="3df0d-121">개체 유형 및 서식을 정의합니다</span><span class="sxs-lookup"><span data-stu-id="3df0d-121">Define Object Types and Formatting</span></span>](#Define-Object-Types-and-Formatting)

- [<span data-ttu-id="3df0d-122">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="3df0d-122">Building the Cmdlet</span></span>](#Building-the-Cmdlet)

- [<span data-ttu-id="3df0d-123">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3df0d-123">Testing the Cmdlet</span></span>](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet"></a><span data-ttu-id="3df0d-124">Cmdlet을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-124">Defining the Cmdlet</span></span>

<span data-ttu-id="3df0d-125">Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-125">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="3df0d-126">Cmdlet의 모든 정렬 메서드를 처리 하는 입력 으로부터의 사용자 알림을 작성할 수 있습니다. 따라서 일반적으로 cmdlet은 시스템 수정 사항이 무엇 인지를 나타내는 모든 동사를 사용 하 여이 cmdlet를 명명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-126">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="3df0d-127">승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-127">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="3df0d-128">시스템을 수정 하려면 중지 Proc cmdlet은 따라서 합니다 [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) .NET 클래스에 대 한 선언을 포함 해야 합니다는 `SupportsShouldProcess` 키워드를 특성 및 설정할 `true`.</span><span class="sxs-lookup"><span data-stu-id="3df0d-128">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="3df0d-129">다음 코드는이 중지 Proc cmdlet 클래스에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-129">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="3df0d-130">이 정의 대 한 자세한 내용은 참조 하십시오 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-130">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="3df0d-131">시스템 수정에 대 한 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-131">Defining Parameters for System Modification</span></span>

<span data-ttu-id="3df0d-132">세 가지 매개 변수를 정의 하는 중지 Proc cmdlet: `Name`, `Force`, 및 `PassThru`합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-132">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="3df0d-133">이러한 매개 변수를 정의 하는 방법에 대 한 자세한 내용은 참조 하세요. [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-133">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="3df0d-134">중지 Proc cmdlet에 대 한 매개 변수 선언은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-134">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

```csharp
[Parameter(
           Position = 0,
           Mandatory = true,
           ValueFromPipeline = true,
           ValueFromPipelineByPropertyName = true
)]
public string[] Name
{
  get { return processNames; }
  set { processNames = value; }
}
private string[] processNames;

/// <summary>
/// Specify the Force parameter that allows the user to override
/// the ShouldContinue call to force the stop operation. This
/// parameter should always be used with caution.
/// </summary>
[Parameter]
public SwitchParameter Force
{
  get { return force; }
  set { force = value; }
}
private bool force;

/// <summary>
/// Specify the PassThru parameter that allows the user to specify
/// that the cmdlet should pass the process object down the pipeline
/// after the process has been stopped.
/// </summary>
[Parameter]
public SwitchParameter PassThru
{
  get { return passThru; }
  set { passThru = value; }
}
private bool passThru;
```

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="3df0d-135">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-135">Overriding an Input Processing Method</span></span>

<span data-ttu-id="3df0d-136">Cmdlet는 입력 처리 메서드를 재정의 해야, 가장 자주 [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-136">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="3df0d-137">중지 Proc cmdlet이 재정의 [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 처리 방법을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-137">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="3df0d-138">중지 Proc cmdlet의이 구현에서 자세한 정보 메시지, 디버그 메시지 및 경고 메시지를 쓸 호출은 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-138">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="3df0d-139">이 메서드를 호출 하는 방법에 대 한 자세한 내용은 합니다 [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드 참조 [시스템을 수정 하는 Cmdlet를 만들](./creating-a-cmdlet-that-modifies-the-system.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-139">For more information about how this method calls the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.Shouldcontinue\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="3df0d-140">자세한 정보 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-140">Writing a Verbose Message</span></span>

<span data-ttu-id="3df0d-141">합니다 [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 메서드는 특정 오류 조건에 관련 된 일반 사용자 수준 정보를 쓰는 데 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-141">The [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="3df0d-142">다른 명령 처리를 계속 하려면 시스템 관리자가 해당 정보를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-142">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="3df0d-143">또한이 메서드를 사용 하 여 기록 된 정보는 필요에 따라 지역화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-143">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="3df0d-144">이 중지 Proc cmdlet에서 다음 코드를 두 번 호출을 보여 줍니다 합니다 [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 재정의 메서드에서 [System.Management.Automation.Cmdlet.Processrecord\* ](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.</span><span class="sxs-lookup"><span data-stu-id="3df0d-144">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="3df0d-145">디버그 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-145">Writing a Debug Message</span></span>

<span data-ttu-id="3df0d-146">[System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 메서드 cmdlet의 작업 문제 해결에 사용할 수 있는 디버그 메시지 쓰기를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-146">The [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="3df0d-147">메서드를 처리 하는 입력에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-147">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="3df0d-148">Windows PowerShell도 정의 `Debug` 모두 자세한 정보를 제공 하 고 디버그 정보를 제공 하는 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-148">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="3df0d-149">Cmdlet이 매개이 변수를 지 원하는 경우 되지 않아도 호출 [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 호출 하는 동일한 코드에서 [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="3df0d-149">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.Writeverbose\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="3df0d-150">코드 샘플 중지 Proc cmdlet에서 다음 두 섹션에 대 한 호출을 표시 합니다 [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 재정의 메서드에서 [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.</span><span class="sxs-lookup"><span data-stu-id="3df0d-150">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="3df0d-151">이 디버그 메시지는 바로 앞에 쓰여집니다 [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-151">This debug message is written immediately before [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="3df0d-152">이 디버그 메시지는 바로 앞에 쓰여집니다 [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-152">This debug message is written immediately before [System.Management.Automation.Cmdlet.Writeobject\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="3df0d-153">Windows PowerShell에 모든 항목을 자동으로 라우팅합니다 [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 추적 인프라 및 cmdlet을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-153">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.Writedebug\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="3df0d-154">이 cmdlet에서 추가 개발 작업을 수행 하지 않아도 호스팅 응용 프로그램, 파일 또는 디버거를 추적할 메서드 호출을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-154">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="3df0d-155">다음 명령줄 항목 추적 작업을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-155">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="3df0d-156">**PS > 식을 추적 중지 proc-proc.log 파일-명령 중지 proc 메모장**</span><span class="sxs-lookup"><span data-stu-id="3df0d-156">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="3df0d-157">경고 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-157">Writing a Warning Message</span></span>

<span data-ttu-id="3df0d-158">합니다 [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 메서드 cmdlet 예기치 않은 결과 예를 들어, 읽기 전용 파일을 덮어쓸 수 있는 작업을 수행 하려고 할 때 경고를 작성 하는 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-158">The [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="3df0d-159">샘플 프로시저 중지 cmdlet에서 다음 코드에 대 한 호출을 보여 줍니다 합니다 [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) 재정의 메서드에서 [ System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드.</span><span class="sxs-lookup"><span data-stu-id="3df0d-159">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.Writewarning\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.Processrecord\*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="3df0d-160">진행률 메시지를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-160">Writing a Progress Message</span></span>

<span data-ttu-id="3df0d-161">합니다 [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) cmdlet 작업 소요 시간을 들여야 하는 경우 진행률 메시지를 쓰는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-161">The [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="3df0d-162">에 대 한 호출 [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 전달 된 [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) 사용자에 게 렌더링에 대 한 호스팅 응용 프로그램에 전송 되는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-162">A call to [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="3df0d-163">이 프로시저 중지 cmdlet에 대 한 호출을 다루지 않습니다 합니다 [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 메서드.</span><span class="sxs-lookup"><span data-stu-id="3df0d-163">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.Writeprogress\*](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="3df0d-164">다음 코드는 항목을 복사 하려고 하는 cmdlet에 의해 기록 되는 진행률 메시지의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-164">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="3df0d-165">코드 예제</span><span class="sxs-lookup"><span data-stu-id="3df0d-165">Code Sample</span></span>

<span data-ttu-id="3df0d-166">전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample02 샘플](./stopprocesssample02-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-166">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="3df0d-167">개체 유형 및 서식을 정의합니다</span><span class="sxs-lookup"><span data-stu-id="3df0d-167">Define Object Types and Formatting</span></span>

<span data-ttu-id="3df0d-168">Windows PowerShell.NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-168">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="3df0d-169">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-169">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="3df0d-170">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-170">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="3df0d-171">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="3df0d-171">Building the Cmdlet</span></span>

<span data-ttu-id="3df0d-172">Cmdlet를 구현한 후 등록 해야 Windows PowerShell을 사용 하 여 Windows PowerShell 스냅인을 통해.</span><span class="sxs-lookup"><span data-stu-id="3df0d-172">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="3df0d-173">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-173">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="3df0d-174">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3df0d-174">Testing the Cmdlet</span></span>

<span data-ttu-id="3df0d-175">Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-175">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="3df0d-176">샘플 프로시저 중지 cmdlet를 테스트해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-176">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="3df0d-177">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-177">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="3df0d-178">다음 명령줄 항목 "NOTEPAD" 라는 프로세스를 중지, 자세한 알림을 제공 하 고 디버그 정보를 인쇄 하려면 중지 프로시저를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-178">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

<span data-ttu-id="3df0d-179">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3df0d-179">The following output appears.</span></span>

    ```
    VERBOSE: Attempting to stop process " notepad ".
    DEBUG: Acquired name for pid 5584 : "notepad"

    Confirm
    Continue with this operation?
    [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"): Y

    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (5584)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    VERBOSE: Stopped process "notepad", pid 5584.
    ```

## <a name="see-also"></a><span data-ttu-id="3df0d-180">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3df0d-180">See Also</span></span>

[<span data-ttu-id="3df0d-181">시스템을 수정 하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="3df0d-181">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="3df0d-182">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="3df0d-182">How to Create a Windows PowerShell Cmdlet</span></span>](http://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[<span data-ttu-id="3df0d-183">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="3df0d-183">Extending Object Types and Formatting</span></span>](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="3df0d-184">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="3df0d-184">How to Register Cmdlets, Providers, and Host Applications</span></span>](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="3df0d-185">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3df0d-185">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
