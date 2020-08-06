---
title: 시스템을 수정 하는 Cmdlet 만들기 | Microsoft Docs
ms.date: 09/13/2016
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.openlocfilehash: 03ffe0c9c02dcdeb2dd24f81014b2013ae169aa4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782177"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="9e027-102">시스템을 수정하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="9e027-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="9e027-103">경우에 따라 cmdlet은 Windows PowerShell 런타임의 상태 뿐만 아니라 시스템의 실행 상태를 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="9e027-104">이 경우 cmdlet을 사용 하 여 사용자가 변경할 수 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="9e027-105">확인을 지원 하려면 cmdlet에서 두 가지 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="9e027-106">SupportsShouldProcess 키워드를로 설정 하 여 cmdlet이 확인을 지원함을 선언 [합니다.](/dotnet/api/System.Management.Automation.CmdletAttribute) `true`</span><span class="sxs-lookup"><span data-stu-id="9e027-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="9e027-107">다음 예제와 같이 cmdlet을 실행 하는 동안에는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="9e027-108">Cmdlet은 확인을 지원 하 여 `Confirm` `WhatIf` Windows PowerShell에서 제공 하는 및 매개 변수를 노출 하 고 cmdlet에 대 한 개발 지침을 충족 합니다. cmdlet 개발 지침에 대 한 자세한 내용은 [cmdlet 개발 지침](./cmdlet-development-guidelines.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9e027-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="9e027-109">시스템 변경</span><span class="sxs-lookup"><span data-stu-id="9e027-109">Changing the System</span></span>

<span data-ttu-id="9e027-110">"시스템 변경" 작업은 잠재적으로 Windows PowerShell 외부의 시스템 상태를 변경 하는 모든 cmdlet을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="9e027-111">예를 들어 프로세스 중지, 사용자 계정 사용 또는 사용 안 함 또는 데이터베이스 테이블에 행 추가는 확인 해야 하는 시스템의 모든 변경 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="9e027-112">반대로 데이터를 읽거나 임시 연결을 설정 하는 작업은 시스템을 변경 하지 않으며 일반적으로 확인이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="9e027-113">또한와 같이 Windows PowerShell 런타임 내에서 효과가 제한 된 작업에는 확인이 필요 하지 않습니다 `set-variable` .</span><span class="sxs-lookup"><span data-stu-id="9e027-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="9e027-114">영구적으로 변경 될 수도 있고 그렇지 않을 수도 있는 cmdlet은 `SupportsShouldProcess` 영구적으로 변경 하려는 경우에만 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 선언 하 고 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="9e027-115">ShouldProcess 확인은 cmdlet에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="9e027-116">명령 또는 스크립트가 .NET 메서드나 속성을 직접 호출 하거나 Windows PowerShell 외부에서 응용 프로그램을 호출 하 여 시스템의 실행 상태를 수정 하는 경우에는이 형식의 확인을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="9e027-117">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="9e027-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="9e027-118">이 항목에서는 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)에 설명 된 것 처럼, Get proc cmdlet을 사용 하 여 검색 된 프로세스를 중지 하는 데 사용 되는 stop proc cmdlet에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="9e027-119">Cmdlet 정의</span><span class="sxs-lookup"><span data-stu-id="9e027-119">Defining the Cmdlet</span></span>

