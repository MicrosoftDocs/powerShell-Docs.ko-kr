---
description: Windows PowerShell 워크플로에서 활동에 추가 하는 매개 변수를 설명 합니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_activitycommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_ActivityCommonParameters
ms.openlocfilehash: b745bf17e4ae26156042ecdc25211830177bc692
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221914"
---
# <a name="about-activitycommonparameters"></a><span data-ttu-id="9ff31-104">ActivityCommonParameters 정보</span><span class="sxs-lookup"><span data-stu-id="9ff31-104">About ActivityCommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="9ff31-105">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="9ff31-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="9ff31-106">Windows PowerShell 워크플로에서 활동에 추가 하는 매개 변수를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-106">Describes the parameters that Windows PowerShell Workflow adds to activities.</span></span>

## <a name="long-description"></a><span data-ttu-id="9ff31-107">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="9ff31-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="9ff31-108">Windows PowerShell 워크플로는 PSActivity 기본 클래스에서 파생 된 활동에 활동 일반 매개 변수를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-108">Windows PowerShell Workflow adds the activity common parameters to activities that are derived from the PSActivity base class.</span></span> <span data-ttu-id="9ff31-109">이 범주에는 Get-Process 및 WinEvent와 같이 활동으로 구현 되는 InlineScript 활동 및 Windows PowerShell cmdlet이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-109">This category includes the InlineScript activity and Windows PowerShell cmdlets that are implemented as activities, such as Get-Process and Get-WinEvent.</span></span>

<span data-ttu-id="9ff31-110">활동 일반 매개 변수는 Suspend-Workflow 및 Checkpoint-Workflow 활동에서 유효 하지 않으며 Windows PowerShell 워크플로가 InlineScript 스크립트 블록이 나 유사한 활동에서 자동으로 실행 하는 cmdlet 또는 식에는 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-110">The activity common parameters are not valid on the Suspend-Workflow and Checkpoint-Workflow activities and they are not added to cmdlets or expressions that Windows PowerShell Workflow automatically runs in an InlineScript script block or similar activity.</span></span> <span data-ttu-id="9ff31-111">InlineScript 활동에서는 활동 일반 매개 변수를 사용할 수 있지만 InlineScript 스크립트 블록의 명령에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-111">The activity common parameters are available on the InlineScript activity, but not on commands in the InlineScript script block.</span></span>

<span data-ttu-id="9ff31-112">활동 일반 매개 변수 중 일부는 워크플로 일반 매개 변수 또는 Windows PowerShell 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-112">Several of the activity common parameters are also workflow common parameters or Windows PowerShell common parameters.</span></span> <span data-ttu-id="9ff31-113">다른 활동 일반 매개 변수는 활동에 대해 고유 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-113">Other activity common parameters are unique to activities.</span></span>

<span data-ttu-id="9ff31-114">워크플로 일반 매개 변수에 대한 자세한 내용은 about_WorkflowCommonParameters를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-114">For information about the workflow common parameters, see about_WorkflowCommonParameters.</span></span> <span data-ttu-id="9ff31-115">Windows PowerShell 일반 매개 변수에 대 한 자세한 내용은 about_CommonParameters를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-115">For information about the Windows PowerShell common parameters, see about_CommonParameters.</span></span>

### <a name="list-of-activity-common-parameters"></a><span data-ttu-id="9ff31-116">활동 일반 매개 변수 목록</span><span class="sxs-lookup"><span data-stu-id="9ff31-116">LIST OF ACTIVITY COMMON PARAMETERS</span></span>

```
AppendOutput                      PSDebug
Debug                             PSDisableSerialization
DisplayName                       PSDisableSerializationPreference
ErrorAction                       PSError
Input                             PSPersist
MergeErrorToOutput                PSPort
PSActionRetryCount                PSProgress
PSActionRetryIntervalSec          PSProgressMessage
PSActionRunningTimeoutSec         PSRemotingBehavior
PSApplicationName                 PSRequiredModules
PSAuthentication                  PSSessionOption
PSCertificateThumbprint           PSUseSSL
PSComputerName                    PSVerbose
PSConfigurationName               PSWarning
PSConnectionRetryCount            Result
PSConnectionRetryIntervalSec      UseDefaultInput
PSConnectionURI                   Verbose
PSCredential                      WarningAction
```

### <a name="parameter-descriptions"></a><span data-ttu-id="9ff31-117">매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="9ff31-117">PARAMETER DESCRIPTIONS</span></span>

<span data-ttu-id="9ff31-118">이 섹션에서는 활동 일반 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-118">This section describes the activity common parameters.</span></span>

#### <a name="appendoutput-boolean"></a><span data-ttu-id="9ff31-119">AppendOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-119">AppendOutput \<Boolean\></span></span>

<span data-ttu-id="9ff31-120">값은 `$True` 변수의 값에 활동의 출력을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-120">A value of `$True` adds the output of the activity to the value of the variable.</span></span>
<span data-ttu-id="9ff31-121">값은 아무런 `$False` 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-121">A value of `$False` has no effect.</span></span> <span data-ttu-id="9ff31-122">기본적으로 값을 변수에 할당하면 변수 값이 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-122">By default, assigning a value to a variable replaces the variable value.</span></span>

<span data-ttu-id="9ff31-123">예를 들어 다음 명령은 변수에서 service 개체에 process 개체를 추가 `$x` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-123">For example, the following commands add a process object to the service object in the `$x` variable.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x = Get-Process -AppendOutput $true
}
```

<span data-ttu-id="9ff31-124">이 매개 변수는 XAML 기반 워크플로 용으로 설계 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-124">This parameter is designed for XAML-based workflows.</span></span> <span data-ttu-id="9ff31-125">스크립트 워크플로에서 다음 예와 같이 + = 대입 연산자를 사용 하 여 출력을 변수 값에 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-125">In script workflows, you can also use the += assignment operator to add output to the value of a variable, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $x = Get-Service
    $x += Get-Process
}
```

#### <a name="debug-switchparameter"></a><span data-ttu-id="9ff31-126">디버그 \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="9ff31-126">Debug \<SwitchParameter\></span></span>

<span data-ttu-id="9ff31-127">명령에 의해 수행 된 작업에 대 한 프로그래머 수준의 세부 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-127">Displays programmer-level detail about the operation performed by the command.</span></span>
<span data-ttu-id="9ff31-128">Debug 매개 변수는 현재 명령에 대 한 $DebugPreference 변수의 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-128">The Debug parameter overrides the value of the $DebugPreference variable for the current command.</span></span> <span data-ttu-id="9ff31-129">이 매개 변수는 명령에서 디버깅 메시지를 생성 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-129">This parameter works only when the command generates debugging messages.</span></span> <span data-ttu-id="9ff31-130">이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-130">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="displayname-string"></a><span data-ttu-id="9ff31-131">DisplayName \<String\></span><span class="sxs-lookup"><span data-stu-id="9ff31-131">DisplayName \<String\></span></span>

