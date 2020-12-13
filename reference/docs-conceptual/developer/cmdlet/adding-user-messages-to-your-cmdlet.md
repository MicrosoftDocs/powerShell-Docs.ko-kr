---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet에 사용자 메시지 추가
description: Cmdlet에 사용자 메시지 추가
ms.openlocfilehash: de6fcc093af1d01287eed1eb8cc7b81cf5d2fdd8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92668340"
---
# <a name="adding-user-messages-to-your-cmdlet"></a><span data-ttu-id="24d3a-103">Cmdlet에 사용자 메시지 추가</span><span class="sxs-lookup"><span data-stu-id="24d3a-103">Adding User Messages to Your Cmdlet</span></span>

<span data-ttu-id="24d3a-104">Cmdlet은 Windows PowerShell 런타임에 의해 사용자에 게 표시 될 수 있는 여러 종류의 메시지를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-104">Cmdlets can write several kinds of messages that can be displayed to the user by the Windows PowerShell runtime.</span></span> <span data-ttu-id="24d3a-105">이러한 메시지에는 다음과 같은 형식이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-105">These messages include the following types:</span></span>

- <span data-ttu-id="24d3a-106">일반 사용자 정보를 포함 하는 자세한 정보 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-106">Verbose messages that contain general user information.</span></span>

- <span data-ttu-id="24d3a-107">문제 해결 정보를 포함 하는 메시지를 디버깅 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-107">Debug messages that contain troubleshooting information.</span></span>

- <span data-ttu-id="24d3a-108">예기치 않은 결과를 가질 수 있는 작업을 cmdlet에서 수행 하려고 한다는 알림이 포함 된 경고 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-108">Warning messages that contain a notification that the cmdlet is about to perform an operation that can have unexpected results.</span></span>

- <span data-ttu-id="24d3a-109">시간이 오래 걸리는 작업을 수행할 때 cmdlet이 완료 한 작업량에 대 한 정보가 포함 된 진행률 보고서 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-109">Progress report messages that contain information about how much work the cmdlet has completed when performing an operation that takes a long time.</span></span>

<span data-ttu-id="24d3a-110">Cmdlet에서 쓸 수 있는 메시지 수 나 cmdlet이 쓰는 메시지 유형에는 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-110">There are no limits to the number of messages that your cmdlet can write or the type of messages that your cmdlet writes.</span></span> <span data-ttu-id="24d3a-111">각 메시지는 cmdlet의 입력 처리 메서드 내에서 특정 호출을 수행 하 여 작성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-111">Each message is written by making a specific call from within the input processing method of your cmdlet.</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="24d3a-112">Cmdlet 정의</span><span class="sxs-lookup"><span data-stu-id="24d3a-112">Defining the Cmdlet</span></span>

<span data-ttu-id="24d3a-113">Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-113">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="24d3a-114">모든 종류의 cmdlet은 입력 처리 메서드에서 사용자 알림을 쓸 수 있습니다. 따라서 일반적으로 cmdlet이 수행 하는 시스템 수정을 나타내는 동사를 사용 하 여이 cmdlet의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-114">Any sort of cmdlet can write user notifications from its input processing methods; so, in general, you can name this cmdlet using any verb that indicates what system modifications the cmdlet performs.</span></span> <span data-ttu-id="24d3a-115">승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d3a-115">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="24d3a-116">Stop-Proc cmdlet은 시스템을 수정 하도록 디자인 되었습니다. 따라서 .NET 클래스에 대 한 [System.object 특성](/dotnet/api/System.Management.Automation.CmdletAttribute) 선언에 attribute 키워드를 포함 하 `SupportsShouldProcess` 고로 설정 해야 합니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="24d3a-116">The Stop-Proc cmdlet is designed to modify the system; therefore, the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration for the .NET class must include the `SupportsShouldProcess` attribute keyword and be set to `true`.</span></span>

<span data-ttu-id="24d3a-117">다음 코드는이 Stop-Proc cmdlet 클래스에 대 한 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-117">The following code is the definition for this Stop-Proc cmdlet class.</span></span> <span data-ttu-id="24d3a-118">이 정의에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d3a-118">For more information about this definition, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="24d3a-119">시스템 수정 매개 변수 정의</span><span class="sxs-lookup"><span data-stu-id="24d3a-119">Defining Parameters for System Modification</span></span>