<span data-ttu-id="9e027-120">Cmdlet을 만드는 첫 번째 단계는 항상 cmdlet의 이름을 지정 하 고 cmdlet을 구현 하는 .NET 클래스를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="9e027-121">시스템을 변경 하는 cmdlet을 작성 하 고 있으므로 이름을 적절 하 게 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="9e027-122">이 cmdlet은 시스템 프로세스를 중지 하므로 여기서 선택한 동사 이름은 [Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) 클래스에 의해 정의 되는 "Stop" 이며,이는 cmdlet이 프로세스를 중지 함을 나타내는 명사 "Proc"로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="9e027-123">승인 된 cmdlet 동사에 대 한 자세한 내용은 [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e027-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="9e027-124">다음은이 Stop Proc cmdlet에 대 한 클래스 정의입니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="9e027-125">[System.object](/dotnet/api/System.Management.Automation.CmdletAttribute) 를 사용 하 여 `SupportsShouldProcess` cmdlet을 호출 하 여.... `true` [.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) ........ a n d a.. a n d [a](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)..</span><span class="sxs-lookup"><span data-stu-id="9e027-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="9e027-126">이 키워드를 설정 하지 않으면 `Confirm` 사용자가 및 `WhatIf` 매개 변수를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="9e027-127">매우 파괴적인 작업</span><span class="sxs-lookup"><span data-stu-id="9e027-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="9e027-128">활성 하드 디스크 파티션을 다시 포맷 하는 등의 일부 작업은 매우 파괴적인 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="9e027-129">이러한 경우, cmdlet은 system.object 특성을 `ConfirmImpact`  =  `ConfirmImpact.High` 선언할 때 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="9e027-130">이 설정은 사용자가 매개 변수를 지정 하지 않은 경우에도 cmdlet이 강제로 사용자 확인을 요청 합니다 `Confirm` .</span><span class="sxs-lookup"><span data-stu-id="9e027-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="9e027-131">그러나 cmdlet 개발자는 `ConfirmImpact` 사용자 계정 삭제와 같이 잠재적으로 파괴적인 인 작업에 대해 과도를 피해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="9e027-132">`ConfirmImpact`가 [system.object](/dotnet/api/System.Management.Automation.ConfirmImpact) 로 설정 되어 있으면이 **고**, 그렇지 않으면입니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.ConfirmImpact](/dotnet/api/System.Management.Automation.ConfirmImpact) **High**.</span></span>

<span data-ttu-id="9e027-133">마찬가지로, 이론적으로는 Windows PowerShell 외부 시스템의 실행 상태를 수정 하지만 일부 작업은 안전 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="9e027-134">이러한 cmdlet은 `ConfirmImpact` 를 system.object로 설정할 수 있습니다 [. 낮음](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="9e027-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="9e027-135">이렇게 하면 사용자가 중간 영향 및 높은 영향의 작업만 확인 하도록 요청한 확인 요청이 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="9e027-136">시스템 수정 매개 변수 정의</span><span class="sxs-lookup"><span data-stu-id="9e027-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="9e027-137">이 섹션에서는 시스템 수정 작업을 지 원하는 데 필요한 cmdlet 매개 변수를 포함 하 여 cmdlet 매개 변수를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="9e027-138">매개 변수 정의에 대 한 일반 정보가 필요한 경우 [명령줄 입력을 처리 하는 매개 변수 추가](./adding-parameters-that-process-command-line-input.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e027-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="9e027-139">Stop Proc cmdlet은 3 개의 매개 변수 `Name` , `Force` 및를 정의 `PassThru` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="9e027-140">`Name`매개 변수는 `Name` 프로세스 입력 개체의 속성에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="9e027-141">`Name`이 샘플의 매개 변수는 필수 항목입니다. 중지 하는 명명 된 프로세스가 없으면 cmdlet이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="9e027-142">`Force`사용자는 매개 변수를 사용 하 여 호출을 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)로 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="9e027-143">실제로 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하는 모든 cmdlet에 `Force` 는 매개 변수가 있어야 합니다 .이 매개 변수를 `Force` 지정 하면 cmdlet에서 system.object에 대 한 호출을 건너뛰고 작업을 [계속](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="9e027-144">이는 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)에 대 한 호출에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="9e027-145">`PassThru`사용자는 매개 변수를 사용 하 여 cmdlet이 파이프라인 (이 경우에는 프로세스가 중지 된 후)을 통해 출력 개체를 전달 하는지 여부를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="9e027-146">이 매개 변수는 입력 개체의 속성이 아니라 cmdlet 자체에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="9e027-147">다음은 Stop Proc cmdlet에 대 한 매개 변수 선언입니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="9e027-148">입력 처리 메서드 재정의</span><span class="sxs-lookup"><span data-stu-id="9e027-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="9e027-149">Cmdlet은 입력 처리 메서드를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="9e027-150">다음 코드는 샘플 ProcessRecord Cmdlet에서 사용 되는 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 재정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="9e027-151">요청 된 각 프로세스 이름에 대해이 메서드는 프로세스가 특수 프로세스가 아니라 프로세스를 중지 한 다음 매개 변수가 지정 된 경우 출력 개체를 보냅니다 `PassThru` .</span><span class="sxs-lookup"><span data-stu-id="9e027-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="9e027-152">ShouldProcess 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="9e027-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="9e027-153">Cmdlet의 입력 처리 메서드는 시스템의 실행 상태를 변경 (예: 파일 삭제) 하기 전에 작업 실행을 확인 하기 위해 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 의 입력 처리 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="9e027-154">이를 통해 Windows PowerShell 런타임은 올바른 "WhatIf" 및 "Confirm" 동작을 셸 내에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="9e027-155">지원 되는 cmdlet 상태를 처리 하 고이를 실행 [하는 데](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 실패 하는 경우 사용자는 시스템을 예기치 않게 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="9e027-156">Windows PowerShell 런타임은 사용자에 게 표시 되는 항목을 결정 하는 데 필요한 모든 명령줄 설정이 나 기본 설정 변수를 고려 하 여 사용자에 게 변경 될 리소스의 [이름을 보냅니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)</span><span class="sxs-lookup"><span data-stu-id="9e027-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="9e027-157">다음 예제에서는 샘플 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) cmdlet의 재정의에서 [system.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 를 호출 하는 방법에 대해 설명 하는 예제를 보여 줍니다..</span><span class="sxs-lookup"><span data-stu-id="9e027-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="9e027-158">ShouldContinue 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="9e027-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="9e027-159">[System.object](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 를 호출 하면 두 번째 메시지가 사용자에 게 전송 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="9e027-160">이 호출은를 [호출 하 고](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) `true` , `Force` 매개 변수가로 설정 되어 있지 않은 경우를 반환 합니다. `true`</span><span class="sxs-lookup"><span data-stu-id="9e027-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="9e027-161">그런 다음 사용자는 작업을 계속 해야 하는지 여부에 대 한 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="9e027-162">Cmdlet은 잠재적으로 위험한 시스템 수정에 대 한 추가 검사 나 사용자에 게 예-모두 및 모두 사용 안 함 옵션을 제공 하려고 [합니다.](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)</span><span class="sxs-lookup"><span data-stu-id="9e027-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="9e027-163">다음 예제에서는 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 에 대 한 호출을 보여 줍니다 .이 cmdlet은 sample Stop-Proc cmdlet의 재정의에서 [계속](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="9e027-164">입력 처리 중지</span><span class="sxs-lookup"><span data-stu-id="9e027-164">Stopping Input Processing</span></span>

<span data-ttu-id="9e027-165">시스템 수정 작업을 수행 하는 cmdlet의 입력 처리 메서드는 입력 처리를 중지 하는 방법을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="9e027-166">이 Stop Proc cmdlet의 경우 [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드에서 [system. Kill \*](/dotnet/api/System.Diagnostics.Process.Kill) 메서드로 호출을 호출 하 게 됩니다 (예를 들어).</span><span class="sxs-lookup"><span data-stu-id="9e027-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="9e027-167">`PassThru`매개 변수가로 설정 되어 있기 때문에 `true` [ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) . [WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 를 호출 하 여 프로세스 개체를 파이프라인으로 전송 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9e027-168">코드 예제</span><span class="sxs-lookup"><span data-stu-id="9e027-168">Code Sample</span></span>

<span data-ttu-id="9e027-169">전체 c # 샘플 코드는 [StopProcessSample01 샘플](./stopprocesssample01-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e027-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="9e027-170">개체 형식 및 서식 정의</span><span class="sxs-lookup"><span data-stu-id="9e027-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="9e027-171">Windows PowerShell은 .Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="9e027-172">따라서 cmdlet은 자체 형식을 정의 해야 할 수도 있고, 다른 cmdlet에서 제공 하는 기존 형식을 cmdlet에서 확장 해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="9e027-173">새 형식을 정의 하거나 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 [개체 형식 확장 및 서식 지정](/previous-versions//ms714665(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e027-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85)).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="9e027-174">Cmdlet 빌드</span><span class="sxs-lookup"><span data-stu-id="9e027-174">Building the Cmdlet</span></span>

<span data-ttu-id="9e027-175">Cmdlet을 구현한 후 Windows PowerShell 스냅인을 통해 Windows PowerShell에 등록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="9e027-176">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 [cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e027-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85)).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="9e027-177">Cmdlet 테스트</span><span class="sxs-lookup"><span data-stu-id="9e027-177">Testing the Cmdlet</span></span>

<span data-ttu-id="9e027-178">Windows PowerShell을 사용 하 여 cmdlet을 등록 한 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="9e027-179">다음은 Stop Proc cmdlet을 테스트 하는 여러 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="9e027-180">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 [Windows PowerShell 시작](/powershell/scripting/getting-started/getting-started-with-windows-powershell)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9e027-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="9e027-181">Windows PowerShell을 시작 하 고 아래와 같이 Stop Proc cmdlet을 사용 하 여 처리를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="9e027-182">Cmdlet은 매개 변수를 필수로 지정 하기 때문에 `Name` cmdlet은 매개 변수를 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

    <span data-ttu-id="9e027-183">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="9e027-184">이제 cmdlet을 사용 하 여 "NOTEPAD" 라는 프로세스를 중지 하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="9e027-185">Cmdlet은 작업을 확인 하 라는 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

    <span data-ttu-id="9e027-186">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="9e027-187">표시 된 대로 Stop Proc를 사용 하 여 "WINLOGON" 이라는 중요 한 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="9e027-188">이 작업을 수행 하면 운영 체제가 재부팅 되기 때문에이 작업을 수행 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

    <span data-ttu-id="9e027-189">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="9e027-190">이제 경고를 받지 않고 WINLOGON 프로세스를 중지 해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="9e027-191">이 명령 항목은 매개 변수를 사용 하 여 `Force` 경고를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

    <span data-ttu-id="9e027-192">다음 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9e027-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="9e027-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e027-193">See Also</span></span>

[<span data-ttu-id="9e027-194">명령줄 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="9e027-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

<span data-ttu-id="9e027-195">[개체 형식 및 서식 확장](/previous-versions//ms714665(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9e027-195">[Extending Object Types and Formatting](/previous-versions//ms714665(v=vs.85))</span></span>

<span data-ttu-id="9e027-196">[Cmdlet, 공급자 및 호스트 응용 프로그램을 등록 하는 방법](/previous-versions//ms714644(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="9e027-196">[How to Register Cmdlets, Providers, and Host Applications](/previous-versions//ms714644(v=vs.85))</span></span>

[<span data-ttu-id="9e027-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="9e027-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="9e027-198">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="9e027-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)
