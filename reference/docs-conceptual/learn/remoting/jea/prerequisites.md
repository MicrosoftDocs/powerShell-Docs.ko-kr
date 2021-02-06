---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA 필수 조건
description: 이 문서에서는 JEA 사용을 시작하기 위해 충족해야 하는 필수 조건을 설명합니다.
ms.openlocfilehash: 5cc70a06887a2d0a840cc83117f865d3148056e1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "92501731"
---
# <a name="prerequisites"></a><span data-ttu-id="ea05f-104">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="ea05f-104">Prerequisites</span></span>

<span data-ttu-id="ea05f-105">Just Enough Administration은 PowerShell 5.0 이상에 포함된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-105">Just Enough Administration is a feature included in PowerShell 5.0 and higher.</span></span> <span data-ttu-id="ea05f-106">이 문서에서는 JEA 사용을 시작하기 위해 충족해야 하는 필수 조건을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-106">This article describes the prerequisites that must be satisfied to start using JEA.</span></span>

## <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="ea05f-107">설치된 PowerShell 버전 확인</span><span class="sxs-lookup"><span data-stu-id="ea05f-107">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="ea05f-108">시스템에 설치된 PowerShell 버전을 확인하려면 Windows PowerShell 프롬프트에서 `$PSVersionTable` 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-108">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="ea05f-109">JEA는 PowerShell 5.0 이상에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-109">JEA is available with PowerShell 5.0 and higher.</span></span> <span data-ttu-id="ea05f-110">전체 기능을 사용하려면 시스템에 사용할 수 있는 최신 버전의 PowerShell을 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-110">For full functionality, it's recommended that you install the latest version of PowerShell available for your system.</span></span> <span data-ttu-id="ea05f-111">다음 표에는 Windows Server에 대한 JEA의 가용성이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-111">The following table describes JEA's availability on Windows Server:</span></span>

| <span data-ttu-id="ea05f-112">서버 운영 체제</span><span class="sxs-lookup"><span data-stu-id="ea05f-112">Server Operating System</span></span> |                <span data-ttu-id="ea05f-113">JEA 가용성</span><span class="sxs-lookup"><span data-stu-id="ea05f-113">JEA Availability</span></span>                |
| ----------------------- | ---------------------------------------------- |
| <span data-ttu-id="ea05f-114">Windows Server 2016+</span><span class="sxs-lookup"><span data-stu-id="ea05f-114">Windows Server 2016+</span></span>    | <span data-ttu-id="ea05f-115">사전 설치됨</span><span class="sxs-lookup"><span data-stu-id="ea05f-115">Preinstalled</span></span>                                   |
| <span data-ttu-id="ea05f-116">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ea05f-116">Windows Server 2012 R2</span></span>  | <span data-ttu-id="ea05f-117">WMF 5.1이 있는 경우 전체 기능</span><span class="sxs-lookup"><span data-stu-id="ea05f-117">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="ea05f-118">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="ea05f-118">Windows Server 2012</span></span>     | <span data-ttu-id="ea05f-119">WMF 5.1이 있는 경우 전체 기능</span><span class="sxs-lookup"><span data-stu-id="ea05f-119">Full functionality with WMF 5.1</span></span>                |
| <span data-ttu-id="ea05f-120">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ea05f-120">Windows Server 2008 R2</span></span>  | <span data-ttu-id="ea05f-121">WMF 5.1에서 축소된 기능<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ea05f-121">Reduced functionality<sup>1</sup> with WMF 5.1</span></span> |

<span data-ttu-id="ea05f-122">다음과 같은 가정용 또는 업무용 컴퓨터에서도 JEA를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-122">You can also use JEA on your home or work computer:</span></span>