<span data-ttu-id="24d3a-120">Stop-Proc cmdlet은, 및의 세 가지 매개 변수를 정의 합니다. `Name` `Force` `PassThru`</span><span class="sxs-lookup"><span data-stu-id="24d3a-120">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span> <span data-ttu-id="24d3a-121">이러한 매개 변수를 정의 하는 방법에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d3a-121">For more information about defining these parameters, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

<span data-ttu-id="24d3a-122">다음은 Stop-Proc cmdlet에 대 한 매개 변수 선언입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-122">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="24d3a-123">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="24d3a-123">Overriding an Input Processing Method</span></span>

<span data-ttu-id="24d3a-124">Cmdlet은 입력 처리 메서드를 재정의 해야 합니다. 가장 자주 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-124">Your cmdlet must override an input processing method, most often it will be [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord).</span></span> <span data-ttu-id="24d3a-125">이 Stop-Proc cmdlet은 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-125">This Stop-Proc cmdlet overrides the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) input processing method.</span></span> <span data-ttu-id="24d3a-126">이 Stop-Proc cmdlet 구현에서를 호출 하 여 자세한 메시지, 디버그 메시지 및 경고 메시지를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-126">In this implementation of the Stop-Proc cmdlet, calls are made to write verbose messages, debug messages, and warning messages.</span></span>

