---
ms.date: 09/13/2016
ms.topic: reference
title: 시스템을 수정하는 Cmdlet 만들기
description: 시스템을 수정하는 Cmdlet 만들기
ms.openlocfilehash: 757f2c97bb4b5dcf2fb633cd35fe52bc5f6c5cf9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "93355547"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="ac523-103">시스템을 수정하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="ac523-103">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="ac523-104">경우에 따라 cmdlet은 Windows PowerShell 런타임의 상태 뿐만 아니라 시스템의 실행 상태를 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-104">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="ac523-105">이 경우 cmdlet을 사용 하 여 사용자가 변경할 수 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-105">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="ac523-106">확인을 지원 하려면 cmdlet에서 두 가지 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-106">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="ac523-107">SupportsShouldProcess 키워드를로 설정 하 여 cmdlet이 확인을 지원함을 선언 [합니다.](/dotnet/api/System.Management.Automation.CmdletAttribute) `true`</span><span class="sxs-lookup"><span data-stu-id="ac523-107">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="ac523-108">다음 예제와 같이 cmdlet을 실행 하는 동안에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-108">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="ac523-109">Cmdlet은 확인을 지원 하 여 `Confirm` `WhatIf` Windows PowerShell에서 제공 하는 및 매개 변수를 노출 하 고 cmdlet에 대 한 개발 지침을 충족 합니다. cmdlet 개발 지침에 대 한 자세한 내용은 [cmdlet 개발 지침](./cmdlet-development-guidelines.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="ac523-109">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="ac523-110">시스템 변경</span><span class="sxs-lookup"><span data-stu-id="ac523-110">Changing the System</span></span>

<span data-ttu-id="ac523-111">"시스템 변경" 작업은 잠재적으로 Windows PowerShell 외부의 시스템 상태를 변경 하는 모든 cmdlet을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-111">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="ac523-112">예를 들어 프로세스 중지, 사용자 계정 사용 또는 사용 안 함 또는 데이터베이스 테이블에 행 추가는 확인 해야 하는 시스템의 모든 변경 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-112">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span>
<span data-ttu-id="ac523-113">반대로 데이터를 읽거나 임시 연결을 설정 하는 작업은 시스템을 변경 하지 않으며 일반적으로 확인이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-113">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="ac523-114">또한와 같이 Windows PowerShell 런타임 내에서 효과가 제한 된 작업에는 확인이 필요 하지 않습니다 `set-variable` .</span><span class="sxs-lookup"><span data-stu-id="ac523-114">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="ac523-115">영구적으로 변경 될 수도 있고 그렇지 않을 수도 있는 cmdlet은 `SupportsShouldProcess` 영구적으로 변경 하려는 경우에만 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 선언 하 고 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-115">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="ac523-116">ShouldProcess 확인은 cmdlet에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-116">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="ac523-117">명령 또는 스크립트가 .NET 메서드나 속성을 직접 호출 하거나 Windows PowerShell 외부에서 응용 프로그램을 호출 하 여 시스템의 실행 상태를 수정 하는 경우에는이 형식의 확인을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-117">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="ac523-118">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ac523-118">The StopProc Cmdlet</span></span>

<span data-ttu-id="ac523-119">이 항목에서는 Get-Proc cmdlet을 사용 하 여 검색 된 프로세스를 중지 하려고 시도 하는 Stop-Proc cmdlet에 대해 설명 합니다 ( [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)참조).</span><span class="sxs-lookup"><span data-stu-id="ac523-119">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="ac523-120">Cmdlet 정의</span><span class="sxs-lookup"><span data-stu-id="ac523-120">Defining the Cmdlet</span></span>

<span data-ttu-id="ac523-121">Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-121">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="ac523-122">시스템을 변경 하는 cmdlet을 작성 하 고 있으므로 이름을 적절 하 게 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-122">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="ac523-123">이 cmdlet은 시스템 프로세스를 중지 하므로 여기서 선택한 동사 이름은 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스에 의해 정의 되는 "Stop" 이며,이는 cmdlet이 프로세스를 중지 함을 나타내는 명사 "Proc"로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-123">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="ac523-124">승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac523-124">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="ac523-125">다음은이 Stop-Proc cmdlet에 대 한 클래스 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-125">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="ac523-126">[System.object](/dotnet/api/System.Management.Automation.CmdletAttribute) 를 사용 하 여 `SupportsShouldProcess` cmdlet을 호출 하 여.... `true` [.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ........ a n d a.. a n d [a](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)..</span><span class="sxs-lookup"><span data-stu-id="ac523-126">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="ac523-127">이 키워드를 설정 하지 않으면 `Confirm` 사용자가 및 `WhatIf` 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-127">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="ac523-128">매우 파괴적인 작업</span><span class="sxs-lookup"><span data-stu-id="ac523-128">Extremely Destructive Actions</span></span>

<span data-ttu-id="ac523-129">활성 하드 디스크 파티션을 다시 포맷 하는 등의 일부 작업은 매우 파괴적인 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-129">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="ac523-130">이러한 경우, cmdlet은 system.object 특성을 `ConfirmImpact`  =  `ConfirmImpact.High` 선언할 때 [](/dotnet/api/System.Management.Automation.CmdletAttribute) 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-130">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="ac523-131">이 설정은 사용자가 매개 변수를 지정 하지 않은 경우에도 cmdlet이 강제로 사용자 확인을 요청 합니다 `Confirm` .</span><span class="sxs-lookup"><span data-stu-id="ac523-131">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="ac523-132">그러나 cmdlet 개발자는 `ConfirmImpact` 사용자 계정 삭제와 같이 잠재적으로 파괴적인 인 작업에 대해 과도를 피해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-132">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="ac523-133">`ConfirmImpact`가 [system.object](/dotnet/api/System.Management.Automation.ConfirmImpact)로 설정 되어 있으면이 
 **고**, 그렇지 않으면입니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-133">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact)
**High**.</span></span>

<span data-ttu-id="ac523-134">마찬가지로, 이론적으로는 Windows PowerShell 외부 시스템의 실행 상태를 수정 하지만 일부 작업은 안전 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-134">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="ac523-135">이러한 cmdlet은 `ConfirmImpact` 를 system.object로 설정할 수 있습니다 [. 낮음](/dotnet/api/system.management.automation.confirmimpact).</span><span class="sxs-lookup"><span data-stu-id="ac523-135">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact).</span></span>
<span data-ttu-id="ac523-136">이렇게 하면 사용자가 중간 영향 및 높은 영향의 작업만 확인 하도록 요청한 확인 요청이 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-136">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="ac523-137">시스템 수정 매개 변수 정의</span><span class="sxs-lookup"><span data-stu-id="ac523-137">Defining Parameters for System Modification</span></span>

<span data-ttu-id="ac523-138">이 섹션에서는 시스템 수정 작업을 지 원하는 데 필요한 cmdlet 매개 변수를 포함 하 여 cmdlet 매개 변수를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-138">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="ac523-139">매개 변수 정의에 대 한 일반 정보가 필요한 경우 [명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac523-139">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="ac523-140">Stop-Proc cmdlet은, 및의 세 가지 매개 변수를 정의 합니다. `Name` `Force` `PassThru`</span><span class="sxs-lookup"><span data-stu-id="ac523-140">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="ac523-141">`Name`매개 변수는 `Name` 프로세스 입력 개체의 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-141">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="ac523-142">`Name`이 샘플의 매개 변수는 필수 항목입니다. 중지 하는 명명 된 프로세스가 없으면 cmdlet이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-142">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="ac523-143">`Force`사용자는 매개 변수를 사용 하 여 호출을 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)로 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-143">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span>
<span data-ttu-id="ac523-144">실제로 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 모든 cmdlet에 `Force` 는 매개 변수가 있어야 합니다 .이 매개 변수를 `Force` 지정 하면 cmdlet에서 system.object에 대 한 호출을 건너뛰고 작업을 [계속](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-144">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="ac523-145">이는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)에 대 한 호출에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-145">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="ac523-146">`PassThru`사용자는 매개 변수를 사용 하 여 cmdlet이 파이프라인 (이 경우에는 프로세스가 중지 된 후)을 통해 출력 개체를 전달 하는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-146">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="ac523-147">이 매개 변수는 입력 개체의 속성이 아니라 cmdlet 자체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-147">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="ac523-148">다음은 Stop-Proc cmdlet에 대 한 매개 변수 선언입니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-148">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="ac523-149">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="ac523-149">Overriding an Input Processing Method</span></span>

<span data-ttu-id="ac523-150">Cmdlet은 입력 처리 메서드를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-150">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="ac523-151">다음 코드는 샘플 Stop-Proc Cmdlet에 사용 된 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 재정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-151">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="ac523-152">요청 된 각 프로세스 이름에 대해이 메서드는 프로세스가 특수 프로세스가 아니라 프로세스를 중지 한 다음 매개 변수가 지정 된 경우 출력 개체를 보냅니다 `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="ac523-152">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

```csharp
protected override void ProcessRecord()
{
  foreach (string name in processNames)
  {
    // For every process name passed to the cmdlet, get the associated
    // process(es). For failures, write a non-terminating error
    Process[] processes;

    try
    {
      processes = Process.GetProcessesByName(name);
    }
    catch (InvalidOperationException ioe)
    {
      WriteError(new ErrorRecord(ioe,"Unable to access the target process by name",
                 ErrorCategory.InvalidOperation, name));
      continue;
    }

    // Try to stop the process(es) that have been retrieved for a name
    foreach (Process process in processes)
    {
      string processName;

      try
      {
        processName = process.ProcessName;
      }

      catch (Win32Exception e)
        {
          WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                     ErrorCategory.ReadError, process));
          continue;
        }

        // Call Should Process to confirm the operation first.
        // This is always false if WhatIf is set.
        if (!ShouldProcess(string.Format("{0} ({1})", processName,
                           process.Id)))
        {
          continue;
        }
        // Call ShouldContinue to make sure the user really does want
        // to stop a critical process that could possibly stop the computer.
        bool criticalProcess =
             criticalProcessNames.Contains(processName.ToLower());

        if (criticalProcess &&!force)
        {
          string message = String.Format
                ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                processName);

          // It is possible that ProcessRecord is called multiple times
          // when the Name parameter receives objects as input from the
          // pipeline. So to retain YesToAll and NoToAll input that the
          // user may enter across multiple calls to ProcessRecord, this
          // information is stored as private members of the cmdlet.
          if (!ShouldContinue(message, "Warning!",
                              ref yesToAll,
                              ref noToAll))
          {
            continue;
          }
        } // if (criticalProcess...
        // Stop the named process.
        try
        {
          process.Kill();
        }
        catch (Exception e)
        {
          if ((e is Win32Exception) || (e is SystemException) ||
              (e is InvalidOperationException))
          {
            // This process could not be stopped so write
            // a non-terminating error.
            string message = String.Format("{0} {1} {2}",
                             "Could not stop process \"", processName,
                             "\".");
            WriteError(new ErrorRecord(e, message,
                       ErrorCategory.CloseError, process));
                       continue;
          } // if ((e is...
          else throw;
        } // catch

        // If the PassThru parameter argument is
        // True, pass the terminated process on.
        if (passThru)
        {
          WriteObject(process);
        }
    } // foreach (Process...
  } // foreach (string...
} // ProcessRecord
```

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="ac523-153">ShouldProcess 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="ac523-153">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="ac523-154">Cmdlet의 입력 처리 메서드는 시스템의 실행 상태를 변경 (예: 파일 삭제) 하기 전에 작업 실행을 확인 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 의 입력 처리 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-154">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="ac523-155">이를 통해 Windows PowerShell 런타임은 올바른 "WhatIf" 및 "Confirm" 동작을 셸 내에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-155">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="ac523-156">지원 되는 cmdlet 상태를 처리 하 고이를 실행 [하는 데](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 실패 하는 경우 사용자는 시스템을 예기치 않게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-156">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="ac523-157">Windows PowerShell 런타임은 사용자에 게 표시 되는 항목을 결정 하는 데 필요한 모든 명령줄 설정이 나 기본 설정 변수를 고려 하 여 사용자에 게 변경 될 리소스의 [이름을 보냅니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)</span><span class="sxs-lookup"><span data-stu-id="ac523-157">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="ac523-158">다음 예제에서는 sample Stop-Proc Cmdlet의 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 하는 방법으로 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 방법을 보여 줍니다 (예:</span><span class="sxs-lookup"><span data-stu-id="ac523-158">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="ac523-159">ShouldContinue 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="ac523-159">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="ac523-160">[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하면 두 번째 메시지가 사용자에 게 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-160">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="ac523-161">이 호출은를 [호출 하 고](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) `true` , `Force` 매개 변수가로 설정 되어 있지 않은 경우를 반환 합니다. `true`</span><span class="sxs-lookup"><span data-stu-id="ac523-161">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="ac523-162">그런 다음 사용자는 작업을 계속 해야 하는지 여부에 대 한 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-162">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="ac523-163">Cmdlet은 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 나 사용자에 게 예-모두 및 모두 사용 안 함 옵션을 제공 하려고 [합니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="ac523-163">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="ac523-164">다음 예제에서는 ProcessRecord에 대 한 호출을 보여 [줍니다. 다음](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 예제에서는 샘플 Stop-Proc Cmdlet의 [](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-164">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (criticalProcess &&!force)
{
  string message = String.Format
        ("The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
        processName);

  // It is possible that ProcessRecord is called multiple times
  // when the Name parameter receives objects as input from the
  // pipeline. So to retain YesToAll and NoToAll input that the
  // user may enter across multiple calls to ProcessRecord, this
  // information is stored as private members of the cmdlet.
  if (!ShouldContinue(message, "Warning!",
                      ref yesToAll,
                      ref noToAll))
  {
    continue;
  }
} // if (criticalProcess...
```