<span data-ttu-id="9ff31-132">활동에 식별 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-132">Specifies a friendly name for the activity.</span></span> <span data-ttu-id="9ff31-133">워크플로를 실행 하는 동안 및 워크플로 작업의 Progress 속성 값에서 DisplayName 값이 진행률 표시줄에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-133">The DisplayName value appears in the progress bar while the workflow runs and in the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="9ff31-134">PSProgressMessage 매개 변수가 명령에도 포함 된 경우 진행률 표시줄 콘텐츠가: 형식으로 표시 됩니다 \<DisplayName\> \<PSProgressMessage\> .</span><span class="sxs-lookup"><span data-stu-id="9ff31-134">When the PSProgressMessage parameter is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

#### <a name="erroraction-actionpreference"></a><span data-ttu-id="9ff31-135">ErrorAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="9ff31-135">ErrorAction \<ActionPreference\></span></span>

<span data-ttu-id="9ff31-136">작업이 명령에서 종료 되지 않는 오류에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-136">Determines how the activity responds to a non-terminating error from the command.</span></span> <span data-ttu-id="9ff31-137">종료 오류에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-137">It has no effect on termination errors.</span></span> <span data-ttu-id="9ff31-138">이 매개 변수는 Write-Error cmdlet의 경우와 같이 명령이 종료 되지 않는 오류를 생성 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-138">This parameter works only when the command generates a non-terminating error, such as those from the Write-Error cmdlet.</span></span> <span data-ttu-id="9ff31-139">ErrorAction 매개 변수는 현재 명령에 대 한 $ErrorActionPreference 변수의 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-139">The ErrorAction parameter overrides the value of the $ErrorActionPreference variable for the current command.</span></span> <span data-ttu-id="9ff31-140">이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-140">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="9ff31-141">유효한 값은</span><span class="sxs-lookup"><span data-stu-id="9ff31-141">Valid values:</span></span>

- <span data-ttu-id="9ff31-142">하기.</span><span class="sxs-lookup"><span data-stu-id="9ff31-142">Continue.</span></span> <span data-ttu-id="9ff31-143">오류 메시지를 표시 하 고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-143">Displays the error message and continues executing the command.</span></span> <span data-ttu-id="9ff31-144">"Continue"가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-144">"Continue" is the default value.</span></span>

- <span data-ttu-id="9ff31-145">무시.</span><span class="sxs-lookup"><span data-stu-id="9ff31-145">Ignore.</span></span> <span data-ttu-id="9ff31-146">오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-146">Suppresses the error message and continues executing the command.</span></span>
  <span data-ttu-id="9ff31-147">SilentlyContinue와 달리 Ignore는 $Error 자동 변수에 오류 메시지를 추가 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-147">Unlike SilentlyContinue, Ignore does not add the error message to the $Error automatic variable.</span></span> <span data-ttu-id="9ff31-148">Ignore 값은 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-148">The Ignore value is introduced in Windows PowerShell 3.0.</span></span>

- <span data-ttu-id="9ff31-149">Inquire.</span><span class="sxs-lookup"><span data-stu-id="9ff31-149">Inquire.</span></span> <span data-ttu-id="9ff31-150">오류 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-150">Displays the error message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="9ff31-151">이 값은 거의 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-151">This value is rarely used.</span></span>

- <span data-ttu-id="9ff31-152">일시 중단.</span><span class="sxs-lookup"><span data-stu-id="9ff31-152">Suspend.</span></span> <span data-ttu-id="9ff31-153">추가 조사를 허용 하도록 워크플로 작업을 자동으로 일시 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-153">Automatically suspends a workflow job to allow for further investigation.</span></span> <span data-ttu-id="9ff31-154">조사 후 워크플로를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-154">After investigation, the workflow can be resumed.</span></span>

- <span data-ttu-id="9ff31-155">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="9ff31-155">SilentlyContinue.</span></span> <span data-ttu-id="9ff31-156">오류 메시지를 표시 하지 않고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-156">Suppresses the error message and continues executing the command.</span></span>

- <span data-ttu-id="9ff31-157">중지</span><span class="sxs-lookup"><span data-stu-id="9ff31-157">Stop.</span></span> <span data-ttu-id="9ff31-158">오류 메시지를 표시 하 고 명령 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-158">Displays the error message and stops executing the command.</span></span>

#### <a name="input-object"></a><span data-ttu-id="9ff31-159">입력 \<Object[]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-159">Input \<Object[]\></span></span>

<span data-ttu-id="9ff31-160">개체의 컬렉션을 활동에 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-160">Submits a collection of objects to an activity.</span></span> <span data-ttu-id="9ff31-161">이는 한 번에 하나씩 개체를 활동에 파이프하는 것에 대한 대안입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-161">This is an alternative to piping objects to the activity one at a time.</span></span>

#### <a name="mergeerrortooutput-boolean"></a><span data-ttu-id="9ff31-162">MergeErrorToOutput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-162">MergeErrorToOutput \<Boolean\></span></span>

<span data-ttu-id="9ff31-163">값이 이면 `$True` 출력 스트림에 오류가 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-163">A value of `$True` adds errors to the output stream.</span></span> <span data-ttu-id="9ff31-164">값은 `$False` 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-164">A value of `$False` has not effect.</span></span> <span data-ttu-id="9ff31-165">병렬 및 키워드와 함께이 매개 변수를 사용 `ForEach -Parallel` 하 여 단일 컬렉션의 여러 병렬 명령에서 발생 하는 오류 및 출력을 수집 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-165">Use this parameter with the Parallel and `ForEach -Parallel` keywords to collect errors and output from multiple parallel commands in a single collection.</span></span>

#### <a name="psactionretrycount-int32"></a><span data-ttu-id="9ff31-166">PSActionRetryCount \<Int32\></span><span class="sxs-lookup"><span data-stu-id="9ff31-166">PSActionRetryCount \<Int32\></span></span>

<span data-ttu-id="9ff31-167">첫 번째 시도가 실패하면 반복해서 활동을 실행하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-167">Tries repeatedly to run the activity if the first attempt fails.</span></span> <span data-ttu-id="9ff31-168">기본값 0은 다시 시도하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-168">The default value, 0, does not retry.</span></span>

#### <a name="psactionretryintervalsec-int32"></a><span data-ttu-id="9ff31-169">PSActionRetryIntervalSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="9ff31-169">PSActionRetryIntervalSec \<Int32\></span></span>

<span data-ttu-id="9ff31-170">동작 다시 시도 사이의 간격을 초 단위로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-170">Determines the interval between action retries in seconds.</span></span> <span data-ttu-id="9ff31-171">기본값 0은 동작을 즉시 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-171">The default value, 0, retries the action immediately.</span></span> <span data-ttu-id="9ff31-172">이 매개 변수는 PSActionRetryCount 매개 변수가 명령에도 사용 되는 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-172">This parameter is valid only when the PSActionRetryCount parameter is also used in the command.</span></span>

