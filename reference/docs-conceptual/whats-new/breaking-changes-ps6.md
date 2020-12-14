---
ms.date: 02/03/2020
keywords: powershell,core
title: PowerShell 6.0의 주요 변경 내용
description: 이 문서에서는 Windows PowerShell 5.1과 PowerShell 6.0의 차이점을 요약합니다.
ms.openlocfilehash: b53365ee72e6a6e85faa56125a8aa7961d3ecc7f
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2020
ms.locfileid: "96833807"
---
# <a name="breaking-changes-for-powershell-6x"></a><span data-ttu-id="91c87-104">PowerShell 6.x의 호환성이 손상되는 변경</span><span class="sxs-lookup"><span data-stu-id="91c87-104">Breaking Changes for PowerShell 6.x</span></span>

## <a name="features-no-longer-available-in-powershell-core"></a><span data-ttu-id="91c87-105">PowerShell Core에서 더 이상 사용할 수 없는 기능</span><span class="sxs-lookup"><span data-stu-id="91c87-105">Features no longer available in PowerShell Core</span></span>

### <a name="modules-not-shipped-for-powershell-6x"></a><span data-ttu-id="91c87-106">PowerShell 6.x에 제공되지 않는 모듈</span><span class="sxs-lookup"><span data-stu-id="91c87-106">Modules not shipped for PowerShell 6.x</span></span>

<span data-ttu-id="91c87-107">다양한 호환성 이유로 PowerShell 6에는 다음 모듈이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-107">For various compatibility reasons, the following modules are not included in PowerShell 6.</span></span>

- <span data-ttu-id="91c87-108">ISE</span><span class="sxs-lookup"><span data-stu-id="91c87-108">ISE</span></span>
- <span data-ttu-id="91c87-109">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="91c87-109">Microsoft.PowerShell.LocalAccounts</span></span>
- <span data-ttu-id="91c87-110">Microsoft.PowerShell.ODataUtils</span><span class="sxs-lookup"><span data-stu-id="91c87-110">Microsoft.PowerShell.ODataUtils</span></span>
- <span data-ttu-id="91c87-111">Microsoft.PowerShell.Operation.Validation</span><span class="sxs-lookup"><span data-stu-id="91c87-111">Microsoft.PowerShell.Operation.Validation</span></span>
- <span data-ttu-id="91c87-112">PSScheduledJob</span><span class="sxs-lookup"><span data-stu-id="91c87-112">PSScheduledJob</span></span>
- <span data-ttu-id="91c87-113">PSWorkflow</span><span class="sxs-lookup"><span data-stu-id="91c87-113">PSWorkflow</span></span>
- <span data-ttu-id="91c87-114">PSWorkflowUtility</span><span class="sxs-lookup"><span data-stu-id="91c87-114">PSWorkflowUtility</span></span>

### <a name="powershell-workflow"></a><span data-ttu-id="91c87-115">PowerShell 워크플로</span><span class="sxs-lookup"><span data-stu-id="91c87-115">PowerShell Workflow</span></span>

<span data-ttu-id="91c87-116">[PowerShell][workflow]는 [Windows WF(Workflow Foundation)][workflow-foundation]을 토대로 빌드되는 Windows PowerShell의 기능으로, 장기 실행 또는 병렬 처리 작업을 위한 강력한 Runbook을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-116">[PowerShell Workflow][workflow] is a feature in Windows PowerShell that builds on top of [Windows Workflow Foundation (WF)][workflow-foundation] that enables the creation of robust runbooks for long-running or parallelized tasks.</span></span>

<span data-ttu-id="91c87-117">.NET Core에 Windows Workflow Foundation 지원이 없으므로 PowerShell Core에서는 이후에도 PowerShell 워크플로를 지원하지 않을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-117">Due to the lack of support for Windows Workflow Foundation in .NET Core, we are not supporting PowerShell Workflow in PowerShell Core.</span></span>

<span data-ttu-id="91c87-118">앞으로 PowerShell 워크플로 없이도 PowerShell 언어에서 네이티브 병렬 처리/동시성을 사용할 수 있기를 바랍니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-118">In the future, we would like to enable native parallelism/concurrency in the PowerShell language without the need for PowerShell Workflow.</span></span>

<span data-ttu-id="91c87-119">OS를 다시 시작한 후에도 검사점을 사용하여 스크립트를 다시 시작해야하는 경우에는 작업 스케줄러를 사용하여 OS를 시작할 때 스크립트를 실행하는 것이 좋습니다. 하지만 스크립트는 자체 상태를 유지해야 합니다(예: 파일에 유지).</span><span class="sxs-lookup"><span data-stu-id="91c87-119">If there is a need to use checkpoints to resume a script after the OS restarts, we recommend using Task Scheduler to run a script on OS startup, but the script would need to maintain its own state (like persisting it to a file).</span></span>

[workflow]: /previous-versions/powershell/scripting/components/workflows-guide
[workflow-foundation]: /dotnet/framework/windows-workflow-foundation/

### <a name="custom-snap-ins"></a><span data-ttu-id="91c87-120">사용자 지정 스냅인</span><span class="sxs-lookup"><span data-stu-id="91c87-120">Custom snap-ins</span></span>

<span data-ttu-id="91c87-121">[PowerShell 스냅인][snapin]은 PowerShell 커뮤니티에서 널리 사용되지 않는 PowerShell 모듈의 선행 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-121">[PowerShell snap-ins][snapin] are a predecessor to PowerShell modules that do not have widespread adoption in the PowerShell community.</span></span>

<span data-ttu-id="91c87-122">스냅인 지원이 복잡하고 커뮤니티에서 많이 사용되지 않으므로 PowerShell Core에서는 사용자 지정 스냅인을 더 이상 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-122">Due to the complexity of supporting snap-ins and their lack of usage in the community, we no longer support custom snap-ins in PowerShell Core.</span></span>

<span data-ttu-id="91c87-123">이로 인해, 현재 Windows와 Windows Server의 `ActiveDirectory` 및 `DnsClient` 모듈이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-123">Today, this breaks the `ActiveDirectory` and `DnsClient` modules in Windows and Windows Server.</span></span>

[snapin]: /powershell/module/microsoft.powershell.core/about/about_pssnapins

### <a name="wmi-v1-cmdlets"></a><span data-ttu-id="91c87-124">WMI v1 cmdlet</span><span class="sxs-lookup"><span data-stu-id="91c87-124">WMI v1 cmdlets</span></span>

<span data-ttu-id="91c87-125">두 개의 WMI 기반 모듈 집합을 지원하는 것은 복잡하므로 PowerShell Core에서는 WMI v1 cmdlet이 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-125">Due to the complexity of supporting two sets of WMI-based modules, we removed the WMI v1 cmdlets from PowerShell Core:</span></span>

- `Register-WmiEvent`
- `Set-WmiInstance`
- `Invoke-WmiMethod`
- `Get-WmiObject`
- `Remove-WmiObject`

<span data-ttu-id="91c87-126">대신, 동일한 기능과 함께 새로운 기능과 새롭게 디자인된 구문을 제공하는 CIM(WMI v2라고도 함) cmdlet을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-126">Instead, we recommend that you the use the CIM (aka WMI v2) cmdlets which provide the same functionality with new functionality and a redesigned syntax:</span></span>

- `Get-CimAssociatedInstance`
- `Get-CimClass`
- `Get-CimInstance`
- `Get-CimSession`
- `Invoke-CimMethod`
- `New-CimInstance`
- `New-CimSession`
- `New-CimSessionOption`
- `Register-CimIndicationEvent`
- `Remove-CimInstance`
- `Remove-CimSession`
- `Set-CimInstance`

