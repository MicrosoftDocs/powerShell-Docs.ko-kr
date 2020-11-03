---
description: 이 항목에서는 모든 Windows PowerShell 워크플로 명령에 유효한 매개 변수에 대해 설명 합니다. Windows PowerShell 엔진은 워크플로에 추가 하므로 워크플로를 통해 이러한 매개 변수를 사용할 수 있으며 작성자가 만든 워크플로에서 자동으로 사용 하도록 설정 됩니다.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psworkflow/about/about_workflowcommonparameters?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WorkflowCommonParameters
ms.openlocfilehash: 386200475c1dab9735921edd60abbde20ee354c4
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "93221857"
---
# <a name="about-workflowcommonparameters"></a><span data-ttu-id="97aa5-105">WorkflowCommonParameters 정보</span><span class="sxs-lookup"><span data-stu-id="97aa5-105">About WorkflowCommonParameters</span></span>

## <a name="short-description"></a><span data-ttu-id="97aa5-106">간단한 설명</span><span class="sxs-lookup"><span data-stu-id="97aa5-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="97aa5-107">이 항목에서는 모든 Windows PowerShell 워크플로 명령에 유효한 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-107">This topic describes the parameters that are valid on all Windows PowerShell workflow commands.</span></span> <span data-ttu-id="97aa5-108">Windows PowerShell 엔진은 워크플로에 추가 하므로 워크플로를 통해 이러한 매개 변수를 사용할 수 있으며 작성자가 만든 워크플로에서 자동으로 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-108">Because the Windows PowerShell engine adds them to workflows, you can use these parameters on any workflow and they are automatically enabled on the workflows that you author.</span></span>

## <a name="long-description"></a><span data-ttu-id="97aa5-109">자세한 설명</span><span class="sxs-lookup"><span data-stu-id="97aa5-109">LONG DESCRIPTION</span></span>

<span data-ttu-id="97aa5-110">Windows PowerShell 워크플로 일반 매개 변수는 모든 Windows PowerShell 워크플로 및 작업에 사용할 수 있는 cmdlet 매개 변수 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-110">Windows PowerShell Workflow common parameters are a set of cmdlet parameters that you can use with all Windows PowerShell workflows and activities.</span></span> <span data-ttu-id="97aa5-111">이러한 워크플로는 워크플로 작성자가 아닌 Windows PowerShell 워크플로 엔진에 의해 추가 되며 워크플로 및 활동에서 자동으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-111">They are added by the Windows PowerShell Workflow engine, not by the workflow author, and they are automatically available on workflows and activities.</span></span> <span data-ttu-id="97aa5-112">그러나 세 수준 깊이 중첩 된 워크플로는 워크플로 일반 매개 변수를 포함 하 여 일반 매개 변수를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-112">However, workflows that are nested three levels deep do not support any common parameters, including workflow common parameters.</span></span>

<span data-ttu-id="97aa5-113">모든 워크플로 매개 변수는 선택 사항이 며 위치는 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-113">All workflow parameters are optional and named (not positional).</span></span> <span data-ttu-id="97aa5-114">파이프라인에서 입력을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-114">They do not take input from the pipeline.</span></span>

<span data-ttu-id="97aa5-115">대부분의 워크플로 일반 매개 변수에는 PS 접두사 (예: 및)가 있습니다 `PSComputerName` `PSCredential` .</span><span class="sxs-lookup"><span data-stu-id="97aa5-115">Most of the workflow common parameters have a PS prefix, such as `PSComputerName` and `PSCredential`.</span></span> <span data-ttu-id="97aa5-116">PS 접두사가 있는 매개 변수는 대상 컴퓨터에 대 한 연결 및 실행 환경을 구성 합니다 ("원격 노드" 라고도 함).</span><span class="sxs-lookup"><span data-stu-id="97aa5-116">The PS-prefixed parameters configure the connection and the execution environment for the target computers, also known as "remote nodes."</span></span>

<span data-ttu-id="97aa5-117">및와 같은 대부분의 워크플로 일반 매개 변수에 `PSAllowRedirection` 는 `AsJob` Windows PowerShell 원격 작업 및 백그라운드 작업에서 사용 되는 매개 변수와 비슷한 이름이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-117">Many of the workflow common parameters, such as `PSAllowRedirection` and `AsJob`, have names that are similar to parameters used in Windows PowerShell remoting and background jobs.</span></span> <span data-ttu-id="97aa5-118">이러한 매개 변수는 비슷한 이름의 remoting 및 작업 매개 변수와 동일한 방식으로 작동 하므로 원격 작업에서 개발한 정보를 사용 하 여 워크플로를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-118">These parameters work in the same way as the similarly-named remoting and job parameters, so you can use the knowledge that you developed in remoting and jobs to manage workflows.</span></span>

<span data-ttu-id="97aa5-119">워크플로는 Windows PowerShell 3.0에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-119">Workflows are introduced in Windows PowerShell 3.0.</span></span>

### <a name="parameter-descriptions"></a><span data-ttu-id="97aa5-120">매개 변수 설명</span><span class="sxs-lookup"><span data-stu-id="97aa5-120">PARAMETER DESCRIPTIONS</span></span>

<span data-ttu-id="97aa5-121">이 섹션에서는 워크플로 일반 매개 변수에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-121">This section describes the workflow common parameters.</span></span>

#### <a name="-asjob-switchparameter"></a><span data-ttu-id="97aa5-122">-AsJob \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="97aa5-122">-AsJob \<SwitchParameter\></span></span>

