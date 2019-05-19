---
title: 시스템을 수정 하는 Cmdlet를 만들 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- should process [PowerShell Programmer's Guide]
- should continue [PowerShell Programmer's Guide]
- user feedback [PowerShell Programmer's Guide]
- confirm impact [PowerShell Programmer's Guide]
ms.assetid: 59be4120-1700-4d92-a308-ef4a32ccf11a
caps.latest.revision: 8
ms.openlocfilehash: a4fa9ce52855928679a2425f24f2e49a68030c63
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65854908"
---
# <a name="creating-a-cmdlet-that-modifies-the-system"></a><span data-ttu-id="cb9f9-102">시스템을 수정하는 Cmdlet 만들기</span><span class="sxs-lookup"><span data-stu-id="cb9f9-102">Creating a Cmdlet that Modifies the System</span></span>

<span data-ttu-id="cb9f9-103">경우에 따라 cmdlet 뿐 아니라 Windows PowerShell 런타임 상태 시스템의 실행 상태를 수정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-103">Sometimes a cmdlet must modify the running state of the system, not just the state of the Windows PowerShell runtime.</span></span> <span data-ttu-id="cb9f9-104">이러한 경우 변경할 것인지 여부를 확인할 수 cmdlet 사용자 허용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-104">In these cases, the cmdlet should allow the user a chance to confirm whether or not to make the change.</span></span>

<span data-ttu-id="cb9f9-105">Cmdlet는 확인을 지원 하기 위해 두 가지 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-105">To support confirmation a cmdlet must do two things.</span></span>

- <span data-ttu-id="cb9f9-106">지정 하는 경우 cmdlet은 확인을 지원 하는지 선언 된 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 특성 SupportsShouldProcess 키워드가 설정 하 여 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-106">Declare that the cmdlet supports confirmation when you specify the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute by setting the SupportsShouldProcess keyword to `true`.</span></span>

- <span data-ttu-id="cb9f9-107">호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) cmdlet (다음 예제와 같이) 실행 중입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-107">Call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) during the execution of the cmdlet (as shown in the following example).</span></span>

<span data-ttu-id="cb9f9-108">확인을 지원 하 여 cmdlet을 표시 합니다 `Confirm` 및 `WhatIf` Windows PowerShell에서 제공 하는 또한 cmdlet에 대 한 개발 지침을 충족 하는 매개 변수 (cmdlet 개발 지침에 대 한 자세한 내용은 참조 [ Cmdlet 개발 지침](./cmdlet-development-guidelines.md).).</span><span class="sxs-lookup"><span data-stu-id="cb9f9-108">By supporting confirmation, a cmdlet exposes the `Confirm` and `WhatIf` parameters that are provided by Windows PowerShell, and also meets the development guidelines for cmdlets (For more information about cmdlet development guidelines, see [Cmdlet Development Guidelines](./cmdlet-development-guidelines.md).).</span></span>

## <a name="changing-the-system"></a><span data-ttu-id="cb9f9-109">시스템 변경</span><span class="sxs-lookup"><span data-stu-id="cb9f9-109">Changing the System</span></span>

<span data-ttu-id="cb9f9-110">"시스템 변경" act 잠재적으로 Windows PowerShell 외부 시스템의 상태를 변경 하는 cmdlet를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-110">The act of "changing the system" refers to any cmdlet that potentially changes the state of the system outside Windows PowerShell.</span></span> <span data-ttu-id="cb9f9-111">예를 들어, 사용자 계정을 사용 하지 않도록 설정 또는 확인 되어야 하는 시스템의 모든 변경 내용이 데이터베이스 테이블에 행 추가 사용 하도록 설정 하는 프로세스를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-111">For example, stopping a process, enabling or disabling a user account, or adding a row to a database table are all changes to the system that should be confirmed.</span></span> <span data-ttu-id="cb9f9-112">반면에 데이터를 읽거나 일시적인 연결을 설정 하는 작업 시스템 변경 하지 않으며 일반적으로 확인이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-112">In contrast, operations that read data or establish transient connections do not change the system and generally do not require confirmation.</span></span> <span data-ttu-id="cb9f9-113">확인 효과 제한 되어 Windows PowerShell 런타임 내에서 같은 작업에 필요 하지도 않습니다 `set-variable`합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-113">Confirmation is also not needed for actions whose effect is limited to inside the Windows PowerShell runtime, such as `set-variable`.</span></span> <span data-ttu-id="cb9f9-114">영구 변경 하지 못할 수 있거나 봐야 할 Cmdlet를 선언 해야 합니다 `SupportsShouldProcess` 호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 영구 변경 하려는 경우에 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-114">Cmdlets that might or might not make a persistent change should declare `SupportsShouldProcess` and call [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) only if they are about to make a persistent change.</span></span>

> [!NOTE]
> <span data-ttu-id="cb9f9-115">ShouldProcess 확인 cmdlet에만 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-115">ShouldProcess confirmation applies only to cmdlets.</span></span> <span data-ttu-id="cb9f9-116">명령 또는 스크립트를 직접.NET 메서드 또는 속성을 호출 하 여 또는 Windows PowerShell의 외부 호출 응용 프로그램에서 시스템의 실행 상태를 수정, 확인이 폼은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-116">If a command or script modifies the running state of a system by directly calling .NET methods or properties, or by calling applications outside of Windows PowerShell, this form of confirmation will not be available.</span></span>

## <a name="the-stopproc-cmdlet"></a><span data-ttu-id="cb9f9-117">StopProc Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cb9f9-117">The StopProc Cmdlet</span></span>

<span data-ttu-id="cb9f9-118">이 항목에서는 Get-proc cmdlet을 사용 하 여 검색 되는 프로세스를 중지 하려고 하는 중지 Proc cmdlet에 설명 합니다 (에 설명 된 [첫 번째 Cmdlet 만들기](./creating-a-cmdlet-without-parameters.md)).</span><span class="sxs-lookup"><span data-stu-id="cb9f9-118">This topic describes a Stop-Proc cmdlet that attempts to stop processes that are retrieved using the Get-Proc cmdlet (described in [Creating Your First Cmdlet](./creating-a-cmdlet-without-parameters.md)).</span></span>

## <a name="defining-the-cmdlet"></a><span data-ttu-id="cb9f9-119">Cmdlet을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-119">Defining the Cmdlet</span></span>

<span data-ttu-id="cb9f9-120">Cmdlet 만드는 첫 번째 단계는 항상 cmdlet 이름과 cmdlet을 구현 하는.NET 클래스를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-120">The first step in cmdlet creation is always naming the cmdlet and declaring the .NET class that implements the cmdlet.</span></span> <span data-ttu-id="cb9f9-121">시스템을 변경 하는 cmdlet를 작성 하는 때문에 적절 하 게 명명 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-121">Because you are writing a cmdlet to change the system, it should be named accordingly.</span></span> <span data-ttu-id="cb9f9-122">이 cmdlet은 중지 시스템 프로세스를 "중지"를 선택한 다음 동사 이름 이므로 정의한를 [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) cmdlet은 프로세스 중지를 나타내기 위해 "Proc" 명사를 사용 하 여 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-122">This cmdlet stops system processes, so the verb name chosen here is "Stop", defined by the [System.Management.Automation.Verbslifecycle](/dotnet/api/System.Management.Automation.VerbsLifeCycle) class, with the noun "Proc" to indicate that the cmdlet stops processes.</span></span> <span data-ttu-id="cb9f9-123">승인 된 cmdlet 동사에 대 한 자세한 내용은 참조 하세요. [Cmdlet 동사 이름](./approved-verbs-for-windows-powershell-commands.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-123">For more information about approved cmdlet verbs, see [Cmdlet Verb Names](./approved-verbs-for-windows-powershell-commands.md).</span></span>

<span data-ttu-id="cb9f9-124">다음은이 중지 Proc cmdlet에 대 한 클래스 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-124">The following is the class definition for this Stop-Proc cmdlet.</span></span>

```csharp
[Cmdlet(VerbsLifecycle.Stop, "Proc",
        SupportsShouldProcess = true)]
public class StopProcCommand : Cmdlet
```

<span data-ttu-id="cb9f9-125">주의는 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 선언 합니다 `SupportsShouldProcess` 특성 키워드로 설정 되어 `true` 를 호출 하기 위해 cmdlet을 사용 하도록 설정 하려면 [ System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 하 고 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-125">Be aware that in the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) declaration, the `SupportsShouldProcess` attribute keyword is set to `true` to enable the cmdlet to make calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="cb9f9-126">이 키워드 집합 없이 합니다 `Confirm` 고 `WhatIf` 매개 변수가 사용자에 게 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-126">Without this keyword set, the `Confirm` and `WhatIf` parameters will not be available to the user.</span></span>

### <a name="extremely-destructive-actions"></a><span data-ttu-id="cb9f9-127">매우 안전 하지 않은 작업</span><span class="sxs-lookup"><span data-stu-id="cb9f9-127">Extremely Destructive Actions</span></span>

<span data-ttu-id="cb9f9-128">일부 작업은 다시 포맷 하는 활성 하드 디스크 파티션 등 야기할입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-128">Some operations are extremely destructive, such as reformatting an active hard disk partition.</span></span> <span data-ttu-id="cb9f9-129">이러한 경우 cmdlet을 설정 해야 `ConfirmImpact`  =  `ConfirmImpact.High` 선언할 때 합니다 [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-129">In these cases, the cmdlet should set `ConfirmImpact` = `ConfirmImpact.High` when declaring the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute.</span></span> <span data-ttu-id="cb9f9-130">이 설정을 사용자 지정 하지 하는 경우에 요청 사용자에 게 확인 하려면 cmdlet을 사용 하면를 `Confirm` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-130">This setting forces the cmdlet to request user confirmation even when the user has not specified the `Confirm` parameter.</span></span> <span data-ttu-id="cb9f9-131">그러나 cmdlet 개발자 안 지나치게 `ConfirmImpact` 사용자 계정 삭제와 같은 잠재적으로 방금 삭제 된 작업에 대 한 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-131">However, cmdlet developers should avoid overusing `ConfirmImpact` for operations that are just potentially destructive, such as deleting a user account.</span></span> <span data-ttu-id="cb9f9-132">경우 `ConfirmImpact` 로 설정 된 [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-132">Remember that if `ConfirmImpact` is set to [System.Management.Automation.Confirmimpact.High](/dotnet/api/System.Management.Automation.ConfirmImpact.High).</span></span>

<span data-ttu-id="cb9f9-133">마찬가지로, 일부 작업을 수행할 이론상에서 수정 Windows PowerShell 외부 시스템의 실행 상태 이지만 시스템을 손상 시키는 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-133">Similarly, some operations are unlikely to be destructive, although they do in theory modify the running state of a system outside Windows PowerShell.</span></span> <span data-ttu-id="cb9f9-134">이러한 cmdlet을 설정할 수 있습니다 `ConfirmImpact` 하 [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-134">Such cmdlets can set `ConfirmImpact` to [System.Management.Automation.Confirmimpact.Low](/dotnet/api/system.management.automation.confirmimpact?view=powershellsdk-1.1.0).</span></span> <span data-ttu-id="cb9f9-135">이 중간 영향 및 강력한 작업을 확인 하 라는 메시지가 표시 된 확인 요청을 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-135">This will bypass confirmation requests where the user has asked to confirm only medium-impact and high-impact operations.</span></span>

## <a name="defining-parameters-for-system-modification"></a><span data-ttu-id="cb9f9-136">시스템 수정에 대 한 매개 변수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-136">Defining Parameters for System Modification</span></span>

<span data-ttu-id="cb9f9-137">이 섹션에는 지원 시스템 수정 하는 데 필요한를 포함 하 여 cmdlet 매개 변수를 정의 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-137">This section describes how to define the cmdlet parameters, including those that are needed to support system modification.</span></span> <span data-ttu-id="cb9f9-138">참조 [해당 프로세스 명령줄 입력 매개 변수 추가](./adding-parameters-that-process-command-line-input.md) 매개 변수를 정의 하는 방법에 대 한 일반 정보 제공 해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-138">See [Adding Parameters that Process CommandLine Input](./adding-parameters-that-process-command-line-input.md) if you need general information about defining parameters.</span></span>

<span data-ttu-id="cb9f9-139">세 가지 매개 변수를 정의 하는 중지 Proc cmdlet: `Name`, `Force`, 및 `PassThru`합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-139">The Stop-Proc cmdlet defines three parameters: `Name`, `Force`, and `PassThru`.</span></span>

<span data-ttu-id="cb9f9-140">합니다 `Name` 에 해당 하는 매개 변수는 `Name` 프로세스 입력된 개체의 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-140">The `Name` parameter corresponds to the `Name` property of the process input object.</span></span> <span data-ttu-id="cb9f9-141">주의는 `Name` 명명 된 프로세스를 중지 되지 않은 경우에 cmdlet이 실패 하는 대로이 샘플의 매개 변수가 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-141">Be aware that the `Name` parameter in this sample is mandatory, as the cmdlet will fail if it does not have a named process to stop.</span></span>

<span data-ttu-id="cb9f9-142">합니다 `Force` 매개 변수로 사용자에 대 한 호출을 재정의할 수 있습니다 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-142">The `Force` parameter allows the user to override calls to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).</span></span> <span data-ttu-id="cb9f9-143">실제로 cmdlet을 호출 하는 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 있어야를 `Force` 매개 변수 있도록 때 `Force` 를 지정 하면 cmdlet에 대 한 호출을 건너뛰고 [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 작업을 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-143">In fact, any cmdlet that calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) should have a `Force` parameter so that when `Force` is specified, the cmdlet skips the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) and proceeds with the operation.</span></span> <span data-ttu-id="cb9f9-144">이 영향을 주지 않습니다에 대 한 호출에 유의 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-144">Be aware that this does not affect calls to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess).</span></span>

<span data-ttu-id="cb9f9-145">`PassThru` 매개 변수는 프로세스를 중지 한 후 cmdlet을 파이프라인을 통해 출력 개체를이 예제의 경우 성공 여부를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-145">The `PassThru` parameter allows the user to indicate whether the cmdlet passes an output object through the pipeline, in this case, after a process is stopped.</span></span> <span data-ttu-id="cb9f9-146">이 매개 변수가 cmdlet 대신 자체 속성에 입력된 개체의 연결 되어 있는지 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-146">Be aware that this parameter is tied to the cmdlet itself instead of to a property of the input object.</span></span>

<span data-ttu-id="cb9f9-147">중지 Proc cmdlet에 대 한 매개 변수 선언은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-147">Here is the parameter declaration for the Stop-Proc cmdlet.</span></span>

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

## <a name="overriding-an-input-processing-method"></a><span data-ttu-id="cb9f9-148">입력 처리 메서드를 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-148">Overriding an Input Processing Method</span></span>

<span data-ttu-id="cb9f9-149">Cmdlet는 입력 처리 메서드를 재정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-149">The cmdlet must override an input processing method.</span></span> <span data-ttu-id="cb9f9-150">다음 코드에서는 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 샘플 중지 Proc cmdlet에 사용 되는 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-150">The following code illustrates the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) override used in the sample Stop-Proc cmdlet.</span></span> <span data-ttu-id="cb9f9-151">프로세스 이름, 요청 각각에 대해이 메서드 프로세스 되었는지 확인 하지는 특별 한 프로세스, 프로세스를 중지 하려고 한 경우 다음 출력 개체를 보냅니다는 `PassThru` 매개 변수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-151">For each requested process name, this method ensures that the process is not a special process, tries to stop the process, and then sends an output object if the `PassThru` parameter is specified.</span></span>

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

## <a name="calling-the-shouldprocess-method"></a><span data-ttu-id="cb9f9-152">ShouldProcess 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-152">Calling the ShouldProcess Method</span></span>

<span data-ttu-id="cb9f9-153">입력 처리 cmdlet의 메서드를 호출 해야 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 변경 (예를 들어, 파일 삭제) 실행 중 상태로 되기 전에 작업의 실행을 확인 하는 방법 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-153">The input processing method of your cmdlet should call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to confirm execution of an operation before a change (for example, deleting files) is made to the running state of the system.</span></span> <span data-ttu-id="cb9f9-154">이 사용 하면 Windows PowerShell 런타임이 셸 내에서 올바른 "WhatIf" 및 "확인" 동작을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-154">This allows the Windows PowerShell runtime to supply the correct "WhatIf" and "Confirm" behavior within the shell.</span></span>

> [!NOTE]
> <span data-ttu-id="cb9f9-155">Cmdlet을 지 원하는 경우 처리 해야 하 고에 실패 했습니다. 합니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 호출 사용자 시스템을 예기치 않게 수정 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-155">If a cmdlet states that it supports should process and fails to make the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call, the user might modify the system unexpectedly.</span></span>

<span data-ttu-id="cb9f9-156">에 대 한 호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 명령줄 설정이 나 기본 설정 변수를 고려 하는 Windows PowerShell 런타임에 사용자에 게 변경 될 리소스의 이름을 전송 사용자에 게 표시 되어야 할 사항을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-156">The call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) sends the name of the resource to be changed to the user, with the Windows PowerShell runtime taking into account any command-line settings or preference variables in determining what should be displayed to the user.</span></span>

<span data-ttu-id="cb9f9-157">다음 예제에 대 한 호출을 보여 줍니다 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 재정의에서 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 예제의 메서드 중지 Proc cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-157">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

```csharp
if (!ShouldProcess(string.Format("{0} ({1})", processName,
                   process.Id)))
{
  continue;
}
```

## <a name="calling-the-shouldcontinue-method"></a><span data-ttu-id="cb9f9-158">ShouldContinue 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-158">Calling the ShouldContinue Method</span></span>

<span data-ttu-id="cb9f9-159">에 대 한 호출을 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 메서드는 사용자에 게 보조 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-159">The call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method sends a secondary message to the user.</span></span> <span data-ttu-id="cb9f9-160">호출한 후에이 호출 [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) 반환 `true` 경우에 `Force` 매개 변수를 설정 하지 않은 `true`합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-160">This call is made after the call to [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) returns `true` and if the `Force` parameter was not set to `true`.</span></span> <span data-ttu-id="cb9f9-161">사용자 작업을 계속 진행 해야 하는지 여부를에 피드백을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-161">The user can then provide feedback to say whether the operation should be continued.</span></span> <span data-ttu-id="cb9f9-162">Cmdlet 호출 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 잠재적으로 위험한 시스템 수정 또는 사용자에 게 전체 예 및 아니요-모든 옵션을 제공 하려는 경우에 대 한 추가 검사 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-162">Your cmdlet calls [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) as an additional check for potentially dangerous system modifications or when you want to provide yes-to-all and no-to-all options to the user.</span></span>

<span data-ttu-id="cb9f9-163">다음 예제에 대 한 호출을 보여 줍니다 [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) 재정의에서 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 예제의 메서드 중지 Proc cmdlet입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-163">The following example shows the call to [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) from the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method in the sample Stop-Proc cmdlet.</span></span>

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

## <a name="stopping-input-processing"></a><span data-ttu-id="cb9f9-164">입력된 처리를 중지 하는 중</span><span class="sxs-lookup"><span data-stu-id="cb9f9-164">Stopping Input Processing</span></span>

<span data-ttu-id="cb9f9-165">입력 처리 메서드 시스템을 수정 하는 cmdlet의 입력 처리를 중지 하는 방법을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-165">The input processing method of a cmdlet that makes system modifications must provide a way of stopping the processing of input.</span></span> <span data-ttu-id="cb9f9-166">이 중지 Proc cmdlet의 경우 호출에서 합니다 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 메서드를 합니다 [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) 메서드.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-166">In the case of this Stop-Proc cmdlet, a call is made from the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method to the [System.Diagnostics.Process.Kill\*](/dotnet/api/System.Diagnostics.Process.Kill) method.</span></span> <span data-ttu-id="cb9f9-167">때문에 합니다 `PassThru` 매개 변수는 설정 `true`를 [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) 도 호출 [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) 보낼 프로세스 개체를 파이프라인입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-167">Because the `PassThru` parameter is set to `true`, [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) also calls [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) to send the process object to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="cb9f9-168">코드 예제</span><span class="sxs-lookup"><span data-stu-id="cb9f9-168">Code Sample</span></span>

<span data-ttu-id="cb9f9-169">전체 C# 코드 샘플을 참조 하십시오 [StopProcessSample01 샘플](./stopprocesssample01-sample.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-169">For the complete C# sample code, see [StopProcessSample01 Sample](./stopprocesssample01-sample.md).</span></span>

## <a name="defining-object-types-and-formatting"></a><span data-ttu-id="cb9f9-170">개체 유형 정의 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="cb9f9-170">Defining Object Types and Formatting</span></span>

<span data-ttu-id="cb9f9-171">Windows PowerShell.Net 개체를 사용 하 여 cmdlet 간에 정보를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-171">Windows PowerShell passes information between cmdlets using .Net objects.</span></span> <span data-ttu-id="cb9f9-172">따라서 cmdlet는 고유한 형식을 정의 해야 합니다. 또는 cmdlet을 다른 cmdlet에서 제공 하는 기존 형식을 확장 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-172">Consequently, a cmdlet may need to define its own type, or the cmdlet may need to extend an existing type provided by another cmdlet.</span></span> <span data-ttu-id="cb9f9-173">새 형식 정의 또는 기존 형식을 확장 하는 방법에 대 한 자세한 내용은 참조 하세요. [확장 개체 형식 및 서식](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-173">For more information about defining new types or extending existing types, see [Extending Object Types and Formatting](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).</span></span>

## <a name="building-the-cmdlet"></a><span data-ttu-id="cb9f9-174">Cmdlet은 빌드</span><span class="sxs-lookup"><span data-stu-id="cb9f9-174">Building the Cmdlet</span></span>

<span data-ttu-id="cb9f9-175">Cmdlet를 구현한 후 등록 해야 Windows PowerShell을 사용 하 여 Windows PowerShell 스냅인을 통해.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-175">After implementing a cmdlet, it must be registered with Windows PowerShell through a Windows PowerShell snap-in.</span></span> <span data-ttu-id="cb9f9-176">Cmdlet을 등록 하는 방법에 대 한 자세한 내용은 참조 하세요. [등록 Cmdlet, 공급자 및 응용 프로그램을 호스트 하는 방법을](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-176">For more information about registering cmdlets, see [How to Register Cmdlets, Providers, and Host Applications](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).</span></span>

## <a name="testing-the-cmdlet"></a><span data-ttu-id="cb9f9-177">테스트 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="cb9f9-177">Testing the Cmdlet</span></span>

<span data-ttu-id="cb9f9-178">Windows PowerShell cmdlet에 등록 하는 경우 명령줄에서 실행 하 여 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-178">When your cmdlet has been registered with Windows PowerShell, you can test it by running it on the command line.</span></span> <span data-ttu-id="cb9f9-179">중지 Proc cmdlet을 테스트 하는 몇 가지 테스트는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-179">Here are several tests that test the Stop-Proc cmdlet.</span></span> <span data-ttu-id="cb9f9-180">명령줄에서 cmdlet을 사용 하는 방법에 대 한 자세한 내용은 참조는 [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell)합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-180">For more information about using cmdlets from the command line, see the [Getting Started with Windows PowerShell](/powershell/scripting/getting-started/getting-started-with-windows-powershell).</span></span>

- <span data-ttu-id="cb9f9-181">Windows PowerShell을 시작 및 중지 Proc cmdlet을 사용 하 여 아래와 같이 처리를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-181">Start Windows PowerShell and use the Stop-Proc cmdlet to stop processing as shown below.</span></span> <span data-ttu-id="cb9f9-182">Cmdlet은 지정 하기 때문에 `Name` 필수 매개 변수, 매개 변수에 대해 cmdlet 쿼리 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-182">Because the cmdlet specifies the `Name` parameter as mandatory, the cmdlet queries for the parameter.</span></span>

    ```powershell
    PS> stop-proc
    ```

<span data-ttu-id="cb9f9-183">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-183">The following output appears.</span></span>

    ```
    Cmdlet stop-proc at command pipeline position 1
    Supply values for the following parameters:
    Name[0]:
    ```

- <span data-ttu-id="cb9f9-184">이제 "NOTEPAD" 라는 프로세스를 중지 하려면 cmdlet을 사용해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-184">Now let's use the cmdlet to stop the process named "NOTEPAD".</span></span> <span data-ttu-id="cb9f9-185">Cmdlet를 사용 하 여 작업을 확인 하려면 묻습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-185">The cmdlet asks you to confirm the action.</span></span>

    ```powershell
    PS> stop-proc -Name notepad
    ```

<span data-ttu-id="cb9f9-186">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-186">The following output appears.</span></span>

    ```
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "notepad (4996)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    ```

- <span data-ttu-id="cb9f9-187">"WINLOGON" 라는 중요 한 프로세스를 중지 하려면 표시 된 것 처럼 중지 프로시저를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-187">Use Stop-Proc as shown to stop the critical process named "WINLOGON".</span></span> <span data-ttu-id="cb9f9-188">메시지가 표시 하 고 다시 부팅 하려면 운영 체제를 발생 시키기 때문에이 작업을 수행 하는 방법에 대 한 경고가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-188">You are prompted and warned about performing this action because it will cause the operating system to reboot.</span></span>

    ```powershell
    PS> stop-proc -Name Winlogon
    ```

<span data-ttu-id="cb9f9-189">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-189">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): Y
    Warning!
    The process " winlogon " is a critical process and should not be stopped. Are you sure you wish to stop the process?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

- <span data-ttu-id="cb9f9-190">경고를 수신 하지 않고 WINLOGON 프로세스를 중지 하려면 이제 사용해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-190">Let's now try to stop the WINLOGON process without receiving a warning.</span></span> <span data-ttu-id="cb9f9-191">이 명령은 항목에서 사용 하는 주의 `Force` 경고 재정의 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-191">Be aware that this command entry uses the `Force` parameter to override the warning.</span></span>

    ```powershell
    PS> stop-proc -Name winlogon -Force
    ```

<span data-ttu-id="cb9f9-192">다음과 같은 출력이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb9f9-192">The following output appears.</span></span>

    ```output
    Confirm
    Are you sure you want to perform this action?
    Performing operation "stop-proc" on Target "winlogon (656)".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): N
    ```

## <a name="see-also"></a><span data-ttu-id="cb9f9-193">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cb9f9-193">See Also</span></span>

[<span data-ttu-id="cb9f9-194">명령줄 입력을 처리 하는 매개 변수 추가</span><span class="sxs-lookup"><span data-stu-id="cb9f9-194">Adding Parameters that Process Command-Line Input</span></span>](./adding-parameters-that-process-command-line-input.md)

[<span data-ttu-id="cb9f9-195">확장 개체 형식 및 서식 지정</span><span class="sxs-lookup"><span data-stu-id="cb9f9-195">Extending Object Types and Formatting</span></span>](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[<span data-ttu-id="cb9f9-196">Cmdlet, 공급자, 등록 및 응용 프로그램을 호스트 하는 방법</span><span class="sxs-lookup"><span data-stu-id="cb9f9-196">How to Register Cmdlets, Providers, and Host Applications</span></span>](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[<span data-ttu-id="cb9f9-197">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="cb9f9-197">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

[<span data-ttu-id="cb9f9-198">Cmdlet 샘플</span><span class="sxs-lookup"><span data-stu-id="cb9f9-198">Cmdlet Samples</span></span>](./cmdlet-samples.md)