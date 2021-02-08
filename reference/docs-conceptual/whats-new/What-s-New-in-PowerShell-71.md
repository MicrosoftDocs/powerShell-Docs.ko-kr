---
title: PowerShell 7.1의 새로운 기능
description: PowerShell 7.1에서 릴리스된 새로운 기능 및 변경 내용
ms.date: 12/15/2020
ms.openlocfilehash: 6bbeccd07dd696ee019828bdcd68ce3f6ee627e3
ms.sourcegitcommit: 1628fd2a1f50aec2f31ffb1c451a3ce77c08983c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97577210"
---
# <a name="whats-new-in-powershell-71"></a><span data-ttu-id="fa7a5-103">PowerShell 7.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="fa7a5-103">What's New in PowerShell 7.1</span></span>

<span data-ttu-id="fa7a5-104">2020년 11월 11일에 PowerShell 7.1의 일반 공급을 [발표](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/)했습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-104">On November 11, 2020 we [announced](https://devblogs.microsoft.com/powershell/announcing-powershell-7-1/) the general availability of PowerShell 7.1.</span></span> <span data-ttu-id="fa7a5-105">PowerShell 7.0에 구축된 토대를 기반으로 하여 커뮤니티에서 보고된 문제에 초점을 맞춘 노력을 통해 다수의 개선 사항 및 수정 사항을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-105">Building on the foundation established in PowerShell 7.0, our efforts focused on community issues and include a number of improvements and fixes.</span></span> <span data-ttu-id="fa7a5-106">Microsoft에서는 PowerShell을 안정적이고 성능이 뛰어난 플랫폼으로 유지하기 위해 최선을 다하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-106">We are committed to ensuring that PowerShell remains a stable and performant platform.</span></span>

<span data-ttu-id="fa7a5-107">PowerShell 7.1에는 다음과 같은 기능, 업데이트, 호환성이 손상되는 변경이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-107">PowerShell 7.1 includes the following features, updates, and breaking changes.</span></span>

- <span data-ttu-id="fa7a5-108">예측 IntelliSense를 포함하는 PSReadLine 2.1.0</span><span class="sxs-lookup"><span data-stu-id="fa7a5-108">PSReadLine 2.1.0, which includes Predictive IntelliSense</span></span>
- <span data-ttu-id="fa7a5-109">PowerShell 7.1이 Microsoft Store에 게시됨</span><span class="sxs-lookup"><span data-stu-id="fa7a5-109">PowerShell 7.1 has been published to the Microsoft Store</span></span>
- <span data-ttu-id="fa7a5-110">ARM64 지원과 함께 새 OS 버전용으로 업데이트된 설치 프로그램 패키지</span><span class="sxs-lookup"><span data-stu-id="fa7a5-110">Installer packages updated for new OS versions with support for ARM64</span></span>
- <span data-ttu-id="fa7a5-111">4개의 새로운 실험적 기능 및 2개의 실험적 기능이 기본 기능으로 승격됨</span><span class="sxs-lookup"><span data-stu-id="fa7a5-111">4 new experimental features and 2 experimental features promoted to mainstream</span></span>
- <span data-ttu-id="fa7a5-112">유용성 향상을 위한 몇 가지 호환성이 손상되는 변경</span><span class="sxs-lookup"><span data-stu-id="fa7a5-112">Several breaking changes to improve usability</span></span>

