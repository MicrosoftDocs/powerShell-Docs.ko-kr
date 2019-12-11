---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
title: DSC(원하는 상태 구성)의 알려진 문제 및 제한 사항
ms.openlocfilehash: a76c5bb336804c5b384e6b6ba6a705c6049ef7fb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416613"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="a882b-103">DSC(원하는 상태 구성)의 알려진 문제 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="a882b-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="a882b-104">주요 변경 내용: DSC 구성에서 암호를 암호화/암호 해독하는 데 사용된 인증서가 WMF 5.0 RTM 설치 후 작동하지 않을 수 있음</span><span class="sxs-lookup"><span data-stu-id="a882b-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="a882b-105">WMF 4.0 및 WMF 5.0 Preview 릴리스의 DSC 구성에서는 121자보다 긴 암호를 허용하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="a882b-106">DSC는 길고 강력한 암호가 적합한 경우에도 짧은 암호를 사용해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="a882b-107">이 새로운 변경 사항은 DSC 구성에서 임의 길이의 암호를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="a882b-108">**해결 방법:** 데이터 암호화 또는 키 암호화 키 사용 및 문서 암호화 향상된 키 사용(1.3.6.1.4.1.311.80.1)을 사용하여 인증서를 다시 만드세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="a882b-109">자세한 내용은 [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="a882b-110">DSC cmdlet이 WMF 5.0 RTM 설치 후 실패할 수 있음</span><span class="sxs-lookup"><span data-stu-id="a882b-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="a882b-111">WMF 5.0 RTM 설치 후 `Start-DscConfiguration` 및 기타 DSC cmdlet이 다음과 같은 오류로 인해 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="a882b-112">**해결 방법:** 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하여 DSCEngineCache.mof를 삭제하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="a882b-113">WMF 5.0 RTM이 WMF 5.0 Production Preview 위에 설치된 경우 DSC cmdlet이 작동하지 않을 수 있음</span><span class="sxs-lookup"><span data-stu-id="a882b-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="a882b-114">**해결 방법:** 다음 명령을 관리자 권한 PowerShell 세션에서 실행(관리자 권한으로 실행)하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="a882b-115">DebugMode에서 Get-DscConfiguration을 사용하는 동안 LCM이 불안정한 상태가 될 수 있음</span><span class="sxs-lookup"><span data-stu-id="a882b-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="a882b-116">LCM이 DebugMode인 경우 Ctrl+C를 눌러 `Get-DscConfiguration`의 처리를 중지하면 LCM이 불안정한 상태가 되어 대부분의 DSC cmdlet이 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="a882b-117">**해결 방법:** `Get-DscConfiguration` cmdlet을 디버깅하는 동안 Ctrl+C를 누르지 마세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="a882b-118">Stop-DscConfiguration이 DebugMode에서 응답하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="a882b-119">LCM이 DebugMode인 경우 `Get-DscConfiguration`으로 시작한 작업을 중지하려고 하면 `Stop-DscConfiguration`이 응답하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="a882b-120">**해결 방법:** [DSC 리소스 디버그](/powershell/scripting/dsc/troubleshooting/debugResource)에 설명된 대로 `Get-DscConfiguration`으로 시작한 작업의 디버깅을 완료하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="a882b-121">DebugMode에 자세한 오류 메시지가 표시되지 않음</span><span class="sxs-lookup"><span data-stu-id="a882b-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="a882b-122">LCM이 **DebugMode**인 경우 DSC 리소스에서 자세한 오류 메시지가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="a882b-123">**해결 방법:** 리소스에서 자세한 정보 메시지를 표시하려면 **DebugMode**를 사용하지 않도록 설정하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="a882b-124">Get-DscConfigurationStatus cmdlet에서 Invoke-DscResource 작업을 검색할 수 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="a882b-125">`Invoke-DscResource` cmdlet을 사용하여 리소스의 메서드를 직접 호출한 후에는 `Get-DscConfigurationStatus`를 통해 이 작업의 레코드를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="a882b-126">**해결 방법:** 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="a882b-127">Get-DscConfigurationStatus에서 끌어오기 주기 작업을 **Consistency** 형식으로 반환함</span><span class="sxs-lookup"><span data-stu-id="a882b-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="a882b-128">노드가 PULL 새로 고침 모드로 설정된 경우 수행된 각 끌어오기 작업에 대해 `Get-DscConfigurationStatus` cmdlet은 작업 유형을 *Initial*이 아닌 **Consistency**로 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="a882b-129">**해결 방법:** 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="a882b-130">Invoke-DscResource cmdlet이 메시지를 생성된 순서대로 반환하지 않음</span><span class="sxs-lookup"><span data-stu-id="a882b-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="a882b-131">`Invoke-DscResource` cmdlet이 자세한 정보, 경고 및 오류 메시지를 LCM 또는 DSC 리소스에서 생성된 순서대로 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="a882b-132">**해결 방법:** 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="a882b-133">Invoke-DscResource와 함께 사용할 경우 DSC 리소스를 쉽게 디버그할 수 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="a882b-134">LCM이 디버그 모드에서 실행되고 있으면 `Invoke-DscResource` cmdlet에서 디버깅을 위해 연결할 runspace에 대한 정보를 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="a882b-135">자세한 내용은 [DSC 리소스 디버그](/powershell/scripting/dsc/troubleshooting/debugResource)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-135">For more information, see [Debugging DSC resources](/powershell/scripting/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="a882b-136">**해결 방법:** `Get-PSHostProcessInfo`, `Enter-PSHostProcess`, `Get-Runspace` 및 `Debug-Runspace` cmdlet을 사용하여 runspace를 검색 및 연결하여 DSC 리소스를 디버깅하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="a882b-137">동일한 노드에 대한 다양한 부분 구성 문서에 동일한 리소스 이름이 포함될 수 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="a882b-138">단일 노드로 배포되는 여러 부분 구성에 대해 리소스 이름이 동일하면 런타임 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="a882b-139">**해결 방법:** 다른 부분 구성에 있는 동일한 리소스인 경우에도 다른 이름을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="a882b-140">Start-DscConfiguration –UseExisting이 -Credential에서 작동하지 않음</span><span class="sxs-lookup"><span data-stu-id="a882b-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="a882b-141">`Start-DscConfiguration`을 **UseExisting** 매개 변수와 함께 사용하면 **Credential** 매개 변수가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="a882b-142">DSC에서는 기본 프로세스 ID를 사용하여 작업을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="a882b-143">그러면 원격 노드에서 계속 진행하는 데 다른 자격 증명이 필요하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="a882b-144">**해결 방법:** 원격 DSC 작업에 CIM 세션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="a882b-145">DSC 구성에서 노드 이름으로 사용된 IPv6 주소</span><span class="sxs-lookup"><span data-stu-id="a882b-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="a882b-146">이 릴리스에서는 DSC 구성 스크립트에서 노드 이름으로 사용되는 IPv6 주소가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="a882b-147">**해결 방법:** 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="a882b-148">`Class-Based` DSC 리소스의 디버깅</span><span class="sxs-lookup"><span data-stu-id="a882b-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="a882b-149">이 릴리스에서는 클래스 기반 DSC 리소스의 디버깅이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="a882b-150">**해결 방법:** 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="a882b-151">DSC 클래스 기반 리소스의 $script 범위에 정의된 변수 및 함수는 여러 DSC 리소스 호출에서 유지되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="a882b-152">구성에서 `$script` 범위에 정의된 변수나 함수가 있는 클래스 기반 리소스를 사용하고 있는 경우 `Start-DSCConfiguration`을 여러 번 연속해서 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="a882b-153">**해결 방법:** DSC 리소스 클래스 자체에서 모든 변수 및 함수를 정의하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="a882b-154">`$script` 범위 변수/함수가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="a882b-155">리소스가 PSDscRunAsCredential을 사용하는 경우의 DSC 리소스 디버깅</span><span class="sxs-lookup"><span data-stu-id="a882b-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="a882b-156">이 릴리스에서는 리소스가 구성에서 **PSDscRunAsCredential** 속성을 사용하는 경우의 DSC 리소스 디버깅이 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="a882b-157">**해결 방법:** 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="a882b-158">DSC 복합 리소스에서는 PsDscRunAsCredential이 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="a882b-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="a882b-159">**해결 방법:** 사용 가능한 경우 Credential 속성을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="a882b-160">예제 ServiceSet 및 WindowsFeatureSet</span><span class="sxs-lookup"><span data-stu-id="a882b-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="a882b-161">Get-DscResource -Syntax에 PsDscRunAsCredential이 올바르게 반영되지 않음</span><span class="sxs-lookup"><span data-stu-id="a882b-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="a882b-162">리소스에서 필수로 표시하거나 지원하지 않는 경우 **Syntax** 매개 변수는 **PsDscRunAsCredential**을 올바르게 반영하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="a882b-163">**해결 방법:** 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-163">**Resolution:** None.</span></span> <span data-ttu-id="a882b-164">그러나 ISE에서 구성을 작성하면 IntelliSense를 사용할 때 **PsDscRunAsCredential** 속성에 대한 올바른 메타데이터가 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="a882b-165">WindowsOptionalFeature를 Windows 7에서 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="a882b-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="a882b-166">**WindowsOptionalFeature** DSC 리소스는 Windows 7에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="a882b-167">이 리소스에는 DISM 모듈 및 Windows 운영 체제의 Windows 8 이상 버전부터 사용할 수 있는 DISM cmdlet이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="a882b-168">클래스 기반 DSC 리소스의 경우, Import-DscResource -ModuleVersion이 예상대로 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="a882b-169">컴파일 노드에 여러 버전의 클래스 기반 DSC 리소스 모듈이 있는 경우 `Import-DscResource -ModuleVersion`은 지정된 버전을 선택하지 않고 다음 컴파일 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="a882b-170">**해결 방법:** 다음과 같이 **ModuleSpecification** 개체를 **RequiredVersion** 키가 지정된 **ModuleName** 매개 변수로 정의하여 필요한 버전을 가져오세요.</span><span class="sxs-lookup"><span data-stu-id="a882b-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="a882b-171">레지스트리 리소스와 같은 일부 DSC 리소스는 요청을 처리하는 데 시간이 오래 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="a882b-172">**해결 방법 1:** 다음 폴더를 정기적으로 정리하는 일정 작업을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="a882b-173">**해결 방법 2:** 구성 마지막에 *CommandAnalysis* 폴더를 정리하도록 DSC 구성을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="a882b-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