### <a name="microsoftpowershelllocalaccounts"></a><span data-ttu-id="91c87-127">Microsoft.PowerShell.LocalAccounts</span><span class="sxs-lookup"><span data-stu-id="91c87-127">Microsoft.PowerShell.LocalAccounts</span></span>

<span data-ttu-id="91c87-128">지원되지 않는 API를 사용하는 `Microsoft.PowerShell.LocalAccounts`는 더 나은 해결 방법을 찾을 때까지 PowerShell Core에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-128">Due to the use of unsupported APIs, `Microsoft.PowerShell.LocalAccounts` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="new-webserviceproxy-cmdlet-removed"></a><span data-ttu-id="91c87-129">`New-WebServiceProxy` cmdlet이 제거됨</span><span class="sxs-lookup"><span data-stu-id="91c87-129">`New-WebServiceProxy` cmdlet removed</span></span>

<span data-ttu-id="91c87-130">.NET Core는 SOAP 프로토콜을 사용하기 위한 서비스를 제공하는 Windows Communication Framework를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-130">.NET Core does not support the Windows Communication Framework, which provide services for using the SOAP protocol.</span></span> <span data-ttu-id="91c87-131">이 cmdlet은 SOAP가 필요하므로 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-131">This cmdlet was removed because it requires SOAP.</span></span>

### <a name="-transaction-cmdlets-removed"></a><span data-ttu-id="91c87-132">`*-Transaction` cmdlet이 제거됨</span><span class="sxs-lookup"><span data-stu-id="91c87-132">`*-Transaction` cmdlets removed</span></span>

<span data-ttu-id="91c87-133">다음 cmdlet은 매우 제한적으로 사용되었으며</span><span class="sxs-lookup"><span data-stu-id="91c87-133">These cmdlets had very limited usage.</span></span> <span data-ttu-id="91c87-134">지원을 중단하기 위해 내린 결정입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-134">The decision was made to discontinue support for them.</span></span>

- `Complete-Transaction`
- `Get-Transaction`
- `Start-Transaction`
- `Undo-Transaction`
- `Use-Transaction`

### <a name="security-cmdlets-not-available-on-non-windows-platforms"></a><span data-ttu-id="91c87-135">Windows 이외의 플랫폼에서 보안 cmdlet을 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="91c87-135">Security cmdlets not available on non-Windows platforms</span></span>

- `Get-Acl`
- `Set-Acl`
- `Get-AuthenticodeSignature`
- `Set-AuthenticodeSignature`
- `Get-CmsMessage`
- `Protect-CmsMessage`
- `Unprotect-CmsMessage`
- `New-FileCatalog`
- `Test-FileCatalog`

### <a name="-computerand-other-windows-specific-cmdlets"></a><span data-ttu-id="91c87-136">`*-Computer` 및 기타 Windows 관련 cmdlet</span><span class="sxs-lookup"><span data-stu-id="91c87-136">`*-Computer`and other Windows-specific cmdlets</span></span>

<span data-ttu-id="91c87-137">지원되지 않는 API를 사용하기 때문에 다음 cmdlets이 더 나은 해결 방법을 찾을 때까지 PowerShell Core에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-137">Due to the use of unsupported APIs, the following cmdlets have been removed from PowerShell Core until a better solution is found.</span></span>

- `Get-Clipboard`
- `Set-Clipboard`
- `Add-Computer`
- `Checkpoint-Computer`
- `Remove-Computer`
- `Restore-Computer`
- `Reset-ComputerMachinePassword`
- `Disable-ComputerRestore`
- `Enable-ComputerRestore`
- `Get-ComputerRestorePoint`
- `Test-ComputerSecureChannel`
- `Get-ControlPanelItem`
- `Show-ControlPanelItem`
- `Get-HotFix`
- `Clear-RecycleBin`
- `Update-List`
- `Out-Printer`
- `ConvertFrom-String`
- `Convert-String`

### <a name="-counter-cmdlets"></a><span data-ttu-id="91c87-138">`*-Counter` cmdlet</span><span class="sxs-lookup"><span data-stu-id="91c87-138">`*-Counter` cmdlets</span></span>

<span data-ttu-id="91c87-139">지원되지 않는 API를 사용하는 `*-Counter`는 더 나은 해결 방법을 찾을 때까지 PowerShell Core에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-139">Due to the use of unsupported APIs, the `*-Counter` has been removed from PowerShell Core until a better solution is found.</span></span>

### <a name="-eventlog-cmdlets"></a><span data-ttu-id="91c87-140">`*-EventLog` cmdlet</span><span class="sxs-lookup"><span data-stu-id="91c87-140">`*-EventLog` cmdlets</span></span>

<span data-ttu-id="91c87-141">지원되지 않는 API를 사용하는 `*-EventLog`는 PowerShell Core에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-141">Due to the use of unsupported APIs, the `*-EventLog` has been removed from PowerShell Core.</span></span> <span data-ttu-id="91c87-142">더 나은 해결 방법을 찾을 때까지입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-142">until a better solution is found.</span></span> <span data-ttu-id="91c87-143">`Get-WinEvent` 및 `New-WinEvent`는 Windows에서 이벤트를 가져오고 만드는 데 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-143">`Get-WinEvent` and `New-WinEvent` are available to get and create events on Windows.</span></span>

### <a name="cmdlets-that-use-wpf-removed"></a><span data-ttu-id="91c87-144">WPF를 사용하는 cmdlet이 제거됨</span><span class="sxs-lookup"><span data-stu-id="91c87-144">Cmdlets that use WPF removed</span></span>

<span data-ttu-id="91c87-145">Windows Presentation Framework는 CoreCLR에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-145">The Windows Presentation Framework is not supported on CoreCLR.</span></span> <span data-ttu-id="91c87-146">영향을 받는 cmdlet은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-146">The following cmdlets are affected:</span></span>

- `Show-Command`
- `Out-GridView`
- <span data-ttu-id="91c87-147">`Get-Help`의 **showwindow** 매개 변수</span><span class="sxs-lookup"><span data-stu-id="91c87-147">The **showwindow** parameter of `Get-Help`</span></span>

### <a name="some-dsc-cmdlets-removed"></a><span data-ttu-id="91c87-148">일부 DSC cmdlet이 제거됨</span><span class="sxs-lookup"><span data-stu-id="91c87-148">Some DSC cmdlets removed</span></span>

- `Get-DscConfiguration`
- `Publish-DscConfiguration`
- `Restore-DscConfiguration`
- `Start-DscConfiguration`
- `Stop-DscConfiguration`
- `Test-DscConfiguration`
- `Update-DscConfiguration`
- `Remove-DscConfigurationDocument`
- `Get-DscConfigurationStatus`
- `Disable-DscDebug`
- `Enable-DscDebug`
- `Get-DscLocalConfigurationManager`
- `Set-DscLocalConfigurationManager`
- `Invoke-DscResource`

## <a name="enginelanguage-changes"></a><span data-ttu-id="91c87-149">엔진/언어 변경 내용</span><span class="sxs-lookup"><span data-stu-id="91c87-149">Engine/language changes</span></span>

### <a name="rename-powershellexe-to-pwshexe-5101"></a><span data-ttu-id="91c87-150">`powershell.exe`의 이름을 로 바꿈 `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span><span class="sxs-lookup"><span data-stu-id="91c87-150">Rename `powershell.exe` to `pwsh.exe` [#5101](https://github.com/PowerShell/PowerShell/issues/5101)</span></span>