<span data-ttu-id="fa7a5-113">전체 변경 내용 목록은 GitHub 리포지토리에서 [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-113">For a complete list of changes, see the [CHANGELOG](https://github.com/PowerShell/PowerShell/blob/master/CHANGELOG/7.1.md) in the GitHub repository.</span></span>

## <a name="psreadline-210"></a><span data-ttu-id="fa7a5-114">PSReadLine 2.1.0</span><span class="sxs-lookup"><span data-stu-id="fa7a5-114">PSReadLine 2.1.0</span></span>

<span data-ttu-id="fa7a5-115">PowerShell 7.1에는 PSReadLine 2.1.0도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-115">PowerShell 7.1 also include PSReadLine 2.1.0.</span></span> <span data-ttu-id="fa7a5-116">이 버전은 예측 IntelliSense를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-116">This version includes Predictive IntelliSense.</span></span> <span data-ttu-id="fa7a5-117">예측 IntelliSense 기능에 대한 자세한 내용은 PowerShell 블로그의 [공지](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-117">For more information about the Predictive IntelliSense feature, see the [announcement](https://devblogs.microsoft.com/powershell/announcing-psreadline-2-1-with-predictive-intellisense/) in the PowerShell blog.</span></span>

## <a name="microsoft-store-installer-package"></a><span data-ttu-id="fa7a5-118">Microsoft Store 설치 프로그램 패키지</span><span class="sxs-lookup"><span data-stu-id="fa7a5-118">Microsoft Store installer package</span></span>

<span data-ttu-id="fa7a5-119">PowerShell 7.1이 Microsoft Store에 게시되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-119">PowerShell 7.1 has been published to the Microsoft Store.</span></span> <span data-ttu-id="fa7a5-120">이 PowerShell 릴리스는 [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) 웹 사이트 또는 Windows의 Microsoft Store 애플리케이션에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-120">You can find the PowerShell release on the [Microsoft Store](https://www.microsoft.com/store/apps/9MZ1SNWT0N5D) website or in the Store application in Windows.</span></span>

<span data-ttu-id="fa7a5-121">Microsoft Store 패키지의 이점:</span><span class="sxs-lookup"><span data-stu-id="fa7a5-121">Benefits of the Microsoft Store package:</span></span>

- <span data-ttu-id="fa7a5-122">Windows 10에 바로 기본 제공되는 자동 업데이트</span><span class="sxs-lookup"><span data-stu-id="fa7a5-122">Automatic updates built right into Windows 10</span></span>
- <span data-ttu-id="fa7a5-123">Intune 및 SCCM과 같은 기타 소프트웨어 배포 메커니즘과 통합</span><span class="sxs-lookup"><span data-stu-id="fa7a5-123">Integrates with other software distribution mechanisms like Intune and SCCM</span></span>

> [!NOTE]
> <span data-ttu-id="fa7a5-124">`$PSHOME`에 저장된 시스템 수준 구성 설정은 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-124">Any system-level configuration settings stored in `$PSHOME` cannot be modified.</span></span> <span data-ttu-id="fa7a5-125">여기에는 WSMAN 구성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-125">This includes the WSMAN configuration.</span></span> <span data-ttu-id="fa7a5-126">그러므로 원격 세션에서 PowerShell의 저장소 기반 설치에 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-126">This prevents remote sessions from connecting to Store-based installs of PowerShell.</span></span> <span data-ttu-id="fa7a5-127">사용자 수준 구성 및 SSH 원격 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-127">User-level configurations and SSH remoting are supported.</span></span>

## <a name="other-installers"></a><span data-ttu-id="fa7a5-128">다른 설치 프로그램</span><span class="sxs-lookup"><span data-stu-id="fa7a5-128">Other installers</span></span>

<span data-ttu-id="fa7a5-129">지원되는 운영 체제 및 지원 주기에 대한 최신 정보는 [PowerShell 지원 수명 주기](/powershell/scripting/powershell-support-lifecycle)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-129">For more up-to-date information about supported operating systems and support lifecycle, see the [PowerShell Support Lifecycle](/powershell/scripting/powershell-support-lifecycle).</span></span>

<span data-ttu-id="fa7a5-130">기본 운영 체제에 대한 설치 지침을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-130">Check the installation instructions for your preferred operating system:</span></span>

- [<span data-ttu-id="fa7a5-131">Windows</span><span class="sxs-lookup"><span data-stu-id="fa7a5-131">Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows)
- [<span data-ttu-id="fa7a5-132">macOS</span><span class="sxs-lookup"><span data-stu-id="fa7a5-132">macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos)
- [<span data-ttu-id="fa7a5-133">Linux</span><span class="sxs-lookup"><span data-stu-id="fa7a5-133">Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux)

<span data-ttu-id="fa7a5-134">또한 PowerShell 7.1은 Debian, Ubuntu 및 ARM64 Alpine Linux의 ARM32 및 ARM64 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-134">Additionally, PowerShell 7.1 supports ARM32 and ARM64 flavors of Debian, Ubuntu, and ARM64 Alpine Linux.</span></span>

<span data-ttu-id="fa7a5-135">공식적으로 지원되는 것은 아니지만 커뮤니티는 [Arch](https://aur.archlinux.org/packages/powershell/) 및 Kali Linux에 대한 패키지도 제공했습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-135">While not officially supported, the community has also provided packages for [Arch](https://aur.archlinux.org/packages/powershell/) and Kali Linux.</span></span>

> [!NOTE]
> <span data-ttu-id="fa7a5-136">Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine, ARM은 현재 WinRM 원격 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-136">Debian 10+, CentOS 8+, Ubuntu 20.04, Alpine and Arm currently do not support WinRM remoting.</span></span> <span data-ttu-id="fa7a5-137">SSH 기반 원격을 설정하는 방법에 대한 자세한 내용은 [SSH를 통한 PowerShell 원격](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-137">For details on setting up SSH-based remoting, see [PowerShell Remoting over SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).</span></span>

## <a name="experimental-features"></a><span data-ttu-id="fa7a5-138">실험적 기능</span><span class="sxs-lookup"><span data-stu-id="fa7a5-138">Experimental Features</span></span>

<span data-ttu-id="fa7a5-139">실험적 기능에 대한 자세한 내용은 [실험적 기능 사용](../learn/experimental-features.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-139">For more information about the Experimental Features, see [Using Experimental Features](../learn/experimental-features.md).</span></span>

<span data-ttu-id="fa7a5-140">이제 이 릴리스에서는 다음과 같은 실험적 기능이 기본 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-140">The following experimental features are now mainstream features in this release:</span></span>

- [<span data-ttu-id="fa7a5-141">PSNullConditionalOperators</span><span class="sxs-lookup"><span data-stu-id="fa7a5-141">PSNullConditionalOperators</span></span>](../learn/experimental-features.md#psnullconditionaloperators)
- [<span data-ttu-id="fa7a5-142">PSUnixFileStat</span><span class="sxs-lookup"><span data-stu-id="fa7a5-142">PSUnixFileStat</span></span>](../learn/experimental-features.md#psunixfilestat)

<span data-ttu-id="fa7a5-143">이 릴리스에는 다음과 같은 실험적 기능이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-143">The following experimental features were added in this release:</span></span>

- [<span data-ttu-id="fa7a5-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span><span class="sxs-lookup"><span data-stu-id="fa7a5-144">Microsoft.PowerShell.Utility.PSManageBreakpointsInRunspace</span></span>](../learn/experimental-features.md#microsoftpowershellutilitypsmanagebreakpointsinrunspace)
  - <span data-ttu-id="fa7a5-145">PowerShell 7.1은 이 실험적 기능을 확장하여 **Runspace** 매개 변수를 모든 `*-PSBreakpoint` cmdlet에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-145">PowerShell 7.1 extends this experimental feature to add the **Runspace** parameter to all `*-PSBreakpoint` cmdlets.</span></span> <span data-ttu-id="fa7a5-146">**Runspace** 매개 변수는 지정된 Runspace에서 중단점과 상호 작용할 **Runspace** 개체를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-146">The **Runspace** parameter specifies a **Runspace** object to interact with breakpoints in the specified runspace.</span></span>

- <span data-ttu-id="fa7a5-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - 이 기능을 사용하면 PowerShell 경로 구문을 지원하지 않는 네이티브 명령에 PowerShell 공급자 경로를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-147">[PSNativePSPathResolution](../learn/experimental-features.md#psnativepspathresolution) - This feature allows you to pass PowerShell provider paths to native commands that don't support PowerShell path syntax.</span></span>

- <span data-ttu-id="fa7a5-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - `-replace` 연산자 문의 왼쪽 피연산자가 문자열이 아닌 경우 해당 피연산자는 문자열로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-148">[PSCultureInvariantReplaceOperator](../learn/experimental-features.md#pscultureinvariantreplaceoperator) - When the left-hand operand in a `-replace` operator statement is not a string, that operand is converted to a string.</span></span> <span data-ttu-id="fa7a5-149">기능을 사용하도록 설정하면, 변환에서 문자열 변환용 문화권 설정이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-149">With the feature enabled, the conversion does not use Culture settings for string conversion.</span></span>

- <span data-ttu-id="fa7a5-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel)은 향후 예측 IntelliSense 플러그 인을 지원하기 위한 토대를 마련합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-150">[PSSubsystemPluginModel](../learn/experimental-features.md#pssubsystempluginmodel) lays the groundwork to support future Predictive IntelliSense plug-ins.</span></span>

## <a name="breaking-changes-and-improvements"></a><span data-ttu-id="fa7a5-151">주요 변경 내용 및 개선 사항</span><span class="sxs-lookup"><span data-stu-id="fa7a5-151">Breaking Changes and Improvements</span></span>

- <span data-ttu-id="fa7a5-152">네이티브 명령이 `stderr`에 쓸 때 `$false`가 되지 않도록 `$?` 수정([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span><span class="sxs-lookup"><span data-stu-id="fa7a5-152">Fix `$?` to not be `$false` when native command writes to `stderr` ([#13395](https://github.com/PowerShell/PowerShell/pull/13395))</span></span>

  <span data-ttu-id="fa7a5-153">실패를 표시하지 않고 네이티브 명령이 `stderr`에 쓰는 것은 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-153">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="fa7a5-154">이 변경에 따라, 네이티브 명령에 0이 아닌 종료 코드가 있는 경우에만 `$?`가 `$false`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-154">With this change `$?` is set to `$false` only when the native command also has a non-zero exit code.</span></span> <span data-ttu-id="fa7a5-155">이 변경 내용은 실험적 기능 `PSNotApplyErrorActionToStderr`과 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-155">This change is unrelated to the experimental feature `PSNotApplyErrorActionToStderr`.</span></span>

- <span data-ttu-id="fa7a5-156">`$ErrorActionPreference`가 네이티브 명령의 `stderr` 출력에 영향을 주지 않도록 설정([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span><span class="sxs-lookup"><span data-stu-id="fa7a5-156">Make `$ErrorActionPreference` not affect `stderr` output of native commands ([#13361](https://github.com/PowerShell/PowerShell/pull/13361))</span></span>

  <span data-ttu-id="fa7a5-157">실패를 표시하지 않고 네이티브 명령이 `stderr`에 쓰는 것은 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-157">It is common for native commands to write to `stderr` without intending to indicate a failure.</span></span>
  <span data-ttu-id="fa7a5-158">이 변경에 따라, `stderr` 출력이 **ErrorRecord** 개체에서 계속 캡처되지만, 네이티브 명령에서 **ErrorRecord** 가 제공되는 경우 런타임이 더 이상 `$ErrorActionPreference`에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-158">With this change, `stderr` output is still captured in **ErrorRecord** objects, but the runtime no longer applies `$ErrorActionPreference` if the **ErrorRecord** comes from a native command.</span></span>

- <span data-ttu-id="fa7a5-159">`Get-Date`에서 `-FromUnixTime` 이름을 `-UnixTimeSeconds`로 변경하여 Unix 시간 입력을 허용([#13084](https://github.com/PowerShell/PowerShell/pull/13084))(@aetos382에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-159">Rename `-FromUnixTime` to `-UnixTimeSeconds` on `Get-Date` to allow Unix time input ([#13084](https://github.com/PowerShell/PowerShell/pull/13084)) (Thanks @aetos382!)</span></span>

  <span data-ttu-id="fa7a5-160">`-FromUnixTime` 매개 변수가 7.1-preview.2 중에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-160">The `-FromUnixTime` parameter was added during 7.1-preview.2.</span></span> <span data-ttu-id="fa7a5-161">매개 변수의 이름이 데이터 형식과 좀 더 일치하도록 변경되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-161">The parameter was renamed to better match the data type.</span></span> <span data-ttu-id="fa7a5-162">이 매개 변수는 1970년 1월 1일, 0:00:00 이후의 시간(초)을 나타내는 정수 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-162">This parameter takes an integer value that represents in seconds since January 1, 1970, 0:00:00.</span></span>

  <span data-ttu-id="fa7a5-163">이 예에서는 Unix 시간(1970-01-01 0:00:00 이후의 초로 표시됨)을 DateTime으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-163">This example converts a Unix time (represented by the number of seconds since 1970-01-01 0:00:00) to DateTime.</span></span>

  ```powershell
  Get-Date -UnixTimeSeconds 1577836800

  Wednesday, January 01, 2020 12:00:00 AM
  ```

- <span data-ttu-id="fa7a5-164">명시적으로 지정된 명명된 매개 변수가 해시 테이블 스플래팅의 동일한 매개 변수를 대체하도록 허용(#13162)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-164">Allow explicitly specified named parameter to supersede the same one from hashtable splatting (#13162)</span></span>

  <span data-ttu-id="fa7a5-165">이 변경에 따라, 스플래팅의 명명된 매개 변수는 매개 변수 목록의 끝으로 이동하며 명시적으로 지정된 명명된 매개 변수가 모두 바인딩된 후에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-165">With this change, the named parameters from splatting are moved to the end of the parameter list so that they are bound after all explicitly specified named parameters are bound.</span></span> <span data-ttu-id="fa7a5-166">지정된 명명된 매개 변수를 찾을 수 없는 경우 간단한 함수에 대한 매개 변수 바인딩이 오류를 throw하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-166">Parameter binding for simple functions doesn't throw an error when a specified named parameter cannot be found.</span></span> <span data-ttu-id="fa7a5-167">알 수 없는 명명된 매개 변수는 간단한 함수의 `$args` 매개 변수에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-167">Unknown named parameters are bound to the `$args` parameter of the simple function.</span></span> <span data-ttu-id="fa7a5-168">스플래팅이 인수 목록의 끝으로 이동하면 `$args`에서 매개 변수가 표시되는 순서가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-168">Moving splatting to the end of the argument list changes the order the parameters appears in `$args`.</span></span>

  <span data-ttu-id="fa7a5-169">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-169">For example:</span></span>

  ```powershell
  function SimpleTest {
      param(
          $Name,
          $Path
      )
      "Name: $Name; Path: $Path; Args: $args"
  }
  ```

  <span data-ttu-id="fa7a5-170">이전 동작에서 **MyPath** 는 인수 목록에서 세 번째 인수이므로 `-Path`에 바인딩되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-170">In the previous behavior, **MyPath** is not bound to `-Path` because it's the third argument in the argument list.</span></span> <span data-ttu-id="fa7a5-171">## 따라서 결국 `Blah = "World"`와 함께 ‘$args’에 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-171">## So it ends up being stuffed into '$args' along with `Blah = "World"`</span></span>

  ```powershell
  PS> $hash = @{ Name = "Hello"; Blah = "World" }
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: ; Args: -Blah: World MyPath
  ```

  <span data-ttu-id="fa7a5-172">이 변경에 따라, `@hash`의 인수가 인수 목록의 끝으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-172">With this change, the arguments from `@hash` are moved to the end of the argument list.</span></span> <span data-ttu-id="fa7a5-173">**MyPath** 는 목록의 첫 번째 인수가 되기 때문에 `-Path`에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-173">**MyPath** becomes the first argument in the list, so it is bound to `-Path`.</span></span>

  ```powershell
  PS> SimpleTest @hash "MyPath"
  Name: Hello; Path: MyPath; Args: -Blah: World
  ```

- <span data-ttu-id="fa7a5-174">스위치 매개 변수 `-Qualifier`가 `Split-Path`에 대해 위치를 지정하지 않도록 설정([#12960](https://github.com/PowerShell/PowerShell/pull/12960))(@yecril71pl에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-174">Make the switch parameter `-Qualifier` not positional for `Split-Path` ([#12960](https://github.com/PowerShell/PowerShell/pull/12960)) (Thanks @yecril71pl!)</span></span>

- <span data-ttu-id="fa7a5-175">지정되지 않은 경우 작업 디렉터리를 `Start-Process`에 대한 리터럴 경로로 확인([#11946](https://github.com/PowerShell/PowerShell/pull/11946))(@NoMoreFood에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-175">Resolve the working directory as literal path for `Start-Process` when it's not specified ([#11946](https://github.com/PowerShell/PowerShell/pull/11946)) (Thanks @NoMoreFood!)</span></span>

- <span data-ttu-id="fa7a5-176">웹 cmdlet의 `-OutFile` 매개 변수가 `-LiteralPath`처럼 작동하도록 설정([#11701](https://github.com/PowerShell/PowerShell/pull/11701))(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-176">Make `-OutFile` parameter in web cmdlets to work like `-LiteralPath` ([#11701](https://github.com/PowerShell/PowerShell/pull/11701)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="fa7a5-177">`BigInteger` 숫자 리터럴에 대한 문자열 매개 변수 바인딩을 수정([#11634](https://github.com/PowerShell/PowerShell/pull/11634))(@vexx32에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-177">Fix string parameter binding for `BigInteger` numeric literals ([#11634](https://github.com/PowerShell/PowerShell/pull/11634)) (Thanks @vexx32!)</span></span>

- <span data-ttu-id="fa7a5-178">Windows에서 `Start-Process`는 현재 세션의 모든 환경 변수를 사용하여 프로세스 환경을 만들고, `-UseNewEnvironment`는 새 기본 프로세스 환경을 만듦([#10830](https://github.com/PowerShell/PowerShell/pull/10830))(@iSazonov에게 감사드립니다!)</span><span class="sxs-lookup"><span data-stu-id="fa7a5-178">On Windows, `Start-Process` creates a process environment with all the environment variables from current session, using `-UseNewEnvironment` creates a new default process environment ([#10830](https://github.com/PowerShell/PowerShell/pull/10830)) (Thanks @iSazonov!)</span></span>

- <span data-ttu-id="fa7a5-179">`ScriptBlock`을 대리자로 변환할 때 `PSObject`에서 반환 결과를 래핑하지 않음([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span><span class="sxs-lookup"><span data-stu-id="fa7a5-179">Do not wrap return result in `PSObject` when converting a `ScriptBlock` to a delegate ([#10619](https://github.com/PowerShell/PowerShell/pull/10619))</span></span>

  <span data-ttu-id="fa7a5-180">C# 컨텍스트에서 사용할 대리자 형식으로 `ScriptBlock`을 변환하는 경우 `PSObject`에서 결과를 래핑하면 불필요한 문제가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-180">When a `ScriptBlock` is converted to a delegate type to be used in C# context, wrapping the result in a `PSObject` brings unneeded troubles:</span></span>

  - <span data-ttu-id="fa7a5-181">값이 대리자 반환 형식으로 변환되면 `PSObject`는 기본적으로 래핑 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-181">When the value is converted to the delegate return type, the `PSObject` essentially gets unwrapped.</span></span> <span data-ttu-id="fa7a5-182">따라서 `PSObject`는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-182">So the `PSObject` is unneeded.</span></span>
  - <span data-ttu-id="fa7a5-183">대리자 반환 형식이 `object`인 경우 C# 코드에서 사용할 수 있도록 `PSObject`에 래핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-183">When the delegate return type is `object`, it gets wrapped in a `PSObject` making it hard to work with in C# code.</span></span>

  <span data-ttu-id="fa7a5-184">이 변경 이후에는 반환된 개체가 기본 개체가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa7a5-184">After this change, the returned object is the underlying object.</span></span>
