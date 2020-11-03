---
description: PowerShell 워크플로 기능에 대 한 간략 한 소개를 제공 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflows?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Workflows
ms.openlocfilehash: fbd8ee62b1e9c6969d489c5024c33f5cca883dc6
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221849"
---
# <a name="about-workflows"></a><span data-ttu-id="c9a97-104">워크플로 정보</span><span class="sxs-lookup"><span data-stu-id="c9a97-104">About Workflows</span></span>

## <a name="short-description"></a><span data-ttu-id="c9a97-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="c9a97-105">Short description</span></span>

<span data-ttu-id="c9a97-106">PowerShell 워크플로 기능에 대 한 간략 한 소개를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-106">Provides a brief introduction to the PowerShell Workflow feature.</span></span>

## <a name="long-description"></a><span data-ttu-id="c9a97-107">자세한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-107">Long description</span></span>

<span data-ttu-id="c9a97-108">PowerShell 워크플로는 [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) 의 이점을 powershell로 제공 하 고 워크플로를 작성 하 고 실행할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-108">PowerShell Workflow brings the benefits of the [Windows Workflow Foundation](/dotnet/framework/windows-workflow-foundation) to PowerShell and enables you to write and run workflows.</span></span>

<span data-ttu-id="c9a97-109">Powershell 워크플로는 powershell 3.0에서 도입 되었으며 모듈은 PowerShell 5.1까지 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-109">PowerShell Workflow was introduced in PowerShell 3.0 and the module is available up to PowerShell 5.1.</span></span> <span data-ttu-id="c9a97-110">PowerShell 워크플로에 대 한 자세한 내용은 [워크플로 가이드](/previous-versions/powershell/scripting/components/workflows-guide) 및 [Windows PowerShell 워크플로 작성](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9a97-110">For more information about PowerShell Workflow, see the [Workflows Guide](/previous-versions/powershell/scripting/components/workflows-guide) and [Writing a Windows PowerShell Workflow](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow).</span></span>

## <a name="about-workflows"></a><span data-ttu-id="c9a97-111">워크플로 정보</span><span class="sxs-lookup"><span data-stu-id="c9a97-111">About workflows</span></span>

<span data-ttu-id="c9a97-112">워크플로는 일련의 관련 작업으로 구성 된 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-112">Workflows are commands that consist of an ordered sequence of related activities.</span></span> <span data-ttu-id="c9a97-113">일반적으로 다른 유형의 환경에서 많은 수의 데이터를 수집 하 여 수백 대의 컴퓨터를 변경 하는 데 오랜 시간 동안 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-113">Typically, they run for an extended period of time, gathering data from and making changes to hundreds of computers, often in heterogeneous environments.</span></span>

