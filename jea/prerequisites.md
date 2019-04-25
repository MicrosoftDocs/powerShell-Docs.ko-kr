---
ms.date: 06/12/2017
keywords: jea,powershell,security
title: JEA 필수 조건
ms.openlocfilehash: acc16c0c7eec357b621c0706a66b8752ae5578cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084847"
---
# <a name="prerequisites"></a><span data-ttu-id="fa60e-103">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="fa60e-103">Prerequisites</span></span>

> <span data-ttu-id="fa60e-104">적용 대상: Windows Powershell 5.0</span><span class="sxs-lookup"><span data-stu-id="fa60e-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="fa60e-105">Just Enough Administration은 Windows PowerShell 5.0 이상에 포함된 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-105">Just Enough Administration is a feature included with Windows PowerShell 5.0 and higher.</span></span>
<span data-ttu-id="fa60e-106">이 항목에서는 JEA 사용을 시작하기 위해 충족해야 하는 필수 조건을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-106">This topic describes the prerequisites that must be satisfied in order to start using JEA.</span></span>

## <a name="install-jea"></a><span data-ttu-id="fa60e-107">JEA 설치</span><span class="sxs-lookup"><span data-stu-id="fa60e-107">Install JEA</span></span>

<span data-ttu-id="fa60e-108">JEA는 Windows PowerShell 5.0 이상에서 사용할 수 있지만, 전체 기능을 사용하려면 시스템에 사용할 수 있는 최신 버전의 PowerShell을 설치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-108">JEA is available with Windows PowerShell 5.0 and higher, but for full functionality it is recommended that you install the latest version of PowerShell available for your system.</span></span>
<span data-ttu-id="fa60e-109">다음 표에는 Windows Server에 대한 JEA의 가용성이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-109">The following table describes JEA's availability on Windows Server:</span></span>

<span data-ttu-id="fa60e-110">서버 운영 체제</span><span class="sxs-lookup"><span data-stu-id="fa60e-110">Server Operating System</span></span>   | <span data-ttu-id="fa60e-111">JEA 가용성</span><span class="sxs-lookup"><span data-stu-id="fa60e-111">JEA Availability</span></span>
--------------------------|--------------------------------
<span data-ttu-id="fa60e-112">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fa60e-112">Windows Server 2016</span></span>       | <span data-ttu-id="fa60e-113">사전 설치됨</span><span class="sxs-lookup"><span data-stu-id="fa60e-113">Preinstalled</span></span>
<span data-ttu-id="fa60e-114">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fa60e-114">Windows Server 2012 R2</span></span>    | <span data-ttu-id="fa60e-115">WMF 5.1이 있는 경우 전체 기능</span><span class="sxs-lookup"><span data-stu-id="fa60e-115">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="fa60e-116">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="fa60e-116">Windows Server 2012</span></span>       | <span data-ttu-id="fa60e-117">WMF 5.1이 있는 경우 전체 기능</span><span class="sxs-lookup"><span data-stu-id="fa60e-117">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="fa60e-118">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fa60e-118">Windows Server 2008 R2</span></span>    | <span data-ttu-id="fa60e-119">WMF 5.1에서 축소된 기능<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fa60e-119">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="fa60e-120">다음과 같은 가정용 또는 업무용 컴퓨터에서도 JEA를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-120">You can also use JEA on your home or work computer:</span></span>