<span data-ttu-id="91c87-151">Windows PowerShell과 구분하여, Windows에서 PowerShell Core를 가리키는 확실한 방법을 사용자에게 제공하기 위해 PowerShell Core 이진이 Windows에서는 `pwsh.exe`, 비 Windows 플랫폼에서는 `pwsh`로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-151">In order to give users a deterministic way to call PowerShell Core on Windows (as opposed to Windows PowerShell), the PowerShell Core binary was changed to `pwsh.exe` on Windows and `pwsh` on non-Windows platforms.</span></span>

<span data-ttu-id="91c87-152">약식 이름도 비 Windows 플랫폼의 셸 이름 지정과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-152">The shortened name is also consistent with naming of shells on non-Windows platforms.</span></span>

### <a name="dont-insert-line-breaks-to-output-except-for-tables-5193"></a><span data-ttu-id="91c87-153">출력에 줄 바꿈을 삽입하지 않음(테이블 제외) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span><span class="sxs-lookup"><span data-stu-id="91c87-153">Don't insert line breaks to output (except for tables) [#5193](https://github.com/PowerShell/PowerShell/issues/5193)</span></span>

<span data-ttu-id="91c87-154">이전에는 출력이 콘솔 너비에 맞게 조정되고 콘솔의 끝 너비에 줄 바꿈이 추가되었으므로 터미널의 크기를 조정할 경우, 출력의 서식이 예상대로 재지정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-154">Previously, output was aligned to the width of the console and line breaks were added at the end width of the console, meaning the output didn't get reformatted as expected if the terminal was resized.</span></span> <span data-ttu-id="91c87-155">열 맞춤 상태를 유지하려면 줄 바꿈이 필요하므로 테이블에는 이 변경 내용이 적용되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-155">This change was not applied to tables, as the line breaks are necessary to keep the columns aligned.</span></span>

### <a name="skip-null-element-check-for-collections-with-a-value-type-element-type-5432"></a><span data-ttu-id="91c87-156">값 형식 요소 유형을 포함하는 컬렉션에 대한 null 요소 검사 건너뜀 [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span><span class="sxs-lookup"><span data-stu-id="91c87-156">Skip null-element check for collections with a value-type element type [#5432](https://github.com/PowerShell/PowerShell/issues/5432)</span></span>

<span data-ttu-id="91c87-157">`Mandatory` 매개 변수와 `ValidateNotNull` 및 `ValidateNotNullOrEmpty` 특성에서, 컬렉션의 요소 유형이 값 형식인 경우 null 요소 검사를 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-157">For the `Mandatory` parameter and `ValidateNotNull` and `ValidateNotNullOrEmpty` attributes, skip the null-element check if the collection's element type is value type.</span></span>

### <a name="change-outputencoding-to-use-utf-8-nobom-encoding-rather-than-ascii-5369"></a><span data-ttu-id="91c87-158">ASCII가 아니라 `UTF-8 NoBOM` 인코딩을 사용하도록 `$OutputEncoding` 변경 [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span><span class="sxs-lookup"><span data-stu-id="91c87-158">Change `$OutputEncoding` to use `UTF-8 NoBOM` encoding rather than ASCII [#5369](https://github.com/PowerShell/PowerShell/issues/5369)</span></span>

<span data-ttu-id="91c87-159">이전 인코딩인 ASCII(7비트)에서는 출력이 잘못 변경되는 경우가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-159">The previous encoding, ASCII (7-bit), would result in incorrect alteration of the output in some cases.</span></span> <span data-ttu-id="91c87-160">이 변경은 `UTF-8 NoBOM`을 기본값으로 설정하기 위한 것으로, 대부분의 도구 및 운영 체제에서 지원되는 인코딩을 사용하여 유니코드 출력을 보존합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-160">This change is to make `UTF-8 NoBOM` default, which preserves Unicode output with an encoding supported by most tools and operating systems.</span></span>

### <a name="remove-allscope-from-most-default-aliases-5268"></a><span data-ttu-id="91c87-161">대부분의 기본 별칭에서 `AllScope` 제거 [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span><span class="sxs-lookup"><span data-stu-id="91c87-161">Remove `AllScope` from most default aliases [#5268](https://github.com/PowerShell/PowerShell/issues/5268)</span></span>

<span data-ttu-id="91c87-162">범위를 빨리 만들 수 있도록 `AllScope`가 대부분의 기본 별칭에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-162">To speed up scope creation, `AllScope` was removed from most default aliases.</span></span> <span data-ttu-id="91c87-163">자주 사용하는 몇 가지 별칭에 대해서는 조회 속도가 더 빠른 `AllScope`가 유지되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-163">`AllScope` was left for a few frequently used aliases where the lookup was faster.</span></span>

### <a name="-verbose-and--debug-no-longer-overrides-erroractionpreference-5113"></a><span data-ttu-id="91c87-164">`-Verbose` 및 `-Debug`가 더 이상 를 재정의하지 않음 `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span><span class="sxs-lookup"><span data-stu-id="91c87-164">`-Verbose` and `-Debug` no longer overrides `$ErrorActionPreference` [#5113](https://github.com/PowerShell/PowerShell/issues/5113)</span></span>

<span data-ttu-id="91c87-165">이전에는 `-Verbose` 또는 `-Debug`가 지정된 경우 `$ErrorActionPreference`의 동작을 재정의했습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-165">Previously, if `-Verbose` or `-Debug` were specified, it overrode the behavior of `$ErrorActionPreference`.</span></span> <span data-ttu-id="91c87-166">이 변경으로, `-Verbose` 및 `-Debug`가 더 이상 `$ErrorActionPreference`의 동작에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-166">With this change, `-Verbose` and `-Debug` no longer affect the behavior of `$ErrorActionPreference`.</span></span>

## <a name="cmdlet-changes"></a><span data-ttu-id="91c87-167">cmdlet 변경 내용</span><span class="sxs-lookup"><span data-stu-id="91c87-167">Cmdlet changes</span></span>

### <a name="invoke-restmethod-doesnt-return-useful-info-when-no-data-is-returned-5320"></a><span data-ttu-id="91c87-168">반환된 데이터가 없을 때 Invoke-RestMethod에서 유용한 정보를 반환하지 않음</span><span class="sxs-lookup"><span data-stu-id="91c87-168">Invoke-RestMethod doesn't return useful info when no data is returned.</span></span> [<span data-ttu-id="91c87-169">#5320</span><span class="sxs-lookup"><span data-stu-id="91c87-169">#5320</span></span>](https://github.com/PowerShell/PowerShell/issues/5320)

<span data-ttu-id="91c87-170">API에서 `null`만 반환하는 경우 Invoke-RestMethod에서 이 값을 `$null`이 아니라 `"null"` 문자열로 직렬화했습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-170">When an API returns just `null`, Invoke-RestMethod was serializing this as the string `"null"` instead of `$null`.</span></span> <span data-ttu-id="91c87-171">이 변경으로, `Invoke-RestMethod`의 논리가 유효한 단일 값 JSON `null` 리터럴을 `$null`로 올바르게 직렬화하도록 수정됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-171">This change fixes the logic in `Invoke-RestMethod` to properly serialize a valid single value JSON `null` literal as `$null`.</span></span>

### <a name="remove--protocol-from--computer-cmdlets-5277"></a><span data-ttu-id="91c87-172">`*-Computer` cmdlet에서 `-Protocol` 제거 [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span><span class="sxs-lookup"><span data-stu-id="91c87-172">Remove `-Protocol` from `*-Computer` cmdlets [#5277](https://github.com/PowerShell/PowerShell/issues/5277)</span></span>