> [!NOTE]
> <span data-ttu-id="24d3a-127">이 메서드가 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 및 system.object를 호출 하는 방법에 대 한 자세한 내용은 [시스템을 수정 하는 Cmdlet 만들기](./creating-a-cmdlet-that-modifies-the-system.md)를 참조 하세요 [..](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="24d3a-127">For more information about how this method calls the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods, see [Creating a Cmdlet that Modifies the System](./creating-a-cmdlet-that-modifies-the-system.md).</span></span>

## <a name="writing-a-verbose-message"></a><span data-ttu-id="24d3a-128">자세한 정보 메시지 작성</span><span class="sxs-lookup"><span data-stu-id="24d3a-128">Writing a Verbose Message</span></span>

<span data-ttu-id="24d3a-129">[System.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 는 특정 오류 조건과 관련이 없는 일반 사용자 수준 정보를 작성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-129">The [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method is used to write general user-level information that is unrelated to specific error conditions.</span></span> <span data-ttu-id="24d3a-130">그러면 시스템 관리자는이 정보를 사용 하 여 다른 명령을 계속 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-130">The system administrator can then use that information to continue processing other commands.</span></span> <span data-ttu-id="24d3a-131">또한이 메서드를 사용 하 여 작성 된 모든 정보는 필요에 따라 지역화 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-131">In addition, any information written using this method should be localized as needed.</span></span>

<span data-ttu-id="24d3a-132">이 Stop-Proc cmdlet의 다음 코드는 ProcessRecord 메서드를 재정의 하 여 [](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) [메서드를](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) 재정의 하는 두 가지 호출을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-132">The following code from this Stop-Proc cmdlet shows two calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
message = String.Format("Attempting to stop process \"{0}\".", name);
WriteVerbose(message);
```

```csharp
message = String.Format("Stopped process \"{0}\", pid {1}.",
                        processName, process.Id);

WriteVerbose(message);
```

## <a name="writing-a-debug-message"></a><span data-ttu-id="24d3a-133">디버그 메시지 작성</span><span class="sxs-lookup"><span data-stu-id="24d3a-133">Writing a Debug Message</span></span>

<span data-ttu-id="24d3a-134">이 cmdlet은 cmdlet의 작업 문제를 해결 하는 데 사용할 수 있는 디버그 메시지를 작성 하는 데 사용 [됩니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug)</span><span class="sxs-lookup"><span data-stu-id="24d3a-134">The [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method is used to write debug messages that can be used to troubleshoot the operation of the cmdlet.</span></span> <span data-ttu-id="24d3a-135">호출은 입력 처리 메서드에서 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-135">The call is made from an input processing method.</span></span>

> [!NOTE]
> <span data-ttu-id="24d3a-136">Windows PowerShell은 자세한 정보와 `Debug` 디버그 정보를 모두 표시 하는 매개 변수도 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-136">Windows PowerShell also defines a `Debug` parameter that presents both verbose and debug information.</span></span> <span data-ttu-id="24d3a-137">Cmdlet에서이 매개 변수를 지 원하는 경우에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose)를 호출 하는 것과 같은 코드에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 호출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-137">If your cmdlet supports this parameter, it does not need to call [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) in the same code that calls [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

<span data-ttu-id="24d3a-138">샘플 Stop-Proc cmdlet의 다음 두 섹션에서는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 여 메서드를 재정의 하 [는 방법에](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 대 한 호출을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-138">The following two sections of code from the sample Stop-Proc cmdlet show calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

<span data-ttu-id="24d3a-139">이 디버그 메시지는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하기 직전에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-139">This debug message is written immediately before [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) is called.</span></span>

```csharp
message =
          String.Format("Acquired name for pid {0} : \"{1}\"",
                       process.Id, processName);
WriteDebug(message);
```

<span data-ttu-id="24d3a-140">이 디버그 메시지는 [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 가 호출 되기 직전에 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-140">This debug message is written immediately before [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) is called.</span></span>

```csharp
message =
         String.Format("Writing process \"{0}\" to pipeline",
         processName);
WriteDebug(message);
WriteObject(process);
```

<span data-ttu-id="24d3a-141">Windows PowerShell은 추적 인프라 및 cmdlet에 대 한 모든 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) 를 자동으로 라우팅합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-141">Windows PowerShell automatically routes any [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) calls to the tracing infrastructure and cmdlets.</span></span> <span data-ttu-id="24d3a-142">이를 통해 cmdlet 내에서 추가 개발 작업을 수행 하지 않고도 호스팅 응용 프로그램, 파일 또는 디버거로 메서드 호출을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-142">This allows the method calls to be traced to the hosting application, a file, or a debugger without your having to do any extra development work within the cmdlet.</span></span> <span data-ttu-id="24d3a-143">다음 명령줄 항목은 추적 작업을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-143">The following command-line entry implements a tracing operation.</span></span>

<span data-ttu-id="24d3a-144">**PS> 추적 식-proc-file proc-command stop-proc notepad**</span><span class="sxs-lookup"><span data-stu-id="24d3a-144">**PS> trace-expression stop-proc -file proc.log -command stop-proc notepad**</span></span>

## <a name="writing-a-warning-message"></a><span data-ttu-id="24d3a-145">경고 메시지 작성</span><span class="sxs-lookup"><span data-stu-id="24d3a-145">Writing a Warning Message</span></span>

<span data-ttu-id="24d3a-146">Cmdlet이 읽기 전용 파일을 덮어쓰는 등 예기치 않은 결과가 발생할 수 있는 작업을 수행 하려고 할 때 경고를 작성 하는 데 사용 [됩니다.](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)</span><span class="sxs-lookup"><span data-stu-id="24d3a-146">The [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method is used to write a warning when the cmdlet is about to perform an operation that might have an unexpected result, for example, overwriting a read-only file.</span></span>

<span data-ttu-id="24d3a-147">샘플 Stop-Proc cmdlet의 다음 코드는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하 여 메서드를 호출 하는 것을 보여 줍니다. [이 메서드는](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning)</span><span class="sxs-lookup"><span data-stu-id="24d3a-147">The following code from the sample Stop-Proc cmdlet shows the call to the [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) method from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span>

```csharp
 if (criticalProcess)
 {
   message =
             String.Format("Stopping the critical process \"{0}\".",
                           processName);
   WriteWarning(message);
} // if (criticalProcess...
```

## <a name="writing-a-progress-message"></a><span data-ttu-id="24d3a-148">진행률 메시지 작성</span><span class="sxs-lookup"><span data-stu-id="24d3a-148">Writing a Progress Message</span></span>

<span data-ttu-id="24d3a-149">Cmdlet 작업을 완료 하는 데 시간이 오래 걸리는 경우에는 progress를 사용 [하 여 진행률](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 메시지를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-149">The [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) is used to write progress messages when cmdlet operations take an extended amount of time to complete.</span></span> <span data-ttu-id="24d3a-150">[Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) 를 호출 하면 사용자에 게 렌더링 하기 위해 호스팅 응용 프로그램으로 전송 되는 [개체가 전달 되](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 고,</span><span class="sxs-lookup"><span data-stu-id="24d3a-150">A call to [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) passes a [System.Management.Automation.Progressrecord](/dotnet/api/System.Management.Automation.ProgressRecord) object that is sent to the hosting application for rendering to the user.</span></span>

> [!NOTE]
> <span data-ttu-id="24d3a-151">이 Stop-Proc cmdlet에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) 를 호출 하는 작업이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-151">This Stop-Proc cmdlet does not include a call to the [System.Management.Automation.Cmdlet.WriteProgress](/dotnet/api/System.Management.Automation.Cmdlet.WriteProgress) method.</span></span>

<span data-ttu-id="24d3a-152">다음 코드는 항목 복사를 시도 하는 cmdlet에 의해 작성 된 진행률 메시지의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-152">The following code is an example of a progress message written by a cmdlet that is attempting to copy an item.</span></span>

```csharp
int myId = 0;
string myActivity = "Copy-item: Copying *.* to c:\abc";
string myStatus = "Copying file bar.txt";
ProgressRecord pr = new ProgressRecord(myId, myActivity, myStatus);
WriteProgress(pr);

pr.RecordType = ProgressRecordType.Completed;
WriteProgress(pr);
```

## <a name="code-sample"></a><span data-ttu-id="24d3a-153">코드 예제</span><span class="sxs-lookup"><span data-stu-id="24d3a-153">Code Sample</span></span>

<span data-ttu-id="24d3a-154">전체 c # 샘플 코드는 [StopProcessSample02 샘플](./stopprocesssample02-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d3a-154">For the complete C# sample code, see [StopProcessSample02 Sample](./stopprocesssample02-sample.md).</span></span>

## <a name="define-object-types-and-formatting"></a><span data-ttu-id="24d3a-155">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="24d3a-155">Define Object Types and Formatting</span></span>

<span data-ttu-id="24d3a-156">Windows PowerShell은 .NET 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-156">Windows PowerShell passes information between cmdlets using .NET objects.</span></span> <span data-ttu-id="24d3a-157">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-157">Consequently, a cmdlet might need to define its own type, or the cmdlet might need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="24d3a-158">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d3a-158">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="24d3a-159">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="24d3a-159">Building the Cmdlet</span></span>

<span data-ttu-id="24d3a-160">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-160">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="24d3a-161">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d3a-161">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="24d3a-162">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="24d3a-162">Testing the Cmdlet</span></span>

<span data-ttu-id="24d3a-163">Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-163">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="24d3a-164">샘플 Stop-Proc cmdlet을 테스트 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-164">Let's test the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="24d3a-165">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24d3a-165">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="24d3a-166">다음 명령줄 항목은 Stop-Proc를 사용 하 여 "NOTEPAD" 라는 프로세스를 중지 하 고, 자세한 알림 메시지를 제공 하 고, 디버그 정보를 인쇄 합니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-166">The following command-line entry uses Stop-Proc to stop the process named "NOTEPAD", provide verbose notifications, and print debug information.</span></span>

    ```powershell
    PS> stop-proc -Name notepad -Verbose -Debug
    ```

    <span data-ttu-id="24d3a-167">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-167">The following output appears.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="24d3a-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24d3a-168">See Also</span></span>

[<span data-ttu-id="24d3a-169">시스템을 수정 하는 Cmdlet을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="24d3a-169">Create a Cmdlet that Modifies the System</span></span>](./creating-a-cmdlet-that-modifies-the-system.md)

[<span data-ttu-id="24d3a-170">Windows PowerShell Cmdlet을 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="24d3a-170">How to Create a Windows PowerShell Cmdlet</span></span>](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

<span data-ttu-id="24d3a-171">[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="24d3a-171">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="24d3a-172">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="24d3a-172">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="24d3a-173">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="24d3a-173">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