<span data-ttu-id="fa60e-121">클라이언트 운영 체제</span><span class="sxs-lookup"><span data-stu-id="fa60e-121">Client Operating System</span></span>   | <span data-ttu-id="fa60e-122">JEA 가용성</span><span class="sxs-lookup"><span data-stu-id="fa60e-122">JEA Availability</span></span>
--------------------------|-----------------------------------------------------
<span data-ttu-id="fa60e-123">Windows 10 1607+</span><span class="sxs-lookup"><span data-stu-id="fa60e-123">Windows 10 1607+</span></span>          | <span data-ttu-id="fa60e-124">사전 설치됨</span><span class="sxs-lookup"><span data-stu-id="fa60e-124">Preinstalled</span></span>
<span data-ttu-id="fa60e-125">Windows 10 1603, 1511</span><span class="sxs-lookup"><span data-stu-id="fa60e-125">Windows 10 1603, 1511</span></span>     | <span data-ttu-id="fa60e-126">기능이 축소된 상태로 사전 설치됨<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="fa60e-126">Preinstalled, with reduced functionality<sup>2</sup></span></span>
<span data-ttu-id="fa60e-127">Windows 10 1507</span><span class="sxs-lookup"><span data-stu-id="fa60e-127">Windows 10 1507</span></span>           | <span data-ttu-id="fa60e-128">사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="fa60e-128">Not available</span></span>
<span data-ttu-id="fa60e-129">Windows 8, 8.1</span><span class="sxs-lookup"><span data-stu-id="fa60e-129">Windows 8, 8.1</span></span>            | <span data-ttu-id="fa60e-130">WMF 5.1이 있는 경우 전체 기능</span><span class="sxs-lookup"><span data-stu-id="fa60e-130">Full functionality with WMF 5.1</span></span>
<span data-ttu-id="fa60e-131">Windows 7</span><span class="sxs-lookup"><span data-stu-id="fa60e-131">Windows 7</span></span>                 | <span data-ttu-id="fa60e-132">WMF 5.1에서 축소된 기능<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="fa60e-132">Reduced functionality<sup>1</sup> with WMF 5.1</span></span>

<span data-ttu-id="fa60e-133"><sup>1</sup> Windows Server 2008 R2 또는 Windows 7에서 관리되는 서비스 계정을 사용하도록 JEA를 구성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-133"><sup>1</sup> JEA cannot be configured to use group managed service accounts on Windows Server 2008 R2 or Windows 7.</span></span>
<span data-ttu-id="fa60e-134">가상 계정 및 기타 JEA 기능이 *지원됩니다*.</span><span class="sxs-lookup"><span data-stu-id="fa60e-134">Virtual accounts and other JEA features *are* supported.</span></span>

<span data-ttu-id="fa60e-135"><sup>2</sup> Windows 10 버전 1511 및 1603은 그룹 관리 서비스 계정으로 실행, 세션 구성의 조건부 액세스 규칙, 사용자 드라이브 및 로컬 사용자 계정에 대한 액세스 권한 부여 JEA 기능을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-135"><sup>2</sup> Windows 10 versions 1511 and 1603 do not support the following JEA features: running as a group managed service account, conditional access rules in session configurations, the user drive, and granting access to local user accounts.</span></span>
<span data-ttu-id="fa60e-136">이러한 기능에 대한 지원을 받으려면 Windows를 버전 1607(1주년 업데이트) 이상으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-136">To get support for these features, update Windows to version 1607 (Anniversary Update) or higher.</span></span>

### <a name="check-which-version-of-powershell-is-installed"></a><span data-ttu-id="fa60e-137">설치된 PowerShell 버전 확인</span><span class="sxs-lookup"><span data-stu-id="fa60e-137">Check which version of PowerShell is installed</span></span>

<span data-ttu-id="fa60e-138">시스템에 설치된 PowerShell 버전을 확인하려면 Windows PowerShell 프롬프트에서 `$PSVersionTable` 변수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-138">To check which version of PowerShell is installed on your system, check the `$PSVersionTable` variable in a Windows PowerShell prompt.</span></span>

```powershell
$PSVersionTable.PSVersion
```