#### <a name="psactionrunningtimeoutsec-int32"></a><span data-ttu-id="9ff31-173">PSActionRunningTimeoutSec \<Int32\></span><span class="sxs-lookup"><span data-stu-id="9ff31-173">PSActionRunningTimeoutSec \<Int32\></span></span>

<span data-ttu-id="9ff31-174">각 대상 컴퓨터에서 활동이 실행될 수 있는 기간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-174">Determines how long the activity can run on each target computer.</span></span> <span data-ttu-id="9ff31-175">제한 시간이 만료 되기 전에 작업이 완료 되지 않으면 Windows PowerShell 워크플로에서 종료 오류를 생성 하 고 영향을 받는 대상 컴퓨터에서 워크플로 처리를 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-175">If the activity does not complete before the timeout expires, Windows PowerShell Workflow generates a terminating error and stops processing the workflow on the affected target computer.</span></span>

#### <a name="psallowredirection-boolean"></a><span data-ttu-id="9ff31-176">PSAllowRedirection \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-176">PSAllowRedirection \<Boolean\></span></span>

<span data-ttu-id="9ff31-177">$True 값은 대상 컴퓨터에 대 한 연결 리디렉션을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-177">A value of $True allows redirection of the connection to the target computers.</span></span>
<span data-ttu-id="9ff31-178">$False 값은 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-178">A value of $False has no effect.</span></span> <span data-ttu-id="9ff31-179">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-179">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-180">PSConnectionURI 매개 변수를 사용 하는 경우 원격 대상이 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-180">When you use the PSConnectionURI parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="9ff31-181">기본적으로 Windows PowerShell은 연결을 리디렉션하지 않지만, PSAllowRedirection 매개 변수를 $True 값과 함께 사용 하 여 대상 컴퓨터에 대 한 연결 리디렉션을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-181">By default, Windows PowerShell does not redirect connections, but you can use the PSAllowRedirection parameter with a value of $True to allow redirection of the connection to the target computer.</span></span>

<span data-ttu-id="9ff31-182">`$PSSessionOption`기본 설정 변수의 MaximumConnectionRedirectionCount 속성을 설정 하거나 세션을 만드는 cmdlet의 SSessionOption 매개 변수 값의 MaximumConnectionRedirectionCount 속성을 설정 하 여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-182">You can also limit the number of times that the connection is redirected by setting the MaximumConnectionRedirectionCount property of the `$PSSessionOption` preference variable, or the MaximumConnectionRedirectionCount property of the value of the SSessionOption parameter of cmdlets that create a session.</span></span> <span data-ttu-id="9ff31-183">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-183">The default value is 5.</span></span>

#### <a name="psapplicationname-string"></a><span data-ttu-id="9ff31-184">PSApplicationName \<String\></span><span class="sxs-lookup"><span data-stu-id="9ff31-184">PSApplicationName \<String\></span></span>

<span data-ttu-id="9ff31-185">대상 컴퓨터에 연결 하는 데 사용 되는 연결 URI의 응용 프로그램 이름 세그먼트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-185">Specifies the application name segment of the connection URI that is used to connect to the target computers.</span></span> <span data-ttu-id="9ff31-186">이 매개 변수를 사용하여 명령에 ConnectionURI 매개 변수를 사용하지 않는 경우 애플리케이션 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-186">Use this parameter to specify the application name when you are not using the ConnectionURI parameter in the command.</span></span> <span data-ttu-id="9ff31-187">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-187">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-188">기본값은 `$PSSessionApplicationName` 대상 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-188">The default value is the value of the `$PSSessionApplicationName` preference variable on the target computer.</span></span> <span data-ttu-id="9ff31-189">이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-189">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="9ff31-190">이 값은 대부분의 사용에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-190">This value is appropriate for most uses.</span></span> <span data-ttu-id="9ff31-191">자세한 내용은 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-191">For more information, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="9ff31-192">WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-192">The WinRM service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="9ff31-193">이 매개 변수 값은 원격 컴퓨터에 있는 수신기의 URLPrefix 속성 값과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-193">The value of this parameter should match the value of the URLPrefix property of a listener on the remote computer.</span></span>

#### <a name="psauthentication-authenticationmechanism"></a><span data-ttu-id="9ff31-194">PSAuthentication \<AuthenticationMechanism\></span><span class="sxs-lookup"><span data-stu-id="9ff31-194">PSAuthentication \<AuthenticationMechanism\></span></span>

<span data-ttu-id="9ff31-195">대상 컴퓨터에 연결할 때 사용자의 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-195">Specifies the mechanism that is used to authenticate the user's credentials when connecting to the target computers.</span></span> <span data-ttu-id="9ff31-196">유효한 값은 Default, Basic, Credssp, Digest, Kerberos, Negotiate 및 NegotiateWithImplicitCredential입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-196">Valid values are Default, Basic, Credssp, Digest, Kerberos, Negotiate, and NegotiateWithImplicitCredential.</span></span> <span data-ttu-id="9ff31-197">기본값은 Default입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-197">The default value is Default.</span></span> <span data-ttu-id="9ff31-198">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-198">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-199">이 매개 변수 값에 대한 자세한 내용은 MSDN의 **System.Management.Automation.Runspaces.AuthenticationMechanism** 열거형 설명을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-199">For information about the values of this parameter, see the description of the **System.Management.Automation.Runspaces.AuthenticationMechanism** enumeration in MSDN.</span></span>

> [!WARNING]
> <span data-ttu-id="9ff31-200">사용자 자격 증명이 인증할 원격 컴퓨터로 전달되는 CredSSP(Credential Security Service Provider) 인증은 원격 네트워크 공유 액세스 등 두 개 이상의 리소스에서 인증이 필요한 명령에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-200">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="9ff31-201">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-201">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="9ff31-202">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-202">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

#### <a name="pscertificatethumbprint-string"></a><span data-ttu-id="9ff31-203">PSCertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="9ff31-203">PSCertificateThumbprint \<String\></span></span>

<span data-ttu-id="9ff31-204">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-204">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="9ff31-205">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-205">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="9ff31-206">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-206">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-207">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-207">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="9ff31-208">인증서 손 도장(Thumbprint)은 로컬 사용자 계정으로만 매핑될 수 있고 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-208">They can only be mapped to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="9ff31-209">인증서를 가져오려면 Windows PowerShell Cert: 드라이브의 [Get Item](xref:Microsoft.PowerShell.Management.Get-Item) 또는 [Get-childitem](xref:Microsoft.PowerShell.Management.Get-ChildItem) cmdlet을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-209">To get a certificate, use the [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) or [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem) cmdlets in the Windows PowerShell Cert: drive.</span></span>

#### <a name="pscomputername-string"></a><span data-ttu-id="9ff31-210">PSComputerName \<String[]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-210">PSComputerName \<String[]\></span></span>