<span data-ttu-id="91c87-173">CoreFX의 RPC 원격 관련 문제로 인해(특히 비 Windows 플랫폼) PowerShell에서 일관성 있는 원격 경험을 보장하기 위해 `-Protocol` 매개 변수가 `\*-Computer` cmdlet에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-173">Due to issues with RPC remoting in CoreFX (particularly on non-Windows platforms) and ensuring a consistent remoting experience in PowerShell, the `-Protocol` parameter was removed from the `\*-Computer` cmdlets.</span></span> <span data-ttu-id="91c87-174">DCOM은 더 이상 원격 작업을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-174">DCOM is no longer supported for remoting.</span></span> <span data-ttu-id="91c87-175">다음 cmdlet은 WSMAN 원격만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-175">The following cmdlets only support WSMAN remoting:</span></span>

- <span data-ttu-id="91c87-176">Rename-Computer</span><span class="sxs-lookup"><span data-stu-id="91c87-176">Rename-Computer</span></span>
- <span data-ttu-id="91c87-177">Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="91c87-177">Restart-Computer</span></span>
- <span data-ttu-id="91c87-178">Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="91c87-178">Stop-Computer</span></span>

### <a name="remove--computername-from--service-cmdlets-5090"></a><span data-ttu-id="91c87-179">`*-Service` cmdlet에서 `-ComputerName` 제거 [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span><span class="sxs-lookup"><span data-stu-id="91c87-179">Remove `-ComputerName` from `*-Service` cmdlets [#5090](https://github.com/PowerShell/PowerShell/issues/5094)</span></span>

<span data-ttu-id="91c87-180">일관성 있는 PSRP 사용을 권장하기 위해 `-ComputerName` 매개 변수가 `*-Service` cmdlet에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-180">In order to encourage the consistent use of PSRP, the `-ComputerName` parameter was removed from `*-Service` cmdlets.</span></span>

### <a name="fix-get-item--literalpath-ab-if-ab-doesnt-actually-exist-to-return-error-5197"></a><span data-ttu-id="91c87-181">`a*b`가 실제로 존재하지 않을 경우 `Get-Item -LiteralPath a*b`에서 오류를 반환하도록 수정 [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span><span class="sxs-lookup"><span data-stu-id="91c87-181">Fix `Get-Item -LiteralPath a*b` if `a*b` doesn't actually exist to return error [#5197](https://github.com/PowerShell/PowerShell/issues/5197)</span></span>

<span data-ttu-id="91c87-182">이전에는 `-LiteralPath`에 와일드카드를 지정할 경우, `-Path`와 동일하게 처리되고, 와일드카드를 통해 파일을 찾지 못할 경우 자동으로 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-182">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="91c87-183">올바른 동작은 파일이 존재하지 않을 경우 오류가 발생하도록 `-LiteralPath`가 리터럴이 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-183">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="91c87-184">`-Literal`과 함께 사용된 와일드카드를 리터럴로 처리하도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-184">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="import-csv-should-apply-pstypenames-upon-import-when-type-information-is-present-in-the-csv-5134"></a><span data-ttu-id="91c87-185">형식 정보가 CSV에 있는 경우 `Import-Csv`에서 가져올 때 `PSTypeNames`를 적용해야 함 [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span><span class="sxs-lookup"><span data-stu-id="91c87-185">`Import-Csv` should apply `PSTypeNames` upon import when type information is present in the CSV [#5134](https://github.com/PowerShell/PowerShell/issues/5134)</span></span>

<span data-ttu-id="91c87-186">이전에는 `ConvertFrom-Csv`를 사용하여 `TypeInformation`을 가져오고, `Export-CSV`를 사용하여 내보낸 개체가 형식 정보를 보존하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-186">Previously, objects exported using `Export-CSV` with `TypeInformation` imported with `ConvertFrom-Csv` were not retaining the type information.</span></span> <span data-ttu-id="91c87-187">이 변경으로, CSV 파일에서 사용 가능한 경우 형식 정보가 `PSTypeNames` 멤버에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-187">This change adds the type information to `PSTypeNames` member if available from the CSV file.</span></span>

### <a name="-notypeinformation-should-be-default-on-export-csv-5131"></a><span data-ttu-id="91c87-188">에서 `-NoTypeInformation`이 기본값이어야 함 `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span><span class="sxs-lookup"><span data-stu-id="91c87-188">`-NoTypeInformation` should be default on `Export-Csv` [#5131](https://github.com/PowerShell/PowerShell/issues/5131)</span></span>

<span data-ttu-id="91c87-189">이 변경은 형식 정보를 포함하는 `Export-CSV`의 기본 동작에 대한 고객 피드백을 반영하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-189">This change was made to address customer feedback on the default behavior of `Export-CSV` to include type information.</span></span>

<span data-ttu-id="91c87-190">이전에는 cmdlet에서 개체의 형식 이름을 포함하는 주석을 첫째 줄로 출력했습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-190">Previously, the cmdlet would output a comment as the first line containing the type name of the object.</span></span> <span data-ttu-id="91c87-191">대부분의 도구에서 인식되지 않으므로 이 주석을 기본적으로 표시하지 않도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-191">The change is to suppress this by default as it's not understood by most tools.</span></span> <span data-ttu-id="91c87-192">이전 동작을 유지하려면 `-IncludeTypeInformation`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-192">Use `-IncludeTypeInformation` to retain the previous behavior.</span></span>

### <a name="web-cmdlets-should-warn-when--credential-is-sent-over-unencrypted-connections-5112"></a><span data-ttu-id="91c87-193">`-Credential`이 암호화되지 않은 연결을 통해 전송될 경우 웹 cmdlet에서 경고해야 함 [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span><span class="sxs-lookup"><span data-stu-id="91c87-193">Web Cmdlets should warn when `-Credential` is sent over unencrypted connections [#5112](https://github.com/PowerShell/PowerShell/issues/5112)</span></span>

<span data-ttu-id="91c87-194">HTTP를 사용하는 경우 암호를 포함하는 콘텐츠가 일반 텍스트로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-194">When using HTTP, content including passwords are sent as clear-text.</span></span> <span data-ttu-id="91c87-195">이 변경은 이 동작을 기본적으로 허용하지 않고 자격 증명이 비보안 방식으로 전달될 경우 오류를 반환하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-195">This change is to not allow this by default and return an error if credentials are being passed in an insecure manner.</span></span> <span data-ttu-id="91c87-196">사용자는 `-AllowUnencryptedAuthentication` 스위치를 사용하여 이 변경을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-196">Users can bypass this by using the `-AllowUnencryptedAuthentication` switch.</span></span>

## <a name="api-changes"></a><span data-ttu-id="91c87-197">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="91c87-197">API changes</span></span>

### <a name="remove-addtypecommandbase-class-5407"></a><span data-ttu-id="91c87-198">`AddTypeCommandBase` 클래스 제거 [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span><span class="sxs-lookup"><span data-stu-id="91c87-198">Remove `AddTypeCommandBase` class [#5407](https://github.com/PowerShell/PowerShell/issues/5407)</span></span>

<span data-ttu-id="91c87-199">성능 향상을 위해 `AddTypeCommandBase` 클래스가 `Add-Type`에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-199">The `AddTypeCommandBase` class was removed from `Add-Type` to improve performance.</span></span> <span data-ttu-id="91c87-200">이 클래스는 Add-Type cmdlet에서만 사용되며 사용자에게 영향을 주면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-200">This class is only used by the Add-Type cmdlet and should not impact users.</span></span>