```output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

<span data-ttu-id="fa60e-139">*주* 버전이 **5**보다 크거나 같으면 JEA를 사용할 준비가 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-139">You are ready to use JEA if the *Major* version is equal to or greater than **5**.</span></span>
<span data-ttu-id="fa60e-140">최상의 환경을 구축하고 모든 최신 기능에 액세스하려면 가능한 경우 PowerShell 버전 **5.1**로 업그레이드하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-140">For the best experience, and to have access to all the latest features, it is recommended that you upgrade to PowerShell version **5.1** when possible.</span></span>

### <a name="install-windows-management-framework"></a><span data-ttu-id="fa60e-141">Windows Management Framework 설치</span><span class="sxs-lookup"><span data-stu-id="fa60e-141">Install Windows Management Framework</span></span>

<span data-ttu-id="fa60e-142">이전 버전의 PowerShell을 실행 중인 경우 최신 WMF(Windows Management Framework) 업데이트로 시스템을 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-142">If you are running an older version of PowerShell, you will need to update your system with the latest Windows Management Framework (WMF) update.</span></span>
<span data-ttu-id="fa60e-143">업데이트 패키지 및 최신 WMF 릴리스 정보 링크는 [다운로드 센터](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/)에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-143">Update packages and a link to the latest WMF release notes are available in the [Download Center](https://blogs.msdn.microsoft.com/powershell/2016/02/24/windows-management-framework-wmf-5-0-rtm-packages-has-been-republished/).</span></span>

<span data-ttu-id="fa60e-144">모든 서버를 업그레이드하기 전에 WMF와의 워크로드 호환성을 테스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-144">It is strongly recommended that you test your workload's compatibility with WMF before upgrading all of your servers.</span></span>

<span data-ttu-id="fa60e-145">Windows 10 사용자는 최신 기능 업데이트를 설치하여 현재 버전의 Windows PowerShell을 얻어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-145">Windows 10 users should install the latest feature updates to obtain the current version of Windows PowerShell.</span></span>

## <a name="enable-powershell-remoting"></a><span data-ttu-id="fa60e-146">PowerShell 원격 사용</span><span class="sxs-lookup"><span data-stu-id="fa60e-146">Enable PowerShell Remoting</span></span>

<span data-ttu-id="fa60e-147">PowerShell 원격은 JEA가 작성된 기반을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-147">PowerShell Remoting provides the foundation on which JEA is built.</span></span>
<span data-ttu-id="fa60e-148">따라서 JEA를 사용하기 전에 먼저 시스템에서 PowerShell 원격을 사용하도록 설정하고 [올바르게 보안을 설정](/powershell/scripting/setup/winrmsecurity)해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-148">It is therefore necessary to ensure PowerShell Remoting is enabled and [properly secured](/powershell/scripting/setup/winrmsecurity) on your system before you can use JEA.</span></span>

<span data-ttu-id="fa60e-149">Windows Server 2012, 2012 R2 및 2016에서는 PowerShell 원격이 기본적으로 사용하도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-149">PowerShell Remoting is enabled by default on Windows Server 2012, 2012 R2, and 2016.</span></span>
<span data-ttu-id="fa60e-150">관리자 권한 PowerShell 창에서 다음 명령을 실행하여 PowerShell 원격을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-150">You can enable PowerShell Remoting by running the following command in an elevated PowerShell window.</span></span>

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a><span data-ttu-id="fa60e-151">PowerShell 모듈 및 스크립트 블록 로깅 사용(선택 사항)</span><span class="sxs-lookup"><span data-stu-id="fa60e-151">Enable PowerShell module and script block logging (optional)</span></span>

<span data-ttu-id="fa60e-152">다음 단계에서는 시스템에서 모든 PowerShell 작업에 대한 로깅을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-152">The following steps enable logging for all PowerShell actions on your system.</span></span>
<span data-ttu-id="fa60e-153">PowerShell 모듈 로깅이 JEA에 필요하지는 않지만, 사용자가 실행한 명령이 중앙 위치에 기록되도록 PowerShell 모듈 로깅을 켜는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-153">PowerShell Module Logging is not required for JEA, however it is strongly recommended that you turn it on to ensure the commands users run are logged in a central location.</span></span>

<span data-ttu-id="fa60e-154">그룹 정책을 사용하여 PowerShell 모듈 로깅 정책을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-154">You can configure the PowerShell Module Logging policy using Group Policy.</span></span>

1. <span data-ttu-id="fa60e-155">워크스테이션에서 로컬 그룹 정책 편집기를 열거나 Active Directory 도메인 컨트롤러의 그룹 정책 관리 콘솔에서 그룹 정책 개체를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-155">Open the Local Group Policy Editor on a workstation or a Group Policy Object in the Group Policy Management Console on an Active Directory Domain Controller</span></span>
2. <span data-ttu-id="fa60e-156">**컴퓨터 구성\\관리 템플릿\\Windows 구성 요소\\Windows PowerShell**로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-156">Navigate to **Computer Configuration\\Administrative Templates\\Windows Components\\Windows PowerShell**</span></span>
3. <span data-ttu-id="fa60e-157">**모듈 로깅 켜기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-157">Double click on **Turn on Module Logging**</span></span>
4. <span data-ttu-id="fa60e-158">**사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-158">Click **Enabled**</span></span>
5. <span data-ttu-id="fa60e-159">[옵션] 섹션에서 [모듈 이름] 옆의 **표시**를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-159">In the Options section, click on **Show** next to Module Names</span></span>
6. <span data-ttu-id="fa60e-160">팝업 창에 `\*`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-160">Type `\*` in the pop up window.</span></span> <span data-ttu-id="fa60e-161">이렇게 하면 PowerShell에서 모든 모듈의 명령을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-161">This instructs PowerShell to log commands from all modules.</span></span>
7. <span data-ttu-id="fa60e-162">**확인**을 클릭하여 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-162">Click **OK** to set the policy</span></span>
8. <span data-ttu-id="fa60e-163">**PowerShell 스크립트 블록 로깅 켜기**를 두 번 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-163">Double click on **Turn on PowerShell Script Block Logging**</span></span>
9. <span data-ttu-id="fa60e-164">**사용**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-164">Click **Enabled**</span></span>
10. <span data-ttu-id="fa60e-165">**확인**을 클릭하여 정책을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-165">Click **OK** to set the policy</span></span>
11. <span data-ttu-id="fa60e-166">(도메인에 가입된 컴퓨터만 해당) `gpupdate`를 실행하거나 그룹 정책에서 업데이트된 정책을 처리하고 설정을 적용할 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-166">(On domain-joined machines only) Run `gpupdate` or wait for Group Policy to process the updated policy and apply the settings</span></span>

<span data-ttu-id="fa60e-167">그룹 정책을 통해 시스템 차원의 PowerShell 기록을 사용하도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fa60e-167">You can also enable system-wide PowerShell transcription through Group Policy.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fa60e-168">다음 단계</span><span class="sxs-lookup"><span data-stu-id="fa60e-168">Next steps</span></span>

[<span data-ttu-id="fa60e-169">역할 기능 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="fa60e-169">Create a role capability file</span></span>](role-capabilities.md)

[<span data-ttu-id="fa60e-170">세션 구성 파일 만들기</span><span class="sxs-lookup"><span data-stu-id="fa60e-170">Create a session configuration file</span></span>](session-configurations.md)

## <a name="see-also"></a><span data-ttu-id="fa60e-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa60e-171">See also</span></span>

[<span data-ttu-id="fa60e-172">PowerShell 원격 및 WinRM 보안에 대한 추가 정보</span><span class="sxs-lookup"><span data-stu-id="fa60e-172">Additional information about PowerShell Remoting and WinRM security</span></span>](/powershell/scripting/setup/winrmsecurity)

[<span data-ttu-id="fa60e-173">보안에 관한 *PowerShell ♥ the Blue Team*(PowerShell ♥ Blue Team) 블로그 게시물</span><span class="sxs-lookup"><span data-stu-id="fa60e-173">*PowerShell ♥ the Blue Team* blog post on security</span></span>](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)