<span data-ttu-id="9ff31-211">작업이 실행 되는 대상 컴퓨터를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-211">Specifies the target computers on which the activity run.</span></span> <span data-ttu-id="9ff31-212">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-212">The default is the local computer.</span></span> <span data-ttu-id="9ff31-213">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-213">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-214">하나 이상의 컴퓨터의 NETBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-214">Type the NETBIOS name, IP address, or fully-qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="9ff31-215">로컬 컴퓨터를 지정하려면 컴퓨터 이름, "localhost" 또는 점(.)을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-215">To specify the local computer, type the computer name, "localhost", or a dot (.).</span></span>

<span data-ttu-id="9ff31-216">PSComputerName 매개 변수 값에 로컬 컴퓨터를 포함 하려면 "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-216">To include the local computer in the value of the PSComputerName parameter, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="9ff31-217">명령에서이 매개 변수를 생략 하거나 값이 $null 또는 빈 문자열인 경우 워크플로 대상은 로컬 컴퓨터이 고 Windows PowerShell 원격을 사용 하 여 명령을 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-217">If this parameter is omitted from the command, or it value is $null or an empty string, the workflow target is the local computer and Windows PowerShell remoting is not used to run the command.</span></span>

<span data-ttu-id="9ff31-218">ComputerName 매개 변수 값에 IP 주소를 사용 하려면 명령에 PSCredential 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-218">To use an IP address in the value of the ComputerName parameter, the command must include the PSCredential parameter.</span></span> <span data-ttu-id="9ff31-219">또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-219">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="9ff31-220">TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)의 "신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9ff31-220">For instructions for adding a computer name to the TrustedHosts list, see "How to Add a Computer to the Trusted Host List" in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

#### <a name="psconfigurationname-string"></a><span data-ttu-id="9ff31-221">PSConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="9ff31-221">PSConfigurationName \<String\></span></span>