### <a name="unify-cmdlets-with-parameter--encoding-to-be-of-type-systemtextencoding-5080"></a><span data-ttu-id="91c87-201"> 형식이 되도록 `-Encoding` 매개 변수와 cmdlet 통합 `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span><span class="sxs-lookup"><span data-stu-id="91c87-201">Unify cmdlets with parameter `-Encoding` to be of type `System.Text.Encoding` [#5080](https://github.com/PowerShell/PowerShell/issues/5080)</span></span>

<span data-ttu-id="91c87-202">`-Encoding` 값 `Byte`가 파일 시스템 공급자 cmdlet에서 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-202">The `-Encoding` value `Byte` has been removed from the filesystem provider cmdlets.</span></span> <span data-ttu-id="91c87-203">이제 새 매개 변수 `-AsByteStream`을 사용하여 바이트 스트림이 입력으로 필요한 경우나 출력이 바이트 스트림인 경우를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-203">A new parameter, `-AsByteStream`, is now used to specify that a byte stream is required as input or that the output is a stream of bytes.</span></span>

### <a name="add-better-error-message-for-empty-and-null--uformat-parameter-5055"></a><span data-ttu-id="91c87-204">비어 있는 null `-UFormat` 매개 변수에 대해 더 나은 오류 메시지 추가 [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span><span class="sxs-lookup"><span data-stu-id="91c87-204">Add better error message for empty and null `-UFormat` parameter [#5055](https://github.com/PowerShell/PowerShell/issues/5055)</span></span>

<span data-ttu-id="91c87-205">이전에는 빈 형식 문자열을 `-UFormat`에 전달할 때 도움이 되지 않는 오류 메시지가 표시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-205">Previously, when passing an empty format string to `-UFormat`, an unhelpful error message would appear.</span></span> <span data-ttu-id="91c87-206">더 자세한 설명을 포함하는 오류가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-206">A more descriptive error has been added.</span></span>

### <a name="clean-up-console-code-4995"></a><span data-ttu-id="91c87-207">콘솔 코드 정리 [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span><span class="sxs-lookup"><span data-stu-id="91c87-207">Clean up console code [#4995](https://github.com/PowerShell/PowerShell/issues/4995)</span></span>

<span data-ttu-id="91c87-208">다음 기능은 PowerShell Core에서 지원되지 않아 제거되었으며, Windows PowerShell에 대한 레거시 이유로 존재하기 때문에 지원을 추가할 플랜이 없습니다. `-psconsolefile` 스위치 및 코드, `-importsystemmodules` 스위치 및 코드, 글꼴 변경 코드</span><span class="sxs-lookup"><span data-stu-id="91c87-208">The following features were removed as they are not supported in PowerShell Core, and there are no plans to add support as they exist for legacy reasons for Windows PowerShell: `-psconsolefile` switch and code, `-importsystemmodules` switch and code, and font changing code.</span></span>

### <a name="removed-runspaceconfiguration-support-4942"></a><span data-ttu-id="91c87-209">`RunspaceConfiguration` 지원 제거 [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span><span class="sxs-lookup"><span data-stu-id="91c87-209">Removed `RunspaceConfiguration` support [#4942](https://github.com/PowerShell/PowerShell/issues/4942)</span></span>

<span data-ttu-id="91c87-210">이전에는 API를 사용하여 프로그래밍 방식으로 PowerShell Runspace를 만들 때 레거시 [`RunspaceConfiguration`][runspaceconfig] 또는 최신 [`InitialSessionState`][iss]를 사용할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-210">Previously, when creating a PowerShell runspace programmatically using the API you could use the legacy [`RunspaceConfiguration`][runspaceconfig] or the newer [`InitialSessionState`][iss].</span></span> <span data-ttu-id="91c87-211">이 변경으로, `RunspaceConfiguration` 지원이 제거되었으며 `InitialSessionState`만 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-211">This change removed support for `RunspaceConfiguration` and only supports `InitialSessionState`.</span></span>

[runspaceconfig]: /dotnet/api/system.management.automation.runspaces.runspaceconfiguration
[iss]: /dotnet/api/system.management.automation.runspaces.initialsessionstate

### <a name="commandinvocationintrinsicsinvokescript-bind-arguments-to-input-instead-of-args-4923"></a><span data-ttu-id="91c87-212">`CommandInvocationIntrinsics.InvokeScript`에서 인수를 가 아니라 `$input`에 바인딩함 `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span><span class="sxs-lookup"><span data-stu-id="91c87-212">`CommandInvocationIntrinsics.InvokeScript` bind arguments to `$input` instead of `$args` [#4923](https://github.com/PowerShell/PowerShell/issues/4923)</span></span>

<span data-ttu-id="91c87-213">잘못된 매개 변수 위치로 인해 인수가 아니라 입력으로 인수가 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-213">An incorrect position of a parameter resulted in the args passed as input instead of as args.</span></span>

### <a name="remove-unsupported--showwindow-switch-from-get-help-4903"></a><span data-ttu-id="91c87-214">에서 지원되지 않는 `-showwindow` 스위치 제거 `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span><span class="sxs-lookup"><span data-stu-id="91c87-214">Remove unsupported `-showwindow` switch from `Get-Help` [#4903](https://github.com/PowerShell/PowerShell/issues/4903)</span></span>

<span data-ttu-id="91c87-215">`-showwindow`는 CoreCLR에서 지원되지 않는 WPF를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-215">`-showwindow` relies on WPF, which is not supported on CoreCLR.</span></span>

### <a name="allow--to-be-used-in-registry-path-for-remove-item-4866"></a><span data-ttu-id="91c87-216">의 레지스트리 경로에 \*를 사용할 수 있도록 허용 `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span><span class="sxs-lookup"><span data-stu-id="91c87-216">Allow \* to be used in registry path for `Remove-Item` [#4866](https://github.com/PowerShell/PowerShell/issues/4866)</span></span>

<span data-ttu-id="91c87-217">이전에는 `-LiteralPath`에 와일드카드를 지정할 경우, `-Path`와 동일하게 처리되고, 와일드카드를 통해 파일을 찾지 못할 경우 자동으로 종료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-217">Previously, `-LiteralPath` given a wildcard would treat it the same as `-Path` and if the wildcard found no files, it would silently exit.</span></span> <span data-ttu-id="91c87-218">올바른 동작은 파일이 존재하지 않을 경우 오류가 발생하도록 `-LiteralPath`가 리터럴이 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-218">Correct behavior should be that `-LiteralPath` is literal so if the file doesn't exist, it should error.</span></span> <span data-ttu-id="91c87-219">`-Literal`과 함께 사용된 와일드카드를 리터럴로 처리하도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-219">Change is to treat wildcards used with `-Literal` as literal.</span></span>

### <a name="fix-set-service-failing-test-4802"></a><span data-ttu-id="91c87-220">`Set-Service` 실패 테스트 수정 [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span><span class="sxs-lookup"><span data-stu-id="91c87-220">Fix `Set-Service` failing test [#4802](https://github.com/PowerShell/PowerShell/issues/4802)</span></span>

<span data-ttu-id="91c87-221">이전에는 `New-Service -StartupType foo`를 사용할 경우, `foo`가 무시되고 기본 시작 유형으로 서비스가 생성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-221">Previously, if `New-Service -StartupType foo` was used, `foo` was ignored and the service was created with some default startup type.</span></span> <span data-ttu-id="91c87-222">이 변경은 잘못된 시작 유형에 대해 명시적으로 오류를 throw하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-222">This change is to explicitly throw an error for an invalid startup type.</span></span>

### <a name="rename-isosx-to-ismacos-4700"></a><span data-ttu-id="91c87-223">`$IsOSX`의 이름을 로 바꿈 `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span><span class="sxs-lookup"><span data-stu-id="91c87-223">Rename `$IsOSX` to `$IsMacOS` [#4700](https://github.com/PowerShell/PowerShell/issues/4700)</span></span>