<span data-ttu-id="97aa5-123">워크플로 작업으로 워크플로를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-123">Runs the workflow as a workflow job.</span></span> <span data-ttu-id="97aa5-124">워크플로 명령은 부모 작업을 나타내는 개체를 즉시 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-124">The workflow command immediately returns an object that represents a parent job.</span></span> <span data-ttu-id="97aa5-125">부모 작업에는 각 대상 컴퓨터에서 실행 되는 자식 작업이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-125">The parent job contains the child jobs that are running on each of the target computers.</span></span> <span data-ttu-id="97aa5-126">작업을 관리하려면 Job cmdlet을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-126">To manage the job, use the Job cmdlets.</span></span> <span data-ttu-id="97aa5-127">작업 결과를 가져오려면 [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-127">To get the job results, use [Receive-Job](xref:Microsoft.PowerShell.Core.Receive-Job).</span></span>

#### <a name="-jobname-string"></a><span data-ttu-id="97aa5-128">-JobName \<String\></span><span class="sxs-lookup"><span data-stu-id="97aa5-128">-JobName \<String\></span></span>

<span data-ttu-id="97aa5-129">워크플로 작업에 대 한 친숙 한 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-129">Specifies a friendly name for the workflow job.</span></span> <span data-ttu-id="97aa5-130">기본적으로 작업 이름은 "작업\<n\>"이며, \<n\>은 서수 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-130">By default, jobs are named "Job\<n\>", where \<n\> is an ordinal number.</span></span>

<span data-ttu-id="97aa5-131">워크플로 명령에 JobName 매개 변수를 사용 하는 경우 `AsJob` 명령에 매개 변수를 포함 하지 않더라도 워크플로는 작업으로 실행 되 고 워크플로 명령은 작업 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-131">If you use the JobName parameter in a workflow command, the workflow is run as a job and the workflow command returns a job object, even if you do not include the `AsJob` parameter in the command.</span></span>

<span data-ttu-id="97aa5-132">Windows PowerShell 백그라운드 작업에 대한 자세한 내용은 [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="97aa5-132">For more information about Windows PowerShell background jobs, see [about_Jobs](../../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

#### <a name="-psallowredirection-switchparameter"></a><span data-ttu-id="97aa5-133">-PSAllowRedirection \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="97aa5-133">-PSAllowRedirection \<SwitchParameter\></span></span>

<span data-ttu-id="97aa5-134">대상 컴퓨터에 대 한 연결 리디렉션을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-134">Allows redirection of the connection to the target computers.</span></span>

<span data-ttu-id="97aa5-135">매개 변수를 사용 하는 경우 `PSConnectionURI` 원격 대상이 다른 URI로 리디렉션하는 명령을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-135">When you use the `PSConnectionURI` parameter, the remote destination can return an instruction to redirect to a different URI.</span></span> <span data-ttu-id="97aa5-136">기본적으로 Windows PowerShell은 연결을 리디렉션하지 않지만 매개 변수를 사용 하 여 `PSAllowRedirection` 대상 컴퓨터에 대 한 연결 리디렉션을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-136">By default, Windows PowerShell does not redirect connections, but you can use the `PSAllowRedirection` parameter to allow redirection of the connection to the target computer.</span></span>

<span data-ttu-id="97aa5-137">`MaximumConnectionRedirectionCount` `$PSSessionOption` 기본 설정 변수의 속성을 설정 하거나 `MaximumConnectionRedirectionCount` 값의 속성을 설정 하 여 연결이 리디렉션되는 횟수를 제한할 수도 있습니다 `PSSessionOption parameter` .</span><span class="sxs-lookup"><span data-stu-id="97aa5-137">You can also limit the number of times that the connection is redirected by setting the `MaximumConnectionRedirectionCount` property of the `$PSSessionOption` preference variable, or the `MaximumConnectionRedirectionCount` property of the value of the `PSSessionOption parameter`.</span></span> <span data-ttu-id="97aa5-138">기본값은 5입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-138">The default value is 5.</span></span> <span data-ttu-id="97aa5-139">자세한 내용은 `PSSessionOption` 매개 변수 및 [새-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption)에 대 한 설명을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97aa5-139">For more information, see the description of the `PSSessionOption` parameter and [New-PSSessionOption](xref:Microsoft.PowerShell.Core.New-PSSessionOption).</span></span>

#### <a name="-psapplicationname-string"></a><span data-ttu-id="97aa5-140">-PSApplicationName \<String\></span><span class="sxs-lookup"><span data-stu-id="97aa5-140">-PSApplicationName \<String\></span></span>

<span data-ttu-id="97aa5-141">대상 컴퓨터에 연결 하는 데 사용 되는 연결 URI의 응용 프로그램 이름 세그먼트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-141">Specifies the application name segment of the connection URI that is used to connect to the target computers.</span></span> <span data-ttu-id="97aa5-142">명령에 매개 변수를 사용 하지 않는 경우이 매개 변수를 사용 하 여 응용 프로그램 이름을 지정 합니다 `ConnectionURI` .</span><span class="sxs-lookup"><span data-stu-id="97aa5-142">Use this parameter to specify the application name when you are not using the `ConnectionURI` parameter in the command.</span></span>

<span data-ttu-id="97aa5-143">기본값은 `$PSSessionApplicationName` 로컬 컴퓨터의 기본 설정 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-143">The default value is the value of the `$PSSessionApplicationName` preference variable on the local computer.</span></span> <span data-ttu-id="97aa5-144">이 기본 설정 변수를 정의하지 않으면 WSMAN이 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-144">If this preference variable is not defined, the default value is WSMAN.</span></span> <span data-ttu-id="97aa5-145">이 값은 대부분의 사용에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-145">This value is appropriate for most uses.</span></span> <span data-ttu-id="97aa5-146">자세한 내용은 [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97aa5-146">For more information, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="97aa5-147">WinRM 서비스는 애플리케이션 이름을 사용하여 연결 요청을 제공하는 수신기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-147">The WinRM service uses the application name to select a listener to service the connection request.</span></span> <span data-ttu-id="97aa5-148">이 매개 변수 값은 `URLPrefix` 원격 컴퓨터에 있는 수신기의 속성 값과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-148">The value of this parameter should match the value of the `URLPrefix` property of a listener on the remote computer.</span></span>

#### <a name="-psauthentication-authenticationmechanism"></a><span data-ttu-id="97aa5-149">-PSAuthentication \<AuthenticationMechanism\></span><span class="sxs-lookup"><span data-stu-id="97aa5-149">-PSAuthentication \<AuthenticationMechanism\></span></span>

<span data-ttu-id="97aa5-150">대상 컴퓨터에 연결할 때 사용자의 자격 증명을 인증 하는 데 사용 되는 메커니즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-150">Specifies the mechanism that is used to authenticate the user's credentials when connecting to the target computers.</span></span>

<span data-ttu-id="97aa5-151">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-151">Valid values are:</span></span>

- <span data-ttu-id="97aa5-152">**기본값**</span><span class="sxs-lookup"><span data-stu-id="97aa5-152">**Default**</span></span>
- <span data-ttu-id="97aa5-153">**기본**</span><span class="sxs-lookup"><span data-stu-id="97aa5-153">**Basic**</span></span>
- <span data-ttu-id="97aa5-154">**Credssp**</span><span class="sxs-lookup"><span data-stu-id="97aa5-154">**Credssp**</span></span>
- <span data-ttu-id="97aa5-155">**다이제스트**</span><span class="sxs-lookup"><span data-stu-id="97aa5-155">**Digest**</span></span>
- <span data-ttu-id="97aa5-156">**Kerberos**</span><span class="sxs-lookup"><span data-stu-id="97aa5-156">**Kerberos**</span></span>
- <span data-ttu-id="97aa5-157">**결정할**</span><span class="sxs-lookup"><span data-stu-id="97aa5-157">**Negotiate**</span></span>
- <span data-ttu-id="97aa5-158">**NegotiateWithImplicitCredential**</span><span class="sxs-lookup"><span data-stu-id="97aa5-158">**NegotiateWithImplicitCredential**</span></span>

<span data-ttu-id="97aa5-159">기본값은 **Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-159">The default value is **Default**.</span></span>

<span data-ttu-id="97aa5-160">이 매개 변수 값에 대 한 자세한 내용은 `System.Management.Automation.Runspaces.AuthenticationMechanism` MSDN의 열거 설명을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="97aa5-160">For information about the values of this parameter, see the description of the `System.Management.Automation.Runspaces.AuthenticationMechanism` enumeration in MSDN.</span></span>

> [!WARNING]
> <span data-ttu-id="97aa5-161">사용자 자격 증명이 인증할 원격 컴퓨터로 전달되는 CredSSP(Credential Security Service Provider) 인증은 원격 네트워크 공유 액세스 등 두 개 이상의 리소스에서 인증이 필요한 명령에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-161">Credential Security Service Provider (CredSSP) authentication, in which the user's credentials are passed to a remote computer to be authenticated, is designed for commands that require authentication on more than one resource, such as accessing a remote network share.</span></span> <span data-ttu-id="97aa5-162">이렇게 하면 원격 작업의 보안 위험이 커집니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-162">This mechanism increases the security risk of the remote operation.</span></span> <span data-ttu-id="97aa5-163">원격 컴퓨터가 손상된 경우 이 컴퓨터로 전달된 자격 증명을 사용하여 네트워크 세션을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-163">If the remote computer is compromised, the credentials that are passed to it can be used to control the network session.</span></span>

#### <a name="-psauthenticationlevel-authenticationlevel"></a><span data-ttu-id="97aa5-164">-PSAuthenticationLevel \<AuthenticationLevel\></span><span class="sxs-lookup"><span data-stu-id="97aa5-164">-PSAuthenticationLevel \<AuthenticationLevel\></span></span>

<span data-ttu-id="97aa5-165">대상 컴퓨터에 대 한 연결의 인증 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-165">Specifies the authentication level for the connections to the target computers.</span></span>
<span data-ttu-id="97aa5-166">기본값은 **Default** 입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-166">The default value is **Default**.</span></span>

<span data-ttu-id="97aa5-167">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-167">Valid values are:</span></span>

|<span data-ttu-id="97aa5-168">속성</span><span class="sxs-lookup"><span data-stu-id="97aa5-168">Name</span></span> |<span data-ttu-id="97aa5-169">Description</span><span class="sxs-lookup"><span data-stu-id="97aa5-169">Description</span></span> |
|---------|---------|
|<span data-ttu-id="97aa5-170">**변경 안 됨**</span><span class="sxs-lookup"><span data-stu-id="97aa5-170">**Unchanged**</span></span> | <span data-ttu-id="97aa5-171">인증 수준이 이전 명령과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-171">The authentication level is the same as the previous command.</span></span> |
|<span data-ttu-id="97aa5-172">**기본값**</span><span class="sxs-lookup"><span data-stu-id="97aa5-172">**Default**</span></span> | <span data-ttu-id="97aa5-173">Windows 인증.</span><span class="sxs-lookup"><span data-stu-id="97aa5-173">Windows Authentication.</span></span> |
|<span data-ttu-id="97aa5-174">**없음**</span><span class="sxs-lookup"><span data-stu-id="97aa5-174">**None**</span></span> | <span data-ttu-id="97aa5-175">COM 인증이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-175">No COM authentication.</span></span>   |
|<span data-ttu-id="97aa5-176">**연결**</span><span class="sxs-lookup"><span data-stu-id="97aa5-176">**Connect**</span></span> | <span data-ttu-id="97aa5-177">연결 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-177">Connect-level COM authentication.</span></span>|
|<span data-ttu-id="97aa5-178">**호출**</span><span class="sxs-lookup"><span data-stu-id="97aa5-178">**Call**</span></span> | <span data-ttu-id="97aa5-179">호출 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-179">Call-level COM authentication.</span></span>   |
|<span data-ttu-id="97aa5-180">**패킷**</span><span class="sxs-lookup"><span data-stu-id="97aa5-180">**Packet**</span></span> | <span data-ttu-id="97aa5-181">패킷 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-181">Packet-level COM authentication.</span></span>|
|<span data-ttu-id="97aa5-182">**PacketIntegrity**</span><span class="sxs-lookup"><span data-stu-id="97aa5-182">**PacketIntegrity**</span></span> | <span data-ttu-id="97aa5-183">패킷 무결성 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-183">Packet Integrity-level COM authentication.</span></span>  |
|<span data-ttu-id="97aa5-184">**PacketPrivacy**</span><span class="sxs-lookup"><span data-stu-id="97aa5-184">**PacketPrivacy**</span></span> | <span data-ttu-id="97aa5-185">패킷 전용 수준 COM 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-185">Packet Privacy-level COM authentication.</span></span> |

#### <a name="-pscertificatethumbprint-string"></a><span data-ttu-id="97aa5-186">-PSCertificateThumbprint \<String\></span><span class="sxs-lookup"><span data-stu-id="97aa5-186">-PSCertificateThumbprint \<String\></span></span>

<span data-ttu-id="97aa5-187">이 작업을 수행할 권한이 있는 사용자 계정의 디지털 공개 키 인증서(X509)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-187">Specifies the digital public key certificate (X509) of a user account that has permission to perform this action.</span></span> <span data-ttu-id="97aa5-188">인증서의 인증서 지문을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-188">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="97aa5-189">인증서는 클라이언트 인증서 기반 인증에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-189">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="97aa5-190">인증서 손 도장(Thumbprint)은 로컬 사용자 계정으로만 매핑될 수 있고 도메인 계정에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-190">They can only be mapped to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="97aa5-191">인증서를 가져오려면 [Get Item](xref:Microsoft.PowerShell.Management.Get-Item) 또는 [Get-childitem] (.)을 사용 합니다. /.. Windows PowerShell Cert: 드라이브의 cmdlet을/Microsoft.PowerShell.Management/Get-Childitem.md 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-191">To get a certificate, use the [Get-Item](xref:Microsoft.PowerShell.Management.Get-Item) or [Get-ChildItem] (../../Microsoft.PowerShell.Management/Get-Childitem.md) cmdlets in the Windows PowerShell Cert: drive.</span></span>

#### <a name="-pscomputername-string"></a><span data-ttu-id="97aa5-192">-PSComputerName \<String[]\></span><span class="sxs-lookup"><span data-stu-id="97aa5-192">-PSComputerName \<String[]\></span></span>

<span data-ttu-id="97aa5-193">워크플로의 대상 노드인 컴퓨터 목록을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-193">Specifies the list of computers that are the target nodes of the workflow.</span></span>
<span data-ttu-id="97aa5-194">워크플로의 명령 또는 활동은이 매개 변수를 사용 하 여 지정 된 컴퓨터에서 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-194">Commands or activities in a workflow are run on the computers that are specified by using this parameter.</span></span> <span data-ttu-id="97aa5-195">기본값은 로컬 컴퓨터입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-195">The default is the local computer.</span></span>

<span data-ttu-id="97aa5-196">하나 이상의 컴퓨터의 NETBIOS 이름, IP 주소 또는 정규화된 도메인 이름을 쉼표로 구분된 목록으로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-196">Type the NETBIOS name, IP address, or fully-qualified domain name of one or more computers in a comma-separated list.</span></span> <span data-ttu-id="97aa5-197">로컬 컴퓨터를 지정하려면 컴퓨터 이름, "localhost" 또는 점(.)을 입력하세요.</span><span class="sxs-lookup"><span data-stu-id="97aa5-197">To specify the local computer, type the computer name, "localhost", or a dot (.).</span></span>

<span data-ttu-id="97aa5-198">매개 변수 값에 로컬 컴퓨터를 포함 하려면 `PSComputerName` "관리자 권한으로 실행" 옵션을 사용 하 여 Windows PowerShell을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-198">To include the local computer in the value of the `PSComputerName` parameter, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="97aa5-199">명령에서이 매개 변수를 생략 하거나 값이 `$null` 또는 빈 문자열인 경우 워크플로 대상은 로컬 컴퓨터이 고 Windows PowerShell 원격을 사용 하 여 명령을 실행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-199">If this parameter is omitted from the command, or it value is `$null` or an empty string, the workflow target is the local computer and Windows PowerShell remoting is not used to run the command.</span></span>

<span data-ttu-id="97aa5-200">매개 변수 값에 IP 주소를 사용 하려면 `ComputerName` 명령에 매개 변수를 포함 해야 합니다 `PSCredential` .</span><span class="sxs-lookup"><span data-stu-id="97aa5-200">To use an IP address in the value of the `ComputerName` parameter, the command must include the `PSCredential` parameter.</span></span> <span data-ttu-id="97aa5-201">또한 HTTPS 전송을 사용하도록 컴퓨터를 구성하거나 원격 컴퓨터의 IP 주소를 로컬 컴퓨터의 WinRM TrustedHosts 목록에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-201">Also, the computer must be configured for HTTPS transport or the IP address of the remote computer must be included in the WinRM TrustedHosts list on the local computer.</span></span> <span data-ttu-id="97aa5-202">TrustedHosts 목록에 컴퓨터 이름을 추가 하는 방법에 대 한 지침은 [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md)의 *"신뢰할 수 있는 호스트 목록에 컴퓨터를 추가 하는 방법"* 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="97aa5-202">For instructions for adding a computer name to the TrustedHosts list, see *"How to Add a Computer to the Trusted Host List"* in [about_Remote_Troubleshooting](../../Microsoft.PowerShell.Core/About/about_Remote_Troubleshooting.md).</span></span>

#### <a name="-psconfigurationname-string"></a><span data-ttu-id="97aa5-203">-PSConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="97aa5-203">-PSConfigurationName \<String\></span></span>

<span data-ttu-id="97aa5-204">대상 컴퓨터에서 세션을 구성 하는 데 사용 되는 세션 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-204">Specifies the session configurations that are used to configure sessions on the target computers.</span></span> <span data-ttu-id="97aa5-205">대상 컴퓨터에 세션 구성을 입력 합니다 (워크플로 서버 컴퓨터가 아님).</span><span class="sxs-lookup"><span data-stu-id="97aa5-205">Enter a session configuration on the target computers (not the workflow server computer).</span></span> <span data-ttu-id="97aa5-206">기본값은 `Microsoft.PowerShell.Workflow`입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-206">The default is `Microsoft.PowerShell.Workflow`.</span></span>

#### <a name="-psconnectionretrycount-uint"></a><span data-ttu-id="97aa5-207">-PSConnectionRetryCount \<UInt\></span><span class="sxs-lookup"><span data-stu-id="97aa5-207">-PSConnectionRetryCount \<UInt\></span></span>

<span data-ttu-id="97aa5-208">첫 번째 연결 시도가 실패 한 경우 각 대상 컴퓨터에 대 한 최대 연결 시도 횟수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-208">Specifies the maximum number of attempts to connect to each target computer if the first connection attempt fails.</span></span> <span data-ttu-id="97aa5-209">1에서 4294967295 사이의 숫자 (Int32.maxvalue)를 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-209">Enter a number between 1 and 4,294,967,295 (UInt.MaxValue).</span></span> <span data-ttu-id="97aa5-210">기본값 영 (0)은 재시도 횟수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-210">The default value, zero (0), represents no retry attempts.</span></span>

#### <a name="-psconnectionretryintervalsec-uint"></a><span data-ttu-id="97aa5-211">-PSConnectionRetryIntervalSec \<UInt\></span><span class="sxs-lookup"><span data-stu-id="97aa5-211">-PSConnectionRetryIntervalSec \<UInt\></span></span>

<span data-ttu-id="97aa5-212">연결 다시 시도 사이의 지연 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-212">Specifies the delay between connection retry attempts in seconds.</span></span> <span data-ttu-id="97aa5-213">기본값은 영(0)입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-213">The default value is zero (0).</span></span> <span data-ttu-id="97aa5-214">이 매개 변수는 PSConnectionRetryCount의 값이 1 이상인 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-214">This parameter is valid only when the value of PSConnectionRetryCount is at least 1.</span></span>

#### <a name="-psconnectionuri-systemuri"></a><span data-ttu-id="97aa5-215">-PSConnectionURI \<System.Uri\></span><span class="sxs-lookup"><span data-stu-id="97aa5-215">-PSConnectionURI \<System.Uri\></span></span>

<span data-ttu-id="97aa5-216">대상 컴퓨터에서 워크플로의 연결 끝점을 정의 하는 URI (Uniform Resource Identifier)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-216">Specifies a Uniform Resource Identifier (URI) that defines the connection endpoint for the workflow on the target computer.</span></span> <span data-ttu-id="97aa5-217">URI는 정규화된 URI여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-217">The URI must be fully qualified.</span></span>

<span data-ttu-id="97aa5-218">이 문자열의 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-218">The format of this string is as follows:</span></span>

`<Transport>://<ComputerName>:<Port>/<ApplicationName>`

<span data-ttu-id="97aa5-219">기본값은 `http://localhost:5985/WSMAN`입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-219">The default value is `http://localhost:5985/WSMAN`.</span></span>

<span data-ttu-id="97aa5-220">을 지정 하지 않으면,, `PSConnectionURI` `PSUseSSL` `PSComputerName` `PSPort` 및 매개 변수를 사용 하 여 값을 `PSApplicationName` 지정할 수 있습니다 `PSConnectionURI` .</span><span class="sxs-lookup"><span data-stu-id="97aa5-220">If you do not specify a `PSConnectionURI`, you can use the `PSUseSSL`, `PSComputerName`, `PSPort`, and `PSApplicationName` parameters to specify the `PSConnectionURI` values.</span></span>

<span data-ttu-id="97aa5-221">URI의 전송 세그먼트에 유효한 값은 **HTTP** 및 **HTTPS** 입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-221">Valid values for the Transport segment of the URI are **HTTP** and **HTTPS**.</span></span>
<span data-ttu-id="97aa5-222">전송 세그먼트를 사용 하 여 연결 URI를 지정 하 고 포트를 지정 하지 않으면 세션은 표준 포트 80 (HTTP의 경우, HTTPS의 경우 443)를 사용 하 여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-222">If you specify a connection URI with a Transport segment, but do not specify a port, the session is created with standards ports: 80 for HTTP and 443 for HTTPS.</span></span> <span data-ttu-id="97aa5-223">Windows PowerShell 원격을 위한 기본 포트를 사용하려면 HTTP의 경우 포트 5985 또는 HTTPS의 경우 5986을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-223">To use the default ports for Windows PowerShell remoting, specify port 5985 for HTTP or 5986 for HTTPS.</span></span>

#### <a name="-pscredential-pscredential"></a><span data-ttu-id="97aa5-224">-PSCredential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="97aa5-224">-PSCredential \<PSCredential\></span></span>

<span data-ttu-id="97aa5-225">대상 컴퓨터에서 워크플로를 실행할 수 있는 권한을 가진 사용자 계정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-225">Specifies a user account that has permission to run a workflow on the target computer.</span></span> <span data-ttu-id="97aa5-226">기본값은 현재 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-226">The default is the current user.</span></span> <span data-ttu-id="97aa5-227">이 매개 변수는 PSComputerName 매개 변수가 명령에 포함 된 경우에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-227">This parameter is valid only when the PSComputerName parameter is included in the command.</span></span>

<span data-ttu-id="97aa5-228">"User01" 또는 "Domain01\User01"과 같은 사용자 이름을 입력 하거나 `PSCredential` cmdlet이 반환 하는 개체와 같은 개체를 포함 하는 변수를 입력 `Get-Credential` 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-228">Type a user name, such as "User01" or "Domain01\User01", or enter a variable that contains a `PSCredential` object, such as one that the `Get-Credential` cmdlet returns.</span></span> <span data-ttu-id="97aa5-229">사용자 이름만 입력하면 암호를 묻는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-229">If you enter only a user name, you will be prompted for a password.</span></span>

#### <a name="-pselapsedtimeoutsec-uint32"></a><span data-ttu-id="97aa5-230">-PSElapsedTimeoutSec \<UInt32\></span><span class="sxs-lookup"><span data-stu-id="97aa5-230">-PSElapsedTimeoutSec \<UInt32\></span></span>

<span data-ttu-id="97aa5-231">시스템에서 워크플로 및 모든 관련 리소스를 유지 관리 하는 기간을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-231">Determines how long the workflow and all related resources are maintained in the system.</span></span> <span data-ttu-id="97aa5-232">제한 시간이 만료 되 면 워크플로는 아직 처리 중인 경우에도 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-232">When the timeout expires, the workflow is deleted, even if it is still processing.</span></span> <span data-ttu-id="97aa5-233">10에서 4294967295 사이의 값을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-233">Enter a value between 10 and 4,294,967,295.</span></span> <span data-ttu-id="97aa5-234">기본값 0은 경과 된 시간 제한이 없음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-234">The default value, 0 (zero), means that there is no elapsed timeout.</span></span>

#### <a name="-psparametercollection-hashtable"></a><span data-ttu-id="97aa5-235">-PSParameterCollection \<Hashtable[]\></span><span class="sxs-lookup"><span data-stu-id="97aa5-235">-PSParameterCollection \<Hashtable[]\></span></span>

<span data-ttu-id="97aa5-236">서로 다른 대상 컴퓨터에 대해 서로 다른 워크플로 일반 매개 변수 값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-236">Specifies different workflow common parameter values for different target computers.</span></span>

<span data-ttu-id="97aa5-237">각 대상 컴퓨터에 대해 하나의 해시 테이블을 사용 하 여 쉼표로 구분 된 해시 테이블 목록을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-237">Enter a comma-separated list of hash tables with one hash table for each target computer.</span></span> <span data-ttu-id="97aa5-238">각 해시 테이블에서 첫 번째 키는이 `PSComputerName` 고 해당 값은 대상 컴퓨터의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-238">In each hash table, the first key is `PSComputerName` and its value is the name of the target computer.</span></span> <span data-ttu-id="97aa5-239">컴퓨터 이름에 와일드 카드 문자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-239">Wildcard characters are permitted in the computer name.</span></span> <span data-ttu-id="97aa5-240">해시 테이블의 나머지 키에 대 한 키는 매개 변수 이름이 고 값은 매개 변수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-240">For the remaining keys in the hash table, the key is the parameter name and the value is the parameter value.</span></span>

<span data-ttu-id="97aa5-241">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="97aa5-241">For example:</span></span>

```powershell
-PSParameterCollection @{PSComputerName="*"; PSElapsedTimeoutSec=20},
@{PSComputerName="Server02"},
@{PSComputerName="Server03"},
@{PSComputerName="Server01"; PSElapsedTimeoutSec=10}
```

<span data-ttu-id="97aa5-242">위의 예제에서 모든 연결의 기본 PSElapsedTimeoutSec은 20 초의 기본 Server01를 제외 하 고, 기본 값을 10 초로 지정 하 여 기본값을 재정의 하는 경우를 제외 하 고,</span><span class="sxs-lookup"><span data-stu-id="97aa5-242">In the above example, all connections will have a default PSElapsedTimeoutSec of 20 seconds, except for Server01 which overrides the default value by specifying its own timeout of 10 seconds.</span></span>

#### <a name="-pspersist-boolean"></a><span data-ttu-id="97aa5-243">-PSPersist \<Boolean\></span><span class="sxs-lookup"><span data-stu-id="97aa5-243">-PSPersist \<Boolean\></span></span>

<span data-ttu-id="97aa5-244">워크플로에 지정 된 검사점 외에도 워크플로에 검사점을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-244">Adds checkpoints to the workflow, in addition to any checkpoints that are specified in the workflow.</span></span>

<span data-ttu-id="97aa5-245">이 매개 변수는 `PSPersist` 활동 일반 매개 변수, `Checkpoint-Workflow` 활동 또는 변수를 사용 하 여 지정 된 검사점 등 워크플로의 검사점을 표시 하지 않습니다 `$PSPersistPreference` .</span><span class="sxs-lookup"><span data-stu-id="97aa5-245">This parameter cannot suppress the checkpoints in a workflow, such as those specified by using the `PSPersist` activity common parameter, the `Checkpoint-Workflow` activity, or the `$PSPersistPreference` variable.</span></span>

<span data-ttu-id="97aa5-246">"검사점" 또는 "지 속성 지점"은 워크플로가 실행 되는 동안 캡처되고 디스크 또는 SQL 데이터베이스의 지 속성 저장소에 저장 되는 데이터와 워크플로 상태에 대 한 스냅숏입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-246">A "checkpoint" or "persistence point" is a snapshot of the workflow state and data that is captured while the workflow runs and is saved to a persistence store on disk or in a SQL database.</span></span> <span data-ttu-id="97aa5-247">Windows PowerShell 워크플로는 저장 된 데이터를 사용 하 여 워크플로를 다시 시작 하지 않고 마지막 지 속성 지점에서 일시 중단 또는 중단 된 워크플로를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-247">Windows PowerShell Workflow uses the saved data to resume a suspended or interrupted workflow from the last persistence point, rather than to restart the workflow.</span></span>

<span data-ttu-id="97aa5-248">유효한 값은</span><span class="sxs-lookup"><span data-stu-id="97aa5-248">Valid values:</span></span>

- <span data-ttu-id="97aa5-249">( *기본값* ) 이 매개 변수를 생략 하면 워크플로에 지정 된 검사점 외에도 워크플로의 시작과 끝에 검사점이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-249">( *Default* ) If you omit this parameter, a checkpoint is added to the beginning and end of the workflow, in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="97aa5-250">`$True`.</span><span class="sxs-lookup"><span data-stu-id="97aa5-250">`$True`.</span></span> <span data-ttu-id="97aa5-251">워크플로에 지정 된 검사점 외에도 워크플로의 시작과 끝에 검사점을 추가 하 고 각 활동 뒤에 검사점을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-251">Adds a checkpoint to the beginning and end of the workflow and a checkpoint after each activity, in addition to any checkpoints that are specified in the workflow.</span></span>

- <span data-ttu-id="97aa5-252">`$False`.</span><span class="sxs-lookup"><span data-stu-id="97aa5-252">`$False`.</span></span> <span data-ttu-id="97aa5-253">검사점이 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-253">No checkpoints are added.</span></span> <span data-ttu-id="97aa5-254">검사점은 워크플로에 지정 된 경우에만 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-254">Checkpoints are taken only when specified in the workflow.</span></span>

#### <a name="-psport-int32"></a><span data-ttu-id="97aa5-255">-PSPort \<Int32\></span><span class="sxs-lookup"><span data-stu-id="97aa5-255">-PSPort \<Int32\></span></span>

<span data-ttu-id="97aa5-256">대상 컴퓨터의 네트워크 포트를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-256">Specifies the network port on the target computers.</span></span> <span data-ttu-id="97aa5-257">기본 포트는 5985(HTTP용 WinRM 포트) 및 5986(HTTPS용 WinRM 포트)입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-257">The default ports are 5985 (the WinRM port for HTTP) and 5986 (the WinRM port for HTTPS).</span></span>

<span data-ttu-id="97aa5-258">반드시 필요한 경우가 아니면 PSPort 매개 변수를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="97aa5-258">Do not use the PSPort parameter unless you must.</span></span> <span data-ttu-id="97aa5-259">명령에 설정 된 포트는 명령이 실행 되는 모든 컴퓨터 또는 세션에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-259">The port set in the command applies to all computers or sessions on which the command runs.</span></span> <span data-ttu-id="97aa5-260">대체 포트 설정을 사용하면 일부 컴퓨터에서 명령이 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-260">An alternate port setting might prevent the command from running on all computers.</span></span> <span data-ttu-id="97aa5-261">대체 포트를 사용하려면 먼저 원격 컴퓨터에 해당 포트에서 수신 대기할 WinRM 수신기를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-261">Before using an alternate port, you must configure the WinRM listener on the remote computer to listen at that port.</span></span>

#### <a name="-psprivatemetadata-hashtable"></a><span data-ttu-id="97aa5-262">-PSPrivateMetadata \<Hashtable\></span><span class="sxs-lookup"><span data-stu-id="97aa5-262">-PSPrivateMetadata \<Hashtable\></span></span>

<span data-ttu-id="97aa5-263">워크플로 작업에 사용자 지정 된 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-263">Provides customized information to workflow jobs.</span></span> <span data-ttu-id="97aa5-264">해시 테이블을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-264">Enter a hash table.</span></span> <span data-ttu-id="97aa5-265">각 워크플로에 대 한 키 및 값이 사용자 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-265">The keys and values are customized for each workflow.</span></span> <span data-ttu-id="97aa5-266">워크플로의 개인 메타 데이터에 대 한 자세한 내용은 워크플로에 대 한 도움말 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97aa5-266">For information about the private metadata of a workflow, see the help topic for the workflow.</span></span>

<span data-ttu-id="97aa5-267">이 매개 변수는 Windows PowerShell 워크플로 엔진에서 처리 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-267">This parameter is not processed by the Windows PowerShell Workflow engine.</span></span>
<span data-ttu-id="97aa5-268">대신, 엔진은 해시 테이블을 워크플로로 직접 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-268">Instead, the engine passes the hash table directly to the workflow.</span></span>

#### <a name="-psrunningtimeoutsec-uint32"></a><span data-ttu-id="97aa5-269">-PSRunningTimeoutSec \<UInt32\></span><span class="sxs-lookup"><span data-stu-id="97aa5-269">-PSRunningTimeoutSec \<UInt32\></span></span>

<span data-ttu-id="97aa5-270">워크플로가 일시 중단 된 시간을 제외 하 고 워크플로의 실행 시간 (초)을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-270">Specifies the running time of the workflow in seconds, excluding any time that the workflow is suspended.</span></span> <span data-ttu-id="97aa5-271">시간이 만료 될 때 워크플로 실행이 완료 되지 않으면 Windows PowerShell 워크플로 엔진은 워크플로 실행을 강제로 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-271">If workflow execution is not complete when the time expires, the Windows PowerShell Workflow engine forcibly stops the execution of the workflow.</span></span>

#### <a name="-pssessionoption-pssessionoption"></a><span data-ttu-id="97aa5-272">-PSSessionOption \<PSSessionOption\></span><span class="sxs-lookup"><span data-stu-id="97aa5-272">-PSSessionOption \<PSSessionOption\></span></span>

<span data-ttu-id="97aa5-273">대상 컴퓨터에 대 한 세션의 고급 옵션을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-273">Sets advanced options for the sessions to the target computers.</span></span> <span data-ttu-id="97aa5-274">Cmdlet을 `PSSessionOption` 사용 하 여 만든 개체와 같은 개체를 입력 합니다 `New-PSSessionOption` .</span><span class="sxs-lookup"><span data-stu-id="97aa5-274">Enter a `PSSessionOption` object, such as one that you create by using the `New-PSSessionOption` cmdlet.</span></span>

<span data-ttu-id="97aa5-275">세션 옵션의 기본값은 기본 설정 `$PSSessionOption` 변수의 값 (설정 된 경우)에 따라 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-275">The default values for the session options are determined by the value of the `$PSSessionOption` preference variable, if it is set.</span></span> <span data-ttu-id="97aa5-276">그렇지 않으면 세션 구성에 지정 된 값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-276">Otherwise, the session uses the values specified in the session configuration.</span></span>

<span data-ttu-id="97aa5-277">기본값을 포함 하 여 세션 옵션에 대 한 자세한 내용은 cmdlet의 도움말 항목 `New-PSSessionOption` (.. /.. /Microsoft.PowerShell.Core/New-PSSessionOption.md).</span><span class="sxs-lookup"><span data-stu-id="97aa5-277">For a description of the session options, including the default values, see the help topic for the `New-PSSessionOption` cmdlet (../../Microsoft.PowerShell.Core/New-PSSessionOption.md).</span></span> <span data-ttu-id="97aa5-278">기본 설정 변수에 대 한 자세한 내용은 `$PSSessionOption` [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="97aa5-278">For information about the `$PSSessionOption` preference variable, see [about_Preference_Variables](../../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

#### <a name="-psusessl-switchparameter"></a><span data-ttu-id="97aa5-279">-PSUseSSL \<SwitchParameter\></span><span class="sxs-lookup"><span data-stu-id="97aa5-279">-PSUseSSL \<SwitchParameter\></span></span>

<span data-ttu-id="97aa5-280">는 SSL(Secure Sockets Layer) (SSL) 프로토콜을 사용 하 여 대상 컴퓨터에 대 한 연결을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-280">Uses the Secure Sockets Layer (SSL) protocol to establish a connection to the target computer.</span></span> <span data-ttu-id="97aa5-281">기본적으로 SSL은 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-281">By default, SSL is not used.</span></span>

<span data-ttu-id="97aa5-282">WS-Management는 네트워크를 통해 전송되는 모든 Windows PowerShell 내용을 암호화합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-282">WS-Management encrypts all Windows PowerShell content transmitted over the network.</span></span> <span data-ttu-id="97aa5-283">UseSSL은 HTTP 대신 HTTPS를 통해 데이터를 보내는 추가적인 보호 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-283">UseSSL is an additional protection that sends the data across an HTTPS, instead of HTTP.</span></span> <span data-ttu-id="97aa5-284">이 매개 변수를 사용하지만 명령에 사용되는 포트에서 SSL을 사용할 수 없는 경우 명령이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="97aa5-284">If you use this parameter, but SSL is not available on the port used for the command, the command fails.</span></span>

## <a name="see-also"></a><span data-ttu-id="97aa5-285">참고 항목</span><span class="sxs-lookup"><span data-stu-id="97aa5-285">SEE ALSO</span></span>

- [<span data-ttu-id="97aa5-286">about_ActivityCommonParameters</span><span class="sxs-lookup"><span data-stu-id="97aa5-286">about_ActivityCommonParameters</span></span>](about_ActivityCommonParameters.md)
- [<span data-ttu-id="97aa5-287">about_Workflows</span><span class="sxs-lookup"><span data-stu-id="97aa5-287">about_Workflows</span></span>](about_Workflows.md)
- [<span data-ttu-id="97aa5-288">Invoke-AsWorkflow</span><span class="sxs-lookup"><span data-stu-id="97aa5-288">Invoke-AsWorkflow</span></span>](xref:PSWorkflowUtility.Invoke-AsWorkflow)
- [<span data-ttu-id="97aa5-289">New-PSWorkflowExecutionOption</span><span class="sxs-lookup"><span data-stu-id="97aa5-289">New-PSWorkflowExecutionOption</span></span>](xref:PSWorkflow.New-PSWorkflowExecutionOption)
- [<span data-ttu-id="97aa5-290">New-PSWorkflowSession</span><span class="sxs-lookup"><span data-stu-id="97aa5-290">New-PSWorkflowSession</span></span>](xref:PSWorkflow.New-PSWorkflowSession)