<span data-ttu-id="c9a97-114">워크플로는 XAML, Windows Workflow Foundation에 사용 되는 언어 또는 PowerShell 언어로 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-114">Workflows can be written in XAML, the language used in Windows Workflow Foundation, or in the PowerShell language.</span></span> <span data-ttu-id="c9a97-115">워크플로는 일반적으로 모듈에 패키지 되며 도움말 항목을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-115">Workflows are typically packaged in modules and include help topics.</span></span> <span data-ttu-id="c9a97-116">자세한 내용은 [XAML 개요 (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9a97-116">For more information, see [XAML Overview (WPF)](/dotnet/framework/wpf/advanced/xaml-overview-wpf).</span></span>

<span data-ttu-id="c9a97-117">워크플로는 다시 부팅 하 고 일반적인 오류 로부터 자동으로 복구할 수 있기 때문에 IT 환경에서 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-117">Workflows are critical in an IT environment because they can survive reboots and recover automatically from common failures.</span></span> <span data-ttu-id="c9a97-118">워크플로 처리를 중단 하지 않고 워크플로를 실행 하는 세션 및 컴퓨터에서 연결을 끊고 다시 연결 하 고, 데이터 손실 없이 워크플로를 일시 중단 하 고 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-118">You can disconnect and reconnect from sessions and computers running workflows without interrupting workflow processing, and suspend and resume workflows transparently without data loss.</span></span> <span data-ttu-id="c9a97-119">워크플로의 각 작업을 기록 하 고 참조를 감사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-119">Each activity in a workflow can be logged and audited for reference.</span></span>
<span data-ttu-id="c9a97-120">워크플로는 작업으로 실행 될 수 있으며 PowerShell의 예약 된 작업 기능을 사용 하 여 예약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-120">Workflows can run as jobs and can be scheduled by using the Scheduled Jobs feature of PowerShell.</span></span>

<span data-ttu-id="c9a97-121">워크플로의 상태와 데이터는 워크플로의 시작과 끝 및 지정 된 지점에 저장 되거나 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-121">The state and data in a workflow is saved or persisted at the beginning and end of the workflow and at points that you specify.</span></span> <span data-ttu-id="c9a97-122">워크플로 지 속성 지점은 데이터베이스 스냅숏 또는 프로그램 검사점과 같은 작업을 수행 하 여 중단 및 오류의 영향 으로부터 워크플로를 보호 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-122">Workflow persistence points work like database snapshots or program checkpoints to protect the workflow from the effects of interruptions and failures.</span></span> <span data-ttu-id="c9a97-123">워크플로에서 오류를 복구할 수 없는 경우 처음부터 광범위 한 워크플로를 다시 실행 하는 대신 지속형 데이터를 사용 하 고 마지막 지 속성 지점에서 재개할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-123">If the workflow is unable to recover from a failure, you can use the persisted data and resume from the last persistence point, instead of rerunning an extensive workflow from the beginning.</span></span>

## <a name="workflow-requirements-and-configuration"></a><span data-ttu-id="c9a97-124">워크플로 요구 사항 및 구성</span><span class="sxs-lookup"><span data-stu-id="c9a97-124">Workflow requirements and configuration</span></span>

<span data-ttu-id="c9a97-125">PowerShell 워크플로 구성은 다음 요소로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-125">A PowerShell Workflow configuration consists of the following elements:</span></span>

- <span data-ttu-id="c9a97-126">워크플로를 실행 하는 클라이언트 컴퓨터</span><span class="sxs-lookup"><span data-stu-id="c9a97-126">A client computer, which runs the workflow.</span></span>
- <span data-ttu-id="c9a97-127">클라이언트 컴퓨터 또는 원격 컴퓨터의 워크플로 세션 **PSSession**</span><span class="sxs-lookup"><span data-stu-id="c9a97-127">A workflow session, **PSSession** , on the client computer or on a remote computer.</span></span>
- <span data-ttu-id="c9a97-128">워크플로 활동의 영향을 받는 대상 컴퓨터인 관리 되는 노드입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-128">Managed nodes, the target computers that are affected by the workflow activities.</span></span>

<span data-ttu-id="c9a97-129">워크플로 세션은 필요 하지 않지만 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-129">The workflow session isn't required, but is recommended.</span></span> <span data-ttu-id="c9a97-130">**Pssessions** 는 PowerShell의 강력한 복구 및 연결 되지 않은 세션 기능을 활용 하 여 연결 되지 않은 워크플로 세션을 복구할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-130">**PSSessions** can take advantage of the robust recovery and Disconnected Sessions features of PowerShell to recover disconnected workflow sessions.</span></span> <span data-ttu-id="c9a97-131">자세한 내용은 [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9a97-131">For more information, see [about_Remote_Disconnected_Sessions](../../Microsoft.PowerShell.Core/About/about_Remote_Disconnected_Sessions.md)</span></span>

<span data-ttu-id="c9a97-132">워크플로 세션이 실행 되는 컴퓨터와 클라이언트 컴퓨터는 관리 되는 노드가 될 수 있으므로 모든 역할을 충족 하는 단일 컴퓨터에서 워크플로를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-132">Because the client computer and the computer on which the workflow session runs can be managed nodes, you can run a workflow on a single computer that fulfills all roles.</span></span>

<span data-ttu-id="c9a97-133">클라이언트 컴퓨터와 워크플로 세션이 실행 되는 컴퓨터에서 PowerShell 3.0을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-133">The client computer and the computer on which the workflow session runs must be running PowerShell 3.0.</span></span> <span data-ttu-id="c9a97-134">Windows Server 운영 체제의 Server Core 설치 옵션을 포함 하 여 적합 한 모든 시스템이 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-134">All eligible systems are supported, including the Server Core installation options of Windows Server operating systems.</span></span>

<span data-ttu-id="c9a97-135">Cmdlet을 포함 하는 워크플로를 실행 하려면 관리 되는 노드에 Windows PowerShell 2.0 이상이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-135">To run workflows that include cmdlets, the managed nodes must have Windows PowerShell 2.0 or later.</span></span> <span data-ttu-id="c9a97-136">워크플로에 cmdlet이 포함 되어 있지 않으면 관리 되는 노드에 PowerShell이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-136">Managed nodes don't require PowerShell unless the workflow includes cmdlets.</span></span> <span data-ttu-id="c9a97-137">PowerShell이 없는 컴퓨터에 WMI(Windows Management Instrumentation) (WMI) 및 CIM(Common Information Model) (CIM) 명령을 포함 하는 워크플로를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-137">You can run workflows that include Windows Management Instrumentation (WMI) and Common Information Model (CIM) commands on computers that don't have PowerShell.</span></span>

## <a name="how-to-get-workflows"></a><span data-ttu-id="c9a97-138">워크플로를 가져오는 방법</span><span class="sxs-lookup"><span data-stu-id="c9a97-138">How to get workflows</span></span>

<span data-ttu-id="c9a97-139">워크플로는 일반적으로 모듈에 패키지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-139">Workflows are typically packaged in modules.</span></span> <span data-ttu-id="c9a97-140">워크플로를 포함 하는 모듈을 가져오려면 모듈의 명령을 사용 하거나 cmdlet을 사용 `Import-Module` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-140">To import the module that includes a workflow, use any command in the module or use the `Import-Module` cmdlet.</span></span>
<span data-ttu-id="c9a97-141">모듈의 명령을 처음 사용할 때 자동으로 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-141">Modules are imported automatically on first use of any command in the module.</span></span>

<span data-ttu-id="c9a97-142">컴퓨터에 설치 된 모듈에서 워크플로를 찾으려면 `Get-Command` cmdlet의 **CommandType** 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-142">To find the workflows in modules installed on your computer, use the `Get-Command` cmdlet's **CommandType** parameter.</span></span>

```powershell
Get-Command -CommandType Workflow
```

## <a name="how-to-run-workflows"></a><span data-ttu-id="c9a97-143">워크플로를 실행 하는 방법</span><span class="sxs-lookup"><span data-stu-id="c9a97-143">How to run workflows</span></span>

<span data-ttu-id="c9a97-144">워크플로를 실행 하려면 다음 절차를 따르십시오.</span><span class="sxs-lookup"><span data-stu-id="c9a97-144">To run a workflow, use the following procedure.</span></span>

1. <span data-ttu-id="c9a97-145">관리 되는 노드가 로컬 컴퓨터인 경우에는이 단계가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-145">When the managed node is the local computer, this step isn't required.</span></span>
   <span data-ttu-id="c9a97-146">그렇지 않으면 클라이언트 컴퓨터에서 **관리자 권한으로 실행** 옵션을 사용 하 여 PowerShell을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-146">Otherwise, on the client computer, start PowerShell with the **Run as administrator** option.</span></span>

   ```powershell
   Start-Process PowerShell -Verb RunAs
   ```

1. <span data-ttu-id="c9a97-147">워크플로 세션을 실행 하는 컴퓨터와 cmdlet을 포함 하는 워크플로의 영향을 받는 관리 되는 노드에서 PowerShell 원격을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-147">Enable PowerShell remoting on the computer that runs the workflow session and on managed nodes affected by workflows that include cmdlets.</span></span>

   <span data-ttu-id="c9a97-148">참여 하는 각 컴퓨터에서이 단계를 한 번만 수행 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-148">You only need to do this step once on each participating computer.</span></span>

   <span data-ttu-id="c9a97-149">Cmdlet을 포함 하는 워크플로를 실행 하는 경우에만이 단계가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-149">This step is required only when running workflows that include cmdlets.</span></span> <span data-ttu-id="c9a97-150">워크플로 세션이 클라이언트 컴퓨터에서 실행 되는 경우 또는 PowerShell 3.0를 실행 하는 모든 관리 되는 노드에서 클라이언트 컴퓨터에서 원격 기능을 사용 하도록 설정할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-150">You don't need to enable remoting on the client computer, unless the workflows session runs on the client computer, or on any managed nodes that are running PowerShell 3.0.</span></span>

   <span data-ttu-id="c9a97-151">원격 기능을 사용 하도록 설정 하려면 cmdlet을 사용 `Enable-PSRemoting` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-151">To enable remoting, use the `Enable-PSRemoting` cmdlet.</span></span>

   ```powershell
   Enable-PSRemoting -Force
   ```

   <span data-ttu-id="c9a97-152">**스크립트 실행** 그룹 정책 설정을 사용 하 여 원격 기능을 사용 하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-152">You can enable remoting by using the **Turn on Script Execution** Group Policy setting.</span></span> <span data-ttu-id="c9a97-153">자세한 내용은 [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) 및 [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9a97-153">For more information, see [about_Group_Policy_Settings](../../Microsoft.PowerShell.Core/About/about_Group_Policy_Settings.md) and [about_Execution_Policies](../../Microsoft.PowerShell.Core/About/about_Execution_Policies.md).</span></span>

1. <span data-ttu-id="c9a97-154">`New-PSWorkflowSession`또는 `New-PSSession` cmdlet을 사용 하 여 워크플로 세션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-154">Use the `New-PSWorkflowSession` or `New-PSSession` cmdlets to create the workflow session.</span></span>

   <span data-ttu-id="c9a97-155">`New-PSWorkflowSession`Cmdlet은 대상 컴퓨터에서 기본 제공 되는 **Microsoft PowerShell 워크플로** 세션 구성을 사용 하는 세션을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-155">The `New-PSWorkflowSession` cmdlet starts a session that uses the built-in **Microsoft.PowerShell.Workflow** session configuration on the destination computer.</span></span> <span data-ttu-id="c9a97-156">이 세션 구성에는 스크립트, 형식 및 서식 파일, 워크플로에 대해 설계 된 옵션이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-156">This session configuration includes scripts, type and formatting files, and options that are designed for workflows.</span></span>

   <span data-ttu-id="c9a97-157">또는 cmdlet을 사용 `New-PSSession` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-157">Or, use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="c9a97-158">**ConfigurationName** 매개 변수를 사용 하 여 **Microsoft. PowerShell 워크플로** 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-158">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span> <span data-ttu-id="c9a97-159">이 명령은 cmdlet을 사용 하는 것과 같습니다 `New-PSWorkflowSession` .</span><span class="sxs-lookup"><span data-stu-id="c9a97-159">This command is the same as using the `New-PSWorkflowSession` cmdlet.</span></span>

   <span data-ttu-id="c9a97-160">다른 방법은 cmdlet을 사용 하는 것입니다 `New-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="c9a97-160">An alternative is to use the `New-PSSession` cmdlet.</span></span> <span data-ttu-id="c9a97-161">**ConfigurationName** 매개 변수를 사용 하 여 **Microsoft. PowerShell 워크플로** 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-161">Use the **ConfigurationName** parameter to specify the **Microsoft.PowerShell.Workflow** session configuration.</span></span>

   <span data-ttu-id="c9a97-162">로컬 컴퓨터에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-162">On the local computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession
   ```

   <span data-ttu-id="c9a97-163">원격 컴퓨터에서 다음을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-163">On a remote computer:</span></span>

   ```powershell
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

   <span data-ttu-id="c9a97-164">워크플로 세션 컴퓨터의 관리자 인 경우 cmdlet을 사용 `New-PSWorkflowExecutionOption` 하 여 워크플로 세션 구성에 대 한 사용자 지정 옵션 설정을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-164">If you are an Administrator on the workflow session computer, you can use the `New-PSWorkflowExecutionOption` cmdlet to create custom option settings for the workflow session configuration.</span></span> <span data-ttu-id="c9a97-165">Cmdlet을 사용 `Set-PSSessionConfiguration` 하 여 세션 구성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-165">And, use the `Set-PSSessionConfiguration` cmdlet to change the session configuration.</span></span>

   ```powershell
   $sto = New-PSWorkflowExecutionOption -MaxConnectedSessions 150
   Invoke-Command -ComputerName Server01 `
   {Set-PSSessionConfiguration Microsoft.PowerShell.Workflow `
   -SessionTypeOption $Using:sto}
   $ws = New-PSWorkflowSession -ComputerName Server01 `
   -Credential Domain01\Admin01
   ```

1. <span data-ttu-id="c9a97-166">워크플로 세션에서 워크플로를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-166">Run the workflow in the workflow session.</span></span> <span data-ttu-id="c9a97-167">관리 되는 노드 (대상 컴퓨터)의 이름을 지정 하려면 **PSComputerName** 워크플로 일반 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-167">To specify the names of the managed nodes, target computers, use the **PSComputerName** workflow common parameter.</span></span>

   <span data-ttu-id="c9a97-168">다음 예제에서는 **테스트** 워크플로 라는 워크플로를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-168">The following examples run the workflow named **Test-Workflow**.</span></span>

   <span data-ttu-id="c9a97-169">여기서 관리 되는 노드는 워크플로 세션을 호스트 하는 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-169">Where the managed node is the computer that hosts the workflow session:</span></span>

   ```powershell
   Invoke-Command -Session $ws {Test-Workflow}
   ```

   <span data-ttu-id="c9a97-170">여기에서 관리 되는 노드는 원격 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-170">Where the managed nodes are remote computers.</span></span>

   ```powershell
   Invoke-Command -Session $ws{
   Test-Workflow -PSComputerName Server01, Server02 }
   ```

   <span data-ttu-id="c9a97-171">다음 예제에서는 수백 대의 컴퓨터에서 **테스트 워크플로** 를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-171">The following example runs the **Test-Workflow** on hundreds of computers.</span></span> <span data-ttu-id="c9a97-172">`Get-Content`Cmdlet은 텍스트 파일에서 컴퓨터 이름을 가져와서 `$Servers` 로컬 컴퓨터의 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-172">The `Get-Content` cmdlet gets the computer names from a text file and saves them in the `$Servers` variable on the local computer.</span></span>

   <span data-ttu-id="c9a97-173">`Invoke-Command` 범위 한정자를 사용 하 여 `$Using` `$Servers` 로컬 세션에서 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-173">`Invoke-Command` uses the `$Using` scope modifier to define the `$Servers` variable in the local session.</span></span> <span data-ttu-id="c9a97-174">범위 한정자에 대 한 자세한 내용은 `$Using` [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9a97-174">For more information about the `$Using` scope modifier, see [about_Remote_Variables](../../Microsoft.PowerShell.Core/About/about_Remote_Variables.md).</span></span>

   ```powershell
   $Servers = Get-Content Servers.txt
   Invoke-Command -Session $ws {Test-Workflow -PSComputerName $Using:Servers }
   ```

## <a name="using-workflow-common-parameters"></a><span data-ttu-id="c9a97-175">워크플로 일반 매개 변수 사용</span><span class="sxs-lookup"><span data-stu-id="c9a97-175">Using workflow common parameters</span></span>

<span data-ttu-id="c9a97-176">워크플로 일반 매개 변수는 PowerShell이 모든 워크플로에 자동으로 추가 하는 매개 변수 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-176">The workflow common parameters are a set of parameters that PowerShell adds automatically to all workflows.</span></span> <span data-ttu-id="c9a97-177">워크플로에서 **Cmdletbinding** 특성을 사용 하지 않는 경우에도 PowerShell은 모든 워크플로에 cmdlet 일반 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-177">PowerShell adds the cmdlet common parameters to all workflows, even if the workflow doesn't use the **CmdletBinding** attribute.</span></span>

<span data-ttu-id="c9a97-178">예를 들어 다음 워크플로는 매개 변수를 정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-178">For example, the following workflow defines no parameters.</span></span> <span data-ttu-id="c9a97-179">그러나 워크플로를 실행 하는 경우 **CommonParameters** 와 **WorkflowCommonParameters** 가 모두 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-179">However, when you run the workflow, it has both the **CommonParameters** and **WorkflowCommonParameters**.</span></span>

```powershell
workflow Test-Workflow {Get-Process}
Get-Command Test-Workflow -Syntax
```

```powershell
Test-Workflow [<WorkflowCommonParameters>] [<CommonParameters>]
```

<span data-ttu-id="c9a97-180">워크플로 일반 매개 변수에는 워크플로를 실행 하는 데 필수적인 몇 가지 매개 변수가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-180">The workflow common parameters include several parameters that are essential to running workflows.</span></span> <span data-ttu-id="c9a97-181">예를 들어 **PSComputerName** 일반 매개 변수는 워크플로가 영향을 주는 관리 되는 노드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-181">For example, the **PSComputerName** common parameter specifies the managed nodes that the workflow affects.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02
}
```

<span data-ttu-id="c9a97-182">**Pspersist** 워크플로 일반 매개 변수는 워크플로 데이터가 유지 되는 시기를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-182">The **PSPersist** workflow common parameter determines when workflow data is persisted.</span></span> <span data-ttu-id="c9a97-183">이를 통해 지 속성 포인트를 정의 하지 않는 워크플로에 활동 간 지 속성 지점을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-183">It enables you to add persistence point between activities to workflows that don't define persistence points.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPersist:$True
}
```

<span data-ttu-id="c9a97-184">다른 워크플로 일반 매개 변수를 사용 하면 관리 되는 노드에 대 한 원격 연결의 특성을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-184">Other workflow common parameters let you specify the characteristics of the remote connection to the managed nodes.</span></span> <span data-ttu-id="c9a97-185">이름 및 기능은 원격 cmdlet의 매개 변수 (포함)와 유사 `Invoke-Command` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-185">Their names and functionality are similar to the parameters of remoting cmdlets, including `Invoke-Command`.</span></span>

```powershell
Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSPort 443
}
```

<span data-ttu-id="c9a97-186">관리 되는 노드에 대 한 연결을 정의 하는 **PS 접두사** 워크플로 일반 매개 변수에서 워크플로 세션에 대 한 연결을 정의 하는 원격 매개 변수를 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-186">Take care to distinguish the remoting parameters that define the connection for the workflow session from the **PS-prefixed** workflow common parameters that define the connection to the managed nodes.</span></span>

```powershell
$ws = New-PSSession -ComputerName Server01 -ConfigurationName Microsoft.PowerShell.Workflow

Invoke-Command -Session $ws {
  Test-Workflow -PSComputerName Server01, Server02 -PSConfigurationName Microsoft.PowerShell.Workflow
}
```

<span data-ttu-id="c9a97-187">일부 워크플로 일반 매개 변수는 여러 원격 노드에 대해 서로 다른 워크플로 일반 매개 변수 값을 지정할 수 있는 **PSParameterCollection** 매개 변수와 같은 워크플로에 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="c9a97-187">Some workflow common parameters are unique to workflows, such as the **PSParameterCollection** parameter that lets you specify different workflow common parameter values for different remote nodes.</span></span> <span data-ttu-id="c9a97-188">워크플로 일반 매개 변수에 대 한 목록 및 설명은 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c9a97-188">For a list and description of the workflow common parameters, see [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9a97-189">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c9a97-189">See also</span></span>

[<span data-ttu-id="c9a97-190">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="c9a97-190">Invoke-AsWorkflow</span></span>](xref:PSWorkflowUtility.Invoke-AsWorkflow)

[<span data-ttu-id="c9a97-191">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="c9a97-191">New-PSSession</span></span>](xref:Microsoft.PowerShell.Core.New-PSSession)

<span data-ttu-id="c9a97-192">[Psworkflow](xref:PSWorkflow) cmdlet</span><span class="sxs-lookup"><span data-stu-id="c9a97-192">[PSWorkflow](xref:PSWorkflow) cmdlets</span></span>

[<span data-ttu-id="c9a97-193">워크플로 가이드</span><span class="sxs-lookup"><span data-stu-id="c9a97-193">Workflows Guide</span></span>](/previous-versions/powershell/scripting/components/workflows-guide)

[<span data-ttu-id="c9a97-194">Windows PowerShell 워크플로 작성</span><span class="sxs-lookup"><span data-stu-id="c9a97-194">Writing a Windows PowerShell Workflow</span></span>](/previous-versions/powershell/scripting/developer/workflow/writing-a-windows-powershell-workflow)