<span data-ttu-id="91c87-224">PowerShell의 이름 지정은 Microsoft의 이름 지정과 일치하는 동시에 OSX가 아니라 Apple의 macOS 사용을 준수해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-224">The naming in PowerShell should be consistent with our naming and conform to Apple's use of macOS instead of OSX.</span></span> <span data-ttu-id="91c87-225">그러나 가독성과 일관성을 위해 파스칼식 대/소문자를 유지하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-225">However, for readability and consistently we are staying with Pascal casing.</span></span>

### <a name="make-error-message-consistent-when-invalid-script-is-passed-to--file-better-error-when-passed-ambiguous-argument-4573"></a><span data-ttu-id="91c87-226">잘못된 스크립트가 -File에 전달될 경우 일관성 있는 오류 메시지 작성, 모호한 인수가 전달될 경우 더 나은 오류 작성 [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span><span class="sxs-lookup"><span data-stu-id="91c87-226">Make error message consistent when invalid script is passed to -File, better error when passed ambiguous argument [#4573](https://github.com/PowerShell/PowerShell/issues/4573)</span></span>

<span data-ttu-id="91c87-227">Unix 규칙에 맞게 `pwsh.exe`의 종료 코드 변경</span><span class="sxs-lookup"><span data-stu-id="91c87-227">Change the exit codes of `pwsh.exe` to align with Unix conventions</span></span>

### <a name="removal-of-localaccount-and-cmdlets-from--diagnostics-modules-4302-4303"></a><span data-ttu-id="91c87-228">`Diagnostics` 모듈의 cmdlet 및 `LocalAccount` 제거</span><span class="sxs-lookup"><span data-stu-id="91c87-228">Removal of `LocalAccount` and cmdlets from  `Diagnostics` modules.</span></span> <span data-ttu-id="91c87-229">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span><span class="sxs-lookup"><span data-stu-id="91c87-229">[#4302](https://github.com/PowerShell/PowerShell/issues/4302) [#4303](https://github.com/PowerShell/PowerShell/issues/4303)</span></span>

<span data-ttu-id="91c87-230">지원되지 않는 API 때문에 `Diagnostics` 모듈의 `Counter` cmdlet 및 `LocalAccounts` 모듈이 더 나은 해결 방법을 찾을 때까지 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-230">Due to unsupported APIs, the `LocalAccounts` module and the `Counter` cmdlets in the `Diagnostics` module were removed until a better solution is found.</span></span>

### <a name="executing-powershell-script-with-bool-parameter-does-not-work-4036"></a><span data-ttu-id="91c87-231">부울 매개 변수를 포함한 PowerShell 스크립트를 실행할 경우 작동하지 않음 [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span><span class="sxs-lookup"><span data-stu-id="91c87-231">Executing PowerShell script with bool parameter does not work [#4036](https://github.com/PowerShell/PowerShell/issues/4036)</span></span>

<span data-ttu-id="91c87-232">이전에는 **powershell.exe**(현재 **pwsh.exe**)를 사용하여 `-File`을 사용하는 PowerShell 스크립트를 실행할 경우 `$true`/`$false`를 매개 변수 값으로 전달할 수 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-232">Previously, using **powershell.exe** (now **pwsh.exe**) to execute a PowerShell script using `-File` provided no way to pass `$true`/`$false` as parameter values.</span></span> <span data-ttu-id="91c87-233">매개 변수에 대한 구문 분석된 값으로 `$true`/`$false` 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-233">Support for `$true`/`$false` as parsed values to parameters was added.</span></span> <span data-ttu-id="91c87-234">현재 문서화된 구문이 작동하지 않으므로 스위치 값도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-234">Switch values are also supported as currently documented syntax doesn't work.</span></span>

### <a name="remove-clrversion-property-from-psversiontable-4027"></a><span data-ttu-id="91c87-235">에서 `ClrVersion` 속성 제거 `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span><span class="sxs-lookup"><span data-stu-id="91c87-235">Remove `ClrVersion` property from `$PSVersionTable` [#4027](https://github.com/PowerShell/PowerShell/issues/4027)</span></span>

<span data-ttu-id="91c87-236">`$PSVersionTable`의 `ClrVersion` 속성은 CoreCLR에서 유용하지 않습니다. 최종 사용자는 호환성을 확인하기 위해 이 값을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-236">The `ClrVersion` property of `$PSVersionTable` is not useful with CoreCLR, end users should not be using that value to determine compatibility.</span></span>

### <a name="change-positional-parameter-for-powershellexe-from--command-to--file-4019"></a><span data-ttu-id="91c87-237">`powershell.exe`에 대한 위치 지정 매개 변수를 `-Command`에서 로 변경 `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span><span class="sxs-lookup"><span data-stu-id="91c87-237">Change positional parameter for `powershell.exe` from `-Command` to `-File` [#4019](https://github.com/PowerShell/PowerShell/issues/4019)</span></span>

<span data-ttu-id="91c87-238">비 Windows 플랫폼에서 PowerShell의 구조를 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-238">Enable shebang use of PowerShell on non-Windows platforms.</span></span> <span data-ttu-id="91c87-239">즉, Unix 기반 시스템에서 `pwsh`를 명시적으로 호출하지 않고 PowerShell을 자동으로 호출하는 스크립트 실행 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-239">This means on Unix based systems, you can make a script executable that would invoke PowerShell automatically rather than explicitly invoking `pwsh`.</span></span> <span data-ttu-id="91c87-240">이제 `-File`을 지정하지 않고 `powershell foo.ps1` 또는 `powershell fooScript`와 같은 작업을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-240">This also means that you can now do things like `powershell foo.ps1` or `powershell fooScript` without specifying `-File`.</span></span> <span data-ttu-id="91c87-241">그러나 이 변경으로, 이제 `powershell.exe Get-Command`와 같은 작업을 수행할 때 `-c` 또는 `-Command`를 명시적으로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-241">However, this change now requires that you explicitly specify `-c` or `-Command` when trying to do things like `powershell.exe Get-Command`.</span></span>

### <a name="implement-unicode-escape-parsing-3958"></a><span data-ttu-id="91c87-242">유니코드 이스케이프 구문 분석 구현 [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span><span class="sxs-lookup"><span data-stu-id="91c87-242">Implement Unicode escape parsing [#3958](https://github.com/PowerShell/PowerShell/issues/3958)</span></span>