<span data-ttu-id="9ff31-222">대상 컴퓨터에서 세션을 만드는 데 사용 되는 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-222">Specifies the session configurations that are used to create sessions on the target computers.</span></span> <span data-ttu-id="9ff31-223">워크플로를 실행 하는 컴퓨터가 아니라 대상 컴퓨터에 세션 구성의 이름을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-223">Enter the name of a session configuration on the target computers (not on the computer that is running the workflow.</span></span> <span data-ttu-id="9ff31-224">기본값은 Microsoft. PowerShell입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-224">The default is Microsoft.PowerShell.</span></span> <span data-ttu-id="9ff31-225">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-225">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretrycount-uint"></a><span data-ttu-id="9ff31-226">PSConnectionRetryCount \<UInt\></span><span class="sxs-lookup"><span data-stu-id="9ff31-226">PSConnectionRetryCount \<UInt\></span></span>

<span data-ttu-id="9ff31-227">첫 번째 연결 시도가 실패 한 경우 각 대상 컴퓨터에 대 한 최대 연결 시도 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-227">Specifies the maximum number of attempts to connect to each target computer if the first connection attempt fails.</span></span> <span data-ttu-id="9ff31-228">1에서 4294967295 사이의 숫자 (Int32.maxvalue)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-228">Enter a number between 1 and 4,294,967,295 (UInt.MaxValue).</span></span> <span data-ttu-id="9ff31-229">기본값 영 (0)은 재시도 횟수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-229">The default value, zero (0), represents no retry attempts.</span></span>
<span data-ttu-id="9ff31-230">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-230">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionretryintervalsec-uint"></a><span data-ttu-id="9ff31-231">PSConnectionRetryIntervalSec \<UInt\></span><span class="sxs-lookup"><span data-stu-id="9ff31-231">PSConnectionRetryIntervalSec \<UInt\></span></span>

<span data-ttu-id="9ff31-232">연결 다시 시도 사이의 지연 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-232">Specifies the delay between connection retry attempts in seconds.</span></span> <span data-ttu-id="9ff31-233">기본값은 영(0)입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-233">The default value is zero (0).</span></span> <span data-ttu-id="9ff31-234">이 매개 변수는 PSConnectionRetryCount의 값이 1 이상인 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-234">This parameter is valid only when the value of PSConnectionRetryCount is at least 1.</span></span> <span data-ttu-id="9ff31-235">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-235">This activity common parameter is also a workflow common parameter.</span></span>

#### <a name="psconnectionuri-systemuri"></a><span data-ttu-id="9ff31-236">PSConnectionURI \<System.Uri\></span><span class="sxs-lookup"><span data-stu-id="9ff31-236">PSConnectionURI \<System.Uri\></span></span>

<span data-ttu-id="9ff31-237">대상 컴퓨터에서 작업에 대 한 연결 끝점을 정의 하는 URI (Uniform Resource Identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-237">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint for the activity on the target computer.</span></span> <span data-ttu-id="9ff31-238">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-238">The URI must be fully qualified.</span></span> <span data-ttu-id="9ff31-239">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-239">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-240">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-240">The format of this string is as follows:</span></span>

```
<Transport>://<ComputerName>:<Port>/<ApplicationName>
```

<span data-ttu-id="9ff31-241">기본값은 `http://localhost:5985/WSMAN`입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-241">The default value is `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="9ff31-242">PSConnectionURI를 지정 하지 않으면 PSUseSSL, PSComputerName, PSPort 및 PSApplicationName 매개 변수를 사용 하 여 PSConnectionURI 값을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-242">If you do not specify a PSConnectionURI, you can use the PSUseSSL, PSComputerName, PSPort, and PSApplicationName parameters to specify the PSConnectionURI values.</span></span>

<span data-ttu-id="9ff31-243">URI의 전송 세그먼트에 유효한 값은 HTTP 및 HTTPS입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-243">Valid values for the Transport segment of the URI are HTTP and HTTPS.</span></span> <span data-ttu-id="9ff31-244">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-244">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="9ff31-245">Windows PowerShell 원격을 위한 기본 포트를 사용하려면 HTTP의 경우 포트 5985 또는 HTTPS의 경우 5986을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-245">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

#### <a name="pscredential-pscredential"></a><span data-ttu-id="9ff31-246">유형이 \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="9ff31-246">PSCredential \<PSCredential\></span></span>

<span data-ttu-id="9ff31-247">대상 컴퓨터에서 작업을 실행할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-247">Specifies a user account that has permission to run the activity on the target computer.</span></span> <span data-ttu-id="9ff31-248">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-248">The default is the current user.</span></span> <span data-ttu-id="9ff31-249">이 매개 변수는 PSComputerName 매개 변수가 명령에 포함 된 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-249">This parameter is valid only when the PSComputerName parameter is included in the command.</span></span> <span data-ttu-id="9ff31-250">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-250">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-251">사용자 이름 (예: "User01" 또는 "Domain01\User01")을 입력 하거나 PSCredential 개체 (예: Get-Credential cmdlet이 반환 하는 변수)를 포함 하는 변수를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-251">Type a user name, such as "User01" or "Domain01\User01", or enter a variable that contains a PSCredential object, such as one that the Get-Credential cmdlet returns.</span></span> <span data-ttu-id="9ff31-252">사용자 이름만 입력하면 암호를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-252">If you enter only a user name, you will be prompted for a password.</span></span>

#### <a name="psdebug-psdatacollectiondebugrecord"></a><span data-ttu-id="9ff31-253">Set-psdebug \<PSDataCollection[DebugRecord]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-253">PSDebug \<PSDataCollection[DebugRecord]\></span></span>

<span data-ttu-id="9ff31-254">디버그 메시지를 콘솔에 기록 하거나 워크플로 작업의 Debug 속성 값에 쓰지 않고 활동의 디버그 메시지를 지정 된 디버그 레코드 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-254">Adds debug messages from the activity to the specified debug record collection, instead of writing the debug messages to the console or to the value of the Debug property of the workflow job.</span></span> <span data-ttu-id="9ff31-255">여러 활동의 디버그 메시지를 동일한 디버그 레코드 컬렉션 개체에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-255">You can add debug messages from multiple activities to the same debug record collection object.</span></span>

<span data-ttu-id="9ff31-256">이 활동 일반 매개 변수를 사용 하려면 New-Object cmdlet을 사용 하 여 DebugRecord 형식의 P s d 개체를 만들고 개체를 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-256">To use this activity common parameter, use the New-Object cmdlet to create a PSDataCollection object with a type of DebugRecord and save the object in a variable.</span></span> <span data-ttu-id="9ff31-257">그런 다음, 다음 예제와 같이 변수를 하나 이상의 활동에 대 한 PSDebug 매개 변수 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-257">Then, use the variable as the value of the PSDebug parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
    $debugCollection = New-Object -Type `
    System.Management.Automation.PSDataCollection[System.Management.Automation.DebugRecord]
    InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSDebug $debugCollection -Debug $True
    if ($debugCollection -like "Missing") { ...}
}
```

#### <a name="psdisableserialization-boolean"></a><span data-ttu-id="9ff31-258">PSDisableSerialization \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-258">PSDisableSerialization \<Boolean\></span></span>

<span data-ttu-id="9ff31-259">활동이 워크플로에 "라이브"(직렬화하지 않음) 개체를 반환하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-259">Directs the activity to return "live" (not serialized) objects to the workflow.</span></span>
<span data-ttu-id="9ff31-260">결과 개체는 방법 및 속성이 있지만 검사점을 사용하는 경우 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-260">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>

#### <a name="psdisableserializationpreference-boolean"></a><span data-ttu-id="9ff31-261">PSDisableSerializationPreference \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-261">PSDisableSerializationPreference \<Boolean\></span></span>

<span data-ttu-id="9ff31-262">활동 뿐만 아니라 전체 워크플로에 PSDisableSerialization 매개 변수에 해당 하는 것을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-262">Applies the equivalent of the PSDisableSerialization parameter to the entire workflow, not just the activity.</span></span> <span data-ttu-id="9ff31-263">개체를 직렬화 하지 않는 워크플로는 다시 시작 하거나 지속할 수 없으므로 일반적으로이 매개 변수를 추가 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-263">Adding this parameter is generally not recommended, because a workflow that doesn't serialize its objects cannot be resumed or persisted.</span></span>

<span data-ttu-id="9ff31-264">유효한 값은</span><span class="sxs-lookup"><span data-stu-id="9ff31-264">Valid values:</span></span>

- <span data-ttu-id="9ff31-265">기본 생략 하는 경우 PSDisableSerialization 매개 변수를 작업에 추가 하지 않은 경우에도 개체가 serialize 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-265">(Default) If omitted, and you have also not added the PSDisableSerialization parameter to an activity, objects are serialized.</span></span>

- <span data-ttu-id="9ff31-266">`$True`.</span><span class="sxs-lookup"><span data-stu-id="9ff31-266">`$True`.</span></span> <span data-ttu-id="9ff31-267">워크플로 내의 모든 활동이 "라이브" (직렬화 되지 않음) 개체를 반환 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-267">Directs all activities within a workflow to return "live" (not serialized) objects.</span></span> <span data-ttu-id="9ff31-268">결과 개체는 방법 및 속성이 있지만 검사점을 사용하는 경우 저장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-268">The resulting objects have methods, as well as properties, but they cannot be saved when a checkpoint is taken.</span></span>
- <span data-ttu-id="9ff31-269">`$False`.</span><span class="sxs-lookup"><span data-stu-id="9ff31-269">`$False`.</span></span> <span data-ttu-id="9ff31-270">워크플로 개체는 serialize 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-270">Workflow objects are serialized.</span></span>

#### <a name="pserror-psdatacollectionerrorrecord"></a><span data-ttu-id="9ff31-271">PSError \<PSDataCollection[ErrorRecord]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-271">PSError \<PSDataCollection[ErrorRecord]\></span></span>

<span data-ttu-id="9ff31-272">워크플로 작업의 오류 속성 값 또는 콘솔에 오류 메시지를 쓰지 않고 활동의 오류 메시지를 지정 된 오류 레코드 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-272">Adds error messages from the activity to the specified error record collection, instead of writing the error messages to the console or to the value of the Error property of the workflow job.</span></span> <span data-ttu-id="9ff31-273">여러 활동의 오류 메시지를 동일한 오류 레코드 컬렉션 개체에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-273">You can add error messages from multiple activities to the same error record collection object.</span></span>

<span data-ttu-id="9ff31-274">이 활동 일반 매개 변수를 사용 하려면 cmdlet을 사용 하 여 `New-Object` ErrorRecord 유형의 p s d 개체를 만들고 해당 개체를 변수에 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-274">To use this activity common parameter, use the `New-Object` cmdlet to create a PSDataCollection object with a type of ErrorRecord and save the object in a variable.</span></span> <span data-ttu-id="9ff31-275">그런 다음, 다음 예제와 같이 변수를 하나 이상의 활동에 대 한 PSError 매개 변수 값으로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-275">Then, use the variable as the value of the PSError parameter of one or more activities, as shown in the following example.</span></span>

```powershell
Workflow Test-Workflow
{
   $typeName = "System.Management.Automation.PSDataCollection"
   $typeName += '[System.Management.Automation.ErrorRecord]'
   $ec = New-Object $typeName
   InlineScript {\Server01\Share01\Get-AssetData.ps1} -PSError $ec
   InlineScript {\Server01\Share01\Set-AssetData.ps1} -PSError $ec
   if ($ec.Count -gt 2)
   {
      # Do Some Work.
   }
}
```

#### <a name="pspersist-boolean"></a><span data-ttu-id="9ff31-276">PSPersist \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-276">PSPersist \<Boolean\></span></span>

<span data-ttu-id="9ff31-277">작업 후 검사점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-277">Takes a checkpoint after the activity.</span></span> <span data-ttu-id="9ff31-278">이 검사점은 워크플로에 지정 된 검사점에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-278">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span> <span data-ttu-id="9ff31-279">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-279">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-280">"검사점" 또는 "지 속성 지점"은 워크플로 상태와 워크플로를 실행 하는 동안 캡처되고 디스크의 지 속성 저장소에 저장 되는 데이터의 스냅숏입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-280">A "checkpoint" or "persistence point" is a snapshot of the workflow state and data that is captured while the workflow runs and is saved to a persistence store on disk.</span></span> <span data-ttu-id="9ff31-281">Windows PowerShell 워크플로는 저장 된 데이터를 사용 하 여 워크플로를 다시 시작 하지 않고 마지막 지 속성 지점에서 일시 중단 또는 중단 된 워크플로를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-281">Windows PowerShell Workflow uses the saved data to resume a suspended or interrupted workflow from the last persistence point, rather than to restart the workflow.</span></span>

<span data-ttu-id="9ff31-282">유효한 값은</span><span class="sxs-lookup"><span data-stu-id="9ff31-282">Valid values:</span></span>

- <span data-ttu-id="9ff31-283">기본 이 매개 변수를 생략 하면 검사점이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-283">(Default) If you omit this parameter, no checkpoints are added.</span></span> <span data-ttu-id="9ff31-284">검사점은 워크플로의 설정에 따라 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-284">Checkpoints are taken based on the settings for the workflow.</span></span>

- <span data-ttu-id="9ff31-285">`$True`.</span><span class="sxs-lookup"><span data-stu-id="9ff31-285">`$True`.</span></span> <span data-ttu-id="9ff31-286">활동이 완료된 후 검사점을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-286">Takes a checkpoint after the activity completes.</span></span>
  <span data-ttu-id="9ff31-287">이 검사점은 워크플로에 지정 된 검사점에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-287">This checkpoint is in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="9ff31-288">`$False`.</span><span class="sxs-lookup"><span data-stu-id="9ff31-288">`$False`.</span></span> <span data-ttu-id="9ff31-289">검사점이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-289">No checkpoints are added.</span></span> <span data-ttu-id="9ff31-290">검사점은 워크플로에 지정 된 경우에만 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-290">Checkpoints are taken only when specified in the workflow.</span></span>

#### <a name="psport-int32"></a><span data-ttu-id="9ff31-291">PSPort \<Int32\></span><span class="sxs-lookup"><span data-stu-id="9ff31-291">PSPort \<Int32\></span></span>

<span data-ttu-id="9ff31-292">대상 컴퓨터의 네트워크 포트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-292">Specifies the network port on the target computers.</span></span> <span data-ttu-id="9ff31-293">기본 포트는 5985(HTTP용 WinRM 포트) 및 5986(HTTPS용 WinRM 포트)입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-293">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span> <span data-ttu-id="9ff31-294">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-294">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-295">반드시 필요한 경우가 아니면 PSPort 매개 변수를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-295">Do not use the PSPort parameter unless you must.</span></span> <span data-ttu-id="9ff31-296">명령에 설정 된 포트는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-296">The port set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="9ff31-297">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-297">An alternate port setting might prevent the command from running on all computers.</span></span> <span data-ttu-id="9ff31-298">대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-298">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>

#### <a name="psprogress-psdatacollectionprogressrecord"></a><span data-ttu-id="9ff31-299">PSProgress \<PSDataCollection[ProgressRecord]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-299">PSProgress \<PSDataCollection[ProgressRecord]\></span></span>

<span data-ttu-id="9ff31-300">워크플로 작업의 progress 속성 값 또는 콘솔에 진행률 메시지를 쓰지 않고 활동의 진행률 메시지를 지정 된 진행률 레코드 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-300">Adds progress messages from the activity to the specified progress record collection, instead of writing the progress messages to the console or to the value of the Progress property of the workflow job.</span></span> <span data-ttu-id="9ff31-301">여러 활동의 진행률 메시지를 동일한 진행률 레코드 컬렉션 개체에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-301">You can add progress messages from multiple activities to the same progress record collection object.</span></span>

#### <a name="psprogressmessage-string"></a><span data-ttu-id="9ff31-302">PSProgressMessage \<String\></span><span class="sxs-lookup"><span data-stu-id="9ff31-302">PSProgressMessage \<String\></span></span>

<span data-ttu-id="9ff31-303">활동에 대한 간단한 설명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-303">Specifies a friendly description of the activity.</span></span> <span data-ttu-id="9ff31-304">PSProgressMessage 값은 워크플로가 실행 되는 동안 진행률 표시줄에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-304">The PSProgressMessage value appears in the progress bar while the workflow runs.</span></span> <span data-ttu-id="9ff31-305">DisplayName이 명령에도 포함 된 경우 진행률 표시줄 콘텐츠가: 형식으로 표시 됩니다 \<DisplayName\> \<PSProgressMessage\> .</span><span class="sxs-lookup"><span data-stu-id="9ff31-305">When the DisplayName is also included in the command, the progress bar content appears in \<DisplayName\>:\<PSProgressMessage\> format.</span></span>

<span data-ttu-id="9ff31-306">이 매개 변수는 ForEach-Parallel 스크립트 블록에서 활동을 식별 하는 데 특히 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-306">This parameter is particularly useful for identifying activities in a ForEach -Parallel script block.</span></span> <span data-ttu-id="9ff31-307">이 메시지가 없으면 모든 병렬 분기의 활동이 같은 이름으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-307">Without this message, activities in all parallel branches are identified by the same name.</span></span>

#### <a name="psremotingbehavior-remotingbehavior"></a><span data-ttu-id="9ff31-308">Psremo의 동작 \<RemotingBehavior\></span><span class="sxs-lookup"><span data-stu-id="9ff31-308">PSRemotingBehavior \<RemotingBehavior\></span></span>

<span data-ttu-id="9ff31-309">활동이 대상 컴퓨터에서 실행될 때 원격이 어떻게 관리되는지 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-309">Specifies how remoting is managed when the activity is run on target computers.</span></span>
<span data-ttu-id="9ff31-310">PowerShell이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-310">PowerShell is the default.</span></span>

<span data-ttu-id="9ff31-311">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-311">Valid values are:</span></span>

- <span data-ttu-id="9ff31-312">없음: 작업이 원격 컴퓨터에서 실행 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-312">None: The activity is not run on remote computers.</span></span>

- <span data-ttu-id="9ff31-313">PowerShell: 대상 컴퓨터에서 작업을 실행 하는 데 Windows PowerShell 원격 기능을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-313">PowerShell: Windows PowerShell remoting is used to run the activity on target computers.</span></span>

- <span data-ttu-id="9ff31-314">사용자 지정: 활동은 고유한 유형의 원격을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-314">Custom: The activity supports its own type of remoting.</span></span> <span data-ttu-id="9ff31-315">이 값은 활동으로 구현 되는 cmdlet이 Remorerecommand 특성의 값을 SupportedByCommand로 설정 하 고 명령에 ComputerName 매개 변수를 포함 하는 경우에 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-315">This value is valid when the cmdlet that is being implemented as an activity sets the value of the RemotingCapability attribute to SupportedByCommand and the command includes the ComputerName parameter.</span></span>

#### <a name="psrequiredmodules-string"></a><span data-ttu-id="9ff31-316">PSRequiredModules \<String[]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-316">PSRequiredModules \<String[]\></span></span>

<span data-ttu-id="9ff31-317">명령을 실행하기 전에 지정된 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-317">Imports the specified modules before running the command.</span></span> <span data-ttu-id="9ff31-318">모듈 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-318">Enter the module names.</span></span> <span data-ttu-id="9ff31-319">모듈은 대상 컴퓨터에 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-319">The modules must be installed on the target computer.</span></span>

<span data-ttu-id="9ff31-320">PSModulePath 환경 변수에 지정 된 경로에 설치 된 모듈은 모듈의 명령을 처음 사용할 때 자동으로 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-320">Modules that are installed in a path specified in the PSModulePath environment variable are automatically imported on first use of any command in the module.</span></span>
<span data-ttu-id="9ff31-321">PSModulePath 위치에 없는 모듈을 가져오려면이 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-321">Use this parameter to import modules that are not in a PSModulePath location.</span></span>

<span data-ttu-id="9ff31-322">워크플로의 각 활동은 자체 세션에서 실행되기 때문에 Import-Module 명령은 해당 활동이 실행되는 세션으로만 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-322">Because each activity in a workflow runs in its own session, an Import-Module command imports a module only into the session in which it runs.</span></span> <span data-ttu-id="9ff31-323">다른 활동이 실행되는 세션으로 모듈을 가져오지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-323">It does not import the module into sessions in which other activities run.</span></span>

#### <a name="pssessionoption-pssessionoption"></a><span data-ttu-id="9ff31-324">PSSessionOption \<PSSessionOption\></span><span class="sxs-lookup"><span data-stu-id="9ff31-324">PSSessionOption \<PSSessionOption\></span></span>

<span data-ttu-id="9ff31-325">대상 컴퓨터에 대 한 세션의 고급 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-325">Sets advanced options for the sessions to the target computers.</span></span> <span data-ttu-id="9ff31-326">New-PSSessionOption cmdlet을 사용 하 여 만든 것과 같은 PSSessionOption 개체를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-326">Enter a PSSessionOption object, such as one that you create by using the New-PSSessionOption cmdlet.</span></span> <span data-ttu-id="9ff31-327">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-327">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-328">세션 옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-328">The default values for the session options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="9ff31-329">그렇지 않으면 세션 구성에 지정 된 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-329">Otherwise, the session uses the values specified in the session configuration.</span></span>

<span data-ttu-id="9ff31-330">기본값을 비롯 한 세션 옵션에 대 한 자세한 내용은 New-PSSessionOption cmdlet [새-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-330">For a description of the session options, including the default values, see the help topic for the New-PSSessionOption cmdlet [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

<span data-ttu-id="9ff31-331">$PSSessionOption 기본 설정 변수에 대 한 자세한 내용은 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9ff31-331">For more information about the $PSSessionOption preference variable, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

#### <a name="psusessl-boolean"></a><span data-ttu-id="9ff31-332">PSUseSSL \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-332">PSUseSSL \<Boolean\></span></span>

<span data-ttu-id="9ff31-333">$True 값은 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 대상 컴퓨터에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-333">A value of $True uses the Secure Sockets Layer (SSL) protocol to establish a connection to the target computer.</span></span> <span data-ttu-id="9ff31-334">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-334">By default, SSL is not used.</span></span> <span data-ttu-id="9ff31-335">$False 값은 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-335">A value of $False has no effect.</span></span> <span data-ttu-id="9ff31-336">이 활동 일반 매개 변수는 워크플로 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-336">This activity common parameter is also a workflow common parameter.</span></span>

<span data-ttu-id="9ff31-337">WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-337">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="9ff31-338">UseSSL은 HTTP 대신 HTTPS를 통해 데이터를 보내는 추가적인 보호 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-338">UseSSL is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span> <span data-ttu-id="9ff31-339">이 매개 변수를 사용하지만 명령에 사용되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-339">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

#### <a name="psverbose-psdatacollectionverboserecord"></a><span data-ttu-id="9ff31-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-340">PSVerbose \<PSDataCollection[VerboseRecord]\></span></span>

<span data-ttu-id="9ff31-341">워크플로 작업의 verbose 속성 값 또는 콘솔에 자세한 정보 표시 메시지를 쓰지 않고 활동의 자세한 정보 표시 메시지를 지정 된 자세한 정보 표시 레코드 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-341">Adds verbose messages from the activity to the specified verbose record collection, instead of writing the verbose messages to the console or to the value of the Verbose property of the workflow job.</span></span> <span data-ttu-id="9ff31-342">여러 활동의 자세한 정보 표시 메시지를 동일한 자세한 정보 표시 레코드 컬렉션 개체에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-342">You can add verbose messages from multiple activities to the same verbose record collection object.</span></span>

#### <a name="pswarning-psdatacollectionwarningrecord"></a><span data-ttu-id="9ff31-343">PSWarning \<PSDataCollection[WarningRecord]\></span><span class="sxs-lookup"><span data-stu-id="9ff31-343">PSWarning \<PSDataCollection[WarningRecord]\></span></span>

<span data-ttu-id="9ff31-344">워크플로 작업의 경고 속성 값 또는 콘솔에 경고 메시지를 쓰지 않고 활동의 경고 메시지를 지정 된 경고 레코드 컬렉션에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-344">Adds warning messages from the activity to the specified warning record collection, instead of writing the warning messages to the console or to the value of the Warning property of the workflow job.</span></span> <span data-ttu-id="9ff31-345">여러 활동의 경고 메시지를 동일한 경고 레코드 컬렉션 개체에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-345">You can add warning messages from multiple activities to the same warning record collection object.</span></span>

#### <a name="result"></a><span data-ttu-id="9ff31-346">결과</span><span class="sxs-lookup"><span data-stu-id="9ff31-346">Result</span></span>

<span data-ttu-id="9ff31-347">이 매개 변수는 XAML 워크플로에서만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-347">This parameter is valid only in XAML workflows.</span></span>

#### <a name="usedefaultinput-boolean"></a><span data-ttu-id="9ff31-348">UseDefaultInput \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="9ff31-348">UseDefaultInput \<Boolean\></span></span>

<span data-ttu-id="9ff31-349">모든 워크플로 입력을 활동에 대한 입력 값으로 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-349">Accepts all workflow input as input to the activity by value.</span></span>

<span data-ttu-id="9ff31-350">예를 들어 다음 샘플 워크플로의 Get-Process 활동은 UseDefaultInput 활동 일반 매개 변수를 사용하여 워크플로에 전달된 입력을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-350">For example, the Get-Process activity in the following sample workflow uses the UseDefaultInput activity common parameter to get input that is passed to the workflow.</span></span> <span data-ttu-id="9ff31-351">입력을 사용하여 워크플로를 실행하는 경우 해당 입력이 활동에 의해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-351">When you run the workflow with input, that input is used by the activity.</span></span>

```powershell
workflow Test-Workflow
{
    Get-Service -UseDefaultInput $True
}

PS C:> Test-Workflow -InputObject WinRm
```

```output
Status   Name        DisplayName                            PSComputerName
------   ----        -----------                            --------------
Running  winrm       Windows Remote Management (WS-Manag... localhost
```

#### <a name="verbose-switchparameter"></a><span data-ttu-id="9ff31-352">구문 \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="9ff31-352">Verbose \<SwitchParameter\></span></span>

<span data-ttu-id="9ff31-353">명령에 의해 수행 된 작업에 대 한 자세한 정보를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-353">Displays detailed information about the operation performed by the command.</span></span>
<span data-ttu-id="9ff31-354">이 정보는 추적 또는 트랜잭션 로그의 정보와 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-354">This information resembles the information in a trace or in a transaction log.</span></span>
<span data-ttu-id="9ff31-355">Verbose 매개 변수는 현재 명령에 대 한 $VerbosePreference 변수의 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-355">The Verbose parameter overrides the value of the $VerbosePreference variable for the current command.</span></span> <span data-ttu-id="9ff31-356">이 매개 변수는 명령이 자세한 정보 메시지를 생성 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-356">This parameter works only when the command generates a verbose message.</span></span> <span data-ttu-id="9ff31-357">이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-357">This parameter is also a Windows PowerShell common parameter.</span></span>

#### <a name="warningaction-actionpreference"></a><span data-ttu-id="9ff31-358">WarningAction \<ActionPreference\></span><span class="sxs-lookup"><span data-stu-id="9ff31-358">WarningAction \<ActionPreference\></span></span>

<span data-ttu-id="9ff31-359">활동에서 경고에 응답 하는 방법을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-359">Determines how the activity responds to a warning.</span></span> <span data-ttu-id="9ff31-360">"Continue"가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-360">"Continue" is the default value.</span></span> <span data-ttu-id="9ff31-361">WarningAction 매개 변수는 현재 명령에 대 한 $WarningPreference 변수의 값을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-361">The WarningAction parameter overrides the value of the $WarningPreference variable for the current command.</span></span> <span data-ttu-id="9ff31-362">이 매개 변수는 명령에서 경고 메시지를 생성 하는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-362">This parameter works only when the command generates a warning message.</span></span> <span data-ttu-id="9ff31-363">이 매개 변수는 Windows PowerShell 일반 매개 변수 이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-363">This parameter is also a Windows PowerShell common parameter.</span></span>

<span data-ttu-id="9ff31-364">유효한 값은</span><span class="sxs-lookup"><span data-stu-id="9ff31-364">Valid Values:</span></span>

- <span data-ttu-id="9ff31-365">SilentlyContinue.</span><span class="sxs-lookup"><span data-stu-id="9ff31-365">SilentlyContinue.</span></span> <span data-ttu-id="9ff31-366">경고 메시지를 표시 하지 않고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-366">Suppresses the warning message and continues executing the command.</span></span>

- <span data-ttu-id="9ff31-367">하기.</span><span class="sxs-lookup"><span data-stu-id="9ff31-367">Continue.</span></span> <span data-ttu-id="9ff31-368">경고 메시지를 표시 하 고 명령을 계속 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-368">Displays the warning message and continues executing the command.</span></span>
  <span data-ttu-id="9ff31-369">"Continue"가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-369">"Continue" is the default value.</span></span>

- <span data-ttu-id="9ff31-370">Inquire.</span><span class="sxs-lookup"><span data-stu-id="9ff31-370">Inquire.</span></span> <span data-ttu-id="9ff31-371">경고 메시지를 표시 하 고 실행을 계속 하기 전에 확인 메시지를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-371">Displays the warning message and prompts you for confirmation before continuing execution.</span></span> <span data-ttu-id="9ff31-372">이 값은 거의 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-372">This value is rarely used.</span></span>

- <span data-ttu-id="9ff31-373">중지</span><span class="sxs-lookup"><span data-stu-id="9ff31-373">Stop.</span></span> <span data-ttu-id="9ff31-374">경고 메시지를 표시 하 고 명령 실행을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-374">Displays the warning message and stops executing the command.</span></span>

> [!NOTE]
> <span data-ttu-id="9ff31-375">WarningAction 매개 변수는 스크립트 또는 함수를 실행 하는 명령에 매개 변수가 사용 되는 경우 $WarningAction 기본 설정 변수의 값을 재정의 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-375">The WarningAction parameter does not override the value of the $WarningAction preference variable when the parameter is used in a command to run a script or function.</span></span>

### <a name="examples"></a><span data-ttu-id="9ff31-376">예제</span><span class="sxs-lookup"><span data-stu-id="9ff31-376">EXAMPLES</span></span>

<span data-ttu-id="9ff31-377">활동 일반 매개 변수는 매우 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-377">The activity common parameters are extremely useful.</span></span> <span data-ttu-id="9ff31-378">예를 들어, PSComputerName 매개 변수를 사용 하 여 대상 컴퓨터의 하위 집합에 대해서만 특정 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-378">For example, you can use the PSComputerName parameter to run particular activities on only a subset of the target computers.</span></span>

<span data-ttu-id="9ff31-379">또는 PSConnectionRetryCount 및 PSConnectionRetryIntervalSec 매개 변수를 사용 하 여 특정 작업에 대 한 재시도 값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-379">Or, you might use the PSConnectionRetryCount and PSConnectionRetryIntervalSec parameters to adjust the retry values for particular activities.</span></span>

<span data-ttu-id="9ff31-380">다음 예제에서는 PSComputerName 활동 일반 매개 변수를 사용 하 여 특정 도메인에 있는 컴퓨터 에서만 Get-EventLog 작업을 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ff31-380">The following example shows how to use the PSComputerName activity common parameters to run a Get-EventLog activity only on computers it a particular domain.</span></span>

```powershell
Workflow Test-Workflow
{
    $UserDomain = Get-Content -Path '.\UserComputers.txt'
    $Log = (Get-EventLog -LogName "Windows PowerShell" `
      -PSComputerName $UserDomain)

    if ($Log)
    {
        # Do Work Here.
    }
}
```

<!--
# KEYWORDS
[about_Activity_Common_Parameters](about_Activity_Common_Parameters.md)
[about_Activity_Parameters](about_Activity_Parameters.md)
[about_ActivityParameters]()about_ActivityParameters.md) -->

## <a name="see-also"></a><span data-ttu-id="9ff31-381">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9ff31-381">SEE ALSO</span></span>

<span data-ttu-id="9ff31-382">[about_Workflows](about_workflows.md) 
 [about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span><span class="sxs-lookup"><span data-stu-id="9ff31-382">[about_Workflows](about_workflows.md)
[about_WorkflowCommonParameters](about_WorkflowCommonParameters.md)</span></span>