| <span data-ttu-id="ea05f-123">클라이언트 운영 체제</span><span class="sxs-lookup"><span data-stu-id="ea05f-123">Client Operating System</span></span> |                   <span data-ttu-id="ea05f-124">JEA 가용성</span><span class="sxs-lookup"><span data-stu-id="ea05f-124">JEA Availability</span></span>                   |
| ----------------------- | ---------------------------------------------------- |
| <span data-ttu-id="ea05f-125">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="ea05f-125">Windows 10 1607+</span></span>        | <span data-ttu-id="ea05f-126">사전 설치됨</span><span class="sxs-lookup"><span data-stu-id="ea05f-126">Preinstalled</span></span>                                         |
| <span data-ttu-id="ea05f-127">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="ea05f-127">Windows 10 1603, 1511</span></span>   | <span data-ttu-id="ea05f-128">기능이 축소된 상태로 사전 설치됨<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="ea05f-128">Preinstalled, with reduced functionality<sup>2</sup></span></span> |
| <span data-ttu-id="ea05f-129">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="ea05f-129">Windows 10 1507</span></span>         | <span data-ttu-id="ea05f-130">사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="ea05f-130">Not available</span></span>                                        |
| <span data-ttu-id="ea05f-131">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="ea05f-131">Windows 8, 8.1</span></span>          | <span data-ttu-id="ea05f-132">WMF 5.1이 있는 경우 전체 기능</span><span class="sxs-lookup"><span data-stu-id="ea05f-132">Full functionality with WMF 5.1</span></span>                      |
| <span data-ttu-id="ea05f-133">Windows 7</span><span class="sxs-lookup"><span data-stu-id="ea05f-133">Windows 7</span></span>               | <span data-ttu-id="ea05f-134">WMF 5.1에서 축소된 기능<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="ea05f-134">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>       |

- <span data-ttu-id="ea05f-135"><sup>1</sup> Windows Server 2008 R2 또는 Windows 7에서 그룹 관리 서비스 계정을 사용하도록 JEA를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-135"><sup>1</sup> JEA can't be configured to use group-managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span> <span data-ttu-id="ea05f-136">가상 계정 및 기타 JEA 기능이 *지원됩니다*.</span><span class="sxs-lookup"><span data-stu-id="ea05f-136">Virtual accounts and other JEA features *are* supported.</span></span>

- <span data-ttu-id="ea05f-137"><sup>2</sup> 다음 JEA 기능은 Windows 10 버전 1511 및 1603에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-137"><sup>2</sup> The following JEA features aren't supported on Windows 10 versions 1511 and 1603:</span></span>

  - <span data-ttu-id="ea05f-138">그룹 관리 서비스 계정으로 실행</span><span class="sxs-lookup"><span data-stu-id="ea05f-138">Running as a group-managed service account</span></span>
  - <span data-ttu-id="ea05f-139">세션 구성의 조건부 액세스 규칙</span><span class="sxs-lookup"><span data-stu-id="ea05f-139">Conditional access rules in session configurations</span></span>
  - <span data-ttu-id="ea05f-140">사용자 드라이브</span><span class="sxs-lookup"><span data-stu-id="ea05f-140">The user drive</span></span>
  - <span data-ttu-id="ea05f-141">로컬 사용자 계정에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="ea05f-141">Granting access to local user accounts</span></span>

  <span data-ttu-id="ea05f-142">이러한 기능에 대한 지원을 받으려면 Windows를 버전 1607(1주년 업데이트) 이상으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-142">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="ea05f-143">Windows Management Framework 설치</span><span class="sxs-lookup"><span data-stu-id="ea05f-143">Install Windows Management Framework</span></span>

<span data-ttu-id="ea05f-144">이전 버전의 PowerShell을 실행 중인 경우 최신 WMF(Windows Management Framework) 업데이트로 시스템을 업데이트해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-144">If you're running an older version of PowerShell, you may need to update your system with the latest Windows Management Framework (WMF) update.</span></span> <span data-ttu-id="ea05f-145">자세한 내용은 [WMF 설명서](/powershell/scripting/wmf/overview)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea05f-145">For more information, see the [WMF documentation](/powershell/scripting/wmf/overview).</span></span>

<span data-ttu-id="ea05f-146">모든 서버를 업그레이드하기 전에 WMF와의 워크로드 호환성을 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-146">It's recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="ea05f-147">Windows 10 사용자는 최신 기능 업데이트를 설치하여 현재 버전의 Windows PowerShell을 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-147">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="ea05f-148">PowerShell 원격 사용</span><span class="sxs-lookup"><span data-stu-id="ea05f-148">Enable PowerShell Remoting</span></span>