## <a name="stopping-input-processing"></a><span data-ttu-id="ac523-165">입력 처리 중지</span><span class="sxs-lookup"><span data-stu-id="ac523-165">Stopping Input Processing</span></span>

<span data-ttu-id="ac523-166">시스템 수정 작업을 수행 하는 cmdlet의 입력 처리 메서드는 입력 처리를 중지 하는 방법을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-166">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="ac523-167">이 Stop-Proc cmdlet의 경우 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드에서 [system. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill) 메서드로 호출을 수행 합니다 .이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-167">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="ac523-168">`PassThru`매개 변수가로 설정 되어 있기 때문에 `true` [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 를 호출 하 여 프로세스 개체를 파이프라인으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-168">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ac523-169">코드 예제</span><span class="sxs-lookup"><span data-stu-id="ac523-169">Code Sample</span></span>

<span data-ttu-id="ac523-170">전체 c # 샘플 코드는 [StopProcessSample01 샘플](./stopprocesssample01-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac523-170">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="ac523-171">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="ac523-171">Defining Object Types and Formatting</span></span>

<span data-ttu-id="ac523-172">Windows PowerShell은 .Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-172">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="ac523-173">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-173">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="ac523-174">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac523-174">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="ac523-175">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="ac523-175">Building the Cmdlet</span></span>

<span data-ttu-id="ac523-176">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-176">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="ac523-177">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac523-177">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="ac523-178">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="ac523-178">Testing the Cmdlet</span></span>

<span data-ttu-id="ac523-179">Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-179">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="ac523-180">Stop-Proc cmdlet을 테스트 하는 여러 테스트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-180">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="ac523-181">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ac523-181">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="ac523-182">Windows PowerShell을 시작 하 고 아래와 같이 Stop-Proc cmdlet을 사용 하 여 처리를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-182">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="ac523-183">Cmdlet은 매개 변수를 필수로 지정 하기 때문에 `Name` cmdlet은 매개 변수를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-183">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="ac523-184">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-184">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="ac523-185">이제 cmdlet을 사용 하 여 "NOTEPAD" 라는 프로세스를 중지 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-185">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="ac523-186">Cmdlet은 작업을 확인 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-186">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

    <span data-ttu-id="ac523-187">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-187">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="ac523-188">표시 된 대로 Stop-Proc를 사용 하 여 "WINLOGON" 이라는 중요 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-188">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="ac523-189">이 작업을 수행 하면 운영 체제가 재부팅 되기 때문에이 작업을 수행 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-189">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    <span data-ttu-id="ac523-190">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-190">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="ac523-191">이제 경고를 받지 않고 WINLOGON 프로세스를 중지 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-191">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="ac523-192">이 명령 항목은 매개 변수를 사용 하 여 `Force` 경고를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-192">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    <span data-ttu-id="ac523-193">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac523-193">The following output appears.</span></span>

    ```Output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="ac523-194">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ac523-194">See Also</span></span>

[<span data-ttu-id="ac523-195">Command-Line 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="ac523-195">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="ac523-196">[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ac523-196">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="ac523-197">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ac523-197">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="ac523-198">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ac523-198">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="ac523-199">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="ac523-199">Cmdlet Samples</span></span>](./cmdlet-samples.md)