<span data-ttu-id="91c87-243">`` `u####`` 또는 `` `u{####}``이 해당 유니코드 문자로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-243">`` `u####`` or `` `u{####}`` is converted to the corresponding Unicode character.</span></span> <span data-ttu-id="91c87-244">리터럴 `` `u``를 출력하려면 backtick을 이스케이프합니다(``` ``u```).</span><span class="sxs-lookup"><span data-stu-id="91c87-244">To output a literal `` `u``, escape the backtick: ``` ``u```.</span></span>

### <a name="change-new-modulemanifest-encoding-to-utf8nobom-on-non-windows-platforms-3940"></a><span data-ttu-id="91c87-245">비 Windows 플랫폼에서 `New-ModuleManifest` 인코딩을 `UTF8NoBOM`으로 변경 [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span><span class="sxs-lookup"><span data-stu-id="91c87-245">Change `New-ModuleManifest` encoding to `UTF8NoBOM` on non-Windows platforms [#3940](https://github.com/PowerShell/PowerShell/issues/3940)</span></span>

<span data-ttu-id="91c87-246">이전에는 `New-ModuleManifest`에서 BOM을 포함하는 UTF-16으로 psd1 매니페스트를 만들어 Linux 도구에서 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-246">Previously, `New-ModuleManifest` creates psd1 manifests in UTF-16 with BOM, creating a problem for Linux tools.</span></span> <span data-ttu-id="91c87-247">호환성이 손상되는 이 변경으로, 비 Windows 플랫폼에서 `New-ModuleManifest`의 인코딩이 UTF(BOM 없음)로 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-247">This breaking change changes the encoding of `New-ModuleManifest` to be UTF (no BOM) in non-Windows platforms.</span></span>

### <a name="prevent-get-childitem-from-recursing-into-symlinks-1875-3780"></a><span data-ttu-id="91c87-248">`Get-ChildItem`이 바로 가기 링크로 재귀되지 않도록 방지 (#1875)</span><span class="sxs-lookup"><span data-stu-id="91c87-248">Prevent `Get-ChildItem` from recursing into symlinks (#1875).</span></span> [<span data-ttu-id="91c87-249">#3780</span><span class="sxs-lookup"><span data-stu-id="91c87-249">#3780</span></span>](https://github.com/PowerShell/PowerShell/issues/3780)

<span data-ttu-id="91c87-250">이 변경으로, `Get-ChildItem`이 Unix `ls -r` 및 Windows `dir /s` 네이티브 명령과 더 일치하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-250">This change brings `Get-ChildItem` more in line with the Unix `ls -r` and the Windows `dir /s` native commands.</span></span> <span data-ttu-id="91c87-251">언급한 명령과 유사하게, 이 cmdlet은 재귀되는 동안 찾은 디렉터리에 대한 바로 가기 링크를 표시하지만 해당 디렉터리로 재귀되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-251">Like the mentioned commands, the cmdlet displays symbolic links to directories found during recursion, but does not recurse into them.</span></span>

### <a name="fix-get-content--delimiter-to-not-include-the-delimiter-in-the-returned-lines-3706"></a><span data-ttu-id="91c87-252">반환된 줄에 구분 기호를 포함하지 않도록 `Get-Content -Delimiter` 수정 [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span><span class="sxs-lookup"><span data-stu-id="91c87-252">Fix `Get-Content -Delimiter` to not include the delimiter in the returned lines [#3706](https://github.com/PowerShell/PowerShell/issues/3706)</span></span>

<span data-ttu-id="91c87-253">이전에는 `Get-Content -Delimiter`를 사용하여 생성된 출력에서 구분 기호를 제거하기 위해 데이터를 추가로 처리해야 했기 때문에 불편하고 일관성이 없었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-253">Previously, the output while using `Get-Content -Delimiter` was inconsistent and inconvenient as it required further processing of the data to remove the delimiter.</span></span> <span data-ttu-id="91c87-254">이 변경으로, 반환된 줄에서 구분 기호가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-254">This change removes the delimiter in returned lines.</span></span>

### <a name="implement-format-hex-in-c-3320"></a><span data-ttu-id="91c87-255">C#에서 Format-Hex 구현 [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span><span class="sxs-lookup"><span data-stu-id="91c87-255">Implement Format-Hex in C# [#3320](https://github.com/PowerShell/PowerShell/issues/3320)</span></span>

<span data-ttu-id="91c87-256">이제 `-Raw` 매개 변수가 “no-op”(아무 작업도 안 함)입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-256">The `-Raw` parameter is now a "no-op" (in that it does nothing).</span></span> <span data-ttu-id="91c87-257">앞으로는 모든 출력이 해당 형식의 모든 바이트를 포함하는 숫자 표현으로 표시됩니다(이 변경 이전에는 `-Raw` 매개 변수가 공식적으로 수행한 작업).</span><span class="sxs-lookup"><span data-stu-id="91c87-257">Going forward all of the output will be displayed with a true representation of numbers that includes all of the bytes for its type (what the `-Raw` parameter was formally doing prior to this change).</span></span>

### <a name="powershell-as-a-default-shell-doesnt-work-with-script-command-3319"></a><span data-ttu-id="91c87-258">기본 셸인 PowerShell이 스크립트 명령에서 작동하지 않음 [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span><span class="sxs-lookup"><span data-stu-id="91c87-258">PowerShell as a default shell doesn't work with script command [#3319](https://github.com/PowerShell/PowerShell/issues/3319)</span></span>

<span data-ttu-id="91c87-259">Unix에서는 셸이 대화형 셸을 나타내는 `-i`를 허용하는 것이 규칙이며, 많은 도구가 이 동작을 기대하고(예를 들어, PowerShell을 기본 셸로 설정하는 경우 `script`) `-i` 스위치로 셸을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-259">On Unix, it is a convention for shells to accept `-i` for an interactive shell and many tools expect this behavior (`script` for example, and when setting PowerShell as the default shell) and calls the shell with the `-i` switch.</span></span> <span data-ttu-id="91c87-260">이전에는 `-i`를 `-inputformat`의 약식으로 사용할 수 있었다는 점에서 이 변경으로 호환성이 손상됩니다. 이제 `-in`을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-260">This change is breaking in that `-i` previously could be used as short hand to match `-inputformat`, which now needs to be `-in`.</span></span>

### <a name="typo-fix-in-get-computerinfo-property-name-3167"></a><span data-ttu-id="91c87-261">Get-ComputerInfo 속성 이름의 오타 수정 [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span><span class="sxs-lookup"><span data-stu-id="91c87-261">Typo fix in Get-ComputerInfo property name [#3167](https://github.com/PowerShell/PowerShell/issues/3167)</span></span>

<span data-ttu-id="91c87-262">`BiosSerialNumber`가 `BiosSeralNumber`로 잘못 표기되었으며 올바른 맞춤법으로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-262">`BiosSerialNumber` was misspelled as `BiosSeralNumber` and has been changed to the correct spelling.</span></span>

### <a name="add-get-stringhash-and-get-filehash-cmdlets-3024"></a><span data-ttu-id="91c87-263">`Get-StringHash` 및 `Get-FileHash` cmdlet 추가 [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span><span class="sxs-lookup"><span data-stu-id="91c87-263">Add `Get-StringHash` and `Get-FileHash` cmdlets [#3024](https://github.com/PowerShell/PowerShell/issues/3024)</span></span>

<span data-ttu-id="91c87-264">이 변경은 일부 해시 알고리즘이 CoreFX에서 지원되지 않아 더 이상 사용할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-264">This change is that some hash algorithms are not supported by CoreFX, therefore they are no longer available:</span></span>

- `MACTripleDES`
- `RIPEMD160`

### <a name="add-validation-on-get--cmdlets-where-passing-null-returns-all-objects-instead-of-error-2672"></a><span data-ttu-id="91c87-265">$null을 전달할 때 오류가 아니라 모든 개체가 반환되는, `Get-*` cmdlet에 대한 유효성 검사 추가 [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span><span class="sxs-lookup"><span data-stu-id="91c87-265">Add validation on `Get-*` cmdlets where passing $null returns all objects instead of error [#2672](https://github.com/PowerShell/PowerShell/issues/2672)</span></span>

<span data-ttu-id="91c87-266">다음 중 하나에 `$null`을 전달하면 이제 오류가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-266">Passing `$null` to any of the following now throws an error:</span></span>

- `Get-Credential -UserName`
- `Get-Event -SourceIdentifier`
- `Get-EventSubscriber -SourceIdentifier`
- `Get-Help -Name`
- `Get-PSBreakpoint -Script`
- `Get-PSProvider -PSProvider`
- `Get-PSSessionConfiguration -Name`
- `Get-PSSnapin -Name`
- `Get-Runspace -Name`
- `Get-RunspaceDebug -RunspaceName`
- `Get-Service -Name`
- `Get-TraceSource -Name`
- `Get-Variable -Name`
- `Get-WmiObject -Class`
- `Get-WmiObject -Property`

### <a name="add-support-w3c-extended-log-file-format-in-import-csv-2482"></a><span data-ttu-id="91c87-267">에서 W3C 확장 로그 파일 형식 지원 추가 `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span><span class="sxs-lookup"><span data-stu-id="91c87-267">Add support W3C Extended Log File Format in `Import-Csv` [#2482](https://github.com/PowerShell/PowerShell/issues/2482)</span></span>

<span data-ttu-id="91c87-268">이전에는 `Import-Csv` cmdlet을 사용하여 W3C 확장 로그 형식의 로그 파일을 직접 가져올 수 없었으며, 추가 작업이 필요했습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-268">Previously, the `Import-Csv` cmdlet cannot be used to directly import the log files in W3C extended log format and additional action would be required.</span></span> <span data-ttu-id="91c87-269">이 변경으로, W3C 확장 로그 형식이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-269">With this change, W3C extended log format is supported.</span></span>

### <a name="parameter-binding-problem-with-valuefromremainingarguments-in-ps-functions-2035"></a><span data-ttu-id="91c87-270">PS 함수에서 `ValueFromRemainingArguments`의 매개 변수 바인딩 문제 [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span><span class="sxs-lookup"><span data-stu-id="91c87-270">Parameter binding problem with `ValueFromRemainingArguments` in PS functions [#2035](https://github.com/PowerShell/PowerShell/issues/2035)</span></span>

<span data-ttu-id="91c87-271">이제 `ValueFromRemainingArguments`에서 그 자체가 배열인 단일 값이 아니라 배열로 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-271">`ValueFromRemainingArguments` now returns the values as an array instead of a single value which itself is an array.</span></span>

### <a name="buildversion-is-removed-from-psversiontable-1415"></a><span data-ttu-id="91c87-272">에서 `BuildVersion` 제거 `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span><span class="sxs-lookup"><span data-stu-id="91c87-272">`BuildVersion` is removed from `$PSVersionTable` [#1415](https://github.com/PowerShell/PowerShell/issues/1415)</span></span>

<span data-ttu-id="91c87-273">`$PSVersionTable`에서 `BuildVersion` 속성이 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-273">Remove the `BuildVersion` property from `$PSVersionTable`.</span></span> <span data-ttu-id="91c87-274">이 속성은 Windows 빌드 버전에 연결되어 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-274">This property was tied to the Windows build version.</span></span> <span data-ttu-id="91c87-275">대신 `GitCommitId`를 사용하여 PowerShell Core의 정확한 빌드 버전을 검색하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-275">Instead, we recommend that you use `GitCommitId` to retrieve the exact build version of PowerShell Core.</span></span>

### <a name="changes-to-web-cmdlets"></a><span data-ttu-id="91c87-276">웹 cmdlet 변경 내용</span><span class="sxs-lookup"><span data-stu-id="91c87-276">Changes to Web Cmdlets</span></span>

<span data-ttu-id="91c87-277">웹 cmdlet의 기본 .NET API가 `System.Net.Http.HttpClient`로 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-277">The underlying .NET API of the Web Cmdlets has been changed to `System.Net.Http.HttpClient`.</span></span> <span data-ttu-id="91c87-278">이 변경은 많은 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-278">This change provides many benefits.</span></span> <span data-ttu-id="91c87-279">그러나 Internet Explorer와의 상호 운용성이 없다는 점과 결부되어, 이 변경으로 인해 `Invoke-WebRequest` 및 `Invoke-RestMethod` 내에서 호환성이 손상되는 여러 가지 변경이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-279">However, this change along with a lack of interoperability with Internet Explorer have resulted in several breaking changes within `Invoke-WebRequest` and `Invoke-RestMethod`.</span></span>

- <span data-ttu-id="91c87-280">이제 `Invoke-WebRequest`에서 기본 HTML 구문 분석만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-280">`Invoke-WebRequest` now supports basic HTML Parsing only.</span></span> <span data-ttu-id="91c87-281">`Invoke-WebRequest`는 항상 `BasicHtmlWebResponseObject` 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-281">`Invoke-WebRequest` always returns a `BasicHtmlWebResponseObject` object.</span></span> <span data-ttu-id="91c87-282">`ParsedHtml` 및 `Forms` 속성이 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-282">The `ParsedHtml` and `Forms` properties have been removed.</span></span>
- <span data-ttu-id="91c87-283">이제 `BasicHtmlWebResponseObject.Headers` 값이 `String`이 아니라 `String[]`입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-283">`BasicHtmlWebResponseObject.Headers` values are now `String[]` instead of `String`.</span></span>
- <span data-ttu-id="91c87-284">이제 `BasicHtmlWebResponseObject.BaseResponse`가 `System.Net.Http.HttpResponseMessage` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-284">`BasicHtmlWebResponseObject.BaseResponse` is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="91c87-285">이제 웹 cmdlet 예외의 `Response` 속성이 `System.Net.Http.HttpResponseMessage` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-285">The `Response` property on Web Cmdlet exceptions is now a `System.Net.Http.HttpResponseMessage` object.</span></span>
- <span data-ttu-id="91c87-286">이제 엄격한 RFC 헤더 구문 분석이 `-Headers` 및 `-UserAgent` 매개 변수의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-286">Strict RFC header parsing is now default for the `-Headers` and `-UserAgent` parameter.</span></span> <span data-ttu-id="91c87-287">이 설정은 `-SkipHeaderValidation`을 사용하여 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-287">This can be bypassed with `-SkipHeaderValidation`.</span></span>
- <span data-ttu-id="91c87-288">`file://` 및 `ftp://` URI 체계가 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-288">`file://` and `ftp://` URI schemes are no longer supported.</span></span>
- <span data-ttu-id="91c87-289">`System.Net.ServicePointManager` 설정이 더 이상 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-289">`System.Net.ServicePointManager` settings are no longer honored.</span></span>
- <span data-ttu-id="91c87-290">현재 macOS에서 사용할 수 있는 인증서 기반 인증은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-290">There is currently no certificate based authentication available on macOS.</span></span>
- <span data-ttu-id="91c87-291">`http://` URI를 통해 `-Credential`을 사용하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-291">Use of `-Credential` over an `http://` URI will result in an error.</span></span> <span data-ttu-id="91c87-292">오류를 표시하지 않으려면 `https://` URI를 사용하거나 `-AllowUnencryptedAuthentication` 매개 변수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-292">Use an `https://` URI or supply the `-AllowUnencryptedAuthentication` parameter to suppress the error.</span></span>
- <span data-ttu-id="91c87-293">`-MaximumRedirection`은 이제 리디렉션이 마지막 리디렉션 결과를 반환하는 대신 제공된 제한을 초과하는 경우 종료 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-293">`-MaximumRedirection` now produces a terminating error when redirection attempts exceed the provided limit instead of returning the results of the last redirection.</span></span>
- <span data-ttu-id="91c87-294">PowerShell 6.2에서는 JSON 응답을 위해 UTF-8 인코딩으로 기본 변경 내용이 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-294">In PowerShell 6.2, a change was made to default to UTF-8 encoding for JSON responses.</span></span> <span data-ttu-id="91c87-295">JSON 응답에 대해 문자 집합이 제공되지 않으면 RFC 8259에 따라 기본 인코딩이 UTF-8이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="91c87-295">When a charset is not supplied for a JSON response, the default encoding should be UTF-8 per RFC 8259.</span></span>