<span data-ttu-id="ea05f-149">PowerShell 원격은 JEA가 작성된 기반을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-149">PowerShell Remoting provides the foundation on which JEA is built.</span></span> <span data-ttu-id="ea05f-150">JEA를 사용하기 전에 PowerShell Remoting을 사용하도록 설정하고 올바르게 보안되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-150">It's necessary to ensure PowerShell Remoting is enabled and properly secured before you can use JEA.</span></span> <span data-ttu-id="ea05f-151">자세한 내용은 [WinRM 보안](/powershell/scripting/learn/remoting/winrmsecurity)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea05f-151">For more information, see [WinRM Security](/powershell/scripting/learn/remoting/winrmsecurity).</span></span>

<span data-ttu-id="ea05f-152">Windows Server 2012, 2012 R2 및 2016에서는 PowerShell 원격이 기본적으로 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-152">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span> <span data-ttu-id="ea05f-153">관리자 권한 PowerShell 창에서 다음 명령을 실행하여 PowerShell 원격을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-153">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="ea05f-154">PowerShell 모듈 및 스크립트 블록 로깅 사용(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="ea05f-154">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="ea05f-155">다음 단계에서는 시스템에서 모든 PowerShell 작업에 대한 로깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-155">The following steps enable logging for all PowerShell actions on your system.</span></span> <span data-ttu-id="ea05f-156">PowerShell 모듈 로깅이 JEA에 필요하지는 않지만, 사용자가 실행한 명령이 중앙 위치에 기록되도록 로깅을 설정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-156">PowerShell Module Logging isn't required for JEA, however it's recommended you turn on logging to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="ea05f-157">그룹 정책을 사용하여 PowerShell 모듈 로깅 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-157">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="ea05f-158">워크스테이션에서 로컬 그룹 정책 편집기를 열거나 Active Directory 도메인 컨트롤러의 그룹 정책 관리 콘솔에서 그룹 정책 개체를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-158">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="ea05f-159">**컴퓨터 구성\\관리 템플릿\\Windows 구성 요소\\Windows PowerShell** 로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-159">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="ea05f-160">**모듈 로깅 켜기** 를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-160">Double-click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="ea05f-161">**사용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-161">Click **Enabled**</span></span>
5. <span data-ttu-id="ea05f-162">[옵션] 섹션에서 [모듈 이름] 옆의 **표시** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-162">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="ea05f-163">모든 모듈에서 명령을 기록하려면 팝업 창에 `*`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-163">Type `*` in the pop-up window to log commands from all modules.</span></span>
7. <span data-ttu-id="ea05f-164">**확인** 을 클릭하여 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-164">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="ea05f-165">**PowerShell 스크립트 블록 로깅 켜기** 를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-165">Double-click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="ea05f-166">**사용** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-166">Click **Enabled**</span></span>
10. <span data-ttu-id="ea05f-167">**확인** 을 클릭하여 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-167">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="ea05f-168">(도메인에 가입된 컴퓨터만 해당) `gpupdate`를 실행하거나 그룹 정책에서 업데이트된 정책을 처리하고 설정을 적용할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-168">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="ea05f-169">그룹 정책을 통해 시스템 차원의 PowerShell 기록을 사용하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ea05f-169">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ea05f-170">다음 단계</span><span class="sxs-lookup"><span data-stu-id="ea05f-170">Next steps</span></span>

[<span data-ttu-id="ea05f-171">역할 기능 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="ea05f-171">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="ea05f-172">세션 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="ea05f-172">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="ea05f-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea05f-173">See also</span></span>

[<span data-ttu-id="ea05f-174">WinRM 보안</span><span class="sxs-lookup"><span data-stu-id="ea05f-174">WinRM Security</span></span>](/powershell/scripting/learn/remoting/winrmsecurity)

[<span data-ttu-id="ea05f-175">PowerShell ♥ Blue Team</span><span class="sxs-lookup"><span data-stu-id="ea05f-175">PowerShell ♥ the Blue Team</span></span>](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